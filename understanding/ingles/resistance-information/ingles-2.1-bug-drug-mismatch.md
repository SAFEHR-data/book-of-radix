---
description: >-
  This is a re-write of the Ingles Bug Drug Mismatch to include things for Bug
  Drug Mismatch
---

# Ingles 2.1 Bug Drug mismatch

## Introduction

{% hint style="warning" %}
Leave for now: will be written after Background and Rationale complete
{% endhint %}

## 2. Background and Rationale

#### Antimicrobial Resistance

{% include "../../../.gitbook/includes/bg-antimicrobial-resistance-a....md" %}

Urinary tract infections (UTIs) represent a particularly important context in which to examine AMR, given their prevalence, burden on the NHS, high rate of empirical antibiotic prescribing, and the significant rates of resistance observed in urinary pathogens.

#### Disease Specific Background

{% include "../../../.gitbook/includes/background-uti-epidemiology.md" %}

#### Dilemma of empirical prescribing

{% include "../../../.gitbook/includes/dilemma-of-empirical-prescribing.md" %}

#### Antimicrobial Stewardship

{% include "../../../.gitbook/includes/antimicrobial-stewardship-s....md" %}

#### The EHRS opportunity for antibiotic stewardship

{% include "../../../.gitbook/includes/bg-the-ehr-opportunity-for-ant....md" %}

#### The Local Context

***

University College London Hospitals NHS Foundation Trust (UCLH) provides acute and specialist services across six hospitals in North Central London, which share a single Electronic Health Record System (EHRS). In addition to serving the local population in the borough of Camden, UCLH receives referrals from across London and the wider country for specialist services including Neurology, Oncology, and Infectious Diseases. This includes sharing patients with neighbouring hospital trusts such as the Royal Free Hospital, Whittington Health, and North Middlesex Hospital amongst a multitude of others.&#x20;

This geographic clustering of hospitals means that patients frequently move between institutions, receiving care across multiple sites and specialties. As these hospitals do not share the same EHRS, a patient's antibiotic history and microbiology results may be distributed across multiple non-interoperable systems, as well as between primary and secondary care, making prior resistance history difficult to access in a timely manner.

#### Bug -Drug Mismatch

_A bug-drug mismatch occurs when a prescribed antibiotic does not effectively treat the bacterial pathogen it is targeting. This mismatch may arise through two principle mechanisms. First, the antibiotic may inherently inactive against the causative organism. Second, the bacterium may have developed AMR, rendering a previously effective agent therapeutically inadequate._

The development of AMR itself can occur via two distinct pathways. In the first, repeated or prolonged exposure to antibiotics exerts selective pressure on bacterial populations within the host. Susceptible organisms are eliminated, while those harbouring pre-existing resistance mutations survive and proliferate, gradually shifting the microbial population toward a resistant phenotype. In the second pathway, resistant bacteria are acquired exogenously from the environment, for example, through contact with other individuals, healthcare settings, animals, or contaminated food sources. Once these exogenous resistant organisms become established within the host, they may transfer their resistance-encoding genetic elements to commensal bacteria already present in the individual's microbiome through horizontal gene transfer mechanisms, such as plasmid exchange. Consequently, bacteria that were previously susceptible within the host's own flora may acquire resistance without ever having been directly exposed to antibiotic selection pressure.

_Resistance is formally determined on susceptibility testing with clinical breakpoints for the laboratory defined by the The European Committee on Antimicrobial Susceptibility Testing (EUCAST), which updates annually. Expected resistance and susceptibility phenotypes are described in the EUCAST expert rules, providing laboratories with a standardised framework on which to define susceptible or resistant bacteria. On the basis of these breakpoints, susceptibility categories are defined as: **S** (Susceptible), **I** (Susceptible at Increased Exposure to the Drug), and **R** (Resistant)._

