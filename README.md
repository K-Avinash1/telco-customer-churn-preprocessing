Telco Customer Churn - Data Preprocessing, EDA, Feature Engineering and Model Building

## Project Overview

This project demonstrates a complete data preparation, exploratory analysis, feature engineering, and machine learning workflow developed in Python using the Telco Customer Churn dataset.

The project is divided into three stages:

- **Week 1:** Data Acquisition and Preprocessing
- **Week 2:** Exploratory Data Analysis (EDA) and Visualization
- **Week 3:** Feature Engineering and Model Building

The objective is to understand, clean, validate, explore, transform, and model customer data for customer churn prediction.

---

# Week 1 - Data Acquisition and Preprocessing

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

- Original dataset: **7,043 rows x 21 columns**
- Final encoded dataset: **7,043 rows x 31 columns**
- Missing values: **0**
- Object columns: **0**
- Infinite values: **0**
- Exact duplicate rows in final validation: **22**
- Duplicate feature profiles identified: **33**
- Feature profiles with different Churn values: **18**
- IQR outliers detected in selected numerical features: **0**

## Duplicate Analysis

Duplicate records were investigated rather than removed blindly.

Repeated feature profiles were examined to determine whether they represented genuinely identical observations or valid customers with different Churn outcomes.

This analysis identified:

- **33 duplicate feature profiles**
- **18 profiles with different Churn values**

Therefore, duplicate-looking records were treated carefully rather than automatically deleted.

---

# Week 2 - Exploratory Data Analysis and Visualization

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

- Dataset size: **7,043 rows x 21 columns**
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

## Churn Distribution

The dataset contains:

| Churn Status | Customers | Percentage |
|---|---:|---:|
| No | 5,174 | 73.46% |
| Yes | 1,869 | 26.54% |

The overall churn rate is therefore **26.54%**.

## Churn Rate by Contract Type

| Contract | No Churn | Churn |
|---|---:|---:|
| Month-to-month | 57.29% | **42.71%** |
| One year | 88.73% | **11.27%** |
| Two year | 97.17% | **2.83%** |

Month-to-month customers show substantially higher churn than customers with longer-term contracts.

## Churn Rate by Internet Service

| Internet Service | No Churn | Churn |
|---|---:|---:|
| DSL | 81.04% | **18.96%** |
| Fiber optic | 58.11% | **41.89%** |
| No Internet | 92.60% | **7.40%** |

Fiber-optic customers have the highest observed churn rate among the three Internet Service categories.

## Churn Rate by Payment Method

| Payment Method | No Churn | Churn |
|---|---:|---:|
| Bank transfer (automatic) | 83.29% | **16.71%** |
| Credit card (automatic) | 84.76% | **15.24%** |
| Electronic check | 54.71% | **45.29%** |
| Mailed check | 80.89% | **19.11%** |

Electronic-check customers have the highest payment-method churn rate at **45.29%**.

## Tenure Analysis

### Mean Tenure

| Churn Status | Mean Tenure |
|---|---:|
| No | 37.57 months |
| Yes | 17.98 months |

### Median Tenure

| Churn Status | Median Tenure |
|---|---:|
| No | 38 months |
| Yes | 10 months |

Churned customers have substantially shorter tenure than customers who did not churn.

## Monthly Charges Analysis

### Mean Monthly Charges

| Churn Status | Mean Monthly Charges |
|---|---:|
| No | 61.27 |
| Yes | 74.44 |

### Median Monthly Charges

| Churn Status | Median Monthly Charges |
|---|---:|
| No | 64.43 |
| Yes | 79.65 |

Customers who churned have higher average and median monthly charges.

## Correlation Analysis

Correlation of numerical features with `Churn_Numeric`:

| Feature | Correlation |
|---|---:|
| tenure | **-0.352** |
| MonthlyCharges | **0.193** |
| TotalCharges | **-0.199** |

The strongest observed numerical relationship with Churn is tenure, with a correlation of **-0.352**. This indicates an inverse association between tenure and churn in the dataset.

Correlation represents association and should not be interpreted as proof of causation.

## Outlier Analysis

The IQR method was used to identify potential statistical outliers.

