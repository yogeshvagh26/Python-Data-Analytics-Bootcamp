# Phase 1: Python Fundamentals for Data Analytics

Welcome to **Python for Data Analytics**! You're about to embark on an exciting journey into one of the most powerful and versatile programming languages in the world. Python has become the **#1 language for data analytics, machine learning, and artificial intelligence** – and for good reason.

Python is:

- **Beginner-friendly** – with clean, readable syntax that reads like plain English.

- **Powerful** – with thousands of libraries for data manipulation, analysis, and visualisation.

- **In-demand** – Python skills are among the most sought-after in the job market.


In this phase, we'll start from the absolute basics – installing Python and writing your first line of code – and gradually build up to a solid foundation. Every concept is explained in simple language, tied to real-world data analytics scenarios, and reinforced with hands-on coding exercises.

Let's begin your Python journey!

---

## Lesson 1.1 – Introduction to Python

### Concept Explanation

**Python** is a high-level, interpreted, general-purpose programming language created by Guido van Rossum in 1991. It is designed to be easy to read and write, with a focus on code readability and simplicity.

**Why Python for Data Analytics?**

| **Feature** | **Why It Matters** |
|-------------|-------------------|
| **Readable Syntax** | Code is easy to understand, even for non-programmers |
| **Extensive Libraries** | Pandas, NumPy, Matplotlib, Scikit-learn – everything you need for data work |
| **Large Community** | Countless tutorials, documentation, and support |
| **Cross-Platform** | Runs on Windows, Mac, Linux |
| **Integration** | Works with databases, web APIs, and other tools |
| **Industry Standard** | Used by Google, NASA, Netflix, and thousands of other organisations |

**Key Characteristics**:

- **Interpreted**: Code runs line by line (no compilation step).

- **Dynamically Typed**: You don't need to declare variable types.

- **Object-Oriented**: Supports classes and objects.

- **Open Source**: Free to use and distribute.

---

### Importance and Real-World Use Cases

- **Why it matters**: Python is the language of data science. Whether you're cleaning data, building dashboards, or training machine learning models, Python is the tool you'll use.

- **Use cases in Data Analytics**:

  - **Data Cleaning**: Using pandas to handle missing values, remove duplicates, and transform data.

  - **Data Analysis**: Aggregating, grouping, and summarising data with pandas.

  - **Data Visualization**: Creating charts and graphs with Matplotlib, Seaborn, or Plotly.

  - **ETL Pipelines**: Extracting data from APIs, transforming it, and loading it to a database.

  - **Machine Learning**: Building predictive models with Scikit-learn, TensorFlow, or PyTorch.

  - **Reporting**: Automating report generation with Python scripts.

---

### Practical Examples

- **Example 1**: A data analyst uses Python to read a CSV file, clean the data, and generate a summary report automatically every morning.

- **Example 2**: A marketing analyst uses Python to pull data from an API, analyse campaign performance, and create visualisations for the team.

- **Example 3**: A financial analyst uses Python to automate the consolidation of monthly financial reports from multiple Excel files.


---

### Hands-on Coding Exercises

**Exercise 1.1** – Write and run your first Python program:
```python
print("Hello, World!")
print("Welcome to Python for Data Analytics!")
```

**Exercise 1.2** – Experiment with Python as a calculator:
```python
print(10 + 5)
print(10 - 5)
print(10 * 5)
print(10 / 5)
print(10 ** 2)  # exponentiation
```

**Exercise 1.3** – Create a simple program that prints your name, age, and favourite colour.

---

### Mini Quiz

1. Who created Python and in what year?
2. What does it mean that Python is "interpreted"?
3. What is Python's primary advantage for data analytics?
4. Name three Python libraries used in data analytics.
5. Is Python free to use?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not practising consistently | Code every day, even if just for 15 minutes |
| Skipping the fundamentals | Master the basics before moving to advanced topics |
| Copy-pasting without understanding | Always type out code yourself to learn |
| Using inconsistent naming conventions | Follow PEP 8 style guide |

---

### Interview Questions

1. **What is Python and why is it popular in data analytics?**  
   *Answer*: Python is a high-level, interpreted programming language known for its readability and versatility. It is popular in data analytics because of its extensive libraries (pandas, NumPy, Matplotlib), large community, and ease of use.

2. **What are the key features of Python?**  
   *Answer*: Readable syntax, dynamically typed, interpreted, object-oriented, open source, extensive standard library, and cross-platform.

3. **What is the difference between Python and R for data analytics?**  
   *Answer*: Both are popular for data analytics. Python is more general-purpose and has better integration with production systems. R is more specialised for statistical analysis and has a steeper learning curve. Python is often preferred for end-to-end data science workflows.

---

### Assignment and Mini Project

**Assignment 1.1** – Write a Python script that:
1. Prints your name.
2. Prints your age.
3. Prints "I am learning Python for data analytics!"
4. Performs and prints the result of: (25 + 10) * 3 / 2

**Mini Project** – Create a simple "About Me" program:
- Ask the user for their name, age, and city.
- Print a message like: "Hello [Name]! You are [Age] years old and you live in [City]. Welcome to Python!"

---

### Summary and Revision Notes

- Python is a high-level, interpreted, dynamically typed programming language.
- Created by Guido van Rossum in 1991.
- Python is the #1 language for data analytics, machine learning, and AI.
- Key libraries for data: pandas, NumPy, Matplotlib, Scikit-learn.
- Python is free, open source, and cross-platform.
- Code readability is a core design philosophy.

---

## Lesson 1.2 – Installing Python and VS Code

### Concept Explanation

Before you can write Python code, you need to install Python and a code editor. This lesson covers:
- Installing Python (the interpreter).
- Installing Visual Studio Code (VS Code) – a popular, free, and powerful code editor.
- Setting up Python in VS Code.

**What is an Interpreter?**
- The Python interpreter is the program that reads and executes your Python code.
- You write code in a `.py` file, and the interpreter runs it.

**What is a Code Editor?**
- A tool for writing, editing, and managing your code.
- VS Code is lightweight, free, and has excellent Python support (with extensions).

**Alternative Editors**:
- **PyCharm**: Full-featured IDE for Python (free Community edition).
- **Jupyter Notebook**: Great for data exploration and visualisation.
- **Spyder**: Popular in data science (part of Anaconda).

---

### Importance and Real-World Use Cases

- **Why it matters**: A proper setup ensures you can write, run, and debug Python code efficiently. In a professional setting, having the right tools increases productivity and reduces frustration.

- **Use cases**:
  - A **data analyst** uses VS Code with Python extensions to write data processing scripts.
  - A **data scientist** uses Jupyter Notebook for interactive data exploration and prototyping.
  - A **developer** uses PyCharm for large-scale Python projects.

---

### Step-by-Step Demonstration

**Step 1: Install Python**

1. Go to `python.org/downloads`.
2. Click the latest version for your operating system.
3. **IMPORTANT**: Check the box **"Add Python to PATH"** during installation.
4. Click **Install Now**.
5. Verify installation: Open **Command Prompt (Windows)** or **Terminal (Mac/Linux)** and type:
   ```bash
   python --version
   ```
   Or on some systems:
   ```bash
   python3 --version
   ```
   You should see something like: `Python 3.12.0`

**Step 2: Install Visual Studio Code**

1. Go to `code.visualstudio.com/download`.
2. Download the installer for your operating system.
3. Run the installer and follow the prompts.
4. Open VS Code.

**Step 3: Install Python Extension in VS Code**

1. Open VS Code.
2. Click the **Extensions** icon (left sidebar, looks like four squares).
3. Search for **Python** (by Microsoft).
4. Click **Install**.
5. Once installed, VS Code will automatically detect your Python installation.

**Step 4: Write and Run Your First Python Program in VS Code**

1. Open VS Code.
2. Click **File** → **New File**.
3. Save the file with a `.py` extension: `first_program.py`.
4. Type: `print("Hello, VS Code!")`.
5. Click the **Run** button (triangle) in the top-right corner, or press `Ctrl+Shift+Enter` (Windows) / `Cmd+Shift+Enter` (Mac).
6. The output appears in the terminal at the bottom.

**Step 5: Using the Terminal in VS Code**

1. Open VS Code.
2. Click **Terminal** → **New Terminal**.
3. Type `python` and press Enter – this opens the Python interactive shell.
4. Try typing: `print("Hello from the terminal!")`.
5. Type `exit()` to leave the Python shell.

---

### Practical Examples

- **Example 1**: You're setting up a new laptop for data analysis. You install Python and VS Code, then install the pandas library to start working with data.
- **Example 2**: You're collaborating on a project. Your team uses VS Code, so you set up the same environment to ensure consistency.

---

### Hands-on Coding Exercises

**Exercise 1.4** – Verify your Python installation:
1. Open Terminal/Command Prompt.
2. Type: `python --version` and note the version.
3. Type: `python` to open the interactive shell.
4. Type: `print("Python is working!")`.
5. Type: `exit()` to close the shell.

**Exercise 1.5** – Set up VS Code:
1. Open VS Code.
2. Create a new file and save it as `test.py`.
3. Type: `print("VS Code is set up correctly!")`.
4. Run the file using the Run button.

