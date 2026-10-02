# Task 1 --- E-Commerce Dataset Cleaning

## Data Science Internship --- Week 1

**Organization:** WeIntern Pvt Ltd\
**Task:** Task 1 --- E-Commerce Dataset Cleaning\
**Objective:** Clean and validate an e-commerce customer shopping
behavior dataset systematically and document the major cleaning
decisions.

## Project Overview

This project prepares a customer shopping behavior dataset for reliable
downstream analysis. The workflow focuses on raw-data inspection,
missing-value treatment, duplicate investigation, column
standardization, logical validation, redundant-feature handling, feature
engineering, and final quality checks.

The raw dataset is preserved unchanged and the cleaned dataset is saved
separately.

## Dataset Description

The raw Customer Shopping Behavior dataset contains:

-   **3,900 rows**
-   **18 columns**
-   Customer demographic information
-   Product and category information
-   Purchase amount and review rating
-   Subscription and shipping information
-   Discount and promotional information
-   Previous-purchase and payment information
-   Purchase-frequency information

After cleaning and feature preparation, the final dataset contains:

-   **3,900 rows**
-   **19 columns**
-   **0 missing values**
-   **0 fully duplicated rows**

## Tools and Libraries

-   Python
-   Pandas
-   Jupyter Notebook

## Cleaning Workflow

### 1. Raw Data Inspection

The dataset was inspected using standard Pandas methods to review:

-   Dataset dimensions
-   Column names
-   Data types
-   Sample records
-   Numerical summaries
-   Categorical distributions

### 2. Missing Value Analysis

`Review Rating` was the only field containing missing values:

-   Missing values: **37**
-   Missing proportion: **0.95%**

The affected records were retained because their remaining customer and
purchase information was still useful.

### 3. Missing Value Treatment

Missing `review_rating` values were filled using the **median review
rating within the corresponding product category**.

This approach uses a category-specific typical rating rather than a
single dataset-wide value.

After imputation:

-   **Remaining missing values: 0**

### 4. Column Standardization

Column names were standardized to lowercase `snake_case` for consistent
programmatic use.

Examples:

-   `Customer ID` → `customer_id`
-   `Item Purchased` → `item_purchased`
-   `Review Rating` → `review_rating`
-   `Purchase Amount (USD)` → `purchase_amount`

### 5. Feature Engineering

Two derived fields were created:

-   `age_group`
-   `purchase_frequency_days`

`age_group` provides broader demographic groupings while retaining the
original numerical age.

`purchase_frequency_days` converts the categorical purchase-frequency
labels into an approximate numerical representation for later analysis.
The original categorical field is retained.

### 6. Data Validation

The following logical checks were performed:

  Validation Rule                                       Invalid Records
  --------------------------------------------------- -----------------
  `age > 0`                                                           0
  `purchase_amount > 0`                                               0
  `previous_purchases >= 0`                                           0
  Leading/trailing whitespace in categorical fields          0 detected

No records required removal under these validation rules.

### 7. Redundant Feature Check

`discount_applied` and `promo_code_used` were compared row by row and
contained identical information.

`promo_code_used` was therefore removed while `discount_applied` was
retained.

### 8. Duplicate Analysis

Duplicate checks produced the following results:

-   Fully duplicated rows: **0**
-   Unique customer IDs: **3,900**
-   Repeated customer IDs: **0**

No records were removed as duplicates because no confirmed duplicate
observations were found.

## Final Cleaning Summary

The completed workflow:

-   Preserved all 3,900 source records
-   Handled 37 missing Review Rating values
-   Reduced missing values to 0
-   Standardized column names
-   Created two useful derived features
-   Performed numerical validation checks
-   Checked categorical whitespace consistency
-   Removed one confirmed redundant feature
-   Confirmed 0 fully duplicated rows
-   Produced a final cleaned dataset of **3,900 rows × 19 columns**

## Repository Structure

``` text
Data_Science_Week1_Task1_Data_Cleaning/
├── data/
│   ├── raw/
│   │   └── customer_shopping_behavior.csv
│   └── cleaned/
│       └── customer_shopping_behavior_cleaned.csv
├── notebooks/
│   └── Task1.ipynb
├── reports/
│   └── Task1_Data_Cleaning_Report.pdf
├── screenshots/
│   ├── dataset-overview.png
│   ├── missing-values-report.png
│   ├── duplicate-analysis.png
│   └── validation-checks.png
├── README.md
└── requirements.txt
```

## How to Run the Project

1.  Clone or download this repository.
2.  Make sure Python is installed.
3.  Install the required dependency:

``` bash
pip install -r requirements.txt
```

4.  Open `notebooks/Task1.ipynb` in Jupyter Notebook, JupyterLab, or VS
    Code.
5.  Run the notebook cells from top to bottom.
6.  The notebook reads the raw dataset from `data/raw/` and produces the
    cleaned dataset in `data/cleaned/`.

## Output Files

The main project outputs are:

-   `customer_shopping_behavior_cleaned.csv` --- cleaned dataset
-   `Task1.ipynb` --- complete cleaning and validation workflow
-   `Task1_Data_Cleaning_Report.pdf` --- written Task 1 report
-   Task-specific screenshots documenting key cleaning results

## Cleaning Decisions and Assumptions

-   The raw dataset is preserved unchanged.
-   Category-level median imputation is used only for missing Review
    Rating values.
-   No rows are removed because no confirmed full duplicates or
    documented invalid numerical records were found.
-   `purchase_frequency_days` is an approximate analytical
    representation of categorical purchase frequency rather than an
    observed transaction interval.
-   The original numerical age and categorical purchase-frequency fields
    are retained alongside the derived features.

## Major Result

The final cleaned dataset contains **3,900 rows and 19 columns with 0
missing values and 0 fully duplicated rows**, providing a validated
dataset ready for downstream analysis.

## Author

**Suman Paliwar**\
Data Science Internship --- Week 1
