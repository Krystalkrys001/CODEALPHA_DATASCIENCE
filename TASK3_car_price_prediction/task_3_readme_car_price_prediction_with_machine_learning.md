# Car Price Prediction with Machine Learning — CodeAlpha Data Science Internship (Task 3)

## Project Overview

This project implements an end-to-end supervised regression pipeline to predict the fair resale value (`Selling_Price`, in Indian Lakhs) of **301 used vehicles** (`car data.csv`) based on original showroom price (`Present_Price`), manufacturing year (`Year`), odometer mileage (`Driven_kms`), fuel type (`Petrol`, `Diesel`, `CNG`), seller type (`Dealer` vs. `Individual`), transmission (`Manual` vs. `Automatic`), and previous owner count (`Owner`).

Developed as **Task 3** of the **CodeAlpha Data Science Internship**, the workflow emphasizes strict duplicate removal, domain-driven feature engineering (`Car_Age`), target distribution diagnostics, and logarithmic target transformation (`np.log1p`) to accurately model percentage-based vehicle depreciation across both budget commuter models and high-end luxury SUVs.

## Key Findings & Results

### 1. Data Integrity & Feature Engineering
* **Dataset Dimensions:** Audited `301` raw vehicle listings across `9` columns (`0` missing values), removing **2 exact duplicate records** to leave **299 unique vehicles**.
* **High-Cardinality Noise Mitigation:** Dropped `Car_Name` (`98` distinct vehicle model strings across 299 rows) to prevent severe overfitting.
* **Depreciation Feature Engineering:** Converted raw manufacturing `Year` (`2003–2018`) into **`Car_Age`** (`2019 - Year`, spanning `1` to `16` years) to directly capture vehicle age depreciation.
* **Primary Valuation Drivers:** Feature importance confirmed that **Original Showroom Price (`Present_Price`: 90.55%)** and **Vehicle Age (`Car_Age`: 7.16%)** account for **97.71%** of predictive signal, followed by `Driven_kms` (`1.34%`).

### 2. Model Performance: Raw Target vs. Log-Transformed Target (`n = 60` Test Set)

Because vehicle depreciation operates multiplicatively (losing a percentage of value annually rather than a flat currency amount) and luxury SUVs create extreme right-skew (`Selling_Price` up to `35.00 Lakhs`), applying a `np.log1p` transformation substantially improved generalization across all models:

| Regression Algorithm | Target Scale | Test $R^2$ Score | MAE (Lakhs) | RMSE (Lakhs) | Key Diagnostic Insight |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Linear Regression (Log-Target)** | **`log1p`** | **0.9034** | **0.914** | **1.578** | **Best overall model; captures multiplicative depreciation & extrapolates cleanly** |
| **Gradient Boosting (Log-Target)** | `log1p` | 0.8399 | 0.966 | 2.032 | Strong non-linear fit; constrained slightly by tree leaf ceiling on luxury SUVs |
| **Linear Regression (Raw Target)** | Raw | 0.7527 | 1.473 | 2.523 | Underpredicts luxury SUVs and overpredicts older budget vehicles |
| **Gradient Boosting (Raw Target)** | Raw | 0.7335 | 1.200 | 2.619 | High variance on right-skewed high-value vehicles |
| **Random Forest (Raw Target)** | Raw | 0.5153 | 1.430 | 3.532 | Unable to extrapolate beyond training leaf bounds on 33.00-Lakh test outlier |

## Repository Structure

```
CodeAlpha_CarPricePrediction/
├── car data.csv                                # Raw used vehicle dataset (301 records)
├── Task3_Car_Price_Prediction.ipynb            # Complete Jupyter Notebook with EDA, models & charts
├── Task3_Car_Price_Prediction_Report.pdf       # Comprehensive technical regression report
└── README.md                                   # Project documentation & modeling summary
```

## Tech Stack

* **Language:** Python 3.10+
* **Data Wrangling & Math:** `pandas`, `numpy`
* **Data Visualization:** `matplotlib`, `seaborn`
* **Machine Learning:** `scikit-learn` (`train_test_split`, `LinearRegression`, `RandomForestRegressor`, `GradientBoostingRegressor`, `r2_score`, `mean_absolute_error`, `mean_squared_error`)

## How to Run Locally

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Krystalkrys001/CodeAlpha_CarPricePrediction.git
   cd CodeAlpha_CarPricePrediction
   ```

2. **Install required dependencies:**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```

3. **Launch the notebook:**
   ```bash
   jupyter notebook Task3_Car_Price_Prediction.ipynb
   ```

## Author

**Chukwuma Obinna Ulasi**  
Data Analyst & AI Evaluation Specialist  
* **Portfolio:** [chukwumaulasi.com.ng](https://www.chukwumaulasi.com.ng)  
* **GitHub:** [github.com/Krystalkrys001](https://github.com/Krystalkrys001)  
* **Email:** ulasistanley1@gmail.com