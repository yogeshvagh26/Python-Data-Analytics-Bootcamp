# Phase 4: Pandas

Welcome to **Phase 4** – the most exciting phase of your Python for Data Analytics journey! If NumPy is the engine, **Pandas** is the steering wheel. Pandas is the library that makes data analysis in Python truly powerful, intuitive, and enjoyable.

Pandas stands for **"Panel Data"** – a term from econometrics for multidimensional structured data. It provides high-performance, easy-to-use data structures and tools for data manipulation and analysis. In fact, Pandas is so essential that it's hard to imagine data analytics in Python without it.

**What you'll learn in this phase:**
- The two core data structures: **Series** (1D) and **DataFrame** (2D).
- **Importing and exporting** data from CSV, Excel, JSON, and more.
- **Selecting, filtering, and sorting** data.
- **Grouping and aggregating** data with `groupby`.
- **Combining datasets** with `merge`, `join`, and `concat`.
- **Handling missing and duplicate** data.
- **Cleaning and transforming** data for analysis.
- **Pivot tables** and **MultiIndex** for advanced analysis.

By the end of this phase, you'll be able to handle real-world datasets with ease – cleaning, transforming, and analysing them like a pro.

Let's dive in!

---

## Lesson 4.1 – Introduction to Pandas

### Concept Explanation

**Pandas** is a fast, powerful, and flexible open-source data analysis and manipulation library for Python. It is built on top of NumPy and provides:

- **Data structures**: Series (1D) and DataFrame (2D) for handling structured data.
- **Data manipulation tools**: Filtering, grouping, joining, pivoting, and more.
- **I/O tools**: Read and write data from/to CSV, Excel, JSON, SQL, and many other formats.
- **Time series support**: Working with dates and times.

**Key features**:
- **Labeled data**: Unlike NumPy arrays, Pandas data structures have labeled axes (row and column names).
- **Missing data handling**: Built-in support for `NaN` (Not a Number).
- **Flexible reshaping**: Pivot, stack, unstack, and more.

**Installation**:
```bash
pip install pandas
```

**Importing Pandas**:
```python
import pandas as pd  # Standard alias
```

---

### Importance and Real-World Use Cases

- **Why it matters**: Pandas is the go-to library for data analysis in Python. It's used in virtually every data project – from small exploratory analyses to large-scale data pipelines.

- **Use cases**:
  - A **data analyst** loads a CSV file, cleans it, and creates summary reports.
  - A **data scientist** explores a dataset, engineers features, and prepares data for machine learning.
  - A **financial analyst** imports Excel files, merges them, and calculates KPIs.

---

### Step-by-Step Demonstration

**Your First Pandas Code**:

```python
import pandas as pd

# Create a simple DataFrame from a dictionary
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana'],
    'Age': [25, 30, 35, 40],
    'City': ['New York', 'London', 'Paris', 'Tokyo']
}

df = pd.DataFrame(data)
print(df)
print("\n")

# Basic info
print(df.info())
print("\n")

# Summary statistics
print(df.describe())
print("\n")

# First 2 rows
print("First 2 rows:")
print(df.head(2))
print("\n")

# Last 2 rows
print("Last 2 rows:")
print(df.tail(2))
```

**Loading Data from a CSV**:

```python
# Read CSV file (in practice, you'd use a real file path)
# df = pd.read_csv('sales_data.csv')

# For this example, create a sample DataFrame and save it
df.to_csv('sample_data.csv', index=False)

# Load it back
df_loaded = pd.read_csv('sample_data.csv')
print(df_loaded)
```

**Checking Your Data**:

```python
# Shape (rows, columns)
print(f"Shape: {df.shape}")

# Column names
print(f"Columns: {df.columns.tolist()}")

# Data types
print(f"Data types:\n{df.dtypes}")

# Quick summary of each column
print(df.describe(include='all'))
```

---

### Practical Examples

- **Example 1**: Loading a sales dataset and checking its structure.
- **Example 2**: Creating a DataFrame from a dictionary of customer data.
- **Example 3**: Saving a processed DataFrame to a CSV file.

---

### Hands-on Coding Exercises

**Exercise 4.1** – Create a DataFrame:
```python
# 1. Create a dictionary with the following data:
#    - Product: ['A', 'B', 'C', 'D', 'E']
#    - Sales: [100, 200, 150, 300, 250]
#    - Quantity: [10, 20, 15, 30, 25]
# 2. Convert it to a DataFrame
# 3. Print the DataFrame
# 4. Print the shape, columns, and data types
# 5. Print summary statistics
```

**Exercise 4.2** – Load and explore:
```python
# 1. Load the sample_data.csv file you created
# 2. Print the first 3 rows
# 3. Print the last 3 rows
# 4. Print information about the DataFrame
# 5. Print summary statistics
```

---

### Mini Quiz

1. What does Pandas stand for?
2. What is the standard import alias for Pandas?
3. What is the difference between a Series and a DataFrame?
4. What method do you use to read a CSV file?
5. What does `df.head()` do?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to import Pandas (`import pandas as pd`) | Always import at the top of your script |
| Not checking data types after loading | Use `df.dtypes` and `df.info()` |
| Not handling large files efficiently | Use `chunksize` or `nrows` parameters |
| Using `print(df)` for large DataFrames | Use `df.head()` or `df.sample()` |

---

### Interview Questions

1. **What is Pandas and why is it used in data analytics?**  
   *Answer*: Pandas is a Python library for data manipulation and analysis. It provides DataFrame and Series data structures, which are essential for handling structured data. It's used for cleaning, transforming, analyzing, and visualizing data.

2. **What are the two main data structures in Pandas?**  
   *Answer*: Series (1D labeled array) and DataFrame (2D labeled data structure with rows and columns).

3. **How do you read a CSV file into a Pandas DataFrame?**  
   *Answer*: Using `pd.read_csv('file_path.csv')`.

---

### Assignment and Mini Project

**Assignment 4.1** – DataFrame creation and exploration:
```python
# 1. Create a dictionary with columns: Student, Math, English, Science
# 2. Create a DataFrame
# 3. Print the DataFrame
# 4. Print the shape, columns, and data types
# 5. Print summary statistics for the numeric columns
# 6. Save the DataFrame to a CSV file
# 7. Load it back and verify it loaded correctly
```

**Mini Project** – Dataset Explorer:
Create a program that:
1. Creates a DataFrame with at least 5 columns (mix of text and numbers).
2. Adds at least 10 rows of data.
3. Saves it to a CSV file.
4. Loads the CSV file.
5. Prints:
   - Shape of the data.
   - Column names and data types.
   - Summary statistics.
   - First 3 rows and last 3 rows.
   - A random sample of 3 rows.
6. Uses comments to explain each step.

---

### Summary and Revision Notes

- Pandas is the essential library for data manipulation in Python.
- Two core data structures: `Series` (1D) and `DataFrame` (2D).
- Import with `import pandas as pd`.
- Read CSV: `pd.read_csv()`.
- Check data: `df.head()`, `df.info()`, `df.describe()`.
- Access shape: `df.shape`, columns: `df.columns`, data types: `df.dtypes`.

---

## Lesson 4.2 – Series

### Concept Explanation

A **Series** is a one-dimensional labeled array that can hold any data type (integers, strings, floats, Python objects, etc.). Think of it as a column in a spreadsheet or a dictionary with ordered keys.

**Key properties**:
- **Index**: Labels for each element (like row labels).
- **Values**: The data stored in the Series.
- **Data type**: All elements share the same data type.

**Creating a Series**:

| **Method** | **Example** |
|------------|-------------|
| From a list | `pd.Series([10, 20, 30])` |
| From a dictionary | `pd.Series({'a': 10, 'b': 20})` |
| With a custom index | `pd.Series([10, 20, 30], index=['x', 'y', 'z'])` |
| From a scalar | `pd.Series(5, index=['a', 'b', 'c'])` |

**Indexing and Slicing**:
- `series[index]` – access by index label.
- `series.iloc[pos]` – access by position.
- `series[start:stop]` – slice by position.

**Operations**:
- Arithmetic operations are vectorized.
- Boolean filtering works similarly to NumPy.

---

### Importance and Real-World Use Cases

- **Why it matters**: A Series is the building block of a DataFrame. Understanding Series is essential for working with DataFrames, as a DataFrame is essentially a collection of Series.

- **Use cases**:
  - A **data analyst** extracts a single column from a DataFrame (which becomes a Series).
  - A **data scientist** creates a Series of customer IDs.
  - A **financial analyst** creates a Series of daily stock prices.

---

### Step-by-Step Demonstration

**Creating Series**:

```python
import pandas as pd

# From a list
s1 = pd.Series([10, 20, 30, 40, 50])
print("From list:\n", s1)
print(f"Index: {s1.index}")
print(f"Values: {s1.values}")
print(f"Data type: {s1.dtype}\n")

# From a dictionary
s2 = pd.Series({'a': 10, 'b': 20, 'c': 30, 'd': 40})
print("From dict:\n", s2)

# With custom index
s3 = pd.Series([10, 20, 30, 40], index=['w', 'x', 'y', 'z'])
print("With custom index:\n", s3)

# From a scalar
s4 = pd.Series(5, index=['a', 'b', 'c', 'd'])
print("From scalar:\n", s4)
```

**Accessing Values**:

```python
s = pd.Series([10, 20, 30, 40, 50], index=['a', 'b', 'c', 'd', 'e'])

# By index label
print("s['c']:", s['c'])
print("s[['a', 'c', 'e']]:\n", s[['a', 'c', 'e']])

# By position (iloc)
print("s.iloc[0]:", s.iloc[0])
print("s.iloc[2:4]:\n", s.iloc[2:4])

# Slicing
print("s[1:3]:\n", s[1:3])  # By position
print("s['b':'d']:\n", s['b':'d'])  # By label (inclusive)
```

**Operations on Series**:

```python
s1 = pd.Series([10, 20, 30, 40])
s2 = pd.Series([5, 10, 15, 20])

print("Addition:\n", s1 + s2)
print("Multiplication:\n", s1 * s2)
print("Greater than 25:\n", s1 > 25)
print("Square root:\n", s1 ** 0.5)

# Filtering
print("Values > 25:\n", s1[s1 > 25])
```

**Boolean Indexing**:

```python
s = pd.Series([10, 25, 30, 45, 50, 65, 70, 85])

# Filter values > 50
print("> 50:\n", s[s > 50])

# Filter between 30 and 70
print("Between 30 and 70:\n", s[(s >= 30) & (s <= 70)])
```

**Handling Missing Values**:

```python
s = pd.Series([10, 20, None, 40, 50])
print("Contains null:", s.isnull())
print("Not null:", s.notnull())
print("Drop null:", s.dropna())
print("Fill null with 0:", s.fillna(0))
```

**Statistical Methods**:

```python
s = pd.Series([10, 20, 30, 40, 50, 60, 70, 80, 90, 100])

print(f"Sum: {s.sum()}")
print(f"Mean: {s.mean()}")
print(f"Median: {s.median()}")
print(f"Min: {s.min()}")
print(f"Max: {s.max()}")
print(f"Std: {s.std()}")
print(f"Describe:\n{s.describe()}")
```

---

### Practical Examples

- **Example 1**: Extracting a column from a DataFrame.
- **Example 2**: Creating a time series of daily temperatures.
- **Example 3**: Converting a list of sales amounts to a Series.

---

### Hands-on Coding Exercises

**Exercise 4.3** – Series creation:
```python
# 1. Create a Series from a list of numbers
# 2. Create a Series from a dictionary
# 3. Create a Series with a custom index
# 4. Print the index, values, and data type of each
# 5. Access elements by index and by position
```

**Exercise 4.4** – Series operations:
```python
# 1. Create two Series of length 5
# 2. Add them
# 3. Subtract the second from the first
# 4. Multiply them
# 5. Find values greater than a threshold
# 6. Calculate the sum, mean, and standard deviation
# 7. Print all results
```

---

### Mini Quiz

1. What is a Pandas Series?
2. How do you create a Series with a custom index?
3. What is the difference between `s['a']` and `s.iloc[0]`?
4. How do you filter a Series based on a condition?
5. What method is used to handle missing values in a Series?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Confusing `.loc` and `.iloc` | Use `.loc` for labels, `.iloc` for positions |
| Using Python lists for operations that should be vectorized | Use Series operations directly |
| Not handling missing values before analysis | Use `dropna()` or `fillna()` |
| Forgetting that Series have a data type | Check `dtype` and convert if needed |

---

### Interview Questions

1. **What is the difference between a Series and a NumPy array?**  
   *Answer*: A Series has labeled indices, can hold heterogeneous data types, and provides additional functionality like indexing by label. A NumPy array has no labels and is homogeneous.

2. **How do you access the first element of a Series?**  
   *Answer*: Using `s.iloc[0]` (by position) or `s.index[0]` to get the label, then `s[s.index[0]]`.

3. **How do you filter a Series to keep only values greater than a threshold?**  
   *Answer*: Using boolean indexing: `s[s > threshold]`.

---

### Assignment and Mini Project

**Assignment 4.2** – Series practice:
```python
# 1. Create a Series of 10 random integers
# 2. Add a custom index (e.g., letters a to j)
# 3. Extract the first 3 elements
# 4. Extract the last 3 elements
# 5. Extract elements from index 2 to 6
# 6. Filter elements greater than the mean
# 7. Replace all values less than 5 with 0
# 8. Print all results
```

**Mini Project** – Sales Series Analyzer:
Create a program that:
1. Creates a Series of monthly sales for a year (12 values).
2. Adds a custom index with month names.
3. Calculates:
   - Total annual sales.
   - Average monthly sales.
   - Best month (highest sales).
   - Worst month (lowest sales).
   - Months with sales above average.
4. Prints a summary report with the results.

---

