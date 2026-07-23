# Phase 5: Data Visualization

Welcome to **Phase 5** – the visual storytelling phase of your Python for Data Analytics journey! You have learned to clean, manipulate, and analyse data with Pandas. Now, you will learn how to **visualise** that data – turning numbers into insights, patterns, and stories.

Visualisation is the bridge between data and decision-making. A well-crafted chart can reveal trends, outliers, and relationships that are invisible in tables of numbers. In this phase, we'll cover the most important visualisation libraries in Python:

- **Matplotlib** – the foundational library for static, animated, and interactive visualisations.
- **Line charts** – for trends over time.
- **Bar charts** – for categorical comparisons.
- **Pie charts** – for part-to-whole relationships.
- **Histograms** – for distributions.
- **Scatter plots** – for relationships between variables.
- **Box plots** – for summarising distributions.
- **Subplots** – for multiple charts in one figure.
- **Figure customisation** – for professional, publication-ready charts.
- **Saving charts** – to export your visualisations.

By the end of this phase, you'll be able to create professional charts that communicate insights effectively.

Let's start visualising!

---

## Lesson 5.1 – Introduction to Matplotlib

### Concept Explanation

**Matplotlib** is the foundational plotting library in Python. It provides a MATLAB-like interface for creating static, animated, and interactive visualisations. Most other Python plotting libraries (Seaborn, Plotly, etc.) are built on top of Matplotlib.

**Key concepts**:
- **Figure**: The entire window or page where the plot is drawn.
- **Axes**: The area where the data is plotted (a subplot).
- **Axis**: The x or y line with ticks and labels.
- **Artist**: Everything you see in the figure (lines, points, text, etc.).

**Two interfaces**:
1. **pyplot interface**: `import matplotlib.pyplot as plt` – the most common way.
2. **Object-oriented interface**: More control, but more verbose.

**Installation**:
```bash
pip install matplotlib
```

**Importing**:
```python
import matplotlib.pyplot as plt
import numpy as np
```

---

### Importance and Real-World Use Cases

- **Why it matters**: Visualisation is the most effective way to communicate data insights. Matplotlib is the foundation of Python visualisation – mastering it enables you to create any chart you can imagine.

- **Use cases**:
  - A **data analyst** creates line charts to show sales trends.
  - A **data scientist** creates scatter plots to explore feature relationships.
  - A **financial analyst** creates bar charts to compare company performance.

---

### Step-by-Step Demonstration

**Your First Plot**:

```python
import matplotlib.pyplot as plt
import numpy as np

# Data
x = np.array([1, 2, 3, 4, 5])
y = np.array([2, 4, 6, 8, 10])

# Create a simple line plot
plt.plot(x, y)
plt.title("My First Plot")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.show()
```

**Figure and Axes (Object-Oriented)**:

```python
# Create a figure and axes
fig, ax = plt.subplots()

# Plot data
ax.plot(x, y)
ax.set_title("Object-Oriented Plot")
ax.set_xlabel("X-axis")
ax.set_ylabel("Y-axis")
plt.show()
```

**Plotting Multiple Lines**:

```python
# Multiple lines
x = np.linspace(0, 10, 100)
y1 = np.sin(x)
y2 = np.cos(x)

plt.plot(x, y1, label='sin(x)')
plt.plot(x, y2, label='cos(x)')
plt.legend()
plt.title("Sine and Cosine")
plt.xlabel("x")
plt.ylabel("y")
plt.show()
```

**Adding Styles**:

```python
plt.plot(x, y1, color='blue', linestyle='-', linewidth=2, marker='o')
plt.plot(x, y2, color='red', linestyle='--', linewidth=2, marker='s')
plt.legend()
plt.grid(True)
plt.show()
```

---

### Practical Examples

- **Example 1**: Plotting sales data over time.
- **Example 2**: Comparing two datasets on the same plot.
- **Example 3**: Customising a plot for a presentation.

---

### Hands-on Coding Exercises

**Exercise 5.1** – Simple plot:
```python
# 1. Create x values from 0 to 10
# 2. Create y = x**2
# 3. Plot y against x
# 4. Add title, xlabel, ylabel
# 5. Display the plot
```

**Exercise 5.2** – Multiple lines:
```python
# 1. Create x from 0 to 2π
# 2. Plot sin(x), cos(x), tan(x)
# 3. Add a legend
# 4. Customize line styles
# 5. Add a grid
# 6. Display the plot
```

---

### Mini Quiz

1. What is the standard alias for `matplotlib.pyplot`?
2. What is the difference between a Figure and an Axes?
3. How do you add a title to a plot?
4. What function is used to display a plot?
5. How do you add a legend to a plot?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting `plt.show()` – plot doesn't appear | Always call `plt.show()` |
| Not importing the library | `import matplotlib.pyplot as plt` |
| Using the wrong interface (pyplot vs OO) | Be consistent in your code |
| Not adding labels and titles | Always label your axes and add a title |

---

### Interview Questions

1. **What is Matplotlib and why is it used?**  
   *Answer*: Matplotlib is the foundational plotting library in Python. It is used to create static, animated, and interactive visualisations, and is the basis for most other Python plotting libraries.

2. **What is the difference between `plt.plot()` and `plt.show()`?**  
   *Answer*: `plt.plot()` creates the plot (adds data to the figure). `plt.show()` displays the plot on the screen.

3. **What is the purpose of `plt.subplots()`?**  
   *Answer*: `plt.subplots()` creates a Figure and one or more Axes objects, providing an object-oriented interface for plotting.

---

### Assignment and Mini Project

**Assignment 5.1** – Basic plotting:
```python
# 1. Create x values from -10 to 10
# 2. Create y = x^3 - 3x
# 3. Plot y against x
# 4. Add title, xlabel, ylabel, and grid
# 5. Save the plot
# 6. Display the plot
```

**Mini Project** – Function Plotter:
Create a program that:
1. Plots the following functions on the same figure:
   - f(x) = x^2
   - g(x) = x^3
   - h(x) = sqrt(x) (for x >= 0)
2. Uses different colours and line styles.
3. Adds a legend, title, and axis labels.
4. Adds a grid.
5. Displays the plot.

---

### Summary and Revision Notes

- Matplotlib is the foundational Python plotting library.
- Import as `import matplotlib.pyplot as plt`.
- Two interfaces: pyplot (simple) and object-oriented (more control).
- `plt.plot()` – create a line plot.
- `plt.title()`, `plt.xlabel()`, `plt.ylabel()` – add labels.
- `plt.legend()` – add a legend.
- `plt.show()` – display the plot.

---

## Lesson 5.2 – Line Charts

### Concept Explanation

**Line charts** are used to display trends over time or continuous data. They are one of the most common chart types in data analytics.

**Key uses**:
- Time series analysis (stock prices, sales over time).
- Showing continuous trends.
- Comparing multiple series.

**Syntax**:
```python
plt.plot(x, y, color, linestyle, linewidth, marker, label)
```

**Common parameters**:
- `color`: 'blue', 'red', 'green', 'black', etc.
- `linestyle`: '-', '--', '-.', ':'.
- `linewidth`: float.
- `marker`: 'o', 's', '^', 'D', 'v', etc.
- `label`: legend label.

---

### Importance and Real-World Use Cases

- **Why it matters**: Line charts are the standard for showing trends. They reveal seasonality, growth, and patterns over time.

- **Use cases**:
  - A **financial analyst** plots stock prices over time.
  - A **sales analyst** shows monthly revenue trends.
  - A **marketing analyst** tracks campaign performance.

---

### Step-by-Step Demonstration

