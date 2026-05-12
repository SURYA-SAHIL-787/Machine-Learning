# Model Evaluation Metrics

## Purpose

- Model evaluation measures how well a trained machine learning model performs.
- The correct metric depends on:
  - Task type
  - Target distribution
  - Cost of false positives
  - Cost of false negatives
  - Class imbalance
  - Business objective
  - Interpretability needs

## Evaluation Pipeline

- Step 1: Identify problem type
- Step 2: Select primary metric
- Step 3: Select secondary metrics
- Step 4: Evaluate on validation set
- Step 5: Tune model using validation metric
- Step 6: Evaluate once on test set
- Step 7: Report final metrics
- Step 8: Analyze errors
- Step 9: Check overfitting and underfitting

## Problem Types

| Problem Type | Target Type | Example Metrics |
|---|---|---|
| Binary classification | 0 or 1 | accuracy, precision, recall, F1-score, AUC-ROC |
| Multiclass classification | one class from many classes | accuracy, macro F1, weighted F1 |
| Multilabel classification | multiple labels per sample | Hamming loss, micro F1, macro F1 |
| Regression | continuous value | MAE, MSE, RMSE, R^2 |
| Clustering | unlabeled groups | silhouette score, Davies-Bouldin index |
| Ranking | ordered results | MAP, MRR, NDCG |

## Classification Metrics

## 1. Confusion Matrix

### Terms

- True Positive: model predicts positive and actual class is positive
- True Negative: model predicts negative and actual class is negative
- False Positive: model predicts positive and actual class is negative
- False Negative: model predicts negative and actual class is positive

### Matrix

| Actual / Predicted | Predicted Positive | Predicted Negative |
|---|---:|---:|
| Actual Positive | TP | FN |
| Actual Negative | FP | TN |

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Binary confusion matrix | O(n) | O(1) |
| Multiclass confusion matrix | O(n) | O(c^2) |

### Symbols

- n = number of samples
- c = number of classes

## 2. Accuracy

### Formula

accuracy = (TP + TN) / (TP + TN + FP + FN)

### Use Case

- Balanced classification datasets.
- Equal cost for all error types.

### Weakness

- Misleading for imbalanced datasets.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Accuracy | O(n) | O(1) |

## 3. Precision

### Formula

precision = TP / (TP + FP)

### Use Case

- False positives are expensive.
- Example: spam detection where marking valid email as spam is costly.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Precision | O(n) | O(1) |

## 4. Recall

### Formula

recall = TP / (TP + FN)

### Use Case

- False negatives are expensive.
- Example: disease detection where missing a real case is costly.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Recall | O(n) | O(1) |

## 5. F1-Score

### Formula

F1 = 2 * precision * recall / (precision + recall)

### Use Case

- Need balance between precision and recall.
- Useful for imbalanced classification.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| F1-score | O(n) | O(1) |

## 6. F-Beta Score

### Formula

F_beta = (1 + beta^2) * precision * recall / ((beta^2 * precision) + recall)

### Interpretation

- beta > 1 gives more weight to recall.
- beta < 1 gives more weight to precision.
- beta = 1 gives F1-score.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| F-beta score | O(n) | O(1) |

## 7. Specificity

### Formula

specificity = TN / (TN + FP)

### Use Case

- Measures ability to correctly identify negatives.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Specificity | O(n) | O(1) |

## 8. Balanced Accuracy

### Formula

balanced_accuracy = (recall + specificity) / 2

### Use Case

- Imbalanced binary classification.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Balanced accuracy | O(n) | O(1) |

## 9. Matthews Correlation Coefficient

### Formula

MCC = (TP*TN - FP*FN) / sqrt((TP+FP)*(TP+FN)*(TN+FP)*(TN+FN))

### Use Case

- Balanced single-number classification metric.
- Useful for imbalanced datasets.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Matthews correlation coefficient | O(n) | O(1) |

## 10. Cohen's Kappa

### Formula

kappa = (observed_accuracy - expected_accuracy) / (1 - expected_accuracy)

### Use Case

- Measures agreement beyond random chance.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Cohen's kappa | O(n+c^2) | O(c^2) |

## 11. Log Loss

### Formula

log_loss = -(1/n) * sum(y_i*log(p_i) + (1-y_i)*log(1-p_i))

