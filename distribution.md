# 확률 분포 개념 정리 (Probability Distributions)
데이터가 어떻게 분포되어 있는지를 설명하는 수학적 모델 

**이산 확률 분포(Discrete)** VS **연속 확률 분포(Continuous)**

# 📌 1. Discrete Probability Distributions
Discrete distributions describe data that takes only integer values (0,1,2,3,...).

이산 확률 분포는 정수(0,1,2,3...) 값만 가질 수 있는 확률 변수의 분포를 나타냅니다.

## 1) Bernoulli Distribution
Definition: A single trial where the outcome is either success (1) or failure (0).

Examples:
- Flipping a coin once (Heads or Tails).
- Checking if a product is defective (Defective/Not Defective).
- Whether a customer opens an email (Open/Not Open).

📌 Probability Mass Function (PMF):

P(X = x) = p^x (1 - p)^{1 - x}, where x ∈ {0,1}

- p: Probability of success
- 1 - p: Probability of failure

📌 Mean and Variance:

μ = p,    σ² = p(1 - p)

✅ When to use it?

Predicting success/failure in a single attempt.(e.g., Will a customer click an ad? Will a coin land on heads?)

한 번 시행에서 성공/실패를 예측할 때 (e.g., 광고 클릭 여부, 제품이 불량인지 정상인지)


## 2) Binomial Distribution
Definition: The probability of getting x successes in n independent trials, where each trial has a probability p of success. (베르누이 시행을 여러 번 수행한 경우)

Examples:
- The number of defective products in a batch of 10.
- A student answering 5 questions correctly out of 10.

📌 Probability Mass Function (PMF):

P(X = x) = (n choose x) p^x (1 - p)^{n - x}

- (n choose x): Number of ways to choose x successes from n trials.

📌 Mean and Variance:

μ = np,    σ² = np(1 - p)

✅ When to use it?

When repeating a Bernoulli trial multiple times and counting successes.(e.g., Out of 100 customers, how many will buy a product?)

여러 번의 시행에서 성공 횟수를 예측할 때 (e.g., 100명의 고객 중 30명이 제품을 구매할 확률)


## 3) Geometric Distribution
Definition: The probability of getting the first success on the n-th trial.

처음 성공이 나오는 시행 횟수를 모델링하는 분포

Examples:
- Rolling a die until you get a 6.
- How many times a salesperson must call before making a sale.

📌 Probability Mass Function (PMF):

P(X = n) = (1 - p)^{n - 1} p

📌 Mean and Variance:

μ = 1/p,    σ² = (1 - p)/p²

✅ When to use it?

When waiting for the first success in repeated trials.(e.g., How many times will a customer see an ad before clicking it?)

처음 성공이 나올 때까지의 시행 횟수를 예측할 때 (e.g., 고객이 처음으로 광고를 클릭할 때까지 몇 번 보여줘야 하는지)

## 4) Poisson Distribution
Definition: The probability of x events occurring in a fixed time period, given an average rate λ.

특정 시간 또는 공간 내에서 발생하는 사건의 개수를 예측하는 분포

Examples:
- Number of calls a call center receives per hour.
- Number of website visits per minute.

📌 Probability Mass Function (PMF):

P(X = x) = (λ^x e^{-λ}) / x!

- λ: Average number of occurrences in a time period.
- λ : 평균 발생 횟수 (단위 시간당 발생하는 평균 사건 수)

📌 Mean and Variance:

μ = λ,    σ² = λ

✅ When to use it?

Predicting the number of events happening in a fixed period.(e.g., How many customers will enter a store in an hour?)

일정 시간 동안 몇 번 사건이 발생하는지 예측할 때 (e.g., 웹사이트에서 1시간 동안 방문자 수)

# 📌 2. Continuous Probability Distributions
Continuous distributions describe data that can take any real value (including decimals).

연속 확률 분포는 실수 값(소수점 포함)으로 나타나는 확률 변수를 모델링합니다.

## 1) Normal (Gaussian) Distribution
Definition: A symmetric, bell-shaped distribution centered around the mean. It appears everywhere in nature and data.

데이터가 평균을 중심으로 대칭적인 형태로 분포하는 경우 사용 (가장 많이 쓰이는 분포)

Examples:
- Heights and weights of people.
- Test scores (e.g., SAT, IQ scores).
- Stock price fluctuations.

📌 Probability Density Function (PDF):

f(x) = (1 / (σ sqrt(2π))) * e^{-(x - μ)² / (2σ²)}

📌 Mean and Variance:

μ = mean,    σ² = variance

✅ When to use it?

Whenever data is symmetrically distributed around a mean.(e.g., Predicting student test scores, analyzing stock returns)

자연 현상, 경제 데이터, 머신러닝 모델에서 사용 (e.g., 주가 변동 예측, 시험 점수 분석)

## 2) Exponential Distribution
Definition: Models the time between two consecutive events in a Poisson process.

사건 간의 시간 간격을 모델링하는 분포

Examples:
- Time between customer arrivals at an ATM.
- Time until a light bulb burns out.

📌 Probability Density Function (PDF):

f(x) = λ e^{-λx},    where x ≥ 0

📌 Mean and Variance:

μ = 1/λ,    σ² = 1/λ²

✅ When to use it?

When measuring time until the next event happens.(e.g., How long until the next earthquake occurs?)

사건 사이의 시간을 예측할 때 (e.g., 고객이 다음으로 웹사이트를 방문할 때까지 걸리는 시간)


📌 면접 대비 핵심 포인트

✅ 각 분포의 특징과 언제 쓰이는지 기억하기

✅ 평균, 분산 공식 이해하기 (mean, variance, PMF/PDF)

✅ 실제 문제 적용 예제 연습하기

✅ 정규 분포는 거의 모든 곳에서 사용되므로 깊이 공부하기

✅ 베르누이 → 이항 → 포아송으로 이어지는 관계 이해하기  (e.g., Bernoulli → Binomial → Poisson)

🔗 관계 정리

Bernoulli → Binomial:

Bernoulli 시행을 여러 번 반복하면 Binomial 분포가 된다.

즉, Binomial 분포는 여러 개의 Bernoulli 분포의 합이다.

Binomial → Poisson:

Binomial 분포에서 시행 횟수  𝑛 이 매우 크고, 성공 확률 𝑝 이 매우 작을 때, Poisson 분포로 근사할 수 있다.

즉, 희귀한 사건이 다수의 시행에서 발생하는 경우 Poisson 분포로 모델링할 수 있다.

<img width="733" alt="Screen Shot 2025-01-17 at 1 49 42 AM" src="https://github.com/user-attachments/assets/ee5279a2-ced4-4552-ae7f-d2560f7e1c95" />


<img width="599" alt="Screen Shot 2025-01-17 at 1 35 39 AM" src="https://github.com/user-attachments/assets/c7012c47-91d3-4141-b885-415dd7dd6e2f" />




