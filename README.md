# Telco Customer Churn – Data Acquisition and Preprocessing

## Project Overview

This project demonstrates a complete data acquisition and preprocessing
pipeline developed in Python using the Telco Customer Churn dataset.

The objective is to transform raw customer data into a clean dataset
suitable for further exploratory analysis and machine learning.

## Objectives

- Acquire a publicly available dataset
- Inspect the dataset structure
- Handle missing values
- Convert incorrect data types
- Investigate duplicate records
- Detect outliers
- Encode categorical variables
- Normalize numerical features
- Perform correlation analysis
- Validate the final dataset

## Tools and Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Google Colab

## Preprocessing Workflow

1. Data acquisition
2. Initial data inspection
3. Missing-value analysis
4. Data-type conversion
5. Missing-value handling
6. Duplicate analysis
7. Outlier detection
8. Identifier removal
9. Categorical encoding
10. Min-Max scaling
11. Correlation analysis
12. Final dataset validation

## Key Results

- Original dataset: 7,043 rows × 21 columns
- Final dataset: 7,043 rows × 31 columns
- Missing values: 0
- Object columns: 0
- Infinite values: 0
- Exact duplicate rows: 22
- IQR outliers detected in selected numerical features: 0

## Duplicate Analysis

Duplicate records were investigated rather than being removed blindly.
Repeated feature profiles were examined to determine whether they
represented genuinely identical observations or valid customers with
different outcomes.

## Future Work

The processed dataset can be used for:

- Exploratory Data Analysis
- Logistic Regression
- Decision Tree
- Random Forest
- Model evaluation
- Feature importance analysis
- Customer churn prediction

## Project Structure

```text
telco-customer-churn-preprocessing/
│
├── README.md
│
├── notebook/
│   └── Week_1_Telco_Customer_Churn_Preprocessing.ipynb
│
├── data/
│
├── report/
│
└── outputs/