---

### Mini Quiz

1. What is the official website for downloading Python?
2. What is the purpose of the "Add Python to PATH" option?
3. What is VS Code and why is it used?
4. What command do you use to check the Python version?
5. What extension do you need for Python support in VS Code?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to check "Add Python to PATH" – Python commands won't work | Always check this box during installation |
| Installing the wrong version (32-bit vs 64-bit) | Choose the 64-bit version for better performance |
| Not using a code editor – working in Notepad | Use a proper code editor like VS Code |
| Not installing the Python extension – no syntax highlighting or debugging | Always install the Microsoft Python extension |
| Using the system Python for project work | Consider using virtual environments (covered later) |

---

### Interview Questions

1. **How do you install Python on a Windows machine?**  
   *Answer*: Download the installer from python.org, run it, check "Add Python to PATH", and click Install. Verify by typing `python --version` in the command prompt.

2. **What is the purpose of an integrated development environment (IDE) like VS Code?**  
   *Answer*: An IDE provides tools for writing, editing, debugging, and running code. VS Code is a lightweight editor with Python support through extensions, making it efficient for data analytics work.

3. **How do you run a Python script in VS Code?**  
   *Answer*: Open the `.py` file, click the Run button (triangle) in the top-right corner, or press `Ctrl+Shift+Enter`.

---

### Assignment and Mini Project

