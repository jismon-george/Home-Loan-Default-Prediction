# 🏛️ Texas State Government Salary Prediction

<div align="center">

### PRCP-1024 | Government Domain | Regression

![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

</div>

---

## 📌 Problem Statement

The **Texas Tribune** obtained salary records from the Texas State Comptroller for every position across **113 state agencies**, made available under the *Texas Public Information Act*.

This project solves 3 tasks:

> **Task 1** → Prepare a complete data analysis report on the given data  
> **Task 2** → Build a predictive model to help the Texas state government know the payroll information of employees  
> **Task 3** → Who are the salary outliers? Which departments have the biggest wage disparities? How have salaries changed over time?

---

## 📂 Repository Structure

```
📦 PRCP-1024-TexasSalaryPrediction
 ┣ 📓 PRCP_1024_Texas_Salary_Prediction.ipynb   ← Main notebook (all 3 tasks)
 ┣ 📄 README.md                                 ← Project documentation
 ┣ 📄 requirements.txt                          ← Python dependencies
 ┗ 📄 .gitignore                                ← Git ignore rules
```

---

## 📊 Dataset Information

| Attribute | Description |
|-----------|-------------|
| `Agency` | Agency code |
| `Agency Name` | Full name of the state agency |
| `Last Name / First Name / MI` | Employee name |
| `Class Title` | Job title / role |
| `Ethnicity` | Employee ethnicity |
| `Gender` | Employee gender |
| `Status` | Employment status (Full-time / Part-time) |
| `Employ Date` | Date of joining |
| `Hourly Rate` | Hourly pay rate ($) |
| `Hrs per Week` | Weekly working hours |
| `Monthly` | Monthly income ($) |
| `Annual` | **Annual income — Target Variable** ($) |
| `State Number` | Unique state employee ID |

📥 **Dataset:** [Download Here](https://d3ilbtxij3aepc.cloudfront.net/projects/CDS-Capstone-Projects/salary.zip)

> ✅ The notebook **auto-downloads and extracts** the dataset on first run — no manual steps needed!

---

## 🔍 EDA Highlights (Task 1)

- 📈 Annual income is **highly right-skewed** — a small number of executives earn significantly more than the median
- 👥 **Gender pay gap** observed — male employees have higher median salaries across most agencies
- 🏢 Top agencies by headcount: Health & Human Services, TxDOT, Corrections
- 🌍 Salary varies significantly across ethnicities and departments
- 📅 Government headcount grew steadily through 2010, then plateaued post-2015

---

## 🔎 Task 3 — Key Insights

### 🚨 Salary Outliers
- ~2–5% of employees (senior executives) earn **> 1.5× IQR above Q3**
- These are legitimate data points — real executive salaries, not errors
- Detected using both **IQR method** and **Z-score (> 3)**

### 💰 Wage Disparities
- **Finance, Legal & Executive-branch agencies** show the largest manager-to-employee pay gaps
- Some agencies have a **200–400% pay difference** between managers and staff

### 📅 Temporal Trends
- Nominal salaries have **increased over the years** but vary significantly by department
- Some departments show **headcount reduction** post-2015 despite salary growth

---

## 🤖 Model Comparison Report (Task 2)

| Model | R² Score | RMSE | MAE | Recommended |
|-------|----------|------|-----|-------------|
| **Random Forest** | ✅ Highest | Lowest | Lowest | ⭐ **Production** |
| Extra Trees | Very High | Low | Low | ✅ Alternative |
| Gradient Boosting | High | Medium | Medium | ✅ Good |
| Decision Tree | Medium | Medium | Medium | ⚠️ Overfits |
| Ridge Regression | Baseline | High | High | ❌ Baseline |
| Lasso Regression | Baseline | High | High | ❌ Baseline |
| Linear Regression | Baseline | High | High | ❌ Baseline |
| K-Nearest Neighbours | Medium | Medium | Medium | ⚠️ Slow |

### 🏆 Best Model: Random Forest Regressor
- ✅ Highest R² Score
- ✅ Robust to outliers and skewed data
- ✅ Handles mixed feature types natively
- ✅ Interpretable via Feature Importance plots
- ✅ No need for feature scaling

---

## 🛠️ Challenges & Solutions

| # | Challenge | Technique Used | Reason |
|---|-----------|---------------|--------|
| 1 | Missing values in numeric columns | **Median Imputation** | Robust to outliers unlike mean |
| 2 | High-cardinality columns (agency, job title) | **Frequency Encoding** | Avoids feature-space explosion |
| 3 | Heavily skewed target (annual income) | **Tree-based models** | Scale-invariant, unaffected by skew |
| 4 | Salary outliers (executive pay) | **IQR + Z-score Analysis** | Retained as real signal, not removed |
| 5 | Missing annual income when hourly data exists | **Derived:** `hourly × hrs/wk × 52` | Recovers otherwise-dropped rows |
| 6 | Inconsistent date formats | `pd.to_datetime(infer_datetime_format=True)` | Gracefully handles multiple formats |
| 7 | Long training time on large dataset | `n_jobs=-1` + **5-Fold Cross Validation** | Parallel processing, balanced variance |

---

## 🚀 How to Run

### 1. Clone the repository
```bash
git clone https://github.com/jismon-george/PRCP-1024-TexasSalaryPrediction.git
cd PRCP-1024-TexasSalaryPrediction
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Launch the notebook
```bash
jupyter notebook PRCP_1024_Texas_Salary_Prediction.ipynb
```

> ▶️ **Run All Cells** — the dataset will be downloaded automatically on first run.

---

## 🧰 Tech Stack

<div align="center">

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=flat-square)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat-square)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=flat-square&logo=scipy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)

</div>

---

## 👤 Author

**Jismon George**

[![GitHub](https://img.shields.io/badge/GitHub-jismon--george-181717?style=flat-square&logo=github)](https://github.com/jismon-george)

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

<div align="center">
<i>Data sourced from the Texas Tribune / Texas State Comptroller via the Texas Public Information Act.</i>
</div>