_(notes \*\*There are some expected phenotpyes of resistance and sensitivities which are described here:_ [_https://www.eucast.org/fileadmin/eucast/pdf/expert\_rules/Expected\_Resistant\_Phenotypes\_v1.2\_20230113.pdf_](https://www.eucast.org/fileadmin/eucast/pdf/expert_rules/Expected_Resistant_Phenotypes_v1.2_20230113.pdf)_. The laboratory uses this to determine susceptibility \*\*notes)_

_The majority of urinary tract infections are caused by **Enterobacterales** — a family of gram-negative bacteria including Escherichia coli, Klebsiella , Proteus , Enterobacter , Citrobacter , Serratia, Providencia and Morganella species._&#x20;

_Two other groups also frequently cause UTIs: **Enterococcus** (both faecalis and faecium), which is a gram-positive organism, and **Pseudomonas**, a gram-negative organism, the latter of which can often colonise the urinary tract if a catheter is in situ or there is foreign material._

As the majority of urinary tract infections are caused by Enterobacterales, and given that organisms such as _Pseudomonas_ can represent colonisation in catheters rather than true infection, this trial will use **Enterobacterales isolates only** as the basis for detecting bug-drug mismatch. Specifically, the alert will be triggered when a prescribed antibiotic is discordant with susceptibility results from a prior Enterobacterales isolate within the preceding 3 months.

Some Enterobacterales have "expected resistant pehnotypes", which isolates of a species are generally universally resistant (>90% of all isolates irrespective of origin exhibit a characteristic resistance mechanism or MIC values above the PK/PD breakpoint listed in EUCAST tables. As laboratories are expected to not report this result or report the isolate as resistant we will map these as resistant as per the EUCAST Expected Phenotypes v1.2 rules ([https://www.eucast.org/fileadmin/eucast/pdf/expert\_rules/Expected\_Resistant\_Phenotypes\_v1.2\_20230113.pdf](https://www.eucast.org/fileadmin/eucast/pdf/expert_rules/Expected_Resistant_Phenotypes_v1.2_20230113.pdf)).&#x20;



#### Ingles 2.1

Research Question

Among adult patients with urinary tract infections caused by Enterobacterales, does a digital alert that surfaces antimicrobial susceptibility data at the point of prescribing when a bug-drug mismatch is detected, compared with standard care, reduce the rate of bug-drug mismatched prescribing?

## PICOT

### _Population_

All adults patients (over 18) who are not pregnant and are prescribed an antibiotic for the following urinary source indications are included.

1. Lower Urinary Tract Infection (Cystitis)
2. Upper Urinary Tract Infection (Pyelonephritis)
3. Recurrent Urinary Tract Infection&#x20;
4. Catheter-associated UTI

_**Exclusion**_&#x20;

1. Pregnancy
2. Under 18s
3. Previously randomised in the trial on the same encounter

### _Intervention_

Adult patients attending hospital who receive an antibiotic order for a urinary source infection indication will be automatically enrolled. At the point of order signature, an Our Practice Advisory Card will be triggered.

Patients who fulfil the eligibility criteria will be randomised between intervention and standard care arms. All study data will be extracted from the electronic patient record, with no additional testing or follow-up requirements.&#x20;

1. _Patient initiated on antibiotic therapy for a urinary source indication._ The patient enters the study at the point of antibiotic order placement.
2. _Clinician opts for antibiotic treatment and selects desired antibiotic from orders tab search box (e.g. Co-Amoxiclav)._
3. _Clinician enters antibiotic indication data within order window (mandated step) for body system and specific indication (as described above).  The dose, timing, frequency and duration are entered.  The order is accepted and appears in the orders sidebar for signature._
4. _Signing the order/prescription, triggers silent evaluation of logic rules determining order appropriateness (compliance against existing guidelines) and second stage eligibility criteria:_

_The logic rules are as below:_

* _1.Does the indication fit a urinary source as described above (Y/N)_
* _2.Has the patient already been randomised within the study during the current patient encounter (Y/N)_
* _3.Is there discordance between the selected antibiotic, and sensitivity to previous microbiology over the last 180 days as described above. (Y/N)_

_Then the following happens_

* If N for question 1 then the patient is excluded from the trial
* If Y for question 2 then the patient is excluded from the trial
* If Y then N, for questions 1 and 2 then the patient moves to question 3. Where they are randomised to an OPA card showing them standard of care at the time in hospital compared to an OPA card which shows a bug-drug mismatch.

**Control arm:** An interruptive OPA card with guideline adherence/ or whatever is current standard of care is shown to the clinicians.&#x20;

_If the eligibility criteria are satisfied then the patient will be randomised to alert or standard care arms (no alert)._ &#x20;

Recruitment will be automatic. Patients who fulfil the eligibility criteria, described above, will be enrolled in the study and randomised between the intervention and standard care arms at the point of prescription. All study data will be extracted from the electronic health record system (EHRS). There will be no additional testing or follow-up requirements beyond routine clinical care.

**Our Practice Advisory (OPA)**

The intervention is delivered through an Our Practice Advisory (OPA) card, a digital alert embedded within the EHRS that is triggered at the point of antibiotic order signature. The OPA card functions as follows:

**Study workflow**

1. A patient is treated for a UTI indication. The patient enters the study at the point of antibiotic order placement by the treating clinician.
2. The clinician selects the desired antibiotic from the orders tab search box (e.g., co-amoxiclav) and enters the antibiotic indication data within the order window, including body system and specific indication. This is a mandated step within the EHRS. The dose, timing, frequency, and duration are entered. The order is accepted and appears in the orders sidebar for signature.
3. Upon signing the order, a silent evaluation of the study logic rules is triggered: a. Has the patient had an antibiotic prescribed for a UTI indication, if no then they are excluded, if yest they move to second part. b. Has the patient already been randomised within the study during the current encounter? If yes, the patient is excluded from the study. c. If no, the patient is randomised into the intervention arm or the control arm.

**Intervention arm**

Patients randomised to the intervention arm are subject to a silent logic check for a bug-drug mismatch between the prescribed antibiotic and any Enterobacterales isolate identified from the patient's microbiological results. Two outcomes are possible:

If a bug-drug mismatch is detected, an OPA card is displayed to the prescribing clinician at the point of order signature highlighting the bug-drug mismatch.The OPA card does not recommend an antibiotic. The clinician may then choose to amend or continue with the original prescription with the information they have been given.

If no bug-drug mismatch is detected,  the patient receives standard care which may be guideline adherence or no OPA card.

**Comparison (Control Arm)**

Patients randomised to the control arm receive standard care. Standard care reflects the existing prescribing environment at the hospital, which may include pre-existing guideline-concordance OPA cards that operate independently of the trial, or no digital decision support at all. No bug-drug mismatch alert is displayed to clinicians for patients in the control arm, regardless of whether a mismatch exists.



<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>



## Outcomes

_Primary outcome_

1. The proportion of patients prescribed an antibiotic to which a culture isolate, from the defined Enterobacterales organisms, within the preceding 180 days demonstrated resistance. This will be expressed as both a proportion and adjusted odds ratios comparing the intervention and control arms.

_Secondary outcomes_

1. The proportion and adjusted odds ratio of patients whose urinary or blood culture isolate of Enterobacterales, obtained between 24 hours before and 48 hours after the index antibiotic prescription, demonstrated resistance to the antibiotic prescribed.
2. Proportion and adjusted odds ratio of antibiotic prescription changes at the point of prescribing among patients with a detected bug-drug mismatch, compared between the intervention and control arms.
3. Time to antibiotic, the interval between the initial antibiotic order and the first administration of an antibiotic compared between the control and intervention arm.&#x20;
4. Time to appropriate antibiotic, the interval between the initial antibiotic order and the first administration of an antibiotic to which the isolate is susceptible, as defined by an isolate obtained between 24 hours before and 48 hours after the index antibiotic prescription.&#x20;
5. Among patients with a documented bug-drug mismatch to the initially prescribed antibiotic within the preceding 90 days, the proportion whose cultures obtained between 24 hours before and 48 hours after the index antibiotic prescription grew an organism susceptible to the initially prescribed antibiotic.
6. Alert override rate (intervention arm only), the proportion of bug-drug mismatch OPA cards where the clinician chose to continue with the original prescription without amendment.

_Safety:_

1. All-cause mortality: in-hospital, 30-day, and 90-day mortality, compared between the intervention and control arms.
2. Length of hospital stay: measured in days from admission to discharge, compared between the intervention and control arms.
3. Escalation of care: proportion of patients escalated to level 2 (enhanced care unit) or level 3 (intensive care unit) care, compared between the intervention and control arms.
4. Readmission: proportion of patients readmitted to hospital within 30 days of discharge, compared between the intervention and control arms.
5. Time to intravenous to oral switch: among patients receiving intravenous antibiotic therapy at the point of inclusion into the trial, the interval in hours from initiation of intravenous therapy to the first oral antibiotic prescription, compared between the intervention and control arms.
6. Time to alternative antibiotic: the interval from the initial antibiotic order signature to the prescription of an alternative antibiotic for Urinary tract indication, compared between the intervention and control arms.

**Stewardship outcomes**

1. Antibiotic consumption: Measured as defined daily doses (DDD) per admission, reported overall and stratified by WHO AWaRe (Access, Watch, Reserve) category and by antibiotic indication, compared between the intervention and control arms.
2. Days of antibiotic spectrum coverage (DASC): Measured per admission and stratified by indication of the antibiotic prescribed during that encounter, compared between the intervention and control arms.
3. Days of therapy (DOT): Total days of antibiotic therapy per admission, compared between the intervention and control arms.
4. Route of administration: the proportion of patients receiving intravenous versus oral antibiotic courses, compared between the intervention and control arms.
5. Carbapenem and Ciprofloxacin usage: Total DDDs of Carbapenem and Ciprofloxacin usage in both groups.
6. Antimicrobial resistance and healthcare-associated infection: Rates of the following within 90 days of the index prescription, compared between the intervention and control arms:
   * _Clostridioides difficile_ infection that was treated&#x20;
   * _Clostridioides difficile_  colonisation if negative prior
   * Extended-spectrum beta-lactamase (ESBL)-producing organism colonisation if negative prior
   * Carbapenem-resistant organisms (CRO) colonisation if negative prior
   * Ciprofloxacin-resistant isolates colonisation if negative prior
   * Vancomycin-resistant enterococci (VRE) colonisation if negative prior



#### 4. Trial design <a href="#id-4.-trial-design" id="id-4.-trial-design"></a>

This is a single centre prospective individually randomised control trial evaluating the effectiveness of a clinically integrated digital prescribing aide that surfaces relevant antimicrobial resistance ie bug-drug mismatch at the point of prescribing for a range of infections that affect the urinary tract.

Eligible patients will be randomised 1:1 to the intervention (bug-drug mismatch OPA) or standard of care (guideline OPA card or no clinical OPA card) using an automated system within the EHRS. Once a patient is allocated, their assignment will be fixed for all subsequent prescribing episodes during the encounter. This ensures consistency of the intervention within individual patients across multiple prescribing episodes.

Due to the nature of the intervention, prescribers cannot be blinded to treatment allocation, they will either see the digital nudge or they will not. Patients are not actively involved in the intervention and will not be aware of their allocation. Outcome assessment will be conducted using routinely collected electronic data and can be performed by analysts blinded to group allocation.

_Patient-level randomisation introduces a risk of contamination, as prescribers exposed to the alert may modify their subsequent prescribing behaviour for patients in the control arm. However, the alternative approach of randomising by prescriber does not eliminate this risk, as colleagues may discuss the alert with one another, meaning that contamination may persist across prescribers. Alternative trial designs such as a stepped-wedge cluster randomised trial have also been considered, in which different wards would receive the alert or be sequentially introduced to the intervention arm, as demonstrated in the SCREEN trial. However, very few prescribers at this site are ward-based; most rotate between clinical areas, and contamination would therefore remain a concern under a cluster design._

_Patient-level randomisation therefore offers the most pragmatic design. Furthermore, the nature of the intervention itself mitigates the impact of contamination. Unlike a generic prescribing prompt, each alert presents patient-specific susceptibility data unique to the individual encounter, limiting the extent to which exposure to one patient's alert can meaningfully influence prescribing decisions for another._

1. LOWER urinary tract infection (Cystitis)
2. UPPER urinary tract infection (Pyelonephritis)
3. RECURRENT urinary tract infection&#x20;
4. Catheter-associated UTI (incl Stent, Nephrostomy, Other)

The intervention in this study involves surfacing clinical data that is already available within the patient's electronic health record specifically, prior microbiology results, antimicrobial sensitivity data, and relevant prescribing guideline information. The nudge does not alter the treatment itself, the prescribing clinician retains full autonomy over the antibiotic selection and all subsequent clinical decisions. In effect, the advisory ensures that information which should already inform prescribing is presented to the clinician at the point of decision-making, supporting best practice rather than introducing a novel therapeutic intervention. The purpose of the study is to evaluate whether this is effective in improving antibiotic prescribing decisions when antimicrobial resistance information is surfaced at the point of care.

On this basis, individual patient consent is not considered necessary for several reasons. First, the intervention is directed at clinician behaviour, how existing information is accessed and displayed, rather than at the patient directly. In routine care, patients would have no awareness of whether their clinician reviewed their microbiology results before prescribing, and the nudge does not change this dynamic.&#x20;

The study will seek approval under the appropriate regulatory framework for the use of patient data without individual consent, and ethical approval will be obtained through the Health Research Authority. The design aligns with the principles of research embedded within a learning health system, where interventions that optimise the use of existing clinical information to improve care quality can be evaluated without requiring individual participant consent, provided appropriate safeguards for data governance and patient confidentiality are maintained.



#### 6. Intervention <a href="#id-6.-intervention" id="id-6.-intervention"></a>



#### 7. Trial procedures <a href="#id-7.-trial-procedures" id="id-7.-trial-procedures"></a>

#### 8. Finance and supply of equipment <a href="#id-8.-finance-and-supply-of-equipment" id="id-8.-finance-and-supply-of-equipment"></a>

#### 9. Data management <a href="#id-9.-data-management" id="id-9.-data-management"></a>

#### 10. Statistical considerations <a href="#id-10.-statistical-considerations" id="id-10.-statistical-considerations"></a>

**Baseline characteristics**

Baseline demographic and clinical characteristics will be summarised by randomisation arm. Categorical variables (e.g., Sex, UTI indication category, prescribing team,outpatient vs inpatient) will be reported as frequencies and percentages and compared using chi-squared tests or Fisher's exact test. Continuous variables (e.g., Age) will be assessed for normality. Normally distributed variables will be reported as means with standard deviations and compared using independent samples t-tests. Non-normally distributed variables will be reported as medians with interquartile ranges and compared using Kruskal-Wallis tests.&#x20;

Logistic regression will be used for the primary and secondary binary outcomes, adjusted for age, sex, ethnicity, UTI indication category, and location of prescription. Covariates will be retained in the final model if they demonstrate an independent association with the outcome or are thought to be clinically relevant.

**Primary outcome analysis**

The primary outcome:  the proportion of patients prescribed an antibiotic to which a culture isolate of Enterobacterales within the preceding 90 days demonstrated resistance, will be compared between the intervention and control arms. A logistic regression model will be used to estimate the adjusted odds ratio, with adjustment for pre-specified covariates including age, sex, UTI indication category, and location of prescription. Results will be reported as proportions, unadjusted and adjusted odds ratios with 95% confidence intervals and associated p-values.

**Secondary outcome analyses**

Binary secondary outcomes (e.g., contemporaneous bug-drug mismatch, antibiotic prescription changes, IV versus oral prescribing rates) will be analysed using logistic regression, reported as adjusted odds ratios with 95% confidence intervals.

Time-to-event secondary outcomes (e.g., time to antibiotic, time to appropriate antibiotic, time to IV-to-oral switch, time to alternative antibiotic) will be analysed using Cox proportional hazards regression or linear regression as appropriate, depending on the distribution of the data.

Continuous secondary outcomes (e.g., length of hospital stay, days of therapy, defined daily doses, days of antibiotic spectrum coverage) are anticipated to be positively skewed. These will be analysed using generalised linear models with a gamma distribution, with results reported as adjusted rate ratios with 95% confidence intervals and associated p-values.

**Safety outcomes**

Safety outcomes including mortality, escalation of care, and readmission will be analysed as binary outcomes using logistic regression, adjusted for pre-specified covariates. Results will be reported as adjusted odds ratios with 95% confidence intervals.

**Stewardship outcomes**

Antibiotic consumption metrics (defined daily doses, days of antibiotic spectrum coverage, days of therapy) will be analysed using generalised linear models with a gamma distribution or Tweedie distribution.  Route of administration (intravenous versus oral) will be analysed using logistic regression. Antimicrobial resistance and healthcare-associated infection rates will be reported descriptively and compared using chi-squared or Fisher's exact tests as appropriate.

**Missing data**

As all data will be extracted from the EHRS, missing data are anticipated to be minimal. The extent and pattern of missing data will be reported. If missing data exceed 5% for any variable, sensitivity analyses using multiple imputation will be considered.

**Significance level**

A two-sided significance level of 0.05 will be used for the primary outcome.

**Sample size**

_Calculation needed_&#x20;

#### 11. Assessment and management of risk <a href="#id-11.-assessment-and-management-of-risk" id="id-11.-assessment-and-management-of-risk"></a>

#### 12. Recording and reporting adverse events <a href="#id-12.-recording-and-reporting-adverse-events" id="id-12.-recording-and-reporting-adverse-events"></a>

#### 13. Oversight committees <a href="#id-13.-oversight-committees" id="id-13.-oversight-committees"></a>

#### 14. Regulatory review and patient and public involvement <a href="#id-14.-regulatory-review-and-patient-and-public-involvement" id="id-14.-regulatory-review-and-patient-and-public-involvement"></a>

**Regulatory review**

**Peer review**

**Patient and public involvement**



#### 15. Monitoring and auditing <a href="#id-15.-monitoring-and-auditing" id="id-15.-monitoring-and-auditing"></a>

#### 16. Training <a href="#id-16.-training" id="id-16.-training"></a>

#### 17. Insurance and indemnity <a href="#id-17.-insurance-and-indemnity" id="id-17.-insurance-and-indemnity"></a>

#### 18. Record keeping and archiving <a href="#id-18.-record-keeping-and-archiving" id="id-18.-record-keeping-and-archiving"></a>

#### 19. Intellectual property <a href="#id-19.-intellectual-property" id="id-19.-intellectual-property"></a>

#### 20. Publication and dissemination <a href="#id-20.-publication-and-dissemination" id="id-20.-publication-and-dissemination"></a>

#### 21. References <a href="#id-21.-references" id="id-21.-references"></a>

#### 22. Appendices <a href="#id-22.-appendices" id="id-22.-appendices"></a>

