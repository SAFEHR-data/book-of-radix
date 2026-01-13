# Overview

## Camino

Camino is a data extraction tool for retrieving antibiotic prescribing and resistance data from Epic's Clarity data warehouse at UCLH. **Camino is built to serve the RADIX translational research project, other usage of the data may be possible but is unsupported.**

Camino is comprised of three main components:

* **Passport**: Extracts data from Clarity into Parquet staging files.
* **Pilgrimage**: Ingests data from Parquet staging files into a [DuckLake](https://ducklake.select/)
* **Planning**: Camino orchestration and scheduling with Prefect.

### Data Model

The dataset is modelled around the concept of a _prescribing encounter_, i.e. an inpatient hospital encounter during which a patient was prescribed an antibiotic with additional dimensions on the patient, the encounter, orders placed and results received during the encounter.

The dataset is constructed from [Clarity](https://datahandbook.epic.com/ClarityDictionary) via the Camino passport and Pilgrimage.

Prescribing encounters from **2020-01-01** onwards are included in the _full_ dataset although the "historical" tables go back as far as 2019-04-01.

See the data model docs for a full description of the tables and columns in the dataset.