### Summary and Revision Notes

- A Series is a 1D labeled array.
- Created with `pd.Series()`.
- Index can be customised.
- Access: `s[label]` or `s.iloc[position]`.
- Vectorized operations.
- Boolean filtering.
- Statistical methods: `sum()`, `mean()`, `median()`, `std()`, etc.

---

## Lesson 4.3 – DataFrames

### Concept Explanation

A **DataFrame** is a two-dimensional labeled data structure with columns of potentially different types. It is the most commonly used Pandas object and is similar to:
- A spreadsheet (Excel).
- A SQL table.
- A dictionary of Series.

**Key properties**:
- **Rows**: Represent individual records.
- **Columns**: Represent variables or features.
- **Index**: Row labels.
- **Columns**: Column labels.

**Creating a DataFrame**:

| **Method** | **Example** |
|------------|-------------|
| From a dictionary of lists | `pd.DataFrame({'col1': [1,2], 'col2': [3,4]})` |
| From a list of dictionaries | `pd.DataFrame([{'a':1, 'b':2}, {'a':3, 'b':4}])` |
| From a NumPy array | `pd.DataFrame(np.array([[1,2],[3,4]]), columns=['A','B'])` |
| From a Series dictionary | `pd.DataFrame({'A': s1, 'B': s2})` |

**Key attributes**:
- `df.shape` – (rows, columns).
- `df.columns` – column names.
- `df.index` – row labels.
- `df.dtypes` – data types of each column.
- `df.values` – NumPy array representation.

---

### Importance and Real-World Use Cases

- **Why it matters**: The DataFrame is the workhorse of data analysis in Python. You'll use it for almost every data task – loading, cleaning, transforming, and analysing.

- **Use cases**:
  - A **data analyst** loads a sales dataset into a DataFrame and explores it.
  - A **data scientist** creates a DataFrame from multiple sources for modeling.
  - A **financial analyst** merges DataFrames of financial statements.

---

### Step-by-Step Demonstration

**Creating DataFrames**:

```python
import pandas as pd
import numpy as np

# From a dictionary of lists
df1 = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana'],
    'Age': [25, 30, 35, 40],
    'City': ['New York', 'London', 'Paris', 'Tokyo']
})
print("From dict of lists:\n", df1)

# From a list of dictionaries
df2 = pd.DataFrame([
    {'Product': 'A', 'Sales': 100},
    {'Product': 'B', 'Sales': 200},
    {'Product': 'C', 'Sales': 150}
])
print("\nFrom list of dicts:\n", df2)

# From a NumPy array
arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
df3 = pd.DataFrame(arr, columns=['X', 'Y', 'Z'])
print("\nFrom NumPy array:\n", df3)

# From a dictionary of Series
s1 = pd.Series([10, 20, 30], index=['a', 'b', 'c'])
s2 = pd.Series([100, 200, 300], index=['a', 'b', 'c'])
df4 = pd.DataFrame({'A': s1, 'B': s2})
print("\nFrom dict of Series:\n", df4)
```

**Viewing Data**:

```python
# Sample dataset for demonstration
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana', 'Eve', 'Frank'],
    'Age': [25, 30, 35, 40, 28, 32],
    'Salary': [50000, 60000, 70000, 80000, 55000, 65000],
    'City': ['New York', 'London', 'Paris', 'Tokyo', 'Sydney', 'Berlin']
})

print("First 3 rows:\n", df.head(3))
print("\nLast 2 rows:\n", df.tail(2))
print("\nRandom sample:\n", df.sample(2))
print("\nShape:", df.shape)
print("\nColumns:", df.columns.tolist())
print("\nIndex:", df.index)
print("\nData types:\n", df.dtypes)
print("\nInfo:")
df.info()
print("\nSummary statistics:")
print(df.describe())
```

**Accessing Data**:

```python
# Column access (returns Series)
print("Single column (Name):\n", df['Name'])
print("\nSingle column (City):\n", df.City)  # Dot notation

# Multiple columns (returns DataFrame)
print("\nMultiple columns:\n", df[['Name', 'Salary']])

# Row access using iloc (by position)
print("\nFirst row:\n", df.iloc[0])
print("\nRows 0-2:\n", df.iloc[0:3])
print("\nRows 2-4, columns 0-2:\n", df.iloc[2:5, 0:3])

# Row access using loc (by label)
print("\nRow at index 2:\n", df.loc[2])
print("\nRows 0-2:\n", df.loc[0:2])  # Inclusive with loc!
```

**Adding and Modifying Columns**:

```python
# Add a new column
df['Bonus'] = df['Salary'] * 0.1
print("Added Bonus column:\n", df)

# Add a column with a constant
df['Department'] = 'Sales'
print("\nAdded Department column:\n", df)

# Modify an existing column
df['Salary'] = df['Salary'] * 1.05
print("\nModified Salary (5% increase):\n", df)

# Drop a column
df_clean = df.drop('Department', axis=1)
print("\nAfter dropping Department:\n", df_clean)
```

---

### Practical Examples

- **Example 1**: Loading a CSV file into a DataFrame for analysis.
- **Example 2**: Creating a DataFrame from multiple data sources.
- **Example 3**: Adding calculated columns (e.g., profit, margin).

---

### Hands-on Coding Exercises

**Exercise 4.5** – DataFrame creation:
```python
# 1. Create a DataFrame with 5 rows and 4 columns using a dictionary
# 2. Print the DataFrame
# 3. Print the shape
# 4. Print the column names
# 5. Print the data types
# 6. Print summary statistics
# 7. Print the first 2 rows
# 8. Print the last 2 rows
```

**Exercise 4.6** – DataFrame operations:
```python
# 1. Add a new column that is a calculation of two existing columns
# 2. Add a constant column
# 3. Drop a column
# 4. Rename a column
# 5. Access a single column
# 6. Access multiple columns
# 7. Access rows using iloc
# 8. Print all results
```

---

### Mini Quiz

1. What is a DataFrame?
2. How do you access a single column of a DataFrame?
3. What is the difference between `.iloc` and `.loc`?
4. How do you add a new column to a DataFrame?
5. What method gives you summary statistics of numeric columns?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using dot notation (`df.column`) when column name has spaces or special characters | Use bracket notation: `df['column name']` |
| Modifying a view instead of a copy | Use `.copy()` when you need a separate copy |
| Not checking data types before operations | Use `df.dtypes` to check |
| Forgetting `axis=1` when dropping columns | Use `axis=1` for columns, `axis=0` for rows |
| Using chained indexing (`df['col'][0]`) | Use `.iloc` or `.loc` for explicit access |

---

### Interview Questions

1. **What is the difference between a Series and a DataFrame?**  
   *Answer*: A Series is a 1D labeled array (single column). A DataFrame is a 2D labeled structure with rows and columns (like a table). A DataFrame is essentially a collection of Series that share the same index.

2. **How do you add a new column to a DataFrame?**  
   *Answer*: Using `df['new_column'] = values`, where values can be a list, Series, or scalar.

3. **What is the difference between `.loc` and `.iloc`?**  
   *Answer*: `.loc` accesses rows/columns by label (index name). `.iloc` accesses by integer position.

---

### Assignment and Mini Project

**Assignment 4.3** – DataFrame manipulation:
```python
# 1. Create a DataFrame with columns: Product, Sales, Quantity, Price
# 2. Add a new column 'Revenue' = Sales * Price
# 3. Add a new column 'Profit' = Revenue * 0.2
# 4. Add a new column 'Category' with a constant value
# 5. Drop the 'Quantity' column
# 6. Rename 'Price' to 'Unit_Price'
# 7. Print the DataFrame
# 8. Print summary statistics
```

**Mini Project** – Employee Data Manager:
Create a program that:
1. Creates a DataFrame with employee data (Name, Age, Department, Salary, Years_Experience).
2. Adds calculated columns:
   - `Bonus` = 10% of Salary.
   - `Salary_with_Bonus` = Salary + Bonus.
   - `Seniority` = "Senior" if Years_Experience > 5 else "Junior".
3. Sorts the DataFrame by Salary (descending).
4. Prints the top 3 highest-paid employees.
5. Prints summary statistics for Salary and Years_Experience.
6. Saves the DataFrame to a CSV file.

---

### Summary and Revision Notes

- DataFrame is a 2D labeled data structure.
- Created from dicts, lists, arrays, or Series.
- Key attributes: `shape`, `columns`, `index`, `dtypes`.
- View data: `head()`, `tail()`, `sample()`.
- Access columns: `df['col']` or `df.col`.
- Access rows: `.iloc[pos]` (position) or `.loc[label]` (label).
- Add columns: `df['new'] = values`.
- Drop columns: `df.drop('col', axis=1)`.

---

## Lesson 4.4 – Importing Data

### Concept Explanation

Pandas provides a wide range of functions to import data from various sources. The most common is reading CSV files, but Pandas supports many formats.

**Common import functions**:

| **Function** | **Description** | **Example** |
|--------------|-----------------|-------------|
| `pd.read_csv()` | Read CSV file | `pd.read_csv('data.csv')` |
| `pd.read_excel()` | Read Excel file | `pd.read_excel('data.xlsx')` |
| `pd.read_json()` | Read JSON file | `pd.read_json('data.json')` |
| `pd.read_html()` | Read HTML tables | `pd.read_html('page.html')` |
| `pd.read_sql()` | Read SQL query | `pd.read_sql('SELECT * FROM table', conn)` |
| `pd.read_parquet()` | Read Parquet file | `pd.read_parquet('data.parquet')` |
| `pd.read_clipboard()` | Read clipboard | `pd.read_clipboard()` |

**Key parameters for `read_csv()`**:
- `filepath_or_buffer`: File path or URL.
- `sep`: Delimiter (default: ',').
- `header`: Row to use as column names.
- `names`: List of column names to use.
- `index_col`: Column to use as row index.
- `usecols`: Columns to read.
- `skiprows`: Rows to skip.
- `nrows`: Number of rows to read.
- `dtype`: Data types for columns.
- `parse_dates`: Parse dates.
- `encoding`: File encoding.

---

### Importance and Real-World Use Cases

- **Why it matters**: Data comes in many formats. Pandas' import functions allow you to load data from virtually anywhere – local files, databases, web pages, and APIs.

- **Use cases**:
  - A **data analyst** imports sales data from CSV files.
  - A **data scientist** loads data from a SQL database.
  - A **financial analyst** reads data from multiple Excel files.

---

### Step-by-Step Demonstration

**Reading CSV with Parameters**:

```python
import pandas as pd

# Basic read
df = pd.read_csv('sample_data.csv')
print("Basic read:\n", df.head())

# Read with specific columns
df = pd.read_csv('sample_data.csv', usecols=['Name', 'Age'])
print("\nOnly Name and Age:\n", df.head())

# Read with custom index
df = pd.read_csv('sample_data.csv', index_col='Name')
print("\nName as index:\n", df.head())

# Read only first 3 rows
df = pd.read_csv('sample_data.csv', nrows=3)
print("\nOnly first 3 rows:\n", df)

# Read with date parsing
# df = pd.read_csv('sales.csv', parse_dates=['Date'])
# print(df.dtypes)

# Read with custom delimiter (e.g., tab)
# df = pd.read_csv('data.tsv', sep='\t')

# Read from URL (public CSV)
url = 'https://raw.githubusercontent.com/datasets/covid-19/main/data/countries-aggregated.csv'
df = pd.read_csv(url)
print("\nFrom URL:\n", df.head())
```

**Reading Excel Files**:

```python
# Read Excel file
# df = pd.read_excel('data.xlsx')

# Read specific sheet
# df = pd.read_excel('data.xlsx', sheet_name='Sales')

# Read multiple sheets
# sheets = pd.read_excel('data.xlsx', sheet_name=None)

# Read a range of columns
# df = pd.read_excel('data.xlsx', usecols='A:C')
```

**Reading JSON Files**:

```python
import json

# Read JSON file
# df = pd.read_json('data.json')

# Read JSON with specific orientation
# df = pd.read_json('data.json', orient='records')

# Read JSON from string
# df = pd.read_json('{"name": ["Alice", "Bob"], "age": [25, 30]}')
```

**Reading SQL Databases**:

```python
# import sqlite3
# conn = sqlite3.connect('database.db')
# df = pd.read_sql('SELECT * FROM sales', conn)
# conn.close()
```

**Reading from Clipboard** (useful for copying from Excel):

```python
# Copy a range from Excel, then:
# df = pd.read_clipboard()
```

---

### Practical Examples

- **Example 1**: Reading a CSV file with custom delimiter and encoding.
- **Example 2**: Loading data from an Excel file with multiple sheets.
- **Example 3**: Reading a public dataset from a URL.

---

### Hands-on Coding Exercises

**Exercise 4.7** – Read CSV with parameters:
```python
# 1. Create a CSV file with sample data
# 2. Read it with default settings
# 3. Read only specific columns (Name, Age)
# 4. Read only first 5 rows
# 5. Set a column as the index
# 6. Print the results
```

**Exercise 4.8** – Read from URL:
```python
# 1. Find a public CSV file online (e.g., from data.gov)
# 2. Read it using pd.read_csv()
# 3. Print the first 5 rows
# 4. Print the shape and data types
```

---

### Mini Quiz

1. What function is used to read a CSV file?
2. How do you read only specific columns from a CSV?
3. How do you set a column as the index when reading a CSV?
4. What function is used to read an Excel file?
5. How do you read a CSV from a URL?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not specifying encoding for non-ASCII files | Use `encoding='utf-8'` or `'latin-1'` |
| Not handling large files efficiently | Use `chunksize` parameter or read in chunks |
| Assuming the first row is the header | Use `header=None` if there's no header |
| Not checking the data after import | Always check with `df.head()` and `df.info()` |
| Reading all columns when only a few are needed | Use `usecols` to read only needed columns |

