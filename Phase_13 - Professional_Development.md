# Phase 13: Professional Development

Welcome to **Phase 13** – the final phase of your Python for Data Analytics journey! You have mastered the technical skills: data manipulation, visualisation, statistics, SQL, automation, and building real-world projects. Now, it's time to learn the **professional practices** that separate a coder from a professional data engineer.

In the real world, you rarely work in isolation. You will collaborate with teams, maintain code over time, deploy solutions to production, and ensure your work is reliable, scalable, and maintainable. This phase covers the essential professional skills that employers look for:

- **Writing Clean Python Code**: Following industry standards (PEP 8) and best practices.
- **Project Structure**: Organising your code for readability and maintainability.
- **Virtual Environments**: Isolating dependencies for reproducible projects.
- **Git and GitHub**: Version control and collaboration.
- **Performance Optimization**: Making your code faster and more efficient.
- **Logging**: Recording events for debugging and monitoring.
- **Testing**: Ensuring your code works as expected.
- **Packaging**: Distributing your code as a library.
- **Deployment Basics**: Getting your code into production.

These skills are what make you a **professional** data analyst or data engineer. Let's level up!

---

## Lesson 13.1 – Writing Clean Python Code

### Concept Explanation

**Clean code** is code that is easy to read, understand, and maintain. It follows consistent style conventions, uses meaningful names, and is well-organised.

**Why clean code matters**:
- **Readability**: Code is read more often than it is written.
- **Maintainability**: Easy to fix bugs and add features.
- **Collaboration**: Team members can understand each other's code.
- **Reduced bugs**: Clear code has fewer errors.

**Key principles**:

1. **Follow PEP 8**: Python's official style guide.
   - Use 4 spaces for indentation.
   - Maximum line length: 79 characters.
   - Use `snake_case` for variables and functions.
   - Use `CamelCase` for classes.
   - Use `UPPER_CASE` for constants.

2. **Use Meaningful Names**:
   - Variables: `total_sales` not `ts`.
   - Functions: `calculate_average()` not `calc_avg()`.
   - Classes: `CustomerData` not `CD`.

3. **Write Docstrings**:
   - Document what each function does.
   - Describe parameters and return values.
   - Provide examples for complex functions.

4. **Keep Functions Small**:
   - Each function should do one thing.
   - Aim for 10-20 lines per function.
   - If a function is too long, break it up.

5. **Use Comments Wisely**:
   - Comments explain *why*, not *what*.
   - Code should be self-documenting.
   - Remove commented-out code.

---

### Importance and Real-World Use Cases

- **Why it matters**: In a professional setting, your code will be reviewed, maintained, and extended by others. Clean code reduces friction and accelerates delivery.

- **Use cases**:
  - A **data engineer** writes a data pipeline that needs to be maintained by the team.
  - A **data scientist** shares a notebook that becomes a production model.
  - A **team lead** reviews pull requests and enforces coding standards.

---

### Step-by-Step Demonstration

```python
# ============== BAD CODE (Don't do this) ==============
def bad_code(a,b,c):
    # this function does stuff
    x=a+b
    y=b+c
    z=x+y
    if z>100:
        print("big")
    else:
        print("small")
    return z

# ============== GOOD CODE (Do this) ==============

def calculate_sum_and_compare(first_value: float, second_value: float, third_value: float) -> float:
    """
    Calculate the sum of three numbers and print whether the sum is greater than 100.

    Args:
        first_value (float): The first number to add.
        second_value (float): The second number to add.
        third_value (float): The third number to add.

    Returns:
        float: The total sum of the three numbers.
    """
    sum_of_two = first_value + second_value
    sum_of_three = sum_of_two + third_value

    if sum_of_three > 100:
        print("The sum is greater than 100.")
    else:
        print("The sum is 100 or less.")

    return sum_of_three

# ============== Documentation ==============

# Use docstrings for functions
def calculate_average(numbers: list) -> float:
    """
    Calculate the average of a list of numbers.

    Args:
        numbers (list): A list of numeric values.

    Returns:
        float: The average of the numbers.

    Raises:
        ValueError: If the list is empty.

    Example:
        >>> calculate_average([10, 20, 30])
        20.0
    """
    if not numbers:
        raise ValueError("Cannot calculate average of empty list")
    return sum(numbers) / len(numbers)

# ============== Type Hints ==============
from typing import List, Dict, Optional

def process_sales_data(sales_data: List[Dict[str, float]], threshold: Optional[float] = None) -> Dict[str, float]:
    """
    Process sales data and calculate summary statistics.

    Args:
        sales_data: List of dictionaries with 'amount' and 'quantity' keys.
        threshold: Optional threshold for filtering.

    Returns:
        Dictionary with total, average, and count.
    """
    pass

# ============== Constants ==============
# Constants should be in UPPER_CASE
MAX_RETRY_ATTEMPTS = 3
DEFAULT_CONNECTION_TIMEOUT = 30
API_BASE_URL = "https://api.example.com"

# ============== Module Docstring ==============
"""
Data Processing Module

This module provides functions for cleaning, transforming, and analysing
sales data.

Author: Your Name
Version: 1.0.0
"""

# ============== Import Order ==============
# 1. Standard library imports
import os
import sys
from datetime import datetime

# 2. Third-party imports
import pandas as pd
import numpy as np

# 3. Local imports
from . import utils
```

---

### Practical Examples

- **Example 1**: Refactoring a messy notebook into a clean script.
- **Example 2**: Adding docstrings to all functions in a module.
- **Example 3**: Using type hints for better code readability.

---

### Hands-on Coding Exercises

**Exercise 13.1** – Code review:
```python
# 1. Write a poorly written function.
# 2. Identify 5 issues in the code.
# 3. Rewrite the function following PEP 8 and best practices.
# 4. Add a docstring and type hints.
```

**Exercise 13.2** – Refactoring:
```python
# 1. Take a long, messy function.
# 2. Break it into smaller, single-purpose functions.
# 3. Add meaningful names and docstrings.
# 4. Add type hints.
```

---

### Mini Quiz

1. What is PEP 8?
2. What naming convention should you use for variables?
3. Why should you write docstrings?
4. What is the maximum recommended line length in PEP 8?
5. What is the purpose of type hints?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using vague variable names (x, y, temp) | Use descriptive names |
| Writing long, complex functions | Keep functions small and focused |
| No docstrings | Always document your code |
| Mixing naming conventions | Follow PEP 8 consistently |
| Commenting obvious code | Comments should explain *why* |

---

### Interview Questions

1. **What is PEP 8 and why is it important?**  
   *Answer*: PEP 8 is Python's official style guide. It ensures consistency and readability across Python code, making it easier to maintain and collaborate on.

2. **What is the difference between a comment and a docstring?**  
   *Answer*: A comment is for developers to understand the code. A docstring is attached to a function/class/module and can be accessed programmatically using `help()`.

3. **Why is it important to write clean code?**  
   *Answer*: Clean code is easier to read, maintain, debug, and extend. It reduces technical debt and improves team productivity.

---

### Assignment and Mini Project

**Assignment 13.1** – Code cleaning:
```python
# 1. Take a messy script (provided or from an old project).
# 2. Clean it following PEP 8 guidelines.
# 3. Add docstrings to all functions.
# 4. Add type hints.
# 5. Break long functions into smaller ones.
# 6. Create a final clean version.
```

