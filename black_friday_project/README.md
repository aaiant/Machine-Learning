# 🫀 Heart Disease Classification

> A binary classification project to predict the presence of heart disease from clinical indicators, using Logistic Regression, KNN, and Random Forest — with a final tuned model achieving **84% accuracy** and **0.91 AUC**.

---

## 📋 Table of Contents

* [🎯 Problem Definition](#-problem-definition)
* [📊 Dataset](#-dataset)
* [📁 Project Structure](#-project-structure)
* [🔬 Methodology](#-methodology)
* [📈 Results](#-results)
* [🔍 Key Findings](#-key-findings)
* [🛠️ Technologies Used](#-technologies-used)
* [▶️ How to Run](#️-how-to-run)
* [📌 Conclusions](#-conclusions)

---

## 🎯 Problem Definition

Cardiovascular diseases are among the leading causes of mortality worldwide, making early detection and risk assessment a critical challenge in modern healthcare.

The goal of this project is to build a supervised machine learning model capable of predicting whether a patient has heart disease based on 13 clinical indicators.

* **Task type:** Binary Classification
* **Target variable:** `target` (1 = Heart Disease, 0 = No Heart Disease)

---

## 📊 Dataset

The dataset originates from the well-known **Cleveland Heart Disease Database (1988)** and combines data from four medical institutions: Cleveland, Hungary, Switzerland, and Long Beach VA.

| Property       | Value              |
| -------------- | ------------------ |
| Raw samples    | 1,025 rows         |
| Features       | 13 clinical inputs |
| Target classes | 2 (binary)         |
| Missing values | None               |

### 🔑 Features

| Feature    | Description                                    |
| ---------- | ---------------------------------------------- |
| `age`      | Age of the patient                             |
| `sex`      | Sex (1 = male, 0 = female)                     |
| `cp`       | Chest pain type (0–3)                          |
| `trestbps` | Resting blood pressure (mm Hg)                 |
| `chol`     | Serum cholesterol (mg/dl)                      |
| `fbs`      | Fasting blood sugar > 120 mg/dl (1 = true)     |
| `restecg`  | Resting ECG results (0–2)                      |
| `thalach`  | Maximum heart rate achieved                    |
| `exang`    | Exercise-induced angina (1 = yes)              |
| `oldpeak`  | ST depression induced by exercise              |
| `slope`    | Slope of peak exercise ST segment              |
| `ca`       | Number of major vessels colored by fluoroscopy |
| `thal`     | Thalassemia type                               |

> **Note:** The raw dataset contained 723 duplicate rows (≈70.5%). After deduplication, 302 unique records remained with a near-balanced class distribution (164 positive, 138 negative).

---

## 📁 Project Structure

```
heart-disease-classification/
│
├── Heart-Disease-Classification.ipynb   # Main analysis notebook
└── README.md
```

---

## 🔬 Methodology

### 1. Data Loading & Cleaning

* Loaded dataset (1,025 rows, 14 columns)
* Removed 723 duplicate rows
* Verified no missing values and correct data types

### 2. Exploratory Data Analysis (EDA)

* Class distribution analysis
* Gender-based comparisons
* Age vs. heart rate visualization
* Chest pain type analysis
* Correlation heatmap

### 3. Baseline Models

* Logistic Regression
* K-Nearest Neighbors
* Random Forest

👉 Random Forest performed best initially

### 4. Hyperparameter Tuning

* **KNN:** Optimal at `k = 11`
* **Logistic Regression:** ~73.7% accuracy
* **Random Forest:** 310 estimators, max depth = 5

### 5. Model Evaluation

* ROC Curve & AUC
* Confusion Matrix
* Precision / Recall / F1 Score
* 5-Fold Cross-Validation

### 6. Feature Importance

Top predictors:

1. `cp` — Chest pain type
2. `thalach` — Maximum heart rate
3. `slope` — ST segment slope
4. `sex` — Gender

---

## 📈 Results

| Metric             | Score |
| ------------------ | ----- |
| Accuracy           | 84.0% |
| Precision          | 84.6% |
| Recall             | 84.3% |
| F1 Score           | 84.1% |
| AUC (ROC)          | 0.91  |
| Cross-val Accuracy | 84.1% |

✔️ Correct predictions: **51 / 61**
✔️ Misclassifications: **10**

---

## 🔍 Key Findings

* **Gender:** Females showed a higher disease rate (**75%**) vs. males (**45%**)
* **Chest pain type:** Strong predictor of disease presence
* **ST slope:** Upsloping segments strongly correlated with disease
* **Age & heart rate:** Inverse relationship observed

---

## 🛠️ Technologies Used

* Python 3 (Jupyter Notebook)
* pandas, numpy
* matplotlib, seaborn
* scikit-learn

  * LogisticRegression
  * KNeighborsClassifier
  * RandomForestClassifier
  * RandomizedSearchCV, GridSearchCV

---

## ▶️ How to Run

```bash
git clone https://github.com/your-username/heart-disease-classification.git
cd heart-disease-classification
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook Heart-Disease-Classification.ipynb
```

---

## 📌 Conclusions

This project successfully developed a binary classification pipeline for predicting heart disease using clinical data.

The tuned **Random Forest model** achieved strong and consistent performance, with:

* **84% accuracy**
* **0.91 AUC**

These results demonstrate reliable predictive capability and generalization.

### 🚀 Future Improvements

* Feature engineering & selection
* Ensemble stacking
* XGBoost / LightGBM models
* Additional datasets for better generalization