---

### Interview Questions

1. **How do you read a CSV file with a different delimiter (e.g., semicolon)?**  
   *Answer*: Use the `sep` parameter: `pd.read_csv('data.csv', sep=';')`.

2. **How do you read only the first 10 rows of a CSV file?**  
   *Answer*: Use the `nrows` parameter: `pd.read_csv('data.csv', nrows=10)`.

3. **How do you read a CSV file that has no header row?**  
   *Answer*: Use `header=None` and optionally specify column names with `names`.

---

### Assignment and Mini Project

**Assignment 4.4** – Data import practice:
```python
# 1. Create a CSV file with at least 5 columns and 20 rows
# 2. Read the CSV file with the following variations:
#    a. Default settings
#    b. Only 3 specific columns
#    c. First 10 rows only
#    d. With a column as the index
# 3. For each, print the first 3 rows and the shape
```

**Mini Project** – Data Import Tool:
Create a program that:
1. Asks the user for a file path.
2. Detects the file type based on extension (.csv, .xlsx, .json).
3. Imports the file using the appropriate Pandas function.
4. Prints:
   - Shape of the data.
   - Column names and data types.
   - First 5 rows.
   - Summary statistics.
5. Handles errors gracefully (file not found, wrong format, etc.).

---

### Summary and Revision Notes

- `pd.read_csv()` for CSV files.
- `pd.read_excel()` for Excel files.
- `pd.read_json()` for JSON files.
- `pd.read_sql()` for SQL databases.
- `pd.read_clipboard()` from clipboard.
- Key parameters: `sep`, `header`, `usecols`, `index_col`, `nrows`, `encoding`.
- Always check data after import.

---

## Lesson 4.5 – Exporting Data

### Concept Explanation

Just as you import data, you often need to export it – saving processed data to files for sharing, reporting, or integration with other tools.

**Common export functions**:

| **Function** | **Description** | **Example** |
|--------------|-----------------|-------------|
| `df.to_csv()` | Write to CSV | `df.to_csv('output.csv')` |
| `df.to_excel()` | Write to Excel | `df.to_excel('output.xlsx')` |
| `df.to_json()` | Write to JSON | `df.to_json('output.json')` |
| `df.to_sql()` | Write to SQL database | `df.to_sql('table', conn)` |
| `df.to_dict()` | Convert to dictionary | `df.to_dict(orient='records')` |
| `df.to_string()` | Convert to string | `df.to_string()` |
| `df.to_clipboard()` | Copy to clipboard | `df.to_clipboard()` |

**Key parameters for `to_csv()`**:
- `path_or_buf`: File path.
- `sep`: Delimiter (default: ',').
- `index`: Include row index (default: True).
- `header`: Include column names (default: True).
- `columns`: Columns to write.
- `encoding`: File encoding.

---

### Importance and Real-World Use Cases

- **Why it matters**: After processing and analysing data, you need to save it. Exporting allows you to share results, create reports, and integrate with other systems.

- **Use cases**:
  - A **data analyst** saves a cleaned dataset to a CSV file.
  - A **financial analyst** exports a summary report to Excel.
  - A **data scientist** saves model predictions to a CSV for evaluation.

---

### Step-by-Step Demonstration

**Exporting to CSV**:

```python
import pandas as pd

# Create sample data
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana'],
    'Age': [25, 30, 35, 40],
    'City': ['New York', 'London', 'Paris', 'Tokyo'],
    'Salary': [50000, 60000, 70000, 80000]
})

# Basic CSV export
df.to_csv('output.csv')
print("Basic CSV exported.")

# Without index
df.to_csv('output_no_index.csv', index=False)
print("CSV without index exported.")

# Custom delimiter (e.g., tab)
df.to_csv('output_tab.tsv', sep='\t', index=False)
print("TSV exported.")

# Only specific columns
df.to_csv('output_selected.csv', columns=['Name', 'Salary'], index=False)
print("CSV with selected columns exported.")
```

**Exporting to Excel**:

```python
# To a single sheet
df.to_excel('output.xlsx', index=False)
print("Excel exported.")

# To multiple sheets
with pd.ExcelWriter('output_multi.xlsx') as writer:
    df.to_excel(writer, sheet_name='Data', index=False)
    df[['Name', 'Salary']].to_excel(writer, sheet_name='Summary', index=False)
print("Excel with multiple sheets exported.")
```

**Exporting to JSON**:

```python
# To JSON file
df.to_json('output.json', orient='records')
print("JSON exported.")

# With indentation
df.to_json('output_pretty.json', orient='records', indent=4)
print("Pretty JSON exported.")
```

**Exporting to Dictionary**:

```python
# Convert to dictionary
dict_data = df.to_dict(orient='records')
print("Dictionary:\n", dict_data)
```

**Exporting with Formatting**:

```python
# Format as string
print(df.to_string(index=False))

# Format with formatting options
# df.to_csv('output.csv', index=False, float_format='%.2f')
```

---

### Practical Examples

- **Example 1**: Saving a cleaned dataset to a CSV file.
- **Example 2**: Exporting a summary report to Excel with multiple sheets.
- **Example 3**: Saving data to JSON for use in a web application.

---

### Hands-on Coding Exercises

**Exercise 4.9** – CSV export:
```python
# 1. Create a DataFrame with sample data
# 2. Export it to a CSV file
# 3. Export it without the index
# 4. Export only specific columns
# 5. Export with a different delimiter (tab)
# 6. Verify the exports by reading them back
```

**Exercise 4.10** – Multi-format export:
```python
# 1. Create a DataFrame
# 2. Export it to CSV
# 3. Export it to Excel
# 4. Export it to JSON
# 5. Export it to a dictionary
# 6. Compare the outputs
```

---

### Mini Quiz

1. How do you export a DataFrame to a CSV file?
2. How do you prevent the index from being exported?
3. How do you export only specific columns to CSV?
4. How do you export to Excel with multiple sheets?
5. What are the common formats for exporting data?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting `index=False` – exporting an unnecessary index column | Always use `index=False` unless the index is meaningful |
| Not checking the output file after export | Read the file back to verify |
| Using the wrong delimiter for the target system | Specify `sep` as needed |
| Not handling encoding for non-ASCII text | Use `encoding='utf-8'` |
| Overwriting existing files by mistake | Check if the file exists before writing |

---

### Interview Questions

1. **How do you export a DataFrame to a CSV file without the index?**  
   *Answer*: Using `df.to_csv('file.csv', index=False)`.

2. **How do you export a DataFrame to Excel with multiple sheets?**  
   *Answer*: Using `pd.ExcelWriter` and writing each sheet with `to_excel`.

3. **What are the common data export formats in Pandas?**  
   *Answer*: CSV, Excel, JSON, SQL, Parquet, and dictionary.

---

### Assignment and Mini Project

**Assignment 4.5** – Export practice:
```python
# 1. Create a DataFrame with 5 columns and 10 rows
# 2. Export it to:
#    a. CSV without index
#    b. CSV with tab delimiter
#    c. Excel with one sheet
#    d. Excel with two sheets
#    e. JSON
# 3. Read each file back to verify it exported correctly
# 4. Print the first 2 rows of each
```

**Mini Project** – Report Exporter:
Create a program that:
1. Creates a DataFrame with sample sales data (Product, Region, Sales, Quantity, Date).
2. Processes the data:
   - Calculates total sales by product.
   - Calculates total sales by region.
   - Calculates overall totals.
3. Exports:
   - The original data to a CSV file.
   - The summary tables to an Excel file with separate sheets.
   - The summary tables to JSON.
4. Prints confirmation messages.

---

### Summary and Revision Notes

- Export functions: `to_csv()`, `to_excel()`, `to_json()`, `to_sql()`.
- Key parameters: `index`, `header`, `columns`, `sep`, `encoding`.
- Use `index=False` to avoid exporting row labels.
- Use `ExcelWriter` for multiple sheets.
- Always verify exports by reading them back.

---

## Lesson 4.6 – Selecting Rows and Columns

### Concept Explanation

Selecting specific rows and columns is one of the most common operations in data analysis. Pandas provides several ways to select data:

| **Method** | **Description** | **When to Use** |
|------------|-----------------|-----------------|
| `df['col']` | Select a single column | Getting a Series |
| `df[['col1', 'col2']]` | Select multiple columns | Getting a DataFrame |
| `df.loc[row_label, col_label]` | Select by label | When you know the index labels |
| `df.iloc[row_pos, col_pos]` | Select by position | When you know the positions |
| `df.ix` | Mixed label/position | Deprecated, use `.loc` or `.iloc` |
| `df.at[label, col]` | Single value by label | Fast access to a single element |
| `df.iat[pos, pos]` | Single value by position | Fast access to a single element |

**Key principles**:
- `.loc` uses labels (inclusive for slices).
- `.iloc` uses positions (exclusive for slices).
- `.at` and `.iat` are for single-element access.

---

### Importance and Real-World Use Cases

- **Why it matters**: Selecting data is the first step in any analysis. You need to extract specific columns, filter rows, or isolate subsets.

- **Use cases**:
  - A **data analyst** selects specific columns for a report.
  - A **data scientist** extracts features (columns) for modeling.
  - A **financial analyst** selects data for a specific time period.

---

### Step-by-Step Demonstration

```python
import pandas as pd

# Create sample data
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana', 'Eve', 'Frank'],
    'Age': [25, 30, 35, 40, 28, 32],
    'Salary': [50000, 60000, 70000, 80000, 55000, 65000],
    'Department': ['HR', 'IT', 'Finance', 'IT', 'HR', 'Finance'],
    'City': ['New York', 'London', 'Paris', 'Tokyo', 'Sydney', 'Berlin']
})
print("Original DataFrame:\n", df)

# Column selection
print("\n--- Column Selection ---")
print("Single column (Name):\n", df['Name'])
print("\nSingle column (Salary):\n", df.Salary)  # Dot notation
print("\nMultiple columns:\n", df[['Name', 'Salary', 'City']])

# Row selection (iloc - by position)
print("\n--- Row Selection (iloc) ---")
print("First row:\n", df.iloc[0])
print("\nLast row:\n", df.iloc[-1])
print("\nRows 1-3:\n", df.iloc[1:4])  # Exclusive stop
print("\nRows 1-4, columns 0-2:\n", df.iloc[1:5, 0:3])

# Row selection (loc - by label)
print("\n--- Row Selection (loc) ---")
print("Row at index 2:\n", df.loc[2])
print("\nRows 0-2:\n", df.loc[0:2])  # Inclusive with loc!

# Mixed selection: rows by position, columns by label
print("\n--- Mixed Selection ---")
print("Rows 1-3, columns 'Name' and 'Salary':\n", df.iloc[1:4][['Name', 'Salary']])

# Using .at and .iat for single values
print("\n--- Single Value Access ---")
print("df.at[2, 'Name']:", df.at[2, 'Name'])
print("df.iat[2, 0]:", df.iat[2, 0])

# Getting a value with loc and iloc
print("\n--- Loc vs Iloc ---")
print("df.loc[2, 'Age']:", df.loc[2, 'Age'])
print("df.iloc[2, 1]:", df.iloc[2, 1])  # Row 2, column 1

# Selecting a row as a Series
row = df.loc[2]
print("\nRow as Series:\n", row)
print("Name:", row['Name'])
```

**Filtering Rows with Conditions**:

```python
# Boolean indexing
print("\n--- Boolean Indexing ---")
print("Age > 30:\n", df[df['Age'] > 30])
print("\nAge between 28 and 35:\n", df[(df['Age'] >= 28) & (df['Age'] <= 35)])
print("\nDepartment is IT:\n", df[df['Department'] == 'IT'])
print("\nDepartment is HR or Finance:\n", df[df['Department'].isin(['HR', 'Finance'])])
print("\nCity contains 'New':\n", df[df['City'].str.contains('New')])
```

**Selecting Random Rows**:

```python
# Random sample
print("\n--- Random Selection ---")
print("Random 2 rows:\n", df.sample(2))
print("\nRandom 20% of rows:\n", df.sample(frac=0.2))
```

---

### Practical Examples

- **Example 1**: Selecting all columns except one: `df.drop('col', axis=1)`.
- **Example 2**: Selecting rows where a condition is met: `df[df['Sales'] > 1000]`.
- **Example 3**: Selecting specific rows and columns: `df.loc[10:20, ['Name', 'Salary']]`.

---

### Hands-on Coding Exercises

**Exercise 4.11** – Column selection:
```python
# 1. Create a DataFrame with 5 columns
# 2. Select a single column
# 3. Select multiple columns
# 4. Select all columns except one
# 5. Print the results
```

**Exercise 4.12** – Row selection:
```python
# 1. Select the first row
# 2. Select the last 3 rows
# 3. Select rows 5-10
# 4. Select a single row and access a specific value
# 5. Print all results
```

**Exercise 4.13** – Conditional selection:
```python
# 1. Select rows where a column value > threshold
# 2. Select rows where a column value equals a specific value
# 3. Select rows where multiple conditions are met
# 4. Select rows where a column contains a substring
# 5. Print all results
```

---

### Mini Quiz

1. What is the difference between `.loc` and `.iloc`?
2. How do you select a single column?
3. How do you select multiple columns?
4. How do you filter rows based on a condition?
5. What is the difference between `df.at[2, 'Name']` and `df.loc[2, 'Name']`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using `.loc` with positions (should use `.iloc`) | Use `.loc` for labels, `.iloc` for positions |
| Forgetting parentheses in complex conditions | Use parentheses: `(df['A'] > 5) & (df['B'] < 10)` |
| Using chained indexing (`df['A'][0]`) | Use `.iloc[0, 'A']` or `.loc[0, 'A']` |
| Not using `.copy()` when modifying slices | Use `.copy()` to avoid modifying the original |
| Using `df[df['A'] == 'value']` when `A` has NaN | Use `df.loc[df['A'] == 'value']` for safety |

