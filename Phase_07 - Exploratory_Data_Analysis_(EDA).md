# Phase 7: Exploratory Data Analysis (EDA)

Welcome to **Phase 7** – the heart of data science and analytics! After mastering data manipulation with Pandas, numerical computing with NumPy, and visualisation with Matplotlib and Seaborn, you are now ready to bring it all together.

**Exploratory Data Analysis (EDA)** is the process of investigating, understanding, and summarising the main characteristics of a dataset. It is the most critical step in any data project. EDA is where you:
- Understand what your data contains.
- Identify patterns, relationships, and anomalies.
- Generate hypotheses for further analysis.
- Prepare data for modelling or reporting.

In this phase, you will learn:
- How to understand the structure and content of any dataset.
- How to calculate and interpret **descriptive statistics**.
- How to perform **correlation analysis** to find relationships.
- How to detect and handle **outliers**.
- How to analyse **missing values** and make decisions about them.
- How to develop a deep **feature understanding**.
- How to translate data insights into **business insights**.
- How to tell a compelling **data story** to stakeholders.

By the end of this phase, you will be able to approach any new dataset with confidence, extract meaningful insights, and communicate your findings effectively.

Let's begin!

---

## Lesson 7.1 – Understanding Datasets

### Concept Explanation

Before you can analyse a dataset, you must understand its structure, content, and context. This involves asking fundamental questions:

**Key questions**:
1. **What does the data represent?** – What is the domain? Sales? Healthcare? Customer behaviour?
2. **How many rows and columns?** – The size of the dataset.
3. **What are the columns?** – What do they mean? What are their data types?
4. **What is the granularity?** – What does each row represent? A transaction? A customer? A day?
5. **Where did the data come from?** – Is it reliable? Is it complete?

**Tools for understanding datasets**:
- `df.head()` – preview the first few rows.
- `df.tail()` – preview the last few rows.
- `df.info()` – data types, non-null counts.
- `df.shape` – number of rows and columns.
- `df.columns` – column names.
- `df.describe()` – summary statistics.
- `df.sample()` – random sample of rows.

---

### Importance and Real-World Use Cases

- **Why it matters**: You cannot solve a problem you don't understand. Understanding your dataset is the foundation of every successful data project.

- **Use cases**:
  - A **data analyst** receives a new sales dataset and needs to understand its structure before building reports.
  - A **data scientist** is given a new dataset for machine learning and needs to understand its features.
  - A **business analyst** needs to quickly assess the quality of a dataset before presenting it to stakeholders.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

# Load a dataset (Titanic)
titanic = sns.load_dataset('titanic')

# 1. Basic overview
print("=" * 60)
print("DATASET OVERVIEW")
print("=" * 60)
print(f"Dataset shape: {titanic.shape}")
print(f"Number of rows: {titanic.shape[0]}")
print(f"Number of columns: {titanic.shape[1]}")
print(f"Column names: {titanic.columns.tolist()}")
print(f"Data types:\n{titanic.dtypes}")

# 2. Preview the data
print("\n" + "=" * 60)
print("DATA PREVIEW")
print("=" * 60)
print("First 5 rows:\n", titanic.head())
print("\nLast 5 rows:\n", titanic.tail())

# 3. Random sample
print("\nRandom sample (3 rows):\n", titanic.sample(3))

# 4. Information summary
print("\n" + "=" * 60)
print("DATA INFORMATION")
print("=" * 60)
titanic.info()

# 5. Column analysis
print("\n" + "=" * 60)
print("COLUMN ANALYSIS")
print("=" * 60)
for col in titanic.columns:
    unique_count = titanic[col].nunique()
    null_count = titanic[col].isnull().sum()
    null_pct = (null_count / len(titanic)) * 100
    dtype = titanic[col].dtype
    print(f"{col:15} | {dtype:15} | Unique: {unique_count:5} | Nulls: {null_count:5} ({null_pct:.1f}%)")

# 6. Summary statistics
print("\n" + "=" * 60)
print("SUMMARY STATISTICS (Numeric Columns)")
print("=" * 60)
print(titanic.describe())

# 7. Categorical columns overview
print("\n" + "=" * 60)
print("CATEGORICAL COLUMNS")
print("=" * 60)
cat_cols = titanic.select_dtypes(include=['object', 'category']).columns
for col in cat_cols:
    print(f"\n{col} value counts:")
    print(titanic[col].value_counts().head())

# 8. Check for memory usage
print("\n" + "=" * 60)
print("MEMORY USAGE")
print("=" * 60)
print(f"Total memory usage: {titanic.memory_usage(deep=True).sum() / 1024:.2f} KB")
```

**Loading and Exploring a Custom Dataset**:

```python
# Simulating loading a CSV
# df = pd.read_csv('sales_data.csv')

# For demonstration, create a sample dataset
np.random.seed(42)
sales_data = pd.DataFrame({
    'Date': pd.date_range('2024-01-01', periods=100),
    'Product': np.random.choice(['A', 'B', 'C', 'D'], 100),
    'Region': np.random.choice(['North', 'South', 'East', 'West'], 100),
    'Sales': np.random.randint(100, 1000, 100),
    'Quantity': np.random.randint(1, 20, 100),
    'Customer_ID': np.random.randint(1000, 2000, 100)
})

print("Sales dataset shape:", sales_data.shape)
print("\nFirst 5 rows:")
sales_data.head()
```

---

### Practical Examples

- **Example 1**: A retail analyst receives a new sales dataset and uses `df.info()` to understand the data types and missing values.
- **Example 2**: A data scientist loads a new dataset and uses `df.describe()` to understand the distribution of numeric variables.
- **Example 3**: A business analyst uses `df.sample()` to get a quick sense of the data quality.

---

### Hands-on Coding Exercises

**Exercise 7.1** – Dataset exploration:
```python
# 1. Load the 'penguins' dataset
# 2. Print the shape
# 3. Print column names
# 4. Print data types
# 5. Display the first 5 rows
# 6. Display the last 5 rows
# 7. Display 3 random rows
# 8. Print summary statistics
# 9. Print the number of unique values in each column
# 10. Print the number of missing values in each column
```

**Exercise 7.2** – Load a custom dataset:
```python
# 1. Create a dictionary with 5 columns and 20 rows
# 2. Convert to a DataFrame
# 3. Explore the dataset using the techniques above
# 4. Write a summary of your findings
```

---

### Mini Quiz

1. What does `df.info()` show?
2. How do you check the number of rows and columns?
3. What is the purpose of `df.describe()`?
4. How do you get a random sample of rows?
5. Why is it important to understand your dataset before analysis?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Skipping data exploration and jumping straight to modelling | Always start with a thorough exploration |
| Not checking data types – assuming everything is numeric | Use `df.dtypes` to check |
| Ignoring missing values | Identify missing values early |
| Not checking for duplicates | Check for duplicates before analysis |

---

### Interview Questions

1. **What is the first thing you do when you get a new dataset?**  
   *Answer*: I explore its structure using `df.head()`, `df.info()`, `df.describe()`, and `df.shape` to understand the size, data types, and basic statistics of the dataset.

2. **Why is understanding the data important before analysis?**  
   *Answer*: Understanding the data helps me identify potential issues (missing values, outliers, incorrect data types), understand the context, and plan the analysis approach.

3. **What does `df.info()` tell you?**  
   *Answer*: It tells you the column names, data types, number of non-null values, and memory usage of the DataFrame.

---

### Assignment and Mini Project

**Assignment 7.1** – Dataset explorer:
```python
# 1. Load the 'titanic' dataset
# 2. Write a function that takes a DataFrame and prints:
#    - Shape
#    - Column names with data types
#    - Missing values count and percentage
#    - Unique values count
#    - Summary statistics
#    - Sample of 5 rows
# 3. Apply the function to the dataset
```

**Mini Project** – Dataset Profile Report:
Create a program that:
1. Loads a dataset (choose one: 'titanic', 'penguins', 'tips', or a custom dataset).
2. Generates a comprehensive report with:
   - Overview (shape, columns, data types).
   - Missing value analysis.
   - Unique value analysis.
   - Summary statistics.
   - First and last rows.
   - Random sample.
3. Formats the output in a readable way.
4. Saves the report to a text file.

---

### Summary and Revision Notes

- Understand the dataset before any analysis.
- Use `df.head()`, `df.tail()`, and `df.sample()` to preview data.
- Use `df.info()` to understand data types and missing values.
- Use `df.describe()` for summary statistics.
- Check column names, shape, and memory usage.
- Identify categorical and numeric columns.
- Document your findings.

---

## Lesson 7.2 – Descriptive Statistics

### Concept Explanation

**Descriptive statistics** summarise the main features of a dataset. They provide a quantitative understanding of the central tendency, spread, and shape of the data.

**Key measures**:

**Central Tendency**:
- **Mean**: The average value.
- **Median**: The middle value (50th percentile).
- **Mode**: The most frequent value.

**Spread (Dispersion)**:
- **Range**: Max - Min.
- **Variance**: Average of squared deviations from the mean.
- **Standard Deviation**: Square root of variance.
- **Interquartile Range (IQR)**: Q3 - Q1.

**Shape**:
- **Skewness**: Symmetry of the distribution.
- **Kurtosis**: Tail heaviness.

**Key functions in Pandas**:
- `df.describe()` – summary statistics for numeric columns.
- `df.mean()`, `df.median()`, `df.mode()`.
- `df.var()`, `df.std()`, `df.quantile()`.
- `df.skew()`, `df.kurtosis()`.
- `df.min()`, `df.max()`.

---

### Importance and Real-World Use Cases

- **Why it matters**: Descriptive statistics provide a quick, quantitative understanding of your data. They help identify:
  - Whether the data is normally distributed.
  - The range of values.
  - Potential outliers.
  - Missing or extreme values.

- **Use cases**:
  - A **data analyst** uses descriptive statistics to summarise sales data for management.
  - A **data scientist** checks the distribution of features before modelling.
  - A **financial analyst** calculates the mean and standard deviation of stock returns.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

# Load dataset
titanic = sns.load_dataset('titanic')

# 1. Basic descriptive statistics
print("=" * 60)
print("DESCRIPTIVE STATISTICS")
print("=" * 60)

# Summary statistics for all numeric columns
print(titanic.describe())

# With percentiles
print("\n" + "=" * 60)
print("WITH CUSTOM PERCENTILES")
print("=" * 60)
print(titanic['age'].describe(percentiles=[0.1, 0.25, 0.5, 0.75, 0.9]))

# 2. Individual statistics
print("\n" + "=" * 60)
print("INDIVIDUAL STATISTICS")
print("=" * 60)
age = titanic['age'].dropna()
print(f"Age statistics:")
print(f"  Mean: {age.mean():.2f}")
print(f"  Median: {age.median():.2f}")
print(f"  Mode: {age.mode().iloc[0]:.2f}")
print(f"  Min: {age.min():.2f}")
print(f"  Max: {age.max():.2f}")
print(f"  Range: {age.max() - age.min():.2f}")
print(f"  Variance: {age.var():.2f}")
print(f"  Std Dev: {age.std():.2f}")
print(f"  Skewness: {age.skew():.2f}")
print(f"  Kurtosis: {age.kurtosis():.2f}")

# 3. Quantiles
print("\n" + "=" * 60)
print("QUANTILES")
print("=" * 60)
quantiles = [0.01, 0.05, 0.10, 0.25, 0.50, 0.75, 0.90, 0.95, 0.99]
for q in quantiles:
    print(f"  {q*100:5.0f}th percentile: {age.quantile(q):.2f}")

# 4. IQR (Interquartile Range)
q1 = age.quantile(0.25)
q3 = age.quantile(0.75)
iqr = q3 - q1
print(f"\nIQR: {iqr:.2f}")
print(f"Lower bound (Q1 - 1.5*IQR): {q1 - 1.5*iqr:.2f}")
print(f"Upper bound (Q3 + 1.5*IQR): {q3 + 1.5*iqr:.2f}")

# 5. Grouped statistics
print("\n" + "=" * 60)
print("GROUPED STATISTICS")
print("=" * 60)
print("Age statistics by survival:")
print(titanic.groupby('survived')['age'].describe())

# 6. Statistics for categorical variables
print("\n" + "=" * 60)
print("CATEGORICAL STATISTICS")
print("=" * 60)
print("Class distribution:")
print(titanic['class'].value_counts())
print("\nClass proportions:")
print(titanic['class'].value_counts(normalize=True))

# 7. Correlation of statistics
print("\n" + "=" * 60)
print("STATISTICAL COMPARISON")
print("=" * 60)
print("Mean vs Median (skewness indicator):")
for col in ['age', 'fare']:
    data = titanic[col].dropna()
    print(f"  {col}: Mean={data.mean():.2f}, Median={data.median():.2f}, Skew={data.skew():.2f}")
```

