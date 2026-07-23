# Phase 8: Statistics for Data Analytics

Welcome to **Phase 8** – the statistical foundation of data analytics! Throughout this curriculum, you have learned to collect, clean, visualise, and explore data. Now, you will learn the **statistical principles** that underpin data-driven decision-making.

Statistics is the science of collecting, analysing, interpreting, and presenting data. It provides the tools to:
- Summarise data meaningfully.
- Make inferences about populations from samples.
- Quantify uncertainty.
- Test hypotheses and make decisions.

Whether you are a data analyst, data scientist, or business professional, understanding statistics is essential for:
- Making data-driven decisions.
- Interpreting the results of your analyses.
- Communicating findings with confidence.
- Avoiding common pitfalls and misinterpretations.

In this phase, we will cover:
- **Mean, Median, Mode** – measures of central tendency.
- **Variance and Standard Deviation** – measures of spread.
- **Probability Basics** – the foundation of statistical inference.
- **Normal Distribution** – the most important distribution in statistics.
- **Sampling** – how to select and work with samples.
- **Confidence Intervals** – quantifying uncertainty.
- **Hypothesis Testing** – making decisions based on data.

Let's build your statistical toolkit!

---

## Lesson 8.1 – Mean, Median, Mode

### Concept Explanation

**Measures of central tendency** describe the "center" or typical value of a dataset.

**Mean (Average)**: The sum of all values divided by the number of values.
- Formula: μ = (Σx) / n (population), x̄ = (Σx) / n (sample)
- Sensitive to outliers.

**Median**: The middle value when data is sorted.
- If n is odd: the middle value.
- If n is even: the average of the two middle values.
- Robust to outliers.

**Mode**: The most frequently occurring value.
- A dataset can have one mode (unimodal), two modes (bimodal), or more.
- Used for categorical data and discrete numerical data.

**When to use which**:
- **Mean**: Symmetric distributions without outliers.
- **Median**: Skewed distributions or data with outliers.
- **Mode**: Categorical data or identifying the most common value.

---

### Importance and Real-World Use Cases

- **Why it matters**: Understanding central tendency is fundamental to describing any dataset. It helps in summarising data, comparing groups, and identifying trends.

- **Use cases**:
  - A **sales analyst** calculates the mean sales to understand average performance.
  - A **financial analyst** uses the median salary to understand typical compensation (less skewed by high earners).
  - A **retail analyst** finds the mode of product purchases to identify the most popular item.

---

### Step-by-Step Demonstration

```python
import numpy as np
import pandas as pd
from scipy import stats
import matplotlib.pyplot as plt
import seaborn as sns

# Sample data
data = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]

# 1. Mean
mean_value = np.mean(data)
print(f"Mean: {mean_value:.2f}")

# 2. Median
median_value = np.median(data)
print(f"Median: {median_value:.2f}")

# 3. Mode
mode_value = stats.mode(data)
print(f"Mode: {mode_value.mode[0]} (appears {mode_value.count[0]} times)")

# 4. Impact of outliers
data_with_outlier = [10, 20, 30, 40, 50, 60, 70, 80, 90, 1000]

mean_outlier = np.mean(data_with_outlier)
median_outlier = np.median(data_with_outlier)

print(f"\nWith outlier:")
print(f"  Mean: {mean_outlier:.2f}")
print(f"  Median: {median_outlier:.2f}")
print(f"  The mean is heavily influenced by the outlier, while the median is not.")

# 5. Creating a DataFrame
df = pd.DataFrame({
    'values': data_with_outlier
})

print("\nSummary statistics:")
print(df.describe())

# 6. Bimodal data
bimodal_data = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4, 5, 5, 5, 6, 6, 7, 7, 8, 8, 9, 9, 9, 9, 10, 10]
mode_bimodal = stats.mode(bimodal_data)
print(f"\nBimodal data mode: {mode_bimodal.mode[0]} (appears {mode_bimodal.count[0]} times)")
print(f"Note: There might be multiple modes in this dataset.")

# 7. Visualising central tendency
fig, axes = plt.subplots(1, 2, figsize=(12, 5))

# Normal distribution
normal_data = np.random.normal(50, 10, 1000)
sns.histplot(normal_data, kde=True, ax=axes[0])
axes[0].axvline(np.mean(normal_data), color='red', linestyle='--', label='Mean')
axes[0].axvline(np.median(normal_data), color='green', linestyle='--', label='Median')
axes[0].set_title('Normal Distribution')
axes[0].legend()

# Skewed distribution
skewed_data = np.random.exponential(20, 1000)
sns.histplot(skewed_data, kde=True, ax=axes[1])
axes[1].axvline(np.mean(skewed_data), color='red', linestyle='--', label='Mean')
axes[1].axvline(np.median(skewed_data), color='green', linestyle='--', label='Median')
axes[1].set_title('Skewed Distribution')
axes[1].legend()

plt.tight_layout()
plt.show()

# 8. Mean, median, mode comparison
print("\n" + "=" * 60)
print("MEAN, MEDIAN, MODE COMPARISON")
print("=" * 60)
print("Distribution Type | Mean vs Median")
print("-" * 40)
print("Symmetric         | Mean ≈ Median")
print("Right-skewed      | Mean > Median")
print("Left-skewed       | Mean < Median")
```

**Real-World Example: Analysing Customer Spend**:

```python
# Simulate customer spend data
np.random.seed(42)
customer_spend = np.random.gamma(2, 100, 500)  # Right-skewed distribution

mean_spend = np.mean(customer_spend)
median_spend = np.median(customer_spend)
mode_spend = stats.mode(np.round(customer_spend, 0))

print("\n" + "=" * 60)
print("CUSTOMER SPEND ANALYSIS")
print("=" * 60)
print(f"Mean spend: ${mean_spend:.2f}")
print(f"Median spend: ${median_spend:.2f}")
print(f"Mode spend: ${mode_spend.mode[0]:.0f}")

print(f"\nInterpretation:")
print(f"The mean is higher than the median (${mean_spend:.2f} > ${median_spend:.2f}),")
print(f"indicating that a few high-spending customers are pulling the average up.")
print(f"The median gives a better picture of typical customer spend.")
```

---

### Practical Examples

- **Example 1**: A company wants to know the average salary of its employees. The mean is $75,000, but the median is $65,000, indicating skewness due to a few high earners.
- **Example 2**: A retail store identifies the mode of customer purchases to determine which product to promote.
- **Example 3**: A real estate analyst calculates the median house price to understand the typical market.

---

### Hands-on Coding Exercises

**Exercise 8.1** – Calculate mean, median, mode:
```python
# 1. Create a list of numbers
# 2. Calculate the mean, median, and mode
# 3. Add an outlier and recalculate
# 4. Compare the results
# 5. Create a histogram with mean and median lines
```

**Exercise 8.2** – Salary analysis:
```python
# 1. Create a dataset of salaries (include a range of values)
# 2. Calculate mean, median, and mode
# 3. Determine which measure best represents typical salary
# 4. Justify your answer
```

---

### Mini Quiz

1. What is the mean of [10, 20, 30, 40, 50]?
2. What is the median of [10, 20, 30, 40, 50]?
3. What is the mode of [1, 2, 2, 3, 3, 3, 4]?
4. Which measure is most affected by outliers?
5. When would you use median instead of mean?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using mean for skewed data | Use median for skewed distributions |
| Reporting mean without considering outliers | Check for outliers before using mean |
| Not explaining which measure was used | Always specify the measure of central tendency |
| Ignoring the mode for categorical data | Use mode for categorical variables |

---

### Interview Questions

1. **What is the difference between mean, median, and mode?**  
   *Answer*: Mean is the average, median is the middle value, and mode is the most frequent value. Mean is sensitive to outliers, median is robust.

2. **When would you use median instead of mean?**  
   *Answer*: When the data is skewed or has outliers, the median provides a better measure of central tendency.

3. **What is a bimodal distribution?**  
   *Answer*: A distribution with two modes (two peaks), indicating two different groups within the data.

---

### Assignment and Mini Project

**Assignment 8.1** – Central tendency analysis:
```python
# 1. Load a dataset (e.g., 'tips' or any dataset with numeric columns)
# 2. Calculate mean, median, and mode for numeric columns
# 3. Create histograms with mean and median lines
# 4. Interpret which measure best describes each column
# 5. Write a summary report
```