**Assignment 1.2** – Set up your Python environment:
1. Install Python.
2. Install VS Code.
3. Install the Python extension.
4. Create a new file called `setup_check.py`.
5. Write code that prints:
   - "Python installation successful!"
   - Your Python version (use `sys.version` – you'll need to import `sys`).
6. Run the file and verify the output.

**Mini Project** – Environment Check:
Write a Python script that:
```python
import sys
print("Welcome to Python for Data Analytics!")
print("Python version:", sys.version)
print("Congratulations! Your environment is set up correctly.")
```

---

### Summary and Revision Notes

- Python is installed from `python.org`.
- Always check **"Add Python to PATH"** during installation.
- Verify installation with `python --version`.
- VS Code is a free, lightweight code editor.
- Install the **Python extension** from Microsoft.
- Run Python code using the Run button or terminal.
- Use the terminal in VS Code for interactive exploration.

---

## Lesson 1.3 – Jupyter Notebook and JupyterLab

### Concept Explanation

**Jupyter Notebook** and **JupyterLab** are interactive web-based environments for writing and running Python code. They are especially popular in data analytics because they allow you to combine code, visualisations, and explanatory text (markdown) in a single document.

**Key differences**:

| **Feature** | **Jupyter Notebook** | **JupyterLab** |
|-------------|----------------------|----------------|
| **Interface** | Single document view | IDE-like interface with multiple panes |
| **Use Case** | Quick exploration, sharing, teaching | Complex projects, multi-file workflows |
| **Ease of Use** | Very simple | More powerful but slightly more complex |
| **File Extension** | `.ipynb` | `.ipynb` (same) |

**Why Jupyter for Data Analytics?**
- **Interactive**: Run code in cells; see results immediately.
- **Iterative**: Perfect for exploring data step by step.
- **Documentation**: Combine code with markdown notes – great for sharing analysis.
- **Visualisation**: Inline charts and graphs.

**Installation**:
Jupyter comes with **Anaconda** (a data science distribution) or can be installed using `pip`.

---

### Importance and Real-World Use Cases

- **Why it matters**: Jupyter is the industry standard for exploratory data analysis (EDA). It allows you to iterate quickly, visualise data, and share reproducible analyses.

- **Use cases**:
  - A **data analyst** uses Jupyter Notebook to explore a new dataset, cleaning it and creating visualisations step by step.
  - A **data scientist** uses JupyterLab to develop machine learning models, with multiple notebooks open simultaneously.
  - A **researcher** uses Jupyter Notebook to document their analysis, combining code, results, and explanations for publication.

---

### Step-by-Step Demonstration

**Installing Jupyter** (if not using Anaconda):
1. Open Terminal/Command Prompt.
2. Type: `pip install jupyterlab`
3. Once installed, type: `jupyter lab` to open JupyterLab.

**Installing Jupyter Notebook**:
1. Type: `pip install notebook`
2. Type: `jupyter notebook` to open the classic notebook interface.

**Using Jupyter Notebook**:
1. Open Jupyter Notebook (`jupyter notebook`).
2. In the browser, click **New** → **Python 3**.
3. A new notebook opens with a blank cell.
4. Type `print("Hello, Jupyter!")` and press `Shift+Enter` to run.
5. Add a new cell – click the **+** button.
6. Type `2 + 2` and press `Shift+Enter`.
7. Add a Markdown cell – click the dropdown at the top (Code → Markdown).
8. Type `# This is a heading` and press `Shift+Enter`.
9. Explore the menu: Run, Restart, Save, etc.

**Using JupyterLab**:
1. Open JupyterLab (`jupyter lab`).
2. Click **Python 3** under **Notebook**.
3. The interface is similar but has a file browser, terminal, and multiple panes.

---

### Practical Examples

- **Example 1**: A data analyst loads a CSV file in a Jupyter Notebook, uses pandas to explore it, and creates visualisations – all in one document.
- **Example 2**: A data scientist develops a machine learning model in JupyterLab, testing different algorithms in different notebooks, and comparing results side by side.

---

### Hands-on Coding Exercises

**Exercise 1.6** – Jupyter Notebook practice:
1. Open Jupyter Notebook (or JupyterLab).
2. Create a new Python notebook.
3. In the first cell, type: `print("Hello, Jupyter!")`.
4. In the second cell, type: `10 + 20`.
5. In the third cell, type: `name = "Alice"` and `print("Welcome, " + name)`.
6. Add a Markdown cell with a heading: `## My First Jupyter Notebook`.
7. Run all cells.
8. Save the notebook as `my_first_notebook.ipynb`.

---

### Mini Quiz

1. What is Jupyter Notebook used for?
2. What is the difference between Jupyter Notebook and JupyterLab?
3. What file extension does a Jupyter Notebook have?
4. How do you run a cell in Jupyter Notebook?
5. What is a Markdown cell used for?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not restarting the kernel after major changes | Restart the kernel to clear any variable state |
| Running cells out of order – variables may not exist | Use Kernel → Run All to ensure correct order |
| Not using Markdown to document your analysis | Always add explanatory text to make your notebook self-contained |
| Saving notebooks with sensitive data | Remove sensitive data before sharing |
| Forgetting to save the notebook | Save frequently (`Ctrl+S`) |

---

### Interview Questions

1. **What is Jupyter Notebook and why is it used in data analytics?**  
   *Answer*: Jupyter Notebook is an interactive web-based environment for writing and running Python code. It is used in data analytics because it combines code, visualisations, and explanatory text in a single document, making it ideal for exploratory data analysis and sharing reproducible research.

2. **What is the difference between Jupyter Notebook and JupyterLab?**  
   *Answer*: Jupyter Notebook is a single-document interface. JupyterLab is a more advanced IDE-like interface with multiple panes, file browser, and the ability to work with multiple notebooks and files simultaneously.

3. **How do you install Jupyter?**  
   *Answer*: Using `pip install jupyterlab` for JupyterLab or `pip install notebook` for the classic notebook. Alternatively, install Anaconda which includes Jupyter by default.

---

### Assignment and Mini Project

**Assignment 1.3** – Create a Jupyter Notebook:
1. Install Jupyter Notebook or JupyterLab.
2. Create a new notebook.
3. Write a markdown cell with the title: "Python Fundamentals - My First Notebook".
4. Write a code cell that prints "Welcome to Jupyter!".
5. Write a code cell that calculates and prints the result of 50 * (20 + 30).
6. Write a markdown cell explaining what the code does.
7. Save the notebook as `assignment_1_3.ipynb`.

**Mini Project** – Data Exploration Preview:
Create a Jupyter Notebook that:
- Uses a markdown cell to introduce the project.
- Has code cells that:
  1. Create a list of numbers: [10, 20, 30, 40, 50].
  2. Calculate and print the sum of the list.
  3. Calculate and print the average of the list.
  4. Print "Data exploration is powerful with Python!".
- Add markdown cells explaining each step.

---

### Summary and Revision Notes

- Jupyter Notebook is an interactive web-based environment for Python code.
- Combines code, visualisations, and markdown text.
- JupyterLab is a more advanced IDE-like version.
- File extension: `.ipynb`.
- Run cells with `Shift+Enter`.
- Use Markdown cells for documentation.

---

## Lesson 1.4 – Variables and Data Types

### Concept Explanation

**Variables** are containers that store data values. In Python, you don't need to declare a variable's type – it is inferred automatically from the value you assign.

**Data Types** in Python:

| **Data Type** | **Description** | **Example** |
|---------------|-----------------|-------------|
| `int` | Integer (whole numbers) | `age = 25` |
| `float` | Decimal numbers | `price = 19.99` |
| `str` | String (text) | `name = "Alice"` |
| `bool` | Boolean (True/False) | `is_student = True` |
| `list` | Ordered, mutable collection | `fruits = ["apple", "banana"]` |
| `tuple` | Ordered, immutable collection | `coordinates = (10, 20)` |
| `dict` | Key-value pairs (dictionary) | `person = {"name": "Alice", "age": 25}` |
| `set` | Unordered, unique values | `unique_ids = {1, 2, 3}` |

**Variable Naming Rules**:
- Must start with a letter or underscore (`_`).
- Can contain letters, numbers, and underscores.
- Case-sensitive (`age` and `Age` are different).
- Cannot use Python keywords (e.g., `if`, `for`, `while`).

**Type Checking**:
- `type(variable)` returns the data type.
- `isinstance(variable, type)` checks if a variable is of a specific type.

---

### Importance and Real-World Use Cases

- **Why it matters**: Variables store the data you work with. Understanding data types is essential for data manipulation, calculations, and avoiding errors.

- **Use cases**:
  - A **data analyst** stores sales figures in a list, customer names in strings, and date values in datetime objects.
  - A **data scientist** uses dictionaries to store model parameters.
  - A **developer** uses boolean flags to control program flow.

---

### Step-by-Step Demonstration

**Creating Variables**:
```python
# Integer
age = 25
print(age)

# Float
price = 19.99
print(price)

# String
name = "Alice"
print(name)

# Boolean
is_student = True
print(is_student)

# List
fruits = ["apple", "banana", "cherry"]
print(fruits)

# Dictionary
person = {"name": "Alice", "age": 25, "city": "New York"}
print(person)
```

**Checking Data Types**:
```python
print(type(age))      # <class 'int'>
print(type(price))    # <class 'float'>
print(type(name))     # <class 'str'>
print(type(is_student)) # <class 'bool'>
print(type(fruits))   # <class 'list'>
print(type(person))   # <class 'dict'>
```

**Type Conversion**:
```python
# String to integer
num_str = "100"
num_int = int(num_str)
print(num_int)

# Integer to float
num_float = float(25)
print(num_float)

# Number to string
num = 50
num_str = str(num)
print(num_str)
```

---

### Practical Examples

- **Example 1**: A dataset has a column of ages as strings. You convert them to integers for analysis.
- **Example 2**: You store customer data in a dictionary: `{"name": "John", "age": 30, "city": "London"}`.
- **Example 3**: You use a list to store sales figures for multiple months and calculate the total.

---

### Hands-on Coding Exercises

**Exercise 1.7** – Create and print variables:
```python
# Create variables for your name, age, and favourite colour
name = "Your Name"
age = 25
favourite_colour = "Blue"

# Print them
print("Name:", name)
print("Age:", age)
print("Favourite Colour:", favourite_colour)
```

**Exercise 1.8** – Check data types:
```python
# Create variables of different types
x = 10          # int
y = 3.14        # float
z = "Hello"     # str
w = True        # bool

# Print their types
print(type(x))
print(type(y))
print(type(z))
print(type(w))
```

**Exercise 1.9** – Type conversion:
```python
# Convert a string to an integer
str_num = "42"
int_num = int(str_num)
print(int_num)

# Convert an integer to a float
int_val = 7
float_val = float(int_val)
print(float_val)

# Convert a number to a string
num = 100
str_val = str(num)
print(str_val)
```

---

### Mini Quiz

1. What are the rules for naming variables in Python?
2. What is the data type of `3.14`?
3. How do you check the type of a variable?
4. What is the difference between a list and a tuple?
5. How do you convert a string to an integer?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using keywords as variable names (`if = 5`) | Avoid Python keywords |
| Case sensitivity issues (`Name` vs `name`) | Use consistent naming conventions |
| Forgetting to convert types before calculations | Always convert to the correct type |
| Using mutable default arguments | Use `None` as default and create a new list inside |
| Not using descriptive variable names | Use meaningful names (`total_sales` not `x`) |

---

### Interview Questions

1. **What are the different data types in Python?**  
   *Answer*: int, float, str, bool, list, tuple, dict, set. Each is used for different kinds of data – integers for whole numbers, floats for decimals, strings for text, booleans for true/false, lists for ordered collections, tuples for immutable ordered collections, dictionaries for key-value pairs, and sets for unordered unique values.

2. **What is the difference between a list and a tuple?**  
   *Answer*: Lists are mutable (can be changed), tuples are immutable (cannot be changed). Lists are defined with square brackets `[]`, tuples with parentheses `()`.

3. **How do you convert a string to an integer in Python?**  
   *Answer*: Using the `int()` function, e.g., `int("42")` returns `42`.

---

### Assignment and Mini Project

**Assignment 1.4** – Variables and types exercise:
```python
# Create the following variables:
# 1. name (string) - your name
# 2. age (integer) - your age
# 3. height (float) - your height in metres
# 4. is_student (boolean) - whether you are a student
# 5. subjects (list) - list of subjects you are studying
# 6. contact (dict) - email and phone number
# Print each variable and its type
```

**Mini Project** – Personal Data Form:
Create a Python script that:
1. Stores your personal information in variables (name, age, city, favourite colour).
2. Stores a list of your hobbies.
3. Stores a dictionary with your contact details (email, phone).
4. Prints all the information in a formatted way.
5. Prints the data type of each variable.

---

### Summary and Revision Notes

- Variables store data values.
- Data types: `int`, `float`, `str`, `bool`, `list`, `tuple`, `dict`, `set`.
- Use `type()` to check a variable's type.
- Convert types using `int()`, `float()`, `str()`.
- Follow naming conventions: lowercase with underscores (e.g., `my_variable`).
- Use descriptive variable names.

---

## Lesson 1.5 – Operators

### Concept Explanation

**Operators** are symbols that perform operations on variables and values. Python provides several types of operators:

**Arithmetic Operators**:

| **Operator** | **Description** | **Example** |
|--------------|-----------------|-------------|
| `+` | Addition | `10 + 5 = 15` |
| `-` | Subtraction | `10 - 5 = 5` |
| `*` | Multiplication | `10 * 5 = 50` |
| `/` | Division (float) | `10 / 5 = 2.0` |
| `//` | Floor Division | `10 // 3 = 3` |
| `%` | Modulus (remainder) | `10 % 3 = 1` |
| `**` | Exponentiation | `10 ** 3 = 1000` |

**Comparison Operators**:

| **Operator** | **Description** | **Example** |
|--------------|-----------------|-------------|
| `==` | Equal to | `10 == 5` → `False` |
| `!=` | Not equal to | `10 != 5` → `True` |
| `>` | Greater than | `10 > 5` → `True` |
| `<` | Less than | `10 < 5` → `False` |
| `>=` | Greater than or equal | `10 >= 10` → `True` |
| `<=` | Less than or equal | `5 <= 10` → `True` |

**Logical Operators**:

| **Operator** | **Description** | **Example** |
|--------------|-----------------|-------------|
| `and` | Both conditions True | `(10 > 5) and (10 < 20)` → `True` |
| `or` | At least one condition True | `(10 > 20) or (5 < 10)` → `True` |
| `not` | Negates the condition | `not (10 > 5)` → `False` |

**Assignment Operators**:

| **Operator** | **Description** | **Example** |
|--------------|-----------------|-------------|
| `=` | Assign | `x = 10` |
| `+=` | Add and assign | `x += 5` is `x = x + 5` |
| `-=` | Subtract and assign | `x -= 5` is `x = x - 5` |
| `*=` | Multiply and assign | `x *= 5` |
| `/=` | Divide and assign | `x /= 5` |
| `%=` | Modulus and assign | `x %= 5` |

---

### Importance and Real-World Use Cases

- **Why it matters**: Operators are the building blocks of all calculations and logic in Python. They are used in everything from simple arithmetic to complex data transformations.

- **Use cases**:
  - A **data analyst** calculates growth rates: `growth = (this_year - last_year) / last_year`.
  - A **financial analyst** computes profit: `profit = revenue - expenses`.
  - A **data scientist** uses logical operators to filter data: `df[(df['age'] > 18) & (df['age'] < 65)]`.

---

### Step-by-Step Demonstration

**Arithmetic Operators**:
```python
a = 10
b = 3

print(a + b)   # 13
print(a - b)   # 7
print(a * b)   # 30
print(a / b)   # 3.3333...
print(a // b)  # 3
print(a % b)   # 1
print(a ** b)  # 1000
```

**Comparison Operators**:
```python
x = 10
y = 5

print(x == y)   # False
print(x != y)   # True
print(x > y)    # True
print(x < y)    # False
print(x >= y)   # True
print(x <= y)   # False
```

**Logical Operators**:
```python
age = 25
is_student = True

print(age > 18 and is_student)   # True
print(age > 18 or age < 18)      # True
print(not is_student)            # False
```

**Assignment Operators**:
```python
x = 10
print(x)    # 10

x += 5
print(x)    # 15

x -= 3
print(x)    # 12

x *= 2
print(x)    # 24

x /= 4
print(x)    # 6.0
```

---

### Practical Examples

- **Example 1**: Calculating total sales: `total = sum(sales_list)` using arithmetic.
- **Example 2**: Filtering data: `if age >= 18 and is_registered:`.
- **Example 3**: Updating values in a loop: `counter += 1`.

---

### Hands-on Coding Exercises

**Exercise 1.10** – Arithmetic operators:
```python
# Calculate the following and print the results
# 1. The sum of 150 and 75
# 2. The difference between 200 and 50
# 3. The product of 25 and 4
# 4. The division of 100 by 3 (both float and floor division)
# 5. 2 to the power of 8
```

**Exercise 1.11** – Comparison and logical operators:
```python
# Check the following conditions and print True/False
# 1. Is 15 greater than 10?
# 2. Is 20 equal to 20?
# 3. Is 5 less than 3?
# 4. Is 10 greater than 5 AND 5 less than 10?
# 5. Is 7 greater than 10 OR 5 greater than 3?
```

---

### Mini Quiz

1. What is the result of `10 / 3`?
2. What is the result of `10 // 3`?
3. What does `%` do?
4. What is the difference between `==` and `=`?
5. What is the result of `(10 > 5) and (5 > 10)`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using `=` instead of `==` in conditions | Use `==` for comparison, `=` for assignment |
| Forgetting operator precedence | Use parentheses to make order explicit: `(a + b) * c` |
| Integer division confusion (`/` vs `//`) | Use `//` when you need an integer result |
| Comparing different types (e.g., `10 == "10"`) | Convert types before comparing |

---

### Interview Questions

1. **What is the difference between `/` and `//`?**  
   *Answer*: `/` performs float division, returning a float result. `//` performs floor division, returning an integer result rounded down.

2. **What is the result of `10 % 3`?**  
   *Answer*: `1` because 10 divided by 3 leaves a remainder of 1.

3. **What are logical operators and how are they used?**  
   *Answer*: Logical operators (`and`, `or`, `not`) combine boolean conditions. They are used in conditional statements to evaluate multiple conditions.

---

### Assignment and Mini Project

**Assignment 1.5** – Operations exercise:
```python
# Create two variables: revenue and expenses
# Calculate:
# 1. Profit (revenue - expenses)
# 2. Profit margin (profit / revenue)
# 3. Is the profit positive? (store result in a boolean variable)
# 4. Print all results
```

**Mini Project** – Financial Calculator:
Create a Python script that:
1. Asks the user for their monthly income.
2. Asks for their monthly expenses.
3. Calculates the savings (income - expenses).
4. Calculates the savings rate (savings / income * 100).
5. Prints a summary message: "Your monthly income is $[income]. Your expenses are $[expenses]. You save $[savings] per month, which is [savings_rate]% of your income."

---

### Summary and Revision Notes

- **Arithmetic**: `+`, `-`, `*`, `/`, `//`, `%`, `**`
- **Comparison**: `==`, `!=`, `>`, `<`, `>=`, `<=`
- **Logical**: `and`, `or`, `not`
- **Assignment**: `=`, `+=`, `-=`, `*=`, `/=`
- Use parentheses for clarity in complex expressions.

---

## Lesson 1.6 – Input and Output

### Concept Explanation

**Input** and **output** (I/O) allow your program to interact with the user. Input is how you get data from the user, and output is how you display results.

**Printing Output**:
- `print()` – displays text or variables to the console.
- Can print multiple items separated by commas.
- Can use f-strings for formatted output.

**Getting Input**:
- `input()` – waits for the user to type something and press Enter.
- Always returns a **string** – you must convert it if you need a different type.

**Formatted Output**:

**1. f-strings** (Python 3.6+):
```python
name = "Alice"
age = 25
print(f"My name is {name} and I am {age} years old.")
```

**2. `.format()` method**:
```python
print("My name is {} and I am {} years old.".format(name, age))
```

**3. Concatenation**:
```python
print("My name is " + name + " and I am " + str(age) + " years old.")
```

---

### Importance and Real-World Use Cases

- **Why it matters**: I/O is how users interact with your program. In data analytics, you often need to ask users for parameters (e.g., date ranges, file paths) and display results.

- **Use cases**:
  - A **data analyst** builds a script that asks for a date range, then generates a report for that period.
  - A **financial analyst** creates a tool that asks for revenue and expenses, then calculates profit.
  - A **developer** builds a command-line tool that takes user input for data processing.

---

### Step-by-Step Demonstration

**Basic `print()`**:
```python
print("Hello, World!")
print("This is a new line.")
print("You can print", "multiple", "items", sep=", ")
print("You can also print numbers:", 100)
```

**Using `input()`**:
```python
name = input("Enter your name: ")
print("Hello, " + name + "!")

age = input("Enter your age: ")
print("You are " + age + " years old.")
```

**Converting Input**:
```python
age_str = input("Enter your age: ")
age_int = int(age_str)  # Convert to integer
print("In 5 years, you will be " + str(age_int + 5) + " years old.")
```

**f-strings**:
```python
name = input("Enter your name: ")
age = int(input("Enter your age: "))
print(f"Hello, {name}! You are {age} years old.")
print(f"In 10 years, you will be {age + 10} years old.")
```

---

### Practical Examples

- **Example 1**: A script that asks for a filename and loads the data.
- **Example 2**: A tool that asks for a date range and generates a report.
- **Example 3**: A calculator that asks for two numbers and an operation.

---

### Hands-on Coding Exercises

**Exercise 1.12** – Basic input and output:
```python
# Ask the user for their name and age
# Print a greeting that includes their name and age
# Calculate and print their age in 10 years
```

**Exercise 1.13** – Data entry form:
```python
# Ask the user for:
# 1. Their first name
# 2. Their last name
# 3. Their city
# 4. Their occupation
# Print a formatted summary
```

**Exercise 1.14** – Simple calculator:
```python
# Ask the user for two numbers
# Ask the user for an operation (+, -, *, /)
# Perform the operation and print the result
```

---

### Mini Quiz

1. What does the `input()` function do?
2. What data type does `input()` return?
3. How do you convert a string to an integer?
4. What is an f-string and how is it used?
5. What is the purpose of the `print()` function?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to convert input – treating strings as numbers | Always convert input when you need a specific type |
| Not handling invalid input – program crashes | Use try/except for robust input handling |
| Using `+` for concatenation with non-strings | Use f-strings for cleaner formatting |
| Not providing clear prompts – users don't know what to enter | Always give clear instructions in the prompt |

---

### Interview Questions

1. **What is the difference between `print()` and `input()`?**  
   *Answer*: `print()` displays output to the console. `input()` waits for the user to type input and returns it as a string.

2. **How do you convert user input to an integer?**  
   *Answer*: Using the `int()` function: `age = int(input("Enter age: "))`.

3. **What is an f-string and why is it useful?**  
   *Answer*: An f-string is a formatted string literal (f"...{variable}..."). It allows you to embed variables directly in strings, making them cleaner and more readable.

---

### Assignment and Mini Project

**Assignment 1.6** – Personal profile program:
```python
# Ask the user for:
# - Name
# - Age
# - City
# - Favourite colour
# Print a formatted personal profile
```

**Mini Project** – Grade Calculator:
Create a program that:
1. Asks the user for their name.
2. Asks for marks in 5 subjects (one by one).
3. Calculates the total and average marks.
4. Prints a summary with the student's name, total marks, average, and grade.
   - Grade: >=90 = A, >=80 = B, >=70 = C, >=60 = D, <60 = F.

---

### Summary and Revision Notes

- `print()` – displays output.
- `input()` – gets user input (returns string).
- Convert input using `int()`, `float()`, etc.
- Use f-strings for formatted output: `f"Hello, {name}!"`.
- Always handle input validation.

---

## Lesson 1.7 – Conditional Statements

### Concept Explanation

**Conditional statements** allow your program to make decisions and execute different code blocks based on conditions. They are the foundation of logic in programming.

**The `if` Statement**:
```python
if condition:
    # code to run if condition is True
```

**`if-else` Statement**:
```python
if condition:
    # code if True
else:
    # code if False
```

**`if-elif-else` Statement**:
```python
if condition1:
    # code if condition1 is True
elif condition2:
    # code if condition2 is True
else:
    # code if all conditions are False
```

**Indentation**:
- Python uses indentation (spaces or tabs) to define code blocks.
- The standard is **4 spaces** per level.
- Consistent indentation is critical – Python will error if it's inconsistent.

**Comparison Operators** (review): `==`, `!=`, `>`, `<`, `>=`, `<=`

**Logical Operators** (review): `and`, `or`, `not`

---

### Importance and Real-World Use Cases

- **Why it matters**: Conditional logic is everywhere in data analytics – filtering data, classifying records, handling edge cases, and making decisions.

- **Use cases**:
  - A **data analyst** uses conditions to classify customers: `if revenue > 10000: "Premium"`.
  - A **financial analyst** checks if a company is profitable: `if profit > 0: "Profitable" else: "Loss"`.
  - A **data scientist** filters data: `if age >= 18 and age <= 65: include`.

---

### Step-by-Step Demonstration

**Basic `if` statement**:
```python
age = 18

if age >= 18:
    print("You are eligible to vote.")
    print("Please register.")
```

**`if-else` statement**:
```python
temperature = 25

if temperature > 30:
    print("It's hot outside!")
else:
    print("The weather is pleasant.")
```

**`if-elif-else` statement**:
```python
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"

print(f"Your grade is: {grade}")
```

**Nested conditions**:
```python
age = 25
is_student = True

if age >= 18:
    if is_student:
        print("You are an adult student.")
    else:
        print("You are an adult.")
else:
    print("You are a minor.")
```

**Using `and`, `or`, `not`**:
```python
age = 25
income = 50000

if age >= 18 and income >= 30000:
    print("You qualify for the loan.")
else:
    print("You do not qualify for the loan.")
```

---

### Practical Examples

- **Example 1**: Classifying customers:
```python
total_spend = 15000

if total_spend >= 10000:
    tier = "Premium"
elif total_spend >= 5000:
    tier = "Gold"
elif total_spend >= 1000:
    tier = "Silver"
else:
    tier = "Bronze"

print(f"Customer tier: {tier}")
```

- **Example 2**: Data validation:
```python
age = input("Enter your age: ")

if age.isdigit():
    age = int(age)
    if age >= 18:
        print("Welcome!")
    else:
        print("You must be 18 or older.")
else:
    print("Please enter a valid number.")
```

---

### Hands-on Coding Exercises

**Exercise 1.15** – Voting eligibility:
```python
# Ask the user for their age
# Print whether they are eligible to vote
# (age >= 18)
```

**Exercise 1.16** – Grade calculator:
```python
# Ask the user for a score
# Print the corresponding grade
# A: 90-100, B: 80-89, C: 70-79, D: 60-69, F: 0-59
```

**Exercise 1.17** – Password validator:
```python
# Ask the user for a password
# Check if the password is at least 8 characters long
# Check if it contains a number
# Print whether the password is valid
```

---

### Mini Quiz

1. What does `elif` stand for?
2. How does Python define code blocks?
3. What is the result of the following: `if 10 > 5: print("Yes")`
4. What is the difference between `=` and `==`?
5. What is the purpose of `elif`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting the colon (`:`) after the condition | Always include `:` at the end of the condition |
| Inconsistent indentation – causes errors | Always use 4 spaces for indentation |
| Using `=` instead of `==` in conditions | Use `==` for comparison |
| Not handling all cases in `if-elif-else` | Always include a final `else` for default handling |
| Over-nesting conditions | Use `and`/`or` to simplify nested conditions |

---

### Interview Questions

1. **What is the difference between `if` and `elif`?**  
   *Answer*: `if` checks a condition and executes the block if True. `elif` (short for "else if") checks an additional condition only if the previous `if` and `elif` conditions were False.

2. **How does Python handle indentation?**  
   *Answer*: Python uses indentation to define code blocks. Consistent indentation (4 spaces) is required; incorrect indentation will cause an `IndentationError`.

3. **What is the result of `if 10 > 5: print("Yes") else: print("No")`?**  
   *Answer*: "Yes" because 10 is greater than 5.

---

### Assignment and Mini Project

**Assignment 1.7** – Tax calculator:
```python
# Ask the user for their annual income
# Calculate tax based on the following brackets:
# 0-10000: 0%
# 10001-30000: 10%
# 30001-60000: 20%
# 60001+: 30%
# Print the tax amount and the effective tax rate
```

**Mini Project** – Loan Approval System:
Create a program that:
1. Asks the user for their age, annual income, and credit score.
2. Approves the loan if:
   - Age >= 18
   - Income >= 30000
   - Credit score >= 600
3. Prints a detailed decision with the reason for rejection (if any).

---

### Summary and Revision Notes

- Conditional statements: `if`, `elif`, `else`.
- Python uses indentation for code blocks.
- Comparison operators: `==`, `!=`, `>`, `<`, `>=`, `<=`.
- Logical operators: `and`, `or`, `not`.
- Always handle all possible cases.

---

## Lesson 1.8 – Loops

### Concept Explanation

**Loops** allow you to repeat a block of code multiple times. They are essential for processing collections of data.

**The `for` Loop**:
- Iterates over a sequence (list, tuple, string, range, etc.).

**Syntax**:
```python
for item in sequence:
    # code to execute for each item
```

**The `while` Loop**:
- Repeats as long as a condition is True.

**Syntax**:
```python
while condition:
    # code to execute while condition is True
```

**Loop Control Statements**:
- `break` – exits the loop immediately.
- `continue` – skips the rest of the current iteration and moves to the next.

**The `range()` Function**:
- Generates a sequence of numbers.
- `range(stop)`: 0 to stop-1
- `range(start, stop)`: start to stop-1
- `range(start, stop, step)`: start to stop-1 by step

---

### Importance and Real-World Use Cases

- **Why it matters**: Loops are used everywhere in data analytics – processing rows in a dataset, calculating aggregates, and automating repetitive tasks.

- **Use cases**:
  - A **data analyst** loops through a list of sales to calculate total revenue.
  - A **data scientist** loops through multiple models to train and evaluate them.
  - A **developer** uses a while loop to read data until the end of a file.

---

### Step-by-Step Demonstration

**`for` loop with a list**:
```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)
```

**`for` loop with `range()`**:
```python
for i in range(5):    # 0, 1, 2, 3, 4
    print(i)

for i in range(2, 7):  # 2, 3, 4, 5, 6
    print(i)

for i in range(0, 10, 2):  # 0, 2, 4, 6, 8
    print(i)
```

**`while` loop**:
```python
count = 0

while count < 5:
    print(f"Count: {count}")
    count += 1

print("Loop finished!")
```

**`break` and `continue`**:
```python
# break
for i in range(10):
    if i == 5:
        break  # exits loop
    print(i)

# continue
for i in range(10):
    if i % 2 == 0:  # if even, skip
        continue
    print(i)  # prints odd numbers only
```

**Nested loops**:
```python
for i in range(3):
    for j in range(2):
        print(f"i={i}, j={j}")
```

**Looping through strings**:
```python
word = "Python"

for letter in word:
    print(letter)
```

---

### Practical Examples

- **Example 1**: Summing numbers in a list:
```python
numbers = [10, 20, 30, 40, 50]
total = 0

for num in numbers:
    total += num

print(f"Total: {total}")
```

- **Example 2**: Finding the maximum value:
```python
numbers = [5, 12, 8, 3, 20]
max_val = numbers[0]

for num in numbers:
    if num > max_val:
        max_val = num

print(f"Maximum: {max_val}")
```

- **Example 3**: Counting occurrences:
```python
data = [1, 2, 3, 2, 1, 2, 3, 4, 5]
count_2 = 0

for item in data:
    if item == 2:
        count_2 += 1

print(f"Number of 2s: {count_2}")
```

---

### Hands-on Coding Exercises

**Exercise 1.18** – Sum of squares:
```python
# Calculate the sum of squares of numbers from 1 to 10
# Use a for loop
```

**Exercise 1.19** – Factorial calculator:
```python
# Calculate the factorial of a number entered by the user
# Use a for loop
```

**Exercise 1.20** – Multiplication table:
```python
# Ask the user for a number
# Print the multiplication table for that number (1 to 10)
```

---

### Mini Quiz

1. What is the difference between `for` and `while` loops?
2. What does `range(5)` generate?
3. What is the purpose of `break`?
4. What is the purpose of `continue`?
5. How do you loop through a list?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Infinite loops (forgetting to update the condition) | Always ensure the loop condition will eventually be False |
| Modifying a list while iterating over it | Iterate over a copy: `for item in list[:]:` |
| Off-by-one errors in `range()` | Remember `range(stop)` goes from 0 to stop-1 |
| Using `break` when `continue` was intended | Understand the difference before using |
| Not using meaningful variable names | Use descriptive names like `total`, `count`, `value` |

---

### Interview Questions

1. **What is the difference between `break` and `continue`?**  
   *Answer*: `break` exits the loop entirely. `continue` skips the rest of the current iteration and moves to the next iteration.

2. **How do you loop through a list and get both the index and the value?**  
   *Answer*: Using `enumerate()`: `for idx, value in enumerate(my_list):`

3. **What is the difference between `range(5)` and `range(1, 5)`?**  
   *Answer*: `range(5)` generates 0, 1, 2, 3, 4. `range(1, 5)` generates 1, 2, 3, 4.

---

### Assignment and Mini Project

**Assignment 1.8** – Data processing with loops:
```python
# Given the following list of monthly sales:
sales = [1200, 1500, 900, 1800, 1100, 1600, 1300, 1400, 1700, 1000, 1550, 1250]
# 1. Calculate total sales
# 2. Calculate average sales
# 3. Find the highest sales month (index + 1)
# 4. Find the lowest sales month (index + 1)
# 5. Count how many months had sales above 1500
```

**Mini Project** – Number Guessing Game:
Create a program that:
1. Generates a random number between 1 and 100 (use `random.randint(1, 100)`).
2. Asks the user to guess the number.
3. Gives hints: "Too high" or "Too low".
4. Counts the number of attempts.
5. Prints a congratulatory message when the user guesses correctly.
6. Uses a while loop and break.

---

### Summary and Revision Notes

- `for` loop: iterates over a sequence.
- `while` loop: repeats while a condition is True.
- `range()`: generates sequences of numbers.
- `break`: exits the loop.
- `continue`: skips the rest of the iteration.
- Use loops for processing collections and repeating operations.

---

## Lesson 1.9 – Functions

### Concept Explanation

**Functions** are reusable blocks of code that perform a specific task. They help you organise code, avoid repetition, and make your programs more modular.

**Defining a Function**:
```python
def function_name(parameters):
    """Docstring (optional)"""
    # code to execute
    return result  # optional
```

**Key Components**:
- `def` – keyword to define a function.
- `function_name` – name of the function (follow same rules as variables).
- `parameters` – inputs to the function (optional).
- `return` – returns a value (optional; if omitted, returns `None`).
- **Docstring** – documentation string (optional but recommended).

**Calling a Function**:
```python
function_name(arguments)
```

**Types of Functions**:
- **No parameters, no return** – prints or performs actions.
- **With parameters, no return** – processes data but doesn't return.
- **With parameters, with return** – processes data and returns a result.
- **Default parameters** – parameters with default values.
- **Keyword arguments** – calling with parameter names.

---

### Importance and Real-World Use Cases

- **Why it matters**: Functions are the building blocks of any Python project. They make code reusable, testable, and readable. In data analytics, functions are used for data cleaning, transformation, and analysis tasks.

- **Use cases**:
  - A **data analyst** writes a function to clean a dataset: `clean_data(df)`.
  - A **data scientist** writes a function to train a model: `train_model(X, y)`.
  - A **developer** writes a function to calculate KPIs: `calculate_metrics(sales_data)`.

---

### Step-by-Step Demonstration

**Basic Function**:
```python
def greet():
    print("Hello, World!")

greet()  # Calling the function
```

**Function with Parameters**:
```python
def greet_person(name):
    print(f"Hello, {name}!")

greet_person("Alice")
greet_person("Bob")
```

**Function with Return**:
```python
def add(a, b):
    return a + b

result = add(5, 3)
print(result)  # 8
```

**Function with Multiple Returns**:
```python
def min_max(numbers):
    return min(numbers), max(numbers)

minimum, maximum = min_max([10, 20, 30, 5, 15])
print(f"Min: {minimum}, Max: {maximum}")
```

**Default Parameters**:
```python
def greet(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

greet("Alice")           # Hello, Alice!
greet("Bob", "Hi")       # Hi, Bob!
```

**Keyword Arguments**:
```python
def describe_person(name, age, city):
    print(f"{name} is {age} years old and lives in {city}.")

describe_person(age=25, city="London", name="Alice")
```

**Docstring**:
```python
def calculate_average(numbers):
    """
    Calculate the average of a list of numbers.

    Args:
        numbers (list): A list of numbers.

    Returns:
        float: The average of the numbers.
    """
    if not numbers:
        return 0
    return sum(numbers) / len(numbers)
```

**Variable Scope**:
- **Local**: Variables defined inside a function.
- **Global**: Variables defined outside any function.

```python
x = 10  # global variable

def my_function():
    y = 5   # local variable
    print(x)  # can access global
    print(y)

my_function()
print(x)  # works
# print(y)  # error - y is not defined outside
```

---

### Practical Examples

- **Example 1**: Data cleaning function:
```python
def clean_sales_data(sales_list):
    """Remove negative values and convert to float."""
    cleaned = [float(s) for s in sales_list if float(s) >= 0]
    return cleaned
```

- **Example 2**: Calculation function:
```python
def calculate_profit(revenue, expenses):
    """Calculate profit and margin."""
    profit = revenue - expenses
    margin = (profit / revenue) * 100 if revenue > 0 else 0
    return profit, margin
```

---

### Hands-on Coding Exercises

**Exercise 1.21** – Simple functions:
```python
# 1. Create a function that takes two numbers and returns their sum
# 2. Create a function that takes a name and prints "Hello, [name]!"
# 3. Create a function that takes a list and returns the maximum value
```

**Exercise 1.22** – Calculator functions:
```python
# Create functions for:
# 1. add(a, b)
# 2. subtract(a, b)
# 3. multiply(a, b)
# 4. divide(a, b)
# Include a docstring for each
```

**Exercise 1.23** – Data summarization:
```python
# Create a function that takes a list of numbers
# Returns: total, average, maximum, minimum
# Use a docstring
```

---

### Mini Quiz

1. What keyword is used to define a function?
2. What is the purpose of `return`?
3. What is a docstring?
4. What is the difference between local and global variables?
5. What is the default return value of a function without `return`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to call the function (missing parentheses) | Always include parentheses when calling: `my_function()` |
| Modifying global variables inside functions | Avoid modifying globals; return values instead |
| Not documenting functions | Always include docstrings |
| Functions that do too many things | Follow the Single Responsibility Principle |
| Using mutable default arguments | Use `None` as default: `def func(items=None):` |

---

### Interview Questions

1. **What is a function in Python?**  
   *Answer*: A function is a reusable block of code that performs a specific task. It can take parameters, process data, and return a result.

2. **What is the difference between `return` and `print()`?**  
   *Answer*: `return` sends a value back to the caller and ends the function. `print()` displays output to the console but does not return a value.

3. **What is the purpose of a docstring?**  
   *Answer*: A docstring documents the purpose, parameters, and return value of a function. It is used by `help()` and is a best practice for writing maintainable code.

---

### Assignment and Mini Project

**Assignment 1.9** – Function practice:
```python
# Create the following functions:
# 1. calculate_area(length, width) - returns the area of a rectangle
# 2. calculate_compound_interest(principal, rate, years) - returns final amount
# 3. is_palindrome(word) - returns True if the word is a palindrome
# 4. count_vowels(text) - returns the number of vowels in a string
```

**Mini Project** – Data Analysis Functions:
Create a program with the following functions:
1. `load_data()` – returns a list of numbers (or use a predefined list).
2. `calculate_total(data)` – returns the sum.
3. `calculate_average(data)` – returns the average.
4. `find_extremes(data)` – returns (min, max).
5. `calculate_std_dev(data)` – returns the standard deviation.
6. `display_stats(data)` – prints all statistics.
7. `main()` – the main program that calls the other functions.

---

### Summary and Revision Notes

- Functions are defined with `def`.
- Parameters are inputs to the function.
- `return` returns a value.
- Docstrings document the function.
- Variables inside functions are local.
- Functions make code reusable, testable, and organised.

---

## Lesson 1.10 – Modules and Packages

### Concept Explanation

**Modules** and **packages** allow you to organise your Python code and reuse functionality from other files and libraries.

**Module**: A single Python file (`.py`) containing functions, classes, and variables.

**Package**: A collection of modules organised in a directory with an `__init__.py` file.

**Importing modules**:
```python
import module_name
import module_name as alias
from module_name import function_name
from module_name import *  # (not recommended)
```

**Common built-in modules for data analytics**:
- `math` – mathematical functions.
- `random` – random number generation.
- `datetime` – date and time manipulation.
- `os` – operating system interface.
- `sys` – system-specific parameters.
- `json` – JSON data handling.
- `csv` – CSV file handling.

---

### Importance and Real-World Use Cases

- **Why it matters**: Modules allow you to leverage existing code (libraries) rather than reinventing the wheel. In data analytics, you'll use external libraries like pandas, NumPy, and Matplotlib extensively.

- **Use cases**:
  - A **data analyst** uses `pandas` to load and analyse data.
  - A **data scientist** uses `numpy` for numerical operations.
  - A **developer** uses `os` to interact with the file system.

---

### Step-by-Step Demonstration

**Importing a module**:
```python
import math

print(math.pi)           # 3.14159
print(math.sqrt(16))     # 4.0
print(math.factorial(5)) # 120
```

**Importing with an alias**:
```python
import math as m

print(m.pi)
```

**Importing specific functions**:
```python
from math import pi, sqrt, factorial

print(pi)
print(sqrt(25))
print(factorial(4))
```

**Creating your own module**:
1. Create a file called `my_module.py`:
```python
# my_module.py
def greet(name):
    return f"Hello, {name}!"

PI = 3.14159

def add(a, b):
    return a + b
```

2. In another file, import it:
```python
import my_module

print(my_module.greet("Alice"))
print(my_module.PI)
print(my_module.add(5, 3))
```

**Common modules in action**:

**Random module**:
```python
import random

print(random.randint(1, 100))  # Random integer
print(random.choice(["a", "b", "c"]))  # Random choice
print(random.random())  # Random float 0-1
```

**Datetime module**:
```python
from datetime import datetime, timedelta

now = datetime.now()
print(now)

# Future date
future = now + timedelta(days=30)
print(future)

# Formatting
print(now.strftime("%Y-%m-%d %H:%M:%S"))
```

**OS module**:
```python
import os

print(os.getcwd())  # Current working directory
# os.listdir('.')   # List files in directory
# os.path.exists('file.txt')  # Check if file exists
```

---

### Practical Examples

- **Example 1**: Using `random` for simulations:
```python
import random

# Simulate flipping a coin 100 times
heads = sum(1 for _ in range(100) if random.random() > 0.5)
print(f"Heads: {heads}, Tails: {100-heads}")
```

- **Example 2**: Using `datetime` for reporting:
```python
from datetime import datetime

def log_message(message):
    timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    print(f"[{timestamp}] {message}")

log_message("Data processing started")
```

---

### Hands-on Coding Exercises

**Exercise 1.24** – Math module:
```python
# Use the math module to:
# 1. Calculate the square root of 144
# 2. Calculate 3 to the power of 4
# 3. Calculate the sine of 90 degrees (radians)
# 4. Calculate the area of a circle with radius 5
```

**Exercise 1.25** – Random module:
```python
# Use the random module to:
# 1. Generate a random number between 1 and 100
# 2. Randomly choose an item from a list
# 3. Shuffle a list
# 4. Generate 10 random numbers between 1 and 50
```

**Exercise 1.26** – Datetime module:
```python
# Use the datetime module to:
# 1. Get the current date and time
# 2. Get today's date
# 3. Format today's date as "2025-01-15"
# 4. Calculate the date 100 days from today
```

---

### Mini Quiz

1. What is the difference between a module and a package?
2. How do you import a specific function from a module?
3. What is the purpose of `import math as m`?
4. What is the `random` module used for?
5. What is the `datetime` module used for?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using `from module import *` – pollutes the namespace | Import only what you need or use `import module` |
| Not creating modules for reusable code | Organise code into modules for reusability |
| Not checking if a module is installed | Use `pip list` to check and `pip install` to install |
| Using `os` functions without error handling | Use try/except when dealing with file operations |

---

### Interview Questions

1. **What is the difference between a module and a package?**  
   *Answer*: A module is a single Python file (`.py`). A package is a directory containing multiple modules, with an `__init__.py` file.

2. **How do you import a module in Python?**  
   *Answer*: Using `import module_name`, `import module_name as alias`, or `from module_name import function_name`.

3. **What is the `math` module used for?**  
   *Answer*: The `math` module provides mathematical functions like `sqrt()`, `sin()`, `cos()`, constants like `pi`, and functions like `factorial()`.

---

### Assignment and Mini Project

**Assignment 1.10** – Module practice:
```python
# 1. Import the math module and calculate:
#    - sin(pi/2)
#    - cos(0)
#    - log(100, 10)
#    - ceil(3.14) and floor(3.14)
# 2. Import the random module and:
#    - Generate a random password (8 characters using letters and numbers)
#    - Simulate rolling a dice 100 times and count the frequency of each number
```

**Mini Project** – Utilities Module:
Create a module (`utils.py`) with the following functions:
1. `read_csv(filepath)` – reads a CSV file and returns a list of rows.
2. `write_csv(filepath, data)` – writes data to a CSV file.
3. `calculate_stats(numbers)` – returns (mean, median, mode).
4. `format_date(date)` – formats a date as "YYYY-MM-DD".
5. `generate_id()` – returns a random 8-character ID.

---

### Summary and Revision Notes

- A module is a single Python file.
- A package is a directory of modules.
- Use `import` to import modules.
- Use `from module import function` to import specific functions.
- `random` – random numbers.
- `datetime` – date and time.
- `math` – mathematical functions.
- Organise code into modules for reusability.

---

## Lesson 1.11 – File Handling

### Concept Explanation

**File handling** allows Python programs to read from and write to files. This is essential for data analytics – loading datasets, saving results, and automating data processing.

**Common file operations**:
1. Open a file.
2. Read or write content.
3. Close the file.

**Opening a file**:
```python
file = open('filename.txt', 'mode')
```

**File Modes**:
| **Mode** | **Description** |
|----------|-----------------|
| `r` | Read (default) |
| `w` | Write (overwrites existing) |
| `a` | Append (adds to end) |
| `r+` | Read and write |
| `x` | Create (fails if file exists) |

**Reading Files**:
- `read()` – reads the entire file.
- `readline()` – reads one line at a time.
- `readlines()` – reads all lines into a list.

**Writing Files**:
- `write()` – writes a string to the file.
- `writelines()` – writes a list of strings.

**Closing Files**:
- Always close files with `file.close()` to free resources.
- Better: use `with` statement (auto-closes).

---

### Importance and Real-World Use Cases

- **Why it matters**: Data analytics is all about working with data files. You'll read CSV files, Excel files, JSON files, and more. File handling is the gateway to your data.

- **Use cases**:
  - A **data analyst** reads a CSV file, processes it, and writes the output to a new CSV.
  - A **financial analyst** reads transaction logs and generates a summary report.
  - A **developer** writes log files for debugging.

---

### Step-by-Step Demonstration

**Reading a Text File**:
```python
# Method 1: Using with (recommended)
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)

# Method 2: Read line by line
with open('example.txt', 'r') as file:
    for line in file:
        print(line.strip())
```

**Writing to a Text File**:
```python
# Writing
with open('output.txt', 'w') as file:
    file.write("Hello, World!\n")
    file.write("This is a new line.")

# Appending
with open('output.txt', 'a') as file:
    file.write("\nThis line is appended.")
```

**Reading a CSV File** (using the `csv` module):
```python
import csv

with open('data.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)  # row is a list
```

**Writing a CSV File**:
```python
import csv

data = [
    ['Name', 'Age', 'City'],
    ['Alice', 25, 'New York'],
    ['Bob', 30, 'London'],
    ['Charlie', 35, 'Paris']
]

with open('output.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerows(data)
```

**Handling File Existence**:
```python
import os

if os.path.exists('data.csv'):
    with open('data.csv', 'r') as file:
        print("File exists. Reading...")
        content = file.read()
else:
    print("File not found.")
```

---

### Practical Examples

- **Example 1**: Reading sales data from a CSV:
```python
import csv

total_sales = 0
with open('sales.csv', 'r') as file:
    reader = csv.reader(file)
    next(reader)  # Skip header
    for row in reader:
        total_sales += float(row[1])  # Assuming sales are in column 1

print(f"Total sales: ${total_sales:,.2f}")
```

- **Example 2**: Writing processed data:
```python
import csv

# Data to write
output_data = [
    ['Product', 'Total Sales'],
    ['Widget A', 1200],
    ['Widget B', 800],
    ['Widget C', 1500]
]

with open('sales_summary.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerows(output_data)
print("Summary saved to sales_summary.csv")
```

---

### Hands-on Coding Exercises

**Exercise 1.27** – File reading:
```python
# Create a text file with your name, age, and city (one per line)
# Write a program that reads the file and prints the information
```

**Exercise 1.28** – CSV reading:
```python
# Create a CSV file with student names and grades
# Write a program that calculates the average grade
```

**Exercise 1.29** – File writing:
```python
# Write a program that takes user input and saves it to a log file
# The log should include a timestamp
```

---

### Mini Quiz

1. What does the `with` statement do in file handling?
2. What is the difference between `r` and `w` modes?
3. What does `readlines()` return?
4. Why is it important to close files?
5. What is the `csv` module used for?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to close files | Use `with` statement for automatic closing |
| Using `r` mode for non-existent files | Check if file exists before opening |
| Not handling encoding issues | Use `encoding='utf-8'` when opening files |
| Reading large files entirely into memory | Use line-by-line reading for large files |
| Not handling exceptions | Use try/except for robust file operations |

---

### Interview Questions

1. **How do you read a CSV file in Python?**  
   *Answer*: Using the `csv` module: `csv.reader()` or `csv.DictReader()`.

2. **What is the advantage of using `with` when opening files?**  
   *Answer*: The `with` statement automatically closes the file when the block is exited, even if an exception occurs. It's cleaner and safer.

3. **How do you write a list of lists to a CSV file?**  
   *Answer*: Using `csv.writer().writerows(list_of_lists)`.

---

### Assignment and Mini Project

**Assignment 1.11** – File processing:
```python
# 1. Read a CSV file with sales data (Product, Month, Sales)
# 2. Calculate total sales per product
# 3. Write the results to a new CSV file
# 4. Use the with statement for all file operations
```

**Mini Project** – Data Logging System:
Create a program that:
1. Asks the user for temperature readings (daily highs and lows).
2. Appends each reading to a log file (`temperature_log.csv`).
3. Can read the log file and calculate:
   - Average high temperature.
   - Average low temperature.
   - Highest recorded temperature.
   - Lowest recorded temperature.
4. Prints a summary report.

---

### Summary and Revision Notes

- Use `open()` to open files.
- Modes: `r` (read), `w` (write), `a` (append).
- Use `with` for automatic closing.
- Read: `read()`, `readline()`, `readlines()`.
- Write: `write()`, `writelines()`.
- Use the `csv` module for CSV files.

---

## Lesson 1.12 – Exception Handling

### Concept Explanation

**Exception handling** allows you to manage errors gracefully, preventing your program from crashing and providing helpful feedback to users.

**Common Exceptions**:
- `ZeroDivisionError` – division by zero.
- `FileNotFoundError` – file not found.
- `ValueError` – invalid value.
- `TypeError` – incorrect type.
- `IndexError` – list index out of range.
- `KeyError` – dictionary key not found.

**Syntax**:
```python
try:
    # code that might raise an exception
except ExceptionType:
    # code to handle the exception
else:
    # code to run if no exception occurred
finally:
    # code to run regardless (always runs)
```

**Types of `except` blocks**:
- `except` – catches all exceptions (not recommended).
- `except ExceptionType` – catches specific exception.
- `except (Type1, Type2)` – catches multiple types.
- `except Exception as e` – catches and stores the exception.

---

### Importance and Real-World Use Cases

- **Why it matters**: Real-world data is messy and unpredictable. Exception handling ensures your programs can handle unexpected inputs, missing files, and other issues without crashing.

- **Use cases**:
  - A **data analyst** handles `FileNotFoundError` when a file is missing.
  - A **developer** handles `ValueError` when users enter invalid data.
  - A **data scientist** handles `ZeroDivisionError` when calculating ratios.

---

### Step-by-Step Demonstration

**Basic `try-except`**:
```python
try:
    numerator = int(input("Enter a number: "))
    denominator = int(input("Enter another number: "))
    result = numerator / denominator
    print(f"Result: {result}")
except ZeroDivisionError:
    print("Error: Cannot divide by zero.")
except ValueError:
    print("Error: Please enter valid numbers.")
```

**Handling Multiple Exceptions**:
```python
try:
    file = open("data.txt", "r")
    content = file.read()
    print(content)
except FileNotFoundError:
    print("Error: File not found.")
except IOError:
    print("Error: Could not read file.")
finally:
    file.close()  # This runs even if an error occurs
```

**Using `else` and `finally`**:
```python
try:
    num = int(input("Enter a number: "))
    result = 100 / num
except ValueError:
    print("Error: Please enter a number.")
except ZeroDivisionError:
    print("Error: Cannot divide by zero.")
else:
    print(f"Result: {result}")  # Runs if no error
finally:
    print("Execution complete.")  # Always runs
```

**Raising Exceptions**:
```python
def set_age(age):
    if age < 0 or age > 120:
        raise ValueError("Age must be between 0 and 120")
    return age

try:
    age = set_age(-5)
except ValueError as e:
    print(f"Error: {e}")
```

**Practical Example** – Robust input function:
```python
def get_number(prompt):
    while True:
        try:
            return float(input(prompt))
        except ValueError:
            print("Invalid input. Please enter a number.")

age = get_number("Enter your age: ")
print(f"Your age is {age}")
```

---

### Practical Examples

- **Example 1**: Handling missing files:
```python
import csv

def read_sales_data(filename):
    try:
        with open(filename, 'r') as file:
            reader = csv.reader(file)
            data = list(reader)
        return data
    except FileNotFoundError:
        print(f"Error: {filename} not found.")
        return []
    except Exception as e:
        print(f"Unexpected error: {e}")
        return []

# Usage
sales_data = read_sales_data("sales.csv")
```

- **Example 2**: Handling data processing errors:
```python
def calculate_average(numbers):
    try:
        return sum(numbers) / len(numbers)
    except ZeroDivisionError:
        print("Error: Empty list.")
        return 0
    except TypeError:
        print("Error: List contains non-numeric values.")
        return 0

# Test
data = [10, 20, 30, 40]
print(calculate_average(data))  # 25.0
print(calculate_average([]))    # Error handling
```

---

### Hands-on Coding Exercises

**Exercise 1.30** – Division with error handling:
```python
# Ask the user for two numbers
# Divide the first by the second
# Handle ZeroDivisionError, ValueError, and any other exceptions
```

**Exercise 1.31** – File reading with error handling:
```python
# Ask the user for a filename
# Try to open and read the file
# Handle FileNotFoundError and any other exceptions
```

**Exercise 1.32** – Input validation:
```python
# Create a function that asks for a number
# Use a while loop and try-except to handle invalid input
# Keep asking until a valid number is entered
```

---

### Mini Quiz

1. What is the purpose of `try-except`?
2. What is the difference between `except` and `except Exception as e`?
3. When does the `else` block execute?
4. When does the `finally` block execute?
5. How do you raise your own exception?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using a bare `except:` – catches everything, including KeyboardInterrupt | Be specific: `except SpecificException:` |
| Catching exceptions too broadly – masks the real issue | Catch specific exceptions and handle appropriately |
| Ignoring the exception – not logging or handling it | Log the error or show a meaningful message to the user |
| Using `except:` and then `pass` – silently failing | Always handle exceptions or raise them |
| Not cleaning up resources in `finally` | Use `finally` or `with` for cleanup |

---

### Interview Questions

1. **What is exception handling in Python?**  
   *Answer*: Exception handling is a mechanism to manage errors gracefully using `try-except-else-finally` blocks. It allows the program to continue running or provide meaningful error messages to the user.

2. **What is the difference between `except` and `finally`?**  
   *Answer*: `except` runs when an exception occurs. `finally` runs regardless of whether an exception occurred, and is used for cleanup operations.

3. **How do you raise a custom exception?**  
   *Answer*: Using the `raise` statement: `raise ValueError("Custom error message")`.

---

### Assignment and Mini Project

**Assignment 1.12** – Exception handling practice:
```python
# 1. Create a function that divides two numbers with proper error handling
# 2. Create a function that opens a file with error handling
# 3. Create a function that converts a string to an integer with error handling
# 4. Test each function with valid and invalid inputs
```

**Mini Project** – Robust Data Processor:
Create a program that:
1. Asks the user for a CSV filename.
2. Handles `FileNotFoundError` gracefully.
3. Handles `ValueError` for invalid data in the CSV.
4. Processes the data and calculates statistics.
5. Handles `ZeroDivisionError` when calculating averages.
6. Prints a summary or error messages as appropriate.
7. Uses `try-except-else-finally` where appropriate.

---

### Summary and Revision Notes

- `try-except`: handle exceptions.
- `except` specific exceptions for precise handling.
- `else`: runs if no exception.
- `finally`: runs regardless.
- `raise`: raise custom exceptions.
- Use exception handling for robust programs, especially when working with user input and files.

---

## Final Phase 1 Assessment

Now that you have completed all lessons, test your overall understanding.

### Self-Evaluation Checklist

- I can write and run Python code in VS Code and Jupyter.
- I can create variables and use different data types.
- I can use operators (arithmetic, comparison, logical).
- I can get user input and display output.
- I can use conditional statements (`if-elif-else`).
- I can use loops (`for`, `while`).
- I can define and use functions.
- I can import and use modules.
- I can read and write files.
- I can handle exceptions.

---

### Answers to Mini Quizzes

**Lesson 1.1**: 1. Guido van Rossum, 1991. 2. Code runs line by line without compilation. 3. Extensive libraries and readability. 4. pandas, NumPy, Matplotlib. 5. Yes.

**Lesson 1.2**: 1. python.org. 2. Allows you to run Python from any directory. 3. A code editor with Python support. 4. `python --version`. 5. Python (by Microsoft).

**Lesson 1.3**: 1. Interactive Python environment. 2. Notebook is single-document; JupyterLab is multi-pane IDE. 3. `.ipynb`. 4. `Shift+Enter`. 5. For explanatory text/documentation.

**Lesson 1.4**: 1. Letters/underscore, then letters/numbers/underscores; not keywords. 2. `float`. 3. `type(variable)`. 4. List is mutable; tuple is immutable. 5. `int(string)`.

**Lesson 1.5**: 1. 3.3333... 2. 3. 3. Remainder. 4. `==` compares; `=` assigns. 5. `False` (and requires both true).

**Lesson 1.6**: 1. Gets user input. 2. String. 3. `int(string)`. 4. Formatted string `f"{variable}"`. 5. Displays output.

**Lesson 1.7**: 1. "else if". 2. Indentation. 3. "Yes". 4. `=` assigns; `==` compares. 5. To check additional conditions.

**Lesson 1.8**: 1. `for` iterates over sequences; `while` repeats while true. 2. 0, 1, 2, 3, 4. 3. Exits the loop. 4. Skips the rest of the iteration. 5. `for item in list:`.

**Lesson 1.9**: 1. `def`. 2. Returns a value. 3. Documentation string. 4. Local is inside function; global is outside. 5. `None`.

**Lesson 1.10**: 1. Module = single file; Package = directory with modules. 2. `from module import function`. 3. To import with an alias. 4. Random numbers. 5. Date and time.

**Lesson 1.11**: 1. Automatically closes files. 2. `r` = read; `w` = write (overwrites). 3. All lines as a list. 4. To free resources. 5. CSV file handling.

**Lesson 1.12**: 1. To handle errors gracefully. 2. `except Exception as e` captures the exception. 3. If no exception occurs. 4. Always runs. 5. `raise Exception("message")`.

---

**Congratulations!** You have completed Phase 1 of Python Fundamentals for Data Analytics. You now have a solid foundation in Python programming. Keep practising!



----




<br/><br/><br/>
<center> <b>Happy Learning! 😊</b> </center>