**Visualising Descriptive Statistics**:

```python
# Visualising distributions
fig, axes = plt.subplots(1, 3, figsize=(15, 4))

# Histogram
axes[0].hist(titanic['age'].dropna(), bins=20, color='skyblue', edgecolor='black')
axes[0].axvline(titanic['age'].mean(), color='red', linestyle='--', label='Mean')
axes[0].axvline(titanic['age'].median(), color='green', linestyle='--', label='Median')
axes[0].set_title('Age Distribution')
axes[0].set_xlabel('Age')
axes[0].set_ylabel('Frequency')
axes[0].legend()

# Box plot
axes[1].boxplot(titanic['age'].dropna())
axes[1].set_title('Age Box Plot')
axes[1].set_ylabel('Age')

# KDE
sns.kdeplot(data=titanic['age'].dropna(), ax=axes[2], fill=True)
axes[2].axvline(titanic['age'].mean(), color='red', linestyle='--', label='Mean')
axes[2].axvline(titanic['age'].median(), color='green', linestyle='--', label='Median')
axes[2].set_title('Age KDE')
axes[2].set_xlabel('Age')
axes[2].set_ylabel('Density')
axes[2].legend()

plt.tight_layout()
plt.show()
```

---

### Practical Examples

- **Example 1**: A sales manager wants to know the average, minimum, and maximum sales for each product category.
- **Example 2**: A financial analyst calculates the standard deviation of monthly returns to assess risk.
- **Example 3**: A data scientist examines the skewness of features to decide on transformations.

---

### Hands-on Coding Exercises

**Exercise 7.3** – Descriptive statistics:
```python
# 1. Load the 'penguins' dataset
# 2. Calculate descriptive statistics for all numeric columns
# 3. For each numeric column, calculate:
#    - Mean, median, mode
#    - Min, max, range
#    - Variance, standard deviation
#    - Skewness, kurtosis
# 4. Group the statistics by species
# 5. Print all results
```

**Exercise 7.4** – Statistical comparison:
```python
# 1. Load the 'tips' dataset
# 2. Compare the statistics of total_bill and tip
# 3. Calculate statistics by day
# 4. Calculate statistics by time (Lunch/Dinner)
# 5. Print a comparison table
```

---

### Mini Quiz

1. What is the difference between mean and median?
2. What does standard deviation measure?
3. How do you calculate the interquartile range (IQR)?
4. What does a positive skewness indicate?
5. What is the purpose of descriptive statistics?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using mean for skewed data | Use median for skewed distributions |
| Ignoring standard deviation | Always consider variability |
| Not checking for outliers | Use IQR or box plots to detect outliers |
| Reporting statistics without context | Always relate statistics to business context |

---

### Interview Questions

1. **What is the difference between mean and median?**  
   *Answer*: The mean is the average of all values. The median is the middle value when data is sorted. Mean is sensitive to outliers, while median is robust.

2. **What is standard deviation and why is it important?**  
   *Answer*: Standard deviation measures the spread of data around the mean. It is important for understanding variability and risk.

3. **How do you interpret skewness?**  
   *Answer*: Positive skewness means the right tail is longer (values are concentrated on the left). Negative skewness means the left tail is longer.

---

### Assignment and Mini Project

**Assignment 7.2** – Descriptive statistics report:
```python
# 1. Load the 'titanic' dataset
# 2. For each numeric column, generate:
#    - Summary statistics (mean, median, mode, min, max, std, skew, kurtosis)
#    - IQR and percentiles
# 3. For each categorical column, generate:
#    - Value counts and proportions
# 4. Create a formatted report
```

**Mini Project** – Statistical Summary Tool:
Create a program that:
1. Loads a dataset (any dataset with numeric and categorical columns).
2. Generates a comprehensive statistical summary.
3. Creates visualisations for key numeric columns (histogram, box plot, KDE).
4. Saves the summary as a CSV file.
5. Saves the visualisations as PNG files.

---

### Summary and Revision Notes

- Descriptive statistics summarise data.
- Central tendency: mean, median, mode.
- Spread: range, variance, std, IQR.
- Shape: skewness, kurtosis.
- Use `df.describe()` for a quick summary.
- Use `groupby()` for grouped statistics.
- Visualise distributions for better understanding.

---

## Lesson 7.3 – Correlation Analysis

### Concept Explanation

**Correlation analysis** measures the strength and direction of the relationship between two numeric variables.

**Key concepts**:
- **Correlation coefficient (r)**: Ranges from -1 to +1.
  - **+1**: Perfect positive correlation.
  - **-1**: Perfect negative correlation.
  - **0**: No correlation.
- **Pearson correlation**: Measures linear relationship.
- **Spearman correlation**: Measures monotonic relationship (rank-based).
- **Covariance**: Measures the direction of the relationship (not standardised).

**Interpreting correlation**:
- `0.9 - 1.0`: Very strong.
- `0.7 - 0.9`: Strong.
- `0.5 - 0.7`: Moderate.
- `0.3 - 0.5`: Weak.
- `0.0 - 0.3`: Very weak.

**Key functions**:
- `df.corr()` – correlation matrix.
- `df.corrwith()` – correlation with a single column.
- `sns.heatmap()` – visualise correlation matrix.

---

### Importance and Real-World Use Cases

- **Why it matters**: Correlation analysis helps identify relationships between variables, which is crucial for:
  - Feature selection for machine learning.
  - Understanding business drivers.
  - Identifying multicollinearity.

