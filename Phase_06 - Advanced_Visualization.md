# Phase 6: Advanced Visualization

Welcome to **Phase 6** – where your visualisations become truly stunning and insightful! In Phase 5, you mastered the fundamentals of Matplotlib. Now, we take your visualisation skills to the next level with **Seaborn** – a high-level interface for drawing attractive and informative statistical graphics.

Seaborn is built on top of Matplotlib and integrates closely with Pandas data structures. It makes it incredibly easy to create complex visualisations with just a few lines of code. While Matplotlib gives you complete control, Seaborn gives you **beauty** and **statistical insight** out of the box.

In this phase, you will learn:
- How Seaborn complements Matplotlib and why it's a game-changer.
- **Statistical plots** that automatically aggregate and show confidence intervals.
- **Heatmaps** for visualising correlations and matrices.
- **Pairplots** for exploring relationships across multiple variables.
- **Distribution plots** for understanding the shape of your data.
- **Regression plots** for visualising linear relationships and trends.
- **Categorical plots** for comparing distributions across categories.
- How to create **dashboard-ready** visualisations with custom styles and contexts.

By the end of this phase, you'll be able to create publication-quality, dashboard-ready visualisations that communicate insights with clarity and impact.

---

## Lesson 6.1 – Introduction to Seaborn

### Concept Explanation

**Seaborn** is a Python data visualisation library based on Matplotlib. It provides a high-level interface for drawing attractive and informative statistical graphics.

**Key advantages of Seaborn**:
- **Simpler syntax**: Create complex plots with a single function.
- **Statistical integration**: Automatically computes and visualises statistical relationships (e.g., confidence intervals, aggregations).
- **Beautiful defaults**: Attractive colour palettes and styling out of the box.
- **Pandas integration**: Works seamlessly with DataFrames.
- **Built-in datasets**: Comes with sample datasets for practice.

**Installation**:
```bash
pip install seaborn
```

**Importing**:
```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
```

**Key concepts**:
- **`sns.set_theme()`**: Applies Seaborn's default styling.
- **`sns.set_style()`**: Changes the background grid.
- **`sns.set_context()`**: Adjusts the scale for presentations.
- **`sns.color_palette()`**: Manages colour palettes.

---

### Importance and Real-World Use Cases

- **Why it matters**: Seaborn makes it easy to create complex visualisations that are both statistically accurate and visually appealing, saving hours of manual customisation.

- **Use cases**:
  - A **data scientist** uses Seaborn for exploratory data analysis (EDA).
  - A **data analyst** creates publication-ready charts for reports.
  - A **business analyst** quickly visualises relationships in sales data.

---

### Step-by-Step Demonstration

```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np

# Load built-in dataset
tips = sns.load_dataset('tips')
print("Tips dataset (first 5 rows):\n", tips.head())

# 1. Default Matplotlib plot (for comparison)
plt.figure(figsize=(8, 4))
plt.scatter(tips['total_bill'], tips['tip'])
plt.title('Matplotlib Scatter Plot')
plt.xlabel('Total Bill')
plt.ylabel('Tip')
plt.show()

# 2. Seaborn plot with default styling
sns.set_theme()  # Apply seaborn default styling
plt.figure(figsize=(8, 4))
sns.scatterplot(data=tips, x='total_bill', y='tip')
plt.title('Seaborn Scatter Plot (Default Style)')
plt.show()

# 3. Adding hue (colour by category)
plt.figure(figsize=(8, 4))
sns.scatterplot(data=tips, x='total_bill', y='tip', hue='day', style='time')
plt.title('Scatter Plot with Hue and Style')
plt.show()

# 4. Built-in datasets
print("\nAvailable datasets:", sns.get_dataset_names())

# Load another dataset
iris = sns.load_dataset('iris')
print("\nIris dataset (first 5 rows):\n", iris.head())

# 5. Setting different styles
sns.set_style('whitegrid')
plt.figure(figsize=(8, 4))
sns.barplot(data=tips, x='day', y='total_bill')
plt.title('Bar Plot with Whitegrid Style')
plt.show()

sns.set_style('darkgrid')
plt.figure(figsize=(8, 4))
sns.barplot(data=tips, x='day', y='total_bill')
plt.title('Bar Plot with Darkgrid Style')
plt.show()

# Reset to default
sns.set_theme()
```

**Exploring Palettes**:

```python
# Visualising colour palettes
sns.color_palette('viridis', 8).as_hex()
sns.palplot(sns.color_palette('viridis', 8))
plt.title('Viridis Palette')
plt.show()

sns.palplot(sns.color_palette('coolwarm', 8))
plt.title('Coolwarm Palette')
plt.show()
```

---

### Practical Examples

- **Example 1**: Using Seaborn to quickly explore the 'tips' dataset.
- **Example 2**: Comparing Matplotlib and Seaborn outputs.
- **Example 3**: Setting up a professional style for a dashboard.

---

### Hands-on Coding Exercises

**Exercise 6.1** – Explore Seaborn:
```python
# 1. Load the 'titanic' dataset
# 2. Display the first 5 rows
# 3. Create a scatter plot of age vs fare
# 4. Colour by 'class'
# 5. Use the 'whitegrid' style
# 6. Display the plot
```

**Exercise 6.2** – Style exploration:
```python
# 1. Try all different styles: whitegrid, darkgrid, white, dark, ticks
# 2. For each, create a simple bar plot
# 3. Compare the results
```

---

### Mini Quiz

1. What is Seaborn and how does it relate to Matplotlib?
2. How do you apply Seaborn's default styling?
3. What is the purpose of `sns.set_style()`?
4. How do you load a built-in dataset in Seaborn?
5. What does the `hue` parameter do?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to call `sns.set_theme()` | Always set the theme for consistent styling |
| Not using `plt.show()` | Remember to display the plot |
| Mixing Matplotlib and Seaborn incorrectly | Use Seaborn's functions for data, Matplotlib for customisation |
| Using `sns.plt` (deprecated) | Use `plt` from `matplotlib.pyplot` |

---

### Interview Questions

1. **What is Seaborn and why is it used in data analytics?**  
   *Answer*: Seaborn is a high-level data visualisation library built on Matplotlib. It simplifies the creation of complex statistical graphics, provides beautiful default styles, and integrates seamlessly with Pandas DataFrames.

2. **What is the difference between Matplotlib and Seaborn?**  
   *Answer*: Matplotlib is a low-level library that provides complete control over plots. Seaborn is a high-level library that simplifies the creation of statistical plots with beautiful defaults. Seaborn is built on top of Matplotlib.

3. **How do you apply a specific style in Seaborn?**  
   *Answer*: Using `sns.set_style('style_name')` where style_name can be 'whitegrid', 'darkgrid', 'white', 'dark', or 'ticks'.

---

### Assignment and Mini Project

**Assignment 6.1** – Seaborn exploration:
```python
# 1. Load the 'penguins' dataset
# 2. Display basic information
# 3. Create a scatter plot of bill_length_mm vs bill_depth_mm
# 4. Colour by species
# 5. Use the 'darkgrid' style
# 6. Add a title and axis labels
# 7. Display the plot
```

**Mini Project** – Style Comparison Dashboard:
Create a program that:
1. Loads the 'titanic' dataset.
2. Creates the same plot (e.g., a histogram of age) for all 5 different styles.
3. Arranges them in a 1x5 subplot grid.
4. Displays the comparison.
5. Saves the figure.

---

### Summary and Revision Notes

- Seaborn is built on Matplotlib for statistical visualisation.
- Import with `import seaborn as sns`.
- Apply styling: `sns.set_theme()`.
- Load built-in datasets: `sns.load_dataset('name')`.
- Key parameter: `hue` for colouring by categories.
- Seaborn simplifies complex plots with minimal code.