---

### Summary and Revision Notes

- Follow PEP 8 for consistent style.
- Use meaningful names (snake_case for variables/functions, CamelCase for classes).
- Write docstrings for all functions.
- Keep functions small and focused.
- Use type hints for better readability.
- Comments should explain *why*, not *what*.

---

## Lesson 13.2 – Project Structure

### Concept Explanation

A well-organised project structure makes your code easy to navigate, test, and deploy. It also makes it easier for others to understand and contribute to your project.

**A typical Python data analytics project structure**:

```
project_name/
│
├── README.md                 # Project description and instructions
├── requirements.txt          # Python dependencies
├── setup.py                  # Package setup (if packaging)
├── .gitignore                # Git ignored files
│
├── data/                     # Data files (CSV, Excel, etc.)
│   ├── raw/                  # Raw data
│   └── processed/            # Processed data
│
├── notebooks/                # Jupyter notebooks
│   └── exploration.ipynb
│
├── src/                      # Source code
│   ├── __init__.py
│   ├── data_processing.py
│   ├── analysis.py
│   └── utils.py
│
├── tests/                    # Unit tests
│   ├── __init__.py
│   └── test_analysis.py
│
├── scripts/                  # Executable scripts
│   └── run_pipeline.py
│
└── config/                   # Configuration files
    └── config.yaml
```

**Key principles**:
- Separate code, data, and notebooks.
- Keep your code modular.
- Use `__init__.py` to make directories into packages.
- Put tests in a separate `tests/` directory.

---

### Importance and Real-World Use Cases

- **Why it matters**: A consistent project structure reduces confusion, makes onboarding easier, and ensures your project can be deployed reliably.

- **Use cases**:
  - A **data engineer** sets up a project structure for a data pipeline.
  - A **data scientist** organises a machine learning project.
  - A **team** uses a standard structure for all projects.

---

### Step-by-Step Demonstration

```python
# ============== Creating a Project Structure ==============

import os
from pathlib import Path

def create_project_structure(project_name: str):
    """Create a standard project structure for a data analytics project."""
    project_dir = Path(project_name)
    
    # Create directories
    directories = [
        project_dir,
        project_dir / 'data' / 'raw',
        project_dir / 'data' / 'processed',
        project_dir / 'notebooks',
        project_dir / 'src',
        project_dir / 'tests',
        project_dir / 'scripts',
        project_dir / 'config'
    ]
    
    for directory in directories:
        directory.mkdir(parents=True, exist_ok=True)
        # Create __init__.py for Python packages
        if directory.name in ['src', 'tests']:
            (directory / '__init__.py').touch()
    
    # Create essential files
    (project_dir / 'README.md').write_text(f"""# {project_name}

## Description
This project does X, Y, and Z.

## Installation
```bash
pip install -r requirements.txt
```

## Usage
```bash
python scripts/run_pipeline.py
```

## Project Structure
- `data/`: Data files
- `notebooks/`: Jupyter notebooks
- `src/`: Source code
- `tests/`: Unit tests
- `scripts/`: Executable scripts
- `config/`: Configuration files
""")

    (project_dir / 'requirements.txt').write_text("""# Data analysis
pandas==1.5.3
numpy==1.24.0
matplotlib==3.6.0
seaborn==0.12.0

# Jupyter
jupyter==1.0.0

# Testing
pytest==7.2.0

# Optional
openpyxl==3.0.10
xlrd==2.0.1
""")

    (project_dir / '.gitignore').write_text("""
# Python
__pycache__/
*.pyc
*.pyo
*.pyd
.Python

# Virtual environment
venv/
env/
.venv/

# Jupyter
.ipynb_checkpoints/
*.ipynb

# Data
data/raw/
data/processed/

# IDE
.vscode/
.idea/

# OS
.DS_Store
Thumbs.db
""")

    print(f"Project structure created at: {project_dir.absolute()}")

# create_project_structure('my_data_project')
```

**Using `__init__.py` to create packages**:

```python
# src/__init__.py
"""
Data Processing Package
Provides functions for cleaning and transforming data.
"""

# src/data_processing.py
def clean_data(df):
    """Clean the input DataFrame."""
    pass

def transform_data(df):
    """Transform the input DataFrame."""
    pass

# src/analysis.py
def calculate_metrics(df):
    """Calculate key metrics."""
    pass
```

**Importing from your own package**:

```python
# scripts/run_pipeline.py
import sys
from pathlib import Path

# Add the src directory to the path
sys.path.insert(0, str(Path(__file__).parent.parent / 'src'))

from data_processing import clean_data, transform_data
from analysis import calculate_metrics

# Use the functions
# df = clean_data(df)
# df = transform_data(df)
# metrics = calculate_metrics(df)
```

---

### Practical Examples

- **Example 1**: Setting up a project structure for a data pipeline.
- **Example 2**: Organising a machine learning project.
- **Example 3**: Using the structure for a data analysis project.

---

### Hands-on Coding Exercises

**Exercise 13.3** – Project structure:
```python
# 1. Create a project structure using the script above.
# 2. Add a simple Python module in the src/ directory.
# 3. Add a test in the tests/ directory.
# 4. Create a README.md file.
# 5. Commit the structure to Git.
```

---

### Mini Quiz

1. What is the purpose of `__init__.py`?
2. Why should you separate code, data, and notebooks?
3. What should go in the `requirements.txt` file?
4. What is the purpose of the `.gitignore` file?
5. Where should unit tests be placed in a project?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Keeping everything in one notebook | Use a modular structure |
| No `requirements.txt` | Always document dependencies |
| Hardcoding file paths | Use `pathlib` and relative paths |
| Not using `__init__.py` | Makes directories into packages |

---

### Interview Questions

1. **How would you structure a Python data analytics project?**  
   *Answer*: I would use a structure with `data/`, `notebooks/`, `src/`, `tests/`, `scripts/`, and `config/` directories. I would include a `README.md`, `requirements.txt`, and `.gitignore`.

2. **What is the purpose of `requirements.txt`?**  
   *Answer*: It lists all Python dependencies with specific versions, ensuring the project can be reproduced on any machine.

3. **Why do you separate code from notebooks?**  
   *Answer*: Notebooks are for exploration; code in `src/` is for production. Separating them makes code reusable, testable, and deployable.

---

### Assignment and Mini Project

**Assignment 13.2** – Project setup:
```python
# 1. Create a project structure for a data analysis project.
# 2. Add a module with a function that processes data.
# 3. Add a script that runs the data pipeline.
# 4. Add a test file for the function.
# 5. Write a README.md file.
```

---

### Summary and Revision Notes

- Use a consistent project structure.
- Separate: data, notebooks, source code, tests, scripts, config.
- Use `__init__.py` to create packages.
- Document dependencies in `requirements.txt`.
- Use `.gitignore` to exclude unnecessary files.

---

## Lesson 13.3 – Virtual Environments

### Concept Explanation

A **virtual environment** is an isolated Python environment that allows you to install packages specific to a project without affecting the global Python installation.

