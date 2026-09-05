
# Hospital Length of Stay Prediction

## Overview

This project focuses on predicting the **Length of Stay (LOS)** of hospital patients using demographic, hospital, admission, diagnosis, and other available patient-related information.

The problem is formulated as a **regression problem**, where the target variable represents the number of days a patient stays in the hospital.

## Objective

The objective of this project is to develop a machine learning model that can predict a patient's hospital length of stay using information available from the hospital admission records.

Accurate LOS prediction can potentially support hospital resource planning, bed management, and operational decision-making.

## Dataset

The project uses the **New York State SPARCS Hospital Inpatient Discharges** dataset.

The dataset contains approximately **2.2 million hospital discharge records** with 33 original features.

The dataset is not included directly in this repository because of its large size. The source and download information are provided in the [`data`](data/) folder.

## Project Workflow

The project follows the following machine learning workflow:

1. Dataset loading and inspection
2. Exploratory Data Analysis
3. Missing-value analysis
4. Target variable cleaning
5. Feature selection
6. Data leakage prevention
7. Train-test splitting
8. Numerical and categorical preprocessing
9. Model training
10. Model evaluation
11. Model comparison
12. Feature importance analysis

## Models Used

The following regression models were evaluated:

* Linear Regression
* Random Forest Regressor
* XGBoost Regressor
* CatBoost Regressor

## Preprocessing

The dataset contains both numerical and categorical features.

Numerical missing values are handled using median imputation, while missing categorical values are represented using a separate `"Missing"` category.

Categorical features used by the scikit-learn models are transformed using One-Hot Encoding.

For CatBoost, categorical variables are handled using CatBoost's native categorical-feature support.

Several features were removed because they were redundant, uninformative, identifier-like, or potentially associated with information available only after or during the hospitalization.

## Model Performance

| Model             |      MAE ↓ |     RMSE ↓ |       R² ↑ |
| ----------------- | ---------: | ---------: | ---------: |
| Linear Regression |     4.0588 |     8.0955 |     0.1679 |
| Random Forest     |     4.0424 |     8.1561 |     0.1554 |
| XGBoost           |     3.8742 |     7.9807 |     0.1914 |
| **CatBoost**      | **3.7721** | **7.8920** | **0.2092** |

### Best Performing Model

Based on the current experiments, **CatBoost achieved the best overall performance**.

It obtained:

* **MAE:** 3.7721 days
* **RMSE:** 7.8920 days
* **R²:** 0.2092

This means that the CatBoost model's predictions differ from the actual length of stay by approximately **3.77 days on average**, according to MAE.

## Results

The project also includes:

* Actual vs Predicted Length of Stay visualization
* CatBoost feature importance analysis
* Model performance comparison

The feature-importance analysis provides insight into which variables the CatBoost model relied on most strongly when making predictions.

## Current Limitations

The dataset is very large, so the tree-based models were initially trained using a **200,000-record subset** of the available training data due to computational constraints.

Therefore, the current results should be considered an **initial benchmark** rather than a final optimized model comparison.

The current R² also indicates that a substantial portion of the variation in hospital length of stay remains unexplained by the current feature set and model configuration.

## Future Work

Future improvements include:

* Training the selected model on a larger portion of the training data
* Hyperparameter tuning
* Exploring additional relevant features
* Evaluating additional regression techniques
* Further analysis of prediction errors
* Exploring alternative approaches for the highly skewed Length of Stay target

## Repository Structure

```text
hospital-length-of-stay-prediction/
│
├── data/
│   └── README.md
│
├── notebooks/
│   └── LOS_Prediction.ipynb
│
├── results/
│   ├── feature_importance.png
│   ├── actual_vs_predicted.png
│   └── model_comparison.png
│
├── README.md
├── requirements.txt
└── .gitignore
```

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* XGBoost
* CatBoost
* Google Colab
* Jupyter Notebook

## Project Status

**Current Status: Initial Model Benchmark **

Further model optimization and experimentation will be performed as future work.

