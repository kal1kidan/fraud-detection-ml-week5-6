# 🏦 Fraud Detection Using Machine Learning

**Final Project Submission — December 2025**

---

## 📌 Project Overview

This project presents a **complete end-to-end fraud detection system** built using real-world transaction data. It covers the full data science lifecycle — from **data ingestion and cleaning** to **feature engineering, model training, evaluation, and explainability**.

The objective is to **accurately identify fraudulent transactions** while addressing real-world challenges such as **severe class imbalance**, **high-dimensional features**, and **model interpretability for business decisions**.

---

## 📂 Datasets Used

1. **Fraud_Data.csv**

   * E-commerce transaction data
2. **creditcard.csv**

   * Credit card transaction dataset (highly imbalanced)
3. **IpAddress_to_Country.csv**

   * IP address range to country mapping

> **Note:** Raw data files are excluded from the repository and must be placed in the `data/raw/` directory.

---

## 📁 Repository Structure

All code and artifacts are organized into **logical, clearly defined folders**:

```
fraud-detection/
├── .github/
│   └── workflows/
│       └── unittests.yml
├── data/                           # Ignored from GitHub
│   ├── raw/                        # Original datasets (user-provided)
│   └── processed/                  # Cleaned & feature-engineered data
├── notebooks/
│   ├── eda-fraud-data.ipynb
│   ├── eda-creditcard.ipynb
│   ├── feature-engineering.ipynb
│   ├── modeling.ipynb              # Model training & evaluation
│   ├── shap-explainability.ipynb   # Model explainability
│   └── README.md
├── models/
│   └── random_forest_task3.pkl     # Saved trained model
├── src/
│   └── __init__.py
├── tests/
│   └── __init__.py
├── scripts/
│   └── README.md
├── requirements.txt                # Environment dependencies
├── README.md                       # Project documentation
└── .gitignore
```

---

## 🧹 Data Cleaning & Preprocessing

* Removed duplicate records
* Fixed inconsistent data types
* Handled missing values using appropriate imputation strategies
* Converted IP addresses to integers
* Merged transaction data with IP-to-country mapping using **range-based lookup**

---

## ⚙️ Feature Engineering

### Engineered Features

* **Time-based features**

  * `hour_of_day`
  * `day_of_week`
  * `time_since_signup`
* **Behavioral features**

  * `transactions_per_user`
* **IP-based features**

  * `ip_address`
  * `lower_bound_ip_address`
  * `upper_bound_ip_address`
* **Categorical encoding**

  * One-Hot Encoding for `browser`, `source`, `sex`, `country`
* **Numerical scaling**

  * StandardScaler applied where required

---

## 📊 Exploratory Data Analysis (EDA)

Key insights uncovered during analysis:

* Fraud occurs more frequently:

  * Shortly after user signup
  * During unusual hours and days
  * From specific IP ranges
* High transaction velocity is a strong fraud signal
* Severe class imbalance confirmed across datasets

---

## ⚖️ Class Imbalance Strategy

* Fraud transactions represent a very small percentage of total data
* Applied **SMOTE oversampling** on training data only
* Preserved original class distribution in the test set for realistic evaluation

---

## 🤖 Model Training & Evaluation

### Models Implemented

* Logistic Regression (baseline)
* Random Forest Classifier (final model)

### Evaluation Metrics

* F1-Score
* Precision-Recall AUC
* Confusion Matrix
* Classification Report

### Final Model Selection

The **Random Forest classifier** was selected due to:

* Higher recall on fraud cases
* Better balance between false positives and false negatives
* Robust performance on imbalanced data

The trained model is saved under:

```
models/random_forest_task3.pkl
```

---

## 🔍 Model Explainability (SHAP)

To ensure transparency and business interpretability:

* Applied **SHAP (SHapley Additive exPlanations)**
* Generated:

  * Global feature importance plots
  * Local explanations for individual predictions
* Identified **top fraud drivers**:

  * `time_since_signup`
  * `ip_address`
  * IP range features
  * Temporal behavior (`day_of_week`, `hour_of_day`)

---

## 💡 Business Recommendations

1. **Enhanced verification for new users**
   Transactions occurring shortly after signup should receive additional checks.

2. **IP-based fraud monitoring**
   High-risk IP ranges should trigger alerts or secondary authentication.

3. **Time-based monitoring**
   Transactions during unusual hours or days should be flagged for review.

---

## 🛠️ Environment Setup

### Prerequisites

* Python 3.9+
* Virtual environment recommended

### Installation

```bash
pip install -r requirements.txt
```

---

## ▶️ How to Run the Project

1. Place raw datasets in `data/raw/`
2. Run notebooks in the following order:

   * `eda-*.ipynb`
   * `feature-engineering.ipynb`
   * `modeling.ipynb`
   * `shap-explainability.ipynb`

---

## 📌 Final Submission

✔ End-to-end fraud detection pipeline
✔ Clean, well-structured repository
✔ Reproducible environment setup
✔ Interpretable and actionable results

🔗 **GitHub Repository:**
👉 *(https://github.com/kal1kidan/fraud-detection-ml-week5-6)*

