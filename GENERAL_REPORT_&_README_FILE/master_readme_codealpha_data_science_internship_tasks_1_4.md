# CodeAlpha Data Science Internship — Complete Portfolio (Tasks 1–4)

## Program Overview

This repository houses the complete, end-to-end codebase, technical documentation, and analytical reports for all four projects in the **CodeAlpha Data Science Internship**. Across classification, macroeconomic time-series analysis, secondary-market regression, and econometric marketing mix modeling, every workflow enforces strict data auditing, leakage-free validation splits, diagnostic error analysis, and actionable business recommendations.

---

## Executive Summary & Cross-Project Results Matrix

| Task | Project Domain | Dataset & Scale | Core Methodologies | Headline Empirical Result |
| :--- | :--- | :--- | :--- | :--- |
| **Task 1** | **Iris Flower Classification** (Multi-Class Supervised Learning) | `Iris.csv` ($N = 150$, 3 classes, 4 features) | Leakage auditing, stratified 80/20 split, training-fit `StandardScaler`, Logistic Regression vs. Random Forest | **93.33% test accuracy** (Macro F1: `0.93`); petal dimensions drive **86.87%** of species separability |
| **Task 2** | **Unemployment Analysis with Python** (Macroeconomic Time-Series EDA) | `Unemployment in India.csv` ($N = 740$) & `Unemployment_Rate_upto_11_2020.csv` ($N = 267$) | Schema reconciliation, pre- vs. post-lockdown segmentation, Labour Participation Rate (LPR) tracking, regional profiling | Headline unemployment surged from **9.20% (Jan 2020) to 23.24% (May 2020)** while LPR fell **9.33 pp** (`35.30%`), hitting Urban centers harder (`22.08%` vs. `18.26%`) |
| **Task 3** | **Car Price Prediction** (Supervised Regression & Feature Engineering) | `car data.csv` ($N = 299$ clean vehicles, 9 features) | Deduplication, `Car_Age` engineering, target skew diagnostics, `np.log1p` target transformation | Log-Linear Regression boosted test **$R^2$ from `0.7527` to `0.9034`** (`MAE = 0.914 Lakhs`); `Present_Price` + `Car_Age` explain **97.71%** of valuation |
| **Task 4** | **Sales Prediction using Python** (Marketing Mix & Econometric Modeling) | `Advertising.csv` ($N = 200$ regional markets, 3 ad channels) | OLS hypothesis testing ($p$-values), confounding diagnostics, `TV × Radio` synergy engineering, Random Forest | Exposed Newspaper spend as statistically insignificant ($p = 0.860$); modeling `TV × Radio` lift jumped test **$R^2$ from `0.8994` to `0.9742`** (Random Forest: **`0.9818`**) |

---

## Detailed Task Breakdowns

### Task 1: Iris Flower Classification (`Iris.csv`)
* **Objective:** Classify botanical specimens into *Iris-setosa*, *Iris-versicolor*, and *Iris-virginica* using sepal and petal measurements.
* **Key Engineering Decisions:**
  * Identified and dropped the sequentially ordered `Id` column (`1–150`) to prevent target index leakage.
  * Used a stratified 80/20 split (`120` train, `30` test) with `StandardScaler` fit strictly on the training partition.
* **Results:** Logistic Regression achieved **93.33% accuracy** (`28/30` correct), outperforming Random Forest (`90.00%`) by capturing smooth linear boundaries along the overlapping phenotypic zone between *Versicolor* and *Virginica*.

### Task 2: Unemployment Analysis with Python (`Unemployment in India.csv` & `Unemployment_Rate_upto_11_2020.csv`)
* **Objective:** Quantify the impact of the March 2020 COVID-19 national lockdown on India's labor market across urban/rural settlements and geographic zones.
* **Key Engineering Decisions:**
  * Cleaned header whitespace and removed **28 completely blank trailing rows** from Dataset 1 (`768 → 740` rows) while preserving Dataset 2 (`267` rows) for full 2020 recovery tracking.
  * Evaluated both the **Unemployment Rate** and **Labour Participation Rate (LPR)** to uncover hidden discouraged-worker exits.
* **Results:** National unemployment peaked at **23.24% in May 2020** before recovering to **8.03% by October 2020**. Urban markets suffered steeper contraction (`22.08%` mean vs. `18.26%` rural), with acute state-level impacts in **Haryana (`27.48%` mean)**, **Tripura (`25.06%`)**, and **Puducherry (`75.85%` peak)**.

### Task 3: Car Price Prediction with Machine Learning (`car data.csv`)
* **Objective:** Predict used vehicle resale prices (`Selling_Price` in Indian Lakhs) across budget commuter models and luxury SUVs.
* **Key Engineering Decisions:**
  * Removed **2 exact duplicate listings** (`301 → 299` rows), dropped high-cardinality `Car_Name` (`98` unique strings), and engineered **`Car_Age`** (`2019 - Year`).
  * Diagnosed multiplicative percentage depreciation and applied a logarithmic target transformation (`np.log1p` / `np.expm1`).
* **Results:** Log-Linear Regression achieved **$R^2 = 0.9034$** (`MAE = 0.914 Lakhs`, `RMSE = 1.578 Lakhs`), resolving the extrapolation ceiling that limited raw Random Forest (`R² = 0.5153`) on high-value luxury SUVs.

### Task 4: Sales Prediction using Python (`Advertising.csv`)
* **Objective:** Forecast product sales (`Sales` in thousands of units) from TV, Radio, and Newspaper advertising spend (`$ Thousands`) and optimize media budget allocation.
* **Key Engineering Decisions:**
  * Executed Ordinary Least Squares (OLS) statistical inference to isolate true channel elasticity from multicollinearity.
  * Engineered a multiplicative interaction term (`TV × Radio`) to capture cross-channel advertising synergy.
* **Results:** Proved Newspaper spend has zero statistically valid impact ($p = 0.860$; confounded by its $r = 0.3541$ correlation with Radio), while Radio delivers **+188.5 units per $1,000** (over 4× TV's `+45.8 units`). Modeling `TV × Radio` synergy raised linear test **$R^2$ from `0.8994` to `0.9742`**, while Random Forest reached **`0.9818`**.

---

## Repository Structure

```
CodeAlpha_DataScience_Portfolio/
├── Task_1_Iris_Classification/
│   ├── Iris.csv
│   └── Task1_Iris_Classification.ipynb
├── Task_2_Unemployment_Analysis/
│   ├── Unemployment in India.csv
│   ├── Unemployment_Rate_upto_11_2020.csv
│   └── Task2_Unemployment_Analysis.ipynb
├── Task_3_Car_Price_Prediction/
│   ├── car data.csv
│   └── Task3_Car_Price_Prediction.ipynb
├── Task_4_Sales_Prediction/
│   ├── Advertising.csv
│   └── Task4_Sales_Prediction.ipynb
├── CodeAlpha_Capstone_Technical_Report.pdf
└── README.md
```

## Tech Stack

* **Programming & Core Libraries:** Python 3.10+, `pandas`, `numpy`
* **Statistical Inference & Machine Learning:** `scikit-learn`, `statsmodels`
* **Data Visualization:** `matplotlib`, `seaborn`

## Author

**Chukwuma Obinna Ulasi**  
Data Analyst & AI Evaluation Specialist  
* **Portfolio:** [chukwumaulasi.com.ng](https://www.chukwumaulasi.com.ng)  
* **GitHub:** [github.com/Krystalkrys001](https://github.com/Krystalkrys001)  
* **Email:** ulasistanley1@gmail.com