---

### Interview Questions

1. **What is the difference between `.loc` and `.iloc`?**  
   *Answer*: `.loc` selects rows/columns by label (index name). `.iloc` selects by integer position.

2. **How do you select rows where a column value is greater than a threshold?**  
   *Answer*: Using boolean indexing: `df[df['column'] > threshold]`.

3. **How do you select a specific cell value in a DataFrame?**  
   *Answer*: Using `.at[row_label, col_label]` or `.iat[row_pos, col_pos]`.

---

### Assignment and Mini Project

**Assignment 4.6** – Selection practice:
```python
# 1. Create a DataFrame with 8 columns and 15 rows
# 2. Select a single column
# 3. Select three columns
# 4. Select the first 5 rows
# 5. Select rows 5-10
# 6. Select rows where a column > threshold
# 7. Select rows where multiple conditions are met
# 8. Select specific rows and columns
# 9. Print all results
```

**Mini Project** – Employee Data Explorer:
Create a program that:
1. Creates a DataFrame of employee data (Name, Age, Department, Salary, Experience, City).
2. Provides functions to:
   - Select all employees in a specific department.
   - Select employees with salary above a threshold.
   - Select employees with experience above a threshold.
   - Select employees from a specific city.
   - Select employees meeting multiple criteria.
3. Prints the results for each query.
4. Uses `.loc` and `.iloc` appropriately.

---

### Summary and Revision Notes

- `.loc[label]` – access by label.
- `.iloc[pos]` – access by position.
- `df['col']` – single column.
- `df[['col1', 'col2']]` – multiple columns.
- Boolean indexing: `df[df['col'] > threshold]`.
- Multiple conditions: `(cond1) & (cond2)`.
- Single value: `.at[label, col]` or `.iat[pos, col]`.

---

## Lesson 4.7 – Filtering Data

### Concept Explanation

Filtering is the process of selecting a subset of data based on conditions. Pandas provides powerful filtering capabilities:

**Methods**:
1. **Boolean indexing**: `df[condition]`
2. **`.query()`**: `df.query('age > 25')`
3. **`.isin()`**: `df[df['col'].isin(values)]`
4. **`.str.contains()`**: `df[df['col'].str.contains('pattern')]`
5. **`.between()`**: `df[df['col'].between(low, high)]`

**Conditions**:
- Single condition: `df['Age'] > 30`
- Multiple conditions: `(df['Age'] > 30) & (df['Salary'] > 60000)`
- `OR` conditions: `(df['Age'] > 30) | (df['Department'] == 'IT')`

---

### Importance and Real-World Use Cases

- **Why it matters**: Filtering is how you drill down into data – finding specific segments, outliers, or subsets for analysis.

- **Use cases**:
  - A **data analyst** filters sales data to only show a specific region.
  - A **data scientist** filters data to focus on a specific demographic.
  - A **financial analyst** filters transactions above a threshold.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np

# Create sample data
np.random.seed(42)
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana', 'Eve', 'Frank', 'Grace', 'Henry'],
    'Age': np.random.randint(20, 60, 8),
    'Salary': np.random.randint(30000, 100000, 8),
    'Department': np.random.choice(['IT', 'HR', 'Finance', 'Marketing'], 8),
    'City': np.random.choice(['New York', 'London', 'Paris', 'Tokyo'], 8)
})
print("Original DataFrame:\n", df)

# Single condition
print("\n--- Single Condition ---")
print("Age > 35:\n", df[df['Age'] > 35])
print("\nSalary > 60000:\n", df[df['Salary'] > 60000])

# Multiple conditions (AND)
print("\n--- Multiple Conditions (AND) ---")
print("Age > 30 and Salary > 60000:\n", df[(df['Age'] > 30) & (df['Salary'] > 60000)])

# Multiple conditions (OR)
print("\n--- Multiple Conditions (OR) ---")
print("Age > 40 or Department is IT:\n", df[(df['Age'] > 40) | (df['Department'] == 'IT')])

# Using .query()
print("\n--- Using .query() ---")
print("Age > 35:\n", df.query('Age > 35'))
print("Age > 30 and Salary > 60000:\n", df.query('Age > 30 and Salary > 60000'))

# Using .isin()
print("\n--- Using .isin() ---")
print("Department in ['IT', 'Finance']:\n", df[df['Department'].isin(['IT', 'Finance'])])

# Using .str.contains()
print("\n--- Using .str.contains() ---")
print("City contains 'New':\n", df[df['City'].str.contains('New')])

# Using .between()
print("\n--- Using .between() ---")
print("Age between 30 and 45:\n", df[df['Age'].between(30, 45)])

# Filtering with .loc and conditions
print("\n--- Filtering with .loc ---")
print("Age > 35, only Name and Salary:\n", df.loc[df['Age'] > 35, ['Name', 'Salary']])

# Filtering out (negation)
print("\n--- Negation ---")
print("Department is NOT IT:\n", df[df['Department'] != 'IT'])
print("Age <= 35:\n", df[~(df['Age'] > 35)])

# Filtering with .isnull() / .notnull()
df_with_nulls = df.copy()
df_with_nulls.loc[1, 'Salary'] = np.nan
df_with_nulls.loc[3, 'City'] = np.nan
print("\n--- Null Handling ---")
print("Original with nulls:\n", df_with_nulls)
print("Rows with null Salary:\n", df_with_nulls[df_with_nulls['Salary'].isnull()])
print("Rows without null City:\n", df_with_nulls[df_with_nulls['City'].notnull()])
```

**Filtering with Multiple Conditions (Advanced)**:

```python
# Using a list of conditions
conditions = [
    df['Age'] > 30,
    df['Salary'] < 80000,
    df['Department'].isin(['IT', 'Finance'])
]
# Combine with all conditions
filtered = df[pd.concat(conditions, axis=1).all(axis=1)]
print("\n--- Advanced Filtering ---")
print("Age > 30 AND Salary < 80000 AND Dept in ['IT','Finance']:\n", filtered)
```

---

### Practical Examples

- **Example 1**: Filtering sales data by region and product category.
- **Example 2**: Filtering customer data by age and income brackets.
- **Example 3**: Filtering survey responses by specific question answers.

---

### Hands-on Coding Exercises

**Exercise 4.14** – Single condition filtering:
```python
# 1. Create a DataFrame with columns: Name, Age, Salary, Department
# 2. Filter rows where Age > 30
# 3. Filter rows where Salary > 50000
# 4. Filter rows where Department == 'IT'
# 5. Filter rows where City == 'New York'
# 6. Print all results
```

**Exercise 4.15** – Multiple conditions:
```python
# 1. Filter rows where Age > 30 AND Salary > 60000
# 2. Filter rows where Department == 'IT' OR Department == 'Finance'
# 3. Filter rows where Age between 25 and 40
# 4. Filter rows where City contains 'New'
# 5. Filter rows where Salary > 50000 AND Department != 'HR'
# 6. Print all results
```

---

### Mini Quiz

1. How do you filter a DataFrame for a single condition?
2. How do you combine multiple conditions with AND?
3. What is the purpose of `.query()`?
4. How do you filter for values in a list using `.isin()`?
5. How do you filter for string patterns using `.str.contains()`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting parentheses in complex conditions | Use parentheses: `(cond1) & (cond2)` |
| Using `&` and `|` without parentheses | Always wrap conditions in parentheses |
| Using `or` and `and` instead of `|` and `&` | Use `|` and `&` for element-wise operations |
| Not handling NaN in comparisons | Use `.isnull()` or `.notnull()` |
| Modifying the original DataFrame when filtering | Use `.copy()` if you need to modify the result |

---

### Interview Questions

1. **How do you filter a DataFrame for rows where a column is greater than a value?**  
   *Answer*: `df[df['column'] > value]`.

2. **How do you filter for rows that meet multiple conditions?**  
   *Answer*: Using `&` for AND: `df[(df['A'] > 5) & (df['B'] < 10)]`.

3. **What is the difference between using `.query()` and boolean indexing?**  
   *Answer*: `.query()` uses a string expression and can be more readable for complex conditions. Boolean indexing uses Python conditions and is more flexible.

---

### Assignment and Mini Project

**Assignment 4.7** – Filtering practice:
```python
# 1. Create a DataFrame of 20 rows with columns: Name, Age, Salary, Department, City
# 2. Filter using:
#    a. Age > 35
#    b. Salary > 70000
#    c. Department == 'IT'
#    d. Age > 30 AND Salary > 60000
#    e. Department in ['IT', 'Finance', 'HR']
#    f. City contains 'York'
#    g. Age between 25 and 45
# 3. Print each filtered DataFrame with a description
```

**Mini Project** – Customer Segment Filter:
Create a program that:
1. Creates a DataFrame of customer data (Name, Age, Income, City, Segment, Purchase_Count).
2. Provides filtering functions for:
   - High-value customers (Income > 100000).
   - Frequent customers (Purchase_Count > 10).
   - Specific city.
   - Age range.
   - Specific segment.
3. Combines multiple filters (e.g., high-income AND frequent).
4. Prints the results for each filter.
5. Counts how many customers meet each criteria.

---

### Summary and Revision Notes

- Boolean indexing: `df[df['col'] > value]`.
- Multiple conditions: `(cond1) & (cond2)`.
- `.query()` for string-based filtering.
- `.isin()` for membership testing.
- `.str.contains()` for string pattern matching.
- `.between()` for range filtering.
- `.isnull()` and `.notnull()` for missing values.

---

## Lesson 4.8 – Sorting

### Concept Explanation

Sorting allows you to order your data by one or more columns, making it easier to identify patterns, top/bottom performers, and trends.

**Key functions**:
- `df.sort_values()` – sort by column values.
- `df.sort_index()` – sort by index.

**Parameters**:
- `by`: Column(s) to sort by.
- `ascending`: True for ascending, False for descending.
- `inplace`: Whether to modify the original DataFrame.
- `na_position`: Where to place NaN values ('first' or 'last').

---

### Importance and Real-World Use Cases

- **Why it matters**: Sorting is essential for ranking, identifying top/bottom items, and preparing data for presentation.

- **Use cases**:
  - A **data analyst** sorts sales data to find the top-selling products.
  - A **financial analyst** sorts transactions by date.
  - A **data scientist** sorts data before exporting to a report.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np

# Create sample data
np.random.seed(42)
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana', 'Eve', 'Frank'],
    'Age': [25, 35, 30, 45, 28, 32],
    'Salary': [50000, 70000, 60000, 80000, 55000, 65000],
    'Department': ['HR', 'IT', 'Finance', 'IT', 'HR', 'Finance']
})
print("Original:\n", df)

# Sort by a single column (ascending)
print("\n--- Sort by Age (ascending) ---")
print(df.sort_values('Age'))

# Sort by a single column (descending)
print("\n--- Sort by Salary (descending) ---")
print(df.sort_values('Salary', ascending=False))

# Sort by multiple columns
print("\n--- Sort by Department then Salary (descending) ---")
print(df.sort_values(['Department', 'Salary'], ascending=[True, False]))

# Sort by index
df_sorted = df.sort_values('Age')
print("\n--- Sort by index (ascending) ---")
print(df_sorted.sort_index())

# In-place sorting
df.sort_values('Age', inplace=True)
print("\n--- In-place sort by Age ---")
print(df)

# Sorting with NaNs
df_nan = df.copy()
df_nan.loc[2, 'Salary'] = np.nan
print("\n--- Sorting with NaNs ---")
print("Original with NaN:\n", df_nan)
print("Sort with NaNs first:\n", df_nan.sort_values('Salary', na_position='first'))
print("Sort with NaNs last:\n", df_nan.sort_values('Salary', na_position='last'))
```

---

### Practical Examples

- **Example 1**: Sorting sales data to find the top 10 products.
- **Example 2**: Sorting customer data by purchase date.
- **Example 3**: Sorting data by multiple criteria (e.g., department then salary).

---

### Hands-on Coding Exercises

**Exercise 4.16** – Sorting practice:
```python
# 1. Create a DataFrame with columns: Name, Age, Salary, Department
# 2. Sort by Age ascending
# 3. Sort by Salary descending
# 4. Sort by Department then Age
# 5. Sort by Department ascending, Salary descending
# 6. Sort by index
# 7. Print all results
```

**Exercise 4.17** – Top N:
```python
# 1. Sort by a column and get the top 5 rows
# 2. Sort by a column and get the bottom 5 rows
# 3. Sort by two columns and get the top 3
# 4. Print the results
```

---

### Mini Quiz

1. What function is used to sort a DataFrame by column values?
2. How do you sort in descending order?
3. How do you sort by multiple columns?
4. What is the difference between `sort_values()` and `sort_index()`?
5. How do you handle NaN values when sorting?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to assign the sorted result (if `inplace=False`) | Assign to a variable or use `inplace=True` |
| Not handling NaNs in sorting | Use `na_position` parameter |
| Sorting a large DataFrame without filtering first | Filter before sorting for better performance |
| Sorting by a column with mixed types | Ensure consistent data types before sorting |

---

### Interview Questions

1. **How do you sort a DataFrame by a specific column?**  
   *Answer*: Using `df.sort_values('column')`.

2. **How do you sort by multiple columns?**  
   *Answer*: `df.sort_values(['col1', 'col2'], ascending=[True, False])`.

3. **What is the difference between `sort_values()` and `sort_index()`?**  
   *Answer*: `sort_values()` sorts by column values. `sort_index()` sorts by the row index.

---

### Assignment and Mini Project

