# 🛍️ Black Friday Sales Prediction

> A regression project to predict individual purchase amounts during Black Friday, using over 550,000 retail transactions and a tuned **Random Forest Regressor** — achieving an **R² of 0.75** on the test set.

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
* [📤 Output Files](#-output-files)
* [📌 Conclusions](#-conclusions)

---

## 🎯 Problem Definition

This project is based on a real-world retail dataset capturing Black Friday sales transactions.

The objective is to build a supervised machine learning model that predicts the **purchase amount (USD)** for each transaction using demographic and product-related features.

* **Task type:** Regression
* **Target variable:** `Purchase`
* **Success criterion:** R² ≥ 0.75

---

## 📊 Dataset

| Split | Rows    | Columns |
| ----- | ------- | ------- |
| Train | 550,068 | 12      |
| Test  | 233,599 | 11      |

### 🔑 Features

| Feature                      | Type        | Description            |
| ---------------------------- | ----------- | ---------------------- |
| `User_ID`                    | Identifier  | Unique user ID         |
| `Product_ID`                 | Identifier  | Unique product ID      |
| `Gender`                     | Categorical | M / F                  |
| `Age`                        | Categorical | Age group              |
| `Occupation`                 | Numerical   | Occupation code        |
| `City_Category`              | Categorical | A / B / C              |
| `Stay_In_Current_City_Years` | Ordinal     | Years in city          |
| `Marital_Status`             | Binary      | 0 / 1                  |
| `Product_Category_1`         | Numerical   | Main category          |
| `Product_Category_2`         | Numerical   | Secondary category     |
| `Product_Category_3`         | Numerical   | Dropped (>50% missing) |
| `Purchase` *(target)*        | Numerical   | Amount spent           |

---

## 📁 Project Structure

```id="zjv8s8"
black-friday-sales-prediction/
│
├── Black_Friday.ipynb
├── train.csv
├── test.csv
├── submission.csv
├── best_rf_model.pkl   # (optional - large file, not recommended for GitHub)
└── README.md
```

---

## 🔬 Methodology

### 1. Data Cleaning

* Removed `User_ID`, `Product_ID`
* Dropped `Product_Category_3`
* Cleaned `Stay_In_Current_City_Years`
* Removed duplicates

### 2. Exploratory Data Analysis

* Gender distribution (~75% male)
* Purchase trends by age and occupation
* Outlier analysis
* Product category impact

### 3. Preprocessing

* Median imputation (`Product_Category_2`)
* Label encoding (`Age`)
* One-hot encoding (`Gender`, `City_Category`)
* Log transform on `Purchase`
* Feature scaling

### 4. Modeling

| Model             | Test R²  |
| ----------------- | -------- |
| Linear Regression | 0.19     |
| Decision Tree     | 0.74     |
| Random Forest     | **0.75** |

### 5. Tuning

* GridSearchCV for Decision Tree & Random Forest
* Best RF: ~310 trees, depth = 5

### 6. Prediction

* Applied best model to test set
* Inverse log transform (`np.exp`)
* Saved results → `submission.csv`

---

## 📈 Results

| Metric | Value         |
| ------ | ------------- |
| R²     | 0.75          |
| Model  | Random Forest |

✔️ Meets target performance
✔️ Stable across cross-validation

---

## 🔍 Key Findings

* **Gender:** Males dominate transactions (~75%)
* **Age:** Behavior relatively stable across groups
* **Product categories:** Strongest predictor of purchase value
* **Outliers:** High-value purchases are valid, not noise
* **Log transform:** Significantly improved performance
* **Linear models:** Fail to capture non-linear behavior

---

## 🛠️ Technologies Used

* Python 3
* pandas, numpy
* matplotlib, seaborn
* scikit-learn

  * RandomForestRegressor
  * DecisionTreeRegressor
  * GridSearchCV
* joblib

---

## ▶️ How to Run

```bash id="m7k8yy"
git clone https://github.com/your-username/black-friday-sales-prediction.git
cd black-friday-sales-prediction
pip install pandas numpy matplotlib seaborn scikit-learn joblib jupyter
jupyter notebook Black_Friday.ipynb
```

---

## 📤 Output Files

| File                | Description                                   |
| ------------------- | --------------------------------------------- |
| `submission.csv`    | Final predictions                             |
| `best_rf_model.pkl` | Saved model (excluded from repo if too large) |

---

## 📌 Conclusions

This project demonstrates how tree-based models effectively capture **non-linear purchase behavior** in large-scale retail datasets.

The tuned **Random Forest model** achieved:

* **R² = 0.75**
* strong generalization across folds

### 🚀 Future Improvements

* Feature engineering (user/product aggregation)
* Gradient boosting (XGBoost, LightGBM)
* Target encoding
* Ensemble stacking