- **Use cases**:
  - A **marketing analyst** correlates advertising spend with sales to measure ROI.
  - A **data scientist** checks correlations to avoid redundant features.
  - A **financial analyst** correlates stock returns to build a diversified portfolio.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

# Load dataset
titanic = sns.load_dataset('titanic')

# 1. Correlation matrix
print("=" * 60)
print("CORRELATION MATRIX")
print("=" * 60)

# Select numeric columns
numeric_cols = ['age', 'fare', 'sibsp', 'parch']
corr_matrix = titanic[numeric_cols].corr()
print(corr_matrix)

# 2. Correlation with a specific column
print("\n" + "=" * 60)
print("CORRELATION WITH FARE")
print("=" * 60)
print(titanic[numeric_cols].corrwith(titanic['fare']))

# 3. Visualising correlation with heatmap
plt.figure(figsize=(8, 6))
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', fmt='.2f',
            linewidths=0.5, square=True)
plt.title('Correlation Heatmap - Titanic Numeric Variables')
plt.show()

# 4. Pairplot with correlations
sns.pairplot(titanic[numeric_cols])
plt.suptitle('Pairplot of Numeric Variables', y=1.02)
plt.show()

# 5. Spearman correlation (rank-based)
print("\n" + "=" * 60)
print("SPEARMAN CORRELATION")
print("=" * 60)
print(titanic[numeric_cols].corr(method='spearman'))

# 6. Identifying high correlations
print("\n" + "=" * 60)
print("HIGH CORRELATIONS (> 0.5)")
print("=" * 60)
high_corr = corr_matrix[abs(corr_matrix) > 0.5]
print(high_corr)

# 7. Correlation with a categorical variable (using ANOVA or point-biserial)
# For binary categorical variables (like 'survived'), we can use point-biserial correlation
from scipy.stats import pointbiserialr

print("\n" + "=" * 60)
print("CORRELATION WITH SURVIVAL")
print("=" * 60)
for col in numeric_cols:
    corr, p_value = pointbiserialr(titanic['survived'], titanic[col].dropna())
    print(f"  {col}: r={corr:.3f}, p-value={p_value:.4f}")
```

**Correlation in a Real Dataset**:

```python
# Using the 'tips' dataset
tips = sns.load_dataset('tips')
numeric_cols = ['total_bill', 'tip', 'size']

print("\n" + "=" * 60)
print("TIPS DATASET CORRELATION")
print("=" * 60)
print(tips[numeric_cols].corr())

# Visualise
plt.figure(figsize=(6, 5))
sns.heatmap(tips[numeric_cols].corr(), annot=True, cmap='RdBu_r', fmt='.2f')
plt.title('Tips Dataset Correlation')
plt.show()
```

**Scatter Plots for Correlation**:

```python
fig, axes = plt.subplots(1, 3, figsize=(15, 4))

# Positive correlation (simulated)
np.random.seed(42)
x = np.random.randn(100)
y_pos = x + np.random.randn(100) * 0.3
axes[0].scatter(x, y_pos, alpha=0.6)
axes[0].set_title(f'Positive Correlation (r={np.corrcoef(x, y_pos)[0,1]:.2f})')
axes[0].set_xlabel('X')
axes[0].set_ylabel('Y')

# Negative correlation
y_neg = -x + np.random.randn(100) * 0.3
axes[1].scatter(x, y_neg, alpha=0.6)
axes[1].set_title(f'Negative Correlation (r={np.corrcoef(x, y_neg)[0,1]:.2f})')
axes[1].set_xlabel('X')
axes[1].set_ylabel('Y')

# No correlation
y_no = np.random.randn(100)
axes[2].scatter(x, y_no, alpha=0.6)
axes[2].set_title(f'No Correlation (r={np.corrcoef(x, y_no)[0,1]:.2f})')
axes[2].set_xlabel('X')
axes[2].set_ylabel('Y')

plt.tight_layout()
plt.show()
```

---

### Practical Examples

- **Example 1**: A sales analyst finds a strong positive correlation between advertising spend and sales.
- **Example 2**: A data scientist finds high correlation between two features and decides to drop one.
- **Example 3**: A financial analyst finds a negative correlation between interest rates and stock prices.

---

### Hands-on Coding Exercises

**Exercise 7.5** – Correlation analysis:
```python
# 1. Load the 'iris' dataset
# 2. Calculate the correlation matrix for numeric columns
# 3. Visualise with a heatmap
# 4. Identify the highest positive correlation
# 5. Identify the highest negative correlation
# 6. Create pairplots
# 7. Print all results
```

**Exercise 7.6** – Correlation interpretation:
```python
# 1. Load the 'penguins' dataset
# 2. Calculate correlations between all numeric columns
# 3. Interpret the strongest positive correlation
# 4. Interpret the strongest negative correlation
# 5. Explain what these correlations mean in business terms
```

---

### Mini Quiz

1. What does a correlation coefficient of 0.8 indicate?
2. What is the difference between Pearson and Spearman correlation?
3. How do you visualise a correlation matrix?
4. What is multicollinearity?
5. Does correlation imply causation?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Confusing correlation with causation | Correlation ≠ Causation |
| Using Pearson for non-linear relationships | Use Spearman for non-linear/monotonic |
| Ignoring outliers – they can distort correlation | Check outliers before calculating correlation |
| Not visualising relationships | Always visualise with scatter plots |

---

### Interview Questions

1. **What is the difference between Pearson and Spearman correlation?**  
   *Answer*: Pearson measures linear relationships and is sensitive to outliers. Spearman measures monotonic relationships using ranks and is more robust.

2. **How do you interpret a correlation coefficient?**  
   *Answer*: A coefficient close to +1 indicates a strong positive relationship, close to -1 indicates a strong negative relationship, and close to 0 indicates no linear relationship.

3. **Why is it important to check for correlation in data?**  
   *Answer*: To identify redundant features, understand relationships, and avoid multicollinearity in models.

---

### Assignment and Mini Project

**Assignment 7.3** – Correlation analysis:
```python
# 1. Load the 'penguins' dataset
# 2. Calculate the correlation matrix for numeric columns
# 3. Create a heatmap with annotations
# 4. Identify the strongest positive and negative correlations
# 5. Create scatter plots for the strongest positive and negative correlations
# 6. Write a brief interpretation
```

**Mini Project** – Correlation Explorer:
Create a program that:
1. Loads a dataset with at least 5 numeric columns.
2. Calculates the correlation matrix.
3. Creates a heatmap with annotations.
4. Identifies the top 3 strongest positive correlations.
5. Identifies the top 3 strongest negative correlations.
6. Creates scatter plots for each of these pairs.
7. Saves the heatmap and scatter plots.
8. Generates a summary report.

---

### Summary and Revision Notes

- Correlation measures the strength and direction of a linear relationship.
- Pearson: linear, Spearman: monotonic.
- `df.corr()` for correlation matrix.
- `sns.heatmap()` for visualisation.
- Values: +1 (perfect positive), -1 (perfect negative), 0 (none).
- Correlation ≠ causation.
- Always visualise with scatter plots.

---

## Lesson 7.4 – Outlier Detection

### Concept Explanation

**Outliers** are data points that differ significantly from other observations. They can be caused by errors, variability, or genuine extreme values.

**Why detect outliers**:
- Outliers can skew statistical measures.
- Outliers can negatively affect machine learning models.
- Outliers may represent important events (fraud, anomalies).

**Detection methods**:

1. **Z-score method**: Data points with z-score > 3 or < -3 are outliers.
   - `z = (x - mean) / std`

2. **IQR method**: Points beyond Q1 - 1.5*IQR or Q3 + 1.5*IQR.
   - IQR = Q3 - Q1
   - Lower bound = Q1 - 1.5 * IQR
   - Upper bound = Q3 + 1.5 * IQR

3. **Visual methods**: Box plots, scatter plots.

4. **Statistical tests**: Grubbs' test, Dixon's test.

---

### Importance and Real-World Use Cases

- **Why it matters**: Outliers can distort analysis and lead to incorrect conclusions. Detecting and handling them is essential for reliable analysis.

- **Use cases**:
  - A **financial analyst** detects fraudulent transactions.
  - A **quality analyst** identifies defective products.
  - A **data scientist** cleans data before modelling.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
from scipy import stats

# Load dataset
titanic = sns.load_dataset('titanic')

# 1. Z-score method
print("=" * 60)
print("OUTLIER DETECTION - Z-SCORE METHOD")
print("=" * 60)

def detect_outliers_zscore(data, threshold=3):
    """Detect outliers using z-score."""
    z_scores = np.abs(stats.zscore(data.dropna()))
    outliers = np.where(z_scores > threshold)[0]
    return outliers, z_scores

# Apply to age column
age_data = titanic['age'].dropna()
outliers_z, z_scores = detect_outliers_zscore(age_data)

print(f"Age column:")
print(f"  Total values: {len(age_data)}")
print(f"  Outliers detected: {len(outliers_z)}")
print(f"  Outlier indices: {outliers_z[:10]}...")  # First 10
print(f"  Outlier values: {age_data.iloc[outliers_z].values[:10]}...")

# 2. IQR method
print("\n" + "=" * 60)
print("OUTLIER DETECTION - IQR METHOD")
print("=" * 60)

def detect_outliers_iqr(data):
    """Detect outliers using IQR method."""
    q1 = data.quantile(0.25)
    q3 = data.quantile(0.75)
    iqr = q3 - q1
    lower_bound = q1 - 1.5 * iqr
    upper_bound = q3 + 1.5 * iqr
    outliers = data[(data < lower_bound) | (data > upper_bound)]
    return outliers, lower_bound, upper_bound

outliers_iqr, lower, upper = detect_outliers_iqr(age_data)
print(f"Age column:")
print(f"  Q1: {age_data.quantile(0.25):.2f}")
print(f"  Q3: {age_data.quantile(0.75):.2f}")
print(f"  IQR: {age_data.quantile(0.75) - age_data.quantile(0.25):.2f}")
print(f"  Lower bound: {lower:.2f}")
print(f"  Upper bound: {upper:.2f}")
print(f"  Outliers: {len(outliers_iqr)}")
print(f"  Outlier values: {outliers_iqr.values[:10]}...")

# 3. Visual detection - Box plot
fig, axes = plt.subplots(1, 3, figsize=(15, 4))

# Box plot
sns.boxplot(x=titanic['age'], ax=axes[0])
axes[0].set_title('Box Plot - Age')

# Histogram with outlier markers
axes[1].hist(titanic['age'].dropna(), bins=20, color='skyblue', edgecolor='black')
axes[1].axvline(age_data.mean(), color='red', linestyle='--', label='Mean')
axes[1].axvline(age_data.median(), color='green', linestyle='--', label='Median')
axes[1].set_title('Histogram - Age')
axes[1].legend()

# KDE with outlier markers
sns.kdeplot(data=titanic['age'].dropna(), ax=axes[2], fill=True)
axes[2].axvline(age_data.mean(), color='red', linestyle='--', label='Mean')
axes[2].axvline(age_data.median(), color='green', linestyle='--', label='Median')
axes[2].set_title('KDE - Age')
axes[2].legend()

plt.tight_layout()
plt.show()

# 4. Outlier detection for multiple columns
print("\n" + "=" * 60)
print("OUTLIER DETECTION FOR MULTIPLE COLUMNS")
print("=" * 60)

numeric_cols = ['age', 'fare', 'sibsp', 'parch']
outlier_summary = {}

for col in numeric_cols:
    data = titanic[col].dropna()
    outliers, lower, upper = detect_outliers_iqr(data)
    outlier_summary[col] = {
        'total': len(data),
        'outliers': len(outliers),
        'percentage': (len(outliers) / len(data)) * 100,
        'lower': lower,
        'upper': upper
    }

for col, stats in outlier_summary.items():
    print(f"\n{col}:")
    print(f"  Total: {stats['total']}")
    print(f"  Outliers: {stats['outliers']} ({stats['percentage']:.1f}%)")
    print(f"  Range: [{stats['lower']:.2f}, {stats['upper']:.2f}]")

# 5. Scatter plot for outlier visualization
plt.figure(figsize=(8, 6))
plt.scatter(titanic['age'], titanic['fare'], alpha=0.5)
plt.xlabel('Age')
plt.ylabel('Fare')
plt.title('Scatter Plot: Age vs Fare')
plt.show()

# 6. Handling outliers - Capping
print("\n" + "=" * 60)
print("OUTLIER HANDLING - CAPPPING")
print("=" * 60)

def cap_outliers(data):
    """Cap outliers to the upper and lower bounds."""
    q1 = data.quantile(0.25)
    q3 = data.quantile(0.75)
    iqr = q3 - q1
    lower = q1 - 1.5 * iqr
    upper = q3 + 1.5 * iqr
    return data.clip(lower=lower, upper=upper)

age_capped = cap_outliers(age_data)
print(f"Original age range: [{age_data.min():.2f}, {age_data.max():.2f}]")
print(f"Capped age range: [{age_capped.min():.2f}, {age_capped.max():.2f}]")
print(f"Original outliers: {len(detect_outliers_iqr(age_data)[0])}")
print(f"Capped outliers: {len(detect_outliers_iqr(age_capped)[0])}")
```

