---
description: Mapping the modelling task on to the team
---

# Who does what?

### Problem statement

The key coordination problem is how to divide responsibility between the _data engineer_ and the _model engineer_ when defining the prediction task. The data engineer will extract and shape hospital EHR data into reliable, versioned tables of antibiotic prescribing and microbiology outcomes, while the model engineer will build a simple first model (for example, logistic regression). The hardest work sits between them: choosing the index event that anchors each prediction, defining the label window and prediction horizon, and specifying which features are allowed before the cut-off time so that leakage is avoided. We will use the language from Label–Segment–Featurize, and implemented this in tested, modular transformations as per the MLOps philosophy. The dataset, features and labels are reproducible across training an serving environments, and the resulting model can be moved back into NHS systems after development offline in a Trusted Research Environment.

We have four roles in the RADIX team.

<table><thead><tr><th width="223.11328125">Role</th><th data-type="users" data-multiple></th><th>Notes</th></tr></thead><tbody><tr><td>Data engineering</td><td><a href="https://app.gitbook.com/u/JESRYdCkWQgzJXbPuwgQECn0C8l1">peien.xie</a></td><td></td></tr><tr><td>Infrastructure engineering</td><td><a href="https://app.gitbook.com/u/FckLx6MPu1SebeqKxwRrXAynaTQ2">paul.j.smith</a><a href="https://app.gitbook.com/u/yjWQBD9q3NecXTXiLeMcluzkEq72">s.cunliffe</a></td><td></td></tr><tr><td>Model engineering</td><td><a href="https://app.gitbook.com/u/x6ldoZDNqWNPbxgjjeSqI55Os5L2">magnus.ross</a></td><td></td></tr><tr><td>Clinical lead</td><td><a href="https://app.gitbook.com/u/79zLhKq06cNsBt7rnzMBb2KgA4b2">akish.luintel</a></td><td></td></tr></tbody></table>

### Design principles