---

## Lesson 6.2 – Statistical Plots

### Concept Explanation

Statistical plots in Seaborn automatically aggregate data and display statistical summaries, saving you from manual calculations.

**Key functions**:
- **`sns.barplot()`**: Shows the mean (or other aggregate) of a numeric variable for each category with error bars.
- **`sns.countplot()`**: Counts the number of observations in each category.
- **`sns.pointplot()`**: Shows point estimates and confidence intervals, often used for trend analysis.
- **`sns.boxplot()`**: Displays the distribution of a numeric variable across categories (covered in detail later).

**Parameters**:
- `data`: DataFrame.
- `x`, `y`: Variable names.
- `hue`: Group by a categorical variable.
- `estimator`: Aggregate function (default: `mean`).
- `ci`: Confidence interval (default: 95%).
- `errorbar`: Error bar style.

---

### Importance and Real-World Use Cases

- **Why it matters**: Statistical plots provide instant insights into group differences and trends, with built-in uncertainty quantification (confidence intervals).

- **Use cases**:
  - A **marketing analyst** compares average sales across regions.
  - A **financial analyst** shows revenue trends by quarter.
  - A **product manager** compares customer satisfaction scores across product versions.

---

### Step-by-Step Demonstration

```python
import seaborn as sns
import matplotlib.pyplot as plt

# Load dataset
tips = sns.load_dataset('tips')

# Bar plot (mean of total_bill by day)
plt.figure(figsize=(10, 6))

# 1. Bar plot
plt.subplot(2, 2, 1)
sns.barplot(data=tips, x='day', y='total_bill')
plt.title('Average Total Bill by Day')
plt.ylabel('Average Total Bill ($)')

# 2. Bar plot with hue (by time)
plt.subplot(2, 2, 2)
sns.barplot(data=tips, x='day', y='total_bill', hue='time')
plt.title('Average Bill by Day and Time')
plt.ylabel('Average Total Bill ($)')

# 3. Count plot
plt.subplot(2, 2, 3)
sns.countplot(data=tips, x='day')
plt.title('Number of Observations by Day')
plt.ylabel('Count')

# 4. Point plot
plt.subplot(2, 2, 4)
sns.pointplot(data=tips, x='time', y='total_bill', hue='sex')
plt.title('Average Bill by Time and Sex')
plt.ylabel('Average Total Bill ($)')

plt.tight_layout()
plt.show()

# Custom estimator (e.g., median)
plt.figure(figsize=(8, 5))
sns.barplot(data=tips, x='day', y='total_bill', estimator=np.median)
plt.title('Median Total Bill by Day')
plt.ylabel('Median Total Bill ($)')
plt.show()

# Error bar customisation (standard deviation)
plt.figure(figsize=(8, 5))
sns.barplot(data=tips, x='day', y='total_bill', errorbar='sd')
plt.title('Average Bill by Day (with Standard Deviation)')
plt.show()

# Point plot with confidence intervals
plt.figure(figsize=(8, 5))
sns.pointplot(data=tips, x='day', y='total_bill', hue='sex',
              linestyles=['-', '--'], markers=['o', 's'])
plt.title('Point Plot: Average Bill by Day and Sex')
plt.show()

# Using the 'titanic' dataset
titanic = sns.load_dataset('titanic')
plt.figure(figsize=(8, 5))
sns.barplot(data=titanic, x='class', y='fare', hue='sex')
plt.title('Average Fare by Class and Sex')
plt.show()
```

---

### Practical Examples

- **Example 1**: Comparing average sales across product categories.
- **Example 2**: Counting the number of customer complaints by region.
- **Example 3**: Displaying survey responses with confidence intervals.

---

### Hands-on Coding Exercises

**Exercise 6.3** – Bar plots:
```python
# 1. Load the 'tips' dataset
# 2. Create a bar plot of average tip by day
# 3. Create a bar plot of average tip by day, separated by time
# 4. Use the median estimator instead of mean
# 5. Display all plots
```

**Exercise 6.4** – Point plots:
```python
# 1. Load the 'titanic' dataset
# 2. Create a point plot of average age by class
# 3. Create a point plot of average fare by class, separated by sex
# 4. Display the plots
```

---

### Mini Quiz

1. What does `sns.barplot()` show by default?
2. How do you change the aggregation function in a bar plot?
3. What is the purpose of the `errorbar` parameter?
4. What is the difference between `barplot()` and `countplot()`?
5. What does `sns.pointplot()` display?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using bar plots for raw data instead of aggregated | Bar plots are for aggregated summaries |
| Not specifying `estimator` when needed | Use `estimator` for custom aggregations |
| Ignoring confidence intervals | They show the reliability of the estimate |
| Too many categories | Limit categories or use `hue` sparingly |

---

### Interview Questions

1. **What is the difference between `sns.barplot()` and `sns.countplot()`?**  
   *Answer*: `barplot()` shows the aggregated value (e.g., mean) of a numeric variable for each category. `countplot()` counts the number of observations in each category.

2. **What are confidence intervals and why are they shown?**  
   *Answer*: Confidence intervals show the uncertainty around the estimated value. They help assess how reliable the estimate is.

3. **How do you change the estimator in a `barplot()`?**  
   *Answer*: Using the `estimator` parameter: `sns.barplot(..., estimator=np.median)`.

---

### Assignment and Mini Project

**Assignment 6.2** – Statistical plots:
```python
# 1. Load the 'penguins' dataset
# 2. Create a bar plot of average body mass by species
# 3. Create a bar plot of average bill length by species, separated by sex
# 4. Create a count plot of species
# 5. Create a point plot of average bill length by species
# 6. Customise each plot with titles and labels
```

**Mini Project** – Sales Summary Dashboard:
Create a program that:
1. Loads the 'tips' dataset.
2. Creates a dashboard with:
   - A bar plot of average total bill by day.
   - A bar plot of average tip by day.
   - A count plot of day.
   - A point plot showing the relationship between day, time, and total bill.
3. Arranges them in a 2x2 grid.
4. Adds a custom title to the overall figure.

---

### Summary and Revision Notes

- `barplot()`: Aggregated values with error bars.
- `countplot()`: Frequency counts.
- `pointplot()`: Point estimates with confidence intervals.
- `estimator`: Changes the aggregation function.
- `errorbar`: Customises error bars.
- Statistical plots provide built-in uncertainty visualisation.

---

## Lesson 6.3 – Heatmaps

### Concept Explanation

**Heatmaps** are graphical representations of data where values are represented as colours. They are excellent for visualising correlations, confusion matrices, and pivot tables.

**Key uses**:
- **Correlation matrices**: Understanding relationships between variables.
- **Confusion matrices**: Evaluating classification models.
- **Pivot tables**: Visualising multi-dimensional data.

**Syntax**:
```python
sns.heatmap(data, annot, fmt, cmap, cbar, square, linewidths)
```

**Parameters**:
- `data`: 2D dataset (e.g., correlation matrix).
- `annot`: Show values in cells (True/False).
- `fmt`: Format for annotations (e.g., '.2f').
- `cmap`: Colour map (e.g., 'coolwarm', 'viridis').
- `cbar`: Show colour bar.
- `square`: Make cells square.
- `linewidths`: Width of lines between cells.

---

### Importance and Real-World Use Cases

- **Why it matters**: Heatmaps make complex matrices easy to understand at a glance, revealing patterns and correlations that are invisible in raw numbers.

- **Use cases**:
  - A **data scientist** visualises feature correlations.
  - A **financial analyst** shows asset correlations.
  - A **marketing analyst** visualises customer segment overlaps.

