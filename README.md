# Cleaned Insurance Dataset

## Overview

`Cleaned_data.csv` is the analysis-ready version of the insurance dataset from
`raw_data/insurance.csv`. It contains 1,337 records and 17 columns after
cleaning and feature engineering.

## Data preparation

The transformation workflow is documented in
[`jupyter_notebooks/Transformed data.ipynb`](jupyter_notebooks/Transformed%20data.ipynb).
It:

- standardises column names and trims whitespace from categorical values;
- removes duplicate rows;
- fills missing numeric values with each column's median and missing
  categorical values with the most frequent value (or `Unknown` if no mode is
  available);
- one-hot encodes `sex`, `smoker`, `region`, and BMI category, using integer
  `0`/`1` indicators;
- adds `bmi_category` indicators using these ranges: underweight (BMI < 18.5),
  normal (18.5–<25), overweight (25–<30), and obese (BMI >= 30);
- adds `bmi_squared`, the square of the original BMI value.

## Columns

| Column(s) | Description |
| --- | --- |
| `age` | Age in years |
| `bmi` | Body mass index |
| `children` | Number of children covered by the insurance |
| `charges` | Individual medical insurance charges |
| `bmi_squared` | BMI multiplied by itself |
| `sex_female`, `sex_male` | One-hot encoded sex |
| `smoker_no`, `smoker_yes` | One-hot encoded smoking status |
| `region_*` | One-hot encoded geographic region |
| `bmi_category_*` | One-hot encoded BMI category |

## Use

Load the CSV with pandas:

```python
import pandas as pd

df = pd.read_csv("Cleaned_data.csv")
```

The target/amount column is `charges`. The categorical source fields are
represented by indicator columns in the cleaned file.
