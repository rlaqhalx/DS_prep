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

### ✅ MSE (Mean Squared Error) vs. RMSE (Root Mean Squared Error)
MSE와 RMSE는 둘 다 모델의 오차를 측정하는데 사용되지만, 차이점은 오차 값을 해석하는 방식에 있습니다.

**MSE (평균 제곱 오차)**

오차(실제 값 - 예측 값)를 제곱한 후 평균을 낸 값

큰 오차(이상치)에 대해 패널티를 크게 부여

단점: 제곱을 했기 때문에 값이 커지고, 단위가 원래 데이터의 단위와 달라짐 (예: cm 단위의 데이터를 예측할 때 MSE는 cm² 단위가 됨)

📌 사용 예시: 모델을 비교할 때 값이 작을수록 좋은 모델을 선택할 수 있음

**RMSE (평균 제곱근 오차)**

MSE의 제곱근을 취한 값

단위가 원래 데이터와 동일하여 해석이 쉬움 (예: 원래 데이터가 cm이면 RMSE도 cm)

큰 오차에 민감하다는 점은 MSE와 동일함

📌 사용 예시: 모델의 성능을 직관적으로 평가하고 싶을 때 사용 (MSE보다 해석이 쉬움)

💡 언제 RMSE를 사용할까?

- 실제 값과 예측 값의 차이를 원래 단위로 보고 싶을 때
- 오차가 큰 데이터를 다룰 때 (이상치에 민감한 점은 MSE와 동일)

💡 언제 MSE를 사용할까?

- 모델을 비교할 때 (MSE 값이 낮을수록 좋은 모델)
- 단위를 신경 쓰지 않아도 될 때

📌 핵심 차이점:

✔️ MSE는 단위가 제곱이므로 해석이 어려움

✔️ RMSE는 원래 데이터 단위와 같아 해석이 쉬움

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


### ✅ SSE (Sum of Squared Errors) vs. SST (Total Sum of Squares)
SSE와 SST는 R²(설명력)을 계산할 때 중요한 개념입니다.

**SSE (잔차 제곱합, 오차 제곱합)**

실제 값과 예측 값의 차이를 제곱해서 합한 값

모델이 예측한 값이 실제 값과 얼마나 차이가 있는지를 나타냄

작을수록 좋은 모델 (예측이 실제 값에 가까움)

📌 사용 예시: 여러 모델을 비교할 때 SSE 값이 낮은 모델이 데이터를 더 잘 설명하는 모델

**SST (총 제곱합)**

데이터의 총 변동량을 나타냄

평균을 기준으로 데이터가 얼마나 퍼져 있는지 측정하는 지표

SST = Σ(yi - ȳ)²

(yi = 실제 값, ȳ = 실제 값의 평균)

💡 SST의 의미?

- 모델 없이 평균 값만으로 예측했을 때의 오차 크기
- SST가 크면 데이터가 평균에서 많이 벗어나 퍼져 있다는 뜻

📌 사용 예시: 데이터 자체의 변동성을 평가하고, 모델이 이 변동성을 얼마나 잘 설명하는지 비교할 때 사용


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

### ✅ R² (결정계수) vs. RMSE (Root Mean Squared Error)
R²과 RMSE는 모두 모델의 성능을 평가하는 지표이지만, 측정하는 방식이 다릅니다.

**R² (결정계수)**

모델이 데이터를 얼마나 잘 설명하는지를 나타내는 지표

- 값 범위: 0 ~ 1 (또는 음수 가능)
- R² = 1 - (SSE / SST)
  
- SSE가 작아질수록 R² 값이 1에 가까워짐 → 모델이 데이터를 잘 설명함
- SSE가 SST와 비슷하면 R² ≈ 0 (즉, 모델이 평균을 예측하는 것과 비슷한 수준)
- SSE가 SST보다 크면 R² < 0 (즉, 모델이 예측한 값이 평균보다 못함)
  
📌 사용 예시: 모델이 전체 데이터 변동성을 얼마나 잘 설명하는지 평가할 때


📌 핵심 차이점:

✔️ R²은 모델이 데이터를 얼마나 잘 설명하는지 (설명력)

✔️ RMSE는 모델의 예측값이 실제값과 얼마나 가까운지 (오차 크기)

