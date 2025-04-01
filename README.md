# Data Analysis and Preprocessing

## Overview
This notebook performs exploratory data analysis (EDA) and preprocessing on the Telco Customer Churn dataset (`WA_Fn-UseC_-Telco-Customer-Churn.csv`). It cleans the data, visualizes churn patterns, applies feature engineering, scales numerical features, and handles class imbalance using SMOTEENN. The preprocessed dataset is saved as `X_preprocessed.csv` (features) and `y_preprocessed.csv` (target) for use in subsequent model notebooks.

## Objectives
- Load and explore the raw dataset.
- Clean and preprocess the data (e.g., handle missing values, encode categorical variables, scale numerical features).
- Conduct EDA to identify churn patterns across key features.
- Balance the dataset using SMOTEENN.
- Save preprocessed data for model training.

## Dataset
- **Source**: [Telco Customer Churn on Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- **File**: `WA_Fn-UseC_-Telco-Customer-Churn.csv`
- **Features**: 20 (after dropping `customerID`), including `tenure`, `MonthlyCharges`, `TotalCharges`, `Contract`, etc.
- **Target**: `Churn` (binary: 0 = No, 1 = Yes)

## Steps
1. **Data Loading**: Load the CSV file into a Pandas DataFrame.
2. **Preprocessing**:
   - Drop `customerID`.
   - Convert `TotalCharges` to numeric, drop rows with NaN.
   - Clean `PaymentMethod` by removing "(automatic)".
   - Remove duplicates.
   - Encode binary categorical variables (e.g., `Churn`, `PaperlessBilling`) to 0/1.
   - One-hot encode nominal categorical variables with ≤10 unique values.
   - Scale numerical features (`tenure`, `MonthlyCharges`, `TotalCharges`) using `StandardScaler`.
3. **EDA**:
   - Visualize outliers with boxplots.
   - Plot churn distribution and feature-specific churn rates (e.g., `Contract`, `InternetService`).
   - Analyze tenure patterns and relationships with `MonthlyCharges` and `TotalCharges`.
4. **Resampling**: Apply `SMOTEENN` to balance the imbalanced dataset.
5. **Output**: Save preprocessed features (`X_preprocessed.csv`) and target (`y_preprocessed.csv`).

## Requirements
- Python 3.11
- Libraries:
  - `numpy`
  - `pandas`
  - `matplotlib`
  - `seaborn`
  - `sklearn` (for `StandardScaler`)
  - `imblearn` (for `SMOTEENN`)

Install dependencies:
```bash
pip install numpy pandas matplotlib seaborn scikit-learn imbalanced-learn
```

## Usage
1. Upload WA_Fn-UseC_-Telco-Customer-Churn.csv to your Google Colab environment.
2. Run the notebook to generate X_preprocessed.csv and y_preprocessed.csv.
3. Download these files for use in model notebooks or store them in the repository.

## Outputs
- Files: X_preprocessed.csv (resampled features), y_preprocessed.csv (resampled target).
- Visualizations: Multiple plots showing churn patterns and data distributions.

## Notes
- This notebook must be run first to generate the preprocessed data the model notebooks require.
- The EDA provides insights into churn drivers (e.g., month-to-month contracts, and high monthly charges).
