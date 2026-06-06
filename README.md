# 🏠 Home Loan Default Prediction
**Domain:** Banking | **Type:** Binary Classification

## Problem Statement
Predict whether a loan applicant will default (1) or not (0) based on 
application data, bureau history, and repayment behavior.

## Dataset
[Home Credit Dataset](https://d3ilbtxij3aepc.cloudfront.net/projects/CDS-Capstone-Projects/PRCP-1006-HomeLoanDef.zip)

## Files
| File | Description |
|------|-------------|
| application_train.csv | Main training data with target |
| bureau.csv | Previous credits from other institutions |
| bureau_balance.csv | Monthly balances of bureau credits |
| POS_CASH_balance.csv | POS & cash loan history |
| credit_card_balance.csv | Credit card monthly history |
| previous_application.csv | Previous Home Credit applications |
| installments_payments.csv | Repayment history |

## Results
| Model | AUC-ROC | F1-Score |
|-------|---------|----------|
| LightGBM | ~0.78 | ~0.65 |
| Random Forest | ~0.74 | ~0.61 |
| Logistic Regression | ~0.70 | ~0.58 |

## How to Run
pip install -r requirements.txt
jupyter notebook HomeLoanDefault_Analysis.ipynb
