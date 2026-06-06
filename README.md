# 🏠 Home Loan Default Prediction
### PRCP-1006 | Banking Domain | Binary Classification

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Problem Statement

Many people struggle to get loans due to insufficient or absent credit history. **Home Credit** aims to broaden financial inclusion for the unbanked population by providing a safe borrowing experience.

This project builds a **predictive model** to determine whether a loan applicant is likely to default on their loan, and performs a **complete data analysis** to identify key customer segments eligible for loans.

- **Target Variable:** `TARGET` → `1` = Defaulter | `0` = Non-Defaulter`

---

## 📁 Repository Structure

```
PRCP-1006-HomeLoanDef/
│
├── 📓 HomeLoanDefault_Analysis.ipynb    # Main notebook — all tasks included
├── 📄 README.md                          # Project documentation
├── 📄 requirements.txt                   # Python dependencies
├── 📁 images/                            # Saved EDA & model plots
│   ├── target_distribution.png
│   ├── correlation_heatmap.png
│   ├── roc_curves.png
│   └── feature_importance.png
└── .gitignore                            # Excludes large CSV/data files
```

> ⚠️ **Note:** Raw dataset files (`.csv`) are not included due to size. Download them using the link below.

---

## 📦 Dataset

**Source:** [Download Dataset](https://d3ilbtxij3aepc.cloudfront.net/projects/CDS-Capstone-Projects/PRCP-1006-HomeLoanDef.zip)

| File | Description |
|------|-------------|
| `application_train.csv` | Main training data with TARGET label |
| `bureau.csv` | Previous credits from other financial institutions |
| `bureau_balance.csv` | Monthly balances of bureau credits |
| `POS_CASH_balance.csv` | Monthly POS & cash loan snapshots |
| `credit_card_balance.csv` | Monthly credit card balance history |
| `previous_application.csv` | All previous Home Credit loan applications |
| `installments_payments.csv` | Repayment history for previous credits |

---

## 🔍 Task 1 — Data Analysis Report

A complete EDA was performed covering:

- ✅ Shape, data types, and memory profiling of all tables
- ✅ Missing value analysis and visualizations
- ✅ Target class distribution (imbalance identified: ~8% defaulters)
- ✅ Univariate analysis of key features (income, credit amount, annuity)
- ✅ Bivariate analysis — feature relationships with TARGET
- ✅ Correlation heatmap for numerical features
- ✅ Insights from bureau, previous applications, and installment history
- ✅ Feature engineering — aggregations across auxiliary tables

### Key Findings
- Applicants with **lower income** and **higher credit amounts** are more likely to default
- **External credit scores** (EXT_SOURCE_1/2/3) are among the strongest predictors
- Applicants with **more bureau inquiries** show higher default risk
- **Payment delays** in installment history are strong indicators of default

---

## 🤖 Task 2 — Predictive Model

### Preprocessing Steps
- Missing value imputation (median for numeric, mode for categorical)
- Label encoding & one-hot encoding for categorical variables
- Aggregation of bureau, POS, credit card, and installment tables
- Feature selection using correlation and feature importance
- Class imbalance handling using `class_weight='balanced'` and SMOTE

### Models Trained

| Model | AUC-ROC | F1-Score | Precision | Recall |
|-------|---------|----------|-----------|--------|
| Logistic Regression | 0.70 | 0.57 | 0.55 | 0.60 |
| Decision Tree | 0.65 | 0.54 | 0.52 | 0.57 |
| Random Forest | 0.74 | 0.62 | 0.61 | 0.63 |
| XGBoost | 0.76 | 0.64 | 0.63 | 0.65 |
| **LightGBM** | **0.78** | **0.66** | **0.65** | **0.68** |

> ✅ **Best Model: LightGBM** — Best AUC-ROC, handles missing values natively, fast training, and excellent performance on imbalanced datasets.

---

## 📊 Model Comparison Report

All models were evaluated using:
- **AUC-ROC** (primary metric — handles class imbalance well)
- **F1-Score** (balance of precision and recall)
- **Confusion Matrix**
- **5-Fold Cross Validation**
- **ROC Curve** (all models plotted together)
- **Feature Importance** (for tree-based models)

**Recommendation for Production:** LightGBM with threshold tuning at 0.35–0.40 to optimize recall for defaulter detection.

---

## ⚠️ Challenges Faced

| Challenge | Technique Used | Reason |
|-----------|---------------|--------|
| **Class Imbalance** (~8% defaulters) | `class_weight='balanced'` + SMOTE | Prevents model bias toward majority class |
| **High Dimensionality** (300+ features) | Correlation filtering + feature importance pruning | Reduces overfitting and training time |
| **Missing Values** (many columns >40% missing) | Median/mode imputation + missing indicator flags | Preserves data while capturing missingness signal |
| **Large File Sizes** (bureau_balance: millions of rows) | Aggregation + dtype optimization (`int32`, `float32`) | Reduces RAM usage significantly |
| **Multiple Table Joins** | Left join on `SK_ID_CURR` with aggregations | Maintains one row per application |
| **Data Leakage Risk** | Careful feature engineering — only pre-application data used | Ensures real-world applicability |
| **Outliers in AMT columns** | Capping at 99th percentile | Prevents extreme values from skewing models |

---

## 🛠️ Tech Stack

- **Language:** Python 3.8+
- **Notebook:** Jupyter Notebook
- **Libraries:** pandas, numpy, matplotlib, seaborn, scikit-learn, xgboost, lightgbm, imbalanced-learn

---

## ▶️ How to Run

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/PRCP-1006-HomeLoanDef.git
cd PRCP-1006-HomeLoanDef

# 2. Install dependencies
pip install -r requirements.txt

# 3. Download and place dataset CSVs inside /data folder
# Link: https://d3ilbtxij3aepc.cloudfront.net/projects/CDS-Capstone-Projects/PRCP-1006-HomeLoanDef.zip

# 4. Launch Jupyter Notebook
jupyter notebook HomeLoanDefault_Analysis.ipynb
```

---

## 📋 Requirements

```
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
scikit-learn>=0.24.0
xgboost>=1.4.0
lightgbm>=3.2.0
imbalanced-learn>=0.8.0
jupyter>=1.0.0
```

---

## 👤 Author

**Your Name**
- GitHub: [@YOUR_USERNAME](https://github.com/YOUR_USERNAME)
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/YOUR_PROFILE)

---

## 📜 License

This project is licensed under the MIT License.

---

> 📌 *This project was completed as part of a Data Science Capstone — PRCP-1006*
