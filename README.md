# PersistancyOfDrugsByDG

# 🧠 Patient Drug Persistency Prediction: Model Evaluation Report

## 🌍 Business Goal

ABC Pharma aims to predict whether patients will persist with their prescribed medications using demographics, clinical history, risk factors, and treatment behavior. This prediction enables physicians to personalize care and improve drug adherence, leading to better patient outcomes.

---

## 🔢 Data Overview

- **Total Rows:** `X` *(to be updated with dataset info)*
- **Total Columns:** `Y` *(to be updated with dataset info)*

### Features

- **Categorical:** Gender, Race, Region, Ethnicity, Speciality, etc.
- **Numeric:** Dexa_Freq_During_Rx_log, Count_Of_Risks
- **Target Variable:** Persistency_Flag (Binary: Persistent = 1, Non-Persistent = 0)

---

## 🧹 Data Cleaning & Preprocessing

- No missing values detected.
- Outliers found in:
  - `Dexa_Freq_During_Rx` (460 outliers) — addressed via log transformation.
  - `Count_Of_Risks` (8 outliers) — handled by clipping.
- Encoding:
  - Binary risk factors (Y/N) converted to 0/1.
  - Nominal categorical features label-encoded.

---

## 📊 Exploratory Data Analysis (EDA)

- **Target Distribution:**
  - Persistent: 1,289 (≈38%)
  - Non-Persistent: 2,135 (≈62%)
- **Risk Factor Counts:** Majority have 0–2 risks.
- **Age Insights:** Persistency is higher in older patients (75+).
- **Specialist Type:** PCP and OB/GYN associated with higher persistency.

Visualizations like count plots, pie charts, and bar graphs are available in the notebook and Streamlit UI.

---

## 🏆 Model Evaluation Summary

| Model                | Accuracy | ROC-AUC | Interpretability         | Business Fit          |
|----------------------|----------|---------|-------------------------|----------------------|
| Logistic Regression  | 0.75     | 0.78    | ⭐⭐⭐⭐⭐ (Highly explainable) | ✅ High               |
| Random Forest        | 0.81     | 0.85    | ⭐⭐⭐                      | ✅ Medium             |
| Gradient Boosting    | 0.84     | 0.88    | ⭐⭐⭐⭐ (Explainable via SHAP) | ✅ High               |
| Stacking Classifier  | 0.86     | 0.89    | ⭐⭐ (Black box)            | ❌ Low                |

---

## 🔧 Final Recommendation

- **Best Overall Model:** `GradientBoostingClassifier`
  - Balanced high accuracy and ROC-AUC.
  - Explainable with SHAP values.
  - Ideal trade-off between performance and business interpretability.

- **Baseline / Explainable Model:** `LogisticRegression`
  - Great for compliance reports and business presentations due to transparency.

---

## 🧪 Confusion Matrix

The confusion matrix is used to evaluate the classification performance by comparing true labels against predicted labels.

> **Note:** If you encounter feature mismatch errors during prediction (e.g., missing feature `"Risk_Osteogenesis_Imperfecta"`), ensure your test dataset contains the exact same features in the same order as used during model training.

---

## 📈 What is the AUC Score?

The **AUC (Area Under the ROC Curve)** measures a model’s ability to distinguish between classes across all classification thresholds.

- **Range:** 0 to 1
- **Interpretation:**
  - 1 = Perfect classifier
  - 0.5 = Random guessing
  - > 0.8 = Good performance
- The ROC curve plots true positive rate vs false positive rate, showing trade-offs at different thresholds.

## 🏆 Model Evaluation Summary

| Model                | Accuracy | ROC-AUC | Interpretability         | Business Fit          |
|----------------------|----------|---------|-------------------------|----------------------|
| Gradient Boosting    | 0.84     | 0.88    | ⭐⭐⭐⭐ (Explainable via SHAP) | ✅ High               |
| Logistic Regression  | 0.75     | 0.78    | ⭐⭐⭐⭐⭐ (Highly explainable) | ✅ High               |
| Random Forest        | 0.81     | 0.85    | ⭐⭐⭐                      | ✅ Medium             |
| Stacking Classifier  | 0.86     | 0.89    | ⭐⭐ (Black box)            | ❌ Low                |

---

## 🧪 Confusion Matrix (Gradient Boosting)

|               | Predicted 0 | Predicted 1 |
|---------------|-------------|-------------|
| **Actual 0**  | 574 (TN)    | 80 (FP)     |
| **Actual 1**  | 116 (FN)    | 258 (TP)    |

- **True Negatives (TN):** 574  
- **False Positives (FP):** 80  
- **False Negatives (FN):** 116  
- **True Positives (TP):** 258  

This confusion matrix demonstrates the model’s classification performance on the test set.

---

## 📈 AUC Score

The **AUC of 0.88** indicates the Gradient Boosting model has a strong ability to distinguish between persistent and non-persistent patients across classification thresholds, representing excellent classification performance.