| Feature | Q1 | Q3 | IQR | Lower Bound | Upper Bound | Outliers |
|---|---:|---:|---:|---:|---:|---:|
| tenure | 9.00 | 55.00 | 46.00 | -60.00 | 124.00 | 0 |
| MonthlyCharges | 35.50 | 89.85 | 54.35 | -46.02 | 171.38 | 0 |
| TotalCharges | 401.45 | 3794.74 | 3393.29 | -4688.48 | 8884.67 | 0 |

No IQR-based outliers were detected in the three analyzed numerical features.

## Key EDA Findings

- Overall customer churn rate is **26.54%**.
- Month-to-month customers have a **42.71%** churn rate.
- Two-year contract customers have only **2.83%** churn.
- Fiber-optic customers have a **41.89%** churn rate.
- Electronic-check customers have the highest payment-method churn rate at **45.29%**.
- Churned customers have a mean tenure of **17.98 months**, compared with **37.57 months** for non-churned customers.
- Churned customers have higher mean monthly charges (**74.44**) compared with non-churned customers (**61.27**).
- Tenure has the strongest observed numerical correlation with Churn (**-0.352**).
- No IQR-based outliers were detected in tenure, MonthlyCharges, or TotalCharges.

## Business Insights

The EDA identifies several customer segments that may require greater attention in a future churn-management strategy.

Customers with month-to-month contracts, fiber-optic service, and electronic-check payment methods show comparatively high churn rates.

The substantially lower tenure of churned customers also suggests that newer customers may represent an important group for retention analysis.

These findings are exploratory and describe associations in the dataset. They do not establish that any individual feature directly causes customer churn.

---

# Week 3 - Feature Engineering and Model Building

## Objectives

The objective of Week 3 was to transform the prepared Telco Customer Churn dataset into a machine-learning-ready dataset, develop predictive classification models, and compare their performance.

The work focused on:

- Creating meaningful customer-behaviour features
- Preparing numerical and categorical variables through a reproducible pipeline
- Splitting the data into training and testing sets
- Developing a Logistic Regression baseline model
- Developing a Decision Tree Classifier
- Evaluating models with accuracy, precision, recall, F1-score, ROC-AUC, confusion matrices, and ROC curves
- Interpreting feature importance and business implications

## Feature Engineering

Seven new features were created from the existing customer data:

| Feature | Description | Purpose |
|---|---|---|
| `TotalServices` | Count of services subscribed to by the customer | Represents customer engagement with the provider |
| `AvgMonthlySpend` | `TotalCharges / tenure`, with MonthlyCharges used when tenure is zero | Represents average customer spending over time |
| `TenureGroup` | Customers grouped by tenure: 0-12, 13-36, 37-60, and 61-72 months | Represents lifecycle stage and retention period |
| `HasPartnerOrDependents` | Indicates whether the customer has a partner or dependent | Represents household/family context |
| `AutoPayment` | Indicates automatic bank transfer or credit-card payment | Represents billing convenience and payment behaviour |
| `IsMonthToMonth` | Indicates a month-to-month contract | Represents flexible-contract churn risk |
| `ChargePerService` | MonthlyCharges divided by TotalServices | Represents approximate monthly cost per subscribed service |

## Model Development Workflow

1. Reuse the cleaned Telco Customer Churn dataset.
2. Remove `customerID`, because it is an identifier rather than a predictive feature.
3. Convert `TotalCharges` to numeric form and handle blank values.
4. Encode `Churn` as 1 for Yes and 0 for No.
5. Create the seven engineered features.
6. Split the data into 80% training data and 20% testing data using stratified sampling.
7. Apply median imputation and Min-Max scaling to numerical features.
8. Apply one-hot encoding to categorical features.
9. Train Logistic Regression and Decision Tree models.
10. Evaluate and compare both models.
11. Analyze Decision Tree feature importance.

## Train-Test Split

The data was split using an 80:20 train-test ratio with `random_state=42` and stratification on the Churn target.

| Set | Records |
|---|---:|
| Training set | 5,634 |
| Testing set | 1,409 |

The testing set contained **1,035 non-churn customers** and **374 churn customers**.

## Model Performance

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | **0.7991** | **0.6502** | 0.5267 | 0.5820 | **0.8412** |
| Decision Tree | 0.7516 | 0.5220 | **0.7620** | **0.6196** | 0.8353 |

### Logistic Regression

