# 📌 Model Evaluation

## 📌 Regression Metrics
Regression models are evaluated based on how well they predict continuous values. Below are key metrics:

### 1) Mean Squared Error (MSE)

Measures the average squared difference between actual and predicted values.

Penalizes large errors more than small errors.

Formula: 

**MSE = (1/n) * Σ(yi - ŷi)²**

- yi: Actual value
- ŷi: Predicted value
- n: Number of data points

✅ Example:

If actual values are [3, 5, 7] and predicted values are [2.5, 5.5, 6]:

MSE = [(3 - 2.5)² + (5 - 5.5)² + (7 - 6)²] / 3 = 0.5

### 2) Sum of Squared Errors (SSE)

Measures the total squared differences between actual and predicted values.

Formula:

**SSE = Σ(yi - ŷi)²**

✅ When to use it?

Useful for comparing models; a lower SSE indicates a better fit.

### 3) Total Sum of Squares (SST)

Measures total variability in the response variable.

Formula:

**SST = Σ(yi - ȳ)²**

- ȳ: Mean of actual values

### 4) R² (R-Squared)

Measures the proportion of variance explained by the model.

Higher values (closer to 1) indicate a better fit.

Negative R² means the model performs worse than just predicting the mean.

Formula:

**R² = 1 - (SSE / SST)**

✅ Example:

If SSE = 10 and SST = 50, then:

R² = 1 - (10 / 50) = 0.8 (80% variability explained)

### 5) Adjusted R²

Adjusts R² for the number of predictors.

Prevents overfitting when adding irrelevant variables.

Formula:

**Adjusted R² = 1 - (1 - R²) * (N-1) / (N-p-1)**

- N: Number of observations
- p: Number of predictors

✅ When to use it?

When comparing models with different numbers of features.

## 📌 Classification Metrics

Classification models are evaluated based on how well they predict categorical labels.

### 1) Confusion Matrix

A table summarizing model performance:

<img width="598" alt="Screen Shot 2025-01-17 at 3 14 50 AM" src="https://github.com/user-attachments/assets/849e6f28-73f1-42f7-bc3b-4cbaa520d952" />

✅ Example:

If a spam detector predicts 10 spam emails correctly (TP), misses 5 spam emails (FN), mistakenly labels 2 non-spam as spam (FP), and correctly identifies 83 non-spam emails (TN):

<img width="594" alt="Screen Shot 2025-01-17 at 3 15 21 AM" src="https://github.com/user-attachments/assets/ed258824-d5b1-47ea-8a6a-ff616c87c5ea" />

### 2) Precision

Measures the proportion of correctly predicted positive instances.

Also known as Positive Predictive Value (PPV).

Formula:

**Precision = TP / (TP + FP)**

✅ Example:

Precision = 10 / (10 + 2) = 0.83 (83%)

### 3) Recall (Sensitivity, True Positive Rate)

Measures how many actual positives were correctly identified.

Formula:

**Recall = TP / (TP + FN)**

✅ Example:

Recall = 10 / (10 + 5) = 0.67 (67%)

### 4) Specificity (True Negative Rate)

Measures how many actual negatives were correctly identified.

Formula:

**Specificity = TN / (TN + FP)**

✅ Example:

Specificity = 83 / (83 + 2) = 0.98 (98%)

### 5) F1-Score

Harmonic mean of precision and recall.

Useful when classes are imbalanced.

Formula:

**F1 = 2 * (Precision * Recall) / (Precision + Recall)**

✅ Example:

F1 = 2 * (0.83 * 0.67) / (0.83 + 0.67) = 0.74 (74%)

### 6) ROC Curve & AUC

ROC Curve: Plots True Positive Rate (TPR) vs. False Positive Rate (FPR) for different thresholds.

AUC (Area Under Curve): Measures the ability to distinguish between positive and negative classes.

AUC = 1.0: Perfect model.

AUC = 0.5: No predictive power (random guessing).

✅ Example:

If a model has an AUC score of 0.85, it means it correctly ranks a randomly chosen positive case higher than a randomly chosen negative case 85% of the time.

### 7) Precision-Recall Curve

Focuses on the correct prediction of the minority class.

More useful than ROC when data is imbalanced (e.g., fraud detection, rare disease prediction).

✅ Example:

If fraud detection has a 1% fraud rate, using Precision-Recall Curve is more informative than an ROC curve.




<img width="592" alt="Screen Shot 2025-01-17 at 3 17 35 AM" src="https://github.com/user-attachments/assets/94766191-693c-472b-8e77-7a9c9c995c36" />

