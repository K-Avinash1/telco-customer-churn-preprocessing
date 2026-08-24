# Telco Customer Churn – Data Preprocessing, EDA and Visualization

## Project Overview

This project demonstrates a complete data preparation and exploratory analysis workflow developed in Python using the Telco Customer Churn dataset.

The project is divided into two stages:

- **Week 1:** Data Acquisition and Preprocessing
- **Week 2:** Exploratory Data Analysis (EDA) and Visualization

The objective is to understand, clean, validate and explore customer data before using it for further machine learning and customer churn prediction.

---

# Week 1 – Data Acquisition and Preprocessing

## Objectives

- Acquire a publicly available dataset
- Inspect the dataset structure
- Analyze missing values
- Convert incorrect data types
- Investigate duplicate records
- Detect outliers
- Remove unnecessary identifiers
- Encode categorical variables
- Normalize numerical features
- Perform correlation analysis
- Validate the final dataset

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

## Week 1 Key Results

- Original dataset: **7,043 rows × 21 columns**
- Final encoded dataset: **7,043 rows × 31 columns**
- Missing values: **0**
- Object columns: **0**
- Infinite values: **0**
- Exact duplicate rows in final validation: **22**
- Duplicate feature profiles identified: **33**
- Feature profiles with different Churn values: **18**
- IQR outliers detected in selected numerical features: **0**

## Duplicate Analysis

Duplicate records were investigated rather than being removed blindly.

Repeated feature profiles were examined to determine whether they represented genuinely identical observations or valid customers with different Churn outcomes.

This analysis identified:

- **33 duplicate feature profiles**
- **18 profiles with different Churn values**

Therefore, duplicate-looking records were treated carefully rather than automatically deleted.

---

# Week 2 – Exploratory Data Analysis and Visualization

## Objectives

The objective of Week 2 was to perform an in-depth Exploratory Data Analysis (EDA) and visualization of the original Telco Customer Churn dataset.

The analysis focused on:

- Dataset structure and validation
- Missing-value analysis
- Duplicate analysis
- Unique-value analysis
- Descriptive statistics
- Churn distribution
- Numerical feature distributions
- Categorical feature distributions
- Churn analysis by customer segments
- Correlation analysis
- Outlier analysis
- Business insights

## Week 2 EDA Workflow

1. Load the original dataset
2. Inspect dataset shape and structure
3. Analyze missing values
4. Check duplicate records
5. Analyze unique values
6. Validate numerical data types
7. Handle `TotalCharges` conversion
8. Calculate descriptive statistics
9. Analyze Churn distribution
10. Visualize numerical features
11. Visualize categorical features
12. Analyze churn by Contract
13. Analyze churn by Internet Service
14. Analyze churn by Payment Method
15. Compare Tenure by Churn status
16. Compare Monthly Charges by Churn status
17. Perform correlation analysis
18. Perform IQR-based outlier analysis
19. Generate visualizations
20. Document key findings and business insights

## Dataset Validation

The Week 2 analysis confirmed:

- Dataset size: **7,043 rows × 21 columns**
- Missing values: **0**
- Exact duplicate rows: **0**

### TotalCharges Validation

The `TotalCharges` column was initially stored as an object/string data type.

During numeric conversion:

- **11 values could not be converted**
- These values were blank strings
- The affected records had **tenure = 0**
- `TotalCharges` was converted to numeric form for further numerical analysis

This validation was performed before correlation and outlier analysis.

---

## Churn Distribution

The dataset contains:

| Churn Status | Customers | Percentage |
|--------------|-----------|------------|
| No | 5,174 | 73.46% |
| Yes | 1,869 | 26.54% |

The overall churn rate is therefore **26.54%**.

---

## Churn Rate by Contract Type

| Contract | No Churn | Churn |
|----------|----------|-------|
| Month-to-month | 57.29% | **42.71%** |
| One year | 88.73% | **11.27%** |
| Two year | 97.17% | **2.83%** |

Month-to-month customers show substantially higher churn than customers with longer-term contracts.

---

## Churn Rate by Internet Service

