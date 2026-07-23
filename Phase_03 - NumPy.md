# Phase 3: NumPy

Welcome to **Phase 3** – your introduction to **NumPy**, the fundamental library for scientific computing in Python! If Python is the language of data science, NumPy is its beating heart. Virtually every data science and machine learning library in Python – pandas, scikit-learn, TensorFlow, PyTorch – is built on top of NumPy.

In this phase, you'll learn:
- What NumPy is and why it's essential for data analytics.
- How to create and manipulate **NumPy arrays** – the core data structure.
- **Array operations** – arithmetic, comparison, and logical operations.
- **Indexing and slicing** – accessing specific elements and subsets.
- **Broadcasting** – a powerful feature for working with arrays of different shapes.
- **Vectorization** – writing fast, efficient code without explicit loops.
- **Mathematical and statistical operations** – from basic math to advanced statistics.
- The **random module** – generating random data for simulations.
- The **performance benefits** of NumPy over pure Python.

By the end of this phase, you'll be able to handle numerical data efficiently – a skill that forms the backbone of data analysis, machine learning, and scientific computing.

---

## Lesson 3.1 – Introduction to NumPy

### Concept Explanation

**NumPy** (Numerical Python) is the foundational library for numerical computing in Python. It provides:
- A powerful N-dimensional array object (`ndarray`).
- Fast, vectorized operations (no slow Python loops).
- A wide range of mathematical functions.
- Tools for integrating C/C++ and Fortran code.

**Why NumPy?**
- **Performance**: NumPy operations are implemented in C and Fortran, making them significantly faster than pure Python loops.
- **Convenience**: Complex operations can be expressed in a single line of code.
- **Memory efficiency**: NumPy arrays use less memory than Python lists because they store homogeneous data types.

**The `ndarray`**:
- A **homogeneous** (all elements of the same type) multidimensional array.
- Fixed size (cannot grow or shrink after creation).
- Supports vectorized operations (operations applied to the entire array).

**Installation**:
```bash
pip install numpy
```

**Importing NumPy**:
```python
import numpy as np  # Standard alias
```

---

### Importance and Real-World Use Cases

- **Why it matters**: NumPy is the foundation of the entire Python data science ecosystem. Understanding NumPy is essential for working with pandas, scikit-learn, and many other libraries.

- **Use cases**:
  - A **data analyst** uses NumPy to perform fast numerical calculations on large datasets.
  - A **data scientist** uses NumPy arrays to store and manipulate feature matrices for machine learning.
  - A **financial analyst** uses NumPy to perform vectorized calculations on stock price data.

---

### Step-by-Step Demonstration

**Creating NumPy Arrays**:

```python
import numpy as np

# From a Python list
arr1 = np.array([1, 2, 3, 4, 5])
print(arr1)  # [1 2 3 4 5]

# 2D array (matrix)
arr2 = np.array([[1, 2, 3], [4, 5, 6]])
print(arr2)
# [[1 2 3]
#  [4 5 6]]

# Array of zeros
zeros = np.zeros(5)  # [0. 0. 0. 0. 0.]
print(zeros)

# Array of ones
ones = np.ones(5)  # [1. 1. 1. 1. 1.]
print(ones)

# Array with a range of values
range_arr = np.arange(10)  # [0 1 2 3 4 5 6 7 8 9]
print(range_arr)

# Array with evenly spaced values
linspace = np.linspace(0, 10, 5)  # [0.  2.5 5.  7.5 10.]
print(linspace)

# Identity matrix
identity = np.eye(3)
print(identity)
# [[1. 0. 0.]
#  [0. 1. 0.]
#  [0. 0. 1.]]
```

**Checking Array Properties**:

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])

print(f"Shape: {arr.shape}")        # (2, 3)
print(f"Dimensions: {arr.ndim}")    # 2
print(f"Size: {arr.size}")          # 6
print(f"Data type: {arr.dtype}")    # int64
print(f"Item size: {arr.itemsize}") # 8 (bytes per element)
```

**Data Types**:
```python
# Specifying data type
arr_int = np.array([1, 2, 3], dtype=np.int32)
arr_float = np.array([1, 2, 3], dtype=np.float64)
arr_bool = np.array([True, False, True], dtype=np.bool_)

print(arr_int.dtype)   # int32
print(arr_float.dtype) # float64
```

---

### Practical Examples

- **Example 1**: Storing temperature data for analysis.
- **Example 2**: Creating a matrix of sensor readings.
- **Example 3**: Initializing an array of zeros for later computation.

---

### Hands-on Coding Exercises

**Exercise 3.1** – Create arrays:
```python
# 1. Create a 1D array from a list of numbers
# 2. Create a 2D array (3x3) from a list of lists
# 3. Create an array of 10 zeros
# 4. Create an array of 5 ones
# 5. Create an array from 0 to 20 with step 2
# 6. Print the shape, size, and data type of each array
```

**Exercise 3.2** – Array properties:
```python
# Create a 3x4 array of random integers (1-100)
# Print:
# - Shape
# - Number of dimensions
# - Total number of elements
# - Data type
# - Item size
```

---

### Mini Quiz

1. What does NumPy stand for?
2. What is the core data structure in NumPy?
3. How do you create an array of zeros?
4. What is the difference between `np.array()` and `np.arange()`?
5. What property tells you the shape of an array?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using Python lists for numerical operations | Use NumPy arrays for numerical data |
| Forgetting to import NumPy (`import numpy as np`) | Always import with the standard alias |
| Creating arrays with mixed data types | Use homogeneous data types for efficiency |
| Using loops instead of vectorized operations | Leverage NumPy's vectorized operations |

---

### Interview Questions

1. **What is NumPy and why is it used in data science?**  
   *Answer*: NumPy is the fundamental library for numerical computing in Python. It provides fast, memory-efficient array operations and is the foundation for almost all data science libraries in Python.

2. **What is an ndarray and how does it differ from a Python list?**  
   *Answer*: An ndarray is a homogeneous, fixed-size multidimensional array that supports vectorized operations. It uses less memory than a Python list and is much faster for numerical operations.

3. **How do you create a 2D NumPy array?**  
   *Answer*: Using `np.array([[row1], [row2]])` or `np.zeros((rows, cols))`.

---

### Assignment and Mini Project

**Assignment 3.1** – Array creation and exploration:
```python
# 1. Create a 1D array with numbers 10 to 50 (step 5)
# 2. Create a 2D array (4 rows, 3 columns) of random integers (0-100)
# 3. Create a 3x3 identity matrix
# 4. Create an array of 20 equally spaced numbers between 0 and 1
# 5. For each array, print: shape, size, dimensions, data type
```

**Mini Project** – Data Generator:
Create a program that generates the following arrays:
1. A 5x5 array of random numbers between 0 and 100.
2. A 3x4 array of ones.
3. A 2x5 array of zeros.
4. A 1D array with numbers from 1 to 50.
5. A 2x2x2 3D array of random numbers.
Print the shape, size, and data type of each array. Then print the arrays themselves.

---

### Summary and Revision Notes

- NumPy is the fundamental library for numerical computing.
- The core data structure is the `ndarray` (N-dimensional array).
- Arrays are homogeneous (same data type) and fixed size.
- Import with `import numpy as np`.
- Common creation functions: `np.array()`, `np.zeros()`, `np.ones()`, `np.arange()`, `np.linspace()`, `np.eye()`.
- Key properties: `shape`, `ndim`, `size`, `dtype`.

---

## Lesson 3.2 – Arrays

### Concept Explanation

This lesson dives deeper into NumPy arrays – the different ways to create them, their attributes, and how to work with them.

**Types of arrays**:
- **1D array**: Vector (single row or column).
- **2D array**: Matrix (rows and columns).
- **3D array**: Tensor (multiple matrices stacked).

**Creating arrays**:

| **Function** | **Description** | **Example** |
|--------------|-----------------|-------------|
| `np.array(list)` | From a Python list | `np.array([1, 2, 3])` |
| `np.zeros(shape)` | Array of zeros | `np.zeros((2, 3))` |
| `np.ones(shape)` | Array of ones | `np.ones((2, 3))` |
| `np.full(shape, value)` | Array filled with a value | `np.full((2, 3), 7)` |
| `np.arange(start, stop, step)` | Range of values | `np.arange(0, 10, 2)` |
| `np.linspace(start, stop, num)` | Evenly spaced values | `np.linspace(0, 1, 5)` |
| `np.eye(n)` | Identity matrix | `np.eye(3)` |
| `np.random.rand(shape)` | Random values (0-1) | `np.random.rand(2, 3)` |
| `np.random.randint(low, high, shape)` | Random integers | `np.random.randint(0, 10, (2, 3))` |

**Reshaping arrays**:
```python
arr = np.arange(12)  # 0 to 11
print(arr)

# Reshape to 3x4
reshaped = arr.reshape(3, 4)
print(reshaped)

# Reshape to 2x6
reshaped2 = arr.reshape(2, 6)
print(reshaped2)
```

**Flattening arrays**:
```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
flat = arr.flatten()  # [1 2 3 4 5 6]
print(flat)
```

---

### Importance and Real-World Use Cases

- **Why it matters**: Understanding how to create and manipulate arrays is the foundation of all NumPy operations. You'll use these skills in every data analysis and machine learning project.

- **Use cases**:
  - A **data analyst** creates arrays to store and process numerical data.
  - A **data scientist** reshapes arrays to prepare data for machine learning models.
  - A **financial analyst** uses `np.linspace()` to create time series.

---

### Step-by-Step Demonstration

**Array Creation Methods**:

```python
import numpy as np

# 1. From a list
arr1 = np.array([1, 2, 3, 4, 5])
print("From list:", arr1)

# 2. Zeros
arr2 = np.zeros((2, 3))
print("Zeros:\n", arr2)

# 3. Ones
arr3 = np.ones((2, 3))
print("Ones:\n", arr3)

