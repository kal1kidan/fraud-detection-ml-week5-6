# Fraud Detection Project

## Overview
This project focuses on detecting fraudulent transactions using two datasets:
1. `Fraud_Data.csv` (E-commerce transactions)
2. `creditcard.csv` (Credit card transactions)

The goal is to clean, preprocess, and engineer features, then train machine learning models to detect fraud while handling class imbalance.

## Project Structure

```

fraud-detection/
├── .vscode/
│   └── settings.json
├── .github/
│   └── workflows/
│       └── unittests.yml
├── data/                           # Added to .gitignore
│   ├── raw/                        # Original datasets
│   └── processed/                  # Cleaned and feature-engineered data
├── notebooks/
│   ├── eda-fraud-data.ipynb
│   ├── eda-creditcard.ipynb
│   ├── feature-engineering.ipynb
│   ├── modeling.ipynb
│   ├── shap-explainability.ipynb
│   └── README.md
├── src/
│   └── **init**.py
├── tests/
│   └── **init**.py
├── models/                          # Saved ML models
├── scripts/
│   └── README.md
├── requirements.txt
├── README.md
└── .gitignore

```

## Data Cleaning & Preprocessing

- Removed duplicates and corrected data types.
- Imputed missing values where necessary.
- Converted IP addresses to integers for geolocation mapping.
- Merged `Fraud_Data.csv` with `IpAddress_to_Country.csv` using a range-based lookup.

## Feature Engineering

- Created time-based features:
  - `hour_of_day`
  - `day_of_week`
  - `time_since_signup` (purchase_time - signup_time)
- Transaction velocity: number of transactions per user.
- Categorical encoding: One-Hot Encoding for `device_id`, `browser`, `source`, `sex`, `country`.
- Normalized numerical features using StandardScaler.

## Class Imbalance Handling

- Observed severe class imbalance (`fraud` << `non-fraud`).
- Applied SMOTE (on training data only) to oversample minority class.
- Documented class distributions before and after resampling.

## Exploratory Data Analysis (EDA) Insights

- Fraud patterns more prevalent in specific countries and peak hours.
- High-value transactions are slightly more prone to fraud.
- Transaction frequency per user varies, indicating potential velocity-based fraud signals.

## Next Steps

- Task 2: Build and evaluate models (Logistic Regression baseline, Random Forest ensemble) with stratified cross-validation.
- Task 3: Model explainability using SHAP for actionable insights.

```

---

## 2️⃣ Interim Report (Markdown for `reports/interim_task1.md`)

```markdown
# Interim Report 1 - Data Analysis and Preprocessing
**Submission Date:** Sunday, 21 Dec, 2025

## 1. Datasets Overview
- **Fraud_Data.csv**: E-commerce transaction records
- **creditcard.csv**: Credit card transaction records
- **IpAddress_to_Country.csv**: IP-to-country mapping

## 2. Data Cleaning
- Handled missing values using imputation or row removal with justification.
- Removed duplicate rows.
- Corrected data types for timestamps, numeric fields, and categorical variables.

## 3. Feature Engineering
- **Time-based features**
  - `hour_of_day`, `day_of_week`
  - `time_since_signup`: calculated as purchase_time - signup_time
- **Transaction velocity**
  - `transactions_per_user`: count of transactions per user
- **IP Geolocation**
  - Converted IP addresses to integers
  - Merged with `IpAddress_to_Country.csv` using range-based lookup
  - Created `country_mapped` for each transaction
- One-Hot Encoded categorical features: `device_id`, `browser`, `source`, `sex`, `country_mapped`
- Scaled numerical features using StandardScaler

## 4. Exploratory Data Analysis (EDA)
- Univariate analysis: distributions of purchase_value, user age, transaction frequency
- Bivariate analysis: relationships between features and target
- Visualized class distribution:
  - Severe imbalance between `fraud` and `non-fraud` transactions
- Fraud hotspots by country and hour of day identified

## 5. Class Imbalance Strategy
- Applied SMOTE oversampling on training data to balance classes.
- Verified distribution post-resampling.
- Justification: Preserves majority class information while giving minority class adequate representation.

## 6. Key Insights
- Fraudulent transactions tend to cluster in specific countries.
- High-frequency users occasionally contribute to suspicious transactions.
- Timing patterns (`hour_of_day`, `day_of_week`) influence fraud likelihood.
- Model-ready datasets created for Task 2 modeling.

## 7. Next Steps
- Task 2: Train models (Logistic Regression baseline, Random Forest/XGBoost ensemble).
- Task 3: Explain model predictions using SHAP and provide actionable business insights.
```