---

### Step-by-Step Demonstration

```python
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Load dataset
titanic = sns.load_dataset('titanic')

# 1. Correlation matrix
# Select numeric columns
numeric_cols = ['age', 'fare', 'sibsp', 'parch']
corr_matrix = titanic[numeric_cols].corr()
print("Correlation matrix:\n", corr_matrix)

# Basic heatmap
plt.figure(figsize=(8, 6))
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', fmt='.2f')
plt.title('Correlation Matrix Heatmap')
plt.show()

# Customised heatmap
plt.figure(figsize=(8, 6))
sns.heatmap(corr_matrix, annot=True, cmap='RdBu_r', fmt='.2f',
            linewidths=0.5, square=True, cbar_kws={'shrink': 0.8})
plt.title('Customised Correlation Heatmap')
plt.show()

# 2. Pivot table heatmap
# Pivot: average fare by class and sex
pivot = titanic.pivot_table(values='fare', index='class', columns='sex', aggfunc='mean')
print("\nPivot table:\n", pivot)

plt.figure(figsize=(8, 5))
sns.heatmap(pivot, annot=True, cmap='viridis', fmt='.1f',
            linewidths=1, linecolor='white')
plt.title('Average Fare by Class and Sex')
plt.show()

# 3. Confusion matrix (simulated)
from sklearn.metrics import confusion_matrix

# Simulate actual and predicted values
np.random.seed(42)
y_true = np.random.choice([0, 1, 2], 100, p=[0.5, 0.3, 0.2])
y_pred = y_true.copy()
y_pred[np.random.choice(100, 20, replace=False)] = np.random.choice([0, 1, 2], 20)

cm = confusion_matrix(y_true, y_pred)
plt.figure(figsize=(6, 5))
sns.heatmap(cm, annot=True, fmt='d', cmap='Blues',
            xticklabels=['Class 0', 'Class 1', 'Class 2'],
            yticklabels=['Class 0', 'Class 1', 'Class 2'])
plt.title('Confusion Matrix')
plt.xlabel('Predicted')
plt.ylabel('Actual')
plt.show()

# 4. Heatmap with mask (hide upper triangle)
corr = titanic.corr(numeric_only=True)
mask = np.triu(np.ones_like(corr, dtype=bool))

plt.figure(figsize=(8, 6))
sns.heatmap(corr, mask=mask, annot=True, cmap='coolwarm', fmt='.2f',
            linewidths=0.5)
plt.title('Correlation Matrix (Lower Triangle)')
plt.show()
```

**Identifying High Correlations**:

```python
# Find high correlations
corr = titanic.corr(numeric_only=True)
high_corr = corr[abs(corr) > 0.5]
print("\nHigh correlations (>0.5):\n", high_corr)
```

---

### Practical Examples

- **Example 1**: Analysing feature correlations for a machine learning project.
- **Example 2**: Visualising customer segment size by demographics.
- **Example 3**: Displaying model evaluation (confusion matrix).

---

### Hands-on Coding Exercises

**Exercise 6.5** – Correlation heatmap:
```python
# 1. Load the 'iris' dataset
# 2. Select numeric columns
# 3. Calculate the correlation matrix
# 4. Create a heatmap with annotations
# 5. Use the 'coolwarm' colour map
# 6. Display the plot
```

**Exercise 6.6** – Pivot table heatmap:
```python
# 1. Load the 'titanic' dataset
# 2. Create a pivot table of average fare by class and embarked
# 3. Create a heatmap of the pivot table
# 4. Add annotations
# 5. Display the plot
```

---

### Mini Quiz

1. What is a heatmap used for?
2. What is a correlation matrix?
3. What does the `annot` parameter do?
4. What is the purpose of `np.triu()` in a heatmap?
5. What colour map is commonly used for diverging data?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using heatmaps for non-matrix data | Use heatmaps for 2D matrices |
| Not including annotations | Add annotations for exact values |
| Using inappropriate colour maps | Use diverging maps for correlations, sequential for counts |
| Not masking the upper triangle | Mask to avoid redundancy |

---

### Interview Questions

1. **How do you create a correlation heatmap in Seaborn?**  
   *Answer*: Compute the correlation matrix using `df.corr()`, then plot it with `sns.heatmap()`.

2. **What is the purpose of a colour map in a heatmap?**  
   *Answer*: The colour map encodes the values as colours, making patterns easier to spot.

3. **How do you show the values in the cells of a heatmap?**  
   *Answer*: Using the `annot=True` parameter.

---

### Assignment and Mini Project

**Assignment 6.3** – Heatmap practice:
```python
# 1. Load a dataset with numeric columns
# 2. Calculate the correlation matrix
# 3. Create a heatmap with annotations
# 4. Use a diverging colour map
# 5. Mask the upper triangle
# 6. Add a title
# 7. Display the plot
```

**Mini Project** – Correlation Analyzer:
Create a program that:
1. Loads the 'titanic' dataset.
2. Creates a correlation heatmap for all numeric columns.
3. Identifies the strongest positive and negative correlations.
4. Creates a pivot table heatmap of average fare by class and embarked.
5. Saves both heatmaps as high-resolution images.

---

### Summary and Revision Notes

- Heatmaps visualise 2D data as colours.
- `sns.heatmap()` for creating heatmaps.
- Use `annot=True` to show values.
- Use `cmap` for colour schemes.
- Correlation matrices: `df.corr()`.
- Use `mask` to hide duplicate triangles.
- Pivot tables can be visualised as heatmaps.

---

## Lesson 6.4 – Pairplots

### Concept Explanation

**Pairplots** are a powerful exploratory data analysis (EDA) tool that creates a matrix of scatter plots for every pair of variables in a dataset, with histograms or KDE plots on the diagonal.

**Key uses**:
- Understanding pairwise relationships.
- Identifying patterns, trends, and clusters.
- Detecting outliers.

**Syntax**:
```python
sns.pairplot(data, hue, diag_kind, markers, kind)
```

**Parameters**:
- `data`: DataFrame.
- `hue`: Variable for colouring.
- `diag_kind`: 'hist' (default) or 'kde'.
- `markers`: Marker style.
- `kind`: 'scatter' (default) or 'reg' for regression lines.

---

### Importance and Real-World Use Cases

- **Why it matters**: Pairplots provide a comprehensive overview of all relationships in a dataset in a single figure, making them invaluable for EDA.

- **Use cases**:
  - A **data scientist** explores a new dataset before modelling.
  - A **data analyst** identifies which features are correlated.
  - A **business analyst** discovers segmentation patterns.

---

### Step-by-Step Demonstration

```python
import seaborn as sns
import matplotlib.pyplot as plt

# Load dataset
iris = sns.load_dataset('iris')

# Basic pairplot
sns.pairplot(iris)
plt.suptitle('Pairplot of Iris Dataset', y=1.02)
plt.show()

# Pairplot with hue
sns.pairplot(iris, hue='species')
plt.suptitle('Pairplot Coloured by Species', y=1.02)
plt.show()

# Pairplot with KDE on diagonal
sns.pairplot(iris, hue='species', diag_kind='kde')
plt.suptitle('Pairplot with KDE on Diagonal', y=1.02)
plt.show()

# Pairplot with regression lines
sns.pairplot(iris, hue='species', kind='reg')
plt.suptitle('Pairplot with Regression Lines', y=1.02)
plt.show()

# Customising markers and plot size
sns.pairplot(iris, hue='species', markers=['o', 's', 'D'],
             plot_kws={'alpha': 0.6})
plt.suptitle('Customised Pairplot', y=1.02)
plt.show()

# Pairplot with specific variables
sns.pairplot(iris, hue='species', vars=['sepal_length', 'sepal_width', 'petal_length'])
plt.suptitle('Pairplot with Selected Variables', y=1.02)
plt.show()

# Using the 'penguins' dataset
penguins = sns.load_dataset('penguins')
sns.pairplot(penguins, hue='species')
plt.suptitle('Penguins Pairplot', y=1.02)
plt.show()
```