# 4. Full (fill with a value)
arr4 = np.full((2, 3), 7)
print("Full:\n", arr4)

# 5. Arange
arr5 = np.arange(0, 10, 2)
print("Arange:", arr5)

# 6. Linspace
arr6 = np.linspace(0, 1, 5)
print("Linspace:", arr6)

# 7. Identity
arr7 = np.eye(3)
print("Identity:\n", arr7)

# 8. Random
arr8 = np.random.rand(2, 3)  # Uniform 0-1
print("Random:\n", arr8)

arr9 = np.random.randint(0, 100, (3, 4))  # Random integers
print("Random integers:\n", arr9)
```

**Reshaping and Transposing**:

```python
arr = np.arange(12)
print("Original:", arr)

# Reshape
reshaped = arr.reshape(3, 4)
print("Reshaped (3x4):\n", reshaped)

# Transpose
transposed = reshaped.T
print("Transposed (4x3):\n", transposed)

# Flatten
flat = reshaped.flatten()
print("Flattened:", flat)

# Reshape with -1 (auto-compute)
auto_reshape = arr.reshape(4, -1)  # 4 rows, columns auto-computed
print("Auto reshape:\n", auto_reshape)
```

**Converting Data Types**:

```python
arr = np.array([1, 2, 3])
print(arr.dtype)  # int64

# Convert to float
arr_float = arr.astype(np.float64)
print(arr_float.dtype)  # float64

# Convert to int32
arr_int = arr.astype(np.int32)
print(arr_int.dtype)  # int32
```

---

### Practical Examples

- **Example 1**: Creating a matrix of sensor readings:
```python
# 5 sensors, 10 readings each
sensor_readings = np.random.randint(0, 100, (5, 10))
print("Sensor readings shape:", sensor_readings.shape)
```

- **Example 2**: Creating time intervals:
```python
# 100 equally spaced time points between 0 and 1 second
time = np.linspace(0, 1, 100)
print("Time intervals:", time[:5])  # First 5
```

---

### Hands-on Coding Exercises

**Exercise 3.3** – Array creation practice:
```python
# 1. Create a 2x3 array of zeros
# 2. Create a 3x2 array of ones
# 3. Create a 4x4 array of 5s
# 4. Create an identity matrix of size 5
# 5. Create an array of 15 random integers between 1 and 50
# 6. Reshape the random array to 3x5
# 7. Flatten the reshaped array
# 8. Print the shape and data type of each array
```

---

### Mini Quiz

1. How do you create a 2x3 array of zeros?
2. What is the difference between `np.arange()` and `np.linspace()`?
3. What does the `reshape()` method do?
4. How do you flatten a 2D array?
5. What is the purpose of `np.eye()`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Trying to reshape an array to an incompatible shape | Ensure the total number of elements matches |
| Using `shape` as a tuple incorrectly | `(rows, cols)` for 2D arrays |
| Forgetting that `reshape()` returns a new array | It doesn't modify the original array |
| Using `np.array()` without specifying dtype when needed | Specify `dtype` for large or memory-critical applications |

---

### Interview Questions

1. **How do you create a 3x4 matrix of random numbers between 0 and 1?**  
   *Answer*: `np.random.rand(3, 4)`.

2. **What is the difference between `reshape()` and `resize()`?**  
   *Answer*: `reshape()` returns a new array with a different shape without changing the original. `resize()` changes the array in-place.

3. **What does the `-1` do in `arr.reshape(4, -1)`?**  
   *Answer*: It automatically calculates the dimension based on the total number of elements and the other specified dimensions.

---

### Assignment and Mini Project

**Assignment 3.2** – Array creation and manipulation:
```python
# 1. Create a 1D array with numbers 1 to 20
# 2. Reshape it to 4x5
# 3. Reshape it to 5x4
# 4. Reshape it to 2x10
# 5. Flatten the 4x5 array back to 1D
# 6. Transpose the 5x4 array
# 7. Print the shape of each array
# 8. Change the data type of the original array to float32
```

**Mini Project** – Image Array Simulator:
Create a program that:
1. Generates a 3x4 array of random integers (0-255) representing pixel values for a small grayscale image.
2. Creates a 3x4 array of random integers (0-255) for another "image".
3. Reshapes both arrays to 4x3.
4. Flattens both to 1D arrays.
5. Creates a 2x3x4 3D array representing 2 images.
6. Prints all arrays with their shapes.

---

### Summary and Revision Notes

- Arrays can be created from lists or using built-in functions.
- `np.zeros()`, `np.ones()`, `np.full()` create constant arrays.
- `np.arange()` and `np.linspace()` create sequences.
- `np.eye()` creates an identity matrix.
- `reshape()` changes array dimensions.
- `flatten()` converts to 1D.
- `T` transposes the array (rows ↔ columns).
- `astype()` converts data types.

---

## Lesson 3.3 – Array Operations

### Concept Explanation

NumPy supports **vectorized operations** – operations that apply element-wise to arrays without explicit loops. This is what makes NumPy fast and concise.

**Types of operations**:
- **Arithmetic**: `+`, `-`, `*`, `/`, `**`, `%`.
- **Comparison**: `>`, `<`, `>=`, `<=`, `==`, `!=`.
- **Logical**: `&` (and), `|` (or), `~` (not).
- **Universal functions (ufuncs)**: `np.sqrt()`, `np.exp()`, `np.sin()`, `np.log()`, etc.

**Key principle**: Operations are applied **element-wise** to arrays of the same shape.

---

### Importance and Real-World Use Cases

- **Why it matters**: Vectorized operations are the reason NumPy is fast. They allow you to perform complex calculations on entire arrays with a single line of code, avoiding slow Python loops.

- **Use cases**:
  - A **data analyst** calculates percentage change in sales: `(current - previous) / previous`.
  - A **data scientist** normalises data: `(data - mean) / std`.
  - A **financial analyst** calculates returns: `(prices[1:] / prices[:-1]) - 1`.

---

### Step-by-Step Demonstration

**Arithmetic Operations**:

```python
import numpy as np

a = np.array([1, 2, 3, 4, 5])
b = np.array([10, 20, 30, 40, 50])

# Addition
print("Addition:", a + b)

# Subtraction
print("Subtraction:", b - a)

# Multiplication
print("Multiplication:", a * b)

# Division
print("Division:", b / a)

# Exponentiation
print("Exponentiation:", a ** 2)

# Modulus
print("Modulus:", b % a)
```

**Comparison Operations**:

```python
a = np.array([1, 2, 3, 4, 5])
b = np.array([3, 2, 1, 5, 4])

print("a > b:", a > b)
print("a == b:", a == b)
print("a != b:", a != b)
print("a >= 3:", a >= 3)
```

**Universal Functions (ufuncs)**:

```python
arr = np.array([1, 4, 9, 16, 25])

print("Square root:", np.sqrt(arr))
print("Exponential:", np.exp(arr))
print("Log (natural):", np.log(arr))
print("Log base 10:", np.log10(arr))
print("Sin:", np.sin(arr))
print("Absolute value:", np.abs([-1, -2, -3]))
```

**Array-Level Operations**:

```python
arr = np.array([1, 2, 3, 4, 5])

print("Sum:", arr.sum())
print("Mean:", arr.mean())
print("Max:", arr.max())
print("Min:", arr.min())
print("Standard deviation:", arr.std())
print("Variance:", arr.var())
print("Cumulative sum:", arr.cumsum())
print("Cumulative product:", arr.cumprod())
```

**Operations on 2D Arrays**:

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])

print("Sum of all:", arr.sum())
print("Sum by rows:", arr.sum(axis=1))
print("Sum by columns:", arr.sum(axis=0))
print("Mean by rows:", arr.mean(axis=1))
print("Max by columns:", arr.max(axis=0))
```

**Element-wise vs Matrix Operations**:

```python
a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6], [7, 8]])

# Element-wise multiplication
print("Element-wise:\n", a * b)

# Matrix multiplication (dot product)
print("Matrix multiplication:\n", np.dot(a, b))
# Or using @ operator
print("Matrix multiplication (@):\n", a @ b)
```

---

### Practical Examples

**Example 1: Calculating Percentage Change**:

```python
# Sales data for 12 months
sales = np.array([100, 120, 110, 130, 150, 140, 160, 180, 170, 190, 200, 210])

# Percentage change from month to month
changes = (sales[1:] - sales[:-1]) / sales[:-1] * 100
print("Monthly % change:", changes)

# Average change
print("Average change:", changes.mean())
```

**Example 2: Normalizing Data**:

```python
data = np.array([10, 20, 30, 40, 50, 60, 70, 80, 90, 100])

# Normalize to 0-1 range
normalized = (data - data.min()) / (data.max() - data.min())
print("Normalized:", normalized)

# Standardize (z-score)
standardized = (data - data.mean()) / data.std()
print("Standardized:", standardized)
```

**Example 3: Filtering Data**:

```python
data = np.array([10, 25, 30, 45, 50, 65, 70, 85, 90, 100])

# Filter values > 50
filtered = data[data > 50]
print("Values > 50:", filtered)

# Filter between 30 and 70
filtered2 = data[(data >= 30) & (data <= 70)]
print("Values between 30 and 70:", filtered2)
```

---

### Hands-on Coding Exercises

**Exercise 3.4** – Arithmetic operations:
```python
# 1. Create two arrays: [1, 3, 5, 7, 9] and [2, 4, 6, 8, 10]
# 2. Add them
# 3. Subtract them
# 4. Multiply them
# 5. Divide the second by the first
# 6. Square the first array
# 7. Print all results
```

**Exercise 3.5** – Statistical operations:
```python
# 1. Create an array of 20 random integers between 1 and 100
# 2. Calculate: sum, mean, min, max, standard deviation, variance
# 3. Calculate the median
# 4. Calculate the 25th and 75th percentiles
# 5. Print all results
```

**Exercise 3.6** – Filtering:
```python
# 1. Create an array of 15 random integers between 1 and 50
# 2. Filter values greater than 25
# 3. Filter values between 10 and 30
# 4. Filter values that are even
# 5. Print all filtered arrays
```

---

### Mini Quiz

1. What is a vectorized operation?
2. How do you add two arrays element-wise?
3. How do you compute the mean of an array?
4. What is the difference between `arr.sum()` and `arr.sum(axis=0)`?
5. What is the dot product in NumPy?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using Python loops instead of vectorized operations | Use vectorized operations for speed |
| Forgetting to use parentheses in complex conditions | Use `(condition1) & (condition2)` |
| Using `*` for matrix multiplication | Use `np.dot()` or `@` for matrix multiplication |
| Not handling division by zero | Use `np.where()` or masking to avoid division by zero |

---

### Interview Questions

1. **What is the difference between element-wise multiplication and matrix multiplication in NumPy?**  
   *Answer*: Element-wise multiplication uses `*` and multiplies corresponding elements. Matrix multiplication uses `np.dot()` or `@` and performs the dot product.

2. **How do you filter an array based on a condition?**  
   *Answer*: Using boolean indexing: `arr[arr > 5]` returns elements greater than 5.

3. **What is the advantage of vectorized operations?**  
   *Answer*: Vectorized operations are implemented in C and are significantly faster than Python loops. They also make code more concise and readable.

---

### Assignment and Mini Project

**Assignment 3.3** – Array operations:
```python
# 1. Create an array of 30 random integers (1-100)
# 2. Calculate:
#    - Total sum
#    - Mean
#    - Median
#    - Standard deviation
#    - Minimum and maximum
# 3. Filter values above the mean
# 4. Filter values below the mean
# 5. Normalize the array (min-max scaling)
# 6. Print all results
```

**Mini Project** – Portfolio Performance Analyzer:
Create a program that:
1. Creates a 1D array of daily stock prices (200 days) using `np.random.randn` and cumulative sum to simulate realistic prices: `np.cumsum(np.random.randn(200))`.
2. Calculates daily returns: `(prices[1:] / prices[:-1]) - 1`.
3. Calculates:
   - Total return over the period.
   - Average daily return.
   - Maximum daily gain.
   - Maximum daily loss.
   - Volatility (standard deviation of returns).
4. Simulates another stock and compares their performance.
5. Prints a summary report.

---

### Summary and Revision Notes

- Vectorized operations are applied element-wise.
- Arithmetic operations: `+`, `-`, `*`, `/`, `**`, `%`.
- Comparison operations: `>`, `<`, `>=`, `<=`, `==`, `!=`.
- Universal functions: `np.sqrt()`, `np.exp()`, `np.log()`, `np.sin()`, etc.
- Array-level operations: `sum()`, `mean()`, `max()`, `min()`, `std()`, `var()`.
- `axis` parameter: `axis=0` (columns), `axis=1` (rows).
- Boolean indexing for filtering.
- Matrix multiplication: `np.dot()` or `@`.

---

## Lesson 3.4 – Indexing and Slicing

### Concept Explanation

**Indexing** and **slicing** allow you to access and manipulate specific elements or sub-arrays within a NumPy array. This is one of the most important skills for working with data.

**Key concepts**:
- **Indexing**: Accessing a single element.
- **Slicing**: Accessing a range of elements.
- **Fancy indexing**: Using arrays of indices.
- **Boolean indexing**: Using conditions to select elements.

**Slicing syntax**: `start:stop:step`
- `arr[start:stop]` – elements from `start` to `stop-1`.
- `arr[start:]` – elements from `start` to the end.
- `arr[:stop]` – elements from the beginning to `stop-1`.
- `arr[::step]` – every `step`-th element.

**2D slicing**: `arr[row_start:row_stop, col_start:col_stop]`

---

### Importance and Real-World Use Cases

- **Why it matters**: Data analysis often requires extracting specific subsets of data – a particular column, rows that meet a condition, or a time range. Indexing and slicing are how you do this.

- **Use cases**:
  - A **data analyst** extracts the first 100 rows of a dataset for sampling.
  - A **data scientist** selects specific features (columns) for a machine learning model.
  - A **financial analyst** extracts a specific time period from a time series.

---

### Step-by-Step Demonstration

**1D Array Indexing and Slicing**:

```python
import numpy as np

arr = np.array([10, 20, 30, 40, 50, 60, 70, 80, 90, 100])

# Indexing (single element)
print("Element at index 0:", arr[0])
print("Element at index -1:", arr[-1])  # Last element

# Slicing
print("First 3:", arr[:3])
print("Last 3:", arr[-3:])
print("Index 2 to 5:", arr[2:6])
print("Every 2nd:", arr[::2])
print("Reverse:", arr[::-1])

# Fancy indexing
indices = [0, 2, 4, 6]
print("Elements at indices:", arr[indices])
```

**2D Array Indexing and Slicing**:

```python
arr = np.array([[1, 2, 3, 4],
                [5, 6, 7, 8],
                [9, 10, 11, 12],
                [13, 14, 15, 16]])

# Single element
print("Element at (0, 0):", arr[0, 0])
print("Element at (2, 3):", arr[2, 3])

# Row and column
print("Row 1:", arr[1])
print("Column 2:", arr[:, 2])

# Slicing
print("Rows 0-2, Columns 0-2:\n", arr[0:3, 0:3])
print("All rows, columns 1-3:\n", arr[:, 1:4])
print("Rows 1-3, every 2nd column:\n", arr[1:4, ::2])

# Fancy indexing for 2D
rows = [0, 2, 3]
cols = [1, 3]
print("Specific elements:\n", arr[rows, :][:, cols])  # More complex
# Or using np.ix_
print("Using np.ix_:\n", arr[np.ix_(rows, cols)])
```

**Boolean Indexing**:

```python
arr = np.array([10, 20, 30, 40, 50, 60, 70, 80, 90, 100])

# Condition
mask = arr > 50
print("Mask:", mask)
print("Values > 50:", arr[mask])

# Multiple conditions
mask2 = (arr > 30) & (arr < 80)
print("Values between 30 and 80:", arr[mask2])

# Boolean indexing with assignment
arr[arr < 50] = 0
print("Replaced values < 50 with 0:", arr)
```

**Using `np.where()`**:

```python
arr = np.array([10, 20, 30, 40, 50, 60, 70, 80, 90, 100])

# Replace values > 50 with 1, others with 0
result = np.where(arr > 50, 1, 0)
print("Where > 50:", result)

# Replace values > 50 with 100, others unchanged
result2 = np.where(arr > 50, 100, arr)
print("Where > 50 (replace with 100):", result2)
```

**Fancy Indexing with Conditions**:

```python
# Get indices of values > 50
indices = np.where(arr > 50)[0]
print("Indices of values > 50:", indices)
print("Values at those indices:", arr[indices])
```

---

### Practical Examples

**Example 1: Extracting Sales Data**:

```python
# Monthly sales data (12 months, 5 products)
sales = np.random.randint(100, 500, (12, 5))
print("Sales data shape:", sales.shape)

# Q1 sales (first 3 months)
q1_sales = sales[0:3, :]
print("Q1 sales:\n", q1_sales)

# Product 3 sales (index 2)
product3 = sales[:, 2]
print("Product 3 sales:", product3)

# Months with sales > 400 (any product)
mask = (sales > 400).any(axis=1)
high_sales_months = sales[mask]
print("Months with high sales:\n", high_sales_months)
```

**Example 2: Time Series Data**:

```python
# Daily stock prices (250 days)
prices = 100 + np.cumsum(np.random.randn(250) * 0.5)

# Last 30 days
last_30 = prices[-30:]
print("Last 30 days:\n", last_30)

# Days with price > 110
high_days = prices[prices > 110]
print("Days with price > 110:", high_days)

# Volatility (standard deviation of returns)
returns = (prices[1:] - prices[:-1]) / prices[:-1]
print("Volatility:", returns.std() * 100, "%")
```

---

### Hands-on Coding Exercises

**Exercise 3.7** – 1D indexing and slicing:
```python
# 1. Create an array of 20 random integers (1-100)
# 2. Extract the first 5 elements
# 3. Extract the last 5 elements
# 4. Extract elements from index 5 to 14
# 5. Extract every 3rd element
# 6. Extract elements greater than 50
# 7. Replace all elements less than 30 with 0
# 8. Print the results
```

**Exercise 3.8** – 2D indexing and slicing:
```python
# 1. Create a 4x5 array of random integers (1-100)
# 2. Extract the first 2 rows
# 3. Extract the last 3 columns
# 4. Extract the element at row 2, column 3
# 5. Extract the sub-array from rows 1-3, columns 2-4
# 6. Extract the first column
# 7. Extract rows where the sum > 200
# 8. Print the results
```

**Exercise 3.9** – Boolean indexing:
```python
# 1. Create an array of 15 random integers (1-100)
# 2. Find all values greater than 60
# 3. Find all values between 30 and 70
# 4. Replace all odd values with -1
# 5. Count the number of values greater than 50
# 6. Print the results
```

---

### Mini Quiz

1. How do you access the last element of an array?
2. What does `arr[2:6]` return?
3. How do you extract all rows and the first 3 columns of a 2D array?
4. What is boolean indexing?
5. What is the purpose of `np.where()`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using `arr[2:6]` when you want `arr[2:7]` (off-by-one) | Remember `stop` is exclusive |
| Forgetting that slicing returns a view, not a copy | Use `.copy()` if you need a separate copy |
| Mixing up rows and columns in 2D arrays | Use `arr[row, col]` format |
| Using `&` instead of `and` for boolean conditions | Use `&` for element-wise AND |
| Not handling the case when no elements match | Check the length of the result before using it |

---

### Interview Questions

1. **What is the difference between `arr[2:6]` and `arr[2:6].copy()`?**  
   *Answer*: `arr[2:6]` returns a view of the original array (changes affect the original). `arr[2:6].copy()` creates a separate copy.