**Why virtual environments matter**:
- **Dependency isolation**: Different projects may need different versions of the same package.
- **Reproducibility**: Others can recreate your environment.
- **Cleanliness**: Avoids cluttering the global Python installation.

**Tools for virtual environments**:
- **`venv`**: Built-in to Python 3.3+.
- **`conda`**: For Anaconda/Miniconda users.
- **`pipenv`**: Combines pip and virtualenv.
- **`poetry`**: Modern dependency management.

**Using `venv` (built-in)**:
```bash
# Create a virtual environment
python -m venv myenv

# Activate (Windows)
myenv\Scripts\activate

# Activate (Mac/Linux)
source myenv/bin/activate

# Install packages
pip install pandas numpy matplotlib

# Deactivate
deactivate
```

---

### Importance and Real-World Use Cases

- **Why it matters**: In a professional environment, you will work on multiple projects with different dependencies. Virtual environments prevent conflicts.

- **Use cases**:
  - A **data scientist** works on multiple ML projects with different library versions.
  - A **data engineer** maintains a production environment with strict version requirements.
  - A **developer** contributes to open-source projects.

---

### Step-by-Step Demonstration

```python
# ============== Creating and Using a Virtual Environment ==============

"""
Step-by-step guide:
1. Open terminal/command prompt.
2. Navigate to your project directory.
3. Create a virtual environment:
   python -m venv venv
4. Activate it:
   Windows: venv\Scripts\activate
   Mac/Linux: source venv/bin/activate
5. Install packages:
   pip install pandas numpy matplotlib seaborn
6. Freeze dependencies:
   pip freeze > requirements.txt
7. Deactivate:
   deactivate
"""

# ============== Using .env files for environment variables ==============

from dotenv import load_dotenv  # pip install python-dotenv
import os

# Load environment variables from .env file
load_dotenv()

DB_HOST = os.getenv('DB_HOST')
DB_NAME = os.getenv('DB_NAME')
API_KEY = os.getenv('API_KEY')

# .env file example:
# DB_HOST=localhost
# DB_NAME=analytics
# API_KEY=your-secret-key

# ============== Checking the current environment ==============

import sys

def check_environment():
    """Check the current Python environment."""
    print(f"Python version: {sys.version}")
    print(f"Python executable: {sys.executable}")
    print(f"Python path: {sys.path}")

check_environment()
```

**Using `requirements.txt`**:

```bash
# Generate requirements from the current environment
pip freeze > requirements.txt

# Install from requirements.txt
pip install -r requirements.txt
```

**Using `conda` (if using Anaconda)**:

```bash
# Create a conda environment
conda create -n myenv python=3.10 pandas numpy matplotlib

# Activate
conda activate myenv

# Export environment
conda env export > environment.yml

# Create environment from file
conda env create -f environment.yml
```

---

### Practical Examples

- **Example 1**: Setting up a virtual environment for a data science project.
- **Example 2**: Creating a `requirements.txt` file for a project.
- **Example 3**: Using environment variables for sensitive data.

---

### Hands-on Coding Exercises

**Exercise 13.4** – Virtual environment:
```python
# 1. Create a virtual environment for a project.
# 2. Install pandas, numpy, and matplotlib.
# 3. Create a requirements.txt file.
# 4. Deactivate and reactivate the environment.
# 5. Install packages from requirements.txt.
```

---

### Mini Quiz

1. What is a virtual environment?
2. What command is used to create a virtual environment?
3. What command activates a virtual environment on Windows?
4. What is the purpose of `requirements.txt`?
5. What is the difference between `venv` and `conda`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not using virtual environments | Always use a virtual environment |
| Committing `venv/` to Git | Add `venv/` to `.gitignore` |
| Not updating `requirements.txt` | Freeze dependencies after installations |
| Using `conda` and `pip` interchangeably | Stick to one package manager |

---

### Interview Questions

1. **What is a virtual environment and why is it important?**  
   *Answer*: A virtual environment is an isolated Python environment for a project. It prevents dependency conflicts and ensures reproducibility.

2. **How do you create a `requirements.txt` file?**  
   *Answer*: Using `pip freeze > requirements.txt` after installing the required packages.

3. **What is the difference between `venv` and `conda`?**  
   *Answer*: `venv` is built into Python and manages Python packages. `conda` is a cross-platform package manager that can manage Python and non-Python packages.

---

### Assignment and Mini Project

**Assignment 13.3** – Environment setup:
```python
# 1. Create a virtual environment for a new project.
# 2. Install 5 packages used in data analytics.
# 3. Generate a requirements.txt file.
# 4. Create a .gitignore file that excludes the virtual environment.
# 5. Write a README file with environment setup instructions.
```

---

### Summary and Revision Notes

- Virtual environments isolate project dependencies.
- Built-in: `python -m venv venv`.
- Activate: `source venv/bin/activate` (Mac/Linux) or `venv\Scripts\activate` (Windows).
- Freeze dependencies: `pip freeze > requirements.txt`.
- Add `venv/` to `.gitignore`.

---

## Lesson 13.4 – Git and GitHub

### Concept Explanation

**Git** is a version control system that tracks changes to files. **GitHub** is a platform for hosting Git repositories and collaborating with others.

**Key concepts**:
- **Repository (repo)**: A folder with files tracked by Git.
- **Commit**: A snapshot of changes.
- **Branch**: A parallel version of the code.
- **Merge**: Combining changes from different branches.
- **Pull Request (PR)**: A request to merge changes from one branch to another.

**Basic Git workflow**:
1. Clone a repository.
2. Create a new branch.
3. Make changes.
4. Stage and commit changes.
5. Push the branch.
6. Open a pull request.
7. Merge the pull request.

---

### Importance and Real-World Use Cases

- **Why it matters**: Git is the standard for version control in the software industry. It enables collaboration, tracks history, and supports rollback.

- **Use cases**:
  - A **data engineer** collaborates on a data pipeline with a team.
  - A **data scientist** version controls notebooks and code.
  - A **developer** contributes to open-source projects.

---

### Step-by-Step Demonstration

```bash
# ============== Basic Git Commands ==============

# Initialize a Git repository
git init

# Clone an existing repository
git clone https://github.com/username/repo.git

# Check status
git status

# Add files to staging
git add file.py          # Add a specific file
git add .                # Add all files

# Commit changes
git commit -m "Add data processing module"

# Push to remote repository
git push origin main

# Pull changes from remote
git pull origin main

# Create a new branch
git branch feature/new-pipeline

# Switch to a branch
git checkout feature/new-pipeline

# Switch and create (shorthand)
git checkout -b feature/new-pipeline

# Merge a branch
git checkout main
git merge feature/new-pipeline

# See commit history
git log

# See commit history (one line)
git log --oneline
```

```python
# ============== Using Git from Python ==============

import subprocess
import os

def git_status():
    """Get the current Git status."""
    result = subprocess.run(['git', 'status', '--porcelain'], capture_output=True, text=True)
    return result.stdout

def git_commit(message):
    """Commit all changes with a message."""
    subprocess.run(['git', 'add', '.'])
    result = subprocess.run(['git', 'commit', '-m', message], capture_output=True, text=True)
    return result.stdout

def git_push():
    """Push changes to the remote repository."""
    result = subprocess.run(['git', 'push', 'origin', 'main'], capture_output=True, text=True)
    return result.stdout

# Example usage
# print(git_status())
# print(git_commit("Update data processing script"))
# print(git_push())
```

