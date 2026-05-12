# Data Preprocessing

## Purpose

- Data preprocessing converts raw data into a clean, consistent, numerical, model-ready format.
- It is required before training machine learning models because real-world datasets usually contain:
  - Missing values
  - Duplicate records
  - Outliers
  - Inconsistent formats
  - Categorical variables
  - Different feature scales
  - Data leakage risks
  - Imbalanced classes
  - Noisy values

## Preprocessing Pipeline

- Step 1: Load dataset
- Step 2: Inspect dataset structure
- Step 3: Remove duplicate records
- Step 4: Handle missing values
- Step 5: Fix inconsistent data types
- Step 6: Handle outliers
- Step 7: Encode categorical variables
- Step 8: Scale numerical features
- Step 9: Handle class imbalance
- Step 10: Split data into training, validation, and testing sets
- Step 11: Save preprocessing pipeline

## Dataset Inspection

### Required Checks

- Number of rows
- Number of columns
- Column names
- Data types
- Missing value count
- Duplicate row count
- Unique value count per column
- Basic descriptive statistics
- Class distribution for classification tasks
- Target variable distribution for regression tasks

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Dataset shape check | O(1) | O(1) |
| Missing value scan | O(n*d) | O(d) |
| Duplicate detection | O(n*d) | O(n*d) |
| Unique value count | O(n*d) | O(u) |
| Descriptive statistics | O(n*d) | O(d) |

### Symbols

- n = number of rows
- d = number of columns
- u = number of unique values

## Duplicate Handling

### Method

- Remove exact duplicate rows.
- Remove duplicate IDs if the ID column must be unique.
- Keep first occurrence or last occurrence based on business logic.

### Complexity

| Method | Time Complexity | Space Complexity |
|---|---:|---:|
| Hash-based duplicate removal | O(n*d) average | O(n*d) |
| Sort-based duplicate removal | O(n*log(n)*d) | O(n*d) |

## Missing Value Handling

## 1. Drop Missing Rows

### Use Case

- Missing value percentage is very low.
- Missingness is random.
- Dataset is large enough.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Drop rows with missing values | O(n*d) | O(n*d) |

## 2. Drop Missing Columns

### Use Case

- Column has extremely high missing percentage.
- Column is not important.
- Column cannot be reliably imputed.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Drop columns with missing values | O(n*d) | O(n*d) |

## 3. Mean Imputation

### Use Case

- Numerical feature
- Approximately symmetric distribution
- No extreme outliers

### Formula

mean = sum(x_i) / n

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Mean computation | O(n) | O(1) |
| Mean imputation | O(n) | O(1) |

## 4. Median Imputation

### Use Case

- Numerical feature
- Skewed distribution
- Outliers are present

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Median by sorting | O(n*log(n)) | O(n) |
| Median imputation | O(n) | O(1) |

## 5. Mode Imputation

### Use Case

- Categorical feature
- Discrete numerical feature
- Most frequent value is meaningful

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Frequency counting | O(n) | O(k) |
| Mode imputation | O(n) | O(1) |

### Symbols

- k = number of unique categories

## 6. Constant Value Imputation

### Use Case

- Missingness itself carries information.
- A placeholder value is needed.
- Common placeholders:
  - "Unknown"
  - "Missing"
  - -1
  - 0

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Constant imputation | O(n) | O(1) |

## 7. Forward Fill

### Use Case

- Time series data
- Previous value is a valid estimate for current missing value

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Forward fill | O(n) | O(1) |

## 8. Backward Fill

### Use Case

- Time series data
- Future observed value is acceptable for imputation
- Must not be used if it causes data leakage

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Backward fill | O(n) | O(1) |

## 9. KNN Imputation

### Method

- For each row with missing values:
  - Find k nearest complete or partially complete rows.
  - Impute using average or majority vote from neighbors.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Brute-force KNN imputation | O(n^2*d) | O(n*d) |

## 10. Iterative Imputation

### Method

- Each feature with missing values is modeled as a function of other features.
- The process repeats until convergence or maximum iteration count.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Iterative imputation | O(i*d*T_model) | O(n*d + S_model) |

### Symbols

- i = number of iterations
- T_model = training time of selected estimator
- S_model = memory used by selected estimator

## Outlier Handling

## 1. Z-Score Method

### Formula

z = (x - mean) / standard_deviation

### Rule

- A value is often treated as an outlier if:
  - z > 3
  - z < -3

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Z-score calculation | O(n) | O(n) |

## 2. IQR Method

### Formula

IQR = Q3 - Q1

lower_bound = Q1 - 1.5*IQR

upper_bound = Q3 + 1.5*IQR

### Rule

- A value is an outlier if:
  - x < lower_bound
  - x > upper_bound

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| IQR using sorting | O(n*log(n)) | O(n) |
| Outlier detection after quartiles | O(n) | O(n) |

## 3. Percentile Clipping

### Method

- Clip values below lower percentile.
- Clip values above upper percentile.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Percentile calculation by sorting | O(n*log(n)) | O(n) |
| Clipping | O(n) | O(1) |

