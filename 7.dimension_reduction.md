# Dimension Reduction 

High-dimensional data can suffer from the curse of dimensionality, which increases the risk of overfitting and reduces model performance. Dimension reduction techniques help by removing redundant features while preserving essential information.

# 📌 1. Principal Component Analysis (PCA)

PCA projects data onto orthogonal vectors (principal components) that maximize variance, effectively reducing the number of dimensions while preserving patterns in the data.

🔹 How PCA Works?

Standardize the data so that each feature has a mean of 0 and variance of 1.

Compute the covariance matrix to understand feature relationships.

Find eigenvalues and eigenvectors using Singular Value Decomposition (SVD) or eigendecomposition.

Rank principal components (PCs) by variance explained:

Proportion of Variance Explained = ```λᵢ / Σλ```

Higher-ranked PCs retain more variance.

Select the top k principal components that retain sufficient variance.

✅ Example:

Facial Recognition: PCA reduces image pixel dimensions while keeping distinguishing features.

Stock Market Analysis: Extracts dominant trends from stock price movements.

💡 Key Notes:

PCA assumes linear relationships between features.

Number of principal components ≤ number of features (p).

PCA explains variance in X, not necessarily in the target variable Y.

🔵 Sparse PCA

Sparse PCA limits the number of non-zero values in principal components, making it robust to noise and improving interpretability.

✅ Example:

Used in genomics to identify key genes affecting diseases.

# 📌 2. Linear Discriminant Analysis (LDA)

LDA is a supervised technique that maximizes separation between classes while minimizing within-class variance.

🔹 How LDA Works?

Compute the mean and variance of each independent variable for each class Cᵢ.

Calculate within-class (σ²_w) and between-class (σ²_b) variance.

Find the transformation matrix:

```W = (σ²_w)⁻¹ (σ²_b)```

which maximizes Fisher’s signal-to-noise ratio.

Rank discriminant components by their signal-to-noise ratio.

✅ Example:

Handwritten Digit Recognition: LDA improves digit classification from images.

Medical Diagnosis: Differentiates between healthy and diseased patients.

💡 Key Notes:

Maximum number of components = C - 1 (where C is the number of classes).

Assumes:

Independent variables follow a normal distribution.

Equal variance across classes (homoscedasticity).

Low multicollinearity.

# 📌 3. Factor Analysis

Factor Analysis represents data using latent factors rather than original variables.

🔹 How Factor Analysis Works?

Express data in the form:

```X = Lf + ϵ```

where X is the observed data, L represents factor loadings, f represents latent factors, and ϵ is the noise.

Estimate factor loadings to determine how much each variable contributes to a factor.

Use Scree Plot to determine the number of factors to retain.

✅ Example:

Psychological Testing: Identifies underlying personality traits from questionnaire responses.

Economic Analysis: Extracts key macroeconomic factors affecting market trends.

🔵 Scree Plot: Choosing the Right Number of Factors

Plots eigenvalues of factors or principal components.

Elbow Method: The optimal number of factors is where eigenvalues level off (forming an "elbow").

✅ Example:

Selecting the best number of principal components for dimensionality reduction in image processing.