```python
# ============== .gitignore for Data Analytics ==============

"""
# .gitignore file example for data analytics projects

# Python
__pycache__/
*.pyc
*.pyo
*.pyd
.Python
*.so
*.egg
*.egg-info/
dist/
build/

# Virtual environments
venv/
env/
.venv/

# Jupyter Notebooks
.ipynb_checkpoints/
*.ipynb

# Data files
*.csv
*.xlsx
*.xls
*.json
*.parquet
*.pickle
data/raw/
data/processed/

# Environment variables
.env
.env.local

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# Logs
*.log
logs/
"""
```

---

### Practical Examples

- **Example 1**: Initialising a Git repository for a data project.
- **Example 2**: Creating a branch for a new feature.
- **Example 3**: Resolving a merge conflict.

---

### Hands-on Coding Exercises

**Exercise 13.5** – Git basics:
```python
# 1. Create a new project directory.
# 2. Initialize a Git repository.
# 3. Create a Python file and add it.
# 4. Commit the file with a message.
# 5. Create a branch and switch to it.
# 6. Make changes and commit.
# 7. Switch back to main and merge.
```

---

### Mini Quiz

1. What is the purpose of Git?
2. What command stages files for commit?
3. What command creates a new branch?
4. What is a pull request?
5. What is the purpose of `.gitignore`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Committing large data files | Add data files to `.gitignore` |
| Committing secrets | Use `.env` and add to `.gitignore` |
| Making large, unfocused commits | Commit small, logical changes |
| Not using branches | Use branches for new features |
| Forgetting to pull before pushing | Pull before pushing to avoid conflicts |

---

### Interview Questions

1. **What is Git and why is it used?**  
   *Answer*: Git is a version control system used to track changes, collaborate with others, and manage code versions.

2. **What is the difference between `git pull` and `git fetch`?**  
   *Answer*: `git fetch` downloads changes from the remote but doesn't merge them. `git pull` fetches and merges them.

3. **What is a merge conflict and how do you resolve it?**  
   *Answer*: A merge conflict occurs when two branches have conflicting changes. It is resolved by manually editing the conflicting files and committing the resolution.

---

### Assignment and Mini Project

**Assignment 13.4** – Git workflow:
```python
# 1. Create a new repository on GitHub.
# 2. Clone it locally.
# 3. Add a data processing script.
# 4. Commit and push the changes.
# 5. Create a branch for a new feature.
# 6. Make changes and push the branch.
# 7. Open a pull request on GitHub.
# 8. Merge the pull request.
```

---

### Summary and Revision Notes

- Git tracks changes to files.
- `git init` initialises a repository.
- `git add` stages changes.
- `git commit` saves changes.
- `git push` sends changes to remote.
- `git pull` fetches remote changes.
- Use `.gitignore` to exclude files.
- Use branches for new features.

---

## Lesson 13.5 – Performance Optimization

### Concept Explanation

**Performance optimization** is the process of making your code run faster and use fewer resources. In data analytics, this is critical when working with large datasets.

**Key areas to optimize**:
1. **Algorithmic efficiency**: Choosing the right algorithm.
2. **Vectorization**: Using NumPy/Pandas vectorized operations.
3. **Data types**: Using appropriate data types.
4. **Memory usage**: Avoiding unnecessary copies.
5. **Parallel processing**: Using multiple cores.
6. **Caching**: Storing intermediate results.

**Profiling tools**:
- **`time`**: Simple timing.
- **`timeit`**: Accurate timing of small code snippets.
- **`cProfile`**: Profiling to find bottlenecks.
- **`line_profiler`**: Line-by-line profiling.

---

### Importance and Real-World Use Cases

- **Why it matters**: Slow code wastes time and resources. In production, performance can impact user experience and costs.

- **Use cases**:
  - A **data engineer** optimises an ETL pipeline to run faster.
  - A **data scientist** speeds up model training.
  - A **developer** reduces memory usage for large datasets.

---

### Step-by-Step Demonstration

```python
import time
import numpy as np
import pandas as pd

# ============== Profiling with time ==============

def slow_function():
    """A slow function for demonstration."""
    result = []
    for i in range(1000000):
        result.append(i ** 2)
    return result

def fast_function():
    """A fast function for demonstration."""
    return np.arange(1000000) ** 2

start = time.time()
slow_function()
print(f"Slow function time: {time.time() - start:.4f}s")

start = time.time()
fast_function()
print(f"Fast function time: {time.time() - start:.4f}s")

# ============== Vectorization ==============

# Bad: Using loops
def slow_sum_of_squares(data):
    total = 0
    for x in data:
        total += x ** 2
    return total

# Good: Using vectorization
def fast_sum_of_squares(data):
    return np.sum(data ** 2)

data = np.random.rand(1000000)
print(f"Slow sum: {slow_sum_of_squares(data):.2f}")
print(f"Fast sum: {fast_sum_of_squares(data):.2f}")

# ============== Optimizing Pandas ==============

# Bad: Iterating row by row
df = pd.DataFrame({'A': np.random.rand(100000), 'B': np.random.rand(100000)})

def slow_pandas_iteration(df):
    total = 0
    for i, row in df.iterrows():
        total += row['A'] * row['B']
    return total

# Good: Vectorized operation
def fast_pandas_vectorized(df):
    return (df['A'] * df['B']).sum()

print(f"Slow Pandas: {slow_pandas_iteration(df):.2f}")
print(f"Fast Pandas: {fast_pandas_vectorized(df):.2f}")

# ============== Using appropriate data types ==============

def memory_optimization():
    """Demonstrate memory optimization with data types."""
    # Bad: Using float64 when float32 is sufficient
    df_bad = pd.DataFrame({'value': np.random.rand(1000000)})
    
    # Good: Using float32
    df_good = pd.DataFrame({'value': np.random.rand(1000000).astype(np.float32)})
    
    print(f"Float64 memory: {df_bad.memory_usage(deep=True).sum() / 1024**2:.2f} MB")
    print(f"Float32 memory: {df_good.memory_usage(deep=True).sum() / 1024**2:.2f} MB")

memory_optimization()

# ============== Caching with functools ==============

from functools import lru_cache

@lru_cache(maxsize=128)
def expensive_computation(x):
    """A computationally expensive function."""
    time.sleep(0.5)  # Simulate expensive operation
    return x ** 2

# First call (cache miss)
start = time.time()
print(expensive_computation(10))
print(f"First call: {time.time() - start:.2f}s")

# Second call (cache hit)
start = time.time()
print(expensive_computation(10))
print(f"Second call: {time.time() - start:.2f}s")

# ============== Profiling with cProfile ==============

"""
# Run from command line:
import cProfile
cProfile.run('slow_function()')

# Or in code:
import cProfile
cProfile.run('slow_function()', sort='cumtime')
"""

print("\nProfiling example (run in terminal):")
print("python -m cProfile my_script.py")
```

**Using `cProfile` for detailed profiling**:

