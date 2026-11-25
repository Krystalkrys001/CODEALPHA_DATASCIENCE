# Unemployment Analysis with Python — CodeAlpha Data Science Internship (Task 2)

## Project Overview

This project conducts an end-to-end macroeconomic labor market analysis examining **India's unemployment rate dynamics before, during, and immediately after the March 2020 COVID-19 national lockdown**. By reconciling and auditing two multi-regional longitudinal datasets (`Unemployment in India.csv` and `Unemployment_Rate_upto_11_2020.csv`), the workflow quantifies structural labor shocks, hidden worker discouragement via Labour Participation Rate (LPR) tracking, urban-rural vulnerability divergences, and state-level economic disparities.

Developed as **Task 2** of the **CodeAlpha Data Science Internship**, this study translates raw time-series labor indicators into actionable economic and social policy recommendations.

## Key Findings & Macroeconomic Insights

### 1. Data Integrity & Schema Reconciliation
* **Dataset 1 (`Unemployment in India.csv` — May 2019 to June 2020):** Audited `768` raw records, identifying and stripping leading/trailing whitespace across column headers and removing **28 completely blank trailing rows**, yielding **740 clean state-area observations**.
* **Dataset 2 (`Unemployment_Rate_upto_11_2020.csv` — January 2020 to October 2020):** Audited **267 clean state-zone observations** across 5 geographic zones (`North`, `South`, `East`, `West`, `Northeast`) with zero missing values.

### 2. Quantifying the COVID-19 Lockdown Shock
* **Headline Unemployment More Than Doubled:** Across Dataset 1, national mean unemployment surged from **9.61%** (median **7.22%**) during the pre-lockdown baseline (`May 2019 – Mar 2020`) to **20.19%** (median **16.40%**) during the lockdown shock (`Apr – Jun 2020`).
* **Peak & V-Shaped Recovery Trajectory (2020):** In Dataset 2, average monthly unemployment rose from **9.20%** in January and **9.27%** in February to **22.24%** in April and a peak of **23.24% in May 2020**, before rebounding to **8.03% by October 2020**.
* **Hidden Worker Discouragement:** Headline unemployment alone understates total labor distress—the **Labour Participation Rate (LPR)** fell **9.33 percentage points** from **44.63%** in January 2020 to **35.30% in April 2020**, as average state employment contracted from **15.64 million** to **10.57 million**.

### 3. Urban vs. Rural Divergence & Regional Vulnerability

| Labor Market Segment | Pre-Lockdown Mean | Lockdown Shock Mean | Peak Recorded Rate | Primary Economic Driver |
| :--- | :---: | :---: | :---: | :--- |
| **Urban India** | 10.91% | **22.08%** | **76.74%** (Puducherry) | Shutdown of retail, hospitality, construction & informal services |
| **Rural India** | 8.23% | **18.26%** | 74.51% (Puducherry) | Essential agricultural & rabi harvest exemptions buffered job losses |

* **Most Affected States (2020 Average Unemployment):** **Haryana (27.48%)**, **Tripura (25.06%)**, **Jharkhand (19.54%)**, **Bihar (19.47%)**, and **Delhi (18.41%)**. Single-month spikes reached **75.85%** in Puducherry and **59.23%** in Jharkhand.
* **Most Resilient States (2020 Average Unemployment):** **Meghalaya (3.87%)**, **Assam (4.86%)**, and **Gujarat (6.38%)**.

## Repository Structure

```
CodeAlpha_UnemploymentAnalysis/
├── Unemployment in India.csv                    # Longitudinal Rural/Urban dataset (May 2019 – Jun 2020)
├── Unemployment_Rate_upto_11_2020.csv           # Zonal & geospatial dataset (Jan 2020 – Oct 2020)
├── Task2_Unemployment_Analysis.ipynb            # Complete Jupyter Notebook with cleaning, EDA & visuals
├── Task2_Unemployment_Analysis_Report.pdf       # Comprehensive macroeconomic technical report
└── README.md                                    # Project documentation & policy summary
```

## Tech Stack

* **Language:** Python 3.10+
* **Data Wrangling & Time-Series:** `pandas`, `numpy`
* **Data Visualization:** `matplotlib`, `seaborn`

## How to Run Locally

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Krystalkrys001/CodeAlpha_UnemploymentAnalysis.git
   cd CodeAlpha_UnemploymentAnalysis
   ```

2. **Install required dependencies:**
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```

3. **Launch the notebook:**
   ```bash
   jupyter notebook Task2_Unemployment_Analysis.ipynb
   ```

## Author

**Chukwuma Obinna Ulasi**  
Data Analyst & AI Evaluation Specialist  
* **Portfolio:** [chukwumaulasi.com.ng](https://www.chukwumaulasi.com.ng)  
* **GitHub:** [github.com/Krystalkrys001](https://github.com/Krystalkrys001)  
* **Email:** ulasistanley1@gmail.com