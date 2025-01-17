# 📌 Model Evaluation

## 📌 Regression Metrics
Regression models are evaluated based on how well they predict continuous values. Below are key metrics:

회귀 모델은 연속적인 값(예: 집값, 온도, 매출)을 얼마나 정확하게 예측하는지 평가

### 1) Mean Squared Error (MSE)

Measures the average squared difference between actual and predicted values. 실제 값과 예측 값 간의 차이를 제곱하여 평균을 낸 값

Penalizes large errors more than small errors. 즉 오차가 클수록 더 큰 패널티를 부여

Formula: 

**MSE = (1/n) * Σ(yi - ŷi)²**

- yi: Actual value
- ŷi: Predicted value
- n: Number of data points

✅ Example:

If actual values are [3, 5, 7] and predicted values are [2.5, 5.5, 6]:

MSE = [(3 - 2.5)² + (5 - 5.5)² + (7 - 6)²] / 3 = 0.5

큰 오차에 더 민감 → 이상치(outlier)가 많다면 RMSE를 고려하는 것이 좋음

### 2) Sum of Squared Errors (SSE)

Measures the total squared differences between actual and predicted values.

모든 오차를 제곱하여 합한 값으로, 모델의 적합도를 평가


Formula:

**SSE = Σ(yi - ŷi)²**

✅ When to use it?

Useful for comparing models; a lower SSE indicates a better fit.

여러 모델을 비교할 때 사용

값이 작을수록 모델이 더 잘 맞음


### 3) Total Sum of Squares (SST)

Measures total variability in the response variable.

실제 값들이 평균 값에서 얼마나 벗어나 있는지를 측정하는 지표


Formula:

**SST = Σ(yi - ȳ)²**

- ȳ: Mean of actual values


SST는 모델 없이 평균만으로 예측할 때의 총 오차

SSE가 낮을수록 모델이 데이터를 더 잘 설명함

### 4) R² (R-Squared)

Measures the proportion of variance explained by the model.

Higher values (closer to 1) indicate a better fit.

Negative R² means the model performs worse than just predicting the mean.

모델이 데이터를 얼마나 잘 설명하는지를 나타내는 지표

1에 가까울수록 좋고, 0 또는 음수이면 모델이 의미 없음

Formula:

**R² = 1 - (SSE / SST)**

✅ Example:

If SSE = 10 and SST = 50, then:

R² = 1 - (10 / 50) = 0.8 (80% variability explained)


회귀 모델의 성능을 비교할 때 1에 가까울수록 모델이 더 정확함

하지만 변수가 많으면 조정된 R² 사용 필요

### 5) Adjusted R²

Adjusts R² for the number of predictors.

Prevents overfitting when adding irrelevant variables.

변수를 추가할 때 모델의 성능이 정말 좋아졌는지 확인하는 지표

불필요한 변수가 추가될 경우 R²이 높아지는 문제를 방지

Formula:

**Adjusted R² = 1 - (1 - R²) * (N-1) / (N-p-1)**

- N: Number of observations
- p: Number of predictors

✅ When to use it?

When comparing models with different numbers of features.

여러 개의 변수를 사용하는 회귀 모델 비교

변수가 많을 때 과적합(Overfitting)을 방지

## 📌 Classification Metrics

Classification models are evaluated based on how well they predict categorical labels.

분류 모델은 범주형(이진 또는 다중 클래스) 데이터를 얼마나 잘 예측하는지 평가


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

✅ 언제 사용?

FP를 줄이는 것이 중요한 경우 (예: 스팸 필터, 암 진단)


### 3) Recall (Sensitivity, True Positive Rate)

Measures how many actual positives were correctly identified.

Formula:

**Recall = TP / (TP + FN)**

✅ Example:

Recall = 10 / (10 + 5) = 0.67 (67%)

✅ 언제 사용?

FN을 줄이는 것이 중요한 경우 (예: 암 진단, 사기 탐지)

### 4) Specificity (True Negative Rate)

Measures how many actual negatives were correctly identified.

Formula:

**Specificity = TN / (TN + FP)**

✅ Example:

Specificity = 83 / (83 + 2) = 0.98 (98%)

### 5) F1-Score

Harmonic mean of precision and recall.

Useful when classes are imbalanced.

정밀도와 재현율의 조화 평균

불균형한 데이터셋에서 유용함

Formula:

**F1 = 2 * (Precision * Recall) / (Precision + Recall)**

✅ Example:

F1 = 2 * (0.83 * 0.67) / (0.83 + 0.67) = 0.74 (74%)

### 6) ROC Curve & AUC

모델의 전체적인 성능을 평가하는 그래프

AUC (면적)가 1에 가까울수록 더 좋은 모델

ROC Curve: Plots True Positive Rate (TPR) vs. False Positive Rate (FPR) for different thresholds.

AUC (Area Under Curve): Measures the ability to distinguish between positive and negative classes.

AUC = 1.0: Perfect model.

AUC = 0.5: No predictive power (random guessing).

✅ Example:

If a model has an AUC score of 0.85, it means it correctly ranks a randomly chosen positive case higher than a randomly chosen negative case 85% of the time.

✅ 언제 사용?

불균형 데이터셋에서 모델 비교

### 7) Precision-Recall Curve

Focuses on the correct prediction of the minority class.

More useful than ROC when data is imbalanced (e.g., fraud detection, rare disease prediction).

✅ Example:

If fraud detection has a 1% fraud rate, using Precision-Recall Curve is more informative than an ROC curve.


<img width="592" alt="Screen Shot 2025-01-17 at 3 17 35 AM" src="https://github.com/user-attachments/assets/94766191-693c-472b-8e77-7a9c9c995c36" />

✅ MSE, R² → 회귀 모델 평가

✅ 정밀도 (Precision) → FP 줄이는 데 중요 (스팸 필터)

✅ 재현율 (Recall) → FN 줄이는 데 중요 (암 진단)

✅ F1-스코어 → 정밀도 vs 재현율 균형 (사기 탐지)

✅ AUC → 전체적인 분류 성능 평가
