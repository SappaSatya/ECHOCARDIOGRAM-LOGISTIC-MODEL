# 🫀 Echocardiogram-Based Survival Prediction (Cognibot Internship Project)

This project was completed as part of my internship at **Cognibot** and focuses on predicting **1-year survival** after a heart attack using clinical features extracted from **echocardiogram** test data. The goal was to apply machine learning techniques on real-world medical data for a critical classification problem.

---

## 🚀 Project Objectives

- Predict whether a patient survived at least one year after a heart attack.
- Explore the importance of echocardiographic features like wall motion, heart size, and contraction strength.
- Build and compare different classification models using Python.

---

## 🧠 Machine Learning Techniques Used

- Data Cleaning & Preprocessing
- Outlier Detection using **Local Outlier Factor**
- Feature Scaling using **StandardScaler**
- Model Training:
  - **Decision Tree Classifier**
  - **XGBoost Classifier**
- Hyperparameter Tuning using **RandomizedSearchCV**
- Cross-Validation and AUC Score Evaluation
- Data Visualization for interpretation and insight

---

## 🗃️ Dataset Overview

- **Source**: UCI Echocardiogram Dataset  
- **Records**: 132 patients  
- **Target Variable**: `alive` (1 = Alive, 0 = Deceased)  
- **Key Features**:
  - `age`, `pericardialeffusion`, `fractionalshortening`, `epss`, `lvdd`, `wallmotion-index`, etc.

---

## 📊 Performance

| Model            | Metric      | Score  |
|------------------|-------------|--------|
| Decision Tree    | Accuracy    | ~0.78  |
| **XGBoost**      | **AUC Score** | **0.82**  |

---

## 🛠️ Technologies Used

- **Language**: Python 3.8
- **Notebook**: Jupyter (via Anaconda)
- **Libraries**:  
  - `pandas`, `numpy`, `matplotlib`, `seaborn`
  - `scikit-learn`, `xgboost`
  - `LocalOutlierFactor` for anomaly detection

---

## 🧹 Data Preprocessing Steps

1. Dropped irrelevant columns (`name`, `group`, `aliveat1`)
2. Filled missing values:
   - Mean/Median for numeric columns
   - Mode for categorical columns
3. Detected and optionally removed outliers
4. Scaled numerical features using `StandardScaler`
5. Encoded categorical features if needed

---

## 📈 Model Training & Evaluation

```python
from sklearn.tree import DecisionTreeClassifier
from xgboost import XGBClassifier
from sklearn.model_selection import RandomizedSearchCV, cross_val_score
from sklearn.metrics import classification_report, roc_auc_score