```python
import cProfile
import pstats

def my_slow_function():
    """A function to profile."""
    result = []
    for i in range(100000):
        result.append(i ** 2)
    return result

# Profile the function
profiler = cProfile.Profile()
profiler.enable()
my_slow_function()
profiler.disable()

# Print statistics
stats = pstats.Stats(profiler).sort_stats('cumtime')
stats.print_stats(10)  # Print top 10 slowest functions
```

---

### Practical Examples

- **Example 1**: Vectorizing a loop for a large dataset.
- **Example 2**: Optimizing Pandas operations.
- **Example 3**: Using caching for expensive calculations.

---

### Hands-on Coding Exercises

**Exercise 13.6** – Performance optimization:
```python
# 1. Write a slow function.
# 2. Profile it using `time` and `cProfile`.
# 3. Optimize it using vectorization or better algorithms.
# 4. Measure the speed improvement.
```

---

### Mini Quiz

1. What is vectorization?
2. Why is NumPy faster than Python loops?
3. What is the purpose of caching?
4. What does `cProfile` do?
5. How can you reduce memory usage in Pandas?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Premature optimization | Profile first, then optimize |
| Using loops instead of vectorization | Use NumPy/Pandas vectorized operations |
| Not considering memory usage | Use appropriate data types |
| Not caching expensive operations | Use caching for repeated computations |

---

### Interview Questions

1. **How do you optimize Python code for large datasets?**  
   *Answer*: Use vectorization (NumPy/Pandas), appropriate data types, avoid Python loops, and use profiling to find bottlenecks.

2. **What is the difference between `time` and `timeit`?**  
   *Answer*: `time` is for simple timing, `timeit` is more accurate for small code snippets.

3. **How do you profile a Python script?**  
   *Answer*: Using `cProfile` from the command line or in code.

---

### Assignment and Mini Project

**Assignment 13.5** – Performance optimization:
```python
# 1. Take a slow data processing script.
# 2. Profile it to find bottlenecks.
# 3. Optimize at least three parts of the code.
# 4. Measure and document the performance improvement.
```

---

### Summary and Revision Notes

- Profile before optimizing.
- Use vectorized operations (NumPy/Pandas).
- Choose appropriate data types.
- Use caching for repeated calculations.
- Measure performance improvements.

---

## Lesson 13.6 – Logging

### Concept Explanation

**Logging** is the process of recording events that happen during the execution of your program. It is essential for debugging, monitoring, and auditing.

**Why logging matters**:
- **Debugging**: Understand what went wrong.
- **Monitoring**: Track the health of your application.
- **Auditing**: Record who did what and when.
- **Performance**: Track execution times.

**Logging levels**:
| **Level** | **Description** |
|-----------|-----------------|
| `DEBUG` | Detailed information for debugging |
| `INFO` | Confirmation of normal operation |
| `WARNING` | Indications of potential issues |
| `ERROR` | Error events that prevent a function from working |
| `CRITICAL` | Critical errors that may cause the application to fail |

**Using the `logging` module**:
- Built into Python.
- Configurable to write to files, consoles, or external services.
- Supports formatting and filtering.

---

### Importance and Real-World Use Cases

- **Why it matters**: Logging is essential for maintaining and debugging production systems. It provides visibility into what your code is doing.

- **Use cases**:
  - A **data engineer** logs data pipeline execution for monitoring.
  - A **data scientist** logs model training metrics.
  - A **developer** logs API calls for debugging.

---

### Step-by-Step Demonstration

```python
import logging
import sys
from datetime import datetime

# ============== Basic Logging ==============

# Configure logging
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
    handlers=[
        logging.StreamHandler(sys.stdout),  # Output to console
        logging.FileHandler('app.log')      # Output to file
    ]
)

# Create a logger
logger = logging.getLogger(__name__)

# Log different levels
logger.debug("This is a debug message")      # Won't appear (level=INFO)
logger.info("This is an info message")
logger.warning("This is a warning message")
logger.error("This is an error message")
logger.critical("This is a critical message")

# ============== Logging in Functions ==============

def process_data(data):
    """Process data with logging."""
    logger.info(f"Processing {len(data)} items")
    
    try:
        # Simulate processing
        result = [x * 2 for x in data]
        logger.info(f"Successfully processed {len(result)} items")
        return result
    except Exception as e:
        logger.error(f"Error processing data: {e}")
        raise

# Test the function
data = [1, 2, 3, 4, 5]
result = process_data(data)
print(result)

# ============== Configuring Logging with a Dictionary ==============

import logging.config

LOGGING_CONFIG = {
    'version': 1,
    'disable_existing_loggers': False,
    'formatters': {
        'standard': {
            'format': '%(asctime)s - %(name)s - %(levelname)s - %(message)s'
        },
        'detailed': {
            'format': '%(asctime)s - %(name)s - %(levelname)s - %(filename)s:%(lineno)d - %(message)s'
        }
    },
    'handlers': {
        'console': {
            'class': 'logging.StreamHandler',
            'level': 'INFO',
            'formatter': 'standard',
            'stream': 'ext://sys.stdout'
        },
        'file': {
            'class': 'logging.handlers.RotatingFileHandler',
            'level': 'DEBUG',
            'formatter': 'detailed',
            'filename': 'application.log',
            'maxBytes': 10485760,  # 10 MB
            'backupCount': 5
        }
    },
    'root': {
        'level': 'DEBUG',
        'handlers': ['console', 'file']
    }
}

logging.config.dictConfig(LOGGING_CONFIG)
logger = logging.getLogger(__name__)

logger.info("Application started")
logger.debug("This is a debug message")
logger.warning("This is a warning")

# ============== Logging Exceptions ==============

try:
    1 / 0
except Exception as e:
    logger.exception("An error occurred")  # Logs the exception with traceback

# ============== Logging for a Data Pipeline ==============

def run_data_pipeline():
    """A complete data pipeline with logging."""
    logger = logging.getLogger(__name__)
    
    logger.info("=" * 50)
    logger.info("DATA PIPELINE STARTING")
    logger.info("=" * 50)
    
    try:
        # Step 1: Extract
        logger.info("Step 1: Extracting data...")
        # Simulate extraction
        # data = extract_data()
        logger.info("Extraction complete")
        
        # Step 2: Transform
        logger.info("Step 2: Transforming data...")
        # Simulate transformation
        # transformed = transform_data(data)
        logger.info("Transformation complete")
        
        # Step 3: Load
        logger.info("Step 3: Loading data...")
        # Simulate loading
        # load_data(transformed)
        logger.info("Loading complete")
        
        logger.info("=" * 50)
        logger.info("DATA PIPELINE COMPLETED SUCCESSFULLY")
        logger.info("=" * 50)
        
    except Exception as e:
        logger.error(f"Pipeline failed: {e}", exc_info=True)
        sys.exit(1)

# run_data_pipeline()
```

---

### Practical Examples

- **Example 1**: Logging a data pipeline execution.
- **Example 2**: Logging errors with tracebacks.
- **Example 3**: Using rotating log files for production.

---

### Hands-on Coding Exercises

**Exercise 13.7** – Logging:
```python
# 1. Create a logger for a data processing script.
# 2. Log INFO messages at key steps.
# 3. Log ERROR messages for exceptions.
# 4. Write logs to both console and file.
# 5. Use different log levels.
```

---

### Mini Quiz