### Use Case

- Probabilistic binary classification.
- Penalizes confident wrong predictions.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Binary log loss | O(n) | O(1) |
| Multiclass log loss | O(n*c) | O(1) |

## 12. ROC Curve

### Terms

- True Positive Rate = TP / (TP + FN)
- False Positive Rate = FP / (FP + TN)

### Use Case

- Threshold analysis for binary classifiers.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| ROC curve by sorting scores | O(n*log(n)) | O(n) |

## 13. AUC-ROC

### Meaning

- Area under ROC curve.
- Measures ranking quality across thresholds.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| AUC-ROC | O(n*log(n)) | O(n) |

## 14. Precision-Recall Curve

### Terms

- Precision = TP / (TP + FP)
- Recall = TP / (TP + FN)

### Use Case

- Imbalanced datasets where positive class is rare.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Precision-recall curve | O(n*log(n)) | O(n) |

## 15. Average Precision

### Meaning

- Weighted mean of precision values at different recall thresholds.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Average precision | O(n*log(n)) | O(n) |

## Multiclass Classification Metrics

## 1. Macro Average

### Method

- Compute metric independently for each class.
- Take unweighted average across classes.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Macro average metric | O(n+c) | O(c) |

## 2. Micro Average

### Method

- Aggregate TP, FP, and FN across all classes.
- Compute metric globally.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Micro average metric | O(n+c) | O(c) |

## 3. Weighted Average

### Method

- Compute metric per class.
- Average using class support as weight.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Weighted average metric | O(n+c) | O(c) |

## Regression Metrics

## 1. Mean Absolute Error

### Formula

MAE = (1/n) * sum(abs(y_i - y_pred_i))

### Use Case

- Robust compared to MSE.
- Error is measured in original target units.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| MAE | O(n) | O(1) |

## 2. Mean Squared Error

### Formula

MSE = (1/n) * sum((y_i - y_pred_i)^2)

### Use Case

- Penalizes large errors strongly.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| MSE | O(n) | O(1) |

## 3. Root Mean Squared Error

### Formula

RMSE = sqrt(MSE)

### Use Case

- Same target unit as original data.
- Sensitive to large errors.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| RMSE | O(n) | O(1) |

## 4. Root Mean Squared Logarithmic Error

### Formula

RMSLE = sqrt((1/n) * sum((log(1+y_pred_i) - log(1+y_i))^2))

### Use Case

- Targets with exponential growth.
- Penalizes relative error.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| RMSLE | O(n) | O(1) |

## 5. Mean Absolute Percentage Error

### Formula

MAPE = (100/n) * sum(abs((y_i - y_pred_i) / y_i))

### Use Case

- Percentage-based error interpretation.

### Weakness

- Undefined when actual value is zero.
- Explodes when actual value is near zero.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| MAPE | O(n) | O(1) |

## 6. R-Squared

### Formula

R^2 = 1 - (SS_res / SS_tot)

SS_res = sum((y_i - y_pred_i)^2)

SS_tot = sum((y_i - mean_y)^2)

### Use Case

- Measures explained variance.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| R^2 | O(n) | O(1) |

## 7. Adjusted R-Squared

### Formula

adjusted_R^2 = 1 - ((1 - R^2)*(n - 1) / (n - d - 1))

### Use Case

- Penalizes unnecessary features.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Adjusted R^2 | O(n) | O(1) |

## 8. Huber Loss

### Formula

if abs(error) <= delta:
    loss = 0.5 * error^2

if abs(error) > delta:
    loss = delta * (abs(error) - 0.5 * delta)

### Use Case

- Combines MSE behavior for small errors and MAE behavior for large errors.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Huber loss | O(n) | O(1) |

## Clustering Metrics

## 1. Silhouette Score

### Formula

silhouette = (b - a) / max(a, b)

### Terms

- a = mean distance to points in same cluster
- b = mean distance to points in nearest other cluster

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Silhouette score exact | O(n^2*d) | O(n^2) |

## 2. Davies-Bouldin Index

### Meaning

- Lower score indicates better clustering.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Davies-Bouldin index | O(n*d + k^2*d) | O(k*d) |

### Symbols

- k = number of clusters

## 3. Calinski-Harabasz Index

