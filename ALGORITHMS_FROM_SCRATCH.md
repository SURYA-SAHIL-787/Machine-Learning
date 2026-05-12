# Algorithms From Scratch

## Purpose

- This file documents core machine learning algorithms with:
  - Problem type
  - Mathematical objective
  - Training logic
  - Prediction logic
  - Time complexity
  - Space complexity

## Symbols

- n = number of samples
- d = number of features
- c = number of classes
- k = number of clusters or neighbors
- i = number of iterations
- t = number of trees
- depth = tree depth
- nodes = number of tree nodes
- s = number of support vectors
- r = reduced dimensions
- b = batch size

## Supervised Learning Algorithms

## 1. Linear Regression

### Problem Type

- Supervised learning
- Regression

### Objective

- Predict continuous target value.

### Hypothesis

y_pred = X*theta

### Loss Function

MSE = (1/n) * sum((y_i - y_pred_i)^2)

### Training Methods

- Normal Equation
- Gradient Descent

### Normal Equation

theta = inverse(X^T*X)*X^T*y

### Gradient Descent Update

theta = theta - learning_rate * (2/n) * X^T * (X*theta - y)

### Prediction

y_pred = X_new*theta

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Normal Equation | O(d^3 + n*d^2) | O(d) per sample | O(d^2) |
| Gradient Descent | O(i*n*d) | O(d) per sample | O(d) |

## 2. Polynomial Regression

### Problem Type

- Supervised learning
- Regression

### Objective

- Model nonlinear relationships using polynomial feature expansion.

### Feature Expansion

x -> [x, x^2, x^3, ..., x^p]

### Training

- Create polynomial features.
- Train linear regression on expanded feature matrix.

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Polynomial Regression with Gradient Descent | O(i*n*d_p) | O(d_p) per sample | O(d_p) |

### Symbols

- d_p = number of polynomial features after expansion

## 3. Ridge Regression

### Problem Type

- Supervised learning
- Regression

### Objective

- Linear regression with L2 regularization.

### Loss Function

loss = MSE + lambda * sum(theta_j^2)

### Effect

- Shrinks coefficients.
- Reduces overfitting.
- Handles multicollinearity.

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Ridge Regression Gradient Descent | O(i*n*d) | O(d) per sample | O(d) |

## 4. Lasso Regression

### Problem Type

- Supervised learning
- Regression

### Objective

- Linear regression with L1 regularization.

### Loss Function

loss = MSE + lambda * sum(abs(theta_j))

### Effect

- Produces sparse coefficients.
- Performs feature selection.

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Lasso Regression Coordinate Descent | O(i*n*d) | O(d) per sample | O(d) |

## 5. Elastic Net Regression

### Problem Type

- Supervised learning
- Regression

### Objective

- Linear regression with L1 and L2 regularization.

### Loss Function

loss = MSE + lambda1 * sum(abs(theta_j)) + lambda2 * sum(theta_j^2)

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Elastic Net Coordinate Descent | O(i*n*d) | O(d) per sample | O(d) |

## 6. Logistic Regression

### Problem Type

- Supervised learning
- Classification

### Objective

- Predict probability of a binary class.

### Hypothesis

p = sigmoid(X*theta)

sigmoid(z) = 1 / (1 + exp(-z))

### Loss Function

binary_cross_entropy = -(1/n) * sum(y_i*log(p_i) + (1-y_i)*log(1-p_i))

### Gradient Descent Update

theta = theta - learning_rate * (1/n) * X^T * (p - y)

### Prediction

if p >= threshold:
    class = 1

if p < threshold:
    class = 0

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Logistic Regression Gradient Descent | O(i*n*d) | O(d) per sample | O(d) |

## 7. K-Nearest Neighbors

### Problem Type

- Supervised learning
- Classification
- Regression

### Objective

- Predict using nearest training samples.

### Training

- Store training data.

### Prediction For Classification

- Compute distance to all training samples.
- Select k nearest samples.
- Return majority class.

### Prediction For Regression

- Compute distance to all training samples.
- Select k nearest samples.
- Return average target value.

### Distance Metrics

- Euclidean distance
- Manhattan distance
- Minkowski distance
- Cosine distance
- Hamming distance

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Brute-force KNN | O(n*d) storage | O(n*d) per sample | O(n*d) |
| KD-Tree KNN average | O(n*log(n)) | O(log(n)) average, O(n) worst | O(n*d) |
| Ball Tree KNN average | O(n*log(n)) | O(log(n)) average, O(n) worst | O(n*d) |

## 8. Naive Bayes

### Problem Type

- Supervised learning
- Classification

### Objective

- Predict class using Bayes theorem with feature independence assumption.

### Bayes Rule

P(class|features) = P(features|class) * P(class) / P(features)

### Variants

- Gaussian Naive Bayes
- Multinomial Naive Bayes
- Bernoulli Naive Bayes
- Complement Naive Bayes

### Prediction

class = argmax over classes of P(class) * product(P(feature_j|class))

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Naive Bayes | O(n*d) | O(d*c) per sample | O(d*c) |

## 9. Decision Tree

### Problem Type

