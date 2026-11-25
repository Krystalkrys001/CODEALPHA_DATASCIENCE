# Iris Flower Classification — CodeAlpha Data Science Internship (Task 1)

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Classification-orange?logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## Project Overview
This project implements an end-to-end, leakage-free supervised machine learning pipeline to classify **150 Iris botanical specimens** into three distinct species—***Iris-setosa***, ***Iris-versicolor***, and ***Iris-virginica***—using four continuous morphological measurements (`SepalLengthCm`, `SepalWidthCm`, `PetalLengthCm`, and `PetalWidthCm`).

Developed as **Task 1** of the **CodeAlpha Data Science Internship**, the workflow emphasizes strict data integrity auditing, multivariate exploratory data analysis (EDA), training-fit feature standardization, and comparative evaluation between linear and ensemble classifiers.

---

## Key Findings & Results

### 1. Data Integrity & Leakage Prevention
* **Dataset Dimensions:** `150 rows × 6 columns` with **0 missing values** and **0 duplicate records**.
* **Class Balance:** Exact uniform distribution across all three species (**50 samples / 33.33%** per class).
* **Identifier Leakage Mitigation:** The raw `Id` column (`1–150`) is sorted sequentially by species label. Explicitly dropping `Id` prior to splitting prevented target index leakage and ensured models learned genuine botanical morphology.

### 2. Exploratory Morphological Insights
| Species | Samples ($n$) | Mean Sepal Length | Mean Sepal Width | Mean Petal Length | Mean Petal Width |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Iris-setosa** | 50 | 5.01 cm | 3.42 cm | 1.46 cm | 0.24 cm |
| **Iris-versicolor** | 50 | 5.94 cm | 2.77 cm | 4.26 cm | 1.33 cm |
| **Iris-virginica** | 50 | 6.59 cm | 2.97 cm | 5.55 cm | 2.03 cm |

* **Linear Separability:** *Iris-setosa* exhibits markedly smaller petals (`1.46 cm × 0.24 cm`), forming a completely isolated cluster with zero overlap against the other two species.
* **Feature Importance:** Gini impurity analysis confirmed that **Petal Width (43.72%)** and **Petal Length (43.15%)** account for **86.87%** of total predictive power, whereas `SepalWidthCm` contributes just **1.50%**.

### 3. Model Evaluation on Unseen Holdout Data ($n = 30$)
Using an **80/20 stratified train-test split** (`120` training samples, `30` unseen test samples—10 per species) and `StandardScaler` fit strictly on the training partition:

| Model | Test Accuracy | Correct / Total | Macro Precision | Macro Recall | Macro F1-Score |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Logistic Regression (Scaled)** | **93.33%** | **28 / 30** | **0.93** | **0.93** | **0.93** |
| **Random Forest (100 Trees)** | 90.00% | 27 / 30 | 0.90 | 0.90 | 0.90 |

* **Diagnostic Error Analysis:** Logistic Regression achieved **100% precision and recall** on *Iris-setosa* (`10/10`) and **90%** on both *Iris-versicolor* (`9/10`) and *Iris-virginica* (`9/10`). The two misclassifications occurred symmetrically along the natural phenotypic boundary where *Versicolor* and *Virginica* petal sizes overlap, demonstrating why smooth linear hyperplanes outperform axis-aligned tree splits on continuous geometric gradients.

---

## Repository Structure
```text
CodeAlpha_IrisClassification/
├── Iris.csv                                # Raw botanical dataset (150 records)
├── Task1_Iris_Classification.ipynb         # Complete Jupyter Notebook with code & plots
├── Task1_Iris_Classification_Report.pdf    # Comprehensive technical report
└── README.md                               # Project documentation & summary
```

---

## Tech Stack
* **Language:** Python 3.10+
* **Data Manipulation:** `pandas`, `numpy`
* **Data Visualization:** `matplotlib`, `seaborn`
* **Machine Learning:** `scikit-learn` (`train_test_split`, `StandardScaler`, `LogisticRegression`, `RandomForestClassifier`, `classification_report`, `confusion_matrix`)

---

## How to Run Locally
1. **Clone the repository:**
   ```bash
   git clone https://github.com/Krystalkrys001/CodeAlpha_IrisClassification.git
   cd CodeAlpha_IrisClassification
   ```
2. **Install required dependencies:**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```
3. **Launch the notebook:**
   ```bash
   jupyter notebook Task1_Iris_Classification.ipynb
   ```

---

## Author
**Chukwuma Obinna Ulasi**  
Data Analyst & AI Evaluation Specialist  
* **Portfolio:** [chukwumaulasi.com.ng](https://www.chukwumaulasi.com.ng)  
* **GitHub:** [github.com/Krystalkrys001](https://github.com/Krystalkrys001)  
* **Email:** ulasistanley1@gmail.com