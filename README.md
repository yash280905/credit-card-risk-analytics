# Credit Risk Modelling & Analysis

## Overview
An end-to-end educational project exploring historical credit-card default behaviour and comparing two binary classification models. The workflow includes data quality checks, exploratory analysis, statistical tests, model evaluation, feature importance, probability calibration review, and threshold analysis.

## Business question
Can customer repayment behaviour and related credit-card characteristics help distinguish customers who default on their next payment from those who do not?

## Dataset
**Default of Credit Card Clients** — UCI Machine Learning Repository: https://archive.ics.uci.edu/dataset/350/defaultofcreditcardclients

The dataset contains historical consumer credit-card information. The target is `default_payment_next_month` (`1` = default, `0` = no default). Download the dataset from UCI and place the extracted Excel file at:

`data/raw/default of credit card clients.xls`

The raw dataset is not included in this repository.

## Tools
- Python, Jupyter Notebook
- pandas, NumPy
- Matplotlib, Seaborn
- SciPy
- scikit-learn

## Workflow
1. Data loading and data-quality checks
2. Exploratory data analysis and customer-segment comparisons
3. Statistical association tests and correlation analysis
4. Stratified train/test split
5. Logistic Regression and Random Forest pipelines
6. Evaluation with precision, recall, F1-score, ROC-AUC, and average precision
7. Feature-importance and calibration review
8. Random Forest classification-threshold analysis

## Model results
The recorded held-out test-set results at a classification threshold of 0.50 were:

| Metric | Logistic Regression | Random Forest |
|---|---:|---:|
| Accuracy | 67.97% | 78.43% |
| Precision | 36.72% | 51.10% |
| Recall | 62.02% | 57.65% |
| F1-score | 46.13% | 54.18% |
| ROC-AUC | 0.7081 | 0.7722 |
| Average precision | 0.4904 | 0.5512 |

On this split, Random Forest had higher accuracy, precision, F1-score, ROC-AUC, and average precision; Logistic Regression had higher recall at threshold 0.50. The preferred model depends on the relative cost of missed defaults and false-positive flags. These results are specific to this split and should not be treated as a guarantee of future performance.

## Threshold analysis
The exploratory threshold table showed that 0.50 had the highest F1-score among the thresholds tested. For a rigorous evaluation, threshold selection should be done on validation data, followed by one final evaluation on an untouched test set. Do not choose a threshold based on test-set results for deployment.

## Run the notebooks
Run from the project root or open the notebooks in Jupyter. The notebooks expect the dataset at the path shown above.

1. `notebooks/01_data_quality_and_eda.ipynb`
2. `notebooks/02_statistical_analysis.ipynb`
3. `notebooks/03_credit_risk_model.ipynb`

Install dependencies:

```bash
pip install -r requirements.txt
```

## Limitations and responsible use
- This is a consumer credit-card dataset, not a corporate or institutional lending dataset.
- Statistical association does not imply causation.
- Class weighting can affect the interpretation and calibration of predicted probabilities.
- Model performance and calibration can change across populations and over time.
- These models are for educational/portfolio use only and are not production-ready lending decision systems.

## Repository contents
- `notebooks/`: analysis, statistical testing, and model evaluation
- `reports/`: selected summary outputs
- `data/raw/`: local dataset location (not committed)
- `data/processed/`: local generated files (not committed)

## Disclaimer
For educational and portfolio purposes only. Do not use these outputs as the sole basis for real-world credit decisions.