---

### Practical Examples

- **Example 1**: A quality analyst uses IQR to detect defective products.
- **Example 2**: A financial analyst uses z-score to identify unusual transactions.
- **Example 3**: A data scientist caps outliers before training a model.

---

### Hands-on Coding Exercises

**Exercise 7.7** – Outlier detection:
```python
# 1. Load the 'tips' dataset
# 2. Detect outliers in 'total_bill' using z-score
# 3. Detect outliers in 'total_bill' using IQR
# 4. Create a box plot
# 5. Create a histogram with outlier markers
# 6. Print the outlier values
# 7. Cap the outliers and show the new range
```

**Exercise 7.8** – Outlier analysis:
```python
# 1. Load the 'penguins' dataset
# 2. For each numeric column, detect outliers using IQR
# 3. Count the number of outliers in each column
# 4. Create box plots for all numeric columns
# 5. Decide on a strategy for handling outliers
```

---

### Mini Quiz

1. What is an outlier?
2. How does the IQR method detect outliers?
3. What is the z-score method?
4. Why is it important to detect outliers?
5. What is the difference between capping and removing outliers?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Removing outliers without investigation | Investigate outliers before removing |
| Using the wrong method for the data | Choose the right method based on distribution |
| Not documenting outlier handling | Document all decisions |
| Ignoring outliers in analysis | Outliers can provide valuable insights |

---

### Interview Questions

1. **What are outliers and why are they important?**  
   *Answer*: Outliers are data points that differ significantly from other observations. They are important because they can skew analysis and affect model performance.

2. **How do you detect outliers in a dataset?**  
   *Answer*: Using z-score (>3 or <-3), IQR (points beyond Q1 - 1.5*IQR or Q3 + 1.5*IQR), or visual methods like box plots.

3. **How do you handle outliers?**  
   *Answer*: Options include removing them, capping them (winsorising), transforming the data, or keeping them if they are valid.

---

### Assignment and Mini Project

**Assignment 7.4** – Outlier detection report:
```python
# 1. Load the 'titanic' dataset
# 2. For each numeric column, detect outliers using:
#    - Z-score method
#    - IQR method
# 3. Compare the results of both methods
# 4. Create visualisations (box plots, histograms)
# 5. Propose a handling strategy for each column
# 6. Write a summary report
```

**Mini Project** – Outlier Analysis Tool:
Create a program that:
1. Loads a dataset.
2. For each numeric column, detects outliers using both z-score and IQR methods.
3. Compares the two methods.
4. Creates box plots and histograms for outlier visualisation.
5. Applies capping to the outliers.
6. Generates a report showing:
   - Number of outliers before and after capping.
   - Range before and after capping.
   - The outlier values.

---

### Summary and Revision Notes

- Outliers are extreme values that differ from other observations.
- Detection methods: z-score (>3 or <-3), IQR (Q1 - 1.5*IQR, Q3 + 1.5*IQR).
- Visual detection: box plots, scatter plots, histograms.
- Handling: remove, cap (winsorise), transform, or keep.
- Always investigate outliers before making decisions.

---

## Lesson 7.5 – Missing Value Analysis

### Concept Explanation

**Missing values** are a common issue in real-world datasets. They can occur for various reasons: data entry errors, system failures, or genuine missing information.

**Types of missing data**:
1. **MCAR (Missing Completely at Random)**: The missingness is unrelated to any observed or unobserved data.
2. **MAR (Missing at Random)**: The missingness is related to observed data but not the missing value itself.
3. **MNAR (Missing Not at Random)**: The missingness is related to the missing value itself.

**Detection**:
- `df.isnull().sum()` – count missing values per column.
- `df.isnull().mean()` – percentage of missing values.

**Handling strategies**:
1. **Remove**: Drop rows or columns with missing values.
   - `df.dropna()` – drop rows with any missing.
   - `df.dropna(axis=1)` – drop columns with any missing.
   - `df.dropna(thresh=n)` – drop rows with less than n non-null values.

2. **Impute (fill)**: Fill missing values with a value.
   - **Mean/Median/Mode**: `df.fillna(df.mean())`.
   - **Forward/Backward fill**: `df.fillna(method='ffill')`.
   - **Constant**: `df.fillna(0)` or `df.fillna('Unknown')`.
   - **Interpolation**: `df.interpolate()`.
   - **Regression**: Use a model to predict missing values.

3. **Flag**: Create a flag column indicating which values were missing.

---

### Importance and Real-World Use Cases

- **Why it matters**: Missing values can bias analysis and affect model performance. Understanding and handling them is essential for reliable results.

- **Use cases**:
  - A **data analyst** identifies missing customer information and decides to impute it.
  - A **data scientist** removes rows with missing target values.
  - A **quality analyst** investigates why data is missing.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

# Load dataset
titanic = sns.load_dataset('titanic')

# 1. Missing value detection
print("=" * 60)
print("MISSING VALUE ANALYSIS")
print("=" * 60)

