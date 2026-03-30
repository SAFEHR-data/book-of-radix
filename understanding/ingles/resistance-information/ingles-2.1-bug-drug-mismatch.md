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

#### Disease Specific Background

{% include "../../../.gitbook/includes/background-uti-epidemiology.md" %}

#### Dilemma of empirical prescribing

{% include "../../../.gitbook/includes/dilemma-of-empirical-prescribing.md" %}

#### Antimicrobial Stewardship

Antimicrobial stewardship seeks to preserve antibiotic effectiveness by limiting resistance. This involves ensuring  antibiotics are initiated only when indicated and that the most narrow spectrum agent is used to target the causative organism. Within the hospital setting, stewardship programmes that have focussed on enabling better prescribing rather than restricting prescribing  have demonstrated reductions in antibiotic overuse and length of stay, without adversely affecting patient mortality outcomes.

#### The EHRS opportunity for antibiotic stewardship

{% include "../../../.gitbook/includes/bg-the-ehr-opportunity-for-ant....md" %}

#### The Local Context

***

University College London Hospitals NHS Foundation Trust (UCLH) provides acute and specialist services across six hospitals in North Central London, which share a single Electronic Health Record System (EHRS). In addition to serving the local population in the borough of Camden, UCLH receives referrals from across London and the wider country for specialist services including Neurology, Oncology, and Infectious Diseases. This includes sharing patients with neighbouring hospital trusts such as the Royal Free Hospital, Whittington Health, and North Middlesex Hospital amongst a multitude of others.&#x20;

This geographic clustering of hospitals means that patients frequently move between institutions, receiving care across multiple sites and specialties. As these hospitals do not share the same EHRS, a patient's antibiotic history and microbiology results may be distributed across multiple non-interoperable systems, as well as between primary and secondary care, making prior resistance history difficult to access in a timely manner.

#### Bug -Drug Mismatch

_A bug-drug mismatch occurs when a prescribed antibiotic does not effectively treat the bacteria it is targeting. This may be due to antimicrobial resistance that has developed over time as an individual is exposed to antibiotics, or it may result from acquisition of resistant bacteria from the environment, which can then transmit resistance genes._&#x20;



_Resistance is determined on susceptibility testing with clinical breakpoints for the laboratory set by the The European Committee on Antimicrobial Susceptibility Testing (EUCAST), which updates annually. Expected resistance and susceptibility phenotypes are described in the EUCAST expert rules. Susceptibility categories are defined as: **S** (Susceptible), **I** (Susceptible at Increased Exposure), and **R** (Resistant)._

