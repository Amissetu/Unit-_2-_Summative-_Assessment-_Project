



![Insurance charges image](Insurance_charges_image.png)

# Insurance Charges Analysis

This project explores how customer characteristics relate to medical
insurance charges. It includes the original dataset, a data-cleaning notebook,
a cleaned dataset, and an interactive Tableau dashboard.

## Dataset

The raw data is from the Kaggle
[Healthcare Insurance dataset](https://www.kaggle.com/datasets/willianoliveiragibin/healthcare-insurance).
It contains age, sex, BMI, number of children, smoking status, region, and
individual insurance charges.

- Raw data: [`raw_data/insurance.csv`](raw_data/insurance.csv)
- Cleaned data: [`Insurance_Cleaned_Data.csv`](Insurance_Cleaned_Data.csv)
- Preparation steps: [`jupyter_notebooks/Transformed data.ipynb`](jupyter_notebooks/Transformed%20data.ipynb)

The cleaned dataset has 1,337 rows and 17 columns. The notebook removes
duplicate records, handles missing values, standardises categories, creates
BMI categories and a squared-BMI feature, and one-hot encodes categorical
fields.

## Project questions

- Do insurance charges differ between smokers and non-smokers?
- How do charges vary with age, BMI, and region?

The analysis uses data-quality checks, descriptive comparisons, and
visualisations to explore these questions. These are associations, not proof
of cause and effect. The dataset is limited in size and may not represent all
insurance customers.

## Machine learning prototype

[`jupyter_notebooks/prototyps.ipynb`](jupyter_notebooks/prototyps.ipynb)
develops an **Interactive Insurance Cost Prediction Tool** concept and
implements its regression model. Since `charges` is a continuous value, the
notebook compares Scikit-learn Linear Regression and Random Forest models
against a median-prediction baseline. All three use the same held-out test
split and are evaluated with mean absolute error (MAE), root mean squared
error (RMSE), and R-squared:

The main approaches differ by the question they answer: **regression**
predicts a numeric value, **classification** predicts a category, and
**clustering** groups records without a pre-labelled target. Regression is
appropriate here because insurance `charges` are continuous amounts. Linear
Regression was included as a simple, interpretable benchmark for how input
features relate to charges; the Random Forest regressor was compared because
it can capture more complex, non-linear patterns. Classification would
require turning charges into categories and lose the exact cost information,
while clustering would not directly predict a charge.

| Model | MAE | RMSE | R-squared |
| --- | ---: | ---: | ---: |
| Linear Regression | $4,177 | $5,956 | 0.81 |
| Random Forest | $2,456 | $4,452 | 0.89 |
| Median baseline | $9,294 | $14,442 | -0.14 |

The proposed client-facing tool would accept age, BMI, number of children,
sex, smoking status, and region, then show an illustrative annual estimate
and support what-if comparisons, such as changing smoking status while
keeping other inputs fixed. The notebook demonstrates a sample profile and
model, but does not yet implement an interactive user interface. Its
estimate-plus/minus-MAE display is a rough indication of average test error,
not a personalized statistical prediction interval. Feature importance and
scenario differences describe patterns in this dataset and do not establish
causes. Predictions are not quotes, medical advice, or underwriting
decisions.

## Dashboard

![Tableau dashboard screenshot](<Tabeau Dashbord Screenshot.png>)

The [Tableau Public dashboard](https://public.tableau.com/views/InsuranceChargesanalysisDashboardTableau/InsuranceChargesInsightsStory1?:showVizHome=no)
includes descriptive statistics, correlation and geographic analysis,
interactive filters, a cost calculator, and a storytelling view. Treat the
calculator as an illustration, not a validated insurance quote or model.

### Storytelling view screenshots

![Age influences insurance charges](<Age influences insurance charges.png>)

![BMI and insurance charges](<BMI and Inurance charges.png>)

![Regional variation in insurance cost](<Regional Variation in insurance cost.png>)

![Smoking is a major driver](<Smoking is a Major driver.png>)

## Tools

- **Pandas and NumPy** for data cleaning and feature creation.
- **Scikit-learn** for preprocessing, regression models, and evaluation.
- **Jupyter Notebook** for data preparation and machine-learning documentation.
- **Tableau Public** for interactive visualisation.
- **Streamlit** is a possible option for building the proposed interactive
  estimator; a Streamlit app is not currently included in this project.

## Future development

If I had more time, I would develop a Streamlit-based Insurance Cost
Estimator so clients could enter personal information and instantly receive
an estimated healthcare insurance charge. The estimate would be for
exploration only, not an insurance quote or underwriting decision.

## Credits and limitations

- Title image: screenshot from Microsoft 365 Copilot.
- Dataset: [Kaggle Healthcare Insurance dataset](https://www.kaggle.com/datasets/willianoliveiragibin/healthcare-insurance).
- README format: [Code Institute Data Analysis README template](https://github.com/Code-Institute-Solutions/da-README-template.git).
- GitHub Copilot and Microsoft 365 Copilot were used for AI assistance. The Code Institute LMS was used for learning.

Confirm the dataset's licence and cite it appropriately before redistributing

## Acknowledgements

Thank you to the Code Institute instructors and learning community for their
guidance and learning resources throughout this project. Emma Lamont's
Google quick note on the project instructions was also helpful.
