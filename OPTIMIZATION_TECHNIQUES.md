# Optimization Techniques

## Purpose

- Optimization is the process of finding model parameters that minimize a loss function.
- Machine learning models learn by solving optimization problems.
- The optimizer controls:
  - Convergence speed
  - Training stability
  - Final model quality
  - Memory usage
  - Sensitivity to learning rate

## Core Optimization Problem

### Objective

minimize J(theta)

### Terms

- J(theta) = loss function
- theta = model parameters
- gradient = direction of steepest increase
- negative gradient = direction of steepest decrease

## Optimization Pipeline

- Step 1: Define model
- Step 2: Define loss function
- Step 3: Initialize parameters
- Step 4: Compute predictions
- Step 5: Compute loss
- Step 6: Compute gradients
- Step 7: Update parameters
- Step 8: Repeat until stopping condition

## Loss Functions

## 1. Mean Squared Error

### Formula

MSE = (1/n) * sum((y_i - y_pred_i)^2)

### Use Case

- Regression
- Penalizes large errors strongly

### Gradient For Linear Regression

gradient = (2/n) * X^T * (X*theta - y)

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| MSE computation | O(n) | O(1) |
| MSE gradient for linear model | O(n*d) | O(d) |

## 2. Mean Absolute Error

### Formula

MAE = (1/n) * sum(abs(y_i - y_pred_i))

### Use Case

- Regression with outliers
- Robust error measurement

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| MAE computation | O(n) | O(1) |
| MAE subgradient for linear model | O(n*d) | O(d) |

## 3. Binary Cross-Entropy

### Formula

BCE = -(1/n) * sum(y_i*log(p_i) + (1-y_i)*log(1-p_i))

### Use Case

- Binary classification
- Logistic regression
- Binary neural network classifier

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Binary cross-entropy | O(n) | O(1) |
| BCE gradient for logistic regression | O(n*d) | O(d) |

## 4. Categorical Cross-Entropy

### Formula

CCE = -(1/n) * sum(sum(y_ij * log(p_ij)))

### Use Case

- Multiclass classification
- Softmax classifier
- Neural network classifier

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Categorical cross-entropy | O(n*c) | O(1) |
| CCE gradient for linear softmax | O(n*d*c) | O(d*c) |

### Symbols

- c = number of classes

## 5. Hinge Loss

### Formula

hinge_loss = max(0, 1 - y_i * score_i)

### Use Case

- Support Vector Machine
- Maximum-margin classification

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Hinge loss | O(n) | O(1) |
| Hinge loss gradient for linear SVM | O(n*d) | O(d) |

## 6. Huber Loss

### Formula

if abs(error) <= delta:
    loss = 0.5 * error^2

if abs(error) > delta:
    loss = delta * (abs(error) - 0.5*delta)

### Use Case

- Regression with some outliers
- Combines MSE and MAE behavior

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Huber loss | O(n) | O(1) |
| Huber gradient for linear model | O(n*d) | O(d) |

## Gradient Descent Family

## 1. Batch Gradient Descent

### Method

- Uses entire training dataset for each parameter update.

### Update Rule

theta = theta - learning_rate * gradient

### Properties

- Stable gradient estimate
- Slow on large datasets
- Deterministic if data and initialization are fixed

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| One update | O(n*d) | O(d) |
| One full training run | O(i*n*d) | O(d) |

### Symbols

- n = number of samples
- d = number of features
- i = number of iterations

## 2. Stochastic Gradient Descent

### Method

- Uses one training sample for each parameter update.

### Update Rule

theta = theta - learning_rate * gradient_single_sample

### Properties

- Fast updates
- Noisy optimization path
- Can escape shallow local minima
- Needs learning rate control

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| One update | O(d) | O(d) |
| One epoch | O(n*d) | O(d) |
| Full training | O(e*n*d) | O(d) |

### Symbols

- e = number of epochs

## 3. Mini-Batch Gradient Descent

### Method

- Uses a small batch of samples for each parameter update.

### Update Rule

theta = theta - learning_rate * gradient_batch

### Properties

- Standard choice for neural networks
- Better hardware utilization than stochastic gradient descent
- Less noisy than stochastic gradient descent
- Faster than batch gradient descent on large datasets

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| One update | O(b*d) | O(b*d) |
| One epoch | O(n*d) | O(b*d) |
| Full training | O(e*n*d) | O(b*d) |

### Symbols

- b = batch size

## Momentum-Based Optimization

## 1. Momentum

### Method

- Maintains velocity vector using past gradients.

### Update Rule

velocity = beta * velocity + gradient

theta = theta - learning_rate * velocity

### Properties

- Reduces oscillation
- Speeds movement in consistent gradient direction
- Useful in ravines and poorly conditioned loss surfaces

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Momentum update | O(d) | O(d) |

## 2. Nesterov Accelerated Gradient

### Method

- Computes gradient after looking ahead in direction of momentum.

### Update Rule

lookahead_theta = theta - learning_rate * beta * velocity

velocity = beta * velocity + gradient(lookahead_theta)

theta = theta - learning_rate * velocity

### Properties

- More anticipatory than classical momentum
- Can improve convergence stability

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Nesterov update | O(d) plus gradient cost | O(d) |

## Adaptive Learning Rate Optimizers

## 1. AdaGrad

### Method

- Accumulates squared gradients.
- Divides learning rate by accumulated gradient magnitude.

### Update Rule

G = G + gradient^2

theta = theta - learning_rate * gradient / sqrt(G + epsilon)

