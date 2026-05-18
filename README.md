# Credit Risk Prediction Using Machine Learning

## Project Overview
This project focuses on predicting whether a credit card customer is likely to default on payment in the next month. The objective is to use machine learning to identify risky customers based on demographic information, credit limit, billing history, repayment history, and payment behavior.

This is a binary classification problem where:

- `0` = customer is not expected to default
- `1` = customer is expected to default

The project follows a complete machine learning workflow including data loading, cleaning, exploratory data analysis, model training, evaluation, and interpretation of results.

---

## Problem Statement
Financial institutions face significant risk when customers fail to repay their credit obligations. The goal of this project is to build a predictive model that can help identify customers with a higher probability of default.

By analyzing historical customer data, this project attempts to answer the question:

**Can we predict whether a credit card client will default next month based on their financial and repayment history?**

---

## Dataset
The dataset used in this project is:

- **default of credit card clients.xls**

It contains information such as:

- Credit limit
- Gender
- Education
- Marital status
- Age
- Repayment history (`PAY_0` to `PAY_6`)
- Bill statement amounts (`BILL_AMT1` to `BILL_AMT6`)
- Previous payment amounts (`PAY_AMT1` to `PAY_AMT6`)
- Target column: `default payment next month`

---

## Project Workflow

### 1. Data Loading and Understanding
Notebook: `01_load_and_understand.ipynb`

In this step:
- the raw Excel dataset was loaded
- the header issue was corrected
- the shape of the dataset was checked
- column names were reviewed
- the initial structure of the data was understood

### 2. Data Cleaning
Notebook: `02_data_cleaning.ipynb`

In this step:
- the target column was renamed to `default_payment_next_month`
- the `ID` column was removed
- missing values and duplicate rows were checked
- invalid values in `EDUCATION` and `MARRIAGE` were cleaned
- the cleaned dataset was saved as `credit_default_clean.csv`

### 3. Exploratory Data Analysis (EDA)
Notebook: `03_eda.ipynb`

In this step:
- summary statistics were generated
- target class distribution was analyzed
- distributions of `AGE`, `LIMIT_BAL`, `SEX`, `EDUCATION`, and `MARRIAGE` were explored
- repayment behavior was studied
- correlations with the target variable were examined
- visualizations were created and saved

### 4. Modeling and Evaluation
Notebook: `04_modeling.ipynb`

In this step:
- the cleaned data was split into training and testing sets
- three classification models were trained
- models were compared using multiple evaluation metrics
- feature importance was analyzed
- detailed results were saved for interpretation

---

## Models Used
The following machine learning models were used in this project:

- Logistic Regression
- Decision Tree Classifier
- Random Forest Classifier

---

## Evaluation Metrics
The models were evaluated using both standard and industry-relevant classification metrics:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- PR-AUC
- Gini Coefficient
- KS Statistic
- Confusion Matrix

These metrics were selected because accuracy alone is often not enough in credit risk problems, especially when the dataset is imbalanced.

---

## Key Findings
- All three models achieved similar overall accuracy, around 81%.
- Logistic Regression performed reasonably well but had lower recall, meaning it missed more actual defaulters.
- Decision Tree and Random Forest performed better on credit risk–relevant metrics such as recall, ROC-AUC, Gini, and KS.
- Random Forest provided the strongest overall balance of predictive performance.
- Accuracy alone was not sufficient for model selection because the project involves identifying high-risk customers, not just maximizing overall correctness.

---

## Top Important Features
Feature importance analysis showed that the most influential variables were mainly related to repayment history, especially:

- `PAY_0`
- `PAY_2`
- `PAY_3`
- `PAY_4`
- `PAY_5`
- `PAY_6`

Other relevant variables included:
- `LIMIT_BAL`
- `PAY_AMT1`
- `PAY_AMT2`
- `BILL_AMT1`

This suggests that a customer’s past repayment behavior is one of the strongest indicators of future default risk.

---

## Business Interpretation
The results show that repayment history is far more informative than basic demographic variables when predicting default. This means that customers with repeated delayed payments are more likely to default in the future.

Such a model can help financial institutions:
- identify high-risk customers earlier
- support credit approval decisions
- improve portfolio risk management
- reduce financial losses due to default

---

## Project Structure
```text
credit-risk-ml/
│
├── data/
│   ├── raw/
│   │   └── default of credit card clients.xls
│   └── processed/
│       ├── credit_default_clean.csv
│       ├── model_results.csv
│       ├── model_results_detailed.csv
│       └── feature_importance.csv
│
├── models/
│
├── notebooks/
│   ├── 01_load_and_understand.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_eda.ipynb
│   └── 04_modeling.ipynb
│
├── reports/
│   └── figures/
│
├── src/
│   ├── data_preprocessing.py
│   ├── train_model.py
│   └── evaluate_model.py
│
├── README.md
└── requirements.txt