**Mini Project** – Salary Analysis Tool:
Create a program that:
1. Generates a dataset of salaries (realistic range with some outliers).
2. Calculates and displays mean, median, and mode.
3. Creates visualisations (histogram with mean/median lines).
4. Determines which measure best represents typical salary.
5. Provides an interpretation and recommendation.

---

### Summary and Revision Notes

- Mean: average, sensitive to outliers.
- Median: middle value, robust to outliers.
- Mode: most frequent value, used for categorical data.
- Choose based on distribution shape and outliers.

---

## Lesson 8.2 – Variance and Standard Deviation

### Concept Explanation

**Measures of spread** describe how spread out or variable the data is.

**Variance (σ² or s²)**: The average of squared deviations from the mean.
- Population variance: σ² = Σ(x - μ)² / N
- Sample variance: s² = Σ(x - x̄)² / (n - 1)

**Standard Deviation (σ or s)**: The square root of variance.
- Population standard deviation: σ = √σ²
- Sample standard deviation: s = √s²

**Why use standard deviation?**
- Same units as the original data (interpretable).
- Used in many statistical tests and methods.
- The "68-95-99.7" rule for normal distributions.

**Interpretation**:
- Small SD: Data points are close to the mean.
- Large SD: Data points are spread out.

---

### Importance and Real-World Use Cases

- **Why it matters**: Central tendency alone is not enough. Two datasets can have the same mean but very different spreads. Understanding variability is essential for:
  - Assessing risk.
  - Comparing groups.
  - Understanding the reliability of estimates.

- **Use cases**:
  - A **financial analyst** calculates the standard deviation of stock returns to measure risk.
  - A **quality analyst** uses variance to measure product consistency.
  - A **data analyst** compares standard deviations to understand variability in sales.

---

### Step-by-Step Demonstration

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Sample data
data = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]

# 1. Calculate variance and standard deviation
mean_value = np.mean(data)
variance_pop = np.var(data)  # Population variance
variance_sample = np.var(data, ddof=1)  # Sample variance
std_pop = np.std(data)  # Population standard deviation
std_sample = np.std(data, ddof=1)  # Sample standard deviation

print(f"Mean: {mean_value:.2f}")
print(f"Population Variance: {variance_pop:.2f}")
print(f"Sample Variance: {variance_sample:.2f}")
print(f"Population Std Dev: {std_pop:.2f}")
print(f"Sample Std Dev: {std_sample:.2f}")

# 2. Interpreting standard deviation
print("\n" + "=" * 60)
print("INTERPRETING STANDARD DEVIATION")
print("=" * 60)
print(f"The data points are, on average, {std_pop:.2f} units away from the mean.")

# 3. Comparing two datasets with the same mean but different SD
data_1 = [45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55]
data_2 = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]

print(f"\nDataset 1 - Mean: {np.mean(data_1):.2f}, Std: {np.std(data_1):.2f}")
print(f"Dataset 2 - Mean: {np.mean(data_2):.2f}, Std: {np.std(data_2):.2f}")
print("Both have the same mean, but Dataset 1 has much lower variability.")

# 4. Visualising spread
fig, axes = plt.subplots(1, 2, figsize=(12, 5))

# Dataset 1 (low variability)
sns.histplot(data_1, kde=True, ax=axes[0])
axes[0].axvline(np.mean(data_1), color='red', linestyle='--', label=f'Mean: {np.mean(data_1):.1f}')
axes[0].axvline(np.mean(data_1) + np.std(data_1), color='green', linestyle='--', label=f'+1 SD: {np.mean(data_1) + np.std(data_1):.1f}')
axes[0].axvline(np.mean(data_1) - np.std(data_1), color='green', linestyle='--', label=f'-1 SD: {np.mean(data_1) - np.std(data_1):.1f}')
axes[0].set_title('Low Variability (SD = 3.0)')
axes[0].legend()

# Dataset 2 (high variability)
sns.histplot(data_2, kde=True, ax=axes[1])
axes[1].axvline(np.mean(data_2), color='red', linestyle='--', label=f'Mean: {np.mean(data_2):.1f}')
axes[1].axvline(np.mean(data_2) + np.std(data_2), color='green', linestyle='--', label=f'+1 SD: {np.mean(data_2) + np.std(data_2):.1f}')
axes[1].axvline(np.mean(data_2) - np.std(data_2), color='green', linestyle='--', label=f'-1 SD: {np.mean(data_2) - np.std(data_2):.1f}')
axes[1].set_title('High Variability (SD = 28.7)')
axes[1].legend()

plt.tight_layout()
plt.show()

# 5. Coefficient of Variation (CV)
cv1 = (np.std(data_1) / np.mean(data_1)) * 100
cv2 = (np.std(data_2) / np.mean(data_2)) * 100

print("\n" + "=" * 60)
print("COEFFICIENT OF VARIATION (CV)")
print("=" * 60)
print(f"Dataset 1 CV: {cv1:.1f}%")
print(f"Dataset 2 CV: {cv2:.1f}%")
print("CV is useful for comparing variability across datasets with different units.")

# 6. Real-world example: Stock returns
np.random.seed(42)
stock_a = np.random.normal(0.001, 0.02, 100)  # Mean 0.1%, SD 2%
stock_b = np.random.normal(0.001, 0.04, 100)  # Mean 0.1%, SD 4%

print("\n" + "=" * 60)
print("STOCK RETURN ANALYSIS")
print("=" * 60)
print(f"Stock A - Mean: {np.mean(stock_a)*100:.2f}%, Std: {np.std(stock_a)*100:.2f}%")
print(f"Stock B - Mean: {np.mean(stock_b)*100:.2f}%, Std: {np.std(stock_b)*100:.2f}%")
print("Stock B has the same average return but is twice as volatile (higher risk).")
```

**Real-World Example: Quality Control**:

```python
# Simulate product weights from two production lines
np.random.seed(42)
line_a = np.random.normal(500, 5, 100)  # Mean 500g, SD 5g
line_b = np.random.normal(500, 15, 100)  # Mean 500g, SD 15g