**Handling Large Datasets**:

```python
# For large datasets, use corner plot or sample
# Pairplot can be slow with many variables

# Sampling for large datasets
# df_sample = df.sample(500)
# sns.pairplot(df_sample, hue='category')
```

---

### Practical Examples

- **Example 1**: Exploring the Iris dataset to see which features separate species.
- **Example 2**: Exploring the Titanic dataset to understand relationships between age, fare, and class.

---

### Hands-on Coding Exercises

**Exercise 6.7** – Basic pairplot:
```python
# 1. Load the 'penguins' dataset
# 2. Create a pairplot
# 3. Colour by species
# 4. Use histograms on the diagonal
# 5. Display the plot
```

**Exercise 6.8** – Customised pairplot:
```python
# 1. Load the 'iris' dataset
# 2. Create a pairplot with KDE on the diagonal
# 3. Use regression lines (kind='reg')
# 4. Select only 3 variables
# 5. Display the plot
```

---

### Mini Quiz

1. What is a pairplot used for?
2. What does the `hue` parameter do?
3. What are the options for `diag_kind`?
4. How do you add regression lines to a pairplot?
5. When might you avoid using a pairplot?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using pairplots on datasets with >10 variables | Use with 3-6 variables |
| Using pairplots on large datasets (>10,000 rows) | Sample the data first |
| Not using `hue` for categorical insight | Always use `hue` to discover patterns |
| Ignoring overplotting | Use `plot_kws={'alpha': 0.5}` |

---

### Interview Questions

1. **What is a pairplot and what does it show?**  
   *Answer*: A pairplot creates a matrix of scatter plots for every pair of variables in a dataset, with distributions on the diagonal. It shows pairwise relationships and is used for EDA.

2. **How do you colour a pairplot by a categorical variable?**  
   *Answer*: Using the `hue` parameter: `sns.pairplot(data, hue='category')`.

3. **What are the limitations of pairplots?**  
   *Answer*: They are slow for large datasets and become cluttered with many variables. They are best used with 3-6 variables.

---

### Assignment and Mini Project

**Assignment 6.4** – Pairplot practice:
```python
# 1. Load the 'penguins' dataset
# 2. Create a pairplot
# 3. Colour by species
# 4. Use KDE on the diagonal
# 5. Use different markers for each species
# 6. Add a title
# 7. Display the plot
```

**Mini Project** – EDA Dashboard:
Create a program that:
1. Loads the 'titanic' dataset.
2. Creates a pairplot of numeric columns (age, fare, sibsp, parch).
3. Colours by 'survived'.
4. Creates a second pairplot of the same variables, coloured by 'class'.
5. Displays both plots side by side (or in separate windows).

---

### Summary and Revision Notes

- Pairplots show pairwise relationships.
- `sns.pairplot(data, hue=...)`.
- `diag_kind`: 'hist' or 'kde'.
- `kind`: 'scatter' or 'reg'.
- Use 3-6 variables.
- Great for EDA and finding patterns.

---

## Lesson 6.5 – Distribution Plots

### Concept Explanation

Distribution plots help understand the shape, spread, and central tendency of a single variable. Seaborn provides several functions for visualising distributions.

**Key functions**:
- **`sns.histplot()`**: Modern histogram with flexible binning and KDE options.
- **`sns.kdeplot()`**: Kernel Density Estimation for smooth distribution curves.
- **`sns.ecdfplot()`**: Empirical Cumulative Distribution Function.
- **`sns.rugplot()`**: Rug plot (small ticks) showing data density.
- **`sns.displot()`**: Figure-level function for distribution plots (combines histplot, kdeplot, ecdfplot).

**Parameters**:
- `data`: DataFrame.
- `x`, `y`: Variable names.
- `bins`: Number of bins or bin edges.
- `kde`: Include KDE.
- `rug`: Include rug plot.
- `hue`: Group by a categorical variable.
- `multiple`: 'layer', 'stack', 'fill', 'dodge'.

---

### Importance and Real-World Use Cases

- **Why it matters**: Understanding data distribution is fundamental to data analysis – it helps identify skewness, outliers, and the appropriate statistical tests.

- **Use cases**:
  - A **data analyst** checks the distribution of customer ages.
  - A **data scientist** verifies assumptions for statistical tests.
  - A **quality analyst** examines defect counts.

---

### Step-by-Step Demonstration

```python
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Load dataset
tips = sns.load_dataset('tips')

# 1. Histogram (histplot)
plt.figure(figsize=(10, 6))

plt.subplot(2, 2, 1)
sns.histplot(data=tips, x='total_bill', bins=20)
plt.title('Histogram of Total Bill')

plt.subplot(2, 2, 2)
sns.histplot(data=tips, x='total_bill', bins=20, kde=True)
plt.title('Histogram with KDE')

plt.subplot(2, 2, 3)
sns.histplot(data=tips, x='total_bill', bins=20, kde=True, rug=True)
plt.title('Histogram with KDE and Rug')

plt.subplot(2, 2, 4)
sns.histplot(data=tips, x='total_bill', hue='time', multiple='stack')
plt.title('Stacked Histogram by Time')

plt.tight_layout()
plt.show()

# 2. KDE plot
plt.figure(figsize=(10, 4))

plt.subplot(1, 2, 1)
sns.kdeplot(data=tips, x='total_bill', fill=True)
plt.title('KDE Plot')
plt.xlabel('Total Bill')

plt.subplot(1, 2, 2)
sns.kdeplot(data=tips, x='total_bill', hue='time', fill=True, alpha=0.5)
plt.title('KDE Plot by Time')

plt.tight_layout()
plt.show()

# 3. ECDF plot
plt.figure(figsize=(8, 5))
sns.ecdfplot(data=tips, x='total_bill')
plt.title('Empirical CDF of Total Bill')
plt.xlabel('Total Bill')
plt.ylabel('Cumulative Proportion')
plt.show()

# 4. displot (figure-level)
sns.displot(data=tips, x='total_bill', kind='hist', bins=20, kde=True)
plt.show()

sns.displot(data=tips, x='total_bill', kind='kde', hue='time', fill=True)
plt.show()

sns.displot(data=tips, x='total_bill', kind='ecdf')
plt.show()

# 5. Distribution plots for multiple variables
iris = sns.load_dataset('iris')
sns.displot(data=iris, x='petal_length', hue='species', kind='kde', fill=True)
plt.show()

# 6. Boxenplot (for large datasets)
np.random.seed(42)
large_data = pd.DataFrame({
    'value': np.concatenate([np.random.normal(0, 1, 1000),
                             np.random.normal(5, 1, 100),
                             np.random.normal(10, 2, 50)]),
    'group': ['A']*1000 + ['B']*100 + ['C']*50
})
plt.figure(figsize=(8, 5))
sns.boxenplot(data=large_data, x='group', y='value')
plt.title('Boxen Plot (for large datasets)')
plt.show()
```

**Comparing Distributions**:

```python
plt.figure(figsize=(10, 5))
sns.histplot(data=tips, x='total_bill', hue='sex', multiple='dodge', bins=15)
plt.title('Distribution of Total Bill by Sex')
plt.show()

plt.figure(figsize=(10, 5))
sns.kdeplot(data=tips, x='total_bill', hue='sex', fill=True, alpha=0.3)
plt.title('KDE of Total Bill by Sex')
plt.show()
```

