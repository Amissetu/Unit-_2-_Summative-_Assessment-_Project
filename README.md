# Insurance Charges Analysis

## Overview

This project prepares insurance customer data for analysis and explores the
factors associated with medical insurance charges.

## Input

- [`raw_data/insurance.csv`](raw_data/insurance.csv) — raw insurance records
  with age, sex, BMI, children, smoking status, region, and charges.

## Data preparation

The transformation workflow is documented in
[`jupyter_notebooks/Transformed data.ipynb`](jupyter_notebooks/Transformed%20data.ipynb).
It standardises column names and categorical values, removes duplicate rows,
fills missing numeric values with the median and categorical values with the
mode (or `Unknown` if no mode is available), and one-hot encodes categorical
variables.

The workflow also creates BMI categories using standard thresholds:
underweight (BMI < 18.5), normal (18.5–<25), overweight (25–<30), and obese
(BMI >= 30). It adds `bmi_squared` as an additional numeric feature.

## Output

- [`Cleaned_data.csv`](Cleaned_data.csv) — cleaned, encoded, analysis-ready
  data. It contains 1,337 rows and 17 columns.
- [Insurance Charges Insights Tableau dashboard](https://public.tableau.com/views/InsuranceChargesanalysisDashboardTableau/InsuranceChargesInsightsStory1?:showVizHome=no)
  — interactive visual exploration of insurance charges.

Load the cleaned data with pandas:

```python
import pandas as pd

df = pd.read_csv("Cleaned_data.csv")
```

## Cleaned data columns

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

## Credits

- Insurance data: [`raw_data/insurance.csv`](raw_data/insurance.csv).
- Data cleaning and feature engineering: this project's transformation is in the Jupyter notebook.
- Learning resources: Code Institute LMS, consulted throughout the project.
- Explanations and coding support: GitHub Copilot, used to clarify concepts,
  provide additional detail, and assist with code.
- Web searches: Google Search, used to find information and supporting
  resources.
- Tableau Public: used to create an interactive dashboard that makes the
  insurance-charge patterns easier to explore and communicate. The dashboard
  includes descriptive statistics, correlation and geographic analyses,
  interactive filters, a predictive insurance cost calculator, and a
  storytelling view that connects the findings into a clear narrative.
## Tableau Dashboard

- you can find the interrutive Dashboard here: [Insurance Charges Insights on Tableau Public](https://public.tableau.com/views/InsuranceChargesanalysisDashboardTableau/InsuranceChargesInsightsStory1?:showVizHome=no)

View the interactive dashboard here:

[Insurance Charges Insights Dashboard](https://public.tableau.com/views/InsuranceChargesanalysisDashboardTableau/InsuranceChargesInsightsStory1?:showVizHome=no)

### Features

- Descriptive Statistics
- Correlation Analysis
- Geographic Analysis
- Interactive Filters
- Predictive Insurance Cost Calculator
- Storytelling Dashboard