| Internet Service | No Churn | Churn |
|------------------|----------|-------|
| DSL | 81.04% | **18.96%** |
| Fiber optic | 58.11% | **41.89%** |
| No Internet | 92.60% | **7.40%** |

Fiber optic customers have the highest observed churn rate among the three Internet Service categories.

---

## Churn Rate by Payment Method

| Payment Method | No Churn | Churn |
|----------------|----------|-------|
| Bank transfer (automatic) | 83.29% | **16.71%** |
| Credit card (automatic) | 84.76% | **15.24%** |
| Electronic check | 54.71% | **45.29%** |
| Mailed check | 80.89% | **19.11%** |

Electronic check customers have the highest observed churn rate at **45.29%**.

---

## Tenure Analysis

### Mean Tenure

| Churn Status | Mean Tenure |
|--------------|-------------|
| No | 37.57 months |
| Yes | 17.98 months |

### Median Tenure

| Churn Status | Median Tenure |
|--------------|---------------|
| No | 38 months |
| Yes | 10 months |

Churned customers have substantially shorter tenure than customers who did not churn.

---

## Monthly Charges Analysis

### Mean Monthly Charges

| Churn Status | Mean Monthly Charges |
|--------------|----------------------|
| No | 61.27 |
| Yes | 74.44 |

### Median Monthly Charges

| Churn Status | Median Monthly Charges |
|--------------|------------------------|
| No | 64.43 |
| Yes | 79.65 |

Customers who churned have higher average and median monthly charges.

---

## Correlation Analysis

Correlation of numerical features with `Churn_Numeric`:

| Feature | Correlation |
|---------|-------------|
| tenure | **-0.352** |
| MonthlyCharges | **0.193** |
| TotalCharges | **-0.199** |

The strongest observed numerical relationship with Churn is tenure, with a correlation of **-0.352**.

This indicates an inverse association between tenure and churn in the dataset.

Correlation represents association and should not be interpreted as proof of causation.

---

## Outlier Analysis

The IQR method was used to identify potential statistical outliers.

| Feature | Q1 | Q3 | IQR | Lower Bound | Upper Bound | Outliers |
|---------|----|----|-----|-------------|-------------|----------|
| tenure | 9.00 | 55.00 | 46.00 | -60.00 | 124.00 | 0 |
| MonthlyCharges | 35.50 | 89.85 | 54.35 | -46.02 | 171.38 | 0 |
| TotalCharges | 401.45 | 3794.74 | 3393.29 | -4688.48 | 8884.67 | 0 |

No IQR-based outliers were detected in the three analyzed numerical features.

---

# Key EDA Findings

The major findings from Week 2 are:

- Overall customer churn rate is **26.54%**.
- Month-to-month customers have a **42.71%** churn rate.
- Two-year contract customers have only **2.83%** churn.
- Fiber optic customers have a **41.89%** churn rate.
- Electronic check customers have the highest payment-method churn rate at **45.29%**.
- Churned customers have a mean tenure of only **17.98 months**, compared with **37.57 months** for non-churned customers.
- Churned customers have higher mean monthly charges (**74.44**) compared with non-churned customers (**61.27**).
- Tenure has the strongest observed numerical correlation with Churn (**-0.352**).
- No IQR-based outliers were detected in tenure, MonthlyCharges or TotalCharges.

---

# Business Insights

The EDA identifies several customer segments that may require greater attention in a future churn-management strategy.

Customers with month-to-month contracts, fiber optic service and electronic-check payment methods show comparatively high churn rates.

The substantially lower tenure of churned customers also suggests that newer customers may represent an important group for retention analysis.

These findings are exploratory and describe associations in the dataset. They do not establish that any individual feature directly causes customer churn.

---

# Tools and Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Google Colab
- GitHub / GitHub Desktop

---

# Project Structure

```text
telco-customer-churn-preprocessing/
│
├── README.md
│
├── notebook/
│   ├── Virtual_InternWeek1.ipynb
│   └── Virtual_InterWeek2.ipynb
│
├── data/
│   └── ...
│
├── report/
│   ├── Virtual_InternWeek1.docx
│   └── Virtual_InterWeek2.docx
│
└── outputs/
    └── ...