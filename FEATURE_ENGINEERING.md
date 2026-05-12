# Feature Engineering

## Purpose

- Feature engineering creates, transforms, selects, and organizes input variables to improve machine learning model performance.
- A feature is a measurable input used by a model.
- Strong features improve:
  - Predictive accuracy
  - Model stability
  - Interpretability
  - Training efficiency
  - Generalization

## Feature Engineering Pipeline

- Step 1: Identify feature types
- Step 2: Clean invalid feature values
- Step 3: Transform numerical features
- Step 4: Encode categorical features
- Step 5: Extract date-time features
- Step 6: Extract text features
- Step 7: Create interaction features
- Step 8: Select important features
- Step 9: Remove redundant features
- Step 10: Validate features against data leakage

## Feature Types

| Feature Type | Examples | Common Methods |
|---|---|---|
| Numerical continuous | age, salary, temperature | scaling, binning, log transform |
| Numerical discrete | count, rating, number_of_items | scaling, clipping, count features |
| Categorical nominal | city, color, product_type | one-hot encoding, target encoding |
| Categorical ordinal | low, medium, high | ordinal encoding |
| Date-time | timestamp, date, time | extraction, lag features, rolling features |
| Text | review, title, document | bag of words, TF-IDF, embeddings |
| Boolean | is_active, has_discount | binary encoding |
| Geospatial | latitude, longitude | distance features, region encoding |

## Numerical Feature Engineering

## 1. Polynomial Features

### Method

- Create powers of original features.
- Example:
  - x
  - x^2
  - x^3

### Use Case

- Linear models need nonlinear decision boundaries.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Polynomial features degree p | O(n*d^p) | O(n*d^p) |

### Symbols

- n = number of samples
- d = number of original features
- p = polynomial degree

## 2. Interaction Features

### Method

- Combine two or more features using multiplication, division, addition, or subtraction.

### Examples

- price_per_unit = total_price / quantity
- income_per_member = household_income / family_size
- area = length * width

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Pairwise interaction features | O(n*d^2) | O(n*d^2) |

## 3. Ratio Features

### Method

- Divide one feature by another feature.

### Examples

- debt_to_income = debt / income
- clicks_per_impression = clicks / impressions
- revenue_per_user = revenue / users

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Ratio feature creation | O(n*r) | O(n*r) |

### Symbols

- r = number of ratio features

## 4. Difference Features

### Method

- Subtract one feature from another feature.

### Examples

- profit = revenue - cost
- age_gap = age_1 - age_2
- delivery_delay = actual_delivery_days - expected_delivery_days

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Difference feature creation | O(n*r) | O(n*r) |

## 5. Binning

### Method

- Convert continuous values into intervals.

### Types

- Equal-width binning
- Equal-frequency binning
- Custom domain-based binning

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Equal-width binning | O(n) | O(n) |
| Equal-frequency binning | O(n*log(n)) | O(n) |

## 6. Log Transformation

### Formula

x_transformed = log(1 + x)

### Use Case

- Highly skewed positive numerical features.
- Reduces impact of large values.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Log transformation | O(n) | O(n) |

## 7. Power Transformation

### Methods

- Box-Cox transformation
- Yeo-Johnson transformation

### Use Case

- Make feature distribution more Gaussian-like.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Power transformation | O(n) | O(n) |

## Categorical Feature Engineering

## 1. One-Hot Encoding

### Method

- Create one binary column per category.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| One-hot encoding | O(n*k) | O(n*k) |

### Symbols

- k = number of unique categories

## 2. Count Encoding

### Method

- Replace category with count of that category.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Count encoding | O(n) | O(k) |

## 3. Frequency Encoding

### Method

- Replace category with frequency percentage of that category.

### Formula

frequency(category) = count(category) / n

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Frequency encoding | O(n) | O(k) |

## 4. Target Encoding

### Method

- Replace category with average target value for that category.

### Formula

encoded_value(category) = mean(target for rows where feature = category)

### Leakage Control

- Use K-fold target encoding.
- Compute category means only from training folds.
- Apply smoothing for rare categories.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Target encoding | O(n) | O(k) |
| K-fold target encoding | O(k_folds*n) | O(k) |

## 5. Rare Category Grouping

### Method

- Replace low-frequency categories with "Other".

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Rare category grouping | O(n) | O(k) |

## 6. Binary Encoding

### Method

- Assign category integer IDs.
- Convert IDs to binary representation.
- Split binary digits into columns.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Binary encoding | O(n*log(k)) | O(n*log(k)) |

## Date-Time Feature Engineering

## 1. Basic Date Features

### Extracted Features

- year
- month
- day
- day_of_week
- day_of_year
- quarter
- week_of_year
- is_weekend
- is_month_start
- is_month_end
- is_quarter_start
- is_quarter_end
- is_year_start
- is_year_end

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Date feature extraction | O(n*f) | O(n*f) |

### Symbols

- f = number of extracted date features

## 2. Time Features

### Extracted Features

- hour
- minute
- second
- is_morning
- is_afternoon
- is_evening
- is_night
- business_hour_flag

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Time feature extraction | O(n*f) | O(n*f) |