1. What are the five logging levels?
2. Why is logging important in production?
3. How do you write logs to a file?
4. How do you log an exception with traceback?
5. What is the difference between `logger.info()` and `print()`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using `print()` instead of logging | Use logging for production |
| Not including enough context | Include timestamps and function names |
| Using the root logger directly | Create module-specific loggers |
| Not rotating log files | Use rotating file handlers |

---

### Interview Questions

1. **What is the purpose of logging in Python?**  
   *Answer*: Logging records events for debugging, monitoring, and auditing. It provides visibility into application behavior.

2. **What are the different logging levels?**  
   *Answer*: DEBUG, INFO, WARNING, ERROR, CRITICAL.

3. **How do you log an exception in Python?**  
   *Answer*: Using `logger.exception("Error message")` inside an except block.

---

### Assignment and Mini Project

**Assignment 13.6** – Logging implementation:
```python
# 1. Add logging to a data processing script.
# 2. Configure logging to write to a file with timestamps.
# 3. Log INFO for each processing step.
# 4. Log ERROR for any failures.
# 5. Test the logging by running the script.
```

---

### Summary and Revision Notes

- Use the `logging` module for production logging.
- Levels: DEBUG, INFO, WARNING, ERROR, CRITICAL.
- Configure logging to write to console and file.
- Use `logger.exception()` for exceptions.
- Use rotating file handlers for production.

---

## Lesson 13.7 – Testing

### Concept Explanation

**Testing** is the process of verifying that your code works as expected. It is essential for maintaining code quality and preventing bugs.

**Types of tests**:
1. **Unit tests**: Test individual functions or methods.
2. **Integration tests**: Test how components work together.
3. **Regression tests**: Ensure new changes don't break existing functionality.

**Test framework**: **`pytest`** is the most popular testing framework for Python.

**Test-driven development (TDD)**:
1. Write a failing test.
2. Write the code to make it pass.
3. Refactor the code.

---

### Importance and Real-World Use Cases

- **Why it matters**: Testing prevents bugs, improves code quality, and gives confidence when making changes.

- **Use cases**:
  - A **data engineer** tests data transformation functions.
  - A **data scientist** tests model evaluation functions.
  - A **developer** tests API endpoints.

---

### Step-by-Step Demonstration

```python
# ============== Simple Testing with assert ==============

def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

# Simple assertion tests
assert add(2, 3) == 5
assert subtract(5, 3) == 2
print("All tests passed!")

# ============== Using unittest (built-in) ==============

import unittest

class TestMathFunctions(unittest.TestCase):
    
    def test_add(self):
        self.assertEqual(add(2, 3), 5)
        self.assertEqual(add(-1, 1), 0)
        self.assertEqual(add(0, 0), 0)
    
    def test_subtract(self):
        self.assertEqual(subtract(5, 3), 2)
        self.assertEqual(subtract(0, 5), -5)
        self.assertEqual(subtract(-5, -3), -2)

# ============== Using pytest (Recommended) ==============

"""
# Save as test_math.py

import pytest

def test_add():
    assert add(2, 3) == 5
    assert add(-1, 1) == 0
    assert add(0, 0) == 0

def test_subtract():
    assert subtract(5, 3) == 2
    assert subtract(0, 5) == -5
    assert subtract(-5, -3) == -2

# Run with: pytest test_math.py -v
"""

# ============== Testing Pandas Operations ==============

import pandas as pd

def clean_sales_data(df):
    """Clean sales data by removing duplicates and handling nulls."""
    df = df.drop_duplicates()
    df = df.fillna({'Sales': 0, 'Quantity': 0})
    return df

def test_clean_sales_data():
    # Create test data
    test_df = pd.DataFrame({
        'Product': ['A', 'A', 'B', 'C'],
        'Sales': [100, 100, 200, None],
        'Quantity': [5, 5, 10, None]
    })
    
    # Clean the data
    cleaned = clean_sales_data(test_df)
    
    # Assertions
    assert len(cleaned) == 3  # Duplicate removed
    assert cleaned['Sales'].isnull().sum() == 0  # No nulls
    assert cleaned['Quantity'].isnull().sum() == 0  # No nulls
    print("test_clean_sales_data passed!")

test_clean_sales_data()

# ============== Testing Exceptions ==============

def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b

def test_divide():
    assert divide(10, 2) == 5
    
    # Test exception
    import pytest
    with pytest.raises(ValueError):
        divide(10, 0)
    print("test_divide passed!")

# ============== Testing with Fixtures ==============

"""
# test_with_fixtures.py
import pytest
import pandas as pd

@pytest.fixture
def sample_data():
    """Create sample data for testing."""
    return pd.DataFrame({
        'Product': ['A', 'B', 'C'],
        'Sales': [100, 200, 300],
        'Quantity': [5, 10, 15]
    })

def test_total_sales(sample_data):
    assert sample_data['Sales'].sum() == 600

def test_total_quantity(sample_data):
    assert sample_data['Quantity'].sum() == 30
"""

# ============== Running Tests ==============

"""
# Command line examples:
# Run all tests in the current directory
pytest

# Run with verbose output
pytest -v

# Run a specific test file
pytest test_math.py

# Run a specific test function
pytest test_math.py::test_add

# Run with coverage
pytest --cov=src tests/
"""
```

---

### Practical Examples

- **Example 1**: Testing a data cleaning function.
- **Example 2**: Testing an analysis function.
- **Example 3**: Testing exception handling.

---

### Hands-on Coding Exercises

**Exercise 13.8** – Testing:
```python
# 1. Write a function that processes data.
# 2. Write unit tests for the function.
# 3. Test edge cases (empty data, null values).
# 4. Test exceptions.
# 5. Run the tests with pytest.
```

---

### Mini Quiz

1. What is a unit test?
2. What is the most popular testing framework for Python?
3. What is the difference between a unit test and an integration test?
4. What is a fixture in testing?
5. Why is testing important?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not testing edge cases | Test with empty data, null values, and edge cases |
| Writing tests after the code | Write tests first (TDD) |
| Not running tests regularly | Automate tests in CI/CD |
| Hardcoding test data | Use fixtures for reusable test data |

---

### Interview Questions

1. **What is the purpose of testing in Python?**  
   *Answer*: Testing ensures code works as expected, catches bugs early, and provides confidence when making changes.

2. **What is the difference between `unittest` and `pytest`?**  
   *Answer*: `unittest` is built into Python but more verbose. `pytest` is a third-party framework with simpler syntax and more features.

3. **What is a fixture in `pytest`?**  
   *Answer*: A fixture is a reusable setup for tests, such as creating test data or establishing a database connection.

---

### Assignment and Mini Project

**Assignment 13.7** – Unit testing:
```python
# 1. Write a Python module with at least 3 functions.
# 2. Write unit tests for each function using pytest.
# 3. Test edge cases and exceptions.
# 4. Run the tests and ensure they pass.
```

---

### Summary and Revision Notes

- Testing verifies code correctness.
- `pytest` is the recommended testing framework.
- Unit tests test individual functions.
- Tests should cover edge cases and exceptions.
- Run tests regularly to catch regressions.

---

## Lesson 13.8 – Packaging

### Concept Explanation

**Packaging** is the process of preparing your Python code for distribution. A package allows others to install and use your code easily.

**Key components**:
- **`setup.py`**: The packaging script.
- **`pyproject.toml`**: Modern packaging configuration.
- **`__init__.py`**: Makes a directory a package.
- **`README.md`**: Documentation.

**Why packaging matters**:
- **Reusability**: Share your code with others.
- **Standardisation**: Follows Python packaging standards.
- **Distribution**: Upload to PyPI for installation via `pip`.

---

### Importance and Real-World Use Cases

- **Why it matters**: Packaging allows you to share your code, contribute to open source, and distribute libraries.

- **Use cases**:
  - A **data engineer** packages a data processing library for the team.
  - A **data scientist** packages a model for deployment.
  - A **developer** contributes to open source.

---

### Step-by-Step Demonstration

```python
# ============== Project Structure for Packaging ==============

"""
my_package/
│
├── my_package/              # Package directory
│   ├── __init__.py
│   ├── core.py
│   └── utils.py
│
├── tests/
│   ├── __init__.py
│   └── test_core.py
│
├── README.md
├── LICENSE
├── setup.py
├── pyproject.toml
└── requirements.txt
"""

# ============== setup.py ==============

"""
from setuptools import setup, find_packages

setup(
    name='my_data_package',
    version='0.1.0',
    author='Your Name',
    author_email='your.email@example.com',
    description='A data processing package for analytics',
    long_description=open('README.md').read(),
    long_description_content_type='text/markdown',
    url='https://github.com/username/my_data_package',
    packages=find_packages(),
    install_requires=[
        'pandas>=1.3.0',
        'numpy>=1.21.0',
        'matplotlib>=3.4.0',
        'seaborn>=0.11.0'
    ],
    python_requires='>=3.8',
    classifiers=[
        'Development Status :: 3 - Alpha',
        'Intended Audience :: Developers',
        'License :: OSI Approved :: MIT License',
        'Programming Language :: Python :: 3.8',
        'Programming Language :: Python :: 3.9',
        'Programming Language :: Python :: 3.10',
    ]
)
"""

# ============== pyproject.toml (Modern) ==============

"""
[build-system]
requires = ["setuptools>=61.0", "wheel"]
build-backend = "setuptools.build_meta"

[project]
name = "my_data_package"
version = "0.1.0"
description = "A data processing package for analytics"
authors = [
    {name = "Your Name", email = "your.email@example.com"}
]
license = {text = "MIT"}
readme = "README.md"
requires-python = ">=3.8"
dependencies = [
    "pandas>=1.3.0",
    "numpy>=1.21.0",
]
"""

# ============== __init__.py ==============

"""
# my_package/__init__.py

__version__ = "0.1.0"
__author__ = "Your Name"

from .core import process_data
from .utils import clean_data

__all__ = ['process_data', 'clean_data']
"""

# ============== Building and Installing ==============

"""
# Install in development mode
pip install -e .

# Build the package
python -m build

# Install from source
pip install .

# Upload to PyPI
# pip install twine
# twine upload dist/*
"""

# ============== Example Package Code ==============

# my_package/core.py
def process_data(data, factor=2):
    """Process data by multiplying by a factor."""
    return [x * factor for x in data]

# my_package/utils.py
def clean_data(data):
    """Clean data by removing None values."""
    return [x for x in data if x is not None]
```

```python
# ============== Using the Package ==============

# After installing the package:
from my_package import process_data, clean_data

data = [1, 2, 3, None, 5]
cleaned = clean_data(data)
processed = process_data(cleaned)
print(processed)  # [2, 4, 6, 10]
```

---

### Practical Examples

- **Example 1**: Packaging a data processing library.
- **Example 2**: Packaging a reusable utility module.
- **Example 3**: Publishing a package to PyPI.

---

### Hands-on Coding Exercises

**Exercise 13.9** – Packaging:
```python
# 1. Create a package with at least 2 modules.
# 2. Add a setup.py or pyproject.toml.
# 3. Install the package in development mode.
# 4. Import and use the package.
```

---

### Mini Quiz

1. What is the purpose of `setup.py`?
2. What is the purpose of `__init__.py`?
3. How do you install a package in development mode?
4. What is PyPI?
5. What is the advantage of packaging your code?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not including `__init__.py` | Always include it for packages |
| Hardcoding dependencies | Specify in `install_requires` |
| Not including a README | Always document your package |
| Not specifying Python version | Use `python_requires` |

---

### Interview Questions

1. **How do you package a Python library?**  
   *Answer*: Use `setuptools` with a `setup.py` or `pyproject.toml` file, include an `__init__.py`, and use `pip install -e .` for development.

2. **What is the purpose of PyPI?**  
   *Answer*: PyPI is the Python Package Index, a repository for Python packages that can be installed using `pip`.

3. **How do you install a package from source?**  
   *Answer*: `pip install .` from the package directory.

---

### Assignment and Mini Project

**Assignment 13.8** – Package creation:
```python
# 1. Create a small data analytics package.
# 2. Include at least 3 useful functions.
# 3. Add documentation (README.md and docstrings).
# 4. Create a setup.py or pyproject.toml.
# 5. Install the package and test it.
```

---

### Summary and Revision Notes

- Packaging makes code reusable and distributable.
- `setup.py` defines the package.
- `__init__.py` makes a directory a package.
- Install in development mode: `pip install -e .`.
- Upload to PyPI with `twine`.

---

## Lesson 13.9 – Deployment Basics

### Concept Explanation

**Deployment** is the process of making your code available for use in a production environment. This could be a web service, a scheduled job, or a packaged application.

**Key deployment concepts**:
- **Environment**: Development, staging, production.
- **CI/CD**: Continuous Integration and Continuous Deployment.
- **Containers**: Using Docker for consistent environments.
- **Orchestration**: Managing containers (Kubernetes).
- **Monitoring**: Tracking application health.

**Common deployment targets**:
1. **Cloud VMs**: EC2, GCP Compute Engine.
2. **Serverless**: AWS Lambda, Google Cloud Functions.
3. **Containerised**: Docker + Kubernetes.
4. **Job Schedulers**: Cron, Airflow, Prefect.

---

### Importance and Real-World Use Cases

- **Why it matters**: Deployment is how your code delivers value to users. Without deployment, your code is just a script on your machine.

- **Use cases**:
  - A **data engineer** deploys a daily data pipeline.
  - A **data scientist** deploys a model as an API.
  - A **developer** deploys a web application.

---

### Step-by-Step Demonstration