2. **How do you extract elements greater than a threshold in NumPy?**  
   *Answer*: Using boolean indexing: `arr[arr > threshold]`.

3. **What is fancy indexing?**  
   *Answer*: Fancy indexing uses arrays of indices to select elements. For example, `arr[[0, 2, 4]]` selects elements at indices 0, 2, and 4.

---

### Assignment and Mini Project

**Assignment 3.4** – Indexing and slicing practice:
```python
# 1. Create a 5x5 array of random integers (1-100)
# 2. Extract the top-left 2x2 sub-array
# 3. Extract the bottom-right 3x3 sub-array
# 4. Extract the first row
# 5. Extract the last column
# 6. Extract all elements greater than 50
# 7. Replace all elements less than 30 with 0
# 8. Find the indices of elements greater than 75
# 9. Print all results
```

**Mini Project** – Data Sampler:
Create a program that:
1. Generates a 1000x5 array of random data (simulating a dataset with 1000 rows and 5 features).
2. Extracts the first 100 rows as a sample.
3. Extracts the last 50 rows as a sample.
4. Extracts every 10th row.
5. Extracts rows where the sum of the row is greater than 250.
6. Extracts the first 3 columns.
7. Extracts columns 2 and 4.
8. Replaces all values greater than 90 with 90 (capping outliers).
9. Prints the shape of each extracted array.

---

### Summary and Revision Notes

- Indexing: `arr[index]` for 1D, `arr[row, col]` for 2D.
- Slicing: `start:stop:step` (stop is exclusive).
- Negative indices count from the end.
- 2D slicing: `arr[row_slice, col_slice]`.
- Boolean indexing: `arr[condition]`.
- `np.where(condition, value_if_true, value_if_false)`.
- Fancy indexing: `arr[[index1, index2, ...]]`.
- Slicing returns a view, not a copy.

---

## Lesson 3.5 – Broadcasting

### Concept Explanation

**Broadcasting** is a powerful feature in NumPy that allows operations on arrays of different shapes. Instead of requiring arrays to have identical shapes, NumPy "broadcasts" the smaller array to match the shape of the larger array.

