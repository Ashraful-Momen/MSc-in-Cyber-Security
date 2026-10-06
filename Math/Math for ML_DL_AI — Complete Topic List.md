# Math for ML/DL/AI --- Complete Topic-wise List

**How to use this:** Take each topic below and ask an AI (or search
YouTube/textbooks) to explain it with: (1) intuition in plain words, (2)
the formula, (3) a worked numerical example, (4) where it\'s used in
ML/DL. This is applied-level math --- you need to *use* these tools, not
prove them from first principles.

------------------------------------------------------------------------

## 1. Linear Algebra (Matrix & Vector)

### Vectors

-   Vector definition, vector as a point/arrow in space
-   Vector addition, subtraction, scalar multiplication
-   Vector magnitude/norm (L1 norm, L2 norm --- very important, used in
    regularization)
-   Unit vector, normalization
-   Dot product (scalar product) --- geometric meaning (projection,
    angle between vectors)
-   Cross product (brief --- less used in ML, skip if short on time)
-   Vector space, basis, dimension (conceptual only)

### Matrices

-   Matrix definition, types (square, identity, diagonal, symmetric,
    sparse)
-   Matrix addition, subtraction, scalar multiplication
-   **Matrix multiplication** (rule, dimensions must match --- this is
    everywhere in DL)
-   Transpose of a matrix
-   Identity matrix, inverse of a matrix (concept --- when it exists,
    why it matters)
-   Determinant (concept-level --- what it tells you about a matrix)
-   Rank of a matrix (concept-level)

### Eigen-concepts (important for PCA/dimensionality reduction)

-   Eigenvalues and Eigenvectors --- what they represent geometrically
-   Eigen-decomposition (concept only)
-   **Theorem to know:** Spectral theorem (concept-level --- symmetric
    matrices have real eigenvalues) --- just the idea, not the proof

### Special topics for ML/DL

-   Tensors (generalization of scalar → vector → matrix → tensor) ---
    this is what PyTorch uses
-   Matrix as a linear transformation (rotate/scale/shear a space ---
    helps visualize what neural network layers do)
-   **PCA (Principal Component Analysis)** --- how
    eigenvectors/eigenvalues are used to reduce dimensions
-   Cosine similarity (dot product + norm --- used in comparing
    vectors/embeddings, very relevant for log/text data)

------------------------------------------------------------------------

## 2. Calculus

### Differential Calculus

-   What a derivative means (rate of change, slope of a curve)
-   Derivative of common functions (power rule, exponential,
    logarithmic) --- just the rules, not derivations
-   **Chain rule** --- critical, this is literally how backpropagation
    works
-   Partial derivatives (derivative with respect to one variable,
    holding others constant)
-   Gradient (vector of partial derivatives) --- the core object in
    optimization

### Optimization-focused Calculus

-   **Gradient Descent** --- the algorithm itself, how it uses
    derivatives to minimize a function
-   Local minimum vs. global minimum, saddle points (concept-level)
-   Learning rate --- why it matters, what happens if too high/too low
-   Convex vs. non-convex functions (concept-level --- why neural
    network loss landscapes are non-convex)

### Backpropagation-specific

-   **Chain rule applied to computational graphs** --- this is literally
    what backprop is
-   Vanishing gradient / exploding gradient (concept --- why deep
    networks can struggle to train)

### What you can SKIP

-   Integral calculus (rarely needed for applied ML/DL --- skip unless
    you hit something specific that needs it)
-   Multivariable calculus proofs, limits/continuity rigor --- skip,
    just use the intuition

------------------------------------------------------------------------

## 3. Probability

### Basics

-   Sample space, events, probability axioms
-   Independent vs. dependent events
-   **Conditional probability** --- P(A\|B), critical for Bayes
-   **Bayes\' Theorem** --- the actual theorem, formula, and a worked
    example (you already touched Naive Bayes in your course, revisit
    this properly)
-   Law of Total Probability

### Random Variables

-   Discrete vs. continuous random variables
-   Probability Mass Function (PMF), Probability Density Function (PDF)
-   Cumulative Distribution Function (CDF)
-   Expectation (mean of a random variable), Variance, Standard
    Deviation

### Distributions (know these by name + shape + when used)

-   **Normal (Gaussian) distribution** --- most important one, know the
    formula and properties (68-95-99.7 rule)
-   Bernoulli distribution (binary outcomes --- used in binary
    classification)
-   Binomial distribution
-   Poisson distribution (useful for modeling rare events --- relevant
    to rare attack events in security data!)
-   Uniform distribution

### ML-specific probability concepts

-   Maximum Likelihood Estimation (MLE) --- concept-level, how models
    \"learn\" parameters that make observed data most probable
-   Entropy and Information Gain --- used in Decision Trees (you\'ve
    covered this in your course, connect it back here)
-   Cross-Entropy Loss --- the loss function used in classification,
    rooted in information theory
-   KL Divergence (Kullback-Leibler) --- concept-level, used in some
    anomaly detection and autoencoder loss functions (relevant to your
    thesis!)

------------------------------------------------------------------------

## 4. Statistics

### Descriptive Statistics

-   Mean, Median, Mode
-   Variance, Standard Deviation
-   Percentiles, Quartiles, IQR (Interquartile Range) --- used in
    outlier detection
-   Skewness, Kurtosis (concept-level --- shape of data distribution)

### Inferential Statistics

-   Population vs. Sample
-   Central Limit Theorem (CLT) --- **important theorem**, concept: why
    sample means tend toward normal distribution
-   Confidence Intervals (concept-level)
-   **Hypothesis Testing** --- null vs. alternative hypothesis, p-value,
    significance level (α)
-   Type I and Type II errors (very relevant --- directly maps to False
    Positive/False Negative in your security detection model!)

### Correlation & Regression (statistical foundation, you\'ve done the ML side already)

-   Correlation coefficient (Pearson correlation)
-   Correlation vs. causation (concept --- important for interpreting
    results honestly in your paper)

### Statistics for Model Evaluation (directly useful for your thesis)

-   Precision, Recall, F1-score --- statistical definitions (you know
    these practically, learn the formula-level understanding)
-   ROC Curve, AUC --- statistical interpretation
-   Confusion Matrix --- the four quadrants (TP, TN, FP, FN) and what
    each means in a security context

------------------------------------------------------------------------

## Suggested order to study (if doing this alongside your course revision)

1.  **Linear Algebra basics** (vectors, matrix multiplication) --- do
    this first, everything in PyTorch depends on this
2.  **Probability basics + Bayes\' Theorem** --- connects directly to
    what you already learned in Naive Bayes
3.  **Statistics --- descriptive + Type I/II errors** --- connects
    directly to your model evaluation metrics
4.  **Calculus --- derivatives, gradient, chain rule** --- do this once
    you\'re ready to understand backpropagation properly
5.  **Eigenvalues/PCA + Normal distribution + Entropy/KL Divergence**
    --- do these last, they\'re the more advanced pieces you\'ll need
    specifically for anomaly detection (Autoencoders) later in your
    thesis

------------------------------------------------------------------------

## Good free resources for these topics

-   **3Blue1Brown** (YouTube) --- \"Essence of Linear Algebra\" and
    \"Essence of Calculus\" series --- best intuition-building videos,
    no heavy math background needed
-   **StatQuest with Josh Starmer** (YouTube) --- excellent for
    probability, statistics, and ML-statistics connections (Bayes,
    entropy, p-values, ROC/AUC all covered clearly)
-   **Khan Academy** --- if you want structured practice problems for
    any topic above