**Assignment 4.8** – Sorting practice:
```python
# 1. Create a DataFrame of 20 rows with columns: Product, Sales, Quantity, Region
# 2. Sort by Sales descending
# 3. Sort by Region ascending, Sales descending
# 4. Sort by Quantity ascending
# 5. Get the top 5 products by sales
# 6. Get the bottom 5 products by sales
# 7. Print all results
```

**Mini Project** – Sales Ranking System:
Create a program that:
1. Creates a DataFrame with product sales data (Product, Region, Sales, Quantity).
2. Calculates total sales by product.
3. Ranks products by sales (top 10).
4. Finds the best-selling product in each region.
5. Finds the worst-selling product in each region.
6. Sorts the data and prints the rankings.

---

### Summary and Revision Notes

- `df.sort_values('col')` – sort by column.
- `ascending=False` for descending.
- Sort by multiple columns: `df.sort_values(['col1', 'col2'])`.
- `sort_index()` sorts by index.
- `na_position` controls NaN placement.

---

## Lesson 4.9 – GroupBy

### Concept Explanation

**GroupBy** is one of Pandas' most powerful features. It follows the **split-apply-combine** pattern:
1. **Split**: Split the data into groups based on some criteria.
2. **Apply**: Apply a function to each group independently.
3. **Combine**: Combine the results into a new data structure.

**Basic syntax**:
```python
df.groupby('column')['column_to_aggregate'].agg(function)
```

**Common aggregation functions**:
- `sum()`, `mean()`, `median()`, `min()`, `max()`, `count()`, `size()`, `std()`, `var()`.

**Multiple aggregations**:
```python
df.groupby('col').agg({'col1': 'sum', 'col2': 'mean'})
```

**Custom aggregations**:
```python
df.groupby('col').agg(lambda x: x.max() - x.min())
```

---

### Importance and Real-World Use Cases

- **Why it matters**: GroupBy is how you summarise and analyse data by categories – sales by region, average salary by department, etc. It's essential for any analytical task.

- **Use cases**:
  - A **data analyst** calculates total sales by region.
  - A **financial analyst** calculates average expenses by department.
  - A **data scientist** groups data for feature engineering.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np

# Create sample data
np.random.seed(42)
df = pd.DataFrame({
    'Department': np.random.choice(['IT', 'HR', 'Finance', 'Marketing'], 20),
    'Region': np.random.choice(['North', 'South', 'East', 'West'], 20),
    'Employee': [f'Employee_{i}' for i in range(1, 21)],
    'Salary': np.random.randint(40000, 100000, 20),
    'Bonus': np.random.randint(0, 10000, 20)
})
print("Original DataFrame (first 5 rows):\n", df.head())

# Basic GroupBy
print("\n--- Basic GroupBy ---")
print("Average salary by department:\n", df.groupby('Department')['Salary'].mean())

# Multiple aggregations
print("\n--- Multiple Aggregations ---")
print("Salary by department (min, max, mean, count):\n", 
      df.groupby('Department')['Salary'].agg(['min', 'max', 'mean', 'count']))

# Multiple columns, multiple aggregations
print("\n--- Multiple Columns & Aggregations ---")
print("Salary and Bonus by department:\n", 
      df.groupby('Department').agg({'Salary': ['mean', 'sum'], 'Bonus': ['mean', 'max']}))

# GroupBy with .value_counts()
print("\n--- Department counts ---")
print(df['Department'].value_counts())

# GroupBy with .size()
print("\n--- Department size ---")
print(df.groupby('Department').size())

# GroupBy with .describe()
print("\n--- Department describe ---")
print(df.groupby('Department')['Salary'].describe())

# GroupBy with custom function
print("\n--- Custom Aggregation (range) ---")
print(df.groupby('Department')['Salary'].agg(lambda x: x.max() - x.min()))

# GroupBy with multiple columns
print("\n--- Group by Department and Region ---")
print(df.groupby(['Department', 'Region'])['Salary'].mean())

# GroupBy with .transform() (returns same shape)
print("\n--- Transform (salary as % of department average) ---")
df['Salary_Pct'] = df['Salary'] / df.groupby('Department')['Salary'].transform('mean')
print(df[['Employee', 'Department', 'Salary', 'Salary_Pct']].head())

# GroupBy with .apply()
print("\n--- Apply custom function ---")
def top_salary_group(group):
    return group.nlargest(2, 'Salary')

print(df.groupby('Department').apply(top_salary_group))
```

**Pivot Table vs GroupBy**:

```python
# Pivot table is similar to GroupBy with unstack
pivot = df.pivot_table(values='Salary', index='Department', columns='Region', aggfunc='mean')
print("\n--- Pivot Table ---\n", pivot)
```

---

### Practical Examples

- **Example 1**: Calculating average sales by product category.
- **Example 2**: Finding the maximum revenue by region.
- **Example 3**: Counting the number of orders by customer segment.

---

### Hands-on Coding Exercises

**Exercise 4.18** – Basic GroupBy:
```python
# 1. Create a DataFrame with columns: Category, Sales, Quantity, Region
# 2. Calculate total sales by Category
# 3. Calculate average sales by Category
# 4. Calculate total quantity by Region
# 5. Calculate average quantity by Category
# 6. Print all results
```

**Exercise 4.19** – Multiple aggregations:
```python
# 1. Calculate min, max, mean, count for sales by Category
# 2. Calculate sum and mean for both sales and quantity by Category
# 3. Calculate the range (max - min) for sales by Region
# 4. Print all results
```

---

### Mini Quiz

1. What is the split-apply-combine pattern?
2. How do you calculate the average of a column by groups?
3. How do you perform multiple aggregations on a GroupBy?
4. What is the difference between `.agg()` and `.transform()`?
5. How do you group by multiple columns?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to specify the aggregation function | Always specify `mean()`, `sum()`, etc. |
| Using `.size()` when you want `.count()` | `.size()` counts all rows, `.count()` excludes nulls |
| Not handling NaNs in GroupBy | Use `dropna=False` to include NaNs |
| Using `.apply()` for simple aggregations | Use `.agg()` for better performance |

---

### Interview Questions

1. **What is the purpose of `groupby` in Pandas?**  
   *Answer*: `groupby` is used to split data into groups based on criteria, apply a function to each group, and combine the results. It's used for summarising and aggregating data.

2. **What is the difference between `.agg()` and `.apply()` in GroupBy?**  
   *Answer*: `.agg()` is used for built-in and simple aggregations (sum, mean, etc.). `.apply()` is more flexible and can be used for custom operations, but is slower.

3. **How do you group by multiple columns?**  
   *Answer*: `df.groupby(['col1', 'col2'])`.

---

### Assignment and Mini Project

**Assignment 4.9** – GroupBy practice:
```python
# 1. Create a DataFrame with columns: Product, Category, Sales, Region, Date
# 2. Calculate total sales by Category
# 3. Calculate average sales by Category
# 4. Calculate total sales by Region
# 5. Calculate min, max, mean, count for sales by Category
# 6. Calculate sum and mean for sales and quantity by Category
# 7. Group by Category and Region and calculate total sales
# 8. Print all results
```

**Mini Project** – Sales Summary Tool:
Create a program that:
1. Generates a sales dataset (Product, Category, Region, Sales, Quantity, Date).
2. Provides functions to generate summaries:
   - Total sales by Category.
   - Total sales by Region.
   - Average sales by Category and Region.
   - Top products by sales.
   - Monthly sales summary.
3. Displays each summary in a readable format.
4. Exports the summaries to separate sheets in an Excel file.

---

### Summary and Revision Notes

- `df.groupby('col')['other'].function()` – basic aggregation.
- `.agg()` for multiple functions.
- `.transform()` for same-shape operations.
- `.size()` counts all rows.
- `.value_counts()` for frequency counts.
- Group by multiple columns: `.groupby(['col1', 'col2'])`.

---

## Lesson 4.10 – Merge, Join, and Concatenate

### Concept Explanation

Combining datasets is a fundamental data analysis task. Pandas provides three main functions:

**1. `pd.concat()` – concatenate (stack) rows or columns**
- Rows: `pd.concat([df1, df2], axis=0)`.
- Columns: `pd.concat([df1, df2], axis=1)`.

**2. `pd.merge()` – database-style joins**
- `how`: 'inner', 'outer', 'left', 'right'.
- `on`: column(s) to join on.
- `left_on` / `right_on`: when column names differ.

**3. `df.join()` – join on index**
- Simplified version of merge for index-based joins.

**Join types**:

| **Type** | **Description** | **Example** |
|----------|-----------------|-------------|
| **Inner** | Only matching rows | `pd.merge(df1, df2, how='inner', on='key')` |
| **Outer** | All rows from both | `pd.merge(df1, df2, how='outer', on='key')` |
| **Left** | All rows from left | `pd.merge(df1, df2, how='left', on='key')` |
| **Right** | All rows from right | `pd.merge(df1, df2, how='right', on='key')` |

---

### Importance and Real-World Use Cases

- **Why it matters**: Data rarely lives in a single table. You'll often need to combine multiple datasets – joining customer data with orders, merging regional data with sales, etc.

- **Use cases**:
  - A **data analyst** joins sales data with product data.
  - A **data scientist** merges customer demographics with transaction history.
  - A **financial analyst** combines budget data with actuals.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np

# Create sample dataframes
df1 = pd.DataFrame({
    'ID': [1, 2, 3, 4],
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana'],
    'Department': ['HR', 'IT', 'Finance', 'IT']
})
print("df1:\n", df1)

df2 = pd.DataFrame({
    'ID': [1, 2, 3, 5],
    'Salary': [50000, 60000, 70000, 80000],
    'Bonus': [5000, 6000, 7000, 8000]
})
print("\ndf2:\n", df2)

df3 = pd.DataFrame({
    'EmpID': [1, 2, 3, 4],
    'City': ['New York', 'London', 'Paris', 'Tokyo'],
    'StartDate': ['2020-01-01', '2020-06-01', '2020-03-01', '2020-09-01']
})
print("\ndf3:\n", df3)

# Inner Join
print("\n--- Inner Join (only matching) ---")
inner = pd.merge(df1, df2, on='ID', how='inner')
print(inner)

# Left Join
print("\n--- Left Join (all from df1) ---")
left = pd.merge(df1, df2, on='ID', how='left')
print(left)

# Right Join
print("\n--- Right Join (all from df2) ---")
right = pd.merge(df1, df2, on='ID', how='right')
print(right)

# Outer Join
print("\n--- Outer Join (all from both) ---")
outer = pd.merge(df1, df2, on='ID', how='outer')
print(outer)

# Merge with different column names
print("\n--- Merge with different column names ---")
merged = pd.merge(df1, df3, left_on='ID', right_on='EmpID', how='left')
print(merged)

# Concatenate rows
print("\n--- Concatenate rows (stack) ---")
df4 = pd.DataFrame({
    'ID': [5, 6],
    'Name': ['Eve', 'Frank'],
    'Department': ['Marketing', 'HR']
})
concat_rows = pd.concat([df1, df4], axis=0, ignore_index=True)
print(concat_rows)

# Concatenate columns
print("\n--- Concatenate columns (side by side) ---")
concat_cols = pd.concat([df1, df2['Salary']], axis=1)
print(concat_cols)

# Join on index
print("\n--- Join on index ---")
df1_idx = df1.set_index('ID')
df2_idx = df2.set_index('ID')
join_idx = df1_idx.join(df2_idx, how='inner')
print(join_idx)
```

**Merging with Multiple Keys**:

```python
df1 = pd.DataFrame({
    'Region': ['North', 'North', 'South', 'South'],
    'Year': [2020, 2021, 2020, 2021],
    'Sales': [100, 110, 120, 130]
})
df2 = pd.DataFrame({
    'Region': ['North', 'North', 'South', 'South'],
    'Year': [2020, 2021, 2020, 2021],
    'Target': [90, 100, 110, 120]
})

print("\n--- Merge on multiple keys ---")
merged = pd.merge(df1, df2, on=['Region', 'Year'], how='outer')
print(merged)
```

---

### Practical Examples

- **Example 1**: Joining sales data with product information.
- **Example 2**: Concatenating monthly sales data.
- **Example 3**: Merging customer data with orders.

---

### Hands-on Coding Exercises

**Exercise 4.20** – Merging practice:
```python
# 1. Create two DataFrames with a common key column
# 2. Perform inner join
# 3. Perform left join
# 4. Perform right join
# 5. Perform outer join
# 6. Print all results
```

**Exercise 4.21** – Concatenation:
```python
# 1. Create two DataFrames with the same columns
# 2. Concatenate them vertically (rows)
# 3. Create two DataFrames with different columns but same rows
# 4. Concatenate them horizontally (columns)
# 5. Print the results
```

---

### Mini Quiz

1. What is the difference between `pd.concat()` and `pd.merge()`?
2. What are the four join types?
3. How do you join on columns with different names?
4. What is the default join type in `pd.merge()`?
5. How do you concatenate DataFrames vertically?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Joining on non-unique keys causing duplicates | Check for duplicates before joining |
| Forgetting to specify the join type | Specify `how` explicitly |
| Using `concat` with `axis=0` when `axis=1` is intended | Always check the axis parameter |
| Joining on different data types | Ensure key columns have the same data type |

---

### Interview Questions

1. **What is the difference between `pd.merge()` and `pd.concat()`?**  
   *Answer*: `pd.merge()` performs database-style joins on common columns. `pd.concat()` stacks DataFrames along rows or columns without requiring a common key.

2. **What are the four join types in Pandas?**  
   *Answer*: Inner, Left, Right, and Outer.

3. **How do you merge DataFrames on different column names?**  
   *Answer*: Using `left_on` and `right_on` parameters.

---

### Assignment and Mini Project

**Assignment 4.10** – Combining data:
```python
# 1. Create three DataFrames: employees, departments, salaries
# 2. Merge employees with departments on department_id
# 3. Merge the result with salaries on employee_id
# 4. Perform inner, left, and outer joins
# 5. Concatenate two employee DataFrames
# 6. Print all results
```