- Supervised learning
- Classification
- Regression

### Objective

- Split data recursively to reduce impurity.

### Classification Split Criteria

- Gini impurity
- Entropy
- Information gain

### Regression Split Criteria

- Mean squared error reduction
- Mean absolute error reduction

### Training

- For each node:
  - Evaluate candidate splits.
  - Choose split with best impurity reduction.
  - Recurse until stopping condition.

### Prediction

- Traverse tree from root to leaf.
- Return leaf prediction.

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Decision Tree average | O(n*d*log(n)) | O(depth) per sample | O(nodes) |
| Decision Tree worst | O(n^2*d) | O(depth) per sample | O(nodes) |

## 10. Random Forest

### Problem Type

- Supervised learning
- Classification
- Regression

### Objective

- Ensemble of decision trees trained on bootstrapped samples and random feature subsets.

### Training

- For each tree:
  - Sample rows with replacement.
  - Sample feature subset at each split.
  - Train decision tree.

### Prediction

- Classification: majority vote across trees.
- Regression: average prediction across trees.

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Random Forest | O(t*n*d_sub*log(n)) | O(t*depth) per sample | O(t*nodes) |

### Symbols

- d_sub = number of features considered per split

## 11. Gradient Boosting

### Problem Type

- Supervised learning
- Classification
- Regression

### Objective

- Build trees sequentially, where each new tree corrects errors from previous trees.

### Training

- Initialize prediction.
- Compute residuals or negative gradients.
- Train weak learner on residuals.
- Add learner to ensemble.
- Repeat.

### Prediction

- Sum predictions from all weak learners.

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Gradient Boosted Trees | O(t*n*d*log(n)) | O(t*depth) per sample | O(t*nodes) |

## 12. Support Vector Machine

### Problem Type

- Supervised learning
- Classification
- Regression through Support Vector Regression

### Objective

- Find maximum-margin separating hyperplane.

### Linear SVM Objective

minimize 0.5 * ||w||^2 + C * sum(hinge_loss_i)

### Hinge Loss

hinge_loss = max(0, 1 - y_i*(w*x_i + b))

### Kernels

- Linear kernel
- Polynomial kernel
- Radial basis function kernel
- Sigmoid kernel

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Linear SVM | O(i*n*d) | O(d) per sample | O(d) |
| Kernel SVM | O(n^2*d) to O(n^3) | O(s*d) per sample | O(n^2) |

## Unsupervised Learning Algorithms

## 13. K-Means Clustering

### Problem Type

- Unsupervised learning
- Clustering

### Objective

- Partition data into k clusters by minimizing within-cluster sum of squares.

### Training

- Initialize k centroids.
- Assign each point to nearest centroid.
- Update each centroid as mean of assigned points.
- Repeat until convergence.

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| K-Means | O(i*n*k*d) | O(k*d) per sample | O(n*d + k*d) |

## 14. Hierarchical Clustering

### Problem Type

- Unsupervised learning
- Clustering

### Objective

- Build hierarchy of clusters.

### Types

- Agglomerative clustering
- Divisive clustering

### Linkage Methods

- Single linkage
- Complete linkage
- Average linkage
- Ward linkage

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Agglomerative Clustering | O(n^3) naive, O(n^2*log(n)) optimized | Not naturally incremental | O(n^2) |

## 15. DBSCAN

### Problem Type

- Unsupervised learning
- Density-based clustering

### Objective

- Group dense regions and identify noise points.

### Parameters

- eps = neighborhood radius
- min_samples = minimum points required for core point

### Point Types

- Core point
- Border point
- Noise point

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| DBSCAN brute force | O(n^2*d) | Not naturally incremental | O(n) |
| DBSCAN with spatial index average | O(n*log(n)) | Not naturally incremental | O(n) |

## 16. Gaussian Mixture Model

### Problem Type

- Unsupervised learning
- Probabilistic clustering

### Objective

- Model data as a mixture of Gaussian distributions.

### Training Method

- Expectation-Maximization

### E-Step

- Compute responsibility of each Gaussian for each sample.

### M-Step

- Update means, covariances, and mixture weights.

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Gaussian Mixture Model full covariance | O(i*n*k*d^2) | O(k*d^2) per sample | O(k*d^2) |

## Dimensionality Reduction Algorithms

## 17. Principal Component Analysis

### Problem Type

- Unsupervised learning
- Dimensionality reduction

### Objective

- Project data into directions of maximum variance.

### Training

- Center data.
- Compute covariance matrix or use Singular Value Decomposition.
- Select top r principal components.

### Prediction

- Project new data onto selected components.

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| PCA covariance eigendecomposition | O(n*d^2 + d^3) | O(d*r) per sample | O(d^2) |
| PCA full SVD | O(min(n^2*d, n*d^2)) | O(d*r) per sample | O(d*r) |

## 18. Linear Discriminant Analysis

### Problem Type

- Supervised learning
- Classification
- Dimensionality reduction

### Objective

- Maximize class separability.

### Training

- Compute class means.
- Compute within-class scatter.
- Compute between-class scatter.
- Solve generalized eigenvalue problem.

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| LDA | O(n*d^2 + d^3) | O(d*r) per sample | O(d^2) |