```python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Create sample data (time series)
np.random.seed(42)
days = np.arange(1, 101)
sales = 100 + np.cumsum(np.random.randn(100) * 5)  # Random walk
sales = np.maximum(sales, 50)  # floor at 50

# Basic line chart
plt.plot(days, sales)
plt.title("Sales Trend")
plt.xlabel("Day")
plt.ylabel("Sales ($)")
plt.grid(True)
plt.show()

# Multiple lines
np.random.seed(42)
sales_A = 100 + np.cumsum(np.random.randn(100) * 5)
sales_B = 120 + np.cumsum(np.random.randn(100) * 3)
sales_C = 80 + np.cumsum(np.random.randn(100) * 4)

plt.plot(days, sales_A, label='Product A', color='blue', linewidth=2)
plt.plot(days, sales_B, label='Product B', color='red', linewidth=2, linestyle='--')
plt.plot(days, sales_C, label='Product C', color='green', linewidth=2, linestyle='-.')

plt.title("Product Sales Comparison")
plt.xlabel("Day")
plt.ylabel("Sales ($)")
plt.legend()
plt.grid(True)
plt.show()

# With markers
plt.plot(days[::10], sales_A[::10], label='Product A', color='blue', 
         marker='o', linestyle='-', linewidth=2)
plt.plot(days[::10], sales_B[::10], label='Product B', color='red', 
         marker='s', linestyle='--', linewidth=2)
plt.legend()
plt.show()

# Customizing line chart
plt.figure(figsize=(10, 6))
plt.plot(days, sales_A, color='darkblue', linewidth=2.5, 
         linestyle='-', marker='o', markersize=4, label='Product A')
plt.title("Customized Line Chart", fontsize=16)
plt.xlabel("Day", fontsize=14)
plt.ylabel("Sales ($)", fontsize=14)
plt.legend(fontsize=12)
plt.grid(True, alpha=0.3)
plt.xticks(fontsize=10)
plt.yticks(fontsize=10)
plt.tight_layout()
plt.show()
```

**Filling Area under the Line**:

```python
plt.fill_between(days, sales_A, alpha=0.3, color='blue')
plt.plot(days, sales_A, color='blue', linewidth=2)
plt.title("Area Under the Curve")
plt.xlabel("Day")
plt.ylabel("Sales ($)")
plt.show()
```

---

### Practical Examples

- **Example 1**: Plotting monthly sales with seasonal patterns.
- **Example 2**: Comparing multiple product sales over time.
- **Example 3**: Creating a stock price chart with moving averages.

---

### Hands-on Coding Exercises

**Exercise 5.3** – Basic line chart:
```python
# 1. Create a time series from 0 to 50
# 2. Generate y = sin(x) + noise
# 3. Plot the line
# 4. Add title, labels, and grid
# 5. Display the plot
```

**Exercise 5.4** – Multiple lines:
```python
# 1. Create x from 0 to 10
# 2. Plot y1 = x, y2 = x**2, y3 = x**3
# 3. Use different colours and line styles
# 4. Add a legend
# 5. Display the plot
```

---

### Mini Quiz

1. What is the primary use of a line chart?
2. How do you change the line style to dashed?
3. How do you add markers to a line chart?
4. What parameter is used to add a legend label?
5. How do you fill the area under a line?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using line charts for categorical data | Use bar charts for categories |
| Too many lines on one chart | Limit to 3-5 lines; use separate charts if needed |
| Not handling missing data | Interpolate or use markers for missing data |
| Small font sizes | Increase font sizes for readability |

---

### Interview Questions

1. **When would you use a line chart instead of a bar chart?**  
   *Answer*: A line chart is used for continuous data, especially time series, to show trends and patterns. A bar chart is used for categorical comparisons.

2. **How do you plot multiple lines on the same chart?**  
   *Answer*: Call `plt.plot()` multiple times with different data, then add a legend.

3. **What is the purpose of `fill_between()`?**  
   *Answer*: `fill_between()` fills the area between a line and a baseline, often used to highlight the area under a curve.

---

### Assignment and Mini Project

**Assignment 5.2** – Line chart practice:
```python
# 1. Create a time series of 100 points (simulated stock price)
# 2. Plot the stock price
# 3. Add a 10-day moving average
# 4. Add a 20-day moving average
# 5. Use different colours and line styles
# 6. Add a legend, title, and labels
# 7. Display the plot
```

**Mini Project** – Stock Price Visualizer:
Create a program that:
1. Generates simulated stock prices for 3 companies over 252 trading days.
2. Plots the prices on the same chart.
3. Adds a 20-day moving average for each.
4. Uses different colours and line styles.
5. Adds a legend, title, and axis labels.
6. Saves the chart to a file.

---

### Summary and Revision Notes

- Line charts show trends over continuous data.
- `plt.plot(x, y, ...)` – create a line chart.
- Customize with `color`, `linestyle`, `linewidth`, `marker`.
- Add legend with `label` and `plt.legend()`.
- Use `fill_between()` for area under the curve.

---

## Lesson 5.3 – Bar Charts

### Concept Explanation

**Bar charts** are used to compare categorical data. They are one of the most versatile and commonly used chart types.

**Types**:
- **Vertical bar chart**: `plt.bar()`.
- **Horizontal bar chart**: `plt.barh()`.
- **Stacked bar chart**: Multiple bars stacked on top of each other.
- **Grouped bar chart**: Multiple bars side by side.

**Syntax**:
```python
plt.bar(x, height, width, color, label)
```

**Parameters**:
- `x`: category positions.
- `height`: bar heights.
- `width`: bar width.
- `color`: bar color.
- `label`: legend label.

---

### Importance and Real-World Use Cases

- **Why it matters**: Bar charts are the standard for comparing categories – sales by product, revenue by region, etc.

- **Use cases**:
  - A **sales analyst** compares product sales.
  - A **marketing analyst** compares campaign performance.
  - A **financial analyst** compares company expenses.

---

### Step-by-Step Demonstration

```python
import matplotlib.pyplot as plt
import numpy as np

# Data
categories = ['Product A', 'Product B', 'Product C', 'Product D', 'Product E']
sales = [1200, 1800, 900, 1500, 1100]
colors = ['blue', 'green', 'red', 'orange', 'purple']

# Basic bar chart
plt.bar(categories, sales, color='skyblue', edgecolor='black')
plt.title("Sales by Product")
plt.xlabel("Product")
plt.ylabel("Sales ($)")
plt.show()

# Customized bar chart
plt.bar(categories, sales, color=colors, edgecolor='black', linewidth=1.5)
plt.title("Sales by Product", fontsize=16)
plt.xlabel("Product", fontsize=14)
plt.ylabel("Sales ($)", fontsize=14)
plt.xticks(rotation=45, ha='right')
plt.grid(axis='y', alpha=0.3)
plt.show()

# Horizontal bar chart
plt.barh(categories, sales, color='skyblue', edgecolor='black')
plt.title("Sales by Product (Horizontal)")
plt.xlabel("Sales ($)")
plt.ylabel("Product")
plt.show()

# Grouped bar chart (multiple categories)
np.random.seed(42)
categories = ['Q1', 'Q2', 'Q3', 'Q4']
product_A = np.random.randint(100, 300, 4)
product_B = np.random.randint(100, 300, 4)
product_C = np.random.randint(100, 300, 4)

width = 0.25
x = np.arange(len(categories))

plt.bar(x - width, product_A, width, label='Product A', color='blue')
plt.bar(x, product_B, width, label='Product B', color='green')
plt.bar(x + width, product_C, width, label='Product C', color='red')

plt.xticks(x, categories)
plt.title("Quarterly Sales by Product")
plt.xlabel("Quarter")
plt.ylabel("Sales ($)")
plt.legend()
plt.show()

# Stacked bar chart
plt.bar(categories, product_A, label='Product A', color='blue')
plt.bar(categories, product_B, bottom=product_A, label='Product B', color='green')
plt.bar(categories, product_C, bottom=product_A+product_B, label='Product C', color='red')

plt.title("Stacked Bar Chart")
plt.xlabel("Quarter")
plt.ylabel("Sales ($)")
plt.legend()
plt.show()
```

**Adding Data Labels**:

```python
bars = plt.bar(categories, sales, color='skyblue')
plt.title("Sales by Product")
plt.xlabel("Product")
plt.ylabel("Sales ($)")

# Add data labels
for bar, value in zip(bars, sales):
    plt.text(bar.get_x() + bar.get_width()/2, bar.get_height() + 10,
             f'${value}', ha='center', va='bottom')

plt.show()
```