## 3. Cyclical Encoding

### Problem

- Month, day, and hour are cyclic.
- December and January are close, but ordinal encoding makes them far.

### Formula

sin_value = sin(2*pi*x/period)

cos_value = cos(2*pi*x/period)

### Examples

- hour period = 24
- month period = 12
- day_of_week period = 7

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Cyclical encoding | O(n) | O(n) |

## 4. Lag Features

### Method

- Use previous values as features.

### Examples

- sales_lag_1
- sales_lag_7
- sales_lag_30

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Lag feature creation | O(n*l) | O(n*l) |

### Symbols

- l = number of lag features

## 5. Rolling Window Features

### Methods

- Rolling mean
- Rolling median
- Rolling standard deviation
- Rolling minimum
- Rolling maximum
- Rolling sum

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Rolling mean with optimized window | O(n) | O(n) |
| Rolling median with naive sorting | O(n*w*log(w)) | O(n) |

### Symbols

- w = window size

## Text Feature Engineering

## 1. Bag of Words

### Method

- Represent text by word counts.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Bag of Words vectorization | O(T) | O(n*v) |

### Symbols

- T = total number of tokens
- v = vocabulary size

## 2. TF-IDF

### Formula

tfidf(term, document) = tf(term, document) * idf(term)

idf(term) = log(N / df(term))

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| TF-IDF vectorization | O(T) | O(n*v) |

### Symbols

- N = number of documents
- df = document frequency

## 3. N-Grams

### Method

- Create token sequences of length n.

### Examples

- unigram: one word
- bigram: two words
- trigram: three words

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| N-gram extraction | O(T*g) | O(n*v_g) |

### Symbols

- g = maximum n-gram size
- v_g = n-gram vocabulary size

## 4. Word Embeddings

### Method

- Convert words to dense vectors.

### Examples

- Word2Vec
- GloVe
- FastText

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Average word embedding per document | O(T*e) | O(n*e) |

### Symbols

- e = embedding dimension

## 5. Sentence Embeddings

### Method

- Convert full sentence or document into dense vector.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Transformer sentence embedding | O(L^2*h) per document | O(L^2 + L*h) |

### Symbols

- L = sequence length
- h = hidden dimension

## Feature Selection

## 1. Variance Threshold

### Method

- Remove features with variance below a selected threshold.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Variance threshold | O(n*d) | O(d) |

## 2. Correlation Filtering

### Method

- Remove one feature from highly correlated feature pairs.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Correlation matrix calculation | O(n*d^2) | O(d^2) |

## 3. Mutual Information

### Method

- Measures dependency between feature and target.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Mutual information feature selection | O(n*d*log(n)) approximate | O(n+d) |

## 4. Chi-Square Test

### Use Case

- Non-negative categorical or count features.
- Classification tasks.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Chi-square feature selection | O(n*d) | O(d) |

## 5. Recursive Feature Elimination

### Method

- Train model.
- Rank features.
- Remove weakest features.
- Repeat until target number of features remains.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Recursive Feature Elimination | O(r*T_model) | O(S_model+d) |

### Symbols

- r = number of elimination rounds
- T_model = model training time
- S_model = model memory usage

## 6. L1 Regularization-Based Selection

### Method

- Train model with L1 penalty.
- Remove features with zero or near-zero coefficients.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| L1 feature selection | O(i*n*d) | O(d) |

### Symbols

- i = number of optimization iterations

## 7. Tree-Based Feature Importance

### Method

- Train tree-based model.
- Rank features by impurity reduction or permutation importance.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Decision tree feature importance | O(n*d*log(n)) average | O(nodes) |
| Random forest feature importance | O(t*n*d*log(n)) average | O(t*nodes) |
| Permutation importance | O(d*T_predict) | O(n*d) |

### Symbols

- t = number of trees
- nodes = number of tree nodes
- T_predict = prediction time for full dataset

## Data Leakage Checks

- Do not use target-derived features unless they are generated only from training data.
- Do not use future information in time series features.
- Do not fit scalers on validation or testing data.
- Do not compute target encodings using validation or testing data.
- Do not create rolling features using future values.
- Do not include identifiers that directly encode the target.

## Summary Table

| Method | Main Use | Time Complexity | Space Complexity |
|---|---|---:|---:|
| Polynomial features | Nonlinear effects | O(n*d^p) | O(n*d^p) |
| Interaction features | Combined effects | O(n*d^2) | O(n*d^2) |
| One-hot encoding | Nominal categories | O(n*k) | O(n*k) |
| Target encoding | High-cardinality categories | O(n) | O(k) |
| Cyclical encoding | Periodic variables | O(n) | O(n) |
| Lag features | Time series memory | O(n*l) | O(n*l) |
| TF-IDF | Text representation | O(T) | O(n*v) |
| Variance threshold | Remove weak features | O(n*d) | O(d) |
| Correlation filtering | Remove redundancy | O(n*d^2) | O(d^2) |
| Recursive Feature Elimination | Model-based selection | O(r*T_model) | O(S_model+d) |