## 4. Winsorization

### Method

- Replace extreme values with nearest accepted percentile boundary.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Winsorization | O(n*log(n)) | O(n) |

## 5. Isolation Forest

### Method

- Randomly partitions data using decision trees.
- Outliers are isolated faster than normal points.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Isolation Forest training | O(t*s*log(s)) | O(t*s) |
| Isolation Forest prediction | O(t*log(s)) per sample | O(t) |

### Symbols

- t = number of trees
- s = subsample size

## Categorical Encoding

## 1. Label Encoding

### Method

- Assign integer ID to each category.

### Example

| Category | Encoded |
|---|---:|
| red | 0 |
| blue | 1 |
| green | 2 |

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Label encoding | O(n) | O(k) |

## 2. One-Hot Encoding

### Method

- Create one binary column per category.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| One-hot encoding | O(n*k) | O(n*k) |

## 3. Ordinal Encoding

### Method

- Assign ordered integer values to ordered categories.

### Example

| Category | Encoded |
|---|---:|
| low | 0 |
| medium | 1 |
| high | 2 |

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Ordinal encoding | O(n) | O(k) |

## 4. Frequency Encoding

### Method

- Replace category with its frequency count.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Frequency encoding | O(n) | O(k) |

## 5. Target Encoding

### Method

- Replace category with mean target value for that category.
- Must be applied with cross-validation to reduce leakage.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Target encoding | O(n) | O(k) |

## Feature Scaling

## 1. Standardization

### Formula

x_scaled = (x - mean) / standard_deviation

### Use Case

- Linear regression
- Logistic regression
- Support Vector Machine
- K-Nearest Neighbors
- Principal Component Analysis
- Neural networks

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Standardization | O(n*d) | O(d) |

## 2. Min-Max Normalization

### Formula

x_scaled = (x - min) / (max - min)

### Use Case

- Neural networks
- Distance-based models
- Image pixel scaling

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Min-max normalization | O(n*d) | O(d) |

## 3. Robust Scaling

### Formula

x_scaled = (x - median) / IQR

### Use Case

- Data contains outliers.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Robust scaling | O(d*n*log(n)) | O(n*d) |

## 4. MaxAbs Scaling

### Formula

x_scaled = x / max(abs(x))

### Use Case

- Sparse data
- Data centered around zero

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| MaxAbs scaling | O(n*d) | O(d) |

## Class Imbalance Handling

## 1. Random Oversampling

### Method

- Duplicate minority class samples.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Random oversampling | O(n) | O(n_new*d) |

## 2. Random Undersampling

### Method

- Remove majority class samples.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Random undersampling | O(n) | O(n_new*d) |

## 3. SMOTE

### Method

- Synthetic Minority Oversampling Technique creates synthetic samples between minority class neighbors.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| SMOTE with brute-force neighbors | O(n_min^2*d) | O(n_new*d) |

### Symbols

- n_min = number of minority class samples
- n_new = number of samples after resampling

## Data Splitting

## 1. Train-Test Split

### Method

- Split data into:
  - Training set
  - Testing set

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Train-test split | O(n) | O(n*d) |

## 2. Train-Validation-Test Split

### Method

- Split data into:
  - Training set
  - Validation set
  - Testing set

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Train-validation-test split | O(n) | O(n*d) |

## 3. Stratified Split

### Method

- Preserves class distribution across splits.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Stratified split | O(n) | O(n*d) |

## 4. Time-Based Split

### Method

- Sort by timestamp.
- Use older records for training.
- Use newer records for validation and testing.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Time sorting | O(n*log(n)) | O(n) |
| Time-based split | O(n) | O(n*d) |

## Data Leakage Rules

- Fit preprocessing steps only on training data.
- Transform validation data using training-fitted parameters.
- Transform testing data using training-fitted parameters.
- Do not compute imputation values using validation data.
- Do not compute scaling values using validation data.
- Do not compute target encoding values using validation data.
- Do not use future timestamps in time series preprocessing.

## Recommended File Structure

- data/raw/
- data/processed/
- notebooks/
- src/preprocessing/
- src/features/
- src/models/
- src/evaluation/
- artifacts/preprocessors/
- artifacts/models/

## Summary Table

| Preprocessing Step | Main Purpose | Time Complexity | Space Complexity |
|---|---|---:|---:|
| Missing value scan | Detect null values | O(n*d) | O(d) |
| Duplicate removal | Remove repeated rows | O(n*d) average | O(n*d) |
| Mean imputation | Fill numerical missing values | O(n) | O(1) |
| Median imputation | Fill skewed numerical missing values | O(n*log(n)) | O(n) |
| One-hot encoding | Convert nominal categories | O(n*k) | O(n*k) |
| Standardization | Scale numerical features | O(n*d) | O(d) |
| IQR outlier detection | Detect extreme values | O(n*log(n)) | O(n) |
| Stratified split | Preserve class ratio | O(n) | O(n*d) |