---

### Practical Examples

- **Example 1**: Comparing sales across regions.
- **Example 2**: Analysing survey responses by category.
- **Example 3**: Creating a budget vs actual comparison.

---

### Hands-on Coding Exercises

**Exercise 5.5** – Basic bar chart:
```python
# 1. Create categories: ['A', 'B', 'C', 'D', 'E']
# 2. Create values: [10, 25, 15, 30, 20]
# 3. Create a bar chart
# 4. Add title, labels
# 5. Display the plot
```

**Exercise 5.6** – Grouped bar chart:
```python
# 1. Create categories: ['Q1', 'Q2', 'Q3', 'Q4']
# 2. Create 3 sets of values (3 products)
# 3. Create a grouped bar chart
# 4. Add a legend
# 5. Display the plot
```

---

### Mini Quiz

1. What is the difference between `plt.bar()` and `plt.barh()`?
2. How do you create a grouped bar chart?
3. How do you add data labels to a bar chart?
4. What parameter controls bar width?
5. How do you create a stacked bar chart?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Too many categories – bars become unreadable | Limit to 10-15 categories; group others |
| No sorting – random order makes comparison hard | Sort bars by value (ascending/descending) |
| Using 3D bar charts | Avoid 3D effects; they distort perception |
| Not labelling data points | Add data labels for exact values |

---

### Interview Questions

1. **When would you use a bar chart vs a line chart?**  
   *Answer*: A bar chart is used for categorical comparisons (e.g., sales by product). A line chart is used for continuous trends (e.g., sales over time).

2. **How do you create a horizontal bar chart?**  
   *Answer*: Using `plt.barh()` instead of `plt.bar()`.

3. **What is the difference between grouped and stacked bar charts?**  
   *Answer*: Grouped bars show values side-by-side for comparison. Stacked bars show composition of totals.

---

### Assignment and Mini Project

**Assignment 5.3** – Bar chart practice:
```python
# 1. Create a dataset: Product, Sales, Profit
# 2. Create a bar chart of Sales by Product
# 3. Create a grouped bar chart of Sales and Profit by Product
# 4. Add data labels
# 5. Sort bars by Sales (descending)
# 6. Display the plot
```

**Mini Project** – Sales Dashboard:
Create a program that:
1. Generates sales data for 5 products across 4 quarters.
2. Creates:
   - A bar chart of total sales by product.
   - A grouped bar chart of quarterly sales by product.
   - A stacked bar chart of quarterly sales.
   - A horizontal bar chart of profit by product.
3. Adds titles, labels, legends, and data labels.
4. Displays all charts.

---

### Summary and Revision Notes

- Bar charts compare categorical data.
- `plt.bar()` – vertical bars.
- `plt.barh()` – horizontal bars.
- Grouped bars: `plt.bar(x - width, ...)`.
- Stacked bars: `bottom` parameter.
- Add data labels with `plt.text()`.

---

## Lesson 5.4 – Pie Charts

### Concept Explanation

**Pie charts** show the proportion of a whole. Each slice represents a category's contribution to the total.

**When to use**:
- Part-to-whole relationships.
- Few categories (2-5).
- When you want to show percentages.

**When NOT to use**:
- More than 5 categories.
- When precise comparison is needed (bar charts are better).

**Syntax**:
```python
plt.pie(x, labels, autopct, colors, explode, startangle, shadow)
```

**Parameters**:
- `x`: slice sizes.
- `labels`: slice labels.
- `autopct`: percentage format.
- `colors`: slice colours.
- `explode`: explode a slice out.
- `startangle`: starting angle.
- `shadow`: add shadow.

---

### Importance and Real-World Use Cases

- **Why it matters**: Pie charts are intuitive for showing proportions – market share, budget allocation, survey responses.

- **Use cases**:
  - A **marketing analyst** shows channel distribution.
  - A **financial analyst** shows expense categories.
  - A **sales analyst** shows product mix.

---

### Step-by-Step Demonstration

```python
import matplotlib.pyplot as plt
import numpy as np

# Data
labels = ['Product A', 'Product B', 'Product C', 'Product D', 'Product E']
sizes = [30, 25, 20, 15, 10]
colors = ['gold', 'lightblue', 'lightgreen', 'orange', 'red']

# Basic pie chart
plt.pie(sizes, labels=labels, colors=colors, autopct='%1.1f%%')
plt.title("Market Share by Product")
plt.show()

# Exploded pie chart
explode = (0.1, 0, 0, 0, 0)  # explode the first slice
plt.pie(sizes, labels=labels, colors=colors, autopct='%1.1f%%',
        explode=explode, shadow=True, startangle=90)
plt.title("Exploded Pie Chart")
plt.show()

# Donut chart (with a hole)
plt.pie(sizes, labels=labels, colors=colors, autopct='%1.1f%%',
        wedgeprops={'edgecolor': 'white', 'linewidth': 2},
        pctdistance=0.85)
centre_circle = plt.Circle((0,0), 0.70, fc='white')
plt.gca().add_artist(centre_circle)
plt.title("Donut Chart")
plt.show()

# Customizing pie chart
fig, ax = plt.subplots()
wedges, texts, autotexts = ax.pie(sizes, labels=labels, colors=colors,
                                   autopct='%1.1f%%',
                                   wedgeprops={'edgecolor': 'black', 'linewidth': 1})

# Format text
plt.setp(texts, size=12, weight='bold')
plt.setp(autotexts, size=10, weight='bold', color='white')
ax.set_title("Customized Pie Chart", size=16)
plt.show()
```

**Pie Chart with Legend**:

```python
plt.pie(sizes, labels=labels, colors=colors, autopct='%1.1f%%')
plt.legend(labels, loc='best')
plt.title("Pie Chart with Legend")
plt.show()
```

---

### Practical Examples

- **Example 1**: Market share by company.
- **Example 2**: Budget allocation by department.
- **Example 3**: Traffic sources for a website.

---

### Hands-on Coding Exercises

**Exercise 5.7** – Basic pie chart:
```python
# 1. Create categories: ['A', 'B', 'C', 'D']
# 2. Create values: [40, 30, 20, 10]
# 3. Create a pie chart
# 4. Add labels and percentages
# 5. Display the plot
```

**Exercise 5.8** – Donut chart:
```python
# 1. Use the same data as above
# 2. Create a donut chart
# 3. Add a centre label
# 4. Display the plot
```

---

### Mini Quiz

1. When should you use a pie chart?
2. What is the purpose of `autopct`?
3. How do you explode a slice?
4. What is a donut chart?
5. When should you NOT use a pie chart?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Too many slices – unreadable | Limit to 5 categories; group the rest as 'Other' |
| Using 3D pie charts | Avoid 3D effects; they distort perception |
| Not sorting slices | Sort slices by size for easier comparison |
| No percentages | Always include percentages |

---

### Interview Questions

1. **When would you use a pie chart vs a bar chart?**  
   *Answer*: A pie chart is used to show part-to-whole relationships with few categories. A bar chart is better for comparing individual categories, especially with many categories.

2. **What is the maximum number of categories for a pie chart?**  
   *Answer*: 5 categories is recommended. More than 5 makes the chart difficult to read.

3. **What is a donut chart and why is it used?**  
   *Answer*: A donut chart is a pie chart with a hole in the centre. It is often used for aesthetic reasons and can be easier to read than a pie chart.

---

### Assignment and Mini Project

**Assignment 5.4** – Pie chart practice:
```python
# 1. Create a dataset: Department, Budget
# 2. Create a pie chart of budget allocation
# 3. Explode the largest slice
# 4. Add percentages
# 5. Create a donut chart
# 6. Display both charts
```

**Mini Project** – Expense Visualizer:
Create a program that:
1. Defines expense categories (Housing, Food, Transport, Entertainment, Savings, Other).
2. Assigns amounts to each category.
3. Creates:
   - A pie chart with percentages.
   - An exploded pie chart highlighting the largest category.
   - A donut chart.
