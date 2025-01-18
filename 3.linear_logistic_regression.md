# Linear & Logistic Regression

# 📌 1. Linear Regression (선형 회귀)

Linear regression models linear relationships between a continuous response variable (Y) and explanatory variables (X).

## Ordinary Least Squares (OLS)

The goal is to find the best-fit line:

회귀선(직선)을 찾기 위해 **오차(SSE, 잔차 제곱합)** 를 최소화하는 방법입니다.


ŷ = β̂₀ + βX̂ + ϵ


💡 To minimize the Sum of Squared Errors (SSE), we estimate β using the formula:

💡 "최적의 기울기(β)를 찾는 방법"


β̂ = (XᵀX)⁻¹XᵀY

📌 쉽게 이해하면?
우리는 데이터(X, Y)를 보고 **"가장 잘 맞는 직선"**을 찾고 싶은 것!
그래서 오차를 최소화하는 기울기(β)를 찾는 것이 핵심입니다.


✅ Example:

Predicting house prices based on square footage.

Estimating student grades based on study hours.


## Assumptions of Linear Regression

1. Linearity - The relationship between X and Y is linear.
   
   X와 Y의 관계가 선형이어야 함

   X가 증가하면 Y도 일정한 비율로 증가 or 감소해야 함

2. Independent Observations - No correlation between observations.

   데이터들이 서로 독립적이어야 함 (한 데이터가 다른 데이터에 영향을 주면 안 됨)

3. Homoscedasticity - Errors have constant variance.

   오차의 분포가 일정해야 함

   즉, X가 커져도 오차(ϵ)의 크기가 일정해야 함

4. Normality - Errors follow a normal distribution.

   오차(ϵ)는 정규 분포를 따라야 함

   쉽게 말해, 데이터가 특정 패턴 없이 랜덤해야 함

5. Low Multicollinearity - Predictors (X variables) should not be highly correlated.

   독립 변수들(X1, X2, X3...)이 서로 강하게 상관관계를 가지면 안 됨

   ex) 키(cm)와 키(m)는 사실상 같은 정보 → 모델 성능 저하

## Multicollinearity Check: Variance Inflation Factor - measures severity of the multicollinearity ##

💡 다중공선성 (Multicollinearity) 해결 방법?

✔ VIF(Variance Inflation Factor, 분산 팽창 계수) 확인!

Use Variance Inflation Factor (VIF): 

VIF = 1 / (1 - R²)

If VIF > 10, multicollinearity is an issue.


## Regularization 

Prevents overfitting by adding a penalty term λ to the cost function.

모델이 너무 복잡하면 오버피팅(Overfitting)이 발생할 수 있음.

그래서 규제(Regularization) 기법을 사용해 모델을 단순화!

### LASSO Regression (L1 Regularization)

λ Σ|β̂| (절대값 패널티 추가)

Shrinks some coefficients to zero (Feature Selection!). 

Useful for sparse models.

중요하지 않은 변수를 0으로 만들어서 Feature Selection 가능!

즉, 불필요한 변수 제거!

### Ridge Regression (L2 Regularization)

λ Σ(β̂)² (제곱 패널티 추가)

Shrinks coefficients towards zero, but does not eliminate them.

Reduces multicollinearity effects.

모든 변수의 계수를 작게 만듦 (0은 아님)

multicollinearity 해결에 효과적!

### Elastic Net (L1 + L2) LASSO + Ridge 결합

Combines LASSO & Ridge to balance feature selection and coefficient shrinkage.

Feature Selection + multicollinearity 해결을 동시에!

✅ Example:

LASSO: Choosing the most important factors affecting house prices.

Ridge: Handling correlated predictors like "height" and "weight" in BMI calculation.


📌 어떨 때 사용?

✔ LASSO → 중요 변수만 선택하고 싶을 때

✔ Ridge → 다중공선성이 있는 데이터를 다룰 때

✔ Elastic Net → 두 가지 문제를 동시에 해결하고 싶을 때


# 📌 2. Logistic Regression (로지스틱 회귀)

Used for binary classification problems (Yes/No, 0/1, Spam/Not Spam).

선형 회귀는 연속 값을 예측하지만, 로지스틱 회귀는 분류(Classification) 문제를 해결합니다.

✔ 이메일이 스팸인지 아닌지? (Spam/Not Spam, 0 or 1)

✔ 고객이 제품을 구매할지 아닐지? (Yes/No, 1 or 0)

### Sigmoid Function (시그모이드 함수)

Transforms predictions into probabilities:

P(Y = 1) = 1 / (1 + e^-(β₀+βX))

Output is between 0 and 1, representing probability.

A threshold (α) is set to classify results (e.g., α = 0.5 → Y=1 if P > 0.5, else Y=0).

출력값이 0과 1 사이의 확률로 변환됨

특정 기준값(α) 이상이면 1, 아니면 0으로 분류

✅ Example:

Predicting if a customer will buy a product (Yes/No).

Identifying if an email is spam or not.

### Assumptions of Logistic Regression

1. Linear relationship between X and log-odds of Y.

   선형 회귀처럼 X가 증가할 때 log(odds)가 일정하게 증가해야 함

   즉, X가 커지면 Y=1이 될 확률이 점진적으로 증가해야 함

2. Independent observations.

3. Low multicollinearity between predictors. (check VIF!)

### Odds & Log-Odds (승산비 & 로그 승산비)

Odds(Y=1) = P(Y=1) / (1 - P(Y=1))

If odds = 2:1 → There is a twice higher chance of Y=1 happening.

예: "합격 확률이 80%"라면 Odds = 0.8 / 0.2 = 4  즉, 합격할 가능성이 불합격보다 4배 높음

Coefficients affect the odds exponentially:

**✔ Log-Odds(로그 승산비):**

선형 회귀처럼 해석 가능

X가 1 증가할 때 → Odds가 e^β배 증가

One unit increase in X → Odds multiply by e^β

✅ Example:

If β = 0.7 for "years of experience", then one additional year increases the odds of getting a job offer by e^0.7 ≈ 2x.
β = 0.7이면 X가 1 증가할 때 Odds는 e^0.7 ≈ 2배 증가  즉, 경력이 1년 증가하면 취업 확률이 2배 증가! :((