Logistic Regression achieved the strongest overall accuracy (**79.91%**), precision (**65.02%**), and ROC-AUC (**0.8412**). It was effective at distinguishing between churned and non-churned customers overall.

However, its churn recall was **52.67%**, meaning that it identified only around half of the customers who actually churned. This is a limitation when the goal is to find at-risk customers before they leave.

### Decision Tree Classifier

The Decision Tree achieved lower overall accuracy (**75.16%**) and precision (**52.20%**), but it achieved substantially higher churn recall (**76.20%**) and a higher F1-score (**61.96%**).

The Decision Tree identified approximately **285 of 374** actual churn customers in the test set, compared with approximately **197** identified by Logistic Regression. It is therefore more useful when the business prioritizes identifying churn-risk customers, even if this creates more false-positive alerts.

## Model Selection

Logistic Regression is preferable when the priority is overall accuracy, higher precision, and fewer unnecessary retention actions.

The Decision Tree is selected as the recommended model for this churn-retention project because it has much higher recall and F1-score for the churn class. In practice, it identifies more customers who may leave, allowing the company to target them with retention campaigns, service support, or contract incentives.

The preferred model can change depending on the business cost of false positives and false negatives.

## Decision Tree Feature Importance

The Decision Tree feature-importance analysis identified the following most useful predictors:

| Rank | Feature | Importance |
|---:|---|---:|
| 1 | `IsMonthToMonth` | **0.6049** |
| 2 | `tenure` | **0.1167** |
| 3 | `InternetService_Fiber optic` | **0.1074** |
| 4 | `MonthlyCharges` | 0.0365 |
| 5 | `TotalCharges` | 0.0210 |
| 6 | `TechSupport_No` | 0.0193 |
| 7 | `AvgMonthlySpend` | 0.0189 |
| 8 | `Contract_Two year` | 0.0170 |
| 9 | `OnlineSecurity_No` | 0.0126 |
| 10 | `PhoneService_Yes` | 0.0116 |
| 11 | `PaymentMethod_Electronic check` | 0.0108 |

`IsMonthToMonth` was the strongest feature by a substantial margin. This supports the Week 2 finding that month-to-month customers have a comparatively high observed churn rate.

Tenure and fiber-optic service were the next most useful predictors. The result is consistent with the EDA finding that churned customers tend to have shorter tenure and that fiber-optic customers show a higher observed churn rate.

Feature importance shows how useful a variable was to this Decision Tree. It does not prove that the feature causes churn. Also, `IsMonthToMonth` was derived from the existing Contract column, so it should be interpreted as a direct contract-flexibility indicator rather than as a completely independent variable.

## Week 3 Key Findings

- Logistic Regression achieved the best overall accuracy (**79.91%**) and ROC-AUC (**0.8412**).
- Decision Tree achieved the best churn recall (**76.20%**) and churn F1-score (**61.96%**).
- The Decision Tree is recommended for early churn-risk identification because it identifies more actual churners.
- Month-to-month contract status was the most important Decision Tree feature (**0.6049**).
- Tenure (**0.1167**) and fibre-optic internet service (**0.1074**) were the next most informative features.
- The Week 3 model findings are consistent with the Week 2 EDA patterns for contract type, tenure, service type, monthly charges, and payment method.

## Potential Improvements

- Tune model hyperparameters using `GridSearchCV` or `RandomizedSearchCV`.
- Evaluate models using cross-validation.
- Tune the classification threshold for Logistic Regression to improve churn recall.
- Compare ensemble models such as Random Forest, Gradient Boosting, or XGBoost if permitted.
- Experiment with class-imbalance techniques only on training data.
- Add satisfaction, support-ticket, complaint, and service-outage data if available.
- Assess fairness and business costs before using predictions in real customer-retention decisions.

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
|
|-- README.md
|
|-- notebook/
|   |-- Virtual_InternWeek1.ipynb
|   |-- Virtual_InternWeek2.ipynb
|   `-- Virtual_InternWeek3.ipynb
|
|-- data/
|   `-- WA_Fn-UseC_-Telco-Customer-Churn.csv
|
|-- report/
|   |-- Virtual_InternWeek1.docx
|   |-- Virtual_InternWeek2.docx
|   `-- Virtual_InternWeek3.docx
|
`-- outputs/
    `-- week3_graphs/