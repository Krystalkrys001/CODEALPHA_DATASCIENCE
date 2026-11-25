# Sales Prediction using Python — CodeAlpha Data Science Internship (Task 4)

## Project Overview

This project builds an end-to-end marketing mix modeling and predictive sales pipeline across **200 regional markets** (`Advertising.csv`), quantifying how advertising expenditure across **TV**, **Radio**, and **Newspaper** channels (in thousands of dollars) drives product **Sales** (in thousands of units).

Developed as **Task 4** of the **CodeAlpha Data Science Internship**, the workflow pairs statistical hypothesis testing (Ordinary Least Squares inference) with non-linear machine learning forecasting to expose confounding media spend illusions, capture cross-channel advertising synergy (`TV × Radio`), and deliver actionable budget reallocation recommendations.

## Key Findings & Marketing Mix Insights

### 1. Data Integrity & Statistical Hypothesis Testing (OLS)
* **Dataset Dimensions:** Audited `200` regional market observations across `5` columns (`0` missing values, `0` duplicate records) and dropped the redundant CSV index column (`Unnamed: 0`).
* **Exposing the Newspaper Confounding Illusion:** In isolation, Newspaper spend appears weakly correlated with Sales ($r = 0.2283$). However, multiple OLS regression controlling for TV and Radio proves that Newspaper's marginal slope is **$-0.0010$** with a **$p$-value of $0.860$**—statistically indistinguishable from zero. Newspaper only appeared effective because marketers who purchased Radio ads ($r = 0.3541$ with Newspaper) drove the actual conversions.
* **Channel ROI Hierarchy:**
  * **Radio ($r = 0.5762$, $p < 0.0001$):** Generates **+188.5 units** (`+0.1885k`) per **$1,000** spent—delivering more than **4× the marginal unit return per dollar** of TV within its `$0–$50k` budget range.
  * **TV ($r = 0.7822$, $p < 0.0001$):** Generates **+45.8 units** (`+0.0458k`) per **$1,000** spent across broad reach budgets up to `$296.4k`.

### 2. Predictive Model Evaluation on Unseen Holdout Markets ($n = 40$)

Evaluating three progressively expressive models on an **80/20 train-test split** (`160` training markets, `40` unseen test markets):

| Predictive Model | Test $R^2$ Score | MAE (k Units) | RMSE (k Units) | Key Analytical Takeaway |
| :--- | :---: | :---: | :---: | :--- |
| **Random Forest Regressor (200 Trees)** | **0.9818** | **0.629** | **0.757** | **Highest predictive accuracy; captures diminishing returns & synergy** |
| **Interaction Linear Regression (`TV × Radio`)** | **0.9742** | **0.672** | **0.902** | Cuts RMSE nearly in half vs. additive baseline by modeling cross-channel lift |
| **Additive Linear Regression (Baseline)** | 0.8994 | 1.461 | 1.782 | Systematically underpredicts high-budget markets where TV & Radio run together |

## Repository Structure

```
CodeAlpha_SalesPrediction/
├── Advertising.csv                             # Regional ad spend & sales dataset (200 records)
├── Task4_Sales_Prediction.ipynb                # Complete Jupyter Notebook with OLS, models & charts
├── Task4_Sales_Prediction_Report.pdf           # Comprehensive marketing mix & modeling report
└── README.md                                   # Project documentation & budget strategy summary
```

## Tech Stack

* **Language:** Python 3.10+
* **Data Wrangling & Statistics:** `pandas`, `numpy`, `statsmodels`
* **Data Visualization:** `matplotlib`, `seaborn`
* **Machine Learning:** `scikit-learn` (`train_test_split`, `LinearRegression`, `RandomForestRegressor`, `r2_score`, `mean_absolute_error`, `mean_squared_error`)

## How to Run Locally

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Krystalkrys001/CodeAlpha_SalesPrediction.git
   cd CodeAlpha_SalesPrediction
   ```

2. **Install required dependencies:**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn statsmodels jupyter
   ```

3. **Launch the notebook:**
   ```bash
   jupyter notebook Task4_Sales_Prediction.ipynb
   ```

## Author

**Chukwuma Obinna Ulasi**  
Data Analyst & AI Evaluation Specialist  
* **Portfolio:** [chukwumaulasi.com.ng](https://www.chukwumaulasi.com.ng)  
* **GitHub:** [github.com/Krystalkrys001](https://github.com/Krystalkrys001)  
* **Email:** ulasistanley1@gmail.com