**Mini Project** – Data Integration Tool:
Create a program that:
1. Creates three related DataFrames (Orders, Customers, Products).
2. Joins them to create a complete sales dataset.
3. Creates a summary showing:
   - Total sales by customer.
   - Total sales by product.
   - Customer details with their orders.
4. Exports the joined dataset to CSV and Excel.
5. Handles different join types and missing data.

---

### Summary and Revision Notes

- `pd.concat()`: stack vertically or horizontally.
- `pd.merge()`: join on columns (SQL-style).
- Join types: inner, outer, left, right.
- `df.join()`: join on index.
- Use `on` for common column names.
- Use `left_on` and `right_on` for different names.

---

## Lesson 4.11 – Missing Values

### Concept Explanation

Real-world data almost always has missing values. Pandas represents missing values as `NaN` (Not a Number). Handling missing values is critical for accurate analysis.

**Detecting missing values**:
- `df.isnull()` – returns True for missing values.
- `df.notnull()` – returns False for missing values.
- `df.isnull().sum()` – counts missing values per column.

**Handling missing values**:
- `df.dropna()` – drop rows/columns with missing values.
- `df.fillna(value)` – fill missing values with a value.
- `df.fillna(method='ffill')` – forward fill.
- `df.fillna(method='bfill')` – backward fill.
- `df.interpolate()` – interpolate values.

**Parameters**:
- `axis`: 0 (rows) or 1 (columns).
- `subset`: columns to check for missing values.
- `how`: 'any' (drop if any missing) or 'all' (drop if all missing).
- `thresh`: minimum number of non-null values to keep.

---

### Importance and Real-World Use Cases

- **Why it matters**: Missing data can skew results, break calculations, and lead to wrong conclusions. Handling it correctly is essential for reliable analysis.

- **Use cases**:
  - A **data analyst** imputes missing sales data.
  - A **data scientist** removes rows with missing target values.
  - A **financial analyst** fills missing transaction data.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np

# Create data with missing values
np.random.seed(42)
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana', 'Eve'],
    'Age': [25, np.nan, 35, 40, np.nan],
    'Salary': [50000, 60000, np.nan, 80000, 55000],
    'Department': ['HR', 'IT', 'Finance', np.nan, 'HR'],
    'StartDate': ['2020-01-01', '2020-06-01', np.nan, '2020-09-01', '2020-11-01']
})
print("Original:\n", df)

# Detecting missing values
print("\n--- Detecting Missing Values ---")
print("Is null:\n", df.isnull())
print("\nCount of missing values:\n", df.isnull().sum())

# Drop missing values
print("\n--- Dropping Missing Values ---")
print("Drop rows with any missing value:\n", df.dropna())
print("\nDrop rows where all values are missing:\n", df.dropna(how='all'))
print("\nDrop rows where Age is missing:\n", df.dropna(subset=['Age']))

# Fill missing values
print("\n--- Filling Missing Values ---")
print("Fill with a specific value (0):\n", df.fillna(0))
print("\nFill with forward fill:\n", df.fillna(method='ffill'))
print("\nFill with backward fill:\n", df.fillna(method='bfill'))

# Fill with column-specific values
print("\n--- Column-specific filling ---")
df_filled = df.copy()
df_filled['Age'] = df_filled['Age'].fillna(df_filled['Age'].mean())
df_filled['Salary'] = df_filled['Salary'].fillna(df_filled['Salary'].median())
df_filled['Department'] = df_filled['Department'].fillna('Unknown')
df_filled['StartDate'] = df_filled['StartDate'].fillna('2020-01-01')
print("Filled with column-specific values:\n", df_filled)

# Interpolation
print("\n--- Interpolation ---")
df_interp = df.copy()
df_interp['Age'] = df_interp['Age'].interpolate(method='linear')
print("Interpolated Age:\n", df_interp)

# Forward fill with limit
print("\n--- Forward fill with limit ---")
df_ffill = df.copy()
df_ffill['Age'] = df_ffill['Age'].fillna(method='ffill', limit=1)
print(df_ffill)
```

**Missing Value Strategies**:

```python
print("\n--- Strategies for Missing Values ---")
print("1. Drop rows with missing values")
print("2. Drop columns with missing values")
print("3. Fill with a constant (0, 'Unknown')")
print("4. Fill with statistics (mean, median, mode)")
print("5. Fill with forward/backward fill")
print("6. Interpolate")
```

---

### Practical Examples

- **Example 1**: Removing rows with missing target values.
- **Example 2**: Imputing missing age values with the mean.
- **Example 3**: Filling missing categorical values with 'Unknown'.

---

### Hands-on Coding Exercises

**Exercise 4.22** – Missing value detection:
```python
# 1. Create a DataFrame with missing values
# 2. Identify missing values
# 3. Count missing values per column
# 4. Print columns with missing values
# 5. Print the percentage of missing values
```

**Exercise 4.23** – Missing value handling:
```python
# 1. Drop rows with any missing value
# 2. Drop rows where a specific column is missing
# 3. Fill missing numeric values with mean
# 4. Fill missing categorical values with 'Unknown'
# 5. Forward fill missing values
# 6. Interpolate missing values
# 7. Print the results
```

---

### Mini Quiz

1. What is the `NaN` value in Pandas?
2. How do you check for missing values?
3. What is the difference between `dropna()` and `fillna()`?
4. How do you fill missing values with the mean?
5. What is interpolation?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Ignoring missing values entirely | Always check for missing values |
| Filling with mean without considering the distribution | Consider using median for skewed data |
| Dropping rows with missing values without checking the impact | Evaluate the impact before dropping |
| Using `fillna(0)` for all columns | Use column-specific strategies |
| Not handling missing values in datetime columns | Use appropriate date imputation strategies |

---

### Interview Questions

1. **How do you handle missing values in Pandas?**  
   *Answer*: First, detect with `isnull().sum()`. Then, either drop with `dropna()` or fill with `fillna()` using a constant, statistic, or method like forward fill.

2. **What is the difference between dropping and imputing missing values?**  
   *Answer*: Dropping removes rows/columns with missing values. Imputing fills them with estimated values, preserving data but potentially introducing bias.

3. **How do you fill missing values with the column mean?**  
   *Answer*: `df['col'] = df['col'].fillna(df['col'].mean())`.

---

### Assignment and Mini Project

**Assignment 4.11** – Missing value handling:
```python
# 1. Create a DataFrame with 20 rows and 5 columns, with 10-15% missing values
# 2. Identify columns with missing values
# 3. Drop rows where any value is missing
# 4. Drop rows where a specific column is missing
# 5. Fill missing values with:
#    a. 0 for numeric columns
#    b. 'Unknown' for categorical columns
#    c. Mean for a numeric column
#    d. Median for another numeric column
# 6. Forward fill and backward fill
# 7. Print the results
```

**Mini Project** – Data Imputation Tool:
Create a program that:
1. Loads a dataset with missing values (or creates one).
2. Identifies and reports missing values per column.
3. Provides options to:
   - Drop rows with missing values.
   - Drop columns with missing values.
   - Fill with a constant.
   - Fill with mean/median/mode.
   - Fill with forward/backward fill.
   - Interpolate.
4. Shows the before and after comparison.
5. Saves the cleaned dataset to a new file.

---

### Summary and Revision Notes

- `df.isnull().sum()` – count missing values.
- `df.dropna()` – remove missing values.
- `df.fillna(value)` – fill with a value.
- `method='ffill'` / `'bfill'` – forward/backward fill.
- `df.interpolate()` – interpolate missing values.
- Column-specific strategies: mean, median, mode, constant, 'Unknown'.

---

## Lesson 4.12 – Duplicate Data

### Concept Explanation

Duplicate data can inflate counts, skew averages, and lead to incorrect conclusions. Pandas provides tools to identify and handle duplicates.

**Detecting duplicates**:
- `df.duplicated()` – returns a boolean Series.
- `df.duplicated(subset=['col1', 'col2'])` – check specific columns.

**Removing duplicates**:
- `df.drop_duplicates()` – removes duplicate rows.
- `df.drop_duplicates(subset=['col1', 'col2'])` – checks specific columns.
- `df.drop_duplicates(keep='first')` – keeps first occurrence (default).
- `df.drop_duplicates(keep='last')` – keeps last occurrence.
- `df.drop_duplicates(keep=False)` – removes all duplicates.

---

### Importance and Real-World Use Cases

- **Why it matters**: Duplicates are common in data from multiple sources, surveys, and transactional systems. Removing them ensures data integrity.

- **Use cases**:
  - A **data analyst** removes duplicate customer records.
  - A **data scientist** deduplicates training data.
  - A **financial analyst** removes duplicate transactions.

---

### Step-by-Step Demonstration

```python
import pandas as pd

# Create data with duplicates
df = pd.DataFrame({
    'ID': [1, 2, 3, 1, 2, 4, 5, 3],
    'Name': ['Alice', 'Bob', 'Charlie', 'Alice', 'Bob', 'Diana', 'Eve', 'Charlie'],
    'City': ['NYC', 'London', 'Paris', 'NYC', 'London', 'Tokyo', 'Sydney', 'Paris'],
    'Age': [25, 30, 35, 25, 30, 40, 28, 35]
})
print("Original (with duplicates):\n", df)

# Detecting duplicates
print("\n--- Detecting Duplicates ---")
print("Duplicate rows (first occurrence):\n", df.duplicated())
print("\nDuplicate rows (all):\n", df.duplicated(keep=False))

# Count duplicates
print(f"\nNumber of duplicate rows: {df.duplicated().sum()}")

# Identify duplicate rows based on specific columns
print("\n--- Duplicates based on 'ID' and 'Name' ---")
print(df.duplicated(subset=['ID', 'Name']))

# Removing duplicates
print("\n--- Removing Duplicates ---")
print("Keep first occurrence:\n", df.drop_duplicates())
print("\nKeep last occurrence:\n", df.drop_duplicates(keep='last'))
print("\nRemove all duplicates (keep=False):\n", df.drop_duplicates(keep=False))

# Removing duplicates based on specific columns
print("\n--- Remove duplicates based on 'ID' only ---")
print(df.drop_duplicates(subset=['ID']))

# Removing duplicates with reset_index
print("\n--- Remove duplicates and reset index ---")
df_dedup = df.drop_duplicates().reset_index(drop=True)
print(df_dedup)

