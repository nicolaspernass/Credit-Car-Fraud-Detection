# Credit Card Fraud Detection

## Overview
This project addresses the problem of detecting fraudulent credit card transactions using machine learning techniques under extreme class imbalance. The analysis focuses on appropriate evaluation metrics, decision thresholds, and model comparison from both a technical and practical (business-oriented) perspective.

The goal is not to maximize accuracy, but to understand and control the trade-off between fraud detection and false alerts.

---

## Dataset
The dataset consists of anonymized credit card transactions, where fraudulent cases represent a very small fraction of the total observations.

- Target variable: `Class`  
  - `0`: Legitimate transaction  
  - `1`: Fraudulent transaction
- Features:
  - `V1`–`V28`: anonymized variables obtained via PCA
  - `Time` and `Amount`: original, non-transformed features

Due to confidentiality constraints, the original meaning of the PCA components is unknown, but they retain strong discriminative information.

---

## Methodology

### 1. Exploratory Data Analysis (EDA)
- Analysis of feature distributions and outliers
- Confirmation of extreme class imbalance
- Identification of statistical differences between fraudulent and legitimate transactions

Outliers are treated as informative signals rather than noise, given the anomaly-driven nature of fraud detection.

---

### 2. Data Preprocessing
- Stratified train/test split to preserve class distribution
- Feature scaling applied only to `Time` and `Amount`
- Careful handling to avoid data leakage

---

### 3. Models

#### Logistic Regression (Baseline)
- Used as an interpretable baseline model
- Demonstrates the limitations of default decision thresholds in imbalanced settings
- Performance significantly improves through threshold analysis

#### Random Forest (Final Model)
- Non-linear ensemble model capable of capturing complex interactions
- Achieves strong performance without explicit threshold tuning
- Provides higher-quality alerts compared to the baseline

---

## Evaluation Metrics
Given the severe class imbalance, standard accuracy is not used as a primary metric. Instead, the following are emphasized:

- Precision and Recall (fraud class)
- ROC–AUC
- Precision–Recall Curve
- Average Precision (AP)

---

## Results Summary

| Model              | Precision (Fraud) | Recall (Fraud) | ROC–AUC | Average Precision |
|--------------------|------------------|---------------|---------|-------------------|
| Logistic Regression (tuned) | ~0.39 | ~0.89 | ~0.97 | ~0.72 |
| **Random Forest** | **0.67** | **0.86** | **0.98** | **0.81** |

The Random Forest model delivers a superior balance between fraud detection and false positives without requiring extensive threshold tuning.

---

## Conclusions
Random Forest outperforms the logistic regression baseline by providing higher-quality alerts while maintaining strong fraud detection rates. Its robust ranking performance and favorable precision–recall trade-off make it a more deployment-ready solution in highly imbalanced fraud detection scenarios.

---

## Future Work
- Hyperparameter optimization
- Cost-sensitive learning
- Probability calibration
- Evaluation under temporal data drift (concept drift)

---

## Requirements
- Python 3.x
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn

---

## Author
Project developed as part of a data science portfolio, focusing on practical and interpretable machine learning solutions.