print("\n" + "=" * 60)
print("QUALITY CONTROL ANALYSIS")
print("=" * 60)
print(f"Line A - Mean: {np.mean(line_a):.2f}g, Std: {np.std(line_a):.2f}g")
print(f"Line B - Mean: {np.mean(line_b):.2f}g, Std: {np.std(line_b):.2f}g")
print("Both lines produce the same average weight.")
print("Line A is more consistent (lower standard deviation), indicating better quality control.")
```

---

### Practical Examples

- **Example 1**: A financial analyst calculates the standard deviation of monthly returns to measure investment risk.
- **Example 2**: A quality analyst measures the standard deviation of product dimensions to ensure consistency.
- **Example 3**: A teacher calculates the variance of test scores to understand student performance spread.

---

### Hands-on Coding Exercises

**Exercise 8.3** – Calculate variance and standard deviation:
```python
# 1. Create a list of numbers
# 2. Calculate variance (population and sample)
# 3. Calculate standard deviation (population and sample)
# 4. Interpret the standard deviation
# 5. Create a visualisation showing the spread
```

**Exercise 8.4** – Comparing variability:
```python
# 1. Create two datasets with the same mean but different standard deviations
# 2. Calculate and compare their standard deviations
# 3. Create histograms showing the difference
# 4. Interpret the results
```

---

### Mini Quiz

1. What is the difference between variance and standard deviation?
2. What is the difference between population and sample variance?
3. What does a small standard deviation indicate?
4. What is the coefficient of variation?
5. Why is standard deviation more commonly used than variance?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using population formulas on samples | Use `ddof=1` for sample variance/standard deviation |
| Interpreting standard deviation without context | Always relate to the mean and data range |
| Not checking for outliers before interpreting SD | Outliers inflate standard deviation |
| Using variance when standard deviation is more interpretable | Use standard deviation for interpretation |

---

### Interview Questions

1. **What is the difference between variance and standard deviation?**  
   *Answer*: Variance is the average of squared deviations from the mean. Standard deviation is the square root of variance and is in the same units as the original data.

2. **What does a small standard deviation indicate?**  
   *Answer*: It indicates that data points are close to the mean, showing low variability or consistency.

3. **Why do we divide by n-1 for sample variance?**  
   *Answer*: To provide an unbiased estimate of the population variance (Bessel's correction).

---

### Assignment and Mini Project

**Assignment 8.2** – Variance analysis:
```python
# 1. Load a dataset (e.g., 'tips' or any dataset with numeric columns)
# 2. Calculate variance and standard deviation for numeric columns
# 3. Interpret the standard deviation for each column
# 4. Compare variability across columns
# 5. Create visualisations showing the spread
# 6. Write a summary report
```

**Mini Project** – Risk Analysis Tool:
Create a program that:
1. Generates two datasets representing returns of two stocks.
2. Calculates mean, variance, and standard deviation for both.
3. Calculates the coefficient of variation for both.
4. Creates histograms showing the distributions.
5. Provides a risk assessment and recommendation.

---

### Summary and Revision Notes

- Variance: average squared deviation from the mean.
- Standard deviation: square root of variance (same units as data).
- Population: divide by N, Sample: divide by n-1.
- Small SD = low variability, Large SD = high variability.
- CV = (SD / Mean) × 100 for comparing variability.

---

## Lesson 8.3 – Probability Basics

### Concept Explanation

**Probability** is the measure of the likelihood that an event will occur. It ranges from 0 (impossible) to 1 (certain).

**Key concepts**:

**1. Sample Space**: All possible outcomes.
- Example: For a coin toss, {Heads, Tails}.

**2. Event**: A subset of the sample space.
- Example: Getting Heads.

**3. Probability of an Event**: P(A) = number of favourable outcomes / total outcomes.

**4. Complement**: P(not A) = 1 - P(A).

**5. Addition Rule**: P(A ∪ B) = P(A) + P(B) - P(A ∩ B).
- For mutually exclusive events: P(A ∪ B) = P(A) + P(B).

**6. Multiplication Rule**: P(A ∩ B) = P(A) × P(B | A).
- For independent events: P(A ∩ B) = P(A) × P(B).

**7. Conditional Probability**: P(A | B) = P(A ∩ B) / P(B).

---

### Importance and Real-World Use Cases

- **Why it matters**: Probability is the foundation of statistical inference. It allows us to quantify uncertainty, make predictions, and evaluate risk.

- **Use cases**:
  - A **financial analyst** calculates the probability of a stock price increase.
  - A **quality analyst** uses probability to assess defect rates.
  - A **marketing analyst** predicts customer churn probabilities.

---

### Step-by-Step Demonstration

```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from itertools import product

# 1. Coin toss probability
print("=" * 60)
print("PROBABILITY BASICS")
print("=" * 60)

# Single coin toss
print("Coin toss:")
print(f"  P(Heads) = 1/2 = {1/2:.2f}")
print(f"  P(Tails) = 1/2 = {1/2:.2f}")

# Two coin tosses
outcomes = list(product(['H', 'T'], repeat=2))
print(f"\nTwo coin toss outcomes: {outcomes}")
prob_two_heads = sum(1 for o in outcomes if o == ('H', 'H')) / len(outcomes)
print(f"  P(two heads) = {prob_two_heads:.2f}")

# 2. Dice roll probability
print("\n" + "=" * 60)
print("DICE PROBABILITY")
print("=" * 60)
# Single dice
print("Single die roll:")
for i in range(1, 7):
    print(f"  P({i}) = 1/6 = {1/6:.2f}")

# Sum of two dice
dice_outcomes = list(product(range(1, 7), range(1, 7)))
sum_counts = {}
for d1, d2 in dice_outcomes:
    total = d1 + d2
    sum_counts[total] = sum_counts.get(total, 0) + 1

print("\nProbability of sums with two dice:")
for total in range(2, 13):
    prob = sum_counts[total] / len(dice_outcomes)
    print(f"  P(sum = {total}) = {sum_counts[total]}/{len(dice_outcomes)} = {prob:.2f}")

# 3. Conditional probability
print("\n" + "=" * 60)
print("CONDITIONAL PROBABILITY")
print("=" * 60)

# Simulated data: 1000 customers, 400 bought product A, 300 bought product B, 150 bought both
total_customers = 1000
bought_A = 400
bought_B = 300
bought_both = 150

# P(A)
p_A = bought_A / total_customers
print(f"P(Bought A) = {p_A:.2f}")

# P(B)
p_B = bought_B / total_customers
print(f"P(Bought B) = {p_B:.2f}")

# P(A and B)
p_A_and_B = bought_both / total_customers
print(f"P(A and B) = {p_A_and_B:.2f}")

# P(A | B) = P(A and B) / P(B)
p_A_given_B = p_A_and_B / p_B
print(f"P(A | B) = {p_A_given_B:.2f} (probability of buying A given they bought B)")

# 4. Independent events
print("\n" + "=" * 60)
print("INDEPENDENT EVENTS")
print("=" * 60)
# Coin toss and die roll are independent
p_heads_and_6 = (1/2) * (1/6)
print(f"P(Heads and rolling a 6) = 1/2 × 1/6 = {p_heads_and_6:.3f}")

# 5. Monte Carlo simulation
print("\n" + "=" * 60)
print("MONTE CARLO SIMULATION")
print("=" * 60)

def simulate_coin_tosses(n, target_heads):
    """Simulate n coin tosses and count the probability of target_heads."""
    trials = 10000
    success = 0
    for _ in range(trials):
        tosses = np.random.choice(['H', 'T'], n)
        if sum(1 for t in tosses if t == 'H') >= target_heads:
            success += 1
    return success / trials

n = 10
target = 7
prob = simulate_coin_tosses(n, target)
print(f"Probability of getting at least {target} heads in {n} tosses: {prob:.4f}")
print(f"Theoretical probability: approximately {1 - sum(stats.binom.pmf(i, n, 0.5) for i in range(target)):.4f}")
```

**Visualising Probability**:

```python
# Visualising the sum of two dice
sums = list(sum_counts.keys())
probs = [sum_counts[s] / len(dice_outcomes) for s in sums]

plt.figure(figsize=(10, 6))
plt.bar(sums, probs, color='skyblue', edgecolor='black')
plt.title('Probability Distribution of Sum of Two Dice')
plt.xlabel('Sum')
plt.ylabel('Probability')
plt.xticks(sums)
plt.grid(axis='y', alpha=0.3)
plt.show()

# Coin toss probability (binomial distribution)
from scipy import stats

n = 10
p = 0.5
x = np.arange(0, n+1)
probs = stats.binom.pmf(x, n, p)

