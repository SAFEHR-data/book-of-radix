---
description: As per the UCLH JRO template headings
---

# JRO protocol

{% hint style="warning" %}
See [UCL/UCLH Interventional studies protocol template](https://www.ucl.ac.uk/joint-research-office/sites/joint_research_office/files/jro_interventional_protocol_template.docx) (section number matches the template)

Use this document to manage version control and print or convert to a word document directly from here when ready to submit
{% endhint %}

## 1. Introduction

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

#### Ingles 2

The Ingles-2 study hypothesises that surfacing a patient's antibiotic history at the point of prescribing will enable more targeted and judicious antibiotic selection in patients who are thought to have a urinary source of infection.

_Urinary Tract Infections have been selected as the indication as they frequently have prior microbiology and resistance history available, are prone to recurrence, and if inadequately treated can progress to pyelonephritis, bacteraemia and mortality._&#x20;



Research Question Ingles 2

In patients attending secondary care with a presumed urinary tract infection or pyelonephritis, can an electronic alert that surfaces prior microbiological resistance data at the point of prescribing improve prescribing?&#x20;

We would investigate this through the following design.

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>



1. Where prior microbiological resistance data +/- antibiotic prescribing (depending on availability) history exists within the preceding 30 days, an alert will surface this information at the point of prescribing.
2. Where no prior microbiology is available, a nudge will fire if the prescribed antibiotic is not guideline-concordant, steering the prescriber toward recommended therapy.



These alerts would be randomised at the patient level, and if a patient was assigned to one group and repeated encounters would mean they remain with the pop up being triggered.

The alert is purely informational, it does not mandate a specific antibiotic choice or prevent the prescriber from proceeding with their intended prescription.

### 3. Objectives and outcome measures

#### Primary objective

Evaluate the effectiveness of a clinically-integrated digital prescribing nudge surfacing antimicrobial resistance information at the point of prescribing.&#x20;

#### Secondary objectives

1. Evaluate the safety of the digital prescribing prompt&#x20;
2. Evaluate the stewardship outcomes of a prescribing prompt



#### Outcome measures/endpoints

_Effectiveness:_

_Primary outcome_

1. **Proportion of patients prescribed an antibiotic to which their most recent culture isolate (from the defined types) within the preceding 30 days demonstrated resistance in the two different groups.**

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

Will need percentages



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