# Count missing values
missing_count = titanic.isnull().sum()
print("Missing values per column:")
print(missing_count)

# Percentage of missing values
missing_pct = (titanic.isnull().sum() / len(titanic)) * 100
print("\nPercentage of missing values:")
print(missing_pct)

# Columns with missing values
cols_with_missing = missing_pct[missing_pct > 0].index.tolist()
print(f"\nColumns with missing values: {cols_with_missing}")

# 2. Visualise missing values
plt.figure(figsize=(10, 6))
sns.heatmap(titanic[cols_with_missing].isnull(), cbar=False, yticklabels=False)
plt.title('Missing Values Heatmap')
plt.show()

# 3. Missing value analysis by column
print("\n" + "=" * 60)
print("DETAILED MISSING VALUE ANALYSIS")
print("=" * 60)

for col in cols_with_missing:
    null_count = titanic[col].isnull().sum()
    null_pct = (null_count / len(titanic)) * 100
    print(f"\n{col}:")
    print(f"  Missing: {null_count} ({null_pct:.1f}%)")
    
    # Check if missingness is related to another column
    if col == 'age':
        # Check if age missingness is related to survival
        age_missing = titanic['age'].isnull()
        print(f"  Survival rate when age is present: {titanic.loc[~age_missing, 'survived'].mean():.2f}")
        print(f"  Survival rate when age is missing: {titanic.loc[age_missing, 'survived'].mean():.2f}")

# 4. Handling missing values - Drop
print("\n" + "=" * 60)
print("HANDLING MISSING VALUES")
print("=" * 60)

# Drop rows with missing age
df_dropped = titanic.dropna(subset=['age'])
print(f"Rows before dropping: {len(titanic)}")
print(f"Rows after dropping age missing: {len(df_dropped)}")

# Drop columns with high missingness
cols_to_drop = ['deck']  # 'deck' has high missingness
df_dropped_cols = titanic.drop(columns=cols_to_drop)
print(f"Columns before dropping: {len(titanic.columns)}")
print(f"Columns after dropping: {len(df_dropped_cols.columns)}")

# 5. Imputation strategies
print("\n" + "=" * 60)
print("IMPUTATION STRATEGIES")
print("=" * 60)

# Mean imputation for age
age_mean = titanic['age'].mean()
titanic_age_mean = titanic['age'].fillna(age_mean)
print(f"Age - Mean imputation: {age_mean:.2f}")

# Median imputation for age
age_median = titanic['age'].median()
titanic_age_median = titanic['age'].fillna(age_median)
print(f"Age - Median imputation: {age_median:.2f}")

# Mode imputation for embarked
embarked_mode = titanic['embarked'].mode()[0]
titanic_embarked_mode = titanic['embarked'].fillna(embarked_mode)
print(f"Embarked - Mode imputation: {embarked_mode}")

# Forward fill for age (by class)
titanic_sorted = titanic.sort_values(['class', 'age'])
titanic_age_ffill = titanic_sorted['age'].fillna(method='ffill')
print(f"Age - Forward fill: Used")

# 6. Multiple imputation comparison
print("\n" + "=" * 60)
print("COMPARISON OF IMPUTATION METHODS")
print("=" * 60)

# Original statistics
original_mean = titanic['age'].mean()
original_std = titanic['age'].std()
original_count = titanic['age'].count()

# After mean imputation
mean_imputed = titanic['age'].fillna(age_mean)
mean_imputed_mean = mean_imputed.mean()
mean_imputed_std = mean_imputed.std()

# After median imputation
median_imputed = titanic['age'].fillna(age_median)
median_imputed_mean = median_imputed.mean()
median_imputed_std = median_imputed.std()

print(f"Original: Mean={original_mean:.2f}, Std={original_std:.2f}, n={original_count}")
print(f"Mean imputation: Mean={mean_imputed_mean:.2f}, Std={mean_imputed_std:.2f}")
print(f"Median imputation: Mean={median_imputed_mean:.2f}, Std={median_imputed_std:.2f}")

# 7. Create a flag for missing values
titanic['age_missing_flag'] = titanic['age'].isnull().astype(int)
print("\nCreated age_missing_flag column:")
print(titanic[['age', 'age_missing_flag']].head())
```

---

### Practical Examples

- **Example 1**: A customer dataset has missing age values. The analyst imputes the median age.
- **Example 2**: A sales dataset has missing values in a column. The analyst decides to drop the column.
- **Example 3**: A survey dataset has missing responses. The analyst creates a flag for missing values.

---

### Hands-on Coding Exercises

**Exercise 7.9** – Missing value analysis:
```python
# 1. Load the 'penguins' dataset
# 2. Identify columns with missing values
# 3. Count and calculate the percentage of missing values
# 4. Visualise missing values
# 5. Try different imputation strategies:
#    - Mean imputation for 'bill_length_mm'
#    - Median imputation for 'bill_depth_mm'
#    - Mode imputation for 'sex'
#    - Forward fill for any column
# 6. Compare the results
```

**Exercise 7.10** – Missing value handling:
```python
# 1. Load the 'titanic' dataset
# 2. Handle missing 'age' using median imputation
# 3. Handle missing 'embarked' using mode imputation
# 4. Drop the 'deck' column
# 5. Create a flag for missing 'age'
# 6. Show the before and after summary
```

---

### Mini Quiz

1. What are the three types of missing data?
2. How do you check for missing values in a DataFrame?
3. What is the difference between dropping and imputing missing values?
4. What is mean imputation?
5. Why would you create a flag for missing values?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Removing all rows with missing values | Only remove if missingness is minimal |
| Using mean imputation for skewed data | Use median for skewed data |
| Not investigating why data is missing | Understand the reason for missingness |
| Imputing without validation | Validate imputation methods |

---

### Interview Questions

1. **How do you handle missing values in a dataset?**  
   *Answer*: First, I identify missing values using `isnull().sum()`. Then I decide on a strategy: remove rows if missingness is low, impute with mean/median/mode, use forward fill, or create a flag column.

2. **What is the difference between MCAR, MAR, and MNAR?**  
   *Answer*: MCAR: missingness is completely random. MAR: missingness is related to observed data. MNAR: missingness is related to the missing value itself.

3. **When would you use mean imputation vs median imputation?**  
   *Answer*: Use mean imputation for symmetric distributions and median imputation for skewed distributions.

---

### Assignment and Mini Project

**Assignment 7.5** – Missing value report:
```python
# 1. Load the 'titanic' dataset
# 2. Create a comprehensive missing value report:
#    - Columns with missing values
#    - Count and percentage of missing values
#    - Visualisation of missing values
# 3. For each column with missing values, propose a handling strategy
# 4. Implement the strategies
# 5. Show before and after statistics
```

**Mini Project** – Missing Value Handler:
Create a program that:
1. Loads a dataset.
2. Identifies missing values.
3. Provides options to:
   - Drop rows with missing values.
   - Drop columns with missing values.
   - Impute with mean/median/mode.
   - Forward/backward fill.
   - Interpolate.
4. Shows before and after statistics.
5. Creates a summary report.

---

### Summary and Revision Notes

- Missing values are common in real-world data.
- Types: MCAR, MAR, MNAR.
- Detection: `df.isnull().sum()` and `df.isnull().mean()`.
- Handling: drop, impute (mean, median, mode, forward fill, interpolation), or flag.
- Always investigate missing values before handling.

---

## Lesson 7.6 – Feature Understanding

### Concept Explanation

**Feature understanding** is about deeply understanding each variable in your dataset – what it represents, how it is distributed, and how it relates to other variables and the target.

**Key aspects**:
1. **Meaning**: What does the feature represent in the real world?
2. **Distribution**: How is it distributed? Normal, skewed, uniform?
3. **Range**: What is the range of values?
4. **Data type**: Numeric, categorical, date, text?
5. **Relationship with target**: How does it relate to the target variable?
6. **Relationship with other features**: Correlations and interactions.

**Tools**:
- `df.describe()` – summary statistics.
- `df['col'].value_counts()` – categorical counts.
- `df['col'].hist()` – distribution.
- `sns.boxplot()` – spread and outliers.
- `sns.scatterplot()` – relationships.
- `sns.heatmap()` – correlations.

**Feature categories**:
- **Numeric**: Continuous or discrete.
- **Categorical**: Nominal or ordinal.
- **Date/Time**: Dates and time stamps.
- **Text**: Free text (needs NLP).
- **Binary**: Two categories.

---

### Importance and Real-World Use Cases

- **Why it matters**: Understanding features is essential for:
  - Choosing the right analysis or model.
  - Engineering new features.
  - Interpreting results.
  - Explaining insights to stakeholders.

- **Use cases**:
  - A **data scientist** understands each feature to choose the right preprocessing steps.
  - A **business analyst** explains feature meanings to stakeholders.
  - A **product manager** uses feature understanding to prioritise data collection.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

# Load dataset
titanic = sns.load_dataset('titanic')

print("=" * 60)
print("FEATURE UNDERSTANDING")
print("=" * 60)

# 1. Overview of all features
print("Feature overview:\n")
for col in titanic.columns:
    dtype = titanic[col].dtype
    unique = titanic[col].nunique()
    nulls = titanic[col].isnull().sum()
    null_pct = (nulls / len(titanic)) * 100
    sample = titanic[col].dropna().iloc[0] if nulls < len(titanic) else 'N/A'
    print(f"{col:20} | {str(dtype):12} | Unique: {unique:5} | Nulls: {nulls:4} ({null_pct:.1f}%) | Sample: {sample}")

# 2. Numeric features
print("\n" + "=" * 60)
print("NUMERIC FEATURES")
print("=" * 60)

numeric_cols = ['age', 'fare', 'sibsp', 'parch']
for col in numeric_cols:
    data = titanic[col].dropna()
    print(f"\n{col}:")
    print(f"  Mean: {data.mean():.2f}")
    print(f"  Median: {data.median():.2f}")
    print(f"  Std: {data.std():.2f}")
    print(f"  Skew: {data.skew():.2f}")
    print(f"  Min: {data.min():.2f}")
    print(f"  Max: {data.max():.2f}")
    print(f"  25th: {data.quantile(0.25):.2f}")
    print(f"  75th: {data.quantile(0.75):.2f}")

# 3. Categorical features
print("\n" + "=" * 60)
print("CATEGORICAL FEATURES")
print("=" * 60)

cat_cols = ['sex', 'class', 'embark_town', 'who', 'adult_male']
for col in cat_cols:
    print(f"\n{col}:")
    print(f"  Unique values: {titanic[col].nunique()}")
    print(titanic[col].value_counts())

# 4. Relationship with target (survived)
print("\n" + "=" * 60)
print("RELATIONSHIP WITH TARGET (SURVIVED)")
print("=" * 60)

# Numeric features vs survival
for col in numeric_cols:
    print(f"\n{col} vs survived:")
    print(titanic.groupby('survived')[col].describe())

# Categorical features vs survival
for col in cat_cols:
    print(f"\n{col} vs survived:")
    print(pd.crosstab(titanic[col], titanic['survived'], normalize='index'))

# 5. Visual feature understanding
fig, axes = plt.subplots(2, 3, figsize=(15, 10))

# Age distribution
sns.histplot(data=titanic, x='age', hue='survived', kde=True, ax=axes[0, 0])
axes[0, 0].set_title('Age Distribution by Survival')

# Fare distribution
sns.histplot(data=titanic, x='fare', hue='survived', kde=True, ax=axes[0, 1])
axes[0, 1].set_title('Fare Distribution by Survival')

# Class vs survival
sns.barplot(data=titanic, x='class', y='survived', ax=axes[0, 2])
axes[0, 2].set_title('Survival Rate by Class')

# Sex vs survival
sns.barplot(data=titanic, x='sex', y='survived', ax=axes[1, 0])
axes[1, 0].set_title('Survival Rate by Sex')

# Age vs Fare (coloured by survival)
sns.scatterplot(data=titanic, x='age', y='fare', hue='survived', alpha=0.6, ax=axes[1, 1])
axes[1, 1].set_title('Age vs Fare (Coloured by Survival)')

# Correlation heatmap for numeric features
corr = titanic[numeric_cols + ['survived']].corr()
sns.heatmap(corr, annot=True, cmap='coolwarm', fmt='.2f', ax=axes[1, 2])
axes[1, 2].set_title('Correlation Heatmap')

plt.tight_layout()
plt.show()
```