plt.figure(figsize=(10, 6))
plt.bar(x, probs, color='lightgreen', edgecolor='black')
plt.title(f'Binomial Distribution (n={n}, p={p})')
plt.xlabel('Number of Heads')
plt.ylabel('Probability')
plt.xticks(x)
plt.grid(axis='y', alpha=0.3)
plt.show()
```

---

### Practical Examples

- **Example 1**: A quality analyst calculates the probability of a defective product.
- **Example 2**: A financial analyst calculates the probability of a stock price exceeding a certain level.
- **Example 3**: A marketing analyst calculates the probability of a customer making a purchase given that they clicked on an ad.

---

### Hands-on Coding Exercises

**Exercise 8.5** – Probability calculations:
```python
# 1. Calculate the probability of rolling a sum of 7 with two dice
# 2. Calculate the probability of drawing a red card from a deck
# 3. Calculate the conditional probability of rain given cloudy weather
# 4. Simulate the probability using Monte Carlo
```

**Exercise 8.6** – Monte Carlo simulation:
```python
# 1. Simulate 1000 coin tosses and calculate the proportion of heads
# 2. Simulate 1000 rolls of two dice and calculate the proportion of sums = 7
# 3. Compare the simulated probabilities with theoretical values
```

---

### Mini Quiz

1. What is the probability of rolling a 6 on a fair die?
2. What is the probability of getting heads on two consecutive coin tosses?
3. What is the difference between independent and dependent events?
4. What is conditional probability?
5. What is the complement of rolling a number less than 3?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Confusing independent and mutually exclusive events | Understand the difference |
| Not using the correct sample space | Clearly define the sample space |
| Assuming events are independent when they're not | Test for independence |
| Overestimating small probabilities | Use proper calculations |

---

### Interview Questions

1. **What is the difference between independent and mutually exclusive events?**  
   *Answer*: Independent events don't affect each other's probabilities. Mutually exclusive events cannot occur simultaneously.

2. **What is conditional probability and how is it used?**  
   *Answer*: Conditional probability is the probability of an event given that another event has occurred. It is used in many real-world applications, such as medical diagnosis and risk assessment.

3. **What is the law of total probability?**  
   *Answer*: It states that the total probability of an event is the sum of its conditional probabilities across all mutually exclusive scenarios.

---

### Assignment and Mini Project

**Assignment 8.3** – Probability analysis:
```python
# 1. Simulate rolling a die 1000 times
# 2. Calculate the probability of each outcome
# 3. Compare with theoretical probabilities
# 4. Calculate the probability of rolling a number greater than 4
# 5. Create a visualisation of the results
```

**Mini Project** – Probability Simulator:
Create a program that:
1. Simulates various probability experiments:
   - Coin tosses.
   - Dice rolls.
   - Drawing cards.
2. Calculates theoretical and simulated probabilities.
3. Visualises the distributions.
4. Allows the user to specify the number of trials.
5. Compares simulated and theoretical results.

---

### Summary and Revision Notes

- Probability measures the likelihood of an event (0 to 1).
- Sample space: all possible outcomes.
- P(A) = favourable outcomes / total outcomes.
- Addition rule for mutually exclusive events.
- Multiplication rule for independent events.
- Conditional probability: P(A|B) = P(A∩B)/P(B).

---

## Lesson 8.4 – Normal Distribution

### Concept Explanation

The **Normal Distribution** is the most important continuous probability distribution in statistics. It is also called the Gaussian distribution or bell curve.

**Key properties**:
- Symmetric around the mean.
- Mean = Median = Mode.
- Bell-shaped curve.
- Defined by two parameters: **mean (μ)** and **standard deviation (σ)**.

**The 68-95-99.7 Rule (Empirical Rule)**:
- 68% of data falls within 1 standard deviation of the mean.
- 95% of data falls within 2 standard deviations.
- 99.7% of data falls within 3 standard deviations.

**Standard Normal Distribution**:
- Mean = 0, Standard Deviation = 1.
- z-score: z = (x - μ) / σ
- Used for calculating probabilities.

---

### Importance and Real-World Use Cases

- **Why it matters**: The normal distribution appears in many natural and social phenomena. It is the foundation of many statistical methods and tests.

- **Use cases**:
  - A **quality analyst** uses the normal distribution to model product dimensions.
  - A **financial analyst** assumes normal distribution for returns.
  - A **psychologist** uses normal distribution for test scores.

---

### Step-by-Step Demonstration

```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats

# 1. Generating normal distributions
print("=" * 60)
print("NORMAL DISTRIBUTION")
print("=" * 60)

# Different means and standard deviations
x = np.linspace(-10, 10, 1000)
dist1 = stats.norm.pdf(x, 0, 1)     # N(0, 1)
dist2 = stats.norm.pdf(x, 2, 1)     # N(2, 1)
dist3 = stats.norm.pdf(x, 0, 2)     # N(0, 2)

plt.figure(figsize=(10, 6))
plt.plot(x, dist1, label='N(0, 1)', linewidth=2)
plt.plot(x, dist2, label='N(2, 1)', linewidth=2, linestyle='--')
plt.plot(x, dist3, label='N(0, 2)', linewidth=2, linestyle='-.')
plt.title('Normal Distributions with Different Parameters')
plt.xlabel('x')
plt.ylabel('Probability Density')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()

# 2. 68-95-99.7 Rule
print("\n" + "=" * 60)
print("68-95-99.7 RULE (EMPIRICAL RULE)")
print("=" * 60)

mu, sigma = 0, 1
x = np.linspace(mu - 4*sigma, mu + 4*sigma, 1000)
y = stats.norm.pdf(x, mu, sigma)

plt.figure(figsize=(12, 6))
plt.plot(x, y, color='blue', linewidth=2)
plt.fill_between(x, y, where=(x >= mu - sigma) & (x <= mu + sigma), color='lightblue', alpha=0.5, label='68%')
plt.fill_between(x, y, where=(x >= mu - 2*sigma) & (x <= mu + 2*sigma), color='green', alpha=0.2, label='95%')
plt.fill_between(x, y, where=(x >= mu - 3*sigma) & (x <= mu + 3*sigma), color='yellow', alpha=0.1, label='99.7%')
plt.axvline(mu, color='red', linestyle='--', label=f'Mean = {mu}')
plt.title('68-95-99.7 Rule (Empirical Rule)')
plt.xlabel('x')
plt.ylabel('Probability Density')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()

# 3. Calculating probabilities
print("\n" + "=" * 60)
print("CALCULATING PROBABILITIES")
print("=" * 60)

mu, sigma = 0, 1
# P(-1 < X < 1)
prob_1 = stats.norm.cdf(1, mu, sigma) - stats.norm.cdf(-1, mu, sigma)
print(f"P(-1 < X < 1) = {prob_1:.4f} (should be approximately 0.6827)")

# P(-2 < X < 2)
prob_2 = stats.norm.cdf(2, mu, sigma) - stats.norm.cdf(-2, mu, sigma)
print(f"P(-2 < X < 2) = {prob_2:.4f} (should be approximately 0.9545)")

# P(X > 1)
prob_greater = 1 - stats.norm.cdf(1, mu, sigma)
print(f"P(X > 1) = {prob_greater:.4f}")

# 4. z-scores
print("\n" + "=" * 60)
print("Z-SCORES")
print("=" * 60)

# IQ scores: mean = 100, SD = 15
iq_mean, iq_sd = 100, 15
iq_score = 130
z_score = (iq_score - iq_mean) / iq_sd
print(f"IQ score: {iq_score}")
print(f"Mean: {iq_mean}, SD: {iq_sd}")
print(f"Z-score: {z_score:.2f}")
print(f"Interpretation: An IQ of {iq_score} is {z_score:.1f} standard deviations above the mean.")

# 5. Percentiles
print("\n" + "=" * 60)
print("PERCENTILES")
print("=" * 60)

# Find the IQ score at the 95th percentile
percentile_95 = stats.norm.ppf(0.95, iq_mean, iq_sd)
print(f"95th percentile IQ: {percentile_95:.1f}")
print("Interpretation: 95% of people have an IQ below this score.")

# 6. Real-world example: Test scores
print("\n" + "=" * 60)
print("REAL-WORLD EXAMPLE: TEST SCORES")
print("=" * 60)

# Test scores: mean = 75, SD = 10
test_mean, test_sd = 75, 10

# What is the probability of scoring above 90?
prob_above_90 = 1 - stats.norm.cdf(90, test_mean, test_sd)
print(f"P(Score > 90) = {prob_above_90:.4f}")

# What is the probability of scoring between 65 and 85?
prob_between = stats.norm.cdf(85, test_mean, test_sd) - stats.norm.cdf(65, test_mean, test_sd)
print(f"P(65 < Score < 85) = {prob_between:.4f}")
```

**Checking for Normality**:

```python
# Generate data
np.random.seed(42)
normal_data = np.random.normal(50, 10, 1000)
non_normal_data = np.random.exponential(20, 1000)

fig, axes = plt.subplots(2, 2, figsize=(12, 10))

# Normal data histogram
sns.histplot(normal_data, kde=True, ax=axes[0, 0])
axes[0, 0].set_title('Normal Data Histogram')

# Normal data Q-Q plot
stats.probplot(normal_data, dist="norm", plot=axes[0, 1])
axes[0, 1].set_title('Normal Q-Q Plot')

# Non-normal data histogram
sns.histplot(non_normal_data, kde=True, ax=axes[1, 0])
axes[1, 0].set_title('Non-Normal Data Histogram')

# Non-normal Q-Q plot
stats.probplot(non_normal_data, dist="norm", plot=axes[1, 1])
axes[1, 1].set_title('Non-Normal Q-Q Plot')

plt.tight_layout()
plt.show()

print("\n" + "=" * 60)
print("NORMALITY TESTS")
print("=" * 60)

# Shapiro-Wilk test
shapiro_normal = stats.shapiro(normal_data)
shapiro_non_normal = stats.shapiro(non_normal_data)