4. Adds labels, percentages, and a title.
5. Displays all charts.

---

### Summary and Revision Notes

- Pie charts show part-to-whole relationships.
- `plt.pie(x, labels, autopct)`.
- Limit to 5 categories.
- Use `explode` to highlight a slice.
- Donut chart: add a circle in the centre.
- Add percentages with `autopct`.

---

## Lesson 5.5 – Histograms

### Concept Explanation

**Histograms** show the distribution of a single variable by dividing data into bins and counting the frequency in each bin. They are essential for understanding the shape of your data.

**Key uses**:
- Understanding data distribution.
- Identifying skewness and outliers.
- Checking assumptions for statistical tests.

**Syntax**:
```python
plt.hist(data, bins, color, edgecolor, alpha)
```

**Parameters**:
- `data`: the data to plot.
- `bins`: number of bins or bin edges.
- `color`: bar colour.
- `edgecolor`: bar border colour.
- `alpha`: transparency.
- `density`: normalise to probability density.

---

### Importance and Real-World Use Cases

- **Why it matters**: Histograms reveal the underlying distribution of data – whether it's normal, skewed, or has outliers.

- **Use cases**:
  - A **data analyst** examines the distribution of sales amounts.
  - A **data scientist** checks the distribution of features.
  - A **quality analyst** examines defect rates.

---

### Step-by-Step Demonstration

```python
import matplotlib.pyplot as plt
import numpy as np

# Generate sample data
np.random.seed(42)
data = np.random.normal(50, 10, 1000)  # Normal distribution
data_skewed = np.random.exponential(20, 1000)  # Skewed distribution

# Basic histogram
plt.hist(data, bins=30, color='skyblue', edgecolor='black')
plt.title("Histogram of Data")
plt.xlabel("Value")
plt.ylabel("Frequency")
plt.show()

# Customized histogram
plt.hist(data, bins=30, color='skyblue', edgecolor='black', alpha=0.7)
plt.title("Customized Histogram", fontsize=16)
plt.xlabel("Value", fontsize=14)
plt.ylabel("Frequency", fontsize=14)
plt.grid(axis='y', alpha=0.3)
plt.axvline(data.mean(), color='red', linestyle='--', label=f'Mean: {data.mean():.2f}')
plt.axvline(data.median(), color='green', linestyle='--', label=f'Median: {data.median():.2f}')
plt.legend()
plt.show()

# Multiple histograms
plt.hist(data, bins=30, color='blue', alpha=0.5, label='Normal')
plt.hist(data_skewed, bins=30, color='red', alpha=0.5, label='Skewed')
plt.title("Comparison of Distributions")
plt.xlabel("Value")
plt.ylabel("Frequency")
plt.legend()
plt.show()

# Density histogram
plt.hist(data, bins=30, color='skyblue', edgecolor='black', density=True)
plt.title("Density Histogram (Area = 1)")
plt.xlabel("Value")
plt.ylabel("Density")
plt.show()

# Histogram with custom bins
bins = [0, 20, 40, 60, 80, 100]
plt.hist(data, bins=bins, color='skyblue', edgecolor='black')
plt.title("Histogram with Custom Bins")
plt.xlabel("Value")
plt.ylabel("Frequency")
plt.show()
```

**Histogram with KDE (Kernel Density Estimation)**:

```python
from scipy import stats

# KDE plot (using matplotlib)
from scipy.stats import gaussian_kde
density = gaussian_kde(data)
x_vals = np.linspace(data.min(), data.max(), 100)
plt.hist(data, bins=30, color='skyblue', edgecolor='black', density=True, alpha=0.7)
plt.plot(x_vals, density(x_vals), color='red', linewidth=2, label='KDE')
plt.legend()
plt.title("Histogram with KDE")
plt.show()
```

---

### Practical Examples

- **Example 1**: Distribution of customer ages.
- **Example 2**: Distribution of product prices.
- **Example 3**: Distribution of test scores.

---

### Hands-on Coding Exercises

**Exercise 5.9** – Basic histogram:
```python
# 1. Generate 1000 random numbers from a normal distribution
# 2. Create a histogram with 20 bins
# 3. Add title and labels
# 4. Display the plot
```

**Exercise 5.10** – Multiple histograms:
```python
# 1. Generate two datasets: normal and uniform
# 2. Create histograms for both on the same plot
# 3. Use transparency
# 4. Add a legend
# 5. Display the plot
```

---

### Mini Quiz

1. What is the purpose of a histogram?
2. What does the `bins` parameter control?
3. How do you normalise a histogram (make the area = 1)?
4. What is the difference between a histogram and a bar chart?
5. How do you add a vertical line to a histogram?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Too few or too many bins | Use the square root rule or Sturges' rule |
| Not labelling axes | Always label axes |
| Using histograms for categorical data | Use bar charts for categorical data |
| Not using `alpha` for overlapping histograms | Use transparency for multiple histograms |

---

### Interview Questions

1. **What is the difference between a histogram and a bar chart?**  
   *Answer*: A histogram is used for continuous data and shows the distribution of a single variable. A bar chart is used for categorical data and compares categories.

2. **How do you choose the number of bins?**  
   *Answer*: Common rules include the square root rule (√n), Sturges' rule (log2(n) + 1), or the Freedman-Diaconis rule.

3. **What is a density histogram?**  
   *Answer*: A density histogram has an area of 1, making it comparable to probability density functions.

---

### Assignment and Mini Project

**Assignment 5.5** – Histogram practice:
```python
# 1. Load a dataset (or generate one) with a numeric column
# 2. Create a histogram of the data
# 3. Add a vertical line for the mean
# 4. Add a vertical line for the median
# 5. Customize the plot
# 6. Display the plot
```

**Mini Project** – Distribution Analyzer:
Create a program that:
1. Generates datasets from different distributions (normal, uniform, exponential, binomial).
2. Creates histograms for each.
3. Adds vertical lines for mean and median.
4. Creates a density histogram with KDE for each.
5. Displays all histograms in subplots.

---

### Summary and Revision Notes

- Histograms show data distributions.
- `plt.hist(data, bins)`.
- `bins` controls the number of bins.
- `density=True` normalises the histogram.
- Use transparency (`alpha`) for overlapping histograms.
- Add KDE with `scipy.stats.gaussian_kde`.

---

## Lesson 5.6 – Scatter Plots

### Concept Explanation

**Scatter plots** show the relationship between two numeric variables. Each point represents an observation, with position determined by its x and y values.

**Key uses**:
- Exploring relationships (positive, negative, or no correlation).
- Identifying outliers.
- Finding clusters.

**Syntax**:
```python
plt.scatter(x, y, s, c, alpha, marker)
```

**Parameters**:
- `x`: x-axis values.
- `y`: y-axis values.
- `s`: point size.
- `c`: point colour.
- `alpha`: transparency.
- `marker`: point shape.

---

### Importance and Real-World Use Cases

- **Why it matters**: Scatter plots reveal relationships and patterns that are invisible in summary statistics.

- **Use cases**:
  - A **sales analyst** plots advertising spend vs revenue.
  - A **data scientist** explores feature relationships.
  - A **quality analyst** plots temperature vs defect rate.

---

### Step-by-Step Demonstration