# Checking for duplicates after removal
print(f"\nDuplicates after removal: {df_dedup.duplicated().sum()}")
```

---

### Practical Examples

- **Example 1**: Removing duplicate customer records based on email.
- **Example 2**: Deduplicating transaction data by transaction ID.
- **Example 3**: Keeping the latest record based on a timestamp.

---

### Hands-on Coding Exercises

**Exercise 4.24** – Duplicate detection:
```python
# 1. Create a DataFrame with 15 rows, including duplicates
# 2. Identify duplicate rows
# 3. Identify duplicates based on specific columns
# 4. Count duplicates
# 5. Print the duplicate rows
# 6. Print the rows that are duplicates (all occurrences)
```

**Exercise 4.25** – Duplicate removal:
```python
# 1. Remove all duplicates (keep first)
# 2. Remove all duplicates (keep last)
# 3. Remove duplicates based on specific columns
# 4. Remove all duplicates (keep=False)
# 5. Reset the index after removal
# 6. Print the results
```

---

### Mini Quiz

1. What function is used to detect duplicates?
2. What is the default `keep` value in `drop_duplicates()`?
3. How do you remove duplicates based on specific columns?
4. How do you keep the last occurrence of duplicates?
5. How do you count duplicate rows?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Removing duplicates without understanding the data | Investigate duplicates first |
| Not resetting the index after dropping duplicates | Use `reset_index(drop=True)` |
| Using `keep=False` when you still need one copy | Use `keep='first'` or `'last'` unless you need to remove all |
| Not checking for duplicates after merging | Always check for duplicates after joins |

---

### Interview Questions

1. **How do you remove duplicate rows from a DataFrame?**  
   *Answer*: Using `df.drop_duplicates()`.

2. **How do you remove duplicates based on a subset of columns?**  
   *Answer*: `df.drop_duplicates(subset=['col1', 'col2'])`.

3. **How do you keep the last occurrence when removing duplicates?**  
   *Answer*: `df.drop_duplicates(keep='last')`.

---

### Assignment and Mini Project

**Assignment 4.12** – Duplicate handling:
```python
# 1. Create a DataFrame with 20 rows and 4 columns, including duplicates
# 2. Identify and count duplicates
# 3. Remove duplicates (keep first)
# 4. Remove duplicates (keep last)
# 5. Remove duplicates based on two columns
# 6. Remove all duplicates (keep=False)
# 7. Reset the index
# 8. Print the results
```

**Mini Project** – Data Deduplication Tool:
Create a program that:
1. Generates a dataset with duplicate records.
2. Provides functions to:
   - Identify duplicate rows.
   - Identify duplicates by specific columns.
   - Remove duplicates (with options: keep first, keep last, remove all).
   - Remove duplicates by subset.
3. Shows before and after row counts.
4. Exports the cleaned data.

---

### Summary and Revision Notes

- `df.duplicated()` – detects duplicates.
- `df.drop_duplicates()` – removes duplicates.
- `keep='first'` (default), `keep='last'`, `keep=False`.
- `subset` for specific columns.
- Reset index after removal: `reset_index(drop=True)`.

---

## Lesson 4.13 – Data Cleaning and Transformation

### Concept Explanation

Data cleaning and transformation are critical steps in any data analysis pipeline. Pandas provides a wide range of tools for cleaning and transforming data.

**Common cleaning tasks**:
- **Renaming columns**: `df.rename(columns={'old': 'new'})`.
- **Changing data types**: `df.astype({'col': 'type'})`.
- **String manipulation**: `df['col'].str.upper()`, `.str.strip()`, etc.
- **Date conversion**: `pd.to_datetime()`.
- **Categorical data**: `pd.Categorical()`.
- **Clipping outliers**: `df['col'].clip(lower, upper)`.
- **Binning**: `pd.cut()` and `pd.qcut()`.
- **Applying functions**: `df.apply()`.

**Transformation operations**:
- `df.apply()` – apply a function to rows/columns.
- `df.map()` – map values in a Series.
- `df.replace()` – replace values.
- `df.transform()` – transform data with aggregation.

---

### Importance and Real-World Use Cases

- **Why it matters**: Raw data is rarely analysis-ready. Cleaning and transforming make it usable, consistent, and meaningful.

- **Use cases**:
  - A **data analyst** cleans text data (strip spaces, standardise case).
  - A **data scientist** converts date strings to datetime.
  - A **financial analyst** bins data into categories (age groups, income brackets).

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np

# Create messy data
df = pd.DataFrame({
    'Name': [' Alice ', ' Bob', 'Charlie ', ' Diana', ' Eve '],
    'Age': [25, 30, 'thirty-five', 40, 28],
    'Salary': ['$50,000', '$60,000', '$70,000', '$80,000', '$55,000'],
    'Join_Date': ['2020-01-01', '2020-06-01', '2020-03-01', '2020-09-01', '2020-11-01'],
    'Email': ['alice@example.com', 'bob@example.com', 'charlie@example.com', 
              'diana@example.com', 'eve@example.com']
})
print("Original messy data:\n", df)

# 1. Renaming columns
print("\n--- Renaming Columns ---")
df_clean = df.rename(columns={'Join_Date': 'Start_Date'})
print(df_clean.columns.tolist())

# 2. String cleaning (strip whitespace, title case)
print("\n--- String Cleaning ---")
df['Name'] = df['Name'].str.strip()
df['Name'] = df['Name'].str.title()
print(df['Name'])

# 3. Email domain extraction
print("\n--- Domain Extraction ---")
df['Domain'] = df['Email'].str.split('@').str[1]
print(df[['Email', 'Domain']])

# 4. Converting dates
print("\n--- Date Conversion ---")
df['Start_Date'] = pd.to_datetime(df['Join_Date'])
print(df[['Join_Date', 'Start_Date']])

# 5. Cleaning salary data
print("\n--- Cleaning Salary ---")
df['Salary'] = df['Salary'].str.replace('$', '').str.replace(',', '').astype(float)
print(df['Salary'])

# 6. Categorical data
print("\n--- Categorical ---")
df['Age_Group'] = pd.cut(df['Age'], bins=[0, 30, 40, 100], labels=['Young', 'Middle', 'Senior'])
print(df[['Age', 'Age_Group']])

# 7. Clipping outliers
print("\n--- Clipping Outliers ---")
df['Salary_Clipped'] = df['Salary'].clip(lower=45000, upper=75000)
print(df[['Salary', 'Salary_Clipped']])

# 8. Using .apply()
print("\n--- Using .apply() ---")
def get_initials(name):
    return ''.join([part[0] for part in name.split()])

df['Initials'] = df['Name'].apply(get_initials)
print(df[['Name', 'Initials']])

# 9. Using .map()
print("\n--- Using .map() ---")
age_map = {25: '25-30', 28: '25-30', 30: '30-35', 35: '35-40', 40: '40-45'}
df['Age_Bin'] = df['Age'].map(age_map)
print(df[['Age', 'Age_Bin']])

# 10. Using .replace()
print("\n--- Using .replace() ---")
df['Department'] = ['HR', 'IT', 'Finance', 'IT', 'HR']
df['Department'] = df['Department'].replace({'IT': 'Technology', 'HR': 'Human Resources'})
print(df[['Department']])
```

**String Operations**:

```python
# Common string methods
print("\n--- String Operations ---")
df['Email_Upper'] = df['Email'].str.upper()
df['Email_Lower'] = df['Email'].str.lower()
df['Name_Length'] = df['Name'].str.len()
df['Contains_Alice'] = df['Name'].str.contains('Alice')
print(df[['Name', 'Name_Length', 'Contains_Alice']])
```

**Handling Missing Data in Cleaning**:

```python
# Fill missing values
df_clean = df.copy()
df_clean.loc[0, 'Salary'] = np.nan
print("\n--- Handling Missing Data ---")
print("Before:\n", df_clean[['Name', 'Salary']])
df_clean['Salary'] = df_clean['Salary'].fillna(df_clean['Salary'].mean())
print("After:\n", df_clean[['Name', 'Salary']])
```

---

### Practical Examples

- **Example 1**: Cleaning a customer dataset: strip whitespace, standardise case, fix dates.
- **Example 2**: Preparing sales data: clean currency strings, convert to numeric.
- **Example 3**: Transforming employee data: bin ages, create categories.

---

### Hands-on Coding Exercises

**Exercise 4.26** – Column renaming and type conversion:
```python
# 1. Create a DataFrame with messy column names
# 2. Rename columns to clean names
# 3. Convert a date string column to datetime
# 4. Convert a numeric string column to float
# 5. Print the results
```

**Exercise 4.27** – String cleaning:
```python
# 1. Strip whitespace from a column
# 2. Convert a column to title case
# 3. Extract a substring (e.g., domain from email)
# 4. Replace a pattern in a string column
# 5. Check if a string column contains a substring
# 6. Print the results
```

---

### Mini Quiz

1. How do you rename a column in Pandas?
2. How do you strip whitespace from a string column?
3. How do you convert a string column to datetime?
4. How do you apply a function to each element in a column?
5. What is the purpose of `pd.cut()`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Modifying the original DataFrame without `.copy()` | Use `.copy()` if you need to keep the original |
| Not checking data types after conversion | Always verify with `df.dtypes` |
| Using `apply()` for simple operations | Use vectorized operations when possible |
| Not handling nulls before transformations | Fill or drop nulls first |

---

### Interview Questions

1. **How do you clean string data in Pandas?**  
   *Answer*: Using `.str` accessor: `df['col'].str.strip()`, `.str.upper()`, `.str.replace()`, etc.

2. **How do you convert a string column to datetime?**  
   *Answer*: `pd.to_datetime(df['column'])`.

3. **What is the difference between `.map()` and `.apply()`?**  
   *Answer*: `.map()` applies a function or mapping to a Series. `.apply()` applies a function to a Series (row-wise) or DataFrame (column-wise).

---

### Assignment and Mini Project

**Assignment 4.13** – Data cleaning:
```python
# 1. Create a messy DataFrame with:
#    - Columns with whitespace in names
#    - Date strings in different formats
#    - Currency strings with $ and commas
#    - Text with inconsistent case
#    - Missing values
# 2. Clean the data:
#    - Rename columns
#    - Strip whitespace
#    - Standardise case
#    - Convert dates to datetime
#    - Convert currency to float
#    - Fill missing values
#    - Create a new column (e.g., age group)
# 3. Print the cleaned DataFrame
```

**Mini Project** – Data Cleaning Pipeline:
Create a program that:
1. Generates a messy dataset with common issues.
2. Defines a cleaning pipeline:
   - Rename columns to snake_case.
   - Strip and standardise text columns.
   - Convert dates to datetime.
   - Convert currency and numeric strings to numbers.
   - Handle missing values.
   - Create derived columns (e.g., age groups, domains).
3. Applies the pipeline step by step.
4. Shows the before and after comparison.
5. Saves the cleaned data to a CSV file.

---

### Summary and Revision Notes

- `df.rename()` – rename columns.
- `df.astype()` – change data types.
- `.str` – string operations.
- `pd.to_datetime()` – date conversion.
- `pd.cut()` – binning.
- `df.apply()` – custom operations.
- `df.map()` – value mapping.
- `df.replace()` – value replacement.

---

## Lesson 4.14 – Pivot Tables

### Concept Explanation

**Pivot tables** are a powerful data summarisation tool. They allow you to:
- Aggregate data by multiple dimensions.
- Reshape data from long to wide format.
- Create cross-tabulations.

**Syntax**:
```python
pd.pivot_table(data, values, index, columns, aggfunc, fill_value)
```

**Key parameters**:
- `values`: column(s) to aggregate.
- `index`: grouping variable(s) for rows.
- `columns`: grouping variable(s) for columns.
- `aggfunc`: aggregation function (default: 'mean').
- `fill_value`: value to replace NaN.
- `margins`: include subtotals (True/False).

**Comparison with GroupBy**:
- `pivot_table()` creates a wide format table.
- `groupby()` creates a long format table.

---

### Importance and Real-World Use Cases

- **Why it matters**: Pivot tables are essential for summarising and presenting data in a cross-tabulated format, similar to Excel pivot tables.

- **Use cases**:
  - A **data analyst** summarises sales by product and region.
  - A **financial analyst** creates a budget vs actual pivot table.
  - A **marketing analyst** analyses campaign performance by channel and month.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np

# Create sample data
np.random.seed(42)
df = pd.DataFrame({
    'Product': np.random.choice(['A', 'B', 'C', 'D'], 100),
    'Region': np.random.choice(['North', 'South', 'East', 'West'], 100),
    'Quarter': np.random.choice(['Q1', 'Q2', 'Q3', 'Q4'], 100),
    'Sales': np.random.randint(100, 500, 100),
    'Quantity': np.random.randint(10, 100, 100)
})
print("Sample data (first 5 rows):\n", df.head())

# Basic pivot table
print("\n--- Basic Pivot Table (mean sales by Product and Region) ---")
pivot1 = pd.pivot_table(df, values='Sales', index='Product', columns='Region', aggfunc='mean')
print(pivot1)

# With sum and margins
print("\n--- Pivot Table with Sum and Margins ---")
pivot2 = pd.pivot_table(df, values='Sales', index='Product', columns='Region', 
                        aggfunc='sum', margins=True)
print(pivot2)

# Multiple values
print("\n--- Pivot Table with Multiple Values ---")
pivot3 = pd.pivot_table(df, values=['Sales', 'Quantity'], index='Product', 
                        columns='Region', aggfunc='sum')
print(pivot3)

# Multiple aggregation functions
print("\n--- Pivot Table with Multiple Aggregations ---")
pivot4 = pd.pivot_table(df, values='Sales', index='Product', columns='Region', 
                        aggfunc=['sum', 'mean', 'count'])
print(pivot4)

# Using fill_value
print("\n--- Pivot Table with fill_value ---")
pivot5 = pd.pivot_table(df, values='Sales', index='Product', columns='Region', 
                        aggfunc='sum', fill_value=0)
print(pivot5)

# Multi-level index and columns
print("\n--- Pivot Table with Multi-level Index ---")
pivot6 = pd.pivot_table(df, values='Sales', index=['Product', 'Quarter'], 
                        columns='Region', aggfunc='sum')
print(pivot6)

# Year-over-year comparison (simulated)
# Actually, let's add a Year column
df['Year'] = np.random.choice([2020, 2021], 100)
pivot7 = pd.pivot_table(df, values='Sales', index='Year', columns='Quarter', 
                        aggfunc='sum', margins=True)
print("\n--- Pivot Table with Year and Quarter ---")
print(pivot7)
```

**Pivot Table vs GroupBy**:

```python
# Using groupby to achieve the same result
grouped = df.groupby(['Product', 'Region'])['Sales'].mean().unstack()
print("\n--- GroupBy with unstack (similar result) ---")
print(grouped)
```

**Crosstab**:

```python
# Crosstab for frequency counts
crosstab = pd.crosstab(df['Product'], df['Region'])
print("\n--- Crosstab (frequency counts) ---")
print(crosstab)