print(f"Normal data Shapiro-Wilk test: p-value = {shapiro_normal.pvalue:.4f}")
print(f"Non-normal data Shapiro-Wilk test: p-value = {shapiro_non_normal.pvalue:.4f}")
print("If p-value > 0.05, we cannot reject normality (data is approximately normal).")
```

---

### Practical Examples

- **Example 1**: A quality analyst uses the normal distribution to model product weights.
- **Example 2**: A teacher uses the normal distribution to grade tests (bell curve).
- **Example 3**: A financial analyst uses the normal distribution to model stock returns.

---

### Hands-on Coding Exercises

**Exercise 8.7** – Normal distribution practice:
```python
# 1. Generate random data from a normal distribution
# 2. Plot the histogram with KDE
# 3. Calculate the mean and standard deviation
# 4. Use the 68-95-99.7 rule to check the data
# 5. Calculate z-scores for specific values
# 6. Calculate probabilities using the CDF
```

**Exercise 8.8** – Normality testing:
```python
# 1. Load a dataset (e.g., 'tips' or 'penguins')
# 2. Select a numeric column
# 3. Create a histogram and Q-Q plot
# 4. Perform a Shapiro-Wilk test
# 5. Determine if the data is approximately normal
```

---

### Mini Quiz

1. What are the two parameters of a normal distribution?
2. What percentage of data falls within 2 standard deviations of the mean?
3. What is a z-score?
4. What is the purpose of the 68-95-99.7 rule?
5. What is a Q-Q plot used for?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Assuming all data is normal | Always check for normality |
| Using normal distribution for skewed data | Transform data or use non-parametric methods |
| Misinterpreting the 68-95-99.7 rule | Ensure data is approximately normal |
| Not checking for outliers | Outliers can affect normality tests |

---

### Interview Questions

1. **What is the normal distribution and why is it important?**  
   *Answer*: The normal distribution is a continuous probability distribution that is symmetric and bell-shaped. It is important because many natural phenomena follow this distribution, and it forms the basis of many statistical methods.

2. **What is the 68-95-99.7 rule?**  
   *Answer*: It states that approximately 68% of data falls within 1 standard deviation of the mean, 95% within 2, and 99.7% within 3.

3. **What is a z-score and how is it used?**  
   *Answer*: A z-score measures how many standard deviations a value is from the mean. It is used to standardise data and calculate probabilities.

---

### Assignment and Mini Project

**Assignment 8.4** – Normal distribution analysis:
```python
# 1. Load a dataset (e.g., 'titanic' or 'penguins')
# 2. Select a numeric column
# 3. Check for normality using:
#    - Histogram with KDE
#    - Q-Q plot
#    - Shapiro-Wilk test
# 4. Calculate probabilities using the normal distribution
# 5. Calculate z-scores for specific values
# 6. Write a summary report
```

**Mini Project** – Grade Analysis Tool:
Create a program that:
1. Generates a dataset of test scores (approximately normal).
2. Calculates the mean and standard deviation.
3. Uses the normal distribution to calculate:
   - Probability of scoring above a threshold.
   - Probability of scoring between two values.
   - Percentile rank of a given score.
   - Score at a given percentile.
4. Visualises the distribution with the 68-95-99.7 rule.
5. Provides an interpretation of the results.

---

### Summary and Revision Notes

- Normal distribution: bell-shaped, symmetric, defined by μ and σ.
- 68-95-99.7 rule: 1σ, 2σ, 3σ.
- z-score: (x - μ) / σ.
- Standard normal: μ = 0, σ = 1.
- Check normality with histograms, Q-Q plots, and Shapiro-Wilk test.

---

## Lesson 8.5 – Sampling

### Concept Explanation

**Sampling** is the process of selecting a subset of individuals from a population to make inferences about the population.

**Key concepts**:

**1. Population**: The entire group of interest.
- Example: All customers of a company.

**2. Sample**: A subset of the population.
- Example: 100 randomly selected customers.

**3. Sampling Methods**:
- **Random sampling**: Every member has an equal chance of being selected.
- **Systematic sampling**: Selecting every kth member.
- **Stratified sampling**: Dividing the population into strata and sampling from each.
- **Cluster sampling**: Dividing the population into clusters and selecting whole clusters.

**4. Sampling Distribution**: The distribution of a statistic (e.g., mean) across all possible samples.

**5. Central Limit Theorem (CLT)**:
- For large enough sample sizes, the sampling distribution of the mean is approximately normal, regardless of the population distribution.
- Sample size ≥ 30 is generally sufficient.

---

### Importance and Real-World Use Cases

- **Why it matters**: It is often impractical or impossible to study an entire population. Sampling allows us to make valid inferences with less time and cost.

- **Use cases**:
  - A **market researcher** surveys a sample of customers to understand the entire customer base.
  - A **quality analyst** inspects a sample of products to estimate the defect rate.
  - A **pollster** surveys a sample of voters to predict election outcomes.

---

### Step-by-Step Demonstration

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats

# 1. Creating a population
print("=" * 60)
print("SAMPLING DEMONSTRATION")
print("=" * 60)

np.random.seed(42)
population = np.random.exponential(20, 10000)  # Non-normal population
print(f"Population size: {len(population)}")
print(f"Population mean: {np.mean(population):.2f}")
print(f"Population standard deviation: {np.std(population):.2f}")

# 2. Random sampling
sample_size = 100
sample = np.random.choice(population, sample_size, replace=False)
print(f"\nSample size: {sample_size}")
print(f"Sample mean: {np.mean(sample):.2f}")
print(f"Sample standard deviation: {np.std(sample):.2f}")

# 3. Sampling distribution of the mean (CLT)
print("\n" + "=" * 60)
print("CENTRAL LIMIT THEOREM (CLT)")
print("=" * 60)

sample_means = []
for _ in range(1000):
    sample = np.random.choice(population, 30)
    sample_means.append(np.mean(sample))

plt.figure(figsize=(12, 5))

plt.subplot(1, 2, 1)
sns.histplot(population, kde=True)
plt.title('Population Distribution (Exponential)')
plt.xlabel('Value')
plt.ylabel('Frequency')

plt.subplot(1, 2, 2)
sns.histplot(sample_means, kde=True)
plt.axvline(np.mean(sample_means), color='red', linestyle='--', label=f'Mean: {np.mean(sample_means):.2f}')
plt.title('Sampling Distribution of the Mean (n=30)')
plt.xlabel('Sample Mean')
plt.ylabel('Frequency')
plt.legend()

plt.tight_layout()
plt.show()

print(f"Mean of sample means: {np.mean(sample_means):.2f}")
print(f"Standard deviation of sample means: {np.std(sample_means):.2f}")
print(f"Population mean: {np.mean(population):.2f}")
print("The sample mean is close to the population mean, demonstrating the CLT.")

# 4. Effect of sample size
print("\n" + "=" * 60)
print("EFFECT OF SAMPLE SIZE")
print("=" * 60)

sample_sizes = [5, 10, 20, 30, 50, 100, 200]
sample_means_by_size = []

for n in sample_sizes:
    means = []
    for _ in range(1000):
        sample = np.random.choice(population, n)
        means.append(np.mean(sample))
    sample_means_by_size.append(means)

# Plot the distribution of sample means for different sample sizes
fig, axes = plt.subplots(2, 4, figsize=(16, 8))
axes = axes.flatten()

for i, (n, means) in enumerate(zip(sample_sizes, sample_means_by_size)):
    axes[i].hist(means, bins=30, density=True, alpha=0.7)
    axes[i].axvline(np.mean(means), color='red', linestyle='--')
    axes[i].set_title(f'n = {n}')
    axes[i].set_xlabel('Mean')
    axes[i].set_ylabel('Density')

plt.tight_layout()
plt.show()

# 5. Standard error of the mean
print("\n" + "=" * 60)
print("STANDARD ERROR OF THE MEAN (SEM)")
print("=" * 60)

for n in sample_sizes:
    sem = np.std(sample_means_by_size[sample_sizes.index(n)])
    print(f"Sample size: {n}, Standard Error: {sem:.4f}")
print("\nLarger sample sizes result in smaller standard errors (more precise estimates).")
```

**Sampling Methods Demonstration**:

```python
# 1. Stratified sampling
print("\n" + "=" * 60)
print("STRATIFIED SAMPLING")
print("=" * 60)

# Create a population with strata
np.random.seed(42)
strata_A = np.random.normal(50, 10, 500)   # Group A
strata_B = np.random.normal(70, 15, 300)   # Group B
strata_C = np.random.normal(30, 5, 200)    # Group C

population_strata = np.concatenate([strata_A, strata_B, strata_C])
strata_labels = np.array(['A']*500 + ['B']*300 + ['C']*200)

# Stratified sample (proportional allocation)
sample_size = 100
strata_sizes = {'A': 500, 'B': 300, 'C': 200}
total_size = sum(strata_sizes.values())

# Calculate sample size for each stratum
sample_sizes_strata = {k: int(sample_size * (v / total_size)) for k, v in strata_sizes.items()}

# Take samples from each stratum
samples = []
for stratum, n in sample_sizes_strata.items():
    stratum_indices = np.where(strata_labels == stratum)[0]
    sample_indices = np.random.choice(stratum_indices, n, replace=False)
    samples.extend(population_strata[sample_indices])

print(f"Total sample size: {len(samples)}")
print(f"Stratified sample mean: {np.mean(samples):.2f}")
print(f"Population mean: {np.mean(population_strata):.2f}")
```

---

### Practical Examples

- **Example 1**: A market researcher uses random sampling to survey customers.
- **Example 2**: A quality inspector uses stratified sampling to check products from different production lines.
- **Example 3**: A pollster uses cluster sampling to survey voters in different regions.

---

### Hands-on Coding Exercises

**Exercise 8.9** – Sampling and the CLT:
```python
# 1. Create a non-normal population
# 2. Take random samples of different sizes
# 3. Calculate the sample means
# 4. Show that the distribution of sample means becomes approximately normal
# 5. Demonstrate the relationship between sample size and standard error
```

**Exercise 8.10** – Sampling methods:
```python
# 1. Create a population with identifiable strata
# 2. Implement simple random sampling
# 3. Implement stratified sampling
# 4. Compare the results
# 5. Discuss which method is more appropriate
```

---

### Mini Quiz

1. What is the difference between a population and a sample?
2. What is the Central Limit Theorem?
3. What is the standard error of the mean?
4. What is the advantage of stratified sampling over simple random sampling?
5. Why is sample size important?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using a non-representative sample | Use random or stratified sampling |
| Sample size too small | Use the Central Limit Theorem guideline (n ≥ 30) |
| Ignoring sampling bias | Ensure the sample is representative |
| Not understanding the standard error | Use the standard error to quantify uncertainty |

---

### Interview Questions

1. **What is the Central Limit Theorem and why is it important?**  
   *Answer*: The CLT states that for large enough sample sizes, the sampling distribution of the mean is approximately normal, regardless of the population distribution. It is important because it justifies using normal-based inference even when the population is not normal.

2. **What is the difference between a sample and a population?**  
   *Answer*: A population is the entire group of interest. A sample is a subset of the population used to make inferences about the population.

3. **How do you choose the sample size?**  
   *Answer*: Based on the desired confidence level, margin of error, and population variability. Larger sample sizes provide more precise estimates.

---

### Assignment and Mini Project

**Assignment 8.5** – Sampling analysis:
```python
# 1. Load or generate a population
# 2. Take multiple random samples of different sizes
# 3. Calculate the mean and standard error for each
# 4. Show the sampling distribution
# 5. Demonstrate the CLT
# 6. Write a summary report
```

**Mini Project** – Sampling Simulator:
Create a program that:
1. Generates a population from a specified distribution.
2. Allows the user to select sample size and number of samples.
3. Simulates the sampling distribution of the mean.
4. Visualises the distribution.
5. Calculates the mean and standard error.
6. Compares with the theoretical normal distribution.

---

### Summary and Revision Notes

- Population: entire group, Sample: subset.
- Central Limit Theorem: sample means are approximately normal for large n.
- Sampling methods: random, systematic, stratified, cluster.
- Standard error: standard deviation of the sampling distribution.
- Larger samples = smaller standard error.

---

## Lesson 8.6 – Confidence Intervals

### Concept Explanation

A **Confidence Interval (CI)** is a range of values that is likely to contain the population parameter with a certain level of confidence.

**Key concepts**:

**1. Point Estimate**: A single value estimate of a population parameter (e.g., sample mean).

**2. Confidence Level**: The probability that the interval contains the population parameter (e.g., 95%).

**3. Margin of Error**: The maximum expected difference between the point estimate and the population parameter.

**Formula for a 95% Confidence Interval**:

- For a mean (population SD known): x̄ ± z* × (σ/√n)
- For a mean (population SD unknown): x̄ ± t* × (s/√n)
- For a proportion: p̂ ± z* × √(p̂(1-p̂)/n)

**Interpretation**:
- If you took many samples and built intervals, 95% of them would contain the true population parameter.

---

### Importance and Real-World Use Cases

- **Why it matters**: Confidence intervals quantify uncertainty. They provide a range of plausible values rather than a single point estimate.

- **Use cases**:
  - A **market researcher** calculates a 95% CI for customer satisfaction.
  - A **quality analyst** computes a 95% CI for defect rates.
  - A **financial analyst** calculates a 95% CI for expected returns.

---

### Step-by-Step Demonstration

```python
import numpy as np
from scipy import stats
import matplotlib.pyplot as plt
import seaborn as sns

# 1. Confidence interval for a mean (known population SD)
print("=" * 60)
print("CONFIDENCE INTERVALS")
print("=" * 60)

# Sample data
np.random.seed(42)
sample = np.random.normal(50, 10, 30)  # n=30, mean=50, sd=10

sample_mean = np.mean(sample)
sample_std = np.std(sample, ddof=1)
n = len(sample)

# 95% CI (using t-distribution)
t_critical = stats.t.ppf(0.975, df=n-1)
margin_error = t_critical * (sample_std / np.sqrt(n))
ci_lower = sample_mean - margin_error
ci_upper = sample_mean + margin_error

print(f"Sample mean: {sample_mean:.2f}")
print(f"Sample standard deviation: {sample_std:.2f}")
print(f"Sample size: {n}")
print(f"95% Confidence Interval: ({ci_lower:.2f}, {ci_upper:.2f})")
print(f"Interpretation: We are 95% confident that the population mean is between {ci_lower:.2f} and {ci_upper:.2f}.")

# 2. Confidence interval using Z (known population SD)
print("\n" + "=" * 60)
print("95% CONFIDENCE INTERVAL (Z-DISTRIBUTION)")
print("=" * 60)

# Known population SD (hypothetical)
pop_sd = 10
z_critical = stats.norm.ppf(0.975)  # 1.96 for 95% CI
margin_error_z = z_critical * (pop_sd / np.sqrt(n))
ci_z_lower = sample_mean - margin_error_z
ci_z_upper = sample_mean + margin_error_z

print(f"95% Confidence Interval (Z): ({ci_z_lower:.2f}, {ci_z_upper:.2f})")

# 3. Confidence intervals for different confidence levels
print("\n" + "=" * 60)
print("CONFIDENCE INTERVALS FOR DIFFERENT LEVELS")
print("=" * 60)

confidence_levels = [0.80, 0.90, 0.95, 0.99]

for cl in confidence_levels:
    alpha = 1 - cl
    t_crit = stats.t.ppf(1 - alpha/2, df=n-1)
    margin = t_crit * (sample_std / np.sqrt(n))
    lower = sample_mean - margin
    upper = sample_mean + margin
    print(f"{int(cl*100)}% CI: ({lower:.2f}, {upper:.2f})")

# 4. Visualising confidence intervals
print("\n" + "=" * 60)
print("VISUALISING CONFIDENCE INTERVALS")
print("=" * 60)

# Generate multiple samples and plot their CIs
np.random.seed(42)
sample_means = []
ci_lowers = []
ci_uppers = []

for i in range(20):
    sample = np.random.normal(50, 10, 30)
    mean = np.mean(sample)
    std = np.std(sample, ddof=1)
    t_crit = stats.t.ppf(0.975, df=29)
    margin = t_crit * (std / np.sqrt(30))
    
    sample_means.append(mean)
    ci_lowers.append(mean - margin)
    ci_uppers.append(mean + margin)

# Plot the CIs
plt.figure(figsize=(10, 6))
for i in range(20):
    plt.plot([ci_lowers[i], ci_uppers[i]], [i+1, i+1], 'b-', linewidth=2)
    plt.plot(sample_means[i], i+1, 'ro', markersize=5)

plt.axvline(50, color='red', linestyle='--', label='Population Mean (50)')
plt.title('20 Confidence Intervals (95%)')
plt.xlabel('Value')
plt.ylabel('Sample Number')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()

# 5. Confidence interval for a proportion
print("\n" + "=" * 60)
print("CONFIDENCE INTERVAL FOR A PROPORTION")
print("=" * 60)

# Simulate customer satisfaction survey
np.random.seed(42)
satisfied = 120  # number of satisfied customers
total = 200      # total customers
p_hat = satisfied / total
z_crit = stats.norm.ppf(0.975)

se = np.sqrt(p_hat * (1 - p_hat) / total)
margin = z_crit * se
ci_lower_prop = p_hat - margin
ci_upper_prop = p_hat + margin

print(f"Sample proportion: {p_hat:.3f}")
print(f"95% Confidence Interval for proportion: ({ci_lower_prop:.3f}, {ci_upper_prop:.3f})")
```

