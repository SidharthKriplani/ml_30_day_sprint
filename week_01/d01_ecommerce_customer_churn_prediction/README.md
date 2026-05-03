# D1 — E-commerce Customer Churn Prediction

## Objective

Build a churn prediction model to identify e-commerce customers who are likely to stop using the platform and prioritize them for retention targeting.

## Dataset

**E-commerce Customer Churn**  
Kaggle dataset: `ankitverma2010/ecommerce-customer-churn-analysis-and-prediction`

## Problem Type

Binary classification.

Target variable: `Churn`

## What Was Done

- Loaded and validated the customer-level dataset.
- Checked missing values, duplicates, data types, and target distribution.
- Explored churn patterns across customer behavior, complaints, satisfaction, tenure, order count, and days since last order.
- Built preprocessing pipelines with imputation, encoding, and scaling where needed.
- Compared Logistic Regression, Random Forest, and XGBoost.
- Evaluated models using ROC-AUC, PR-AUC, precision, recall, F1, and confusion matrix.
- Tuned the churn probability threshold for retention targeting.
- Created churn risk buckets and a scored customer output file.
- Logged the champion model and outputs using MLflow.

## Best Model

**XGBoost** was selected as the champion model.

At the selected threshold of `0.60`, the model achieved:

| Metric | Value |
|---|---:|
| Precision | 0.88 |
| Recall | 0.91 |
| F1 Score | 0.89 |
| Customers Flagged | 197 |
| True Positives | 173 |
| False Positives | 24 |
| False Negatives | 17 |

## Business Recommendation

Use the XGBoost churn probability score to rank customers by churn risk.

For this sprint, customers with churn probability `>= 0.60` are treated as high-risk and should be prioritized for retention outreach.

This threshold gives a strong balance between catching likely churners and avoiding unnecessary outreach.

## Production-Shaped Artifacts

Expected outputs:

```text
models/
  d1_xgboost_churn_model.pkl

outputs/
  threshold_scan.csv
  scored_test_customers.csv
  threshold_policy.json