### 5) Adjusted R²

Adjusts R² for the number of predictors.

Prevents overfitting when adding irrelevant variables.

변수를 추가할 때 모델의 성능이 정말 좋아졌는지 확인하는 지표

불필요한 변수가 추가될 경우 R²이 높아지는 문제를 방지

R²는 변수를 추가하면 무조건 증가하는 단점이 있음.

이를 해결하기 위해 Adjusted R²을 사용합니다

Formula:

**Adjusted R² = 1 - (1 - R²) * (N-1) / (N-p-1)**

- N: Number of observations
- p: Number of predictors

✅ When to use it?

When comparing models with different numbers of features.
여러 변수를 사용하는 회귀 모델을 비교할 때

✔️ 변수를 추가해도 모델이 실제로 좋아지는지 판단

✔️ 변수가 많을수록 과적합(overfitting) 방지

💡 언제 Adjusted R²를 사용할까?

- 변수가 많은 모델에서 필요 없는 변수를 걸러낼 때
- R²은 무조건 높아지지만, Adjusted R²는 진짜 성능 향상을 반영
  
<img width="735" alt="Screen Shot 2025-01-17 at 10 07 17 PM" src="https://github.com/user-attachments/assets/92f11f93-1cc5-4b08-a86e-32ebb8b52b29" />

### ✅ 어떤 지표를 사용해야 할까?

1. 모델을 비교할 때

- MSE, RMSE, SSE를 사용해 가장 낮은 값 선택
- R²이 높을수록 좋음 (하지만 Adjusted R² 고려)

2. 이상치(outlier)가 많다면?

- RMSE보다는 MSE를 사용 (큰 오차에 민감)
  
<img width="749" alt="Screen Shot 2025-01-17 at 10 14 39 PM" src="https://github.com/user-attachments/assets/4d77299f-ebad-4fea-a39f-733bbe36f812" />

3. 변수가 많을 때 과적합을 방지하려면?

- Adjusted R²를 확인하여 불필요한 변수 추가 방지



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


<img width="729" alt="Screen Shot 2025-01-17 at 10 20 05 PM" src="https://github.com/user-attachments/assets/ef7f86a8-53db-4d3d-9285-d5270260772a" />

✔️ "정밀"하게 찾아야 한다 → Precision (FP 줄이기)

✔️ "놓치면 안 된다" → Recall (FN 줄이기)

✔️ "정상적인 걸 잘 걸러야 한다" → Specificity (TN 중요)

✔️ "Precision과 Recall의 밸런스" → F1-score (균형 잡기)


### 6) ROC Curve & AUC

모델의 전체적인 성능을 평가하는 그래프

AUC (면적)가 1에 가까울수록 더 좋은 모델

ROC Curve: Plots True Positive Rate (TPR) vs. False Positive Rate (FPR) for different thresholds.

AUC (Area Under Curve): Measures the ability to distinguish between positive and negative classes.

- AUC = 1 → 완벽한 모델 (100% 정확)
- AUC = 0.5 → 랜덤 추측과 동일 (무의미한 모델)

✅ Example:

If a model has an AUC score of 0.85, it means it correctly ranks a randomly chosen positive case higher than a randomly chosen negative case 85% of the time.


### 7) Precision-Recall Curve

Focuses on the correct prediction of the minority class.

More useful than ROC when data is imbalanced (e.g., fraud detection, rare disease prediction).

✅ Example:

If fraud detection has a 1% fraud rate, using Precision-Recall Curve is more informative than an ROC curve.

<img width="726" alt="Screen Shot 2025-01-17 at 10 22 43 PM" src="https://github.com/user-attachments/assets/a9265aad-a8fd-450b-82d6-e4516d98344b" />


<img width="592" alt="Screen Shot 2025-01-17 at 3 17 35 AM" src="https://github.com/user-attachments/assets/94766191-693c-472b-8e77-7a9c9c995c36" />

✅ MSE, R² → 회귀 모델 평가

✅ 정밀도 (Precision) → FP 줄이는 데 중요 (스팸 필터)

✅ 재현율 (Recall) → FN 줄이는 데 중요 (암 진단)

✅ F1-스코어 → 정밀도 vs 재현율 균형 (사기 탐지)

✅ AUC → 전체적인 분류 성능 평가
