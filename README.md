# Churn Analysis and Prediction

This project focuses on analyzing customer churn data and building predictive models to identify factors influencing churn and predict customer churn probabilities. The workflow includes data exploration, cleaning, visualization, and building machine learning models using Decision Tree and Random Forest classifiers.

## Table of Contents

1. [Introduction](#introduction)
2. [Dataset Overview](#dataset-overview)
3. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
4. [Data Preprocessing](#data-preprocessing)
5. [Model Building](#model-building)
6. [Model Evaluation](#model-evaluation)
7. [Key Insights](#key-insights)
8. [How to Use](#how-to-use)
9. [Future Work](#future-work)
10. [References](#references)

## Introduction

Customer churn refers to the rate at which customers stop doing business with an entity. Predicting churn allows businesses to proactively retain customers by understanding the factors driving churn. This project utilizes the Telco Customer Churn dataset to explore churn factors and build predictive models.

## Dataset Overview

The dataset contains information about customer demographics, account information, and services provided. Key attributes include:

- `gender`, `SeniorCitizen`, `Partner`, `Dependents`
- `tenure`, `PhoneService`, `MultipleLines`, `InternetService`
- `Contract`, `PaymentMethod`, `MonthlyCharges`, `TotalCharges`
- `Churn`: The target variable (Yes/No).

### Dataset Shape

- Rows: 7043
- Columns: 21

## Exploratory Data Analysis (EDA)

### Key Findings:

1. **Churn Distribution**:
   - 26.54% customers have churned.
   - Imbalanced dataset.

2. **Monthly and Total Charges**:
   - Higher churn is observed among customers with higher monthly charges.

3. **Contract Type**:
   - Month-to-month contracts have the highest churn rate.

4. **Tech Support**:
   - Customers without tech support are more likely to churn.

5. **Senior Citizens**:
   - Higher churn observed among senior citizens.

### Visualizations:

- Churn distribution bar plot
- Density plots for MonthlyCharges and TotalCharges
- Heatmap of feature correlations

## Data Preprocessing

1. **Missing Values**:
   - 11 missing values in `TotalCharges` column were dropped.

2. **Feature Engineering**:
   - Created tenure groups (e.g., `1-12`, `13-24`, etc.).
   - Converted categorical variables into dummy variables.

3. **Target Encoding**:
   - Converted `Churn` column to binary (Yes = 1, No = 0).

## Model Building

### Models Used:

1. **Decision Tree Classifier**
   - Criterion: Gini
   - Max Depth: 6
   - Min Samples per Leaf: 8

2. **Random Forest Classifier**
   - Number of Estimators: 100
   - Criterion: Gini
   - Max Depth: 6
   - Min Samples per Leaf: 8

3. **Handling Imbalance**:
   - SMOTEENN technique was used to handle class imbalance.

## Model Evaluation

### Decision Tree Classifier:

- Accuracy: 79.96%
- F1-Score (Class 1 - Churn): 58%

### Random Forest Classifier:

- Accuracy: 81.87%
- F1-Score (Class 1 - Churn): 59%

### SMOTEENN + Decision Tree Classifier:

- Accuracy: 92.55%
- F1-Score (Class 1 - Churn): 93%

### SMOTEENN + Random Forest Classifier:

- Accuracy: 93.44%
- F1-Score (Class 1 - Churn): 94%

## Key Insights

- Month-to-month contracts and lack of tech support significantly impact churn.
- SMOTEENN improves model performance by addressing class imbalance.
- Random Forest with SMOTEENN achieves the best results.

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/vimukthixsandeepa/churn-analysis.git
   ```
2. Install required packages:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the EDA script:
   ```bash
   python eda.py
   ```
4. Train models:
   ```bash
   python model_building.py
   ```
5. Evaluate the model:
   ```bash
   python evaluate.py
   ```

## Future Work

- Include more features for enhanced predictions.
- Experiment with other algorithms like XGBoost or SVM.
- Deploy the model as a web service.

## References

- Telco Customer Churn Dataset: [Kaggle](https://www.kaggle.com/blastchar/telco-customer-churn)
- SMOTEENN Documentation: [imbalanced-learn](https://imbalanced-learn.org/stable/references/generated/imblearn.combine.SMOTEENN.html)
