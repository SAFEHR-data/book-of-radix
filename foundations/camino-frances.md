---
description: A UCLH data pipeline for anti-microbial stewardship and decision making
---

# Camino Frances

## Camino

Camino is a data extraction tool for retrieving antibiotic prescribing and resistance data from Epic's Clarity data warehouse at UCLH. **Camino is built to serve the RADIX translational research project, other usage of the data may be possible but is unsupported.**

Camino is comprised of three main components:

* **Passport**: Extracts data from Clarity into Parquet staging files.
* **Pilgrimage**: Ingests data from Parquet staging files into a [DuckLake](https://ducklake.select/)
* **Planning**: Camino orchestration and scheduling with Prefect.

### Data Model

The dataset is modelled around the concept of a _prescribing encounter_, i.e. an inpatient hospital encounter during which a patient was prescribed an antibiotic with additional dimensions on the patient, the encounter, orders placed and results received during the encounter.

The dataset is constructed from Epic's [Clarity](https://datahandbook.epic.com/ClarityDictionary) data warehouse via the Camino passport[^1] and Pilgrimage.

Prescribing encounters from **2020-01-01** onwards are included in the _full_ dataset although the "historical" tables go back as far as 2019-04-01.

{% hint style="info" %}
We maintain a separate and **private** [Book of Camino](https://camino.antibiotics.help/) because the code and content is intertwined with Epic's intellectual property.&#x20;

Please get in touch if you think you should have access.&#x20;
{% endhint %}

[^1]: This 'passport' is an internal passport and **not** related to the Antibiotic Passport concept being developed in the _Via Francigena_
