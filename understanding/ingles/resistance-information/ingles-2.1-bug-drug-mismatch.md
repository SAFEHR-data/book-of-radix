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

_A bug-drug mismatch occurs when a prescribed antibiotic does not effectively treat the bacterial pathogen it is targeting. This mismatch may arise through two principle mechanisms. First, the antibiotic may inherently inactive against the causative organism. Second, the bacterium may have developed AMR, rendering a previously effective agent therapeutically inadequate._

The development of AMR itself can occur via two distinct pathways. In the first, repeated or prolonged exposure to antibiotics exerts selective pressure on bacterial populations within the host. Susceptible organisms are eliminated, while those harbouring pre-existing resistance mutations survive and proliferate, gradually shifting the microbial population toward a resistant phenotype. In the second pathway, resistant bacteria are acquired exogenously from the environment, for example, through contact with other individuals, healthcare settings, animals, or contaminated food sources. Once these exogenous resistant organisms become established within the host, they may transfer their resistance-encoding genetic elements to commensal bacteria already present in the individual's microbiome through horizontal gene transfer mechanisms, such as plasmid exchange. Consequently, bacteria that were previously susceptible within the host's own flora may acquire resistance without ever having been directly exposed to antibiotic selection pressure.

_Resistance is formaly determined on susceptibility testing with clinical breakpoints for the laboratory defined by the The European Committee on Antimicrobial Susceptibility Testing (EUCAST), which updates annually. Expected resistance and susceptibility phenotypes are described in the EUCAST expert rules, providing laboratories with a standardised framework. On the basis of these breakpoints, susceptibility categories are defined as: **S** (Susceptible), **I** (Susceptible at Increased Exposure to the Drug), and **R** (Resistant)._