**Real-World Example**:

```python
print("\n" + "=" * 60)
print("REAL-WORLD EXAMPLE")
print("=" * 60)

# Customer satisfaction survey
# 150 out of 200 customers are satisfied
n = 200
satisfied = 150
p_hat = satisfied / n

# 95% CI
z_crit = stats.norm.ppf(0.975)
se = np.sqrt(p_hat * (1 - p_hat) / n)
margin = z_crit * se

print(f"Customer satisfaction survey:")
print(f"  Sample size: {n}")
print(f"  Satisfied customers: {satisfied}")
print(f"  Satisfaction rate: {p_hat:.1%}")
print(f"  95% CI: ({p_hat - margin:.3f}, {p_hat + margin:.3f})")
print(f"\nInterpretation: We are 95% confident that the true customer satisfaction rate is between {p_hat - margin:.1%} and {p_hat + margin:.1%}.")
```

---

### Practical Examples

- **Example 1**: A market researcher calculates a 95% confidence interval for the average customer spend.
- **Example 2**: A quality analyst calculates a 95% confidence interval for the defect rate.
- **Example 3**: A financial analyst calculates a 95% confidence interval for the average return.

---

### Hands-on Coding Exercises

**Exercise 8.11** – Confidence intervals:
```python
# 1. Generate a sample from a normal distribution
# 2. Calculate a 95% confidence interval for the mean
# 3. Calculate a 99% confidence interval for the mean
# 4. Compare the widths of the intervals
# 5. Interpret the results
```

**Exercise 8.12** – Proportion CI:
```python
# 1. Simulate a survey with 150 successes out of 300 trials
# 2. Calculate the 95% confidence interval for the proportion
# 3. Calculate the 99% confidence interval
# 4. Interpret the results
# 5. Visualise the confidence interval
```

---

### Mini Quiz

1. What is a confidence interval?
2. What does the confidence level mean?
3. What is the relationship between confidence level and interval width?
4. What is the difference between a confidence interval and a margin of error?
5. What sample size would you need to halve the margin of error?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Misinterpreting the confidence level | It refers to the procedure, not a single interval |
| Using the wrong distribution | Use t-distribution when population SD is unknown |
| Not checking sample size requirements | Ensure sample size is adequate |
| Overly narrow or wide intervals | Choose the appropriate confidence level |

---

### Interview Questions

1. **What is a confidence interval?**  
   *Answer*: A confidence interval is a range of values that is likely to contain the population parameter with a certain level of confidence.

2. **What does a 95% confidence interval mean?**  
   *Answer*: If we took many samples and built intervals, approximately 95% of them would contain the true population parameter.

3. **How does sample size affect the confidence interval?**  
   *Answer*: Larger sample sizes result in narrower (more precise) confidence intervals.

---

### Assignment and Mini Project

**Assignment 8.6** – Confidence interval analysis:
```python
# 1. Load a dataset (e.g., 'tips' or 'titanic')
# 2. Select a numeric column
# 3. Calculate a 95% CI for the mean
# 4. Calculate a 99% CI for the mean
# 5. Compare the intervals
# 6. Calculate a CI for a proportion (if applicable)
# 7. Interpret the results
```

**Mini Project** – Confidence Interval Explorer:
Create a program that:
1. Generates a sample from a population.
2. Calculates confidence intervals at different confidence levels (80%, 90%, 95%, 99%).
3. Shows how the interval width changes with confidence level.
4. Shows how the interval width changes with sample size.
5. Visualises the intervals.
6. Provides an interpretation of the results.

---

### Summary and Revision Notes

- Confidence interval: range of plausible values for a population parameter.
- Point estimate ± margin of error.
- Confidence level: probability that the interval contains the parameter.
- Larger sample = narrower interval.
- Higher confidence = wider interval.

---

## Lesson 8.7 – Hypothesis Testing

### Concept Explanation

**Hypothesis testing** is a statistical method for making decisions about population parameters based on sample data.

**Key concepts**:

**1. Null Hypothesis (H₀)**: The default assumption (no effect, no difference).
- Example: μ = 100, p = 0.5.

**2. Alternative Hypothesis (H₁)**: The claim you want to test.
- Two-sided: μ ≠ 100.
- One-sided (left): μ < 100.
- One-sided (right): μ > 100.

**3. Significance Level (α)**: The probability of rejecting H₀ when it is true (Type I error).
- Common values: 0.05, 0.01, 0.10.

**4. Test Statistic**: A measure of how far the sample statistic is from the null value.
- For means: t = (x̄ - μ₀) / (s / √n).

**5. p-value**: The probability of observing a test statistic as extreme as the one observed, assuming H₀ is true.
- If p < α, reject H₀.

**6. Decision**:
- p ≤ α: Reject H₀ (statistically significant).
- p > α: Fail to reject H₀ (not statistically significant).

**Types of errors**:
- **Type I**: Rejecting H₀ when it is true (false positive).
- **Type II**: Failing to reject H₀ when it is false (false negative).

---

### Importance and Real-World Use Cases

- **Why it matters**: Hypothesis testing is the foundation of evidence-based decision-making. It is used to validate claims, compare groups, and make business decisions.

- **Use cases**:
  - A **marketing analyst** tests whether a new campaign increases conversions.
  - A **quality analyst** tests whether a new process reduces defects.
  - A **medical researcher** tests whether a new drug is effective.

---

### Step-by-Step Demonstration