---

### Practical Examples

- **Example 1**: Checking if sales data is normally distributed.
- **Example 2**: Comparing the age distribution of customers across regions.
- **Example 3**: Visualising the distribution of stock returns.

---

### Hands-on Coding Exercises

**Exercise 6.9** – Distribution plots:
```python
# 1. Load the 'penguins' dataset
# 2. Create a histogram of body_mass_g
# 3. Add KDE to the histogram
# 4. Create a KDE plot of body_mass_g by species
# 5. Create an ECDF plot of body_mass_g
# 6. Display all plots
```

**Exercise 6.10** – displot:
```python
# 1. Load the 'tips' dataset
# 2. Use displot to create a histogram of total_bill
# 3. Use displot to create a KDE plot of total_bill by time
# 4. Use displot to create an ECDF plot of total_bill
# 5. Display all plots
```

---

### Mini Quiz

1. What is the difference between `histplot()` and `kdeplot()`?
2. What is an ECDF plot?
3. What is the purpose of `rug=True`?
4. What is the difference between `multiple='layer'` and `multiple='stack'`?
5. What is `displot()` used for?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using too few or too many bins | Experiment with bin sizes |
| Not using KDE for smooth distributions | Add `kde=True` for a smoothed view |
| Overlapping distributions without transparency | Use `alpha` or `multiple='stack'` |
| Not handling outliers | Use `xlim` to zoom in on the main distribution |

---

### Interview Questions

1. **What is the purpose of a KDE plot?**  
   *Answer*: A KDE plot provides a smooth estimate of the probability density function, making it easier to see the shape of the distribution without the "noise" of binning.

2. **What is the difference between a histogram and an ECDF plot?**  
   *Answer*: A histogram shows the frequency of data in bins. An ECDF shows the cumulative proportion of data up to each value.

3. **What is the advantage of `displot()` over `histplot()`?**  
   *Answer*: `displot()` is a figure-level function that can create multiple subplots for different groups (using `col` and `row` parameters).

---

### Assignment and Mini Project

**Assignment 6.5** – Distribution practice:
```python
# 1. Load the 'penguins' dataset
# 2. Create histograms of bill_length_mm for each species
# 3. Create KDE plots of bill_length_mm for each species
# 4. Create ECDF plots of bill_length_mm for each species
# 5. Use displot to create a faceted view
# 6. Display all plots
```

**Mini Project** – Distribution Analyzer:
Create a program that:
1. Loads the 'titanic' dataset.
2. For the 'age' column, creates:
   - A histogram with KDE.
   - A KDE plot separated by 'survived'.
   - An ECDF plot.
   - A rug plot.
3. For the 'fare' column, creates the same series of plots.
4. Arranges all plots in a 2x3 grid.
5. Saves the combined figure.

---

### Summary and Revision Notes

- `histplot()`: Histogram with KDE options.
- `kdeplot()`: Kernel Density Estimation.
- `ecdfplot()`: Empirical Cumulative Distribution Function.
- `rugplot()`: Small ticks for data density.
- `displot()`: Figure-level distribution plot.
- `multiple`: Controls overlay (layer, stack, fill, dodge).

---

## Lesson 6.6 – Regression Plots

### Concept Explanation

Regression plots visualise the relationship between two variables and fit a regression model to the data. They are excellent for exploring linear and non-linear relationships.

**Key functions**:
- **`sns.regplot()`**: Axes-level function that plots data and a regression model.
- **`sns.lmplot()`**: Figure-level function that can create faceted regression plots.

**Parameters**:
- `data`: DataFrame.
- `x`, `y`: Variable names.
- `order`: Polynomial order for the regression.
- `logistic`: Use logistic regression.
- `lowess`: Use LOWESS (locally weighted) regression.
- `ci`: Confidence interval (default: 95%).
- `scatter_kws`: Additional scatter plot parameters.
- `line_kws`: Additional line parameters.

---

### Importance and Real-World Use Cases

- **Why it matters**: Regression plots help you visualise and communicate relationships between variables, showing the strength and direction of the relationship.

- **Use cases**:
  - A **sales analyst** explores the relationship between advertising spend and sales.
  - A **financial analyst** examines the relationship between interest rates and housing prices.
  - A **data scientist** checks linearity assumptions.

---

### Step-by-Step Demonstration

```python
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Load dataset
tips = sns.load_dataset('tips')

# 1. Basic regplot
plt.figure(figsize=(8, 5))
sns.regplot(data=tips, x='total_bill', y='tip')
plt.title('Regression: Total Bill vs Tip')
plt.show()

# 2. Customised regplot
plt.figure(figsize=(8, 5))
sns.regplot(data=tips, x='total_bill', y='tip',
            scatter_kws={'alpha': 0.5, 'color': 'blue'},
            line_kws={'color': 'red', 'linewidth': 2})
plt.title('Customised Regression Plot')
plt.show()

# 3. Polynomial regression (order=2)
plt.figure(figsize=(8, 5))
sns.regplot(data=tips, x='total_bill', y='tip', order=2)
plt.title('Polynomial Regression (Order 2)')
plt.show()

# 4. Lowess regression (non-parametric)
plt.figure(figsize=(8, 5))
sns.regplot(data=tips, x='total_bill', y='tip', lowess=True)
plt.title('LOWESS Regression (Non-parametric)')
plt.show()

# 5. lmplot (figure-level)
sns.lmplot(data=tips, x='total_bill', y='tip', hue='time', ci=95)
plt.title('lmplot with Hue')
plt.show()

# 6. lmplot with facets
sns.lmplot(data=tips, x='total_bill', y='tip', col='time', row='sex')
plt.show()

# 7. Regression with confidence intervals
plt.figure(figsize=(8, 5))
sns.regplot(data=tips, x='total_bill', y='tip', ci=99)
plt.title('99% Confidence Interval')
plt.show()

# 8. Using log transformation
plt.figure(figsize=(8, 5))
sns.regplot(data=tips, x='total_bill', y='tip', logx=True)
plt.title('Log Transform on X-axis')
plt.show()

# 9. In a pairplot (regression kind)
iris = sns.load_dataset('iris')
sns.pairplot(iris, hue='species', kind='reg')
plt.suptitle('Pairplot with Regression', y=1.02)
plt.show()
```

**Comparing Linear vs Polynomial**:

```python
# Simulated data
np.random.seed(42)
x = np.linspace(0, 10, 100)
y = 0.5 * x**2 + np.random.normal(0, 5, 100)

df = pd.DataFrame({'x': x, 'y': y})

fig, axes = plt.subplots(1, 2, figsize=(12, 5))
sns.regplot(data=df, x='x', y='y', ax=axes[0])
axes[0].set_title('Linear Regression')

sns.regplot(data=df, x='x', y='y', order=2, ax=axes[1])
axes[1].set_title('Polynomial Regression (Order 2)')

plt.tight_layout()
plt.show()
```

---

### Practical Examples

- **Example 1**: Modelling sales as a function of marketing spend.
- **Example 2**: Exploring the relationship between house size and price.
- **Example 3**: Checking linearity assumptions for a regression model.

---

### Hands-on Coding Exercises

**Exercise 6.11** – Regression plots:
```python
# 1. Load the 'tips' dataset
# 2. Create a regplot of total_bill vs tip
# 3. Create a regplot with a polynomial fit (order=2)
# 4. Create an lmplot with hue='time'
# 5. Display all plots
```

