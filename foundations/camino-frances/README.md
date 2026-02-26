---
description: A UCLH data pipeline for anti-microbial stewardship and decision making
---

# Camino Frances

## Camino

Camino is a data extraction tool for retrieving antibiotic prescribing and resistance data from Epic's Clarity data warehouse at UCLH. **Camino is built to serve the RADIX translational research project, other usage of the data may be possible but is unsupported.**

Camino is comprised of four main components:

* **Passport**: Extracts data from Clarity into Parquet staging files.
* **Pilgrimage**: Ingests data from Parquet staging files into a [DuckLake](https://ducklake.select/)
* **Planning**: Camino orchestration and scheduling with Prefect.
* **Portal**: For researchers: [marimo](https://marimo.io/), [RStudio](https://posit.co/products/open-source/rstudio-server/) and \[SuperSet] instances with access to the Camino DuckLake data.

### Data Model

The dataset is modelled around the concept of a _prescribing encounter_, i.e. an inpatient hospital encounter during which a patient was prescribed an antibiotic with additional dimensions on the patient, the encounter, orders placed and results received during the encounter.

The dataset is constructed from Epic's [Clarity](https://datahandbook.epic.com/ClarityDictionary) data warehouse via the Camino passport[^1] and Pilgrimage.

Prescribing encounters from **2020-01-01** onwards are included in the _full_ dataset although the "historical" tables go back as far as 2019-04-01.

### Camino Portal

{% hint style="warning" %}
These instructions are for researchers in the RADIX translational research project with access to the UCLH network.
{% endhint %}

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-cover data-type="image">Cover image</th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td>How to use Marimo for Pythonistas</td><td></td><td data-object-fit="contain"><a href="https://raw.githubusercontent.com/marimo-team/marimo/main/docs/_static/marimo-logotype-thick.svg">https://raw.githubusercontent.com/marimo-team/marimo/main/docs/_static/marimo-logotype-thick.svg</a></td><td><a href="marimo.md">marimo.md</a></td></tr><tr><td>RStudio</td><td><a data-footnote-ref href="#user-content-fn-2">Coming soon!</a></td><td data-object-fit="contain"><a href="https://upload.wikimedia.org/wikipedia/commons/d/d0/RStudio_logo_flat.svg">https://upload.wikimedia.org/wikipedia/commons/d/d0/RStudio_logo_flat.svg</a></td><td><a href="/broken/pages/u9v8NBXlWa6eAWeFBeTv">Broken link</a></td></tr><tr><td>SuperSet</td><td>Coming soon!</td><td data-object-fit="contain"><a href="https://camo.githubusercontent.com/dc551298736c4cc5f9b23512ef7ca67e6a9304be4d2e06a0d3ff09b6491adb9b/68747470733a2f2f73757065727365742e6170616368652e6f72672f696d672f73757065727365742d6c6f676f2d686f72697a2d6170616368652e737667">https://camo.githubusercontent.com/dc551298736c4cc5f9b23512ef7ca67e6a9304be4d2e06a0d3ff09b6491adb9b/68747470733a2f2f73757065727365742e6170616368652e6f72672f696d672f73757065727365742d6c6f676f2d686f72697a2d6170616368652e737667</a></td><td></td></tr></tbody></table>

### Camino core: Passport, Pilgrimage and Planning

{% hint style="info" %}
We maintain a separate and **private** [Book of Camino](https://camino.antibiotics.help/) because the code and content for Passport, and Pilgramage is intertwined with Epic's intellectual property.&#x20;

Please get in touch if you think you should have access.&#x20;
{% endhint %}

[^1]: This 'passport' is an internal passport and **not** related to the Antibiotic Passport concept being developed in the _Via Francigena_

[^2]: 