```python
import matplotlib.pyplot as plt
import numpy as np

# Generate sample data
np.random.seed(42)
x = np.random.randn(100) * 10 + 50
y = 0.8 * x + np.random.randn(100) * 10 + 20

# Basic scatter plot
plt.scatter(x, y, color='blue', alpha=0.6)
plt.title("Scatter Plot")
plt.xlabel("X")
plt.ylabel("Y")
plt.show()

# Customized scatter plot
colors = np.random.randn(100)
sizes = np.abs(np.random.randn(100) * 100 + 50)

plt.scatter(x, y, s=sizes, c=colors, alpha=0.7, cmap='viridis')
plt.colorbar(label='Color Scale')
plt.title("Customized Scatter Plot")
plt.xlabel("X")
plt.ylabel("Y")
plt.show()

# Adding a trend line
m, b = np.polyfit(x, y, 1)
x_line = np.linspace(x.min(), x.max(), 100)
y_line = m * x_line + b

plt.scatter(x, y, color='blue', alpha=0.6, label='Data')
plt.plot(x_line, y_line, color='red', linewidth=2, label='Trend Line')
plt.title("Scatter Plot with Trend Line")
plt.xlabel("X")
plt.ylabel("Y")
plt.legend()
plt.show()

# Correlation example
np.random.seed(42)
positive = np.random.randn(100) * 10 + 50
negative = -0.8 * positive + np.random.randn(100) * 10 + 100
no_corr = np.random.randn(100) * 10 + 50

fig, axes = plt.subplots(1, 3, figsize=(15, 5))

axes[0].scatter(positive, positive + np.random.randn(100) * 5, alpha=0.6)
axes[0].set_title("Positive Correlation")
axes[0].set_xlabel("X")
axes[0].set_ylabel("Y")

axes[1].scatter(positive, negative, alpha=0.6)
axes[1].set_title("Negative Correlation")
axes[1].set_xlabel("X")

axes[2].scatter(positive, no_corr, alpha=0.6)
axes[2].set_title("No Correlation")
axes[2].set_xlabel("X")

plt.tight_layout()
plt.show()
```

**Colour by Category**:

```python
# Simulate categorical data
categories = np.random.choice(['A', 'B', 'C'], 100)
colors = {'A': 'red', 'B': 'blue', 'C': 'green'}

for cat in np.unique(categories):
    mask = categories == cat
    plt.scatter(x[mask], y[mask], color=colors[cat], label=cat, alpha=0.7)

plt.title("Scatter Plot by Category")
plt.xlabel("X")
plt.ylabel("Y")
plt.legend()
plt.show()
```

---

### Practical Examples

- **Example 1**: Advertising spend vs sales.
- **Example 2**: Temperature vs energy consumption.
- **Example 3**: Height vs weight.

---

### Hands-on Coding Exercises

**Exercise 5.11** – Basic scatter plot:
```python
# 1. Generate x values from 0 to 50
# 2. Generate y = 2*x + noise
# 3. Create a scatter plot
# 4. Add title and labels
# 5. Display the plot
```

**Exercise 5.12** – Scatter with trend line:
```python
# 1. Generate data with a strong positive correlation
# 2. Create a scatter plot
# 3. Fit a linear trend line
# 4. Add the trend line to the plot
# 5. Display the plot
```

---

### Mini Quiz

1. What is the purpose of a scatter plot?
2. How do you add a trend line to a scatter plot?
3. What does the `s` parameter control?
4. What does the `alpha` parameter do?
5. How do you colour points by category?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Too many points – overplotting | Use `alpha` for transparency or reduce the sample |
| No colour coding for categories | Use colour to show categories |
| No trend line | Add a trend line to show the relationship |
| Over‑interpreting correlation as causation | Correlation does not imply causation |

---

### Interview Questions

1. **What is the purpose of a scatter plot?**  
   *Answer*: A scatter plot shows the relationship between two numeric variables, revealing correlations, outliers, and clusters.

2. **How do you add a trend line to a scatter plot?**  
   *Answer*: Fit a line using `np.polyfit()` and plot it with `plt.plot()`.

3. **What does a positive correlation look like on a scatter plot?**  
   *Answer*: As x increases, y also increases, with points roughly following an upward trend.

---

### Assignment and Mini Project

**Assignment 5.6** – Scatter plot practice:
```python
# 1. Load a dataset with two numeric columns (or generate them)
# 2. Create a scatter plot
# 3. Add a trend line
# 4. Colour points by a category
# 5. Add a title and labels
# 6. Display the plot
```

**Mini Project** – Correlation Explorer:
Create a program that:
1. Generates datasets with different types of correlation:
   - Strong positive.
   - Weak positive.
   - Strong negative.
   - No correlation.
2. Creates scatter plots for each.
3. Adds trend lines.
4. Displays all plots in a 2x2 grid.

---

### Summary and Revision Notes

- Scatter plots show relationships between two numeric variables.
- `plt.scatter(x, y)`.
- Use `s` for point size, `c` for colour.
- Use `alpha` for transparency.
- Add trend line with `np.polyfit()`.
- Colour by category for additional dimension.

---

## Lesson 5.7 – Box Plots

### Concept Explanation

**Box plots** (box-and-whisker plots) summarise the distribution of a dataset using five statistics:
- **Minimum** (excluding outliers).
- **First quartile (Q1)**.
- **Median (Q2)**.
- **Third quartile (Q3)**.
- **Maximum** (excluding outliers).
- **Outliers** – points beyond 1.5 × IQR.

**Key uses**:
- Comparing distributions across categories.
- Identifying outliers.
- Understanding spread and skewness.

**Syntax**:
```python
plt.boxplot(data, labels, notch, vert, patch_artist)
```

---

### Importance and Real-World Use Cases

- **Why it matters**: Box plots provide a compact summary of distributions and are excellent for comparing multiple groups.

- **Use cases**:
  - A **data analyst** compares salaries by department.
  - A **data scientist** compares feature distributions.
  - A **quality analyst** compares defect rates across shifts.

---

### Step-by-Step Demonstration

```python
import matplotlib.pyplot as plt
import numpy as np

# Generate sample data
np.random.seed(42)
data = [np.random.normal(50, 10, 100) for _ in range(4)]
data[0] = np.random.normal(40, 15, 100)  # Group 1
data[1] = np.random.normal(60, 10, 100)  # Group 2
data[2] = np.random.normal(50, 5, 100)   # Group 3
data[3] = np.random.normal(70, 20, 100)  # Group 4

# Basic box plot
plt.boxplot(data, labels=['A', 'B', 'C', 'D'])
plt.title("Box Plot")
plt.ylabel("Value")
plt.show()

# Customized box plot
plt.boxplot(data, labels=['A', 'B', 'C', 'D'],
            notch=True,  # Notched boxes
            patch_artist=True,  # Fill boxes
            boxprops=dict(facecolor='skyblue', color='black'),
            whiskerprops=dict(color='black'),
            capprops=dict(color='black'),
            medianprops=dict(color='red', linewidth=2),
            flierprops=dict(marker='o', markerfacecolor='red', markersize=6))
plt.title("Customized Box Plot", fontsize=16)
plt.ylabel("Value", fontsize=14)
plt.show()

# Horizontal box plot
plt.boxplot(data, labels=['A', 'B', 'C', 'D'], vert=False)
plt.title("Horizontal Box Plot")
plt.xlabel("Value")
plt.show()

# Grouped box plot (using pandas)
import pandas as pd

# Create a DataFrame with groups
np.random.seed(42)
df = pd.DataFrame({
    'Group': np.repeat(['A', 'B', 'C'], 100),
    'Value': np.concatenate([
        np.random.normal(40, 10, 100),
        np.random.normal(60, 15, 100),
        np.random.normal(50, 5, 100)
    ])
})

# Using pandas for grouped box plot
df.boxplot(by='Group', column='Value', grid=True)
plt.title("Box Plot by Group")
plt.suptitle("")  # Remove default title
plt.show()
```

**Box Plot with Summary Statistics**:

```python
# Calculate and print summary statistics
for i, d in enumerate(data):
    q1 = np.percentile(d, 25)
    q2 = np.percentile(d, 50)
    q3 = np.percentile(d, 75)
    iqr = q3 - q1
    print(f"Group {chr(65+i)}: Median={q2:.2f}, IQR={iqr:.2f}")
```

---

### Practical Examples

- **Example 1**: Comparing salaries by department.
- **Example 2**: Comparing test scores across schools.
- **Example 3**: Comparing prices across product categories.

---

### Hands-on Coding Exercises

**Exercise 5.13** – Basic box plot:
```python
# 1. Generate 3 datasets from different distributions
# 2. Create a box plot for each
# 3. Add labels
# 4. Display the plot
```

**Exercise 5.14** – Grouped box plot:
```python
# 1. Create a DataFrame with groups and values
# 2. Create a box plot by group
# 3. Customize the plot
# 4. Display the plot
```