```python
# ============== Basic Deployment Checklist ==============

"""
Basic Deployment Checklist:
1. ✅ Code is version-controlled (Git).
2. ✅ Requirements are documented (requirements.txt).
3. ✅ Tests pass.
4. ✅ Code is packaged (if needed).
5. ✅ Environment variables are configured.
6. ✅ Logging is set up.
7. ✅ Security is considered.
8. ✅ Monitoring is in place.
"""

# ============== Docker Example (Conceptual) ==============

"""
# Dockerfile
FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "main.py"]
"""

# ============== Python Script for Deployment ==============

import os
import sys
import logging
from pathlib import Path

# Set up logging
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(levelname)s - %(message)s',
    handlers=[
        logging.StreamHandler(sys.stdout),
        logging.FileHandler('deployment.log')
    ]
)
logger = logging.getLogger(__name__)

def deploy():
    """Deploy the application."""
    logger.info("Starting deployment process...")
    
    # Check environment variables
    required_vars = ['DB_HOST', 'DB_NAME', 'API_KEY']
    missing_vars = []
    for var in required_vars:
        if not os.getenv(var):
            missing_vars.append(var)
    
    if missing_vars:
        logger.error(f"Missing environment variables: {', '.join(missing_vars)}")
        sys.exit(1)
    
    # Run tests
    logger.info("Running tests...")
    import subprocess
    test_result = subprocess.run(['pytest', '-v'], capture_output=True, text=True)
    if test_result.returncode != 0:
        logger.error("Tests failed")
        logger.error(test_result.stdout)
        sys.exit(1)
    logger.info("Tests passed")
    
    # Build the application
    logger.info("Building application...")
    # subprocess.run(['python', 'setup.py', 'build'])
    
    # Deploy
    logger.info("Deploying to production...")
    # deployment logic here
    
    logger.info("Deployment completed successfully!")
    return True

# ============== Environment Configuration ==============

# Using Pydantic for configuration (optional)
"""
from pydantic_settings import BaseSettings

class Settings(BaseSettings):
    db_host: str
    db_name: str
    api_key: str
    debug: bool = False
    
    class Config:
        env_file = ".env"

settings = Settings()
print(f"Connecting to {settings.db_host}/{settings.db_name}")
"""

# ============== Health Check ==============

def health_check():
    """Simple health check endpoint."""
    import time
    return {
        'status': 'healthy',
        'timestamp': time.time(),
        'version': '1.0.0'
    }

# ============== Main Entry Point ==============

def main():
    """Main entry point for the application."""
    logger.info("Application starting...")
    
    # Configuration
    debug = os.getenv('DEBUG', 'False').lower() == 'true'
    
    if debug:
        logger.setLevel(logging.DEBUG)
        logger.debug("Debug mode enabled")
    
    try:
        # Run the application
        # app.run()
        logger.info("Application running")
        
        # Health check
        health = health_check()
        logger.info(f"Health: {health}")
        
    except Exception as e:
        logger.error(f"Application failed: {e}")
        sys.exit(1)

if __name__ == "__main__":
    main()
```

**Deployment with CI/CD (GitHub Actions)**:

```yaml
# .github/workflows/deploy.yml
"""
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.10'
      - name: Install dependencies
        run: |
          pip install -r requirements.txt
      - name: Run tests
        run: |
          pytest
      - name: Deploy to production
        run: |
          python deploy.py
"""
```

---

### Practical Examples

- **Example 1**: Deploying a data pipeline with cron.
- **Example 2**: Deploying a model as a REST API.
- **Example 3**: Using Docker for consistent deployment.

---

### Hands-on Coding Exercises

**Exercise 13.10** – Deployment preparation:
```python
# 1. Write a deployment script with logging.
# 2. Check for required environment variables.
# 3. Run tests before deployment.
# 4. Implement a health check.
# 5. Use environment variables for configuration.
```

---

### Mini Quiz

1. What is deployment?
2. What is CI/CD?
3. Why are environment variables important in deployment?
4. What is the purpose of a health check?
5. What is Docker used for?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Hardcoding configuration | Use environment variables |
| Deploying without testing | Run tests before deployment |
| Not logging | Log key events for debugging |
| No health checks | Implement health checks |
| Manual deployment | Automate with CI/CD |

---

### Interview Questions

1. **What is the difference between development, staging, and production environments?**  
   *Answer*: Development is for coding, staging is for testing, and production is for live users.

2. **How do you handle configuration in deployment?**  
   *Answer*: Use environment variables or configuration files that are excluded from version control.

3. **What is the purpose of a health check?**  
   *Answer*: A health check monitors whether the application is running correctly, allowing monitoring systems to detect failures.

---

### Assignment and Mini Project

**Assignment 13.9** – Deployment setup:
```python
# 1. Set up a project with environment variables.
# 2. Add a deployment script with logging.
# 3. Configure health checks.
# 4. Add a Dockerfile for containerisation.
# 5. Document the deployment process.
```

---

### Summary and Revision Notes

- Deployment makes code available in production.
- Use environment variables for configuration.
- Run tests before deployment.
- Implement health checks.
- Automate with CI/CD.
- Use containers (Docker) for consistency.

---

## Final Phase 13 Assessment

Now that you have completed all lessons, test your overall understanding.

### Self-Evaluation Checklist
- [ ] I can write clean, PEP 8-compliant Python code.
- [ ] I can organise a project with a standard structure.
- [ ] I can create and use virtual environments.
- [ ] I can use Git and GitHub for version control.
- [ ] I can optimise Python code for performance.
- [ ] I can implement logging in my applications.
- [ ] I can write unit tests with pytest.
- [ ] I can package Python code for distribution.
- [ ] I can prepare code for deployment.

---

### Answers to Mini Quizzes

**Lesson 13.1**: 1. Python's style guide. 2. snake_case. 3. To document functions. 4. 79 characters. 5. To indicate expected data types.

**Lesson 13.2**: 1. Makes a directory a Python package. 2. For modularity and maintainability. 3. Python dependencies. 4. Excludes files from Git. 5. `tests/` directory.

**Lesson 13.3**: 1. Isolated Python environment. 2. `python -m venv venv`. 3. `venv\Scripts\activate`. 4. Lists dependencies. 5. `venv` is built-in; `conda` is cross-platform.

**Lesson 13.4**: 1. Version control. 2. `git add`. 3. `git branch` or `git checkout -b`. 4. Request to merge changes. 5. Excludes files from Git.

**Lesson 13.5**: 1. Applying operations to entire arrays. 2. Vectorized operations in C. 3. Stores results for reuse. 4. Profiles code execution. 5. Use appropriate data types.

**Lesson 13.6**: 1. DEBUG, INFO, WARNING, ERROR, CRITICAL. 2. For debugging and monitoring. 3. `FileHandler`. 4. `logger.exception()`. 5. Logging is configurable and production-ready.

**Lesson 13.7**: 1. Tests individual functions. 2. `pytest`. 3. Unit tests test components; integration tests test interactions. 4. Reusable setup for tests. 5. Prevents bugs.

**Lesson 13.8**: 1. Defines package metadata. 2. Makes a directory a package. 3. `pip install -e .`. 4. Python Package Index. 5. Reusability and distribution.

**Lesson 13.9**: 1. Making code available in production. 2. Continuous Integration/Continuous Deployment. 3. For configuration without hardcoding. 4. Monitors application health. 5. Containerisation.

---

**Congratulations!** You have completed all 13 phases of this comprehensive Python for Data Analytics curriculum. You are now a professional-grade data analyst/engineer with skills in:

- Python programming.
- Data manipulation and analysis.
- Data visualisation.
- Statistics and machine learning.
- SQL and databases.
- Automation and scheduling.
- Professional development practices.

You are ready to start your career in data analytics. Keep learning, keep building, and keep growing!

**Best of luck in your data analytics career! 🚀**


---




<br/><br/><br/>
<center> <b>Happy Learning! 😊</b> </center>