_(notes \*\*There are some expected phenotpyes of resistance and sensitivities which are described here:_ [_https://www.eucast.org/fileadmin/eucast/pdf/expert\_rules/Expected\_Resistant\_Phenotypes\_v1.2\_20230113.pdf_](https://www.eucast.org/fileadmin/eucast/pdf/expert_rules/Expected_Resistant_Phenotypes_v1.2_20230113.pdf)_. The laboratory uses this to determine susceptibility \*\*notes)_

_The majority of urinary tract infections are caused by **Enterobacterales** — a family of gram-negative bacteria including Escherichia coli, Klebsiella , Proteus , Enterobacter , Citrobacter , Serratia, and Morganella species._&#x20;

_Two other groups also frequently cause UTIs: **Enterococcus** (both faecalis and faecium), which is a gram-positive organism, and **Pseudomonas**, a gram-negative organism, the latter of which can often colonise the urinary tract if a catheter is in situ or there is foreign material._

&#x20;

As the majority of urinary tract infections are caused by Enterobacterales, and given that organisms such as _Pseudomonas_ can represent colonisation in catheters rather than true infection, this trial will use **Enterobacterales isolates only** as the basis for detecting bug-drug mismatch. Specifically, the alert will be triggered when a prescribed antibiotic is discordant with susceptibility results from a prior Enterobacterales isolate within the preceding 3 months.

Some Enterobacterales have "expected resistant pehnotypes", which isolates of a species are generally universally resistant (>90% of all isolates irrespective of origin exhibit a characteristic resistance mechanism or MIC values above the PK/PD breakpoint listed in EUCAST tables. As laboratories are expected to not report this result or report the isolate as resistant we will map these as resistant as per the EUCAST Expected Phenotypes v1.2 rules ([https://www.eucast.org/fileadmin/eucast/pdf/expert\_rules/Expected\_Resistant\_Phenotypes\_v1.2\_20230113.pdf](https://www.eucast.org/fileadmin/eucast/pdf/expert_rules/Expected_Resistant_Phenotypes_v1.2_20230113.pdf)).&#x20;



#### Ingles 2.1

Research Question

Does a digital alert, triggered when a bug-drug mismatch is detected at the point of prescribing, which surfaces resistance data reduce mismatch rates in patients with urinary tract infections compared with a guideline-concordance nudge?

As the majority of urinary tract infections are caused by Enterobacterales, and given that organisms such as _Pseudomonas_ can represent colonisation in catheters rather than true infection, this trial will use **Enterobacterales isolates only** as the basis for detecting bug-drug mismatch. Specifically, the alert will be triggered when a prescribed antibiotic is discordant with susceptibility results from a prior Enterobacterales isolate within the preceding 3 months.

**PICOT**

_Population_

All adults patients (over 18) who are not pregnant and are prescribed an antibiotic for the following indications

1. Lower Urinary Tract Infection (Cystitis)
2. Upper Urinary Tract Infection (Pyelonephritis)
3. Recurrent Urinary Tract Infection&#x20;
4. Catheter-associated UTI
5. Prostatitis&#x20;

**Intervention arm:** An interruptive OPA card is triggered when a bug-drug mismatch is detected, surfacing the patient's prior microbiology data and highlighting of resistance for Enterobacterales.

**Control arm:** An interruptive OPA card nudges toward guideline-concordant prescribing. Prior microbiology data is surfaced but not highlighted.

_Intervention_

_Adult patients attending hospital who receive an antibiotic order for a Urinary Source Infection indication as described above, who are prescribed an antibiotic will be included._ &#x20;

If a patient has a prescription for one of those indications signed then an Our Practice Advisory Card will be triggered. &#x20;

_Recruitment will be automatic.  Patients who fulfil the above eligibility criteria will be enrolled in the study and randomised between intervention and standard care arms.  All study data will be extracted from the electronic patient record.  There will be no additional testing or follow up requirements._ &#x20;

_Description of the proposed study workflow:_

1. _Patient treated for a UTI indication.  The patient enters the study at the point of antibiotic order placement by the treating clinician.  As such, they may be located in the emergency or outpatient departments or may be an inpatient._ &#x20;
2. _Clinician opts for antibiotic treatment and selects desired antibiotic from orders tab search box (e.g. Co-Amoxiclav)._
3. _Clinician enters antibiotic indication data within order window (mandated step) for body system and specific indication (as described above).  The dose, timing, frequency and duration are entered.  The order is accepted and appears in the orders sidebar for signature._



_The Nudge Our Practice Advisory_

* _Signing the order, triggers silent evaluation of logic rules determining order appropriateness (compliance against existing guidelines) and second stage eligibility criteria:_
* _Has the patient already been randomised within the study during the current patient encounter (Y/N) If Yes, excluded from the study._
* _Is there discordance between the selected antibiotic, and sensitivity to previous microbiology in Enterobacterales group  over the last 90 days. (Y/N) If Yes, then randomised to either Intervention arm or Control Arm, If no then randomised to control arm only._



*

    <figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
* _If the patient is receiving the first order for a UTI in this encounter, and the order is discordant with the recommended treatment in the clinical guideline, and the patient has not been previously randomised within the study within the current encounter, then a further screening step will occur:_
  * _In intervention arm-> Surface microbiology within the last 90 days where resistance is shown. There is no advice but just highlighting prior resistance._ &#x20;
  * _Does the patient have a documented allergy to the guideline-concordant antibiotic recommendation? (Y/N)_
* _._

_Under discussion whether 1 > 2 in terms of delivering randomisation and supporting above logic._

_If the eligibility criteria are satisfied then the patient will be randomised to alert or standard care arms (no alert)._ &#x20;

_If randomised to the alert arm, the intervention will display to the clinician during the antibiotic order process:_<br>

_What do we mean by Bug Drug Mismatch in UTIs?_









Primary outcome



_Secondary outcomes_

1. Proportion of patients whose urinary or blood culture isolate of a gram-negative organism likely to cause UTI (e.g Enterobacterales), obtained between 24 hours before and 48 hours after the index antibiotic prescription, demonstrated resistance to the antibiotic prescribed between the two groups.
2. Proportion of antibiotic prescription changes at the point of prescribing, in response to a fired nudge?
3. Proportion of empiric escalation of antibiotic therapy (broadening of antimicrobial spectrum in the absence of new microbiological evidence) within 72 hours of initial prescription.
4. Among prescribing episodes where the nudge fired and no resistance to the prescribed antibiotic was documented within the preceding 30 days, the proportion in which the antibiotic prescription was changed to adhere to guidance?
5. Among patients with documented resistance to the initially prescribed antibiotic within the preceding 30 days, the proportion whose current admission cultures grew an organism sensitive to the initially prescribed antibiotic.

_Safety:_

1. All cause in-hospital and 90-day mortality.
2. Length of hospital stay (days).
3. Escalation to level 2 or 3 care (ECU or ICU).
4. Readmission to hospital within 30 days of discharge.
5. Time to intravenous to oral antibiotic switch (hours).
6. Presence of infection or colonisation by antimicrobial resistant pathogens

_Stewardship:_

1. _Antibiotic consumption measured as  Defined Daily Doses per admission overall and in AWaRE categories split by indication_
2. _Days of Antibiotic Spectrum consumption per admission and indication_
3. _Days of therapy of antibiotics_&#x20;
4. _Proportion of patients who receive IV or Oral antibiotic courses_&#x20;
5. _Rates of Clostridoides Difficile in both groups, ESBL, CRO and Ciprofloxacin Resistance isolates, and Vancomycin resistant enterococci rates_

##

## PICOT

#### &#x20;<a href="#id-4.-trial-design" id="id-4.-trial-design"></a>







#### 4. Trial design <a href="#id-4.-trial-design" id="id-4.-trial-design"></a>

This is a single centre prospective individually randomised control trial evaluating the effectiveness of a clinically integrated digital prescribing aide that surfaces relevant antimicrobial resistance and antimicrobial usage at the point of prescribing for a range of infections that affect the urinary tract.

Eligible patients would be randomised 1:1 to the intervention (digital nudge) or control (standard workflow) using an automated system within the EHRS. Once a patient is allocated, their assignment will be fixed for all subsequent prescribing episodes during the study period. This ensures consistency of the intervention within individual patients across multiple encounters.

Due to the nature of the intervention, prescribers cannot be blinded to treatment allocation, they will either see the digital nudge or they will not. Patients are not actively involved in the intervention and will not be aware of their allocation. Outcome assessment will be conducted using routinely collected electronic data and can be performed by analysts blinded to group allocation.

The patients randomised into three arms:

1. An interruptive Our Practice Advisory (OPA) card showcases prior antibiotic resistance history and antimicrobial prescription data for the last 30 days. The AMR data will be drawn from Helix, and the prescribing data from EPIC and... ? GP?
2. An interruptive Our Practice Advisory card showcases current guidance for each indication if a prescriber has prescribed against guidance if no prior microbiology history/ antimicrobial usage history is present in the last 30 days.
3. &#x20;Usual workflow with no antimicrobial history surfaced.



_Patient level randomisation introduces a risk of contamination as prescribers exposed to these alerts may modify their subsequent prescribing behaviour. However, the alternative method of randomising by prescriber does not eliminate this risk,  as colleagues may discuss the alert with each other meaning that contamination may persist. Other trial designs such as a step wedged cluster randomised trial could be considered, where different wards had the alert or were sequentially included to the intervention arm as demonstrated in the SCREEN trial. However, very few prescribers are ward based and often rotate between clinical areas therefore would have similar contamination._&#x20;

_Therefore, patient level randomisation offers a pragmatic design. Furthermore, the nature of the intervention itself mitigates the impact of contamination: the interruptive alert in arm 1 surfaces individualised prior antimicrobial resistance and usage history specific to each patient. Unlike a generic prescribing prompt, each alert presents different information, limiting the extent to which exposure to one patient's alert can meaningfully influence prescribing decisions for another._

#### 5. Sampling methods <a href="#id-5.-sampling-methods" id="id-5.-sampling-methods"></a>

**Inclusion criteria**

Patients admitted or prescribed antibiotics at UCLH&#x20;

Age over 18

Patients prescribed  of Antibiotics with Indication of:

1. LOWER urinary tract infection (Cystitis)
2. UPPER urinary tract infection (Pyelonephritis)
3. RECURRENT urinary tract infection&#x20;
4. Catheter-associated UTI (incl Stent, Nephrostomy, Other)
5. Prostatitis

**Exclusion criteria**

Age under 18

Pregnancy



**Recruitment**

All wards or new admissions?

**Consent**

**As this is only showing the data, we are testing whether showing the data is helpful therefore no patient level consent**

#### 6. Intervention <a href="#id-6.-intervention" id="id-6.-intervention"></a>

The patients randomised into three arms:

1. An interruptive Our Practice Advisory (OPA) card showcases prior antibiotic resistance history and antimicrobial prescription data for the last 30 days. The AMR data will be drawn from Helix, and the prescribing data from EPIC and... ? GP?
2. An interruptive Our Practice Advisory card showcases current guidance for each indication if a prescriber has prescribed against guidance if no prior microbiology history/ antimicrobial usage history is present in the last 30 days.
3. &#x20;Usual workflow with no antimicrobial history surfaced.

#### 7. Trial procedures <a href="#id-7.-trial-procedures" id="id-7.-trial-procedures"></a>

#### 8. Finance and supply of equipment <a href="#id-8.-finance-and-supply-of-equipment" id="id-8.-finance-and-supply-of-equipment"></a>

#### 9. Data management <a href="#id-9.-data-management" id="id-9.-data-management"></a>

#### 10. Statistical considerations <a href="#id-10.-statistical-considerations" id="id-10.-statistical-considerations"></a>

Will need percentages of risks



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

