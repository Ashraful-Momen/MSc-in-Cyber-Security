# 🎯 Final Master Math Checklist — For AI/ML/DL (Complete Life Reference)

**How to use:** For each topic below, ask AI to generate a note covering: Definition → Types → Formula/Law/Theorem → Worked Example → Problem-solving practice. Check off each topic once your note is made AND you've solved the practice problems yourself by hand. Target: 1.5–2 months, roughly one Pillar every 8–12 days.

---

## 📌 PILLAR 1 — PROBABILITY (Foundation of everything else)

### 1.1 Basic Probability

- [ ] **Definition:** Sample space, event, probability axioms (0 ≤ P(A) ≤ 1)
- [ ] **Types:** Independent vs. Dependent events, Mutually exclusive events
- [ ] **Laws:** Addition Rule — P(A∪B) = P(A)+P(B)−P(A∩B); Multiplication Rule — P(A∩B) = P(A)·P(B|A)
- [ ] **Problem-solving:** Dice/card/coin classic problems, at least 5 solved by hand

### 1.2 Conditional Probability & Bayes' Theorem ⭐ (Critical — do not skip)

- [ ] **Definition:** P(A|B) = P(A∩B)/P(B)
- [ ] **Law:** Chain Rule of probability — P(A∩B∩C) = P(A)·P(B|A)·P(C|A,B)
- [ ] **Theorem:** **Bayes' Theorem** — P(A|B) = \[P(B|A)·P(A)\] / P(B); Law of Total Probability
- [ ] **Problem-solving:** Classic disease-testing problem, spam classification by hand (connects directly to Naive Bayes from your course)

### 1.3 Random Variables

- [ ] **Definition:** Discrete vs. Continuous random variable
- [ ] **Types:** PMF (Probability Mass Function), PDF (Probability Density Function), CDF (Cumulative Distribution Function)
- [ ] **Formula:** E\[X\] (Expected value), Var(X), relationship Var(X) = E\[X²\] − (E\[X\])²

### 1.4 Discrete Distributions

- [ ] **Bernoulli distribution** — definition, formula, when used (single binary trial — binary classification foundation)
- [ ] **Binomial distribution** — formula, mean/variance, worked example
- [ ] **Poisson distribution** ⭐ — formula, when used (rare/count events — directly relevant to modeling rare security attack events)
- [ ] **Geometric distribution** — brief, definition + formula

### 1.5 Continuous Distributions

- [ ] **Uniform distribution** — definition, formula
- [ ] **Exponential distribution** — definition, formula, relation to Poisson (time between events)
- [ ] **Normal (Gaussian) distribution** ⭐⭐ — formula, properties, Empirical Rule (68-95-99.7)
- [ ] **Problem-solving:** Compute probabilities for each distribution type by hand, at least 2 problems each

### 1.6 Moments & Estimation

- [ ] **Definition:** Skewness, Kurtosis (shape of distribution)
- [ ] **Theorem:** **Maximum Likelihood Estimation (MLE)** — concept, how parameters are estimated from data, simple worked example (e.g., MLE for coin bias)

### 1.7 Information Theory (Critical for your thesis — anomaly detection)

- [ ] **Definition:** Entropy — H(X) = −Σ p(x)log p(x)
- [ ] **Formula:** Information Gain (used in Decision Trees — connect back to your course)
- [ ] **Formula:** Cross-Entropy Loss — derivation from likelihood, why used in classification
- [ ] **Formula:** **KL Divergence** ⭐ — D_KL(P||Q), why it's asymmetric, used in Autoencoder/VAE loss functions (directly relevant to your thesis's anomaly detection component)
- [ ] **Problem-solving:** Compute entropy and cross-entropy for a small example dataset by hand

---

## 📌 PILLAR 2 — STATISTICS

### 2.1 Descriptive Statistics