```python
import numpy as np
from scipy import stats
import matplotlib.pyplot as plt
import seaborn as sns

# 1. One-sample t-test
print("=" * 60)
print("HYPOTHESIS TESTING")
print("=" * 60)

print("\n1. ONE-SAMPLE T-TEST")
print("-" * 40)

# Scenario: A company claims their product weight is 500g.
# Sample of 30 products
np.random.seed(42)
sample_weights = np.random.normal(498, 10, 30)  # True mean = 498

# H₀: μ = 500
# H₁: μ ≠ 500

t_stat, p_value = stats.ttest_1samp(sample_weights, 500)
print(f"Sample mean: {np.mean(sample_weights):.2f}")
print(f"Sample std: {np.std(sample_weights, ddof=1):.2f}")
print(f"t-statistic: {t_stat:.3f}")
print(f"p-value: {p_value:.4f}")

alpha = 0.05
if p_value < alpha:
    print("Decision: Reject H₀ (statistically significant)")
    print("Conclusion: There is evidence that the product weight differs from 500g.")
else:
    print("Decision: Fail to reject H₀ (not statistically significant)")
    print("Conclusion: There is not enough evidence to conclude the weight differs from 500g.")

# 2. Two-sample t-test
print("\n" + "=" * 60)
print("2. TWO-SAMPLE T-TEST")
print("=" * 60)

# Comparing two groups: control and treatment
np.random.seed(42)
control = np.random.normal(50, 10, 30)
treatment = np.random.normal(55, 10, 30)  # Treatment has higher mean

# H₀: μ₁ = μ₂
# H₁: μ₁ ≠ μ₂

t_stat, p_value = stats.ttest_ind(control, treatment)
print(f"Control mean: {np.mean(control):.2f}")
print(f"Treatment mean: {np.mean(treatment):.2f}")
print(f"t-statistic: {t_stat:.3f}")
print(f"p-value: {p_value:.4f}")

if p_value < 0.05:
    print("Decision: Reject H₀")
    print("Conclusion: There is a significant difference between control and treatment.")
else:
    print("Decision: Fail to reject H₀")
    print("Conclusion: There is no significant difference between control and treatment.")

# 3. Paired t-test
print("\n" + "=" * 60)
print("3. PAIRED T-TEST")
print("=" * 60)

# Before and after measurements
np.random.seed(42)
before = np.random.normal(100, 15, 20)
after = before + np.random.normal(10, 5, 20)  # After is higher

# H₀: μ_before = μ_after
# H₁: μ_before ≠ μ_after

t_stat, p_value = stats.ttest_rel(before, after)
print(f"Before mean: {np.mean(before):.2f}")
print(f"After mean: {np.mean(after):.2f}")
print(f"Difference: {np.mean(after - before):.2f}")
print(f"t-statistic: {t_stat:.3f}")
print(f"p-value: {p_value:.4f}")

if p_value < 0.05:
    print("Decision: Reject H₀")
    print("Conclusion: There is a significant difference between before and after.")
else:
    print("Decision: Fail to reject H₀")
    print("Conclusion: There is no significant difference between before and after.")

# 4. Chi-square test for independence
print("\n" + "=" * 60)
print("4. CHI-SQUARE TEST")
print("=" * 60)

# Contingency table: Gender vs Purchase
observed = np.array([[40, 60], [30, 70]])  # [[Male-Purchase, Male-No], [Female-Purchase, Female-No]]
chi2_stat, p_value, dof, expected = stats.chi2_contingency(observed)

print("Observed frequencies:")
print(observed)
print(f"Chi-square statistic: {chi2_stat:.3f}")
print(f"p-value: {p_value:.4f}")
print(f"Degrees of freedom: {dof}")

if p_value < 0.05:
    print("Decision: Reject H₀")
    print("Conclusion: There is a relationship between gender and purchase.")
else:
    print("Decision: Fail to reject H₀")
    print("Conclusion: There is no relationship between gender and purchase.")
```

**Visualising Hypothesis Testing**:

```python
# Visualising the t-test
fig, axes = plt.subplots(1, 2, figsize=(12, 5))

# Control vs Treatment
sns.boxplot(data=[control, treatment], ax=axes[0])
axes[0].set_xticklabels(['Control', 'Treatment'])
axes[0].set_title('Control vs Treatment')

# Histogram of difference (paired test)
diff = after - before
sns.histplot(diff, kde=True, ax=axes[1])
axes[1].axvline(0, color='red', linestyle='--', label='No Difference')
axes[1].set_title('Distribution of Differences (Paired)')
axes[1].legend()

plt.tight_layout()
plt.show()
```

**Power and Sample Size**:

```python
print("\n" + "=" * 60)
print("5. POWER AND SAMPLE SIZE")
print("=" * 60)

from statsmodels.stats.power import TTestIndPower

# Calculate sample size for a given power
power_analysis = TTestIndPower()
effect_size = 0.5  # Medium effect
power = 0.8
alpha = 0.05

sample_size = power_analysis.solve_power(effect_size=effect_size, power=power, alpha=alpha, ratio=1)
print(f"Required sample size (per group) for power = {power}: {int(np.ceil(sample_size))}")
print("Power = 1 - β (probability of detecting an effect if it exists)")
```

---

### Practical Examples

- **Example 1**: A marketing analyst tests whether a new campaign increases conversion rates.
- **Example 2**: A quality analyst tests whether a new process reduces defect rates.
- **Example 3**: A product manager tests whether a new feature increases user engagement.

---

### Hands-on Coding Exercises

**Exercise 8.13** – One-sample t-test:
```python
# 1. Generate a sample from a normal distribution
# 2. Test whether the mean is equal to a specified value
# 3. Perform a one-sided test
# 4. Interpret the p-value
# 5. Draw a conclusion
```

**Exercise 8.14** – Two-sample t-test:
```python
# 1. Generate two samples from different distributions
# 2. Test whether they have the same mean
# 3. Perform a one-sided test (mean of group1 > mean of group2)
# 4. Interpret the p-value
# 5. Draw a conclusion
```

---

### Mini Quiz

1. What is the null hypothesis?
2. What is the alternative hypothesis?
3. What does the p-value represent?
4. What is a Type I error?
5. What is the difference between a one-tailed and two-tailed test?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Misinterpreting p-value | p-value is not the probability that H₀ is true |
| Using the wrong test | Choose the appropriate test for the data |
| Ignoring assumptions | Check assumptions (normality, equal variance) |
| P-hacking (multiple testing) | Correct for multiple comparisons |

---

### Interview Questions

1. **What is the difference between the null and alternative hypothesis?**  
   *Answer*: The null hypothesis is the default assumption (no effect). The alternative hypothesis is what you want to test (there is an effect).

2. **What is a p-value?**  
   *Answer*: The probability of observing a test statistic as extreme as the one observed, assuming the null hypothesis is true.

3. **What is the difference between a one-tailed and two-tailed test?**  
   *Answer*: A one-tailed test tests for an effect in one direction. A two-tailed test tests for an effect in either direction.

---

### Assignment and Mini Project

**Assignment 8.7** – Hypothesis testing analysis:
```python
# 1. Load a dataset (e.g., 'tips' or 'titanic')
# 2. Formulate a research question
# 3. Set up the null and alternative hypotheses
# 4. Perform the appropriate test
# 5. Interpret the p-value
# 6. Draw a conclusion
# 7. Write a report
```

**Mini Project** – A/B Test Analyzer:
Create a program that:
1. Simulates A/B test data (control and treatment groups).
2. Performs a two-sample t-test.
3. Calculates the effect size.
4. Calculates the required sample size for a given power.
5. Visualises the results.
6. Provides a recommendation based on the results.

---

### Summary and Revision Notes

- H₀: null hypothesis (no effect).
- H₁: alternative hypothesis (effect).
- p-value: probability under H₀.
- If p < α, reject H₀.
- Type I error: false positive (rejecting H₀ when true).
- Type II error: false negative (failing to reject H₀ when false).

---

## Final Phase 8 Assessment

Now that you have completed all lessons, test your overall understanding.

### Self-Evaluation Checklist

-  I can calculate and interpret mean, median, and mode.

-  I can calculate and interpret variance and standard deviation.

-  I understand probability basics.

-  I understand the normal distribution and its properties.

-  I understand sampling and the Central Limit Theorem.

-  I can calculate and interpret confidence intervals.

-  I can perform and interpret hypothesis tests.

---

### Answers to Mini Quizzes

**Lesson 8.1**: 1. 30. 2. 30. 3. 3. 4. Mean. 5. For skewed data or data with outliers.

**Lesson 8.2**: 1. Variance is squared, standard deviation is in original units. 2. Population uses N, sample uses n-1. 3. Low variability. 4. (SD/Mean) × 100. 5. It's in the same units as the data.

**Lesson 8.3**: 1. 1/6. 2. 1/4. 3. Independent events don't affect each other; dependent events do. 4. Probability of A given B. 5. Rolling 3, 4, 5, or 6.

**Lesson 8.4**: 1. Mean and standard deviation. 2. Approximately 95%. 3. Number of standard deviations from the mean. 4. To understand the spread of data in a normal distribution. 5. To check for normality.

**Lesson 8.5**: 1. Population is the entire group; sample is a subset. 2. Sample means are approximately normal for large n. 3. Standard deviation of the sampling distribution. 4. Ensures representation of all groups. 5. Larger samples give more precise estimates.

**Lesson 8.6**: 1. A range likely to contain the population parameter. 2. The probability that the procedure produces an interval containing the parameter. 3. Higher confidence = wider interval. 4. Margin of error is the half-width of the interval. 5. Increase sample size by 4.

**Lesson 8.7**: 1. The default assumption (no effect). 2. The claim to be tested. 3. Probability under the null hypothesis. 4. Rejecting H₀ when it is true. 5. One-tailed tests for a specific direction; two-tailed for either direction.

---

**Congratulations!** You have completed Phase 8 of Python for Data Analytics. You now have a solid foundation in statistics, which is essential for any data analytics professional. Keep practising!

