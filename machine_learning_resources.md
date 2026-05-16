from pathlib import Path

file_name = "machine_learning_resources.md"
path = Path("/mnt/data") / file_name

content = """# Machine Learning Resources

## File Name

- `machine_learning_resources.md`

## Core Math

### Linear Algebra

- Book
  - *Introduction to Linear Algebra* — Gilbert Strang
- Topics
  - Vectors
  - Matrices
  - Matrix multiplication
  - Matrix inverse
  - Rank
  - Span
  - Basis
  - Eigenvalues
  - Eigenvectors
  - Singular Value Decomposition
  - Orthogonality
  - Projections
- Direct References
  - MIT OpenCourseWare — Linear Algebra
  - Khan Academy — Linear Algebra

### Probability

- Book
  - *Introduction to Probability* — Dimitri P. Bertsekas, John N. Tsitsiklis
- Topics
  - Random variables
  - Probability distributions
  - Conditional probability
  - Bayes theorem
  - Expectation
  - Variance
  - Covariance
  - Independence
  - Bernoulli distribution
  - Binomial distribution
  - Poisson distribution
  - Gaussian distribution
  - Central Limit Theorem
- Direct References
  - Harvard Stat 110 — Probability
  - Khan Academy — Probability and Statistics

### Statistics

- Book
  - *All of Statistics* — Larry Wasserman
- Topics
  - Descriptive statistics
  - Sampling
  - Estimation
  - Hypothesis testing
  - Confidence intervals
  - Maximum likelihood estimation
  - Bias
  - Variance
  - Correlation
  - Regression
  - Statistical inference
- Direct References
  - Penn State STAT 414 / 415
  - OpenIntro Statistics

### Calculus

- Book
  - *Calculus* — James Stewart
- Topics
  - Limits
  - Derivatives
  - Partial derivatives
  - Gradients
  - Chain rule
  - Taylor expansion
  - Optimization
  - Convexity
  - Integrals
- Direct References
  - MIT OpenCourseWare — Single Variable Calculus
  - MIT OpenCourseWare — Multivariable Calculus
  - Khan Academy — Calculus

## Programming Foundations

### Python

- Official Documentation
  - Python Tutorial
  - Python Standard Library Reference
- Books
  - *Automate the Boring Stuff with Python* — Al Sweigart
  - *Fluent Python* — Luciano Ramalho
- Topics
  - Variables
  - Data types
  - Control flow
  - Functions
  - Classes
  - Modules
  - Packages
  - File handling
  - Exceptions
  - Iterators
  - Generators
  - Decorators
  - Type hints
  - Virtual environments

### Numerical Computing

- Libraries
  - NumPy
  - SciPy
- Topics
  - Arrays
  - Broadcasting
  - Vectorization
  - Matrix operations
  - Random number generation
  - Numerical optimization
  - Numerical stability
  - Floating-point precision

### Data Handling

- Libraries
  - pandas
  - Polars
- Topics
  - DataFrames
  - Series
  - Indexing
  - Filtering
  - Aggregation
  - Grouping
  - Joins
  - Missing values
  - Time series
  - CSV files
  - JSON files
  - Parquet files

### Visualization

- Libraries
  - Matplotlib
  - Plotly
  - Altair
- Topics
  - Line charts
  - Scatter plots
  - Histograms
  - Box plots
  - Heatmaps
  - Distribution plots
  - Correlation plots
  - Model diagnostics plots

## Machine Learning Foundations

### General Machine Learning

- Books
  - *Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow* — Aurélien Géron
  - *Pattern Recognition and Machine Learning* — Christopher Bishop
  - *The Elements of Statistical Learning* — Trevor Hastie, Robert Tibshirani, Jerome Friedman
  - *An Introduction to Statistical Learning* — Gareth James, Daniela Witten, Trevor Hastie, Robert Tibshirani
- Courses
  - Stanford CS229 — Machine Learning
  - Carnegie Mellon 10-601 — Machine Learning
  - MIT 6.036 — Introduction to Machine Learning
- Topics
  - Supervised learning
  - Unsupervised learning
  - Semi-supervised learning
  - Self-supervised learning
  - Reinforcement learning
  - Regression
  - Classification
  - Clustering
  - Dimensionality reduction
  - Feature engineering
  - Model evaluation
  - Model selection
  - Cross-validation
  - Bias-variance tradeoff
  - Regularization
  - Overfitting
  - Underfitting

### Classical Machine Learning Algorithms

#### Linear Regression

- Concepts
  - Ordinary Least Squares
  - Mean Squared Error
  - Residuals
  - Normal equation
  - Gradient descent optimization
- Complexity
  - Training with normal equation: `O(n d^2 + d^3)`
  - Training with batch gradient descent: `O(k n d)`
  - Prediction: `O(d)`
  - Space: `O(n d + d)`

#### Logistic Regression

- Concepts
  - Sigmoid function
  - Log loss
  - Maximum likelihood estimation
  - Decision boundary
  - Binary classification
  - Multiclass classification with softmax
- Complexity
  - Training with gradient descent: `O(k n d)`
  - Prediction: `O(d)`
  - Space: `O(n d + d)`

#### k-Nearest Neighbors

- Concepts
  - Distance metric
  - Euclidean distance
  - Manhattan distance
  - Cosine distance
  - Majority voting
  - Weighted voting
- Complexity
  - Training: `O(n d)`
  - Prediction with brute force: `O(n d)`
  - Space: `O(n d)`

#### Naive Bayes

- Concepts
  - Bayes theorem
  - Conditional independence
  - Gaussian Naive Bayes
  - Multinomial Naive Bayes
  - Bernoulli Naive Bayes
- Complexity
  - Training: `O(n d)`
  - Prediction: `O(c d)`
  - Space: `O(c d)`

#### Decision Tree

- Concepts
  - Entropy
  - Information gain
  - Gini impurity
  - Tree depth
  - Pruning
  - Splitting criteria
- Complexity
  - Training: `O(n d log n)`
  - Prediction: `O(h)`
  - Space: `O(nodes)`

#### Random Forest

- Concepts
  - Bagging
  - Bootstrap sampling
  - Feature subsampling
  - Ensemble voting
  - Out-of-bag error
- Complexity
  - Training: `O(t n d log n)`
  - Prediction: `O(t h)`
  - Space: `O(t nodes)`

#### Gradient Boosting

- Concepts
  - Boosting
  - Additive models
  - Weak learners
  - Residual fitting
  - Learning rate
  - Shrinkage
- Implementations
  - XGBoost
  - LightGBM
  - CatBoost
- Complexity
  - Training: `O(t n d log n)`
  - Prediction: `O(t h)`
  - Space: `O(t nodes)`

#### Support Vector Machine

- Concepts
  - Maximum margin classifier
  - Kernel trick
  - Linear kernel
  - Polynomial kernel
  - Radial Basis Function kernel
  - Soft margin
- Complexity
  - Training kernel SVM: `O(n^2 d)` to `O(n^3)`
  - Prediction: `O(s d)`
  - Space: `O(n^2)` for kernel matrix

#### k-Means Clustering

- Concepts
  - Centroids
  - Inertia
  - Lloyd algorithm
  - Cluster assignment
  - Centroid update
- Complexity
  - Training: `O(k n d i)`
  - Prediction: `O(k d)`
  - Space: `O(n d + k d)`

#### Principal Component Analysis

- Concepts
  - Covariance matrix
  - Eigen decomposition
  - Singular Value Decomposition
  - Explained variance
  - Dimensionality reduction
- Complexity
  - Training with SVD: `O(min(n d^2, d n^2))`
  - Transform: `O(d r)`
  - Space: `O(n d + d r)`

## Deep Learning

### Neural Network Foundations

- Books
  - *Deep Learning* — Ian Goodfellow, Yoshua Bengio, Aaron Courville
  - *Neural Networks and Deep Learning* — Michael Nielsen
- Courses
  - Stanford CS231n — Convolutional Neural Networks for Visual Recognition
  - Stanford CS224n — Natural Language Processing with Deep Learning
  - MIT 6.S191 — Introduction to Deep Learning
- Topics
  - Perceptron
  - Multilayer Perceptron
  - Activation functions
  - Loss functions
  - Backpropagation
  - Gradient descent
  - Stochastic gradient descent
  - Mini-batch gradient descent
  - Momentum
  - RMSProp
  - Adam
  - Weight initialization
  - Batch normalization
  - Layer normalization
  - Dropout
  - Residual connections
  - Learning rate scheduling

### Deep Learning Frameworks

- PyTorch
  - Tensors
  - Autograd
  - Modules
  - Optimizers
  - Datasets
  - DataLoaders
  - GPU acceleration
  - Distributed training
- TensorFlow
  - Tensors
  - Keras API
  - GradientTape
  - SavedModel
  - TensorBoard
  - TensorFlow Serving
- JAX
  - Arrays
  - Just-In-Time compilation
  - Automatic differentiation
  - Vectorization
  - Functional transformations

### Convolutional Neural Networks

- Concepts
  - Convolution
  - Filters
  - Kernels
  - Stride
  - Padding
  - Pooling
  - Feature maps
  - Receptive field
- Architectures
  - LeNet
  - AlexNet
  - VGG
  - GoogLeNet
  - ResNet
  - DenseNet
  - EfficientNet
  - ConvNeXt
- Complexity
  - Standard convolution: `O(H W C_in C_out K^2)`
  - Depthwise convolution: `O(H W C_in K^2)`
  - Pointwise convolution: `O(H W C_in C_out)`

### Recurrent Neural Networks

- Concepts
  - Hidden state
  - Sequence modeling
  - Backpropagation Through Time
  - Vanishing gradient
  - Exploding gradient
- Architectures
  - Vanilla RNN
  - LSTM
  - GRU
  - Bidirectional RNN
- Complexity
  - Vanilla RNN per sequence: `O(T h (d + h))`
  - LSTM per sequence: `O(T h (d + h))`
  - Space: `O(T h)`

### Transformers

- Papers
  - *Attention Is All You Need* — Vaswani, Shazeer, Parmar, Uszkoreit, Jones, Gomez, Kaiser, Polosukhin
  - *BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding* — Devlin, Chang, Lee, Toutanova
  - *Language Models are Unsupervised Multitask Learners* — Radford, Wu, Child, Luan, Amodei, Sutskever
- Concepts
  - Tokenization
  - Embeddings
  - Positional encoding
  - Self-attention
  - Multi-head attention
  - Feed-forward network
  - Residual connection
  - Layer normalization
  - Encoder
  - Decoder
  - Causal masking
  - Cross-attention
- Complexity
  - Self-attention time: `O(n^2 d)`
  - Self-attention space: `O(n^2)`
  - Feed-forward time: `O(n d f)`
  - Total transformer block time: `O(n^2 d + n d f)`

## Natural Language Processing

### Core NLP

- Books
  - *Speech and Language Processing* — Daniel Jurafsky, James H. Martin
  - *Natural Language Processing with Python* — Steven Bird, Ewan Klein, Edward Loper
- Topics
  - Tokenization
  - Stemming
  - Lemmatization
  - Part-of-speech tagging
  - Named entity recognition
  - Parsing
  - Language modeling
  - Text classification
  - Sequence labeling
  - Question answering
  - Summarization
  - Machine translation
  - Semantic similarity

### NLP Libraries

- spaCy
- NLTK
- Hugging Face Transformers
- SentenceTransformers
- Gensim

### Embeddings

- Algorithms
  - TF-IDF
  - Word2Vec
  - GloVe
  - FastText
  - BERT embeddings
  - Sentence-BERT embeddings
- Complexity
  - TF-IDF fitting: `O(N V)`
  - TF-IDF transform: `O(nnz)`
  - Word2Vec Skip-Gram training: `O(T c d)`
  - Transformer embedding generation: `O(n^2 d + n d f)`

## Computer Vision

### Core Computer Vision

- Books
  - *Computer Vision: Algorithms and Applications* — Richard Szeliski
  - *Multiple View Geometry in Computer Vision* — Richard Hartley, Andrew Zisserman
- Topics
  - Image classification
  - Object detection
  - Semantic segmentation
  - Instance segmentation
  - Image retrieval
  - Optical flow
  - Pose estimation
  - Image generation
  - Contrastive vision-language learning

### Vision Architectures

- CNN-based
  - ResNet
  - DenseNet
  - EfficientNet
  - ConvNeXt
- Detection
  - R-CNN
  - Fast R-CNN
  - Faster R-CNN
  - YOLO
  - SSD
  - RetinaNet
- Segmentation
  - FCN
  - U-Net
  - DeepLab
  - Mask R-CNN
  - Segment Anything Model
- Transformer-based
  - Vision Transformer
  - Swin Transformer
  - DETR

## Reinforcement Learning

### Core Reinforcement Learning

- Book
  - *Reinforcement Learning: An Introduction* — Richard Sutton, Andrew Barto
- Topics
  - Agent
  - Environment
  - State
  - Action
  - Reward
  - Policy
  - Value function
  - Q-function
  - Bellman equation
  - Markov Decision Process
  - Exploration
  - Exploitation
  - Temporal Difference learning
  - Policy gradient

### Reinforcement Learning Algorithms

- Dynamic Programming
  - Policy iteration
  - Value iteration
- Model-free learning
  - Monte Carlo control
  - SARSA
  - Q-learning
- Deep reinforcement learning
  - Deep Q-Network
  - Double Deep Q-Network
  - Dueling Deep Q-Network
  - Policy Gradient
  - Actor-Critic
  - Advantage Actor-Critic
  - Proximal Policy Optimization
  - Deep Deterministic Policy Gradient
  - Soft Actor-Critic
- Complexity
  - Value iteration: `O(S^2 A i)`
  - Q-learning update: `O(1)`
  - Tabular Q-learning space: `O(S A)`

## Machine Learning Engineering

### Experiment Tracking

- Tools
  - MLflow
  - Weights & Biases
  - TensorBoard
- Concepts
  - Metrics tracking
  - Hyperparameter logging
  - Artifact logging
  - Model registry
  - Reproducibility
  - Versioning

### Data Versioning

- Tools
  - DVC
  - LakeFS
- Concepts
  - Dataset snapshots
  - Data lineage
  - Feature versioning
  - Reproducible pipelines

### Feature Engineering

- Libraries
  - scikit-learn
  - Featuretools
- Concepts
  - Scaling
  - Normalization
  - Standardization
  - One-hot encoding
  - Ordinal encoding
  - Target encoding
  - Feature crosses
  - Text features
  - Date-time features
  - Aggregation features

### Model Serving

- Tools
  - FastAPI
  - Flask
  - BentoML
  - TorchServe
  - TensorFlow Serving
  - ONNX Runtime
- Concepts
  - REST API inference
  - Batch inference
  - Streaming inference
  - Model serialization
  - Latency
  - Throughput
  - Autoscaling
  - Canary deployment
  - A/B testing

### Monitoring

- Tools
  - Evidently AI
  - WhyLabs
  - Prometheus
  - Grafana
- Concepts
  - Data drift
  - Concept drift
  - Prediction drift
  - Model performance monitoring
  - Latency monitoring
  - Error monitoring
  - Alerting

## MLOps

### Pipeline Orchestration

- Tools
  - Airflow
  - Prefect
  - Dagster
  - Kubeflow Pipelines
- Concepts
  - Directed Acyclic Graphs
  - Task dependencies
  - Scheduling
  - Retries
  - Caching
  - Backfills
  - Parameterized runs

### Containerization

- Tools
  - Docker
  - Podman
- Concepts
  - Images
  - Containers
  - Dockerfile
  - Layers
  - Build context
  - Volumes
  - Networks
  - Registries

### Deployment Infrastructure

- Tools
  - Kubernetes
  - Helm
  - Terraform
- Concepts
  - Pods
  - Deployments
  - Services
  - Ingress
  - ConfigMaps
  - Secrets
  - Horizontal Pod Autoscaler
  - Infrastructure as Code

## Responsible Machine Learning

### Fairness

- Topics
  - Demographic parity
  - Equal opportunity
  - Equalized odds
  - Calibration
  - Bias measurement
  - Bias mitigation

### Explainability

- Tools
  - SHAP
  - LIME
  - Captum
  - InterpretML
- Topics
  - Feature attribution
  - Global explanations
  - Local explanations
  - Counterfactual explanations
  - Partial dependence plots
  - Individual conditional expectation plots

### Privacy

- Topics
  - Differential privacy
  - Federated learning
  - Data anonymization
  - Data minimization
  - Access control
  - Secure aggregation

### Security

- Topics
  - Adversarial examples
  - Data poisoning
  - Model extraction
  - Prompt injection for language model systems
  - Supply-chain security
  - Model artifact integrity

## Datasets

### General Tabular

- UCI Machine Learning Repository
- OpenML
- Kaggle Datasets
- Google Dataset Search

### Vision

- MNIST
- Fashion-MNIST
- CIFAR-10
- CIFAR-100
- ImageNet
- COCO
- Open Images
- Cityscapes
- Pascal VOC

### NLP

- GLUE
- SuperGLUE
- SQuAD
- IMDb Reviews
- Common Crawl
- WikiText
- The Pile

### Time Series

- M4 Competition Dataset
- M5 Forecasting Dataset
- UCR Time Series Classification Archive
- Electricity Load Diagrams Dataset

### Recommender Systems

- MovieLens
- Amazon Reviews Dataset
- Yelp Open Dataset
- Last.fm Dataset

## Benchmarking

### Classification Metrics

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- PR-AUC
- Log loss
- Confusion matrix

### Regression Metrics

- Mean Absolute Error
- Mean Squared Error
- Root Mean Squared Error
- R-squared
- Mean Absolute Percentage Error
- Median Absolute Error

### Ranking Metrics

- Precision at K
- Recall at K
- Mean Reciprocal Rank
- Mean Average Precision
- Normalized Discounted Cumulative Gain

### Clustering Metrics

- Silhouette score
- Davies-Bouldin index
- Calinski-Harabasz index
- Adjusted Rand Index
- Normalized Mutual Information

## Papers

### Foundational Machine Learning

- *A Few Useful Things to Know About Machine Learning* — Pedro Domingos
- *Statistical Modeling: The Two Cultures* — Leo Breiman
- *Random Forests* — Leo Breiman
- *Support-Vector Networks* — Corinna Cortes, Vladimir Vapnik
- *Greedy Function Approximation: A Gradient Boosting Machine* — Jerome Friedman

### Deep Learning

- *ImageNet Classification with Deep Convolutional Neural Networks* — Alex Krizhevsky, Ilya Sutskever, Geoffrey Hinton
- *Deep Residual Learning for Image Recognition* — Kaiming He, Xiangyu Zhang, Shaoqing Ren, Jian Sun
- *Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift* — Sergey Ioffe, Christian Szegedy
- *Dropout: A Simple Way to Prevent Neural Networks from Overfitting* — Nitish Srivastava, Geoffrey Hinton, Alex Krizhevsky, Ilya Sutskever, Ruslan Salakhutdinov
- *Adam: A Method for Stochastic Optimization* — Diederik Kingma, Jimmy Ba

### Natural Language Processing

- *Efficient Estimation of Word Representations in Vector Space* — Tomas Mikolov, Kai Chen, Greg Corrado, Jeffrey Dean
- *GloVe: Global Vectors for Word Representation* — Jeffrey Pennington, Richard Socher, Christopher Manning
- *Attention Is All You Need* — Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan Gomez, Łukasz Kaiser, Illia Polosukhin
- *BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding* — Jacob Devlin, Ming-Wei Chang, Kenton Lee, Kristina Toutanova

### Reinforcement Learning

- *Human-level Control through Deep Reinforcement Learning* — Volodymyr Mnih, Koray Kavukcuoglu, David Silver, Alex Graves, Ioannis Antonoglou, Daan Wierstra, Martin Riedmiller
- *Mastering the Game of Go with Deep Neural Networks and Tree Search* — David Silver, Aja Huang, Chris Maddison, Arthur Guez, Laurent Sifre, George van den Driessche, Julian Schrittwieser, Ioannis Antonoglou, Veda Panneershelvam, Marc Lanctot, Sander Dieleman, Dominik Grewe, John Nham, Nal Kalchbrenner, Ilya Sutskever, Timothy Lillicrap, Madeleine Leach, Koray Kavukcuoglu, Thore Graepel, Demis Hassabis
- *Proximal Policy Optimization Algorithms* — John Schulman, Filip Wolski, Prafulla Dhariwal, Alec Radford, Oleg Klimov

## Libraries

### Core Machine Learning

- scikit-learn
- XGBoost
- LightGBM
- CatBoost
- statsmodels

### Deep Learning

- PyTorch
- TensorFlow
- Keras
- JAX
- Flax
- Lightning

### NLP

- spaCy
- NLTK
- Transformers
- SentenceTransformers
- Gensim

### Computer Vision

- OpenCV
- torchvision
- Albumentations
- timm
- Detectron2

### Recommender Systems

- Surprise
- LightFM
- implicit
- RecBole

### Graph Machine Learning

- NetworkX
- PyTorch Geometric
- Deep Graph Library

### Time Series

- statsmodels
- sktime
- Darts
- Prophet

## Practical Projects

### Beginner

- House price regression
- Customer churn classification
- Titanic survival classification
- Handwritten digit classification
- Movie review sentiment classification

### Intermediate

- Credit risk scoring
- Product recommendation system
- Fraud detection
- Image classification API
- Resume parser
- Demand forecasting
- Customer segmentation

### Advanced

- Real-time model monitoring dashboard
- Transformer-based text classifier
- Retrieval-augmented question answering system
- Object detection pipeline
- Semantic search engine
- End-to-end MLOps pipeline
- Federated learning simulation
- Reinforcement learning game agent

## GitHub Repositories

- scikit-learn
- pytorch
- tensorflow
- keras-team/keras
- huggingface/transformers
- explosion/spaCy
- dmlc/xgboost
- microsoft/LightGBM
- catboost/catboost
- opencv/opencv
- mlflow/mlflow
- iterative/dvc

## Reference Documentation

- Python Documentation
- NumPy Documentation
- pandas Documentation
- scikit-learn Documentation
- PyTorch Documentation
- TensorFlow Documentation
- JAX Documentation
- XGBoost Documentation
- LightGBM Documentation
- CatBoost Documentation
- OpenCV Documentation
- spaCy Documentation
- Hugging Face Transformers Documentation
- MLflow Documentation
- DVC Documentation
- Docker Documentation
- Kubernetes Documentation

## Glossary

### Data

- Dataset
  - A collection of examples used for training, validation, or testing.
- Feature
  - An input variable used by a model.
- Label
  - The target output for supervised learning.
- Sample
  - One row, record, image, text, audio clip, or observation.
- Batch
  - A group of samples processed together.

### Modeling

- Model
  - A mathematical function that maps inputs to outputs.
- Parameter
  - A value learned during training.
- Hyperparameter
  - A value configured before training.
- Loss function
  - A function that measures prediction error.
- Optimization
  - The process of minimizing or maximizing an objective function.
- Generalization
  - The ability of a model to perform well on unseen data.

### Evaluation

- Training set
  - Data used to fit model parameters.
- Validation set
  - Data used to tune model choices.
- Test set
  - Data used for final evaluation.
- Cross-validation
  - Repeated splitting strategy for estimating model performance.
- Data leakage
  - Use of information during training that would not be available during inference.

### Deployment

- Inference
  - Running a trained model on new input.
- Latency
  - Time taken to return one prediction.
- Throughput
  - Number of predictions served per unit time.
- Drift
  - Change in data distribution or target relationship after deployment.
- Monitoring
  - Continuous tracking of model behavior after deployment.
"""

path.write_text(content, encoding="utf-8")
print(f"Created: {path}")