**How broadcasting works**:
1. NumPy compares the shapes of the arrays.
2. It aligns dimensions starting from the trailing (rightmost) dimension.
3. Dimensions with size 1 are stretched to match the other array.
4. If dimensions are incompatible (neither is 1 and they don't match), broadcasting fails.

**Example**:
- `arr (3, 4)` + `scalar (1,)` → scalar is broadcast to `(3, 4)`.
- `arr (3, 4)` + `row (4,)` → row is broadcast to `(3, 4)`.
- `arr (3, 4)` + `col (3, 1)` → col is broadcast to `(3, 4)`.

---

### Importance and Real-World Use Cases

- **Why it matters**: Broadcasting eliminates the need for explicit loops when performing operations on arrays of different shapes. It makes code more efficient and concise.

- **Use cases**:
  - A **data analyst** adds a constant to every element of an array.
  - A **data scientist** subtracts the mean from each column of a matrix.
  - A **financial analyst** scales every column by a different factor.

---

### Step-by-Step Demonstration

**Scalar Broadcasting**:

```python
import numpy as np

arr = np.array([[1, 2, 3], [4, 5, 6]])

# Add a scalar to every element
result = arr + 10
print("Add 10:\n", result)

# Multiply by a scalar
result = arr * 2
print("Multiply by 2:\n", result)
```

**Row Broadcasting**:

```python
arr = np.array([[1, 2, 3, 4],
                [5, 6, 7, 8],
                [9, 10, 11, 12]])

row = np.array([10, 20, 30, 40])

# Add row to every row of arr
result = arr + row
print("Add row:\n", result)
```

**Column Broadcasting**:

```python
arr = np.array([[1, 2, 3],
                [4, 5, 6],
                [7, 8, 9]])

col = np.array([[10], [20], [30]])

# Add column to every column of arr
result = arr + col
print("Add column:\n", result)
```

**Matrix and Vector Broadcasting**:

```python
# Matrix 3x4
matrix = np.array([[1, 2, 3, 4],
                   [5, 6, 7, 8],
                   [9, 10, 11, 12]])

# Vector 1x4
vector = np.array([10, 20, 30, 40])

# Broadcast vector to each row
result = matrix + vector
print("Matrix + vector:\n", result)

# Vector 3x1
vector_col = np.array([[10], [20], [30]])

# Broadcast vector to each column
result = matrix + vector_col
print("Matrix + column vector:\n", result)
```

**Conditional Broadcasting with `np.newaxis`**:

```python
arr = np.array([1, 2, 3, 4, 5])

# Add a new axis (convert to column vector)
col_vec = arr[:, np.newaxis]
print("Column vector:\n", col_vec)

# This allows broadcasting between row and column
row_vec = np.array([10, 20, 30])

# arr (5,) + row_vec (3,) → (5, 3)
result = arr[:, np.newaxis] + row_vec
print("Broadcast result:\n", result)
```

**Broadcasting Rules**:

```python
# Compatible shapes
arr1 = np.array([[1, 2, 3]])  # (1, 3)
arr2 = np.array([[4], [5]])   # (2, 1)
result = arr1 + arr2          # (2, 3)
print("Compatible shapes:\n", result)

# Incompatible shapes (error)
arr1 = np.array([[1, 2, 3]])  # (1, 3)
arr2 = np.array([4, 5])       # (2,)
# result = arr1 + arr2  # This would raise an error
```

---

### Practical Examples

**Example 1: Normalizing Data with Broadcasting**:

```python
# Dataset: 5 samples, 3 features
data = np.array([[10, 20, 30],
                 [40, 50, 60],
                 [70, 80, 90],
                 [100, 110, 120],
                 [130, 140, 150]])

# Calculate mean and standard deviation for each feature (column)
mean = data.mean(axis=0)  # (3,)
std = data.std(axis=0)    # (3,)

# Normalize using broadcasting
normalized = (data - mean) / std
print("Normalized data:\n", normalized)
```

**Example 2: Adding a Bias Term**:

```python
# Feature matrix (5 samples, 3 features)
X = np.array([[1, 2, 3],
              [4, 5, 6],
              [7, 8, 9],
              [10, 11, 12],
              [13, 14, 15]])

# Bias term (adding a column of ones)
bias = np.ones((X.shape[0], 1))
X_with_bias = np.hstack((bias, X))
print("X with bias:\n", X_with_bias)
```

**Example 3: Scaling Data**:

```python
# Data matrix (5 samples, 3 features)
data = np.array([[1, 2, 3],
                 [4, 5, 6],
                 [7, 8, 9],
                 [10, 11, 12],
                 [13, 14, 15]])

# Scale factors for each feature
scales = np.array([0.5, 2, 0.1])

# Apply scaling to each column
scaled = data * scales
print("Scaled data:\n", scaled)
```

---

### Hands-on Coding Exercises

**Exercise 3.10** – Broadcasting practice:
```python
# 1. Create a 3x4 array and add 10 to every element
# 2. Create a 3x4 array and add a 1x4 row to every row
# 3. Create a 3x4 array and add a 3x1 column to every column
# 4. Create a 4x5 array and multiply by a 4x1 column
# 5. Create a 5x4 array and divide by a 1x4 row
# 6. Print all results
```

**Exercise 3.11** – Normalization with broadcasting:
```python
# 1. Create a 5x3 array of random integers (1-100)
# 2. Calculate the mean of each column
# 3. Calculate the standard deviation of each column
# 4. Normalize the data using broadcasting
# 5. Print the original data, mean, std, and normalized data
```

---

### Mini Quiz

1. What is broadcasting in NumPy?
2. Can you add a 1D array of shape (4,) to a 2D array of shape (3, 4)? Why?
3. What does `arr[:, np.newaxis]` do?
4. What happens if broadcasting fails?
5. How do you add a column vector to a matrix?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Trying to broadcast incompatible shapes | Check shapes before operations |
| Forgetting to add `np.newaxis` when needed | Use `np.newaxis` or `reshape()` |
| Not understanding the broadcasting rules | Review the rules: trailing dimensions first, size 1 stretches |
| Using loops instead of broadcasting | Use broadcasting for concise, fast code |

---

### Interview Questions

1. **What is broadcasting and why is it useful?**  
   *Answer*: Broadcasting allows operations on arrays of different shapes by stretching the smaller array to match the larger one. It eliminates the need for explicit loops and makes code more efficient.

2. **How do you add a 1D array of length 4 to every row of a 3x4 matrix?**  
   *Answer*: Broadcasting handles this automatically: `matrix + row_vector` works because the row vector is broadcast to match the matrix shape.

3. **What are the rules for broadcasting?**  
   *Answer*: Dimensions are compared starting from the trailing dimension. If sizes don't match, one must be 1 for broadcasting to work. The array with size 1 is stretched to match the other.

---

### Assignment and Mini Project

**Assignment 3.5** – Broadcasting practice:
```python
# 1. Create a 4x5 array of random integers (1-50)
# 2. Add 100 to every element
# 3. Add the row [10, 20, 30, 40, 50] to every row
# 4. Add the column [[10], [20], [30], [40]] to every column
# 5. Multiply each column by [0.5, 1, 1.5, 2, 2.5]
# 6. Normalize the data (subtract column mean, divide by column std)
# 7. Print all results
```

**Mini Project** – Data Preprocessing Pipeline:
Create a program that:
1. Generates a 100x5 array of random data (simulating a dataset).
2. Uses broadcasting to:
   - Add a bias column (column of ones) to the dataset.
   - Normalize the original features (not the bias column) using column-wise mean and standard deviation.
   - Scale each feature by a different factor: [1.0, 0.5, 2.0, 0.8, 1.2].
   - Add a constant value of 5 to every element.
3. Prints the shape and first 5 rows of the processed data.

---

### Summary and Revision Notes

- Broadcasting allows operations on arrays of different shapes.
- The smaller array is "stretched" to match the larger one.
- Dimensions are compared from the trailing end.
- If dimensions don't match and neither is 1, broadcasting fails.
- Use `np.newaxis` to add new dimensions.
- Broadcasting is fast and efficient.

---

## Lesson 3.6 – Vectorization

### Concept Explanation

**Vectorization** is the process of applying operations to entire arrays at once, rather than using explicit loops. This is the single most important reason NumPy is fast.

**Key principles**:
- **Avoid Python loops**: Python loops are slow because of the overhead of the Python interpreter.
- **Use NumPy's vectorized operations**: Operations are implemented in C and are highly optimised.
- **Use universal functions (ufuncs)**: `np.add()`, `np.multiply()`, `np.sqrt()`, etc.

**Why vectorization is faster**:
- No Python loop overhead.
- Operations are executed in compiled C/Fortran code.
- Better use of CPU cache (memory locality).

---

### Importance and Real-World Use Cases

- **Why it matters**: Vectorization can make your code 10-100x faster. For large datasets, this is the difference between seconds and minutes (or hours).

- **Use cases**:
  - A **data analyst** processes millions of rows of sales data.
  - A **data scientist** trains machine learning models on large datasets.
  - A **financial analyst** simulates thousands of scenarios.

---

### Step-by-Step Demonstration

**Loop vs Vectorized**:

```python
import numpy as np
import time

# Large array
arr = np.random.rand(1000000)

# Loop approach (slow)
start = time.time()
sum_loop = 0
for x in arr:
    sum_loop += x
end = time.time()
print(f"Loop time: {end - start:.4f}s")

# Vectorized approach (fast)
start = time.time()
sum_vec = arr.sum()
end = time.time()
print(f"Vectorized time: {end - start:.4f}s")
```

**Square Root with Loop vs Vectorized**:

```python
arr = np.random.rand(1000000)

# Loop
start = time.time()
sqrt_loop = []
for x in arr:
    sqrt_loop.append(x ** 0.5)
end = time.time()
print(f"Loop sqrt time: {end - start:.4f}s")

# Vectorized
start = time.time()
sqrt_vec = np.sqrt(arr)
end = time.time()
print(f"Vectorized sqrt time: {end - start:.4f}s")
```

**Conditional Operations**:

```python
arr = np.random.randint(0, 100, 1000000)

# Loop with condition
start = time.time()
result_loop = []
for x in arr:
    if x > 50:
        result_loop.append(x * 2)
    else:
        result_loop.append(x)
end = time.time()
print(f"Loop time: {end - start:.4f}s")

# Vectorized with np.where
start = time.time()
result_vec = np.where(arr > 50, arr * 2, arr)
end = time.time()
print(f"Vectorized time: {end - start:.4f}s")
```

**Comparison of Vectorized Operations**:

```python
# Element-wise operations are vectorized
a = np.array([1, 2, 3, 4, 5])
b = np.array([10, 20, 30, 40, 50])

# This is vectorized
c = a + b

# This is also vectorized
d = a * b

# Universal functions
e = np.sqrt(a)
f = np.exp(b)
g = np.log(a + 1)
```

**Using `np.where()` for Conditional Logic**:

```python
arr = np.array([10, 20, 30, 40, 50, 60, 70, 80, 90, 100])

# Replace values > 50 with 1, others with 0
result = np.where(arr > 50, 1, 0)
print(result)

# Replace values > 50 with 100, others unchanged
result2 = np.where(arr > 50, 100, arr)
print(result2)
```

**Using Vectorized String Operations**:

```python
# Vectorized string operations (requires np.char)
names = np.array(['Alice', 'Bob', 'Charlie', 'David'])

# Capitalise
print(np.char.capitalize(names))

# Upper case
print(np.char.upper(names))

# Lower case
print(np.char.lower(names))

# Length
print(np.char.str_len(names))
```

---

### Practical Examples

**Example 1: Vectorized Percentage Change**:

```python
# Loop version (slow)
def percentage_change_loop(data):
    result = []
    for i in range(1, len(data)):
        result.append((data[i] - data[i-1]) / data[i-1] * 100)
    return np.array(result)

# Vectorized version (fast)
def percentage_change_vectorized(data):
    return (data[1:] - data[:-1]) / data[:-1] * 100

# Test
data = np.random.rand(1000000)
print("Loop version:", percentage_change_loop(data)[:5])
print("Vectorized version:", percentage_change_vectorized(data)[:5])
```

**Example 2: Vectorized Data Cleaning**:

```python
# Simulate messy data with outliers and missing values
data = np.random.randint(0, 200, 1000000)

# Clip values > 150 to 150 (outlier capping)
cleaned = np.where(data > 150, 150, data)

# Replace values < 10 with 10 (floor)
cleaned = np.where(cleaned < 10, 10, cleaned)

# All in one go
def clean_data(data):
    return np.clip(data, 10, 150)

cleaned = clean_data(data)
```

---

### Hands-on Coding Exercises

**Exercise 3.12** – Speed comparison:
```python
# 1. Create an array of 10 million random numbers
# 2. Calculate the sum using a Python loop
# 3. Calculate the sum using NumPy's sum()
# 4. Calculate the mean using both methods
# 5. Calculate the square root using both methods
# 6. Compare the execution times
# 7. Write a summary of your findings
```

**Exercise 3.13** – Vectorized operations:
```python
# 1. Create two arrays of 5 elements each
# 2. Perform the following operations using vectorized methods:
#    - Add them
#    - Subtract the second from the first
#    - Multiply them
#    - Divide the first by the second
#    - Square each element
#    - Take the square root of each element
#    - Calculate the exponential of each element
# 3. Print all results
```

---

### Mini Quiz

1. What is vectorization?
2. Why is vectorization faster than using Python loops?
3. What is a universal function (ufunc)?
4. How do you use `np.where()`?
5. Why should you avoid Python loops with NumPy arrays?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using Python loops with NumPy arrays | Always use vectorized operations |
| Using `for` loops for element-wise operations | Use `np.add()`, `np.multiply()`, etc. |
| Not using `np.where()` for conditional logic | Use `np.where()` instead of loops with `if` |
| Using Python's built-in functions on arrays | Use NumPy's ufuncs (`np.sum`, `np.mean`, `np.sqrt`) |

---

### Interview Questions

1. **What is the difference between a Python loop and a vectorized operation?**  
   *Answer*: A Python loop executes each iteration in the Python interpreter, which is slow. A vectorized operation is executed in compiled C code, which is much faster.

2. **How do you apply a conditional operation to a NumPy array without a loop?**  
   *Answer*: Using `np.where()`. For example, `np.where(arr > 5, arr * 2, arr)` doubles values > 5, leaves others unchanged.

3. **What is the benefit of using `np.sqrt()` instead of `arr ** 0.5`?**  
   *Answer*: `np.sqrt()` is a universal function and is often more readable. Both are vectorized, so performance is similar.

---

### Assignment and Mini Project

**Assignment 3.6** – Vectorized operations:
```python
# 1. Create an array of 5 million random numbers
# 2. Calculate the sum, mean, min, max using NumPy
# 3. Calculate the standard deviation
# 4. Find all values greater than 0.5
# 5. Replace all values less than 0.3 with 0
# 6. Square all values
# 7. Calculate the natural log of all values (add a small constant to avoid log(0))
# 8. Compare execution times with loop-based equivalents
```

**Mini Project** – Performance Comparison Tool:
Create a program that:
1. Generates arrays of increasing size (100, 1,000, 10,000, 100,000, 1,000,000).
2. For each size, measures the time to:
   - Sum all elements using Python loop.
   - Sum all elements using NumPy's `sum()`.
   - Calculate square root using Python loop.
   - Calculate square root using NumPy's `sqrt()`.
   - Apply conditional logic (`if x > 0.5`) using Python loop.
   - Apply conditional logic using `np.where()`.
3. Prints a table of execution times.
4. Plots the results (if you have Matplotlib installed) or prints a summary.

---

### Summary and Revision Notes

- Vectorization applies operations to entire arrays at once.
- Vectorized operations are implemented in C and are 10-100x faster than Python loops.
- Universal functions (ufuncs): `np.sqrt()`, `np.exp()`, `np.log()`, `np.sin()`, etc.
- Use `np.where()` for conditional logic.
- Avoid Python loops when working with NumPy arrays.
- Vectorization is the key to efficient data analysis.

---

## Lesson 3.7 – Mathematical and Statistical Operations

### Concept Explanation

NumPy provides a comprehensive set of mathematical and statistical functions that can be applied to arrays.

**Mathematical Operations**:

| **Function** | **Description** |
|--------------|-----------------|
| `np.abs(arr)` | Absolute value |
| `np.sqrt(arr)` | Square root |
| `np.exp(arr)` | Exponential (e^x) |
| `np.log(arr)` | Natural log |
| `np.log10(arr)` | Log base 10 |
| `np.log2(arr)` | Log base 2 |
| `np.sin(arr)`, `np.cos(arr)`, `np.tan(arr)` | Trigonometric functions |
| `np.arcsin(arr)`, `np.arccos(arr)`, `np.arctan(arr)` | Inverse trigonometric |
| `np.sinh(arr)`, `np.cosh(arr)`, `np.tanh(arr)` | Hyperbolic functions |
| `np.ceil(arr)` | Round up to nearest integer |
| `np.floor(arr)` | Round down to nearest integer |
| `np.round(arr, decimals)` | Round to specified decimals |
| `np.rint(arr)` | Round to nearest integer |
| `np.sign(arr)` | Sign of each element (-1, 0, 1) |

**Statistical Operations**:

| **Function** | **Description** |
|--------------|-----------------|
| `arr.sum()` | Sum of elements |
| `arr.mean()` | Arithmetic mean |
| `arr.median()` | Median (uses `np.median()`) |
| `arr.min()`, `arr.max()` | Minimum and maximum |
| `arr.argmin()`, `arr.argmax()` | Index of min and max |
| `arr.std()` | Standard deviation |
| `arr.var()` | Variance |
| `arr.cumsum()` | Cumulative sum |
| `arr.cumprod()` | Cumulative product |
| `np.percentile(arr, p)` | Percentile |
| `np.quantile(arr, q)` | Quantile |
| `np.corrcoef(x, y)` | Correlation coefficient |
| `np.cov(x, y)` | Covariance |

---

### Importance and Real-World Use Cases

- **Why it matters**: Data analysis is all about mathematical and statistical operations. NumPy provides these functions efficiently and concisely.

- **Use cases**:
  - A **data analyst** calculates summary statistics (mean, median, standard deviation) for a dataset.
  - A **data scientist** computes correlation between features.
  - A **financial analyst** calculates returns, volatility, and Sharpe ratio.

---

### Step-by-Step Demonstration

**Basic Mathematical Operations**:

```python
import numpy as np

arr = np.array([-5, 0, 5, 10, 15])

print("Absolute:", np.abs(arr))
print("Square root:", np.sqrt(np.abs(arr)))
print("Exponential:", np.exp(arr))
print("Log (natural):", np.log(np.abs(arr) + 1))
print("Log base 10:", np.log10(np.abs(arr) + 1))

# Trigonometric
angles = np.array([0, np.pi/4, np.pi/2])
print("Sin:", np.sin(angles))
print("Cos:", np.cos(angles))
print("Tan:", np.tan(angles))
```

**Rounding Functions**:

```python
arr = np.array([1.2, 2.5, 3.7, 4.1, 5.9])

print("Floor:", np.floor(arr))
print("Ceil:", np.ceil(arr))
print("Round:", np.round(arr))
print("Round to 1 decimal:", np.round(arr, 1))
```

**Basic Statistics**:

```python
data = np.array([10, 20, 30, 40, 50, 60, 70, 80, 90, 100])

print(f"Sum: {data.sum()}")
print(f"Mean: {data.mean()}")
print(f"Median: {np.median(data)}")
print(f"Min: {data.min()}")
print(f"Max: {data.max()}")
print(f"Standard deviation: {data.std()}")
print(f"Variance: {data.var()}")
print(f"25th percentile: {np.percentile(data, 25)}")
print(f"75th percentile: {np.percentile(data, 75)}")

# Indices of min and max
print(f"Index of min: {data.argmin()}, value: {data[data.argmin()]}")
print(f"Index of max: {data.argmax()}, value: {data[data.argmax()]}")
```

**Cumulative Operations**:

```python
arr = np.array([1, 2, 3, 4, 5])

print("Cumulative sum:", arr.cumsum())
print("Cumulative product:", arr.cumprod())
```

**Axis-Based Operations**:

```python
# 2D array
matrix = np.array([[1, 2, 3, 4],
                   [5, 6, 7, 8],
                   [9, 10, 11, 12]])

print("Sum (all):", matrix.sum())
print("Sum (rows):", matrix.sum(axis=1))
print("Sum (columns):", matrix.sum(axis=0))

print("Mean (rows):", matrix.mean(axis=1))
print("Mean (columns):", matrix.mean(axis=0))

print("Max (rows):", matrix.max(axis=1))
print("Max (columns):", matrix.max(axis=0))
```

**Correlation and Covariance**:

```python
x = np.array([1, 2, 3, 4, 5])
y = np.array([2, 4, 6, 8, 10])

# Correlation coefficient
corr = np.corrcoef(x, y)
print("Correlation:\n", corr)

# Covariance
cov = np.cov(x, y)
print("Covariance:\n", cov)
```

---

### Practical Examples

**Example 1: Summary Statistics**:

```python
# Generate sample data (1000 sales transactions)
sales = np.random.randint(100, 1000, 1000)

print("Sales Summary:")
print("=" * 30)
print(f"Total sales: ${sales.sum():,.2f}")
print(f"Average sales: ${sales.mean():,.2f}")
print(f"Median sales: ${np.median(sales):,.2f}")
print(f"Min sales: ${sales.min():,.2f}")
print(f"Max sales: ${sales.max():,.2f}")
print(f"Standard deviation: ${sales.std():,.2f}")
print(f"25th percentile: ${np.percentile(sales, 25):,.2f}")
print(f"75th percentile: ${np.percentile(sales, 75):,.2f}")
```

**Example 2: Financial Returns**:

```python
# Simulate daily stock prices
prices = 100 + np.cumsum(np.random.randn(252) * 2)  # 252 trading days
print(f"Start price: {prices[0]:.2f}")
print(f"End price: {prices[-1]:.2f}")

# Calculate daily returns
returns = (prices[1:] - prices[:-1]) / prices[:-1]

print("\nReturn Statistics:")
print("=" * 30)
print(f"Total return: {(prices[-1] / prices[0] - 1) * 100:.2f}%")
print(f"Average daily return: {returns.mean() * 100:.4f}%")
print(f"Volatility (daily): {returns.std() * 100:.4f}%")
print(f"Maximum daily gain: {returns.max() * 100:.2f}%")
print(f"Maximum daily loss: {returns.min() * 100:.2f}%")
```

**Example 3: Outlier Detection**:

```python
data = np.random.randint(1, 100, 1000)
# Add some outliers
data = np.append(data, [1000, 2000, 3000])

# Detect outliers using z-score
mean = data.mean()
std = data.std()
z_scores = (data - mean) / std
outliers = data[np.abs(z_scores) > 3]
print(f"Number of outliers: {len(outliers)}")
print(f"Outlier values: {outliers}")
```

---

### Hands-on Coding Exercises

**Exercise 3.14** – Statistical summary:
```python
# 1. Create an array of 50 random integers (1-100)
# 2. Calculate and print:
#    - Sum
#    - Mean
#    - Median
#    - Standard deviation
#    - Variance
#    - Min
#    - Max
#    - 25th and 75th percentiles
#    - Range (max - min)
```

**Exercise 3.15** – Correlation:
```python
# 1. Create two arrays with 50 random numbers each
# 2. Calculate the correlation between them
# 3. Create two arrays that are perfectly correlated
# 4. Calculate the correlation
# 5. Create two arrays that are negatively correlated
# 6. Calculate the correlation
# 7. Compare the results
```

**Exercise 3.16** – Financial analysis:
```python
# 1. Simulate 252 daily stock prices
# 2. Calculate daily returns
# 3. Calculate:
#    - Total return
#    - Average daily return
#    - Volatility (std of returns)
#    - Sharpe ratio (average return / std return)
# 4. Print the results
```

---

### Mini Quiz

1. How do you calculate the median of an array?
2. What is the difference between `arr.sum()` and `arr.cumsum()`?
3. How do you calculate the correlation between two arrays?
4. What does `axis=0` mean in `arr.sum(axis=0)`?
5. How do you find the index of the maximum value in an array?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using Python's `sum()` instead of `arr.sum()` | Use NumPy's methods for arrays |
| Forgetting the `axis` parameter for 2D arrays | Specify `axis` to control the direction of operations |
| Using `np.percentile()` with the wrong syntax | `np.percentile(arr, 50)` is the median |
| Not handling NaN values | Use `np.nansum()`, `np.nanmean()`, etc., for data with missing values |

---

### Interview Questions

1. **How do you calculate the standard deviation of a NumPy array?**  
   *Answer*: Using `arr.std()` for the population standard deviation, or `arr.std(ddof=1)` for the sample standard deviation.

2. **What is the difference between `np.percentile()` and `np.quantile()`?**  
   *Answer*: `np.percentile()` uses percentages (0-100), while `np.quantile()` uses fractions (0-1). They are essentially the same operation.

3. **How do you calculate the correlation between two features in NumPy?**  
   *Answer*: Using `np.corrcoef(x, y)`, which returns a correlation matrix.

---

### Assignment and Mini Project

**Assignment 3.7** – Statistical analysis:
```python
# 1. Generate a dataset of 1000 random numbers (normal distribution)
# 2. Calculate all summary statistics (mean, median, std, etc.)
# 3. Calculate the z-scores for all values
# 4. Identify outliers (z-score > 3 or < -3)
# 5. Remove outliers and recalculate statistics
# 6. Compare the statistics before and after outlier removal
# 7. Print all results
```

**Mini Project** – Stock Portfolio Analyzer:
Create a program that:
1. Simulates 3 stocks with 252 daily prices each (using random walks with different parameters).
2. Calculates daily returns for each stock.
3. Calculates:
   - Total return for each stock.
   - Average daily return for each stock.
   - Volatility (std) for each stock.
   - Correlation between all pairs of stocks.
4. Calculates portfolio statistics for an equally weighted portfolio:
   - Portfolio returns (weighted average of stock returns).
   - Portfolio volatility.
   - Sharpe ratio (assuming risk-free rate = 0).
5. Identifies the best and worst performing stocks.
6. Prints a comprehensive report.

---

### Summary and Revision Notes

- Mathematical functions: `np.abs()`, `np.sqrt()`, `np.exp()`, `np.log()`, `np.sin()`, etc.
- Statistical functions: `sum()`, `mean()`, `median()`, `std()`, `var()`, `min()`, `max()`, `percentile()`, `quantile()`.
- Use `axis` parameter for 2D arrays.
- `cumsum()` and `cumprod()` for cumulative operations.
- `corrcoef()` and `cov()` for correlation and covariance.
- `argmin()` and `argmax()` for index of min/max.

---

## Lesson 3.8 – Random Module

### Concept Explanation

NumPy's `random` module provides a comprehensive set of functions for generating random numbers. This is essential for simulations, sampling, and data generation.

**Common functions**:

| **Function** | **Description** | **Example** |
|--------------|-----------------|-------------|
| `np.random.rand(d0, d1, ...)` | Uniform distribution [0, 1) | `np.random.rand(3, 4)` |
| `np.random.randn(d0, d1, ...)` | Standard normal distribution | `np.random.randn(3, 4)` |
| `np.random.randint(low, high, size)` | Random integers | `np.random.randint(0, 100, (3, 4))` |
| `np.random.random(size)` | Uniform [0, 1) | `np.random.random((3, 4))` |
| `np.random.normal(loc, scale, size)` | Normal distribution | `np.random.normal(0, 1, (3, 4))` |
| `np.random.uniform(low, high, size)` | Uniform [low, high) | `np.random.uniform(0, 1, (3, 4))` |
| `np.random.choice(a, size, replace, p)` | Random choice from array | `np.random.choice([1,2,3], 5, p=[0.1,0.2,0.7])` |
| `np.random.permutation(x)` | Random permutation | `np.random.permutation(10)` |
| `np.random.shuffle(x)` | Shuffle in-place | `np.random.shuffle(arr)` |

**Setting the seed**:
- `np.random.seed(seed)` – ensures reproducibility of results.

---

### Importance and Real-World Use Cases

- **Why it matters**: Randomness is everywhere in data analytics – from sampling and bootstrapping to simulations and stochastic models.

- **Use cases**:
  - A **data analyst** generates random samples for A/B testing.
  - A **data scientist** uses random numbers for bootstrapping and Monte Carlo simulations.
  - A **financial analyst** simulates stock prices using random walks.

---

### Step-by-Step Demonstration

**Basic Random Functions**:

```python
import numpy as np

# Uniform distribution [0, 1)
uniform = np.random.rand(3, 3)
print("Uniform:\n", uniform)

# Standard normal distribution
normal = np.random.randn(3, 3)
print("Normal:\n", normal)

# Random integers
integers = np.random.randint(0, 100, (3, 3))
print("Integers:\n", integers)

# Normal distribution with custom parameters
custom_normal = np.random.normal(loc=10, scale=2, size=(3, 3))
print("Custom normal (mean=10, std=2):\n", custom_normal)

# Uniform with custom range
custom_uniform = np.random.uniform(low=5, high=15, size=(3, 3))
print("Custom uniform (5-15):\n", custom_uniform)
```

**Random Choice**:

```python
# Random choice from an array
fruits = ['apple', 'banana', 'cherry', 'date']
choices = np.random.choice(fruits, size=10)
print("Random choices:", choices)

# With probabilities (weighted random)
choices_weighted = np.random.choice(fruits, size=10, p=[0.1, 0.2, 0.3, 0.4])
print("Weighted choices:", choices_weighted)
```

**Permutation and Shuffling**:

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])