# Crosstab with values and aggregation
crosstab2 = pd.crosstab(df['Product'], df['Region'], values=df['Sales'], aggfunc='sum')
print("\n--- Crosstab with aggregation ---")
print(crosstab2)
```

---

### Practical Examples

- **Example 1**: Sales summary by product and region.
- **Example 2**: Employee statistics by department and job level.
- **Example 3**: Survey results by question and demographic.

---

### Hands-on Coding Exercises

**Exercise 4.28** – Basic pivot table:
```python
# 1. Create a DataFrame with columns: Product, Region, Sales, Quantity
# 2. Create a pivot table: mean sales by Product and Region
# 3. Create a pivot table: sum sales by Product and Region
# 4. Create a pivot table with margins
# 5. Print all results
```

**Exercise 4.29** – Advanced pivot table:
```python
# 1. Create a DataFrame with Product, Region, Quarter, Sales, Quantity
# 2. Pivot table with multiple values (Sales and Quantity)
# 3. Pivot table with multiple aggregations (sum and mean)
# 4. Pivot table with multi-level index (Product and Quarter)
# 5. Crosstab with frequency counts
# 6. Print all results
```

---

### Mini Quiz

1. What is a pivot table used for?
2. What is the default aggregation function in `pd.pivot_table()`?
3. What is the purpose of `margins`?
4. What is the difference between `pivot_table()` and `groupby()`?
5. What is `pd.crosstab()` used for?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to specify `values` | Always specify which column to aggregate |
| Using the wrong `aggfunc` | Choose the appropriate function (sum, mean, count, etc.) |
| Not handling NaN in pivot tables | Use `fill_value` to replace NaN |
| Confusing rows and columns | Double-check which fields go to `index` and which to `columns` |
| Using `pivot_table()` when `crosstab()` is more appropriate | Use `crosstab()` for frequency counts |

---

### Interview Questions

1. **What is the difference between `pivot_table()` and `groupby()`?**  
   *Answer*: `pivot_table()` creates a wide-format cross-tabulation with rows and columns. `groupby()` creates a long-format grouped DataFrame. They are often used together with `unstack()` to create similar results.

2. **What is the purpose of `margins` in `pivot_table()`?**  
   *Answer*: `margins` adds subtotals (row and column totals) to the pivot table.

3. **How do you create a pivot table with multiple aggregation functions?**  
   *Answer*: `pd.pivot_table(df, values='Sales', index='Product', columns='Region', aggfunc=['sum', 'mean'])`.

---

### Assignment and Mini Project

**Assignment 4.14** – Pivot table practice:
```python
# 1. Create a DataFrame with columns: Category, Region, Month, Sales
# 2. Create a pivot table: total sales by Category and Region
# 3. Create a pivot table: average sales by Category and Region
# 4. Create a pivot table with margins
# 5. Create a pivot table with multiple values (Sales and Quantity)
# 6. Create a crosstab for Category and Region counts
# 7. Print all results
```

**Mini Project** – Sales Summary Dashboard:
Create a program that:
1. Generates a sales dataset (Product, Region, Quarter, Sales, Quantity).
2. Creates pivot tables for:
   - Total sales by Product and Region.
   - Average sales by Product and Quarter.
   - Total sales by Region and Quarter.
   - Quantity breakdown by Product and Region.
3. Includes subtotals (margins).
4. Converts the pivot tables to CSV files.
5. Prints each pivot table in a readable format.

---

### Summary and Revision Notes

- `pd.pivot_table()` – summarises data.
- `values` – column to aggregate.
- `index` – row grouping.
- `columns` – column grouping.
- `aggfunc` – aggregation function (default 'mean').
- `margins` – add subtotals.
- `fill_value` – replace NaN.
- `pd.crosstab()` – frequency counts.

---

## Lesson 4.15 – MultiIndex

### Concept Explanation

**MultiIndex** (also called hierarchical indexing) allows you to have multiple levels of index or columns. This enables more complex data structures and operations.

**Key concepts**:
- **Hierarchical index**: Multiple levels on the same axis.
- **Levels**: Each level corresponds to a dimension.
- **MultiIndex creation**: `pd.MultiIndex.from_tuples()`, `pd.MultiIndex.from_arrays()`, etc.

**Common operations**:
- `df.set_index(['col1', 'col2'])` – set multi-level index.
- `df.reset_index()` – reset index.
- `df.xs()` – cross-section selection.
- `df.swaplevel()` – swap index levels.
- `df.reorder_levels()` – reorder levels.
- `df.unstack()` – convert index to columns.
- `df.stack()` – convert columns to index.

---

### Importance and Real-World Use Cases

- **Why it matters**: MultiIndex is useful for handling multi-dimensional data – e.g., time series with multiple entities, or data with multiple grouping levels.

- **Use cases**:
  - A **data analyst** uses MultiIndex for data with multiple grouping levels (e.g., Year/Quarter/Month).
  - A **data scientist** uses MultiIndex for panel data.
  - A **financial analyst** uses MultiIndex for financial statements with multiple accounts.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np

# Creating a MultiIndex DataFrame
# Method 1: From arrays
arrays = [
    ['A', 'A', 'B', 'B', 'C', 'C'],
    ['X', 'Y', 'X', 'Y', 'X', 'Y']
]
index = pd.MultiIndex.from_arrays(arrays, names=['Group', 'Subgroup'])
df = pd.DataFrame({
    'Value1': np.random.randint(10, 50, 6),
    'Value2': np.random.randint(100, 200, 6)
}, index=index)
print("MultiIndex DataFrame:\n", df)

# Method 2: From tuples
tuples = [('A', 'X'), ('A', 'Y'), ('B', 'X'), ('B', 'Y'), ('C', 'X'), ('C', 'Y')]
index2 = pd.MultiIndex.from_tuples(tuples, names=['Group', 'Subgroup'])
df2 = pd.DataFrame({
    'Value1': np.random.randint(10, 50, 6),
    'Value2': np.random.randint(100, 200, 6)
}, index=index2)
print("\nFrom tuples:\n", df2)

# Method 3: From a DataFrame (set_index)
df_flat = pd.DataFrame({
    'Group': ['A', 'A', 'B', 'B', 'C', 'C'],
    'Subgroup': ['X', 'Y', 'X', 'Y', 'X', 'Y'],
    'Value1': np.random.randint(10, 50, 6),
    'Value2': np.random.randint(100, 200, 6)
})
df_multi = df_flat.set_index(['Group', 'Subgroup'])
print("\nFrom DataFrame (set_index):\n", df_multi)

# Accessing data with MultiIndex
print("\n--- Accessing Data ---")
print("Index levels:", df.index.names)
print("Values at ('A', 'Y'):\n", df.loc[('A', 'Y')])

# Selecting by level
print("\n--- Selecting by Level ---")
print("All rows where Group = 'A':\n", df.loc['A'])

# Cross-section selection
print("\n--- Cross-section selection (xs) ---")
print("All rows where Subgroup = 'Y':\n", df.xs('Y', level='Subgroup'))

# Slicing with MultiIndex
print("\n--- Slicing with MultiIndex ---")
print("Rows from ('A', 'X') to ('B', 'Y'):\n", df.loc[('A', 'X'):('B', 'Y')])

# Swapping levels
print("\n--- Swapping Levels ---")
df_swapped = df.swaplevel()
print(df_swapped)

# Unstacking (convert index to columns)
print("\n--- Unstacking ---")
df_unstacked = df.unstack()
print(df_unstacked)

# Stacking (convert columns to index)
print("\n--- Stacking ---")
df_stacked = df_unstacked.stack()
print(df_stacked)

# Aggregation with MultiIndex
print("\n--- Aggregation with MultiIndex ---")
print("Sum by Group:\n", df.groupby(level='Group').sum())
```

**MultiIndex Columns**:

```python
# MultiIndex columns
cols = pd.MultiIndex.from_tuples([('A', 'X'), ('A', 'Y'), ('B', 'X'), ('B', 'Y')])
df_cols = pd.DataFrame(np.random.randint(10, 50, (4, 4)), columns=cols)
print("\nDataFrame with MultiIndex columns:\n", df_cols)

# Accessing columns with MultiIndex
print("\n--- Accessing MultiIndex Columns ---")
print("Column ('A', 'X'):\n", df_cols[('A', 'X')])
print("Level 'A':\n", df_cols['A'])
```

---

### Practical Examples

- **Example 1**: Time series data with multiple entities (e.g., stock prices for multiple companies).
- **Example 2**: Survey data with multiple questions and responses.
- **Example 3**: Financial data with multiple accounts and periods.

---

### Hands-on Coding Exercises

**Exercise 4.30** – MultiIndex creation:
```python
# 1. Create a MultiIndex from arrays (Department, Employee)
# 2. Create a MultiIndex from tuples
# 3. Create a MultiIndex from a DataFrame using set_index
# 4. Print all the DataFrames
```

**Exercise 4.31** – MultiIndex operations:
```python
# 1. Access data at a specific index
# 2. Select all rows for a specific level
# 3. Use xs to cross-section
# 4. Swap levels
# 5. Unstack and stack
# 6. Group by a level
# 7. Print all results
```

---

### Mini Quiz

1. What is a MultiIndex?
2. How do you create a MultiIndex from arrays?
3. How do you select all rows for a specific level?
4. What is the difference between `stack()` and `unstack()`?
5. What is the purpose of `xs()`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting that `loc` with MultiIndex requires a tuple | Use `df.loc[('A', 'B')]` not `df.loc['A', 'B']` |
| Not naming index levels | Use `names` parameter when creating MultiIndex |
| Using `reset_index()` without checking levels | Understand which level is being reset |
| Confusing stack and unstack | Remember: `stack` goes rows, `unstack` goes columns |

---

### Interview Questions

1. **What is a MultiIndex in Pandas?**  
   *Answer*: A MultiIndex allows multiple levels of index on a DataFrame, enabling hierarchical data structures.

2. **How do you select data from a MultiIndex DataFrame?**  
   *Answer*: Using `df.loc` with a tuple, `df.xs()` for cross-section selection, or indexing by a specific level.

3. **What is the difference between `stack()` and `unstack()`?**  
   *Answer*: `stack()` pivots columns to rows (long format). `unstack()` pivots rows to columns (wide format).

---

### Assignment and Mini Project

**Assignment 4.15** – MultiIndex practice:
```python
# 1. Create a MultiIndex DataFrame with levels: Department, Employee
# 2. Add columns: Salary, Bonus, Performance
# 3. Select:
#    - All employees in a specific department
#    - A specific employee
#    - All data where Performance > 80
# 4. Unstack the DataFrame
# 5. Stack it back
# 6. Group by Department and calculate average salary and bonus
# 7. Print all results
```

**Mini Project** – Time Series with MultiIndex:
Create a program that:
1. Creates a MultiIndex DataFrame for stock prices: (Ticker, Date) as index.
2. Generates simulated price data for 3 stocks over 252 days.
3. Calculates:
   - Daily returns for each stock.
   - Average price for each stock.
   - Correlation between stocks.
4. Demonstrates MultiIndex operations:
   - Selecting a specific stock.
   - Selecting a date range across all stocks.
   - Stacking and unstacking.
5. Prints summary statistics.

---

### Summary and Revision Notes

- MultiIndex allows hierarchical indexing.
- Created with `pd.MultiIndex.from_arrays()`, `from_tuples()`, or `set_index()`.
- Access with `loc` and tuples.
- `xs()` for cross-section selection.
- `swaplevel()` to swap levels.
- `stack()` (columns → rows) and `unstack()` (rows → columns).

---

## Final Phase 4 Assessment

Now that you have completed all lessons, test your overall understanding.

### Self-Evaluation Checklist

-  I can create and manipulate Series and DataFrames.

-  I can import and export data from various formats.

-  I can select rows and columns using `.loc` and `.iloc`.

-  I can filter data using boolean indexing.

-  I can sort data.

-  I can group and aggregate data with `groupby`.

-  I can combine DataFrames using `merge`, `join`, and `concat`.

-  I can handle missing values.

-  I can remove duplicates.

-  I can clean and transform data.

-  I can create pivot tables.

-  I can work with MultiIndex.


---

### Answers to Mini Quizzes

**Lesson 4.1**: 1. Panel Data. 2. `import pandas as pd`. 3. Series is 1D; DataFrame is 2D. 4. `pd.read_csv()`. 5. Shows first 5 rows.

**Lesson 4.2**: 1. A 1D labeled array. 2. `pd.Series([1,2,3], index=['a','b','c'])`. 3. `s['a']` by label; `s.iloc[0]` by position. 4. `s[s > threshold]`. 5. `dropna()` and `fillna()`.

**Lesson 4.3**: 1. A 2D labeled data structure. 2. `df['col']` or `df.col`. 3. `.iloc` by position, `.loc` by label. 4. `df['new'] = values`. 5. `df.describe()`.

**Lesson 4.4**: 1. `pd.read_csv()`. 2. `pd.read_csv('file.csv', usecols=['col1', 'col2'])`. 3. `index_col='col'`. 4. `pd.read_excel()`. 5. `pd.read_csv(url)`.

**Lesson 4.5**: 1. `df.to_csv('file.csv')`. 2. `index=False`. 3. `columns=['col1', 'col2']`. 4. Using `pd.ExcelWriter`. 5. CSV, Excel, JSON, SQL.

**Lesson 4.6**: 1. `.loc` uses labels, `.iloc` uses positions. 2. `df['col']`. 3. `df[['col1', 'col2']]`. 4. `df[df['col'] > value]`. 5. `.at` is faster for single element.

**Lesson 4.7**: 1. `df[df['col'] > value]`. 2. `(cond1) & (cond2)`. 3. String-based filtering. 4. `df[df['col'].isin(list)]`. 5. `df[df['col'].str.contains('pattern')]`.

**Lesson 4.8**: 1. `df.sort_values('col')`. 2. `ascending=False`. 3. `df.sort_values(['col1', 'col2'])`. 4. `sort_values` sorts by values, `sort_index` sorts by index. 5. `na_position`.

**Lesson 4.9**: 1. Split, apply, combine. 2. `df.groupby('col')['other'].mean()`. 3. `.agg(['sum', 'mean'])`. 4. `.agg` returns aggregates; `.transform` returns same shape. 5. `.groupby(['col1', 'col2'])`.

**Lesson 4.10**: 1. `concat` stacks, `merge` joins on columns. 2. Inner, Outer, Left, Right. 3. `left_on` and `right_on`. 4. Inner. 5. `pd.concat([df1, df2], axis=0)`.

**Lesson 4.11**: 1. Not a Number (missing value). 2. `df.isnull()`. 3. `dropna()` removes, `fillna()` fills. 4. `df['col'].fillna(df['col'].mean())`. 5. Estimating missing values.

**Lesson 4.12**: 1. `df.duplicated()`. 2. `keep='first'`. 3. `df.drop_duplicates(subset=['col1', 'col2'])`. 4. `keep='last'`. 5. `df.duplicated().sum()`.

**Lesson 4.13**: 1. `df.rename(columns={'old': 'new'})`. 2. `df['col'].str.strip()`. 3. `pd.to_datetime(df['col'])`. 4. `df['col'].apply(func)`. 5. Binning data.

**Lesson 4.14**: 1. Summarising data in cross-tabulation. 2. 'mean'. 3. Adds subtotals. 4. `pivot_table` is wide, `groupby` is long. 5. Frequency counts.

**Lesson 4.15**: 1. Hierarchical indexing with multiple levels. 2. `pd.MultiIndex.from_arrays()`. 3. `df.loc['level_value']`. 4. `stack` → rows, `unstack` → columns. 5. Cross-section selection.

---

**Congratulations!** You have completed Phase 4 of Python for Data Analytics. You now have a deep understanding of Pandas – the most important library for data manipulation. Keep practising!


----




<br/><br/><br/>
<center> <b>Happy Learning! 😊</b> </center>
