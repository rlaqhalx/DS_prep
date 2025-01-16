# 확률 분포 개념 정리 (Probability Distributions)
데이터가 어떻게 분포되어 있는지를 설명하는 수학적 모델 

**이산 확률 분포(Discrete)** VS **연속 확률 분포(Continuous)**

# 📌 1. Discrete Probability Distributions
Discrete distributions describe data that takes only integer values (0,1,2,3,...).

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


## 2) Binomial Distribution
Definition: The probability of getting x successes in n independent trials, where each trial has a probability p of success.

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


## 3) Geometric Distribution
Definition: The probability of getting the first success on the n-th trial.

Examples:
- Rolling a die until you get a 6.
- How many times a salesperson must call before making a sale.

📌 Probability Mass Function (PMF):

P(X = n) = (1 - p)^{n - 1} p

📌 Mean and Variance:

μ = 1/p,    σ² = (1 - p)/p²

✅ When to use it?

When waiting for the first success in repeated trials.(e.g., How many times will a customer see an ad before clicking it?)


## 4) Poisson Distribution
Definition: The probability of x events occurring in a fixed time period, given an average rate λ.

Examples:
- Number of calls a call center receives per hour.
- Number of website visits per minute.

📌 Probability Mass Function (PMF):

P(X = x) = (λ^x e^{-λ}) / x!

- λ: Average number of occurrences in a time period.

📌 Mean and Variance:

μ = λ,    σ² = λ

✅ When to use it?

Predicting the number of events happening in a fixed period.(e.g., How many customers will enter a store in an hour?)


# 📌 2. Continuous Probability Distributions
Continuous distributions describe data that can take any real value (including decimals).

## 1) Normal (Gaussian) Distribution
Definition: A symmetric, bell-shaped distribution centered around the mean. It appears everywhere in nature and data.

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

## 2) Exponential Distribution
Definition: Models the time between two consecutive events in a Poisson process.

Examples:
- Time between customer arrivals at an ATM.
- Time until a light bulb burns out.

📌 Probability Density Function (PDF):

f(x) = λ e^{-λx},    where x ≥ 0

📌 Mean and Variance:

μ = 1/λ,    σ² = 1/λ²

✅ When to use it?

When measuring time until the next event happens.(e.g., How long until the next earthquake occurs?)

<img width="599" alt="Screen Shot 2025-01-17 at 1 35 39 AM" src="https://github.com/user-attachments/assets/c7012c47-91d3-4141-b885-415dd7dd6e2f" />