**Exercise 6.12** – Advanced regression:
```python
# 1. Load the 'penguins' dataset
# 2. Create a regplot of bill_length_mm vs bill_depth_mm
# 3. Use lowess regression
# 4. Create an lmplot with hue='species'
# 5. Display the plots
```

---

### Mini Quiz

1. What is the difference between `regplot()` and `lmplot()`?
2. What does `order=2` do?
3. What is LOWESS regression?
4. What does `ci` control?
5. How do you add a log transform in a regression plot?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using linear regression for non-linear data | Use `order` for polynomial or `lowess=True` |
| Not checking assumptions | Visualise residuals or use diagnostic plots |
| Over-interpreting correlations | Remember correlation ≠ causation |
| Ignoring outliers | Identify and investigate outliers |

---

### Interview Questions

1. **What is the purpose of a regression plot in Seaborn?**  
   *Answer*: A regression plot visualises the relationship between two variables and fits a regression model to the data, helping to understand trends and make predictions.

2. **What is the difference between `regplot()` and `lmplot()`?**  
   *Answer*: `regplot()` is an axes-level function that plots a regression model on a single axes. `lmplot()` is a figure-level function that can create faceted regression plots for multiple subsets of data.

3. **What is LOWESS regression and when would you use it?**  
   *Answer*: LOWESS (Locally Weighted Scatterplot Smoothing) is a non-parametric regression method that fits local polynomials to the data. It is used when the relationship is non-linear and you don't want to assume a specific functional form.

---

### Assignment and Mini Project

**Assignment 6.6** – Regression practice:
```python
# 1. Load the 'penguins' dataset
# 2. Create a regplot of bill_length_mm vs bill_depth_mm
# 3. Create a polynomial regplot (order=2)
# 4. Create a lowess regplot
# 5. Create an lmplot with hue='species'
# 6. Add titles and display all plots
```

**Mini Project** – Sales Predictor Visualizer:
Create a program that:
1. Generates a simulated dataset with:
   - Advertising spend (x) and sales (y) with a non-linear relationship.
2. Creates regression plots for:
   - Linear regression.
   - Polynomial regression (order=2, 3).
   - LOWESS regression.
3. Compares the fits and determines which model best captures the relationship.
4. Prints a summary of the findings.

---

### Summary and Revision Notes

- `regplot()`: Axes-level regression plot.
- `lmplot()`: Figure-level regression plot with facets.
- `order`: Polynomial order.
- `lowess`: Non-parametric regression.
- `ci`: Confidence interval.
- Use for exploring relationships and checking assumptions.

---

## Lesson 6.7 – Categorical Plots

### Concept Explanation

Categorical plots visualise the distribution of a numeric variable across different categories. Seaborn provides several powerful functions for this.

**Key functions**:
- **`sns.boxplot()`**: Standard box-and-whisker plots (quartiles and outliers).
- **`sns.violinplot()`**: Combines box plot with KDE (violin shape).
- **`sns.swarmplot()`**: Shows individual data points without overlap (good for small datasets).
- **`sns.stripplot()`**: Shows individual data points with some jitter.
- **`sns.boxenplot()`**: Similar to box plot but optimised for larger datasets.
- **`sns.pointplot()`**: Shows point estimates and confidence intervals.
- **`sns.countplot()`**: Counts observations per category.

**Parameters**:
- `data`: DataFrame.
- `x`, `y`: Variable names.
- `hue`: Group by another categorical variable.
- `split`: Split violin/box plots by hue.
- `dodge`: Separate plots for different hues.

---

### Importance and Real-World Use Cases

- **Why it matters**: Categorical plots make it easy to compare distributions, identify outliers, and spot differences across groups.

- **Use cases**:
  - A **data analyst** compares salaries across departments.
  - A **marketing analyst** compares campaign performance across channels.
  - A **product manager** compares satisfaction scores across versions.

---

### Step-by-Step Demonstration

```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np

# Load dataset
tips = sns.load_dataset('tips')

# 1. Box plot
plt.figure(figsize=(10, 6))

plt.subplot(2, 3, 1)
sns.boxplot(data=tips, x='day', y='total_bill')
plt.title('Box Plot')

plt.subplot(2, 3, 2)
sns.boxplot(data=tips, x='day', y='total_bill', hue='time')
plt.title('Box Plot with Hue')

plt.subplot(2, 3, 3)
sns.boxplot(data=tips, x='day', y='total_bill', hue='time', dodge=True)
plt.title('Box Plot with Dodge')

# 2. Violin plot
plt.subplot(2, 3, 4)
sns.violinplot(data=tips, x='day', y='total_bill')
plt.title('Violin Plot')

plt.subplot(2, 3, 5)
sns.violinplot(data=tips, x='day', y='total_bill', hue='time', split=True)
plt.title('Violin Plot (Split)')

# 3. Swarm plot (avoid overlapping points)
plt.subplot(2, 3, 6)
sns.swarmplot(data=tips, x='day', y='total_bill', hue='time', dodge=True, size=3)
plt.title('Swarm Plot')

plt.tight_layout()
plt.show()

# 4. Stripplot vs Swarmplot
fig, axes = plt.subplots(1, 2, figsize=(12, 5))

sns.stripplot(data=tips, x='day', y='total_bill', ax=axes[0])
axes[0].set_title('Stripplot (with jitter)')

sns.swarmplot(data=tips, x='day', y='total_bill', ax=axes[1])
axes[1].set_title('Swarmplot (no overlap)')

plt.tight_layout()
plt.show()

# 5. Boxenplot (for large datasets)
np.random.seed(42)
large_data = pd.DataFrame({
    'value': np.concatenate([np.random.normal(0, 1, 1000),
                             np.random.normal(5, 1, 1000),
                             np.random.normal(10, 2, 1000)]),
    'group': ['A']*1000 + ['B']*1000 + ['C']*1000
})

plt.figure(figsize=(8, 5))
sns.boxenplot(data=large_data, x='group', y='value')
plt.title('Boxenplot (for large datasets)')
plt.show()

# 6. Violinplot with inner box
plt.figure(figsize=(8, 5))
sns.violinplot(data=tips, x='day', y='total_bill', inner='box')
plt.title('Violin Plot with Inner Box Plot')
plt.show()

# 7. Categorical plot with catplot (figure-level)
sns.catplot(data=tips, x='day', y='total_bill', kind='box', hue='time', col='sex')
plt.show()

sns.catplot(data=tips, x='day', y='total_bill', kind='violin', hue='time', col='sex')
plt.show()
```

**Comparing Multiple Plot Types**:

```python
fig, axes = plt.subplots(2, 2, figsize=(12, 10))

sns.boxplot(data=tips, x='day', y='total_bill', ax=axes[0, 0])
axes[0, 0].set_title('Boxplot')

sns.violinplot(data=tips, x='day', y='total_bill', ax=axes[0, 1])
axes[0, 1].set_title('Violinplot')

sns.swarmplot(data=tips, x='day', y='total_bill', ax=axes[1, 0])
axes[1, 0].set_title('Swarmplot')

sns.pointplot(data=tips, x='day', y='total_bill', ax=axes[1, 1])
axes[1, 1].set_title('Pointplot')

plt.tight_layout()
plt.show()
```

---

### Practical Examples

- **Example 1**: Comparing customer spend across age groups.
- **Example 2**: Analysing employee salaries by department.
- **Example 3**: Visualising test scores by class.

---

### Hands-on Coding Exercises

**Exercise 6.13** – Categorical plots:
```python
# 1. Load the 'penguins' dataset
# 2. Create a boxplot of body_mass_g by species
# 3. Create a violinplot of body_mass_g by species
# 4. Create a swarmplot of body_mass_g by species
# 5. Display all plots
```

