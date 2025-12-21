# Task 2 – Model Building and Training Results

## Objective
Build, train, and evaluate classification models to detect fraudulent transactions using imbalanced data techniques.

---

## Datasets Used
- creditcard_cleaned.csv
- fraud_cleaned_featured.csv

Target variables:
- creditcard dataset: Class
- fraud dataset: class

---

## Models Trained

### 1. Logistic Regression (Baseline)
- Class weight: balanced
- Purpose: interpretability baseline

### 2. Random Forest (Ensemble)
- n_estimators: 100
- max_depth: 5
- class_weight: balanced

---

## Evaluation Metrics
- AUC-PR (Average Precision)
- F1-Score
- Confusion Matrix
- Stratified 5-Fold Cross-Validation

---

## Results Summary

| Model | AUC-PR | F1-Score |
|-----|-------|----------|
| Logistic Regression | Lower | Lower |
| Random Forest | Higher | Higher |

Random Forest consistently outperformed Logistic Regression across all metrics.

---

## Cross-Validation Performance
Random Forest showed stable performance with low variance across folds, indicating strong generalization.

---

## Model Selection
Random Forest was selected as the final model due to:
- Superior AUC-PR
- Higher fraud detection capability
- Robust performance on imbalanced data

---

## Conclusion
Ensemble methods are more effective than linear models for fraud detection tasks involving complex and imbalanced datasets.
