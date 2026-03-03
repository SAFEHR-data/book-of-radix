---
description: Problem set-up for Baby Radix
---

# Baby Radix

### Target model

The running example is based on a much simplified version of the model described in the Yelin paper.  ([Yelin 2019](https://doi.org/10.1038/s41591-019-0503-6)). In words, we wish to predict the risk of resistance to a specific antibiotic at the point of prescribing given the patient's patient's prior history of resistance. The model and the features described here are only to help explain the approach to working rather than a specification for the actual model.

### Data set-up

We describe this in terms of the two potential model deployment environments. The proposed features in the table below are examples to demonstrate the differences in the two deployments

|                        | Deployed at HSL                 | Deployed at UCLH               |
| ---------------------- | ------------------------------- | ------------------------------ |
| Demographics           | Age, sex, postcode              | Age, sex, postcode             |
| Historical resistance  | Complete across NCL             | UCLH only                      |
| Historical prescribing | Not visible (initially)         | UCLH only                      |
| Inflammatory profille  | CRP                             | CRP, vital signs               |
| Immune status          | Neutropaenia                    | Neutropaenia, steroid exposure |
| Co-morbidities         | Count of health care encounters | Charlson, Elixir or similar    |



* The HSL model will be trained and served against data available via the RADIX FHIR server - see [camino-helix.md](../../foundations/camino-helix.md "mention").
* The UCLH model would be built from data held within the hospital data warehouse, and made available through the Camino data pipeline - see [Pilgrimage](https://app.gitbook.com/o/nslEtzGzwZwoDr3tU6Bl/s/e2uVjWL5Ex74zruC39cs/ "mention").

### Minimum working examples

<table data-header-hidden><thead><tr><th width="102.015625" data-type="number">Version</th><th width="212.80078125" valign="top">Features</th><th valign="top">Target</th><th valign="top">Cohort</th></tr></thead><tbody><tr><td>0</td><td valign="top">Age, Sex, $BUG resistance result to $DRUG last N days</td><td valign="top">$BUG resistance result to $DRUG next 7 days</td><td valign="top">DRUG = Cipro, BUG = E. Coli, UTI patients only?</td></tr><tr><td>1</td><td valign="top">Age, Sex, resistance results, past prescriptions, prevalence of bugs?</td><td valign="top">Any resistance result to $DRUG next 7 days</td><td valign="top">DRUG = Cipro, UTI patients only?<br></td></tr><tr><td>2</td><td valign="top">Age, sex, resistance results, past presciptions, prevalence of bugs?</td><td valign="top">"personalised antibiogram" i.e. resistance to set of common drugs</td><td valign="top">Multiple drugs, UTI patients only?</td></tr><tr><td>3</td><td valign="top">Age, sex, resistance results, past presciptions, prevalence of bugs?</td><td valign="top">"personalised antibiogram" i.e. resistance to set of common drugs</td><td valign="top">Multiple drugs, any indication?</td></tr><tr><td>null</td><td valign="top"></td><td valign="top"></td><td valign="top"></td></tr></tbody></table>

## V0 Gold table&#x20;



The following documentation outlines the data extraction and transformation logic used to construct the gold dataset of baby radix. The process involves three primary stages: identifying the cohort of antibiotic prescriptions, extracting relevant historical susceptibility results, and merging these sources to engineer features representing prior specific and class-level resistance exposure. All of the features discussed here are "data features" not "model features" as discussed in [who-does-what](who-does-what/ "mention")

### Query 1: Target Prescriptions Cohort

This query defines the study cohort (the denominator). We identify all medication orders from the Prescriptions table that match the target antimicrobial agents. The selection logic uses substring matching against the generic drug name to capture all formulations (e.g., 'cipro' captures 'ciprofloxacin').

We enrich these prescription records with patient demographics, encounter details (e.g., Inpatient vs. Emergency Department), and indication data. This forms the index date for prediction (RX\_DT).

Output Schema: target\_prescriptions

* ORDER\_MED\_ID: Integer. Unique identifier for the medication order.
* PAT\_MRN\_ID: String. Patient Medical Record Number.
* RX\_DT: Datetime. The timestamp when the prescription was ordered (Index Date).
* SIMPLE\_GENERIC: String. The standardized generic name of the prescribed drug.
* PHARM\_SUBCLASS: String. The pharmacological subclass of the drug (e.g., Fluoroquinolones).
* AGE: Integer. Patient age in years at the time of prescription.
* SEX: String. Biological sex of the patient.
* PATIENT\_STATUS: String. Classification of the encounter (Inpatient, ED, Other).
* CURRENT\_INPATIENT: String. Binary flag indicating if the patient is currently admitted.
* ENC\_LAST\_DEPT\_NAME: String. The clinical department where the order was placed.
* PROPHYLAXIS: String. Binary flag indicating if the order was marked for prophylaxis.

### Query 2: Antimicrobial Susceptibility Test (AST) History

This query extracts the ground truth for resistance. To support the calculation of class-level resistance risk, this query retrieves susceptibility results not just for the target drugs, but for all antibiotics belonging to the same pharmacological subclasses.

This is currently sourced from Matt Hunt's data.

The logic proceeds in two steps: Identify all unique PHARM\_SUBCLASS values associated with the target drug list. Extract all test results from the tests\_table where the drug belongs to those subclasses. Drug names are normalized to ensure alignment with the prescription table. The Sensitivity column serves as the primary outcome marker (S=Susceptible, I=Intermediate, R=Resistant). Other values are considered to be invaild. This needs further investigation.

Output Schema: all\_tests

* MRN: String. Patient Medical Record Number.
* SampleDate: Datetime. The timestamp when the biological specimen was collected.
* DrugName: String. Standardized generic name of the tested antibiotic.
* PharmSubclass: String. Pharmacological subclass of the tested antibiotic.
* Sensitivity: String. The result of the susceptibility test (R, I, S).
* SpecimenID: String. Unique identifier for the biological sample.
* Organism: String. The pathogen identified (if any).

### Query 3: Training Dataset Construction and Feature Engineering

This query joins the prescription cohort with the test history to create the final analytical table. It aligns records by Patient MRN and creates temporal windows relative to the prescription date (RX\_DT).

* We generate two distinct sets of historical features to differentiate between specific drug failure and broader mechanism-based resistance:
* Specific Resistance History: Indicates if the patient had a resistant result ('R') specifically for the prescribed drug in the previous time period.
* Class-Level Resistance History: Indicates if the patient had a resistant result ('R') for any other drug in the same pharmacological subclass in the previous time period excluding the prescribed drug itself. This feature is designed to capture resistance mechanisms that affect the entire class (e.g., cross-resistance among cephalosporins).
* Target Variable: We look forward 1 day back to 2 days forward from the prescription date. If a test for the prescribed drug exists and shows resistance ('R'), the target is 1. If the test shows susceptibility ('S' or 'I'), the target is 0. Prescriptions with no associated test in the 7-day window are flagged.

Output Schema: model\_df

* ORDER\_MED\_ID: Integer. Unique identifier for the medication order.
* PAT\_MRN\_ID: String. Patient Medical Record Number.
* RX\_DT: Datetime. Index date.
* AGE: Integer. Patient age.
* SEX: String. Patient sex.
* PRESCRIBED\_DRUG: String. Name of the drug prescribed.
* resistant\_specific\_last\_30d: Integer (Binary). 1 if prior resistance to the specific drug was found in the last 30 days.
* resistant\_class\_last\_30d: Integer (Binary). 1 if prior resistance to a different drug in the same subclass was found in the last 30 days.
* resistant\_specific\_last\_year: Integer (Binary). 1 if prior resistance to the specific drug was found in the \[-365d, -30d] window.
* resistant\_class\_last\_year: Integer (Binary). 1 if prior resistance to a different drug in the same subclass was found in the \[-365d, -30d] window.
* target\_resistant\_associated: Integer (Binary). The outcome label. 1 if the organism was resistant to the prescribed drug in the next 7 days.
* has\_test\_associated: Integer (Binary). 1 if a valid test result exists in the \[+1d, +2d] window (used for filtering the training set).











