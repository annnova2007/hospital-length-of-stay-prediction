# Dataset

The dataset used in this project is the New York State SPARCS Hospital Inpatient Discharges dataset.

## Source

Official dataset:
[New York State Health Data](https://health.data.ny.gov/)

## Dataset Description

The dataset contains hospital inpatient discharge records with demographic,
diagnosis, admission, facility, and other hospital-related information.

## Target Variable

**Length of Stay** — the number of days a patient stayed in the hospital.

The original dataset represents stays of 120 days or more as `120+`.
For modeling, `120+` was converted to `120`.

## Dataset Size

- Rows: 2,196,737
- Columns: 33

## Note

The original dataset is not included in this repository because of its large size.
Please download the dataset directly from the official source above.
