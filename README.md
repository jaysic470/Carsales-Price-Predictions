# Used Car Price Prediction – Rusty Bargain

This project was developed for **Rusty Bargain**, a used car sales service, with the goal of building a machine learning model to accurately predict vehicle prices based on their technical specifications and historical listing data. This model is intended to power an internal pricing tool that helps customers get a fast and reliable quote for their car.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Business Objective](#business-objective)
- [Process Summary](#process-summary)
- [Modeling & Evaluation](#modeling--evaluation)
- [Key Findings](#key-findings)
- [Recommendations](#recommendations)
- [Tools Used](#tools-used)
- [Project Structure](#project-structure)

---

## Project Overview

The goal was to train, compare, and tune multiple regression models to estimate car prices as accurately and efficiently as possible. The project evaluated:

- **Prediction quality** (RMSE)
- **Training time**
- **Inference speed**

---

## Dataset

- Over 350,000 entries
- 16 features including:
  - Vehicle type, brand, model
  - Engine power and registration year
  - Fuel type, transmission, mileage
  - Price (target variable)

Certain features such as `DateCreated`, `LastSeen`, and `PostalCode` were dropped due to irrelevance or data leakage risk.

---

## Business Objective

- Build a model that balances **accuracy and speed**.
- Recommend the best approach for real-time deployment in Rusty Bargain's pricing engine.

---

## Process Summary

1. **Data Cleaning & Preprocessing**
   - Removed irrelevant or data-leaking columns
   - Handled missing values and categorical encoding
   - Split data into train/validation/test sets (75/25)

2. **Feature Engineering**
   - Categorical variables encoded via `OrdinalEncoder` and `OneHotEncoder`
   - Log transformation applied to the target (`Price`)

3. **Model Training & Testing**
   - Linear Regression
   - Decision Tree (baseline)
   - Random Forest (with and without hyperparameter tuning)
   - CatBoost, LightGBM, XGBoost

---

## Modeling & Evaluation

### Evaluation Metric: RMSE (Root Mean Squared Error)

| Model            | RMSE (Validation) | Training Time | Inference Speed |
|------------------|-------------------|----------------|------------------|
| Decision Tree    | ~2200             | Very Fast      | Instant          |
| Random Forest    | ~1900             | Fast           | Fast             |
| XGBoost          | **~1800**         | Moderate       | Fast             |
| CatBoost         | ~1820             | Slow           | Fast             |
| Linear Regression| ~2800             | Fast           | Fast             |

---

## Key Findings

- **XGBoost** achieved the best balance between accuracy and inference speed.
- **CatBoost** was also highly accurate but slower to train.
- Simpler models like Decision Tree performed poorly in predictive accuracy.

---

## Recommendations

- **Deploy XGBoost** as the production model for pricing estimates.
- Consider retraining quarterly as new market data is collected.
- Optimize further by deploying with batch inference or caching popular queries.

---

## Tools Used

- Python (pandas, NumPy)
- Scikit-learn
- XGBoost, LightGBM, CatBoost
- Matplotlib, Seaborn
- Jupyter Notebook

---

## Project Structure
Carsales-Price-Predictions/
├── Carsales-Price-Predictions.ipynb # Full notebook
├── README.md # This file
└── datasets/
└── vehicles_us.csv # Main dataset (large file)