- [ ] **Definition:** Population vs. Sample, Parameter vs. Statistic
- [ ] **Types:** Qualitative vs. Quantitative data (Discrete/Continuous)
- [ ] **Formula:** Mean, Weighted Mean, Median, Mode
- [ ] **Formula:** Range, Percentile, Quartile, **IQR**, 1.5×IQR outlier rule
- [ ] **Formula:** Population Variance (σ²) vs. Sample Variance (s², Bessel's correction n−1) — know WHY n−1
- [ ] **Problem-solving:** Full descriptive stats computation on a small dataset by hand

### 2.2 Data Distribution Shape

- [ ] **Definition:** Histogram, Frequency distribution
- [ ] **Types:** Right-skew vs. Left-skew, Leptokurtic/Mesokurtic/Platykurtic
- [ ] **Formula:** Z-score — z = (x−μ)/σ
- [ ] **Problem-solving:** Z-score based probability problems (2-3 solved by hand)

### 2.3 Relationships Between Variables

- [ ] **Formula:** Covariance — Cov(X,Y)
- [ ] **Formula:** Correlation Coefficient (**Pearson**, and know what **Spearman** is used for — ranked/non-linear data)
- [ ] **Concept:** Correlation ≠ Causation — be able to explain why, with an example

### 2.4 Sampling & Central Limit Theorem

- [ ] **Definition:** Sampling distribution, Law of Large Numbers
- [ ] **Theorem:** **Central Limit Theorem (CLT)** ⭐ — statement, why it matters, n≥30 rule of thumb
- [ ] **Formula:** Standard Error — SE = σ/√n

### 2.5 Estimation

- [ ] **Definition:** Point estimate vs. Interval estimate
- [ ] **Formula:** Confidence Interval — CI = x̄ ± z·(σ/√n)
- [ ] **Problem-solving:** Build a 95% CI for a given sample by hand

### 2.6 Hypothesis Testing ⭐

- [ ] **Definition:** Null hypothesis (H₀) vs. Alternative hypothesis (H₁)
- [ ] **5-step process:** state hypotheses → set α → compute test statistic → find p-value → decide
- [ ] **Concept:** p-value — correct interpretation (NOT "probability H₀ is true")
- [ ] **Types:** **Type I Error (α, false positive)** vs. **Type II Error (β, false negative)** ⭐⭐ — directly maps to your thesis's detection model evaluation
- [ ] **Problem-solving:** Full Z-test worked example by hand, state conclusion correctly

### 2.7 Statistical Tests (know which test for which situation)

- [ ] **Z-test** — formula, when σ is known
- [ ] **T-test** — formula, when σ is unknown (uses s), independent vs. paired t-test, degrees of freedom
- [ ] **Chi-Square test** — formula, categorical variable independence testing
- [ ] **ANOVA** — concept, when comparing 3+ group means
- [ ] **Problem-solving:** One worked example each for T-test, Chi-square, and ANOVA

### 2.8 Regression Statistics

- [ ] **Formula:** Simple Linear Regression — ŷ = a + bx, formula for a and b
- [ ] **Formula:** Multiple Linear Regression — ŷ = Xw (matrix form — connects to Linear Algebra pillar)
- [ ] **Concept:** Multicollinearity — what it is, why it breaks models
- [ ] **Formula:** R² and Adjusted R² — meaning, difference, why adjusted R² matters as features increase
- [ ] **Concept:** Residuals — what "good" residual pattern looks like

### 2.9 Model Evaluation Statistics (directly for your thesis)

- [ ] **Formula:** Precision = TP/(TP+FP), Recall = TP/(TP+FN), F1-score = harmonic mean of Precision & Recall
- [ ] **Definition:** Confusion Matrix — TP, TN, FP, FN, and what each means in a security detection context
- [ ] **Concept:** ROC Curve, AUC — what they represent, how to read them
- [ ] **Problem-solving:** Build a confusion matrix from raw predictions and compute all metrics by hand

---

## 📌 PILLAR 3 — CALCULUS

### 3.1 Functions

- [ ] **Types:** Constant, Linear, Polynomial, Exponential, Logarithmic, Trigonometric functions
- [ ] **Concept:** Function composition — f(g(x)), directly relevant to neural network layers

### 3.2 Limits & Continuity

- [ ] **Definition:** Limit — lim(x→a) f(x) = L
- [ ] **Concept:** Left-hand vs right-hand limit, Continuity conditions
- [ ] **Law:** L'Hôpital's Rule (for 0/0 or ∞/∞ indeterminate forms)

### 3.3 Derivatives ⭐

- [ ] **Definition:** f'(x) = lim(h→0) \[f(x+h)−f(x)\]/h
- [ ] **Laws/Rules:** Power Rule, Sum/Difference Rule, Product Rule, Quotient Rule
- [ ] **Law:** **Chain Rule** ⭐⭐⭐ — the single most important rule for deep learning (backpropagation)
- [ ] **Formula:** Derivative of e^x, ln(x), sin/cos, and **Sigmoid derivative: σ'(z) = σ(z)(1−σ(z))** ⭐
- [ ] **Problem-solving:** Differentiate 8-10 functions of increasing complexity by hand, including chain rule chains

### 3.4 Partial Derivatives & Gradient

- [ ] **Definition:** Partial derivative — hold other variables constant
- [ ] **Formula:** Gradient vector ∇f — collection of all partial derivatives
- [ ] **Concept:** Direction of steepest ascent/descent

### 3.5 Optimization Basics (Calculus side)

- [ ] **Definition:** Critical point — where ∇f = 0
- [ ] **Law:** Second Derivative Test — f''>0 → min, f''\<0 → max
- [ ] **Concept:** Convex vs. Non-convex functions, local vs. global minimum
- [ ] **Problem-solving:** Find and classify critical points for 3-4 functions by hand

### 3.6 Gradient Descent (the calculus-to-ML bridge)

- [ ] **Formula:** w_new = w_old − α·∇L
- [ ] **Concept:** Why the minus sign, role of learning rate α
- [ ] **Problem-solving:** Manually run 3-4 iterations of gradient descent on a simple loss function

### 3.7 Integration (lighter — applied use only)

- [ ] **Definition:** Integration as reverse of differentiation
- [ ] **Formula:** Basic integral rules (power rule reversed, ∫e^x, ∫1/x)
- [ ] **Concept:** Definite integral = area under curve, connection to probability (P(a≤X≤b) = ∫f(x)dx)

---

## 📌 PILLAR 4 — LINEAR ALGEBRA (Matrix & Vector)

### 4.1 Vectors

- [ ] **Definition:** Vector as magnitude + direction, Row vs. Column vector
- [ ] **Formula:** Vector addition, scalar multiplication
- [ ] **Formula:** **Dot Product**, geometric meaning (a·b = |a||b|cosθ)
- [ ] **Formula:** Vector magnitude/norm — L1 norm, L2 norm ⭐ (used in regularization)
- [ ] **Formula:** Cosine Similarity — used in comparing vectors/embeddings (relevant for log/text-based security data)

### 4.2 Matrices

- [ ] **Definition:** Matrix as a grid, dimension notation (m×n)
- [ ] **Types:** Square, Diagonal, Identity, Symmetric, Triangular matrices
- [ ] **Formula:** Matrix addition, scalar multiplication
- [ ] **Formula:** **Matrix Multiplication** ⭐⭐⭐ — dimension rule (m×n)(n×p)=(m×p), this is literally what every NN layer does
- [ ] **Law:** AB ≠ BA (non-commutative) — must know this
- [ ] **Problem-solving:** Multiply 2-3 matrix pairs by hand

### 4.3 Transpose, Determinant, Inverse

- [ ] **Formula:** Transpose — (AB)ᵀ = BᵀAᵀ (order flips!)
- [ ] **Formula:** Determinant (2×2 and 3×3), geometric meaning
- [ ] **Formula:** Inverse matrix (2×2 formula), condition: det ≠ 0 for inverse to exist
- [ ] **Concept:** Singular vs. Non-singular matrix
- [ ] **Problem-solving:** Compute determinant and inverse for at least 3 matrices by hand (double check: det≠0 means NOT singular)

### 4.4 Linear Equations & Vector Spaces

- [ ] **Concept:** Solving Ax = b (Gaussian Elimination method)
- [ ] **Definition:** Span, Linear Independence, Basis, Dimension
- [ ] **Concept:** Why redundant/dependent features matter for ML (connects to PCA)

### 4.5 Eigenvalues & Eigenvectors ⭐⭐⭐

- [ ] **Definition:** Av = λv — vector whose direction doesn't change under transformation
- [ ] **Formula/Law:** Characteristic Equation — det(A−λI) = 0
- [ ] **Theorem:** Spectral theorem (concept-level — symmetric matrices have real eigenvalues, relevant since covariance matrices are always symmetric)
- [ ] **Problem-solving:** Find eigenvalues and eigenvectors for a 2×2 matrix fully by hand

### 4.6 Advanced — Norms, Projection, Rank, SVD, PCA

- [ ] **Formula:** L1 norm vs L2 norm — connection to Lasso/Ridge regularization
- [ ] **Definition:** Orthogonality (a·b = 0), Projection formula
- [ ] **Definition:** Rank of a matrix — true dimensionality
- [ ] **Theorem:** **SVD (Singular Value Decomposition)** — A = UΣVᵀ, concept-level understanding
- [ ] **Algorithm:** **PCA (Principal Component Analysis)** — full 5-step process, why eigenvectors of covariance matrix give principal components
- [ ] **Concept:** Tensor — generalization of scalar→vector→matrix→tensor (this is what PyTorch works with)

---

## 📌 PILLAR 5 — OPTIMIZATION (ML/DL Training Engine)

### 5.1 Objective/Loss/Cost Functions

- [ ] **Definition:** Objective vs. Loss (single sample) vs. Cost (batch average)
- [ ] **Formula:** MSE, MAE, Binary Cross-Entropy (BCE) — know all three

### 5.2 Convexity

- [ ] **Definition:** Convex function (mathematical definition + intuition)
- [ ] **Concept:** Local vs. Global minimum, Saddle point
- [ ] **Concept:** Why neural networks are non-convex but still trainable in practice

### 5.3 Gradient Descent Variants

- [ ] **Formula:** Standard Gradient Descent update rule
- [ ] **Types:** Batch GD vs. Stochastic GD (SGD) vs. Mini-batch GD — tradeoffs of each
- [ ] **Concept:** Learning rate — effect of too small/too large/too big (divergence)
- [ ] **Concept:** Learning rate schedules — step decay, exponential decay, cosine annealing, warmup

### 5.4 Advanced Optimizers ⭐

- [ ] **Formula:** **Momentum** — v_t = βv\_(t-1) + ∇L, why it smooths zigzag
- [ ] **Formula:** **AdaGrad** — per-parameter adaptive learning rate, why it "dies" over time
- [ ] **Formula:** **RMSProp** — exponential moving average fix to AdaGrad's problem
- [ ] **Formula:** **Adam** ⭐⭐⭐ — Momentum + RMSProp combined, bias correction, default hyperparameters (α=0.001, β₁=0.9, β₂=0.999)
- [ ] **Concept:** AdamW — why weight decay is separated from gradient update
- [ ] **Problem-solving:** Manually compute 2-3 update steps using Momentum and Adam formulas

### 5.5 Practical Training Debugging (applied skill, not pure math)

- [ ] **Checklist:** What to check when loss is NaN, loss isn't decreasing, loss oscillates, model overfits a single batch
- [ ] **Concept:** Gradient clipping, why feature scaling matters for optimizer behavior

---

## 🗓️ Suggested 1.5–2 Month Schedule

| Week | Focus |
| --- | --- |
| 1–2 | Pillar 1 — Probability (all sections, this is foundational for everything else) |
| 3–4 | Pillar 2 — Statistics |
| 5 | Pillar 3 — Calculus |
| 6 | Pillar 4 — Linear Algebra |
| 7 | Pillar 5 — Optimization |
| 8 | Review week — redo all practice problems cold (no notes), identify weak spots, revisit only those |

**Daily rhythm suggestion:** 1 topic (with its sub-bullets) per day using your AI-generated note + hand-solved practice problems. Don't move to the next topic until you can explain the current one out loud without looking at notes — that's the real test of understanding, not just reading it once.

---

## ⚠️ Quality control reminder

When generating notes with AI, always **verify formulas and worked answers yourself** — an error was already found in an earlier note (a determinant of −1 incorrectly labeled "singular," when only det = 0 means singular). AI-generated math content can contain small errors; hand-checking each worked example catches this.
