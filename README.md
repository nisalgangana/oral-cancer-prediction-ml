# Oral Cancer Prediction Using Supervised Machine Learning

**SLIIT | Faculty of Computing | MSc in Artificial Intelligence**  
**Module: Fundamentals of Machine Learning | Group Assignment | 2026**

---

## Group Members

| Student ID | Name | Algorithm | Branch |
|------------|------|-----------|--------|
| MS26910222 | Nisal Wickramathilaka | Random Forest | `nisal/random-forest` |
| MS26912752 | Sanduni Mendis | Logistic Regression | `sanduni/logistic-regression` |

---

## Project Overview

This project applies two supervised machine learning algorithms to predict oral cancer diagnosis using clinical and demographic patient data. The models are trained, evaluated, and compared on the same dataset.

**Dataset:** [Oral Cancer Prediction Dataset — Kaggle](https://www.kaggle.com/datasets/ankushpanday2/oral-cancer-prediction-dataset)

| Property | Value |
|----------|-------|
| Total Records | 84,922 patients |
| Total Features | 25 columns |
| Target Variable | Oral Cancer Diagnosis (Yes / No) |
| Class Balance | No: 42,573 (50.1%) \| Yes: 42,349 (49.9%) |
| Missing Values | None |

---

## Repository Structure
oral-cancer-prediction-ml/
├── nisal_random_forest.ipynb                    # Nisal — Random Forest
├── sanduni_logistic_regression.ipynb            # Sanduni — Logistic Regression
├── oral_cancer_prediction_dataset.csv           # Dataset
└── README.md

---

## Methodology

### Data Preprocessing (Both)
- Removed 6 post-diagnosis columns to prevent data leakage (Treatment Type, Survival Rate, Cost of Treatment, Economic Burden, ID, Country)
- Applied Label Encoding to all categorical Yes/No features
- Train/Test Split: 80% training (67,937 samples) / 20% testing (16,985 samples) with stratification

### Algorithm 1 — Random Forest (Nisal Wickramathilaka)
- **Model:** RandomForestClassifier (scikit-learn)
- **Configuration:** 100 estimators, random_state=42
- **Feature Scaling:** Not required (tree-based algorithm)
- **Extras:** Feature Importance visualization

### Algorithm 2 — Logistic Regression (Sanduni Mendis)
- **Model:** LogisticRegression (scikit-learn)
- **Configuration:** max_iter=1000, random_state=42
- **Feature Scaling:** StandardScaler applied
- **Extras:** ROC Curve visualization

---

## Results

| Metric | Random Forest (Nisal) | Logistic Regression (Sanduni) |
|--------|----------------------|-------------------------------|
| Accuracy | 100.00% | 100.00% |
| Precision | 1.0000 | 1.0000 |
| Recall | 1.0000 | 1.0000 |
| F1 Score | 1.0000 | 1.0000 |
| True Positive | 8,470 | 8,470 |
| True Negative | 8,515 | 8,515 |
| False Positive | 0 | 0 |
| False Negative | 0 | 0 |

> **Important Note:** The 100% accuracy is primarily caused by **data leakage** from the features *Cancer Stage* and *Tumor Size (cm)*, which are post-diagnosis features that dominate model predictions. This is discussed in detail in the report.

---

## Key Findings

- Both algorithms achieved identical perfect accuracy due to data leakage
- Feature Importance analysis (Random Forest) shows Cancer Stage (>0.45) and Tumor Size (>0.45) dominate predictions
- All genuine pre-diagnosis risk factors (Tobacco Use, HPV Infection, Oral Hygiene) contribute negligibly
- For future work: remove leakage features and retrain on pre-diagnosis indicators only

---

## Technologies Used

| Tool | Purpose |
|------|---------|
| Python 3.x | Programming language |
| pandas, numpy | Data manipulation |
| matplotlib, seaborn | Visualization |
| scikit-learn | Machine learning models |
| Jupyter Notebook | Development environment |
| Anaconda | Environment management |
| Git / GitHub | Version control |

---

## Video Presentations

| Member | YouTube Link |
|--------|-------------|
| Nisal Wickramathilaka | https://www.youtube.com/watch?v=7vSToH7uN9c |

---

## References

1. Breiman, L. (2001). Random forests. *Machine learning*, 45(1), 5-32.
2. Cox, D. R. (1958). The regression analysis of binary sequences. *Journal of the Royal Statistical Society*, 20(2), 215-242.
3. Pedregosa, F., et al. (2011). Scikit-learn: Machine learning in Python. *Journal of Machine Learning Research*, 12, 2825-2830.
4. Oral Cancer Prediction Dataset. (2024). Kaggle. https://www.kaggle.com/datasets/ankushpanday2/oral-cancer-prediction-dataset