# Random permutation (returns new array)
permuted = np.random.permutation(arr)
print("Permuted:", permuted)

# Shuffle in-place
np.random.shuffle(arr)
print("Shuffled:", arr)

# Permutation of indices
indices = np.random.permutation(len(arr))
print("Random indices:", indices)
```

**Setting the Seed**:

```python
# Set seed for reproducibility
np.random.seed(42)
print("With seed (42):", np.random.rand(3))

np.random.seed(42)
print("With same seed (42):", np.random.rand(3))

np.random.seed(123)
print("With different seed (123):", np.random.rand(3))
```

**Random Samples with Replacement**:

```python
# Bootstrap sample (sampling with replacement)
data = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
bootstrap_sample = np.random.choice(data, size=10, replace=True)
print("Bootstrap sample:", bootstrap_sample)
```

---

### Practical Examples

**Example 1: Simulating a Coin Toss**:

```python
# Simulate 1000 coin tosses
np.random.seed(42)
tosses = np.random.choice(['H', 'T'], size=1000, p=[0.5, 0.5])

heads = np.sum(tosses == 'H')
tails = np.sum(tosses == 'T')

print(f"Heads: {heads} ({heads/1000*100:.1f}%)")
print(f"Tails: {tails} ({tails/1000*100:.1f}%)")
```

**Example 2: Simulating Dice Rolls**:

```python
# Simulate 10,000 dice rolls
np.random.seed(42)
rolls = np.random.randint(1, 7, size=10000)