**Feature Understanding for Business**:

```python
print("\n" + "=" * 60)
print("BUSINESS INSIGHTS FROM FEATURE UNDERSTANDING")
print("=" * 60)

# Key insights
print("\n1. Survival rate by passenger class:")
print(titanic.groupby('class')['survived'].mean())

print("\n2. Survival rate by sex:")
print(titanic.groupby('sex')['survived'].mean())

print("\n3. Average age by survival:")
print(titanic.groupby('survived')['age'].mean())

print("\n4. Average fare by survival:")
print(titanic.groupby('survived')['fare'].mean())

print("\n5. Most common embarkation town:")
print(titanic['embark_town'].value_counts().iloc[0])
```

---

### Practical Examples

- **Example 1**: A data scientist explores the 'penguins' dataset to understand which features separate species.
- **Example 2**: A business analyst explores customer data to identify key purchase drivers.
- **Example 3**: A product manager explores user data to understand feature usage patterns.

---

### Hands-on Coding Exercises

**Exercise 7.11** – Feature exploration:
```python
# 1. Load the 'penguins' dataset
# 2. For each numeric feature:
#    - Print summary statistics
#    - Create histograms
#    - Create box plots
# 3. For each categorical feature:
#    - Print value counts
#    - Create bar plots
# 4. Analyse relationships between features
# 5. Analyse relationship with target (species)
```

**Exercise 7.12** – Feature summary:
```python
# 1. Load any dataset
# 2. For each column, create a summary including:
#    - Feature name
#    - Data type
#    - Number of unique values
#    - Missing values count and percentage
#    - Key statistics (mean, median, mode, min, max)
#    - Brief description of what the feature represents
# 3. Organise the summary in a table
```

---

### Mini Quiz

1. What are the main categories of features?
2. Why is it important to understand features?
3. How do you check the relationship between a feature and the target?
4. What is the difference between a nominal and ordinal categorical feature?
5. How do you identify which features are most important?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Ignoring feature meanings | Always understand what the feature represents |
| Not checking relationships | Analyse feature-target relationships |
| Treating all features equally | Prioritise features based on importance |
| Not considering interactions | Look for feature interactions |

---

### Interview Questions

1. **How do you understand the features in a new dataset?**  
   *Answer*: I start by examining the data types, distributions, and summary statistics. Then I look at relationships between features and the target variable using visualisations and correlation analysis.

2. **What is the difference between a categorical and a numeric feature?**  
   *Answer*: Categorical features represent categories or groups (e.g., gender, class). Numeric features represent quantities (e.g., age, salary).

3. **How do you identify the most important features?**  
   *Answer*: Using correlation with the target, feature importance from models, or domain knowledge.

---

### Assignment and Mini Project

**Assignment 7.6** – Feature understanding report:
```python
# 1. Load the 'titanic' dataset
# 2. Create a comprehensive feature understanding report:
#    - For each feature: type, unique values, missing values, summary statistics
#    - Relationship with target (survived)
#    - Key insights and interpretations
# 3. Include visualisations
# 4. Write a summary of the most important features
```

**Mini Project** – Feature Explorer Dashboard:
Create a program that:
1. Loads a dataset.
2. Generates a comprehensive feature exploration dashboard with:
   - Summary of all features.
   - Distribution plots for numeric features.
   - Count plots for categorical features.
   - Feature-target relationship plots.
   - Correlation heatmap.
   - Key insights.
3. Saves the dashboard as a high-resolution image.

---

### Summary and Revision Notes

- Feature understanding is essential for analysis and modelling.
- Understand the meaning, type, distribution, and relationships of each feature.
- Use descriptive statistics and visualisations.
- Analyse feature-target relationships.
- Document key insights.

---

## Lesson 7.7 – Business Insights

### Concept Explanation

**Business insights** are the actionable conclusions derived from data analysis. They translate technical findings into business language and recommendations.

**The bridge from data to business**:
1. **Data**: Raw numbers and facts.
2. **Information**: Organised and processed data.
3. **Insights**: Understanding and interpretation of information.
4. **Action**: Decisions and recommendations based on insights.

**Key questions for generating insights**:
- What are the key drivers of success?
- What are the main problems or opportunities?
- What patterns or trends are emerging?
- What are the outliers and what do they mean?
- What actions should be taken?

**Insight categories**:
- **Descriptive**: What happened? (e.g., Sales increased by 15%).
- **Diagnostic**: Why did it happen? (e.g., Sales increased due to a new marketing campaign).
- **Predictive**: What will happen? (e.g., Sales are projected to grow by 10% next quarter).
- **Prescriptive**: What should we do? (e.g., Invest more in the marketing channel).

---

### Importance and Real-World Use Cases

- **Why it matters**: Insights drive action. Without clear, actionable insights, data analysis is just an academic exercise.

- **Use cases**:
  - A **sales analyst** identifies that a specific region is underperforming and recommends a targeted marketing campaign.
  - A **product manager** discovers that a specific customer segment has high churn and recommends a retention program.
  - A **marketing analyst** finds that a campaign performed best on social media and recommends shifting budget.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

# Load dataset
titanic = sns.load_dataset('titanic')

print("=" * 70)
print("BUSINESS INSIGHTS FROM TITANIC DATA")
print("=" * 70)

# 1. Key metrics
print("\n1. OVERALL SURVIVAL RATE")
print("-" * 40)
survival_rate = titanic['survived'].mean() * 100
print(f"Overall survival rate: {survival_rate:.1f}%")

# 2. Insights by passenger class
print("\n2. SURVIVAL BY PASSENGER CLASS")
print("-" * 40)
class_survival = titanic.groupby('class')['survived'].mean() * 100
print(class_survival)
print(f"\nInsight: First-class passengers had a {class_survival['First']:.1f}% survival rate, "
      f"while third-class passengers had only {class_survival['Third']:.1f}%.")