_(notes \*\*There are some expected phenotpyes of resistance and sensitivities which are described here:_ [_https://www.eucast.org/fileadmin/eucast/pdf/expert\_rules/Expected\_Resistant\_Phenotypes\_v1.2\_20230113.pdf_](https://www.eucast.org/fileadmin/eucast/pdf/expert_rules/Expected_Resistant_Phenotypes_v1.2_20230113.pdf)_. The laboratory uses this to determine susceptibility \*\*notes)_

_The majority of urinary tract infections are caused by **Enterobacterales** — a family of gram-negative bacteria including Escherichia coli, Klebsiella , Proteus , Enterobacter , Citrobacter , Serratia, and Morganella species._&#x20;

_Two other groups also frequently cause UTIs: **Enterococcus** (both faecalis and faecium), which is a gram-positive organism, and **Pseudomonas**, a gram-negative organism, the latter of which can often colonise the urinary tract if a catheter is in situ or there is foreign material._

As the majority of urinary tract infections are caused by Enterobacterales, and given that organisms such as _Pseudomonas_ can represent colonisation in catheters rather than true infection, this trial will use **Enterobacterales isolates only** as the basis for detecting bug-drug mismatch. Specifically, the alert will be triggered when a prescribed antibiotic is discordant with susceptibility results from a prior Enterobacterales isolate within the preceding 3 months.

Some Enterobacterales have "expected resistant pehnotypes", which isolates of a species are generally universally resistant (>90% of all isolates irrespective of origin exhibit a characteristic resistance mechanism or MIC values above the PK/PD breakpoint listed in EUCAST tables. As laboratories are expected to not report this result or report the isolate as resistant we will map these as resistant as per the EUCAST Expected Phenotypes v1.2 rules ([https://www.eucast.org/fileadmin/eucast/pdf/expert\_rules/Expected\_Resistant\_Phenotypes\_v1.2\_20230113.pdf](https://www.eucast.org/fileadmin/eucast/pdf/expert_rules/Expected_Resistant_Phenotypes_v1.2_20230113.pdf)).&#x20;

#### Ingles 2.1

Research Question

Does a digital alert, triggered when a bug-drug mismatch is detected in Enterobacterales bacteria at the point of prescribing, which surfaces the resistance data, reduce mismatch rates in patients with urinary tract infections compared with a guideline-concordance nudge?

**PICOT**

_Population_

All adults patients (over 18) who are not pregnant and are prescribed an antibiotic for the following indications

1. Lower Urinary Tract Infection (Cystitis)
2. Upper Urinary Tract Infection (Pyelonephritis)
3. Recurrent Urinary Tract Infection&#x20;
4. Catheter-associated UTI

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
* _Has the patient already been randomised within the study during the current patient encounter or the last 28 days (Y/N) If Yes, excluded from the study._
* _Is there any prior microbiology from the last 90 days? Y/N  if No:_

**Then the patient goes to ARM 1 which is advisory content and guideline adherence information only with a prompt for clinicians to check allergy status.**&#x20;

**If Yes further logic is triggered?**

* _Is there discordance between the selected antibiotic, and sensitivity to previous microbiology in Enterobacterales bacteria over the last 90 days. (Y/N) If Yes, then randomised to either Intervention arm or Control Arm, If no then randomised to prior microbiology arm (Arm 2)._

_**Arm 2 illustrates prior microbiology data as well as guideline adherence information only with a prompt for clinicians to check allergy status.**_

_**If no then randomised to prior microbiology Arm 2**_&#x20;

_**If Yes then can be randomised into Arm 2 or 3**_

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>



_Primary outcome_

1. Evaluate the effectiveness of a clinically-integrated digital prescribing nudge surfacing antimicrobial resistance information at the point of prescribing.&#x20;

**Proportion and adjusted odds ratios of patients prescribed an antibiotic to which their most recent culture isolate (from the defined types) within the preceding 90 days demonstrated resistance in the two different groups (Arm 3 vs Arm 1 and 2)**

_Secondary outcomes_

1. Proportion and adjusted odds ratio of patients whose urinary or blood culture isolate of Enterobacterales, obtained between 24 hours before and 48 hours after the index antibiotic prescription, demonstrated resistance to the antibiotic prescribed between the two groups.
2. Proportion and adjusted odds ratio of antibiotic prescription changes at the point of prescribing in the bug-drug mismatch group, compared between intervention and control arms
3. Proportion and adjusted odds ratio of empiric escalation of antibiotic therapy (broadening of antimicrobial spectrum in the absence of new microbiological evidence) within 72 hours of initial prescription comparing the groups using an increase of Antibiotic Spectrum Index to define escalation or a switch from PO to IV.
4. Among prescribing episodes, in the Control group (Arm 1), and no resistance to the prescribed antibiotic was documented within the preceding 90 days, the proportion in which the antibiotic prescription was changed to adhere to guidance?
5. Among patients with documented bug-drug mismatch to the initially prescribed antibiotic within the preceding 90 days, the proportion whose current admission cultures grew an organism sensitive to the initially prescribed antibiotic.

_Safety:_

1. All cause in-hospital and 90-day mortality between intervention and control groups
2. Length of hospital stay (days) between intervention and control groups
3. Escalation to level 2 or 3 care (ECU or ICU)  between intervention and control groups
4. Readmission to hospital within 30 days of discharge  between intervention and control groups
5. Time to intravenous to oral antibiotic switch (hours)  between intervention and control groups in initial IV therapy at the point of inclusion into trial.
6. Time from initial antibiotic order signature to prescription of an alternative antibiotic, compared between intervention and control groups

_Stewardship:_

1. _Antibiotic consumption measured as Defined Daily Doses per admission overall and in AWaRE categories split by indication of antibiotic_&#x20;
2. _Days of Antibiotic Spectrum consumption per admission and indication of antibiotic prescribed in that encounter_
3. _Days of therapy of antibiotics in each group_&#x20;
4. _Proportions/rates of patients who receive IV or Oral antibiotic courses in each group_
5. _Rates of Clostridoides Difficile in both groups, ESBL, CRO and Ciprofloxacin Resistance isolates, and Vancomycin resistant enterococci rates_ ( 90 days)

##

#### 4. Trial design <a href="#id-4.-trial-design" id="id-4.-trial-design"></a>

This is a single centre prospective individually randomised control trial evaluating the effectiveness of a clinically integrated digital prescribing aide that surfaces relevant antimicrobial resistance at the point of prescribing for a range of infections that affect the urinary tract.

Eligible patients would be randomised 1:1 to the intervention (digital nudge) or control (guideline adherence with prior microbiology or guideline adherence with no prior microbiology) using an automated system within the EHRS. Once a patient is allocated, their assignment will be fixed for all subsequent prescribing episodes during the study period. This ensures consistency of the intervention within individual patients across multiple encounters.

Due to the nature of the intervention, prescribers cannot be blinded to treatment allocation, they will either see the digital nudge or they will not. Patients are not actively involved in the intervention and will not be aware of their allocation. Outcome assessment will be conducted using routinely collected electronic data and can be performed by analysts blinded to group allocation.

The patients randomised into three arms but in reality these are intervention and a control arm which is nuanced.&#x20;



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

**Exclusion criteria**

Age under 18

Pregnancy

**Recruitment**

All inpatient and outpatient encounters prescribed antibiotics with the indication above and without the exclusion.

**Consent**

The intervention in this study involves surfacing clinical data that is already available within the patient's electronic health record specifically, prior microbiology results, antimicrobial sensitivity data, and relevant prescribing guideline information. The nudge does not alter the treatment itself, the prescribing clinician retains full autonomy over the antibiotic selection and all subsequent clinical decisions. In effect, the advisory ensures that information which should already inform prescribing is presented to the clinician at the point of decision-making, supporting best practice rather than introducing a novel therapeutic intervention. The purpose of the study is to evaluate whether this is effective in improving antibiotic prescribing decisions when antimicrobial resistance information is surfaced at the point of care.

On this basis, individual patient consent is not considered necessary for several reasons. First, the intervention is directed at clinician behaviour, how existing information is accessed and displayed, rather than at the patient directly. In routine care, patients would have no awareness of whether their clinician reviewed their microbiology results before prescribing, and the nudge does not change this dynamic.&#x20;

The study will seek approval under the appropriate regulatory framework for the use of patient data without individual consent, and ethical approval will be obtained through the Health Research Authority. The design aligns with the principles of research embedded within a learning health system, where interventions that optimise the use of existing clinical information to improve care quality can be evaluated without requiring individual participant consent, provided appropriate safeguards for data governance and patient confidentiality are maintained.



<br>

#### 6. Intervention <a href="#id-6.-intervention" id="id-6.-intervention"></a>



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