---

### Mini Quiz

1. What are the five statistics shown in a box plot?
2. How are outliers defined in a box plot?
3. What is the purpose of `notch=True`?
4. How do you create a horizontal box plot?
5. What is the difference between a box plot and a histogram?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Ignoring outliers – they may be important | Investigate outliers |
| Using box plots for small datasets | Need at least 10-20 data points |
| Not labelling axes | Always label axes |
| Overlapping boxes | Use appropriate spacing or horizontal layout |

---

### Interview Questions

1. **What information does a box plot provide?**  
   *Answer*: A box plot shows the minimum, first quartile, median, third quartile, maximum, and outliers of a distribution.

2. **How do you identify outliers in a box plot?**  
   *Answer*: Outliers are points beyond 1.5 × IQR (Interquartile Range) from Q1 and Q3.

3. **When would you use a box plot instead of a histogram?**  
   *Answer*: Box plots are better for comparing multiple distributions and identifying outliers. Histograms are better for understanding the shape of a single distribution.

---

### Assignment and Mini Project

**Assignment 5.7** – Box plot practice:
```python
# 1. Load or generate a dataset with a categorical column and a numeric column
# 2. Create a box plot by category
# 3. Customize the plot (colours, labels, title)
# 4. Display the plot
```

**Mini Project** – Distribution Comparator:
Create a program that:
1. Generates data for 5 groups with different distributions.
2. Creates box plots for each group.
3. Adds summary statistics (median, IQR) to the plot.
4. Creates horizontal box plots.
5. Adds a violin plot (if seaborn is available) for comparison.

---

### Summary and Revision Notes

- Box plots summarise distributions.
- `plt.boxplot(data)`.
- Shows: min, Q1, median, Q3, max, outliers.
- `notch=True` for notched boxes.
- `vert=False` for horizontal.
- `patch_artist=True` to fill boxes.

---

## Lesson 5.8 – Subplots

### Concept Explanation

**Subplots** allow you to display multiple charts in a single figure. This is useful for comparing different views of the same data or presenting multiple charts together.

**Key functions**:
- `plt.subplots(nrows, ncols)` – create a grid of subplots.
- `plt.subplot(nrows, ncols, index)` – add a subplot (pyplot style).

**Syntax (Object-Oriented)**:
```python
fig, axes = plt.subplots(nrows, ncols)
axes[0, 0].plot(...)
axes[0, 1].bar(...)
```

**Syntax (Pyplot)**:
```python
plt.subplot(2, 2, 1)
plt.plot(...)
plt.subplot(2, 2, 2)
plt.scatter(...)
```

---

### Importance and Real-World Use Cases

- **Why it matters**: Subplots allow you to create dashboards and compare multiple visualisations side by side.

- **Use cases**:
  - A **data analyst** creates a dashboard with multiple charts.
  - A **data scientist** compares model performance metrics.
  - A **financial analyst** shows multiple KPIs.

---

### Step-by-Step Demonstration

```python
import matplotlib.pyplot as plt
import numpy as np

# Method 1: Using subplots (object-oriented)
np.random.seed(42)
fig, axes = plt.subplots(2, 2, figsize=(10, 8))

# Subplot 1: Line chart
x = np.linspace(0, 10, 100)
axes[0, 0].plot(x, np.sin(x), color='blue')
axes[0, 0].set_title('Line Chart')
axes[0, 0].set_xlabel('x')
axes[0, 0].set_ylabel('sin(x)')

# Subplot 2: Bar chart
categories = ['A', 'B', 'C', 'D']
values = [20, 35, 30, 25]
axes[0, 1].bar(categories, values, color='skyblue')
axes[0, 1].set_title('Bar Chart')
axes[0, 1].set_xlabel('Category')
axes[0, 1].set_ylabel('Value')

# Subplot 3: Scatter plot
x_scatter = np.random.randn(100) * 10 + 50
y_scatter = 0.8 * x_scatter + np.random.randn(100) * 10 + 20
axes[1, 0].scatter(x_scatter, y_scatter, alpha=0.6, color='green')
axes[1, 0].set_title('Scatter Plot')
axes[1, 0].set_xlabel('X')
axes[1, 0].set_ylabel('Y')

# Subplot 4: Histogram
data_hist = np.random.normal(50, 10, 1000)
axes[1, 1].hist(data_hist, bins=30, color='purple', edgecolor='black', alpha=0.7)
axes[1, 1].set_title('Histogram')
axes[1, 1].set_xlabel('Value')
axes[1, 1].set_ylabel('Frequency')

plt.tight_layout()
plt.show()

# Method 2: Using subplot (pyplot style)
plt.figure(figsize=(10, 8))

plt.subplot(2, 2, 1)
plt.plot(x, np.cos(x), color='red')
plt.title('cos(x)')

plt.subplot(2, 2, 2)
plt.bar(categories, values, color='lightgreen')
plt.title('Bar Chart')

plt.subplot(2, 2, 3)
plt.hist(data_hist, bins=30, color='orange', edgecolor='black')
plt.title('Histogram')

plt.subplot(2, 2, 4)
plt.scatter(x_scatter, y_scatter, alpha=0.6, color='blue')
plt.title('Scatter Plot')

plt.tight_layout()
plt.show()

# Shared axes
fig, axes = plt.subplots(2, 2, figsize=(10, 8), sharex=True, sharey=True)

axes[0, 0].plot(x, np.sin(x))
axes[0, 1].plot(x, np.cos(x))
axes[1, 0].plot(x, np.sin(2*x))
axes[1, 1].plot(x, np.cos(2*x))

fig.suptitle('Shared Axes Example')
plt.tight_layout()
plt.show()

# Creating a dashboard with different sizes
fig = plt.figure(figsize=(12, 8))

# Large subplot (2x2 grid, spanning 2 columns)
ax1 = plt.subplot2grid((2, 2), (0, 0), colspan=2)
ax1.plot(x, np.sin(x), color='blue')
ax1.set_title('Main Chart')

# Smaller subplots
ax2 = plt.subplot2grid((2, 2), (1, 0))
ax2.bar(categories, values, color='skyblue')
ax2.set_title('Bar Chart')

ax3 = plt.subplot2grid((2, 2), (1, 1))
ax3.scatter(x_scatter, y_scatter, alpha=0.6, color='green')
ax3.set_title('Scatter Plot')

plt.tight_layout()
plt.show()
```

---

### Practical Examples

- **Example 1**: Creating a dashboard with multiple charts.
- **Example 2**: Comparing two datasets side by side.
- **Example 3**: Showing different views of the same data.

---

### Hands-on Coding Exercises

**Exercise 5.15** – Subplots grid:
```python
# 1. Create a 2x2 grid of subplots
# 2. Plot a line chart in the first
# 3. Plot a bar chart in the second
# 4. Plot a scatter plot in the third
# 5. Plot a histogram in the fourth
# 6. Add titles and labels
# 7. Display the plot
```

**Exercise 5.16** – Dashboard layout:
```python
# 1. Create a figure with different subplot sizes
# 2. Make one subplot larger (spanning 2 columns)
# 3. Add smaller subplots below
# 4. Display the plot
```

---

### Mini Quiz

1. What is the purpose of `plt.subplots()`?
2. How do you access a specific subplot in a 2x2 grid?
3. What is the difference between `subplots()` and `subplot()`?
4. How do you create subplots with shared axes?
5. What does `plt.tight_layout()` do?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Too many subplots – cluttered | Limit to 4-6 subplots |
| Not using `tight_layout()` | Always call `tight_layout()` |
| Inconsistent axis ranges | Use `sharex` and `sharey` |
| Small subplot sizes | Use `figsize` to increase figure size |

---

### Interview Questions

1. **How do you create multiple subplots in Matplotlib?**  
   *Answer*: Using `plt.subplots(nrows, ncols)` which returns a figure and an array of axes objects.

2. **What is the purpose of `plt.tight_layout()`?**  
   *Answer*: `tight_layout()` automatically adjusts subplot parameters to fit within the figure area, preventing overlapping labels.

