---
description: As per the UCLH JRO template headings
---

# JRO protocol

{% hint style="warning" %}
See [UCL/UCLH Interventional studies protocol template](https://www.ucl.ac.uk/joint-research-office/sites/joint_research_office/files/jro_interventional_protocol_template.docx) (section number matches the template)

Use this document to manage version control and print or convert to a word document directly from here when ready to submit
{% endhint %}

### 1. Introduction

{% hint style="warning" %}
Leave for now: will be written after Background and Rationale complete
{% endhint %}

{% hint style="info" %}
**Via JRO:** Overview of the study; it should be sufficient to guide the reader to the main purpose of the study, how it will be conducted, on which population(s) and its expected benefits. It should say how the results of the study would benefit in terms of clinical practice, policy or the NHS as whole. The introduction may include a study flowchart (recommended: allows users of the document to follow the participant and study pathway with ease, e.g. via a Gantt chart or timeline of activity), and should detail whether this project is being conducted in relation to an academic qualification (a student project), or is related to any previous research sponsored by UCL.
{% endhint %}

### 2. Background and Rationale

#### Antimicrobial Resistance

{% include "../../../.gitbook/includes/bg-antimicrobial-resistance-a....md" %}

#### The Antibiotic Prescribing Problem

{% include "../../../.gitbook/includes/bg-the-antibiotic-prescribing-....md" %}

#### Community Acquired Pneumonia

Community-acquired pneumonia (CAP) accounts for 83,000 hospital admissions and 29,000 deaths in England annually (Guest J and Morris A, 1997; Daniel et al, 2016), making it one of the most significant infectious indications for antibiotic treatment among the 1.5 million NHS inpatients who require antibiotics for major infections each year.

Guidelines recommend standard-spectrum (SS) antibiotics for mild-to-moderate CAP. In practice, clinicians follow this recommendation only 58% of the time (Daniel et al, 2016), frequently substituting extended-spectrum (ES) agents. In a subset of patients, ES agents confer no individual benefit whilst increasing the risk of side effects and contributing to AMR (Wei et al, 2024; Gerber et al, 2017).

The consequences are measurable: in England in 2024, 66,730 people developed antibiotic- resistant infections, with 2,640 directly attributable deaths. The NHS has set a target of 70% SS antibiotic use in first-line prescriptions by 2029, in line with the UK National Action Plan on AMR. Achieving this will require interventions that both improve guideline adherence and generate evidence on the clinical circumstances in which deviation is genuinely warranted.

#### Dilemma of empirical prescribing

{% include "../../../.gitbook/includes/dilemma-of-empirical-prescribing.md" %}

#### **The Electronic Health Record Opportunity**

{% include "../../../.gitbook/includes/bg-the-ehr-opportunity-for-ant....md" %}

#### Study Overview

{% include "../../../.gitbook/includes/study-overview.md" %}

### Research Question

In adult patients admitted to secondary care with community-acquired pneumonia, does an electronic nudge embedded into the antibiotic prescribing workflow increase guideline-concordant prescribing safely and effectively?

{% @linear/embed url="https://linear.app/safehr/issue/RAD-249" issueId="RAD-249" %}

{% @linear/embed url="https://linear.app/safehr/issue/RAD-248" issueId="RAD-248" %}

### 3. Objectives and outcome measures

#### 3. Objectives and Outcome Measures

**Primary Objective**

To evaluate the effectiveness of a clinically integrated electronic stewardship prompt in increasing guideline-concordant antibiotic prescribing in patients admitted to secondary care with community-acquired pneumonia.

**Secondary Objectives**

1. To evaluate the safety of the electronic stewardship prompt.
2. To evaluate the effect of the electronic stewardship prompt on antibiotic stewardship.

**Outcome Measures**

**Effectiveness**

1. Proportion of guideline-concordant antibiotic prescriptions in the stewardship prompt versus standard care arms at 24 hours after initial antibiotic prescribing.

**Safety**

1. All-cause in-hospital mortality and 90-day mortality.
2. Length of hospital stay.
3. Escalation to level 2 or level 3 care.
4. Readmission to hospital within 30 days of discharge.

_The study is not powered to detect differences in the safety outcomes listed above. These will be monitored as safety signals._

**Stewardship**

1. Antibiotic consumption measured as Defined Daily Doses (DDD) per admission, overall and stratified by AWaRe category and indication.
2. Time to intravenous-to-oral antibiotic switch.
3. Days of antibiotic spectrum consumption per admission and per indication. \[TODO: confirm metric — DASI or equivalent validated spectrum score]
4. Days of therapy per admission.
5. Proportion of antibiotic switches from the initial prescription at 24, 48, and 72 hours.
6. Proportion of empirical antibiotic escalations — defined as a change in antibiotic treatment independent of new microbiological evidence.
7. Proportion of patients receiving intravenous versus oral antibiotic courses.

**Safety Monitoring: Antimicrobial Resistance Signals**

_The following outcomes will be monitored as safety signals. The study is not powered to detect differences between arms._

1. Rates of _Clostridioides difficile_ infection.
2. Rates of extended-spectrum beta-lactamase (ESBL)-producing isolates.
3. Rates of carbapenem-resistant organism (CRO) isolates.
4. Rates of ciprofloxacin-resistant isolates.
5. Rates of vancomycin-resistant enterococci (VRE).

#### 4. Trial Design

Inglés-Guidelines is a single-centre, randomised controlled trial with parallel assignment, digitally integrated within the electronic patient record (EPR) at University College London Hospitals NHS Foundation Trust (UCLH).

Adult patients admitted to secondary care with community-acquired pneumonia who receive a non-guideline-concordant antibiotic prescription will be randomised between the stewardship prompt arm and standard care. All study data will be extracted from the EPR. Participation requires no additional testing, clinical appointments, or follow-up beyond routine care.

**Study Workflow**

The patient enters the study at the point of antibiotic order placement by the treating clinician. The clinician may be prescribing from the emergency department, an outpatient setting, or an inpatient ward. In all cases, the antibiotic order must be the first for the current encounter.

The prescribing sequence proceeds as follows:

1. The clinician selects the desired antibiotic from the orders tab (e.g. co-amoxiclav).
2. The clinician enters antibiotic indication data at a mandated step within the order window, specifying body system and indication (e.g. Respiratory, Community-Acquired Pneumonia, Mild). Dose, route, frequency, and duration are entered. The order is accepted and queued for signature.
3. On signing the order, the EPR silently evaluates a series of eligibility criteria to determine whether the stewardship prompt should be displayed (see below).

**Eligibility Screening at the Point of Prescribing**

Signing the antibiotic order triggers automated, silent evaluation of the following criteria in sequence:

1. **First antibiotic order**: Is this the first antibiotic order for the current patient encounter?
2. **Guideline discordance**: Is there discordance between the selected antibiotic, the entered indication, and the UCLH clinical guideline recommendation?
3. **Prior randomisation**: Has the patient already been randomised within this encounter?
4. **Allergy to guideline-concordant antibiotic**: Does the patient have a documented allergy to the guideline-recommended antibiotic?

A patient is eligible for randomisation only if criteria 1, 2, and 3 are met, and criterion 4 is not. If the patient has a documented allergy to the guideline-concordant antibiotic, the patient is not enrolled.

If all eligibility criteria are satisfied, the patient is randomised 1:1 to the stewardship prompt arm or standard care (no prompt).

**The Stewardship Prompt**

Patients randomised to the intervention arm trigger display of an electronic stewardship prompt to the prescribing clinician at the point of order signing. The prompt reads:

> _You are prescribing \[antibiotic X] for \[indication Y]._ _UCLH guidelines recommend \[antibiotic Z] for \[indication Y]._ _Select below to switch to \[antibiotic Z], or provide a clinical justification for deviation from the guideline:_
>
> 1. _Requirement for extended-spectrum agent given diagnostic uncertainty_&#x20;
> 2. _Requirement for extended-spectrum agent given additional clinical risk_
> 3. _Extended-spectrum agent use approved by Microbiology or Infectious Diseases_&#x20;
> 4. _Prescription indication is incorrectly recorded; guideline therefore not applicable_
> 5. _Other (free text comment)_

\[TODO: confirm whether one-click antibiotic substitution is technically achievable within Epic Best Practice Advisory architecture, or whether the clinician must manually place a new order.]

Patients randomised to standard care receive no prompt. The prescribing clinician proceeds with the original antibiotic order without interruption.

### 5. Sampling methods

#### Inclusion criteria

All patients over the age of 18 who are prescribed antibiotics for the following indications:

1. Pneumonia (Community, mild , CURB-65 0-1)
2. Pneumonia (Community, moderate, CURB-65 2)
3. Pneumonia (Community, severe, CURB-65 >/=3)

Inclusion criteria are derived automatically from patients receiving an antibiotic order where the clinician enters the above indication data at a mandated step within the prescribing process.&#x20;

#### Exclusion criteria

Pregnant women

Age <18

#### Recruitment

Patients will be automatically recruited based on receipt of an antibiotic prescription meeting the above eligibility criteria. &#x20;

#### Consent

This study seeks to ascertain the effectiveness and safety of a digital prescribing intervention to encourage compliance with an existing standard of care.  This represents a quality improvement evaluation and does not seek to generate generalisable data as to the effectiveness of the proposed intervention in other contexts.  As such, it is comparable to a similar non-digital intervention such as placing a poster of current guidelines in clinical areas for the same aim.  The use of randomisation in this context is intended to deliver a more rigorous evaluation of the effectiveness of the proposed intervention than existing methods current used in quality improvement methodology e.g. before-after analysis. &#x20;

### 6. Intervention

### 7. Trial procedures

### 8. Finance and supply of equipment

### 9. Data management

### 10. Statistical considerations



### 11. Assessment and management of risk

### 12. Recording and reporting adverse events

### 13. Oversight committees

### 14. Regulatory review and patient and public involvement

#### Regulatory review

#### Peer review

#### Patient and public involvement

### 15. Monitoring and auditing

### 16. Training

### 17. Insurance and indemnity

### 18. Record keeping and archiving

### 19. Intellectual property

### 20. Publication and dissemination

### 21. References

### 22. Appendices