# 3. Insights by sex
print("\n3. SURVIVAL BY SEX")
print("-" * 40)
sex_survival = titanic.groupby('sex')['survived'].mean() * 100
print(sex_survival)
print(f"\nInsight: Women had a {sex_survival['female']:.1f}% survival rate, "
      f"while men had only {sex_survival['male']:.1f}%.")

# 4. Insights by fare
print("\n4. SURVIVAL BY FARE")
print("-" * 40)
fare_by_survival = titanic.groupby('survived')['fare'].mean()
print(f"Average fare of survivors: ${fare_by_survival[1]:.2f}")
print(f"Average fare of non-survivors: ${fare_by_survival[0]:.2f}")
print(f"\nInsight: Survivors paid {fare_by_survival[1] - fare_by_survival[0]:.2f} more on average.")

# 5. Insights by age
print("\n5. SURVIVAL BY AGE")
print("-" * 40)
titanic['age_group'] = pd.cut(titanic['age'], bins=[0, 10, 20, 30, 40, 50, 60, 80],
                              labels=['0-10', '11-20', '21-30', '31-40', '41-50', '51-60', '61-80'])
age_survival = titanic.groupby('age_group')['survived'].mean() * 100
print(age_survival)
print(f"\nInsight: Children (0-10) had a {age_survival['0-10']:.1f}% survival rate, "
      f"the highest among all age groups.")

# 6. Insights by embarkation
print("\n6. SURVIVAL BY EMBARKATION")
print("-" * 40)
embark_survival = titanic.groupby('embark_town')['survived'].mean() * 100
print(embark_survival)
print(f"\nInsight: Passengers from Cherbourg had the highest survival rate "
      f"({embark_survival['Cherbourg']:.1f}%), while those from Southampton "
      f"had the lowest ({embark_survival['Southampton']:.1f}%).")

# 7. Key drivers
print("\n7. KEY DRIVERS OF SURVIVAL")
print("-" * 40)
# Correlation with survival
numeric_cols = ['age', 'fare', 'sibsp', 'parch']
corr_with_survival = titanic[numeric_cols + ['survived']].corr()['survived'].sort_values(ascending=False)
print("Correlation with survival:")
print(corr_with_survival)

# 8. Combined insights
print("\n8. COMBINED INSIGHTS")
print("-" * 40)
# Survival by class and sex
class_sex_survival = titanic.groupby(['class', 'sex'])['survived'].mean() * 100
print("Survival by class and sex:")
print(class_sex_survival)

print("\nKey combined insights:")
print("- Women in first class had the highest survival rate.")
print("- Men in third class had the lowest survival rate.")

# 9. Recommendation
print("\n9. RECOMMENDATIONS")
print("-" * 40)
print("Based on the analysis of the Titanic data:")
print("1. Prioritise women and children in emergency situations.")
print("2. Ensure fair access to lifeboats regardless of class.")
print("3. Consider the role of class and fare in safety protocols.")
```

**Visualising Insights for Business**:

```python
fig, axes = plt.subplots(2, 2, figsize=(14, 10))

# Survival by class
sns.barplot(data=titanic, x='class', y='survived', ax=axes[0, 0])
axes[0, 0].set_title('Survival by Class', fontsize=14)
axes[0, 0].set_ylabel('Survival Rate')

# Survival by sex
sns.barplot(data=titanic, x='sex', y='survived', ax=axes[0, 1])
axes[0, 1].set_title('Survival by Sex', fontsize=14)
axes[0, 1].set_ylabel('Survival Rate')

# Survival by age group
sns.barplot(data=titanic, x='age_group', y='survived', ax=axes[1, 0])
axes[1, 0].set_title('Survival by Age Group', fontsize=14)
axes[1, 0].set_ylabel('Survival Rate')
axes[1, 0].tick_params(axis='x', rotation=45)

# Survival by class and sex
sns.barplot(data=titanic, x='class', y='survived', hue='sex', ax=axes[1, 1])
axes[1, 1].set_title('Survival by Class and Sex', fontsize=14)
axes[1, 1].set_ylabel('Survival Rate')

plt.tight_layout()
plt.show()
```

---

### Practical Examples

- **Example 1**: A retail analyst finds that online sales are growing faster than in-store sales. Recommendation: Invest more in the online channel.
- **Example 2**: A customer analyst finds that customers with a high satisfaction score have higher retention. Recommendation: Focus on improving customer satisfaction.

---

### Hands-on Coding Exercises

**Exercise 7.13** – Business insights generation:
```python
# 1. Load the 'tips' dataset
# 2. Analyse the relationship between day and total_bill
# 3. Analyse the relationship between time (Lunch/Dinner) and tip
# 4. Identify the key drivers of high tips
# 5. Generate at least 3 business insights
# 6. Write recommendations based on the insights
```

**Exercise 7.14** – Executive summary:
```python
# 1. Load the 'penguins' dataset
# 2. Analyse the differences between species
# 3. Identify the key features that separate species
# 4. Generate insights about each species
# 5. Write an executive summary for a non-technical audience
```

---

### Mini Quiz

1. What is the difference between a data insight and a business insight?
2. What are the four types of analytics (descriptive, diagnostic, predictive, prescriptive)?
3. Why is it important to translate insights into business language?
4. What is the purpose of recommendations in data analysis?
5. How do you ensure insights are actionable?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Presenting data without interpretation | Always interpret the data |
| Using technical jargon | Use business language |
| No actionable recommendations | Always provide recommendations |
| Ignoring the audience | Tailor insights to the audience |

---

### Interview Questions

1. **How do you translate data analysis into business insights?**  
   *Answer*: I interpret the findings in the context of the business problem, explain what the numbers mean, and provide actionable recommendations based on the analysis.

2. **What is the difference between descriptive and prescriptive analytics?**  
   *Answer*: Descriptive analytics tells you what happened. Prescriptive analytics tells you what to do about it.

3. **How do you ensure your insights are actionable?**  
   *Answer*: By providing specific recommendations and linking them to business outcomes.

---

### Assignment and Mini Project

**Assignment 7.7** – Business insights report:
```python
# 1. Load the 'titanic' dataset
# 2. Generate at least 5 business insights
# 3. Include visualisations that support each insight
# 4. Write an executive summary
# 5. Provide actionable recommendations
```

**Mini Project** – Insights Report Generator:
Create a program that:
1. Loads a dataset.
2. Automatically generates key insights:
   - Overall statistics.
   - Group comparisons.
   - Key drivers.
   - Outliers.
   - Trends.
3. Creates visualisations for each insight.
4. Generates a report with:
   - Executive summary.
   - Key insights with supporting visuals.
   - Recommendations.
   - Next steps.
5. Exports the report as a PDF (or a well-formatted text file).

---

### Summary and Revision Notes

- Insights translate data into actionable business recommendations.
- Types: descriptive, diagnostic, predictive, prescriptive.
- Use business language, not technical jargon.
- Always provide recommendations.
- Tailor insights to the audience.

---

## Lesson 7.8 – Data Storytelling

### Concept Explanation

**Data storytelling** is the art of communicating data insights in a compelling, narrative-driven way. It combines:
- **Data**: The facts and figures.
- **Narrative**: The story that connects the data to a message.
- **Visuals**: The charts and graphics that make the data accessible.

**Why storytelling matters**:
- Stories are memorable.
- Stories create emotional connections.
- Stories drive action.

**The storytelling framework**:
1. **Set the context**: What is the situation?
2. **Introduce the conflict**: What is the problem or opportunity?
3. **Show the analysis**: What does the data say?
4. **Provide resolution**: What should be done?

**Key elements**:
- **Know your audience**: Who are you speaking to?
- **Simplify**: Focus on the key message.
- **Use visuals**: Support the narrative with clear visuals.
- **Make it actionable**: What should the audience do next?

---

### Importance and Real-World Use Cases

- **Why it matters**: Even the best analysis is useless if it's not communicated effectively. Data storytelling bridges the gap between analysts and decision-makers.

- **Use cases**:
  - A **data analyst** presents quarterly sales results to the executive team.
  - A **data scientist** explains a new model to business stakeholders.
  - A **business analyst** presents findings to clients.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load dataset
titanic = sns.load_dataset('titanic')

print("=" * 70)
print("DATA STORY: THE TITANIC SURVIVAL ANALYSIS")
print("=" * 70)

# Part 1: Context
print("\n" + "=" * 70)
print("1. THE CONTEXT")
print("=" * 70)
print("The Titanic was a passenger liner that sank in 1912. "
      "Of the 2,224 passengers on board, approximately 1,500 died. "
      "Our analysis explores the key factors that influenced survival.")

# Part 2: The Conflict (Problem)
print("\n" + "=" * 70)
print("2. THE CONFLICT (WHAT HAPPENED)")
print("=" * 70)
survival_rate = titanic['survived'].mean() * 100
print(f"Only {survival_rate:.1f}% of passengers survived the tragedy.")
print("What factors determined who lived and who died?")

# Part 3: The Analysis
print("\n" + "=" * 70)
print("3. THE ANALYSIS (WHAT THE DATA TELLS US)")
print("=" * 70)

# 3.1 Class
print("\n3.1 Passenger Class")
print("-" * 40)
class_survival = titanic.groupby('class')['survived'].mean() * 100
for class_name, rate in class_survival.items():
    print(f"  {class_name} class: {rate:.1f}% survival")

# 3.2 Sex
print("\n3.2 Sex")
print("-" * 40)
sex_survival = titanic.groupby('sex')['survived'].mean() * 100
for sex, rate in sex_survival.items():
    print(f"  {sex}: {rate:.1f}% survival")

# 3.3 Age
print("\n3.3 Age")
print("-" * 40)
titanic['age_group'] = pd.cut(titanic['age'], bins=[0, 10, 20, 30, 40, 50, 60, 80],
                              labels=['0-10', '11-20', '21-30', '31-40', '41-50', '51-60', '61-80'])
age_survival = titanic.groupby('age_group')['survived'].mean() * 100
print("  Survival by age group:")
for age, rate in age_survival.items():
    if not pd.isna(rate):
        print(f"    {age}: {rate:.1f}%")

# 3.4 Combined
print("\n3.4 Combined Analysis")
print("-" * 40)
print("  Survival by class and sex:")
class_sex_survival = titanic.groupby(['class', 'sex'])['survived'].mean() * 100
for (cls, sex), rate in class_sex_survival.items():
    print(f"    {cls} class {sex}: {rate:.1f}%")

# Part 4: The Resolution
print("\n" + "=" * 70)
print("4. THE RESOLUTION (KEY INSIGHTS)")
print("=" * 70)
print("Based on our analysis, three key factors influenced survival:")
print("1. Class: First-class passengers had the highest survival rate.")
print("2. Sex: Women were much more likely to survive than men.")
print("3. Age: Children had the highest survival rate among all age groups.")
print("\nThe combination of these factors shows that the 'women and children first' "
      "policy was partially followed, but class was also a significant factor.")

# Part 5: Recommendations
print("\n" + "=" * 70)
print("5. RECOMMENDATIONS")
print("=" * 70)
print("While this analysis looks at historical data, the lessons are timeless:")
print("1. Clear safety protocols should prioritize the most vulnerable passengers.")
print("2. Fair access to safety resources is essential.")
print("3. Regular safety drills and training save lives.")

# Create the story visualisations
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
fig.suptitle('The Titanic Survival Story', fontsize=20, fontweight='bold')

# 1. Survival by class
sns.barplot(data=titanic, x='class', y='survived', ax=axes[0, 0], palette='Reds_r')
axes[0, 0].set_title('Survival by Passenger Class', fontsize=14)
axes[0, 0].set_ylabel('Survival Rate')
axes[0, 0].set_ylim(0, 1)

# 2. Survival by sex
sns.barplot(data=titanic, x='sex', y='survived', ax=axes[0, 1], palette='Blues_r')
axes[0, 1].set_title('Survival by Sex', fontsize=14)
axes[0, 1].set_ylabel('Survival Rate')
axes[0, 1].set_ylim(0, 1)

# 3. Survival by age group
age_survival_clean = age_survival.dropna()
ax = sns.barplot(x=age_survival_clean.index, y=age_survival_clean.values, ax=axes[1, 0], palette='Greens_r')
axes[1, 0].set_title('Survival by Age Group', fontsize=14)
axes[1, 0].set_ylabel('Survival Rate')
axes[1, 0].set_ylim(0, 1)

# 4. Survival by class and sex
sns.barplot(data=titanic, x='class', y='survived', hue='sex', ax=axes[1, 1])
axes[1, 1].set_title('Survival by Class and Sex', fontsize=14)
axes[1, 1].set_ylabel('Survival Rate')
axes[1, 1].set_ylim(0, 1)

plt.tight_layout()
plt.show()

print("\n" + "=" * 70)
print("DATA STORY COMPLETE")
print("=" * 70)
```