* [MLOps](https://docs.cloud.google.com/architecture/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning) is the discipline of turning a machine learning model into a reliable, auditable, repeatable service. In practice it means: versioning _data, labels, features, code, and models_; automating training/evaluation; enforcing quality gates (tests, audits, monitoring); and making deployment and rollback safe.([Corbin 2023](https://doi.org/10.1093/jamia/ocad114)) \
  For this project, MLOps implies an end-to-end pipeline that can be run deterministically in both NHS and research environments, with clear interfaces between data preparation, feature generation, model training, and serving—so that a “minimal working model” can be promoted, monitored for drift/performance, and iterated without breaking clinical workflow or information governance.
* **Label–Segment–Featurize (L-S-F)**: A useful design pattern for “prediction engineering” in time-stamped relational data.([Kanter 2016](https://doi.org/10.1109/DSAA.2016.54))  The key principle is to explicitly define (1) the _label_ and its time window, (2) the _cutoff time_ at which the prediction is made and the _lead/lag_ that define what historical data is allowed, and (3) the _feature extraction_ restricted to the allowable segment to prevent label leakage. Applied here, L-S-F forces agreement on what the “prescribing event” is (the anchor), how resistance/mismatch is determined relative to that anchor (label window), and what prior history is admissible as predictors (feature window).

<figure><img src="../../../.gitbook/assets/CleanShot 2026-02-02 at 14.44.56@2x (1).png" alt=""><figcaption></figcaption></figure>

* **High level requirements**
  * Clear ownership: each deliverable has a single accountable role.
  * Reproducibility: datasets and models are versioned and re-runnable.
  * No leakage: features must only use information available at prediction time.
  * IG by design: identifiable work stays on NHS infrastructure; research work stays in the DSH.
  * Deployment path: the trained model can be applied in NHS or HSL infrastructure  with the same feature contract.

### Implementation

#### Overview

* The **data engineer** owns the data product (event definitions, labels, features, dataset versioning).
* The **model engineer** owns the modelling product (training/evaluation code, leakage control, packaging for deployment).
* The **clinical lead** owns clinical validity & safety (definitions, exclusions, outcome validity, evaluation framing).
* The **infrastructure engineer** owns platform & delivery mechanics (environments, CI/CD, orchestration, security boundaries).

### Data versus Model engineering

{% hint style="info" %}
The rule of thumb is that data features are _facts_, and model features are _representations_ of those facts.&#x20;

* **Data features** are time-stamped, clinically interpretable, reproducible facts at the right time granularity ("as-of" $$t_{presciption}$$ ), with stable definitions and data-quality tests.\
  &#xNAN;_&#x49;f you can say “a clinician could recognise this field as a real-world thing” → it’s probably a data feature._
* **Model features** decide how such facts are encoded and transformed for learning and inference (normalisation, interactions, binning, embeddings, missingness strategy, calibration-oriented transforms), and own the code that makes training/inference identical.\
  &#xNAN;_&#x49;f you can say “this is a transformation to help the model” → it’s probably a model feature._
{% endhint %}

This means that **data engineering** will build a data model with _one row per prediction event_ (e.g. antibiotic start time). That model will

* present columns of atomic facts with clear "as-of" $$t_{presciption}$$  semantics, without leakage, with clear units, and stable semantic meaning and interpretation
* this clinical ML feature store with _one row per prediction event_ is likely to be built from either [Camino](../../../foundations/camino-frances.md) (our modular pipeline that maintains tables based on their underlying concepts derived in turn from the UCLH enterprise data warehouse), or the HSL [Radix FHIR store](../../../foundations/camino-helix.md).&#x20;

And **model engineering** will build additional columns within the model pipeline but would not build _fresh_ tables or re-organise the "as-of" $$t_{presciption}$$ data structure.

#### Heuristics for data versus model engineering decisions &#x20;

1. **Would you want this displayed in a clinical dashboard?**\
   For example, who builds the "Number of antibiotic courses in last 90 days" feature (anchored at "as-of" $$t_{presciption}$$ )?  Here you'd argue this would be of interest to a clinical consumer so this is a data feature. Conversely, normalising or log transform the same number would be a model feature.
2. **Does the feature require&#x20;**_**fitting**_**&#x20;parameters?**&#x20;
   * Model features: StandardScaler mean/SD, target encoding priors, PCA loadings, spline knots, calibration maps
   * Data features: Simple deterministic aggregations (“count”, “max”, “days since”)
3. **Is the feature "semantic" or "algorithmic"?**\
   This is similar to (1) above.
   * Semantic feature (has meaning independent of algorithm): comorbidity count, prior resistant isolate, creatinine latest, ward, age → _data features_
   * Model features: Algorithmic feature (meaning depends on algorithm): one-hot encoding choices, missingness indicators, interaction terms, monotonic binning, learned embeddings → _model features_
4. **A promotion rule - from model to data feature**\
   Moving a transformation upstream from model to data only if:
   * it improves _multiple_ models/use-cases,
   * it’s deterministic and stable,
   * it has clinical meaning or operational value,
   * it can be tested with audits,
   * it doesn’t embed training-set statistics.
5. **Default to a&#x20;**_**data feature**_**&#x20;if you're not sure**

#### Summary

Effectively we are building two products - a clinical feature store _and_ a many models and their design matrices

1. Clinical ML Feature Store (facts)
   1. Relationships
      1. Owned by the data engineer
      2. Reviewed by the clinical lead
      3. Consumed by the model engineer
   2. Layers
      1. **Bronze**: raw extracts from Epic Clarity/Caboodle mapped to standard fields&#x20;
      2. **Silver**: [Camino](../../../foundations/camino-frances.md) - cleaned, deduplicated, time-aligned tables (meds, cultures, encounters)
      3. **Gold:** the event-anchored fact table: ⁠features and labels "as-of" $$t_{presciption}$$&#x20;
   3. Never "_saved_" because it represents _current_ truth
2. Model Design Matrix (representations)
   1. Relationships
      1. Owned by the model engineer
      2. Reviewed by the clinical lead
   2. Turns ⁠features "as-of" $$t_{presciption}$$  into
      1. encoded matrix \\(X\\) (categorical encoding, scaling)
      2. derived terms (interactions, non-linear transforms)
      3. missingness handling as implemented logic
   3. Saved as a versioned artefacts within M&#x4C;_&#x66;low_ or similar&#x20;

### Examples

* Data features
  * ⁠age\_at\_event, ⁠sex
  * ⁠drug\_name, ⁠route, ⁠dose, ⁠indication\_code (as recorded)
  * ⁠organism\_last\_12m: last cultured organism category (if known before \\(t\_c\\))
  * ⁠prior\_resistance\_to\_drug\_2y: count of prior non-susceptible results
  * ⁠days\_since\_last\_antibiotic
  * ⁠num\_hospital\_admissions\_1y
  * ⁠latest\_creatinine\_value\_before\_tc + ⁠timestamp\_of\_creatinine
* Model features
  * One-hot / target encoding of ⁠drug\_name, ⁠organism\_last\_12m
  * ⁠missing\_creatinine\_indicator
  * ⁠log1p(num\_hospital\_admissions\_1y)
  * Interaction terms: ⁠drug\_class × prior\_resistance
  * Binning: ⁠age\_group chosen for performance/robustness
  * Calibration mapping and threshold selection
* Borderline cases
  * age\_group
    * If it’s for reporting/clinical interpretability and fixed upfront → a _data feature_
    * If it’s tuned/changed during modelling → a _model feature_