3. **How do you create subplots with different sizes?**  
   *Answer*: Using `plt.subplot2grid()` or `GridSpec`.

---

### Assignment and Mini Project

**Assignment 5.8** – Subplots practice:
```python
# 1. Create a 2x2 grid of subplots
# 2. Each subplot should have a different chart type
# 3. Add titles and labels to each
# 4. Use a figure size of 12x8
# 5. Display the plot
```

**Mini Project** – Dashboard Creator:
Create a program that:
1. Generates a dataset (sales, profit, quantity, etc.).
2. Creates a dashboard with:
   - A line chart (trend over time).
   - A bar chart (sales by product).
   - A pie chart (market share).
   - A scatter plot (sales vs profit).
3. Arranges them in a 2x2 grid.
4. Adds a title to the figure.
5. Displays the dashboard.

---

### Summary and Revision Notes

- Subplots allow multiple charts in one figure.
- `fig, axes = plt.subplots(nrows, ncols)`.
- Access axes with `axes[row, col]`.
- Use `plt.tight_layout()` to avoid overlapping.
- `sharex` and `sharey` for shared axes.

---

## Lesson 5.9 – Figure Customization

### Concept Explanation

Customisation makes your plots professional, readable, and visually appealing. Matplotlib provides extensive customisation options.

**Key customisation areas**:
- **Figure size**: `figsize=(width, height)`.
- **Titles and labels**: `title()`, `xlabel()`, `ylabel()`.
- **Fonts**: `fontsize`, `fontweight`, `fontfamily`.
- **Colors**: Named colors, hex codes, RGB.
- **Grid lines**: `grid()`.
- **Legends**: `legend()` with custom locations.
- **Ticks**: `xticks()`, `yticks()`, `tick_params()`.
- **Spines**: `spines` for axis lines.
- **Text annotations**: `text()` and `annotate()`.
- **Style sheets**: `plt.style.use()`.

---

### Importance and Real-World Use Cases

- **Why it matters**: Customisation makes charts readable, professional, and suitable for presentations or reports.

- **Use cases**:
  - A **data analyst** customises charts for a client report.
  - A **data scientist** creates publication-ready figures.
  - A **financial analyst** prepares charts for a board presentation.

---

### Step-by-Step Demonstration

```python
import matplotlib.pyplot as plt
import numpy as np

# Data
np.random.seed(42)
x = np.linspace(0, 10, 50)
y = np.sin(x) + np.random.normal(0, 0.1, 50)

# Create a figure with custom size
fig, ax = plt.subplots(figsize=(10, 6))

# Main plot
ax.plot(x, y, color='darkblue', linestyle='-', linewidth=2, 
        marker='o', markersize=4, label='Data')

# Title and labels
ax.set_title('Customized Plot', fontsize=20, fontweight='bold', pad=20)
ax.set_xlabel('X-axis', fontsize=14, fontweight='bold')
ax.set_ylabel('Y-axis', fontsize=14, fontweight='bold')

# Legend
ax.legend(loc='best', fontsize=12, framealpha=0.9)

# Grid
ax.grid(True, alpha=0.3, linestyle='--')

# Tick customisation
ax.tick_params(axis='both', labelsize=12, width=2)
ax.set_xticks(np.arange(0, 11, 2))
ax.set_yticks(np.arange(-1.5, 1.5, 0.5))

# Axis limits
ax.set_xlim(0, 10)
ax.set_ylim(-1.5, 1.5)

# Spine customisation
for spine in ax.spines.values():
    spine.set_linewidth(2)
    spine.set_color('black')

# Annotations
ax.annotate('Peak', xy=(1.57, 1), xytext=(3, 1.2),
            arrowprops=dict(facecolor='red', shrink=0.05),
            fontsize=12, fontweight='bold', color='red')

ax.axhline(y=0, color='gray', linestyle='--', linewidth=1, alpha=0.5)

# Background color
fig.patch.set_facecolor('#f8f9fa')
ax.set_facecolor('#ffffff')

plt.tight_layout()
plt.show()

# Using style sheets
plt.style.use('ggplot')
plt.plot(x, y)
plt.title('ggplot Style')
plt.show()

plt.style.use('seaborn-v0_8-darkgrid')
plt.plot(x, y)
plt.title('Seaborn Style')
plt.show()

# Reset to default
plt.style.use('default')

# Saving with high quality
fig.savefig('customized_plot.png', dpi=300, bbox_inches='tight')
```

**Color Palettes**:

```python
# Custom colors
colors = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#96CEB4', '#FFEAA7']
categories = ['A', 'B', 'C', 'D', 'E']
values = [30, 25, 20, 15, 10]

plt.bar(categories, values, color=colors, edgecolor='black', linewidth=1.5)
plt.title('Custom Colors', fontsize=16)
plt.show()
```

---

### Practical Examples

- **Example 1**: Creating a publication-ready line chart.
- **Example 2**: Customising a bar chart for a presentation.
- **Example 3**: Applying a style sheet for consistent design.

---

### Hands-on Coding Exercises

**Exercise 5.17** – Customize a plot:
```python
# 1. Create a figure with size 8x5
# 2. Plot a sine wave
# 3. Add a title with font size 18
# 4. Add axis labels with font size 14
# 5. Add a legend
# 6. Add a grid
# 7. Customize tick labels
# 8. Display the plot
```

**Exercise 5.18** – Style sheets:
```python
# 1. List available style sheets
# 2. Apply three different styles
# 3. Plot the same data with each
# 4. Compare the styles
```

---

### Mini Quiz

1. How do you change the figure size?
2. How do you add grid lines to a plot?
3. What is the purpose of `annotate()`?
4. How do you change the tick label size?
5. What is the purpose of `plt.style.use()`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using default settings – looks unprofessional | Customise for clarity and aesthetics |
| Fonts too small | Use appropriate font sizes |
| Too many colours | Use consistent colour schemes |
| Not using `tight_layout()` | Always call `tight_layout()` |

---

### Interview Questions

1. **How do you customise a plot in Matplotlib?**  
   *Answer*: Using functions like `title()`, `xlabel()`, `ylabel()`, `grid()`, `legend()`, `tick_params()`, and modifying the figure and axes properties.

2. **What are style sheets in Matplotlib?**  
   *Answer*: Style sheets are predefined sets of styling parameters that can be applied with `plt.style.use()`.

3. **How do you save a figure with high quality?**  
   *Answer*: Using `fig.savefig('filename.png', dpi=300, bbox_inches='tight')`.

---

### Assignment and Mini Project

**Assignment 5.9** – Customization practice:
```python
# 1. Create a plot with the following customizations:
#    - Figure size 10x6
#    - Title, xlabel, ylabel with custom fonts
#    - Grid with custom style
#    - Custom colours
#    - Legend with custom location
#    - Annotations
# 2. Save the figure with high quality
```

**Mini Project** – Professional Report Figure:
Create a program that:
1. Generates a dataset (sales, profit, etc.).
2. Creates a professional figure with:
   - Custom size and background.
   - Title, subtitle, and axis labels.
   - Grid and legend.
   - Annotations highlighting key points.
   - Custom colour palette.
   - High-resolution save.
3. Creates a 2x2 dashboard of figures.

---

### Summary and Revision Notes

- Customisation improves readability and professionalism.
- Use `figsize` for figure size.
- Use `title()`, `xlabel()`, `ylabel()` for labels.
- Use `grid()` for grid lines.
- Use `annotate()` for annotations.
- Use `plt.style.use()` for style sheets.
- Save with `savefig()`.

---

## Lesson 5.10 – Saving Charts

### Concept Explanation

Saving charts allows you to use them in presentations, reports, and web pages. Matplotlib provides the `savefig()` function to save plots in various formats.

**Common formats**:
- **PNG**: Standard raster format, good for web and presentations.
- **JPEG**: Lossy compression, smaller file size.
- **PDF**: Vector format, good for printing and scaling.
- **SVG**: Vector format, good for web and editing.
- **EPS**: Vector format for publishing.