---

### Practical Examples

- **Example 1**: A sales analyst presents a quarterly sales story: "Sales are up 15%, driven by strong performance in the West region and the new product line."
- **Example 2**: A marketing analyst presents a campaign performance story: "The email campaign had a 25% open rate, exceeding our target of 20%."

---

### Hands-on Coding Exercises

**Exercise 7.15** – Data storytelling:
```python
# 1. Load the 'tips' dataset
# 2. Tell a story about the data:
#    - Set the context (what is the data about?)
#    - Explain the conflict (what question are we answering?)
#    - Show the analysis (what does the data say?)
#    - Provide resolution (what are the insights and recommendations?)
# 3. Support the story with visualisations
```

**Exercise 7.16** – Presentation preparation:
```python
# 1. Load the 'penguins' dataset
# 2. Prepare a 5-minute presentation:
#    - Introduction: context of the data
#    - Key insights: what did you find?
#    - Visuals: support each insight
#    - Recommendations: what should be done?
# 3. Write the script for the presentation
```

---

### Mini Quiz

1. What are the three components of data storytelling?
2. What is the purpose of setting the context in a data story?
3. Why is it important to have a clear conflict or question?
4. How do visuals support data storytelling?
5. What makes a data story effective?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Presenting too much data | Focus on the key message |
| Using technical jargon | Use clear, simple language |
| No clear narrative | Have a clear beginning, middle, and end |
| Ignoring the audience | Tailor the story to the audience |
| No call to action | Always end with a recommendation |

---

### Interview Questions

1. **What is data storytelling and why is it important?**  
   *Answer*: Data storytelling is the art of communicating data insights through a compelling narrative. It is important because it makes data memorable, creates emotional connections, and drives action.

2. **What are the key elements of a good data story?**  
   *Answer*: Context, conflict, analysis, and resolution. It should also have a clear audience, simple language, supporting visuals, and a call to action.

3. **How do you ensure your data story is effective?**  
   *Answer*: By knowing the audience, focusing on the key message, using clear visuals, simplifying the language, and providing actionable recommendations.

---

### Assignment and Mini Project

**Assignment 7.8** – Data storytelling:
```python
# 1. Load the 'titanic' dataset
# 2. Write a complete data story:
#    - Title
#    - Context (background)
#    - Problem/question
#    - Analysis (with visualisations)
#    - Insights
#    - Recommendations
# 3. Format the story as a presentation or report
```

**Mini Project** – Executive Presentation:
Create a complete data story presentation for any dataset:
1. Title slide with the story title.
2. Context slide: background and business problem.
3. Analysis slides: key insights with visualisations.
4. Conclusion slide: summary of insights.
5. Recommendation slide: actionable recommendations.
6. Appendix: supporting details.

---

### Summary and Revision Notes

- Data storytelling combines data, narrative, and visuals.
- Framework: Context → Conflict → Analysis → Resolution.
- Know your audience and use simple language.
- Support the story with clear visuals.
- Always end with actionable recommendations.

---

## Final Phase 7 Assessment

Now that you have completed all lessons, test your overall understanding.

### Self-Evaluation Checklist

-  I can explore and understand a new dataset.

-  I can calculate and interpret descriptive statistics.

-  I can perform and interpret correlation analysis.

-  I can detect and handle outliers.

-  I can analyse and handle missing values.

-  I can deeply understand each feature in a dataset.

-  I can generate business insights from data.

-  I can tell a compelling data story.


If you have completed all assignments and feel confident, you are ready for the **Final Capstone Project**!

---

### Answers to Mini Quizzes

**Lesson 7.1**: 1. Column names, data types, non-null counts, memory usage. 2. `df.shape`. 3. Summary statistics. 4. `df.sample()`. 5. To avoid mistakes and plan analysis.

**Lesson 7.2**: 1. Mean is average, median is middle value. 2. Spread/variability. 3. Q3 - Q1. 4. Right tail is longer. 5. To summarise data.

**Lesson 7.3**: 1. Strong positive correlation. 2. Pearson is linear, Spearman is monotonic. 3. Heatmap. 4. High correlation between predictors. 5. No, correlation does not imply causation.

**Lesson 7.4**: 1. Extreme data point. 2. Points beyond Q1 - 1.5*IQR or Q3 + 1.5*IQR. 3. Points with z-score > 3 or < -3. 4. To avoid skewing results. 5. Capping limits them, removing deletes them.

**Lesson 7.5**: 1. MCAR, MAR, MNAR. 2. `df.isnull().sum()`. 3. Dropping removes, imputing fills. 4. Filling with the average. 5. To track which values were missing.

**Lesson 7.6**: 1. Numeric, categorical, date, text, binary. 2. To choose the right analysis and interpret results. 3. Using correlation or group comparison. 4. Nominal has no order, ordinal has order. 5. Using correlation or feature importance.

**Lesson 7.7**: 1. Data insights are technical, business insights are actionable. 2. Descriptive, diagnostic, predictive, prescriptive. 3. To ensure understanding and action. 4. To guide next steps. 5. By providing specific, concrete recommendations.

**Lesson 7.8**: 1. Data, narrative, visuals. 2. To provide background. 3. To engage the audience. 4. By making data accessible. 5. When it's clear, memorable, and actionable.

---

**Congratulations!** You have completed Phase 7 of Python for Data Analytics. You now have a complete toolkit for exploring, understanding, and communicating data insights. Keep practising!