## 19. Singular Value Decomposition

### Problem Type

- Matrix factorization
- Dimensionality reduction

### Objective

- Factor matrix X into U, S, and V^T.

### Formula

X = U*S*V^T

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Full SVD | O(min(n^2*d, n*d^2)) | O(d*r) per sample | O(n*r + d*r) |
| Truncated SVD | O(i*n*d*r) | O(d*r) per sample | O(n*r + d*r) |

## 20. t-SNE

### Problem Type

- Unsupervised learning
- Nonlinear dimensionality reduction
- Visualization

### Objective

- Preserve local neighborhoods in low-dimensional space.

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Exact t-SNE | O(n^2) | Not naturally incremental | O(n^2) |
| Barnes-Hut t-SNE | O(n*log(n)) | Not naturally incremental | O(n) |

## 21. UMAP

### Problem Type

- Unsupervised learning
- Nonlinear dimensionality reduction
- Visualization

### Objective

- Preserve local and global structure using graph-based manifold learning.

### Complexity

| Method | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| UMAP approximate | O(n*log(n)) approximate | O(log(n)) approximate per sample | O(n*k) |

## Algorithm Selection Table

| Algorithm | Best For | Avoid When |
|---|---|---|
| Linear Regression | Simple regression baseline | Strong nonlinear relationships dominate |
| Polynomial Regression | Controlled nonlinear regression | Feature explosion becomes too large |
| Ridge Regression | Multicollinearity | Sparse feature selection is required |
| Lasso Regression | Feature selection | Highly correlated features dominate |
| Elastic Net | Correlated features with sparsity | Interpretability is not needed |
| Logistic Regression | Binary classification baseline | Complex nonlinear boundary dominates |
| K-Nearest Neighbors | Small datasets and local structure | Dataset is large or high-dimensional |
| Naive Bayes | Text classification and fast baseline | Feature independence assumption fails badly |
| Decision Tree | Interpretability | High variance is unacceptable |
| Random Forest | Strong tabular baseline | Low-latency prediction is strict |
| Gradient Boosting | High-performance tabular modeling | Training time must be minimal |
| Support Vector Machine | Margin-based classification | Dataset is very large |
| K-Means | Spherical clusters | Clusters have arbitrary shapes |
| Hierarchical Clustering | Cluster hierarchy analysis | Dataset is large |
| DBSCAN | Arbitrary-shaped clusters and noise detection | Density varies heavily |
| Gaussian Mixture Model | Probabilistic soft clusters | Data is not Gaussian-like |
| PCA | Linear dimensionality reduction | Nonlinear manifold dominates |
| LDA | Supervised dimensionality reduction | Class labels are unavailable |
| SVD | Matrix factorization | Nonlinear representation is required |
| t-SNE | Visualization | Need transform for new samples |
| UMAP | Visualization and manifold projection | Exact interpretability is required |

## Complexity Summary Table

| Algorithm | Training Time Complexity | Prediction Time Complexity | Space Complexity |
|---|---:|---:|---:|
| Linear Regression Normal Equation | O(d^3 + n*d^2) | O(d) | O(d^2) |
| Linear Regression Gradient Descent | O(i*n*d) | O(d) | O(d) |
| Polynomial Regression | O(i*n*d_p) | O(d_p) | O(d_p) |
| Ridge Regression | O(i*n*d) | O(d) | O(d) |
| Lasso Regression | O(i*n*d) | O(d) | O(d) |
| Elastic Net Regression | O(i*n*d) | O(d) | O(d) |
| Logistic Regression | O(i*n*d) | O(d) | O(d) |
| K-Nearest Neighbors | O(n*d) storage | O(n*d) | O(n*d) |
| Naive Bayes | O(n*d) | O(d*c) | O(d*c) |
| Decision Tree | O(n*d*log(n)) average | O(depth) | O(nodes) |
| Random Forest | O(t*n*d_sub*log(n)) | O(t*depth) | O(t*nodes) |
| Gradient Boosting | O(t*n*d*log(n)) | O(t*depth) | O(t*nodes) |
| Linear SVM | O(i*n*d) | O(d) | O(d) |
| Kernel SVM | O(n^2*d) to O(n^3) | O(s*d) | O(n^2) |
| K-Means | O(i*n*k*d) | O(k*d) | O(n*d + k*d) |
| Hierarchical Clustering | O(n^3) naive | Not naturally incremental | O(n^2) |
| DBSCAN brute force | O(n^2*d) | Not naturally incremental | O(n) |
| Gaussian Mixture Model | O(i*n*k*d^2) | O(k*d^2) | O(k*d^2) |
| PCA covariance | O(n*d^2 + d^3) | O(d*r) | O(d^2) |
| LDA | O(n*d^2 + d^3) | O(d*r) | O(d^2) |
| Full SVD | O(min(n^2*d, n*d^2)) | O(d*r) | O(n*r + d*r) |
| Exact t-SNE | O(n^2) | Not naturally incremental | O(n^2) |
| UMAP approximate | O(n*log(n)) approximate | O(log(n)) approximate | O(n*k) |