# Count frequency of each outcome
for i in range(1, 7):
    count = np.sum(rolls == i)
    print(f"{i}: {count} ({count/10000*100:.1f}%)")
```

**Example 3: Monte Carlo Simulation for Pi**:

```python
# Estimate Pi using Monte Carlo method
np.random.seed(42)
n_points = 1000000

# Generate random points in a unit square
x = np.random.rand(n_points)
y = np.random.rand(n_points)

# Count points inside the unit circle
inside = np.sum(x**2 + y**2 <= 1)

# Pi estimate (area of circle = pi/4 in a unit square)
pi_estimate = 4 * inside / n_points
print(f"Estimated Pi: {pi_estimate}")
print(f"Actual Pi: {np.pi}")
print(f"Error: {abs(pi_estimate - np.pi):.6f}")
```

**Example 4: Random Walk Simulation**:

```python
# Simulate a random walk
np.random.seed(42)
n_steps = 1000
steps = np.random.choice([-1, 1], size=n_steps)
position = np.cumsum(steps)

print(f"Final position: {position[-1]}")
print(f"Maximum position: {position.max()}")
print(f"Minimum position: {position.min()}")
```

---

### Hands-on Coding Exercises

**Exercise 3.17** – Random generation:
```python
# 1. Generate a 3x4 array of uniform random numbers [0, 1)
# 2. Generate a 4x3 array of random integers (10-50)
# 3. Generate a 5x5 array of standard normal numbers
# 4. Generate a 2x6 array of normal numbers with mean=5, std=2
# 5. Print all arrays
```

**Exercise 3.18** – Random choice:
```python
# 1. Create a list of 10 items
# 2. Randomly choose 5 items with replacement
# 3. Randomly choose 5 items without replacement
# 4. Randomly choose 10 items with weighted probabilities
# 5. Shuffle the list
# 6. Print all results
```

**Exercise 3.19** – Monte Carlo simulation:
```python
# 1. Estimate the value of Pi using Monte Carlo simulation
# 2. Try with different numbers of points: 100, 1000, 10000, 100000, 1000000
# 3. Calculate the error for each
# 4. Print a table of results
```

---

### Mini Quiz

1. How do you generate a random integer between 1 and 10?
2. What is the purpose of `np.random.seed()`?
3. How do you randomly sample without replacement?
4. What is the difference between `np.random.rand()` and `np.random.randn()`?
5. How do you shuffle an array in-place?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not setting a seed for reproducibility | Use `np.random.seed()` for reproducible results |
| Using `np.random.random()` when you need integers | Use `np.random.randint()` |
| Sampling without replacement when you need with replacement | Specify `replace=True` or `replace=False` |
| Using Python's `random` module for arrays | Use NumPy's `np.random` for arrays |

---

### Interview Questions

1. **How do you generate a random sample from a normal distribution in NumPy?**  
   *Answer*: Using `np.random.normal(loc=mean, scale=std, size=n)`.

2. **How do you make random numbers reproducible?**  
   *Answer*: Using `np.random.seed(seed_value)` at the beginning of your code.

3. **What is the difference between `np.random.rand()` and `np.random.random()`?**  
   *Answer*: They are essentially the same – both generate uniform [0, 1) random numbers. `np.random.rand()` takes shape arguments, while `np.random.random()` takes a tuple.

---

### Assignment and Mini Project

**Assignment 3.8** – Random number practice:
```python
# 1. Generate a 5x5 array of random integers (1-100)
# 2. Generate a 3x4 array of random numbers from a normal distribution (mean=0, std=1)
# 3. Randomly sample 20 elements from a list of 50 with replacement
# 4. Randomly sample 20 elements without replacement
# 5. Shuffle a 1D array of 15 elements
# 6. Use a seed to reproduce the results
# 7. Print all arrays
```

**Mini Project** – Monte Carlo Stock Simulator:
Create a program that:
1. Simulates 5 stocks over 252 trading days using Geometric Brownian Motion:
   - Each stock has a different starting price (100, 120, 90, 150, 80).
   - Each stock has a different annual drift (0.05, 0.07, 0.03, 0.09, 0.06).
   - Each stock has a different annual volatility (0.2, 0.25, 0.15, 0.30, 0.18).
2. Uses `np.random.normal()` to generate daily returns.
3. Calculates the final price for each stock.
4. Calculates the total return for each stock.
5. Calculates the correlation between all stocks.
6. Runs 1000 simulations and calculates:
   - Average final price for each stock.
   - Probability of each stock ending above its starting price.
7. Uses `np.random.seed()` for reproducibility.
8. Prints a comprehensive summary report.

---

### Summary and Revision Notes

- Random functions: `rand()`, `randn()`, `randint()`, `random()`, `normal()`, `uniform()`.
- `choice()` for random sampling.
- `permutation()` and `shuffle()` for reordering.
- `seed()` for reproducibility.
- Monte Carlo simulations use random numbers for modeling uncertainty.

---

## Lesson 3.9 – Performance Benefits

### Concept Explanation

This lesson consolidates everything we've learned about NumPy's performance advantages. Understanding why NumPy is fast helps you write better code.

**Why NumPy is fast**:

1. **Compiled Code**: Operations are implemented in C/Fortran, not Python.
2. **Memory Efficiency**: Arrays store data in contiguous memory blocks.
3. **Vectorization**: Operations are applied to entire arrays at once.
4. **No Type Checking**: Arrays are homogeneous, so there's no type checking overhead.
5. **Cache Efficiency**: Contiguous memory access improves CPU cache utilisation.

**Performance Comparison**:

| **Operation** | **Python List** | **NumPy Array** | **Speedup** |
|---------------|-----------------|-----------------|-------------|
| Sum of 10M elements | ~0.5s | ~0.01s | 50x |
| Element-wise multiply | ~0.4s | ~0.005s | 80x |
| Square root | ~1.2s | ~0.02s | 60x |
| Conditional logic | ~0.8s | ~0.01s | 80x |

---

### Importance and Real-World Use Cases

- **Why it matters**: In data analytics, you often work with large datasets (millions or billions of rows). Performance is critical. NumPy's speed enables you to process data efficiently.

- **Use cases**:
  - A **data engineer** processes large datasets in production pipelines.
  - A **data scientist** trains machine learning models on millions of samples.
  - A **financial analyst** runs Monte Carlo simulations with thousands of iterations.

---

### Step-by-Step Demonstration

**Performance Comparison: Sum**:

```python
import numpy as np
import time

