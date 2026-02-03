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

<table data-header-hidden><thead><tr><th width="102.015625" data-type="number">Version</th><th width="212.80078125" valign="top">Features</th><th valign="top">Target</th><th valign="top">Cohort</th></tr></thead><tbody><tr><td>0</td><td valign="top">Age, Sex, $BUG resistance result to $DRUG last N days</td><td valign="top">$BUG resistance result to $DRUG next 7 days</td><td valign="top">DRUG = Cipro, BUG = E. Coli, UTI patients only?</td></tr><tr><td>1</td><td valign="top">Age, Sex, resistance results, past prescriptions, prevalence of bugs?</td><td valign="top">Any resistance result to $DRUG next 7 days</td><td valign="top">DRUG = Cipro, UTI patients only?<br></td></tr><tr><td>2</td><td valign="top">Age, sex, resistance results, past presciptions, prevalence of bugs?</td><td valign="top">"personalised antibiogram" i.e. resistance to set of common drugs</td><td valign="top">Multiple drugs, UTI patients only?</td></tr><tr><td>3</td><td valign="top">Age, sex, resistance results, past presciptions, prevalence of bugs?</td><td valign="top">"personalised antibiogram" i.e. resistance to set of common drugs</td><td valign="top">Multiple drugs, any indication?</td></tr></tbody></table>