### Properties

- Good for sparse features
- Learning rate decays continuously
- Can become too small over time

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| AdaGrad update | O(d) | O(d) |

## 2. RMSProp

### Method

- Uses exponentially weighted moving average of squared gradients.

### Update Rule

S = beta*S + (1-beta)*gradient^2

theta = theta - learning_rate * gradient / sqrt(S + epsilon)

### Properties

- Fixes AdaGrad's aggressive learning rate decay
- Useful for non-stationary objectives

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| RMSProp update | O(d) | O(d) |

## 3. Adam

### Method

- Combines momentum and RMSProp.
- Tracks first moment and second moment of gradients.

### Update Rule

m = beta1*m + (1-beta1)*gradient

v = beta2*v + (1-beta2)*gradient^2

m_hat = m / (1-beta1^t)

v_hat = v / (1-beta2^t)

theta = theta - learning_rate * m_hat / sqrt(v_hat + epsilon)

### Properties

- Strong default optimizer for neural networks
- Handles sparse gradients
- Handles noisy gradients
- Requires extra memory for first and second moments

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Adam update | O(d) | O(d) |

## 4. AdamW

### Method

- Adam with decoupled weight decay.

### Update Rule

theta = theta - learning_rate * weight_decay * theta

theta = theta - learning_rate * adam_update

### Properties

- Better regularization behavior than Adam with L2 penalty
- Common in transformer training

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| AdamW update | O(d) | O(d) |

## Learning Rate Techniques

## 1. Constant Learning Rate

### Formula

learning_rate_t = learning_rate_0

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Constant learning rate calculation | O(1) | O(1) |

## 2. Step Decay

### Formula

learning_rate_t = learning_rate_0 * drop_rate^floor(epoch / step_size)

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Step decay calculation | O(1) | O(1) |

## 3. Exponential Decay

### Formula

learning_rate_t = learning_rate_0 * exp(-decay_rate * epoch)

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Exponential decay calculation | O(1) | O(1) |

## 4. Cosine Annealing

### Formula

learning_rate_t = learning_rate_min + 0.5*(learning_rate_max - learning_rate_min)*(1 + cos(pi*t/T))

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Cosine annealing calculation | O(1) | O(1) |

## 5. Learning Rate Warmup

### Formula

learning_rate_t = learning_rate_max * t / warmup_steps

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Warmup learning rate calculation | O(1) | O(1) |

## Regularization

## 1. L1 Regularization

### Formula

loss_total = loss + lambda * sum(abs(theta_j))

### Effect

- Encourages sparse weights.
- Can perform feature selection.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| L1 penalty computation | O(d) | O(1) |
| L1 gradient update | O(d) | O(d) |

## 2. L2 Regularization

### Formula

loss_total = loss + lambda * sum(theta_j^2)

### Effect

- Shrinks weights.
- Reduces overfitting.
- Does not usually produce exact zero weights.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| L2 penalty computation | O(d) | O(1) |
| L2 gradient update | O(d) | O(d) |

## 3. Elastic Net

### Formula

loss_total = loss + lambda1 * sum(abs(theta_j)) + lambda2 * sum(theta_j^2)

### Effect

- Combines L1 and L2 regularization.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Elastic Net penalty computation | O(d) | O(1) |
| Elastic Net gradient update | O(d) | O(d) |

## 4. Early Stopping

### Method

- Stop training when validation performance stops improving.

### Complexity

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Early stopping check | O(1) per epoch | O(1) |
| Training with early stopping | O(e_actual*T_epoch) | O(S_model) |

## Convex And Non-Convex Optimization

## Convex Optimization

### Definition

- Any local minimum is also a global minimum.

### Examples

- Linear regression with MSE
- Logistic regression with cross-entropy
- Linear SVM with hinge loss

## Non-Convex Optimization

### Definition

- Local minima, saddle points, and flat regions may exist.

### Examples

- Neural networks
- Deep learning models
- Matrix factorization

## Optimization Problems

| Problem | Description | Common Fix |
|---|---|---|
| Vanishing gradients | Gradients become very small | ReLU, normalization, residual connections |
| Exploding gradients | Gradients become very large | Gradient clipping, normalization |
| Saddle points | Gradient near zero but not minimum | Momentum, Adam |
| Poor conditioning | Loss surface has uneven curvature | Feature scaling, adaptive optimizers |
| Learning rate too high | Loss diverges | Lower learning rate |
| Learning rate too low | Training is slow | Increase learning rate |

## Optimizer Selection Table

| Optimizer | Best Use Case | Time Complexity Per Update | Space Complexity |
|---|---|---:|---:|
| Batch Gradient Descent | Small datasets | O(n*d) | O(d) |
| Stochastic Gradient Descent | Large simple models | O(d) | O(d) |
| Mini-Batch Gradient Descent | Neural networks | O(b*d) | O(b*d) |
| Momentum | Noisy gradient paths | O(d) | O(d) |
| Nesterov Accelerated Gradient | Momentum with lookahead | O(d) plus gradient cost | O(d) |
| AdaGrad | Sparse features | O(d) | O(d) |
| RMSProp | Non-stationary objectives | O(d) | O(d) |
| Adam | General neural networks | O(d) | O(d) |
| AdamW | Transformer-style models | O(d) | O(d) |

## Symbols

- n = number of samples
- d = number of parameters or features
- i = number of iterations
- e = number of epochs
- b = batch size
- c = number of classes
- T_model = model training time
- S_model = model memory usage
- T_epoch = time per epoch