**Syntax**:
```python
plt.savefig('filename.png', dpi=300, bbox_inches='tight')
```

**Key parameters**:
- `dpi`: Resolution (dots per inch).
- `bbox_inches`: 'tight' to remove extra whitespace.
- `facecolor`: Background colour.
- `transparent`: Transparent background.

---

### Importance and Real-World Use Cases

- **Why it matters**: Saving charts allows you to share your visualisations in reports, presentations, and on the web.

- **Use cases**:
  - A **data analyst** saves charts for a PowerPoint presentation.
  - A **data scientist** saves figures for a research paper.
  - A **financial analyst** saves charts for a quarterly report.

---

### Step-by-Step Demonstration

```python
import matplotlib.pyplot as plt
import numpy as np

# Create a plot
x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.plot(x, y, color='blue', linewidth=2)
plt.title('Sine Wave')
plt.xlabel('x')
plt.ylabel('sin(x)')
plt.grid(True)

# Save in different formats
# PNG
plt.savefig('sine_wave.png', dpi=300, bbox_inches='tight')
print("Saved as PNG")

# PDF
plt.savefig('sine_wave.pdf', bbox_inches='tight')
print("Saved as PDF")

# SVG
plt.savefig('sine_wave.svg', bbox_inches='tight')
print("Saved as SVG")

# Transparent background
plt.savefig('sine_wave_transparent.png', dpi=300, bbox_inches='tight', transparent=True)
print("Saved as PNG with transparent background")

# High resolution
plt.savefig('sine_wave_high_res.png', dpi=600, bbox_inches='tight')
print("Saved as high-resolution PNG")

plt.show()

# Saving multiple figures
fig1, ax1 = plt.subplots()
ax1.plot(x, np.sin(x))
ax1.set_title('sin(x)')

fig2, ax2 = plt.subplots()
ax2.plot(x, np.cos(x))
ax2.set_title('cos(x)')

fig1.savefig('sin_plot.png', dpi=300, bbox_inches='tight')
fig2.savefig('cos_plot.png', dpi=300, bbox_inches='tight')
print("Saved multiple figures")
```

**Saving with Custom Settings**:

```python
# Create a figure with specific settings
fig = plt.figure(figsize=(10, 6))
plt.plot(x, y, color='darkblue', linewidth=2)
plt.title('Custom Sine Wave', fontsize=16)
plt.xlabel('x', fontsize=14)
plt.ylabel('sin(x)', fontsize=14)
plt.grid(True, alpha=0.3)

# Save with custom metadata (via the figure object)
fig.savefig('custom_sine.png', dpi=300, bbox_inches='tight',
            facecolor='#f8f9fa', edgecolor='none')
print("Saved with custom background")
```

---

### Practical Examples

- **Example 1**: Saving charts for a presentation.
- **Example 2**: Saving high-resolution figures for publication.
- **Example 3**: Saving with transparent background for web embedding.

---

### Hands-on Coding Exercises

**Exercise 5.19** – Saving practice:
```python
# 1. Create a plot
# 2. Save it as PNG
# 3. Save it as PDF
# 4. Save it as SVG
# 5. Save it with high DPI (300)
# 6. Save it with transparent background
```

**Exercise 5.20** – Batch saving:
```python
# 1. Create 3 different plots
# 2. Save each to a different file
# 3. Use a loop to save them
```

---

### Mini Quiz

1. What function is used to save a plot?
2. What does `dpi` control?
3. What is the purpose of `bbox_inches='tight'`?
4. What formats can Matplotlib save to?
5. How do you save a plot with a transparent background?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Saving before `plt.show()` – works but may have issues | Save before `plt.show()` or after |
| Low DPI for publication | Use 300+ DPI for publication |
| Not using `tight_layout()` | Use `bbox_inches='tight'` |
| Overwriting files | Check if files exist before saving |

---

### Interview Questions

1. **How do you save a Matplotlib figure?**  
   *Answer*: Using `plt.savefig('filename.png')` or `fig.savefig('filename.png')`.

2. **What is the difference between saving as PNG and PDF?**  
   *Answer*: PNG is a raster format (pixels), good for web and presentations. PDF is a vector format, good for printing and scaling without quality loss.

3. **What parameters would you use for a high-quality publication figure?**  
   *Answer*: `dpi=300`, `bbox_inches='tight'`, and appropriate `figsize`.

---

### Assignment and Mini Project

**Assignment 5.10** – Saving practice:
```python
# 1. Create a plot with custom styling
# 2. Save it in three formats (PNG, PDF, SVG)
# 3. Save it with high DPI (300)
# 4. Save it with transparent background
# 5. Save it with a custom size
# 6. Verify the files are created
```

**Mini Project** – Report Generator:
Create a program that:
1. Generates a dataset (sales, profit, etc.).
2. Creates a dashboard with multiple charts.
3. Saves the dashboard as a high-resolution PNG.
4. Saves each individual chart as a separate PDF.
5. Creates a summary report with the saved images.

---

### Summary and Revision Notes

- `plt.savefig('filename')` saves the current figure.
- Formats: PNG, PDF, SVG, EPS, JPEG.
- `dpi` controls resolution.
- `bbox_inches='tight'` removes extra whitespace.
- `transparent=True` for transparent background.
- Use `fig.savefig()` for figure-specific saving.

---

## Final Phase 5 Assessment

Now that you have completed all lessons, test your overall understanding.

### Self-Evaluation Checklist

-  I can create line charts with Matplotlib.

-  I can create bar charts (vertical, horizontal, grouped, stacked).

-  I can create pie charts and donut charts.

-  I can create histograms.

-  I can create scatter plots with trend lines.

-  I can create box plots.

-  I can create subplots.

-  I can customise figures.

-  I can save figures.

---

### Answers to Mini Quizzes

**Lesson 5.1**: 1. `plt`. 2. Figure is the whole window; Axes is the plot area. 3. `plt.title()`. 4. `plt.show()`. 5. `plt.legend()`.

**Lesson 5.2**: 1. Showing trends over time. 2. `linestyle='--'`. 3. `marker='o'`. 4. `label`. 5. `plt.fill_between()`.

**Lesson 5.3**: 1. `bar()` is vertical, `barh()` is horizontal. 2. Use `plt.bar(x - width, ...)`. 3. Use `plt.text()`. 4. `width`. 5. Use the `bottom` parameter.

**Lesson 5.4**: 1. For part-to-whole with few categories. 2. Shows percentages. 3. `explode` parameter. 4. Pie chart with a hole. 5. When there are more than 5 categories.

**Lesson 5.5**: 1. To show data distribution. 2. Number of bins. 3. `density=True`. 4. Histogram for continuous data; bar chart for categorical. 5. `plt.axvline()`.

**Lesson 5.6**: 1. To show relationships between two variables. 2. `np.polyfit()` and `plt.plot()`. 3. Point size. 4. Transparency. 5. Use colour mapping.

**Lesson 5.7**: 1. Min, Q1, median, Q3, max. 2. Points beyond 1.5 × IQR. 3. Shows confidence interval. 4. `vert=False`. 5. Histogram shows distribution shape; box plot shows summary statistics.

**Lesson 5.8**: 1. To create multiple subplots. 2. `axes[row, col]`. 3. `subplots()` creates all; `subplot()` adds one. 4. `sharex=True`, `sharey=True`. 5. Adjusts spacing.

**Lesson 5.9**: 1. `figsize=(width, height)`. 2. `plt.grid()`. 3. To add text with an arrow. 4. `tick_params(labelsize=size)`. 5. To apply a style.

**Lesson 5.10**: 1. `plt.savefig()`. 2. Resolution. 3. Removes whitespace. 4. PNG, PDF, SVG, EPS, JPEG. 5. `transparent=True`.

---

**Congratulations!** You have completed Phase 5 of Python for Data Analytics. You now have a solid foundation in data visualisation with Matplotlib. Keep practising!

----




<br/><br/><br/>
<center> <b>Happy Learning! 😊</b> </center>