**Exercise 6.14** – catplot:
```python
# 1. Load the 'tips' dataset
# 2. Use catplot to create boxplots of total_bill by day, faceted by time
# 3. Use catplot to create violinplots of total_bill by day, faceted by sex
# 4. Display the plots
```

---

### Mini Quiz

1. What is the difference between a boxplot and a violinplot?
2. When would you use a swarmplot instead of a stripplot?
3. What is the purpose of `split=True` in a violinplot?
4. What is `boxenplot` used for?
5. What is `catplot` used for?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using swarmplot for large datasets (slow) | Use boxplot or violinplot |
| Not using `dodge` when hue is present | Use `dodge=True` to separate groups |
| Overlapping categories | Use `split` or `dodge` to separate |
| Ignoring outliers in boxplots | Investigate outliers |

---

### Interview Questions

1. **What is the difference between a boxplot and a violinplot?**  
   *Answer*: A boxplot shows quartiles, median, and outliers. A violinplot combines a boxplot with a KDE, showing the full distribution shape, making it better for multimodal distributions.

2. **When would you use a swarmplot?**  
   *Answer*: A swarmplot is used for small datasets (up to a few hundred points) to show individual data points without overlap, providing more detail than a boxplot.

3. **What is the purpose of `catplot`?**  
   *Answer*: `catplot` is a figure-level function that can create various categorical plots (box, violin, swarm, etc.) and facet them by additional variables.

---

### Assignment and Mini Project

**Assignment 6.7** – Categorical practice:
```python
# 1. Load the 'penguins' dataset
# 2. Create a boxplot of bill_length_mm by species
# 3. Create a violinplot of bill_length_mm by species
# 4. Create a swarmplot of bill_length_mm by species, coloured by sex
# 5. Use catplot to create boxplots of bill_length_mm by species, faceted by sex
# 6. Display all plots
```

**Mini Project** – Group Comparison Dashboard:
Create a program that:
1. Loads the 'titanic' dataset.
2. Creates a dashboard comparing 'age' across 'class' and 'survived'.
3. Includes:
   - A boxplot.
   - A violinplot.
   - A swarmplot (sample the data to 100 points).
   - A pointplot.
4. Arranges them in a 2x2 grid.
5. Adds titles and labels.

---

### Summary and Revision Notes

- Categorical plots compare distributions across groups.
- `boxplot()`: Quartiles and outliers.
- `violinplot()`: KDE + boxplot.
- `swarmplot()`: Individual points (small datasets).
- `boxenplot()`: Large datasets.
- `catplot()`: Figure-level categorical plots.

---

## Lesson 6.8 – Dashboard-Ready Visualizations

### Concept Explanation

Creating individual charts is one thing; creating a cohesive, professional dashboard is another. This lesson covers how to combine Seaborn with Matplotlib to create polished, dashboard-ready visualisations.

**Key techniques**:
- **Theme customisation**: `sns.set_style()`, `sns.set_context()`.
- **Context settings**: 'paper', 'notebook', 'talk', 'poster'.
- **Figure composition**: Using `subplots`, `gridspec`, and `figure-level` functions.
- **Consistent styling**: Applying the same palette and styling across multiple plots.
- **Saving**: High-resolution output for presentations and reports.

**Context settings**:
- `paper`: Small, suitable for academic papers.
- `notebook`: Default, suitable for Jupyter notebooks.
- `talk`: Larger, suitable for presentations.
- `poster`: Largest, suitable for posters.

---

### Importance and Real-World Use Cases

- **Why it matters**: A dashboard is more than the sum of its parts. Consistent styling and thoughtful composition create a professional experience that builds trust and communicates effectively.

- **Use cases**:
  - A **data analyst** creates a weekly sales dashboard for the management team.
  - A **data scientist** prepares a model evaluation dashboard.
  - A **business analyst** presents a quarterly performance dashboard.

---

### Step-by-Step Demonstration

```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np

# Load data
tips = sns.load_dataset('tips')
penguins = sns.load_dataset('penguins')
iris = sns.load_dataset('iris')

# 1. Setting context for presentations
sns.set_theme()  # Reset to defaults

# For a presentation (larger text)
sns.set_context('talk')
plt.figure(figsize=(12, 6))
sns.barplot(data=tips, x='day', y='total_bill')
plt.title('Average Total Bill by Day (Talk Context)')
plt.show()

# For a poster (even larger)
sns.set_context('poster')
plt.figure(figsize=(14, 7))
sns.barplot(data=tips, x='day', y='total_bill')
plt.title('Average Total Bill by Day (Poster Context)')
plt.show()

# Reset to notebook context
sns.set_context('notebook')

# 2. Creating a professional dashboard with subplots
sns.set_style('whitegrid')
sns.set_palette('Set2')

fig, axes = plt.subplots(2, 3, figsize=(15, 10))
fig.suptitle('Tips Dataset Dashboard', fontsize=20, fontweight='bold')

# Plot 1: Bar plot
sns.barplot(data=tips, x='day', y='total_bill', ax=axes[0, 0], errorbar='sd')
axes[0, 0].set_title('Average Bill by Day')
axes[0, 0].set_ylabel('Total Bill ($)')

# Plot 2: Box plot
sns.boxplot(data=tips, x='day', y='total_bill', ax=axes[0, 1])
axes[0, 1].set_title('Distribution of Bills by Day')
axes[0, 1].set_ylabel('Total Bill ($)')

# Plot 3: Count plot
sns.countplot(data=tips, x='day', ax=axes[0, 2])
axes[0, 2].set_title('Number of Transactions by Day')
axes[0, 2].set_ylabel('Count')

# Plot 4: Scatter plot
sns.scatterplot(data=tips, x='total_bill', y='tip', hue='time', ax=axes[1, 0])
axes[1, 0].set_title('Tip vs Total Bill')
axes[1, 0].set_xlabel('Total Bill ($)')
axes[1, 0].set_ylabel('Tip ($)')

# Plot 5: Histogram
sns.histplot(data=tips, x='total_bill', kde=True, ax=axes[1, 1])
axes[1, 1].set_title('Distribution of Bills')
axes[1, 1].set_xlabel('Total Bill ($)')

# Plot 6: Point plot
sns.pointplot(data=tips, x='day', y='total_bill', hue='time', ax=axes[1, 2])
axes[1, 2].set_title('Average Bill by Day and Time')
axes[1, 2].set_xlabel('Day')
axes[1, 2].set_ylabel('Total Bill ($)')

plt.tight_layout()
plt.show()

# 3. Using a consistent colour palette
sns.set_palette('viridis')
fig, axes = plt.subplots(1, 3, figsize=(15, 4))

sns.barplot(data=tips, x='day', y='total_bill', ax=axes[0])
axes[0].set_title('Viridis Palette')

sns.set_palette('coolwarm')
sns.barplot(data=tips, x='day', y='total_bill', ax=axes[1])
axes[1].set_title('Coolwarm Palette')

sns.set_palette('Blues_r')
sns.barplot(data=tips, x='day', y='total_bill', ax=axes[2])
axes[2].set_title('Blues_r Palette')

plt.tight_layout()
plt.show()

# 4. Saving a dashboard-ready figure
fig.savefig('dashboard.png', dpi=300, bbox_inches='tight', facecolor='white')
print("Dashboard saved!")

# 5. Using dark style for command-centre look
sns.set_style('darkgrid')
sns.set_palette('RdBu_r')

plt.figure(figsize=(12, 6))
sns.scatterplot(data=tips, x='total_bill', y='tip', hue='day', size='size')
plt.title('Scatter Plot with Dark Style')
plt.show()

# 6. Customising with Matplotlib and Seaborn
sns.set_style('whitegrid')
sns.set_context('talk')

fig, ax = plt.subplots(figsize=(10, 6))
sns.barplot(data=tips, x='day', y='total_bill', hue='time', ax=ax)
ax.set_title('Customised Dashboard Plot', fontsize=18)
ax.set_xlabel('Day', fontsize=14)
ax.set_ylabel('Average Total Bill ($)', fontsize=14)
ax.legend(title='Time', fontsize=12)
ax.grid(axis='y', alpha=0.3)

# Adding a horizontal line
ax.axhline(y=tips['total_bill'].mean(), color='red', linestyle='--',
           label=f'Overall Mean: ${tips["total_bill"].mean():.2f}')
ax.legend()

plt.tight_layout()
plt.show()

# Reset to defaults
sns.set_theme()
```

**Creating a Custom Theme**:

```python
# Create a custom style dictionary
custom_style = {
    'axes.facecolor': '#f0f0f0',
    'axes.edgecolor': 'black',
    'axes.grid': True,
    'grid.color': 'white',
    'grid.linestyle': '-',
    'grid.linewidth': 0.8,
    'figure.facecolor': 'white'
}

sns.set_style(custom_style)
plt.figure(figsize=(8, 4))
sns.barplot(data=tips, x='day', y='total_bill')
plt.title('Custom Style')
plt.show()

# Reset
sns.set_theme()
```

---

### Practical Examples

- **Example 1**: Creating a sales performance dashboard.
- **Example 2**: Preparing a model evaluation dashboard for a client.
- **Example 3**: Designing a daily operational dashboard.

---

### Hands-on Coding Exercises

**Exercise 6.15** – Dashboard creation:
```python
# 1. Load the 'penguins' dataset
# 2. Create a 2x3 dashboard with:
#    - Boxplot of body_mass by species
#    - Violinplot of bill_length by species
#    - Countplot of species
#    - Scatterplot of bill_length vs bill_depth, coloured by species
#    - Histogram of body_mass
#    - Barplot of average bill_length by species
# 3. Use 'whitegrid' style
# 4. Use 'talk' context
# 5. Save the dashboard
```

**Exercise 6.16** – Style customisation:
```python
# 1. Create a plot using 'whitegrid'
# 2. Create the same plot using 'darkgrid'
# 3. Create the same plot using 'ticks'
# 4. Compare the styles
```

---

### Mini Quiz

1. What is the purpose of `sns.set_context()`?
2. What are the four context options?
3. How do you create a custom style in Seaborn?
4. How do you save a figure at high resolution?
5. How do you set a consistent colour palette?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Inconsistent styles across plots | Use `sns.set_style()` and `sns.set_context()` at the top |
| Too much information in one dashboard | Limit to 4-6 key plots |
| Small fonts | Use `talk` or `poster` context for presentations |
| Not saving high-resolution | Use `dpi=300` for saving |

---

### Interview Questions

1. **How do you make a dashboard-ready visualisation in Seaborn?**  
   *Answer*: By setting a consistent style and context (`sns.set_style()`, `sns.set_context()`), using a consistent colour palette, creating multiple subplots, and saving the figure at high resolution.

2. **What is the difference between the 'notebook', 'talk', and 'poster' contexts?**  
   *Answer*: They control the scaling of fonts and plot elements. 'notebook' is default for Jupyter, 'talk' is larger for presentations, 'poster' is largest for posters.

3. **How do you ensure consistent colours across multiple plots?**  
   *Answer*: Using `sns.set_palette()` at the beginning of the notebook or script.

---

### Assignment and Mini Project

**Assignment 6.8** – Dashboard creation:
```python
# 1. Load the 'titanic' dataset
# 2. Create a 2x3 dashboard with:
#    - Boxplot of age by class
#    - Violinplot of fare by class
#    - Countplot of survived
#    - Scatterplot of age vs fare, coloured by survived
#    - Histogram of age
#    - Barplot of average fare by class and sex
# 3. Use 'whitegrid' style and 'talk' context
# 4. Add a title to the overall figure
# 5. Save as 'titanic_dashboard.png' with 300 DPI
```

**Mini Project** – Full Business Dashboard:
Create a program that:
1. Uses a real-world dataset (or generates one) with at least 6 variables.
2. Creates a comprehensive dashboard with:
   - 6-8 visualisations covering:
     - Distribution of key variables.
     - Relationships between variables.
     - Comparisons across categories.
     - Trends (if time-series data available).
3. Uses a consistent colour palette and style.
4. Adds appropriate titles, labels, and annotations.
5. Saves the dashboard at high resolution.
6. Produces a one-page summary of the insights from the dashboard.

---

### Summary and Revision Notes

- `sns.set_style()`: Sets the background style.
- `sns.set_context()`: Sets the scaling for different use cases.
- `sns.set_palette()`: Sets the colour palette.
- Combine Seaborn plots with Matplotlib subplots for dashboards.
- Use `fig.suptitle()` for a main title.
- Save with `fig.savefig()` and `dpi=300`.
- Consistency is key for professional dashboards.

---

## Final Phase 6 Assessment

Now that you have completed all lessons, test your overall understanding.

### Self-Evaluation Checklist

-  I can use Seaborn to create statistical plots.

-  I can create heatmaps for correlation matrices.

-  I can use pairplots for EDA.

-  I can create distribution plots (histograms, KDE, ECDF).

-  I can create regression plots.

-  I can use categorical plots (box, violin, swarm).

-  I can create dashboard-ready visualisations.

---

### Answers to Mini Quizzes

**Lesson 6.1**: 1. Seaborn is a high-level visualisation library built on Matplotlib. 2. `sns.set_theme()`. 3. To change the background style. 4. `sns.load_dataset('name')`. 5. Colours points by a categorical variable.

**Lesson 6.2**: 1. The mean with a confidence interval. 2. `estimator=np.median`. 3. Shows error bars. 4. `barplot` shows aggregated values, `countplot` shows counts. 5. Point estimates with confidence intervals.

**Lesson 6.3**: 1. Visualising 2D data as colours. 2. A table showing correlations between variables. 3. Shows values in cells. 4. Masks the upper triangle. 5. `coolwarm` or `RdBu_r`.

**Lesson 6.4**: 1. Exploring pairwise relationships. 2. Colours by a category. 3. 'hist' or 'kde'. 4. `kind='reg'`. 5. When there are >10 variables or >10,000 rows.

**Lesson 6.5**: 1. `histplot` uses bins; `kdeplot` uses a smooth kernel. 2. Shows cumulative distribution. 3. Adds small ticks for data density. 4. `layer` overlays, `stack` stacks. 5. Figure-level distribution plot.

**Lesson 6.6**: 1. `regplot` is axes-level; `lmplot` is figure-level with facets. 2. Polynomial regression of order 2. 3. Non-parametric local regression. 4. Confidence interval. 5. `logx=True`.

**Lesson 6.7**: 1. Violinplot adds KDE to boxplot. 2. For small datasets where you want to see individual points. 3. Splits the violin by hue. 4. Large datasets. 5. Figure-level categorical plots.

**Lesson 6.8**: 1. To scale elements for different contexts. 2. 'paper', 'notebook', 'talk', 'poster'. 3. Using a dictionary in `sns.set_style()`. 4. `dpi=300`. 5. `sns.set_palette()`.

---

**Congratulations!** You have completed Phase 6 of Python for Data Analytics. You now have advanced visualisation skills that allow you to create professional, statistically-informed, dashboard-ready visualisations. Keep practising!


----




<br/><br/><br/>
<center> <b>Happy Learning! 😊</b> </center>
