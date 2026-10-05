# Tanushree_BreastCancerClassification

## Project Overview

This project is a complete end-to-end machine learning solution for classifying breast tumors as **Malignant** or **Benign** using the Breast Cancer Wisconsin (Diagnostic) Dataset from the UCI Machine Learning Repository. The project was developed as part of a machine learning internship and covers the full data science pipeline — from data exploration and preprocessing to model training, evaluation, and interpretation.

---

## Problem Statement

Given 30 numerical features extracted from digitized images of fine needle aspirate (FNA) of breast masses, build a binary classification model that accurately predicts whether a tumor is **Malignant (M)** or **Benign (B)**. In a medical screening context, minimizing false negatives (missed malignant cases) is of paramount importance.

---

## Objectives

- Analyze and understand the Breast Cancer Wisconsin Diagnostic dataset
- Perform thorough Exploratory Data Analysis (EDA)
- Preprocess the data (encoding, scaling) without data leakage
- Train and evaluate three machine learning models
- Compare model performance using multiple metrics
- Select the best-performing model
- Interpret model outputs and feature importances

---

## Dataset

| Property | Value |
|---|---|
| **Source** | UCI Machine Learning Repository |(https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic)
| **File** | `wdbc.data` |
| **Total Samples** | 569 |
| **Number of Features** | 30 (numerical, real-valued) |
| **Target Variable** | `diagnosis` (M = Malignant, B = Benign) |
| **Benign Samples** | 357 (62.7%) |
| **Malignant Samples** | 212 (37.3%) |
| **Missing Values** | None |
| **Duplicate Rows** | None |

Features are computed from cell nucleus characteristics in three groups:
- **Mean** values (10 features)
- **Standard Error** values (10 features)
- **Worst** (largest) values (10 features)

---

## Technologies Used

| Category | Tools / Libraries |
|---|---|
| Language | Python 3.9+ |
| Data Manipulation | pandas, numpy |
| Visualization | matplotlib, seaborn |
| Machine Learning | scikit-learn |
| Notebook | Jupyter Notebook |
| Report | python-docx |

---

## Project Structure

```text
Tanushree_BreastCancerClassification/
│
├── Tanushree_BreastCancerClassification.ipynb   ← Main Jupyter Notebook
├── requirements.txt                              ← Python dependencies
├── Tanushree_BreastCancerClassificationReport.docx ← Project report
├── README.md                                     ← This file
└── data/
    └── wdbc.data                                 ← Dataset (UCI WDBC)
```

---

## Installation

1. Ensure Python 3.9+ is installed (Anaconda recommended).
2. Clone or download this project folder.
3. Install the required dependencies:

```bash
pip install -r requirements.txt
```

---

## How to Run

1. Open a terminal/Anaconda Prompt in the project folder.
2. Launch Jupyter Notebook:

```bash
jupyter notebook
```

3. Open `Tanushree_BreastCancerClassification.ipynb`.
4. Run all cells sequentially: **Kernel → Restart & Run All**.

> **Note:** The dataset file `data/wdbc.data` must be present in the `data/` subdirectory relative to the notebook.

---

## Methodology

```
Dataset (wdbc.data)
        │
        ▼
  Data Loading & Column Assignment
        │
        ▼
  Data Cleaning
  (Drop 'id' column, check missing/duplicates)
        │
        ▼
  Exploratory Data Analysis
  (Class distribution, histograms, boxplots,
   correlation heatmap, violin plots, pair plots)
        │
        ▼
  Data Preprocessing
  (Target encoding: M→1, B→0)
        │
        ▼
  Train / Test Split (80% / 20%, stratified)
        │
        ▼
  Feature Scaling
  (StandardScaler — fitted on train only)
        │
        ▼
  Model Training
  (Logistic Regression | SVM (RBF) | Random Forest)
        │
        ▼
  Model Evaluation
  (Accuracy, Precision, Recall, F1, ROC-AUC,
   Confusion Matrix, Classification Report, ROC Curve)
        │
        ▼
  Model Comparison & Best Model Selection
        │
        ▼
  Feature Importance / Interpretation
```

---

## Machine Learning Models

| # | Model | Key Hyperparameters |
|---|---|---|
| 1 | **Logistic Regression** | `max_iter=1000`, `random_state=42` |
| 2 | **Support Vector Machine (SVM)** | `kernel='rbf'`, `probability=True`, `random_state=42` |
| 3 | **Random Forest Classifier** | `n_estimators=100`, `random_state=42` |

---

## Evaluation Metrics

| Metric | Description |
|---|---|
| **Accuracy** | Proportion of correctly classified samples |
| **Precision** | Of all predicted malignant, how many were truly malignant |
| **Recall (Sensitivity)** | Of all truly malignant cases, how many were correctly identified *(critical in medical context)* |
| **F1-Score** | Harmonic mean of Precision and Recall |
| **ROC-AUC** | Area under the Receiver Operating Characteristic curve — overall discriminative ability |

---

## Results

> Results obtained by executing the notebook on the WDBC dataset with `random_state=42` and an 80/20 train-test split.

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---|---|---|---|---|
| **Logistic Regression** | 0.9649 | 0.9750 | 0.9286 | 0.9512 | 0.9960 |
| **SVM (RBF)** | 0.9737 | 1.0000 | 0.9286 | 0.9630 | 0.9947 |
| **Random Forest** | 0.9737 | 1.0000 | 0.9286 | 0.9630 | 0.9929 |

**Best Model:** SVM (RBF) — highest accuracy (97.37%) and perfect precision (1.0000) with the highest ROC-AUC among tied models.

### Key Findings

- All three models achieved **>96% accuracy** on the held-out test set.
- **SVM (RBF)** and **Random Forest** tied on accuracy, precision, recall, and F1, with SVM having a slightly higher ROC-AUC (0.9947 vs 0.9929).
- **Logistic Regression** achieved the highest ROC-AUC of **0.9960**, demonstrating excellent probabilistic discrimination.
- Top predictive features: `area_worst`, `concave_points_worst`, `radius_worst`, `perimeter_worst`, `concave_points_mean`.
- Only **3 false negatives** (missed malignant cases) across all three models on the test set of 114 samples.

---

## Conclusion

This project demonstrates that machine learning can achieve high diagnostic accuracy for breast cancer classification. SVM (RBF) and Random Forest emerged as the best-performing models with 97.37% accuracy. The Logistic Regression model, while slightly lower in accuracy, achieved the highest ROC-AUC score (0.9960), indicating strong probabilistic separability.

All models should be interpreted carefully in a clinical setting — **recall (sensitivity) for malignant cases** is the most critical metric, and the 3 false negatives observed underscore that no model should replace professional medical diagnosis.

---

## Disclaimer

> This project is developed for **educational and internship purposes only**. The models and results presented here are based on a benchmark academic dataset and **should not be used as a substitute for professional clinical diagnosis**. Always consult a qualified medical professional for any health-related decisions.