# Python list
list_size = 10_000_000
py_list = list(range(list_size))

start = time.time()
sum_py = sum(py_list)
end = time.time()
print(f"Python sum time: {end - start:.4f}s")

# NumPy array
np_arr = np.array(py_list)

start = time.time()
sum_np = np_arr.sum()
end = time.time()
print(f"NumPy sum time: {end - start:.4f}s")
print(f"Speedup: {(end - start_py) / (end - start_np):.1f}x")
```

**Performance Comparison: Element-wise Operation**:

```python
# Python list
py_list1 = [i for i in range(10_000_000)]
py_list2 = [i * 2 for i in range(10_000_000)]

start = time.time()
py_result = [a + b for a, b in zip(py_list1, py_list2)]
end = time.time()
print(f"Python list add time: {end - start:.4f}s")

# NumPy array
np_arr1 = np.array(py_list1)
np_arr2 = np.array(py_list2)

start = time.time()
np_result = np_arr1 + np_arr2
end = time.time()
print(f"NumPy add time: {end - start:.4f}s")
```

**Performance Comparison: Conditional Logic**:

```python
# Python list
py_list = [i for i in range(10_000_000)]

start = time.time()
py_result = [x * 2 if x > 5_000_000 else x for x in py_list]
end = time.time()
print(f"Python list conditional time: {end - start:.4f}s")

# NumPy array
np_arr = np.array(py_list)

start = time.time()
np_result = np.where(np_arr > 5_000_000, np_arr * 2, np_arr)
end = time.time()
print(f"NumPy conditional time: {end - start:.4f}s")
```

**Memory Comparison**:

```python
import sys

# Python list
py_list = [i for i in range(1_000_000)]
list_memory = sys.getsizeof(py_list) + sum(sys.getsizeof(i) for i in py_list)
print(f"Python list memory: {list_memory / 1024 / 1024:.2f} MB")

# NumPy array
np_arr = np.array(py_list)
print(f"NumPy array memory: {np_arr.nbytes / 1024 / 1024:.2f} MB")
```

---

### Practical Examples

**Example 1: Large Dataset Processing**:

```python
# Processing 10 million records
def process_python():
    data = [i for i in range(10_000_000)]
    result = []
    for x in data:
        if x % 2 == 0:
            result.append(x ** 2)
        else:
            result.append(x ** 0.5)
    return result

def process_numpy():
    data = np.arange(10_000_000, dtype=np.float64)
    return np.where(data % 2 == 0, data ** 2, np.sqrt(data))

# Compare execution times
# process_python()  # Slow
# process_numpy()   # Fast
```

**Example 2: Real-time Data Processing**:

```python
# Simulating real-time data processing
def process_loop(data):
    result = []
    for x in data:
        if x > 0:
            result.append(np.log(x + 1))
        else:
            result.append(0)
    return np.array(result)

def process_vectorized(data):
    return np.where(data > 0, np.log(data + 1), 0)

# Testing with different sizes
sizes = [1000, 10000, 100000, 1000000]
for size in sizes:
    data = np.random.randn(size)
    print(f"Size: {size}")
    print(f"  Loop time: {timeit.timeit(lambda: process_loop(data), number=10):.4f}s")
    print(f"  Vectorized time: {timeit.timeit(lambda: process_vectorized(data), number=10):.4f}s")
```

---

### Hands-on Coding Exercises

**Exercise 3.20** – Performance comparison:
```python
# Compare performance of:
# 1. Sum of 5 million numbers (Python list vs NumPy array)
# 2. Element-wise multiplication (Python list vs NumPy array)
# 3. Square root (Python list vs NumPy array)
# 4. Conditional logic (Python list vs NumPy array)
# 5. Memory usage
# Print a summary table of results
```

**Exercise 3.21** – Optimization practice:
```python
# 1. Create a function to calculate the mean of an array using a Python loop
# 2. Create a function to calculate the mean using NumPy's mean()
# 3. Compare the execution times for sizes: 100, 1000, 10000, 100000, 1000000
# 4. Print a table of results
# 5. Calculate the speedup factor for each size
```

---

### Mini Quiz

1. Why is NumPy faster than Python lists?
2. What is vectorization?
3. How does memory efficiency contribute to performance?
4. What is the speedup factor for NumPy over Python loops?
5. Why should you avoid Python loops with NumPy arrays?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using Python loops for numerical operations | Use NumPy's vectorized operations |
| Creating many small arrays | Use large arrays and vectorized operations |
| Not using the right data types | Use appropriate `dtype` for memory efficiency |
| Copying arrays unnecessarily | Use views and in-place operations when possible |

---

### Interview Questions

1. **Why is NumPy faster than Python lists?**  
   *Answer*: NumPy arrays are stored in contiguous memory blocks, operations are implemented in compiled C code, and vectorization eliminates Python loop overhead.

2. **What is the memory advantage of NumPy arrays over Python lists?**  
   *Answer*: NumPy arrays use homogeneous data types and store data in contiguous blocks, while Python lists store pointers to objects. This makes NumPy arrays much more memory efficient.

3. **How would you optimise a slow NumPy operation?**  
   *Answer*: Check if you're using vectorized operations, avoid unnecessary copies, use appropriate data types, and consider using `np.einsum()` for complex tensor operations.

---

### Assignment and Mini Project

**Assignment 3.9** – Performance testing:
```python
# 1. Create functions for the following operations (both loop and vectorized):
#    - Sum
#    - Mean
#    - Standard deviation
#    - Conditional operation (double if > mean)
# 2. Test with array sizes: 100, 1000, 10000, 100000, 1000000
# 3. Measure execution times
# 4. Calculate speedup factors
# 5. Print a comprehensive table of results
# 6. Write a summary of your findings
```

**Mini Project** – Performance Benchmark Tool:
Create a program that:
1. Defines a set of operations (sum, mean, std, sqrt, conditional, etc.).
2. Defines a set of array sizes (100, 1,000, 10,000, 100,000, 1,000,000, 10,000,000).
3. For each operation and size, measures:
   - Time using Python loops.
   - Time using NumPy vectorized operations.
   - Memory usage of Python list vs NumPy array.
4. Stores the results in a structured format.
5. Generates a report showing:
   - Execution times in a table.
   - Speedup factors.
   - Memory comparison.
6. Plots the results (if Matplotlib is available) or prints a formatted report.

---

### Summary and Revision Notes

- NumPy is fast because of:
  - Compiled C/Fortran code.
  - Contiguous memory storage.
  - Vectorized operations.
  - Homogeneous data types.
  - Cache efficiency.
- Speedup factors are typically 10-100x over Python loops.
- Use vectorized operations for maximum performance.
- Avoid Python loops with NumPy arrays.
- Use appropriate data types for memory efficiency.

---

## Final Phase 3 Assessment

Now that you have completed all lessons, test your overall understanding.

### Self-Evaluation Checklist

- I can create and manipulate NumPy arrays.

- I can perform arithmetic, comparison, and logical operations.

- I can use indexing and slicing to access and modify array elements.

- I understand broadcasting and can apply it correctly.

- I use vectorized operations instead of Python loops.

- I can apply mathematical and statistical operations.

- I can generate random numbers using NumPy's random module.

- I understand the performance benefits of NumPy.



---

### Answers to Mini Quizzes

**Lesson 3.1**: 1. Numerical Python. 2. ndarray. 3. `np.zeros(shape)`. 4. `np.array()` from a list; `np.arange()` generates a range. 5. `.shape`.

**Lesson 3.2**: 1. `np.zeros((2, 3))`. 2. `arange()` uses step; `linspace()` uses number of points. 3. Changes array dimensions. 4. `arr.flatten()`. 5. Creates identity matrix.

**Lesson 3.3**: 1. Operations applied to entire arrays. 2. `arr1 + arr2`. 3. `arr.mean()`. 4. `axis=0` for columns, `axis=1` for rows. 5. Matrix multiplication.

**Lesson 3.4**: 1. `arr[-1]`. 2. Elements from index 2 to 5 (stop exclusive). 3. `arr[:, 0:3]`. 4. Using conditions to select elements. 5. Conditional replacement.

**Lesson 3.5**: 1. Stretching smaller arrays to match larger ones. 2. Yes, shape (4,) broadcasts to (3, 4). 3. Adds a new axis. 4. Raises an error. 5. `matrix + column_vector`.

**Lesson 3.6**: 1. Applying operations to entire arrays. 2. No Python loop overhead. 3. A vectorized function. 4. `np.where(condition, value_if_true, value_if_false)`. 5. They are slow.

**Lesson 3.7**: 1. `np.median(arr)`. 2. `sum()` gives total; `cumsum()` gives cumulative. 3. `np.corrcoef(arr1, arr2)`. 4. Along columns (column-wise). 5. `arr.argmax()`.

**Lesson 3.8**: 1. `np.random.randint(1, 11)`. 2. For reproducibility. 3. `np.random.choice(arr, size=n, replace=False)`. 4. `rand()` is uniform [0,1); `randn()` is standard normal. 5. `np.random.shuffle(arr)`.

**Lesson 3.9**: 1. Compiled C code, memory efficiency, vectorization. 2. Operations on entire arrays. 3. Reduces memory overhead and improves cache usage. 4. 10-100x. 5. They are slow.

---

**Congratulations!** You have completed Phase 3 of Python for Data Analytics. You now have a solid foundation in NumPy – the fundamental library for numerical computing. Keep practising!