### Meaning

- Higher score indicates better clustering.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Calinski-Harabasz index | O(n*d + k*d) | O(k*d) |

## 4. Adjusted Rand Index

### Use Case

- Requires true labels.
- Compares predicted clusters with true classes.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Adjusted Rand Index | O(n + c*k) | O(c*k) |

## 5. Normalized Mutual Information

### Use Case

- Requires true labels.
- Measures mutual dependence between true labels and predicted clusters.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Normalized Mutual Information | O(n + c*k) | O(c*k) |

## Ranking Metrics

## 1. Mean Reciprocal Rank

### Formula

MRR = (1/Q) * sum(1/rank_i)

### Use Case

- Evaluates position of first relevant result.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Mean Reciprocal Rank | O(Q*m) | O(1) |

### Symbols

- Q = number of queries
- m = number of ranked items per query

## 2. Mean Average Precision

### Use Case

- Evaluates ranked retrieval quality.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Mean Average Precision | O(Q*m) | O(1) |

## 3. Normalized Discounted Cumulative Gain

### Formula

DCG = sum(relevance_i / log2(i+1))

NDCG = DCG / IDCG

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| NDCG | O(Q*m*log(m)) | O(m) |

## Validation Techniques

## 1. Holdout Validation

### Method

- Split data once into training and validation sets.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Holdout validation | O(T_model + P_model) | O(S_model+n*d) |

## 2. K-Fold Cross-Validation

### Method

- Split dataset into k folds.
- Train on k-1 folds.
- Validate on the remaining fold.
- Repeat k times.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| K-fold cross-validation | O(k*T_model) | O(S_model+n*d) |

## 3. Stratified K-Fold Cross-Validation

### Method

- Preserves class distribution in each fold.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Stratified K-fold cross-validation | O(k*T_model+n) | O(S_model+n*d) |

## 4. Leave-One-Out Cross-Validation

### Method

- Each sample becomes validation set once.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Leave-one-out cross-validation | O(n*T_model) | O(S_model+n*d) |

## 5. Time Series Split

### Method

- Training data always comes before validation data.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Time series split | O(k*T_model) | O(S_model+n*d) |

## Overfitting And Underfitting Diagnosis

| Training Error | Validation Error | Diagnosis |
|---:|---:|---|
| High | High | Underfitting |
| Low | High | Overfitting |
| Low | Low | Good fit |
| High | Low | Data issue or leakage issue |

## Metric Selection Rules

| Task | Dataset Condition | Primary Metric |
|---|---|---|
| Binary classification | Balanced classes | Accuracy |
| Binary classification | Imbalanced classes | F1-score |
| Binary classification | False positives costly | Precision |
| Binary classification | False negatives costly | Recall |
| Binary classification | Probability quality important | Log loss |
| Binary classification | Threshold-independent ranking | AUC-ROC |
| Regression | Outliers not dominant | RMSE |
| Regression | Outliers present | MAE |
| Regression | Relative error matters | MAPE or RMSLE |
| Clustering | No labels available | Silhouette score |
| Clustering | Labels available | Adjusted Rand Index |
| Ranking | First relevant result matters | Mean Reciprocal Rank |
| Ranking | Full ranking quality matters | NDCG |

## Summary Table

| Metric | Task | Time Complexity | Space Complexity |
|---|---|---:|---:|
| Accuracy | Classification | O(n) | O(1) |
| Precision | Classification | O(n) | O(1) |
| Recall | Classification | O(n) | O(1) |
| F1-score | Classification | O(n) | O(1) |
| MCC | Classification | O(n) | O(1) |
| Log loss | Classification | O(n*c) | O(1) |
| AUC-ROC | Classification | O(n*log(n)) | O(n) |
| MAE | Regression | O(n) | O(1) |
| MSE | Regression | O(n) | O(1) |
| RMSE | Regression | O(n) | O(1) |
| R^2 | Regression | O(n) | O(1) |
| Silhouette score | Clustering | O(n^2*d) | O(n^2) |
| Davies-Bouldin index | Clustering | O(n*d+k^2*d) | O(k*d) |
| MRR | Ranking | O(Q*m) | O(1) |
| NDCG | Ranking | O(Q*m*log(m)) | O(m) |
