---
description: Machine Learning for Health 2025 Conference Paper
---

# ML4H 2025 paper

{% hint style="info" %}
Please see [OpenReview.net](https://openreview.net/forum?id=j8wsqyowid) for the paper including the PDF&#x20;
{% endhint %}

Intravenous (IV) antimicrobial therapy often continues after an oral alternative would be safe, harming patients and increasing costs. The key decision—when to switch from IV to oral (IVOS)—is complex.

Past machine-learning approaches are trained on labels constructed from prescription records that indicate when switches actually happened, not when they were first clinically appropriate; they therefore reproduce delays and suboptimal practice.

We take a different approach, forecasting each patient’s physiological state using a probabilistic neural process and applying established IVOS criteria to those forecasts to estimate switch-readiness. The system ranks patients currently on IV therapy by the probability they will meet all criteria within the next 12 hours, highlighting candidates for clinician review while keeping the final decision with the prescriber.

By anchoring recommendations to clinical criteria rather than past actions, the tool targets a reduction in unnecessary IV days instead of reinforcing the status quo.<br>

<figure><img src="../../.gitbook/assets/Workshop diagram.png" alt=""><figcaption></figcaption></figure>
