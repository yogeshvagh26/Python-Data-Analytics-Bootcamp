# Phase 9: SQL with Python

Welcome to **Phase 9** – where the worlds of SQL and Python collide! Throughout this curriculum, you have mastered Python for data manipulation (Pandas) and visualisation. Now, you will learn how to seamlessly integrate **SQL (Structured Query Language)** into your Python workflows.

SQL is the universal language for interacting with relational databases. In the real world, most enterprise data lives in databases like PostgreSQL, MySQL, SQL Server, or Oracle. Being able to connect Python to these databases, run queries, and pull data directly into Pandas is an absolute must-have skill for any data professional.

In this phase, we will use **SQLite** – a lightweight, serverless, file-based SQL database that comes built-in with Python. The concepts you learn here (connections, cursors, queries, CRUD operations) will transfer directly to any other SQL database (with minor syntax changes).

Let’s bridge the gap between Python and the world of relational databases!

---

## Lesson 9.1 – Introduction to SQLite

### Concept Explanation

**SQLite** is a lightweight, file-based relational database management system (RDBMS). Unlike client-server databases (like PostgreSQL or MySQL), SQLite is **serverless** and **self-contained**. The entire database is stored in a single file on your hard drive.

**Why SQLite for learning**:
- It comes built-in with Python (`import sqlite3`), so no setup is needed.
- It supports standard SQL syntax (SQL-92).
- It's perfect for local development, testing, and small to medium applications.
- The patterns (connect, cursor, execute, commit, close) are identical for all databases.

**What is SQL?**
SQL is the language used to create, read, update, and delete data in relational databases.

**Key SQL operations (CRUD)**:
- **C**reate (`INSERT`)
- **R**ead (`SELECT`)
- **U**pdate (`UPDATE`)
- **D**elete (`DELETE`)

---

### Importance and Real-World Use Cases

- **Why it matters**: Most companies store their transactional and operational data in SQL databases. Analysts need to extract this data into Python for deeper analysis and visualisation. SQL also provides powerful aggregation and joining capabilities that complement Pandas.

- **Use cases**:
  - A **data analyst** connects to a company's PostgreSQL database to pull sales data into a Pandas DataFrame for analysis.
  - A **data scientist** extracts a sample of customer data from a SQL server for building a machine learning model.
  - A **data engineer** writes Python scripts that perform ETL (Extract, Transform, Load) by querying SQL databases and loading the results into a data warehouse.

---

### Step-by-Step Demonstration

**Creating your first SQLite database and table**:

```python
import sqlite3

# 1. Connect to a database (creates the file if it doesn't exist)
# 'company.db' is the file name. Using ':memory:' creates a temporary in-memory database.
conn = sqlite3.connect('company.db')

# 2. Create a cursor object (used to execute SQL commands)
cursor = conn.cursor()

# 3. Execute SQL commands (CREATE TABLE)
cursor.execute('''
CREATE TABLE IF NOT EXISTS employees (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    department TEXT,
    salary REAL
)
''')

# 4. Commit the changes (save them to the file)
conn.commit()

# 5. Close the connection
conn.close()

print("Database and table created successfully!")
```

**Checking the database file**:
```python
import os
print(f"Database file exists: {os.path.exists('company.db')}")
```

---

### Practical Examples

- **Example 1**: Creating a local SQLite database for a personal project.
- **Example 2**: Setting up a test environment for SQL queries without needing a server.

---

### Hands-on Coding Exercises

**Exercise 9.1** – Create a database:
```python
# 1. Connect to a database called 'sales.db'
# 2. Create a table called 'products' with columns:
#    - id (INTEGER PRIMARY KEY)
#    - name (TEXT)
#    - price (REAL)
#    - category (TEXT)
# 3. Commit and close the connection
# 4. Print a confirmation message
```

---

### Mini Quiz

1. What does SQLite stand for? (It’s just a name!)
2. What module do you import to use SQLite in Python?
3. What is the purpose of a cursor in SQLite?
4. What does the `IF NOT EXISTS` clause do in a `CREATE TABLE` statement?
5. What is the difference between `conn.commit()` and not committing?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to commit changes (`conn.commit()`) | Always call `commit()` after `INSERT`, `UPDATE`, `DELETE` |
| Forgetting to close the connection | Use `conn.close()` or use a `with` statement (context manager) |
| Creating a table without checking if it exists | Use `IF NOT EXISTS` to avoid errors |
| Hardcoding file paths for databases | Use environment variables or relative paths for portability |

---

### Interview Questions

1. **What is SQLite and how does it differ from MySQL?**  
   *Answer*: SQLite is a serverless, file-based database, while MySQL is a client-server database. SQLite is lightweight and great for local storage, whereas MySQL is used for large-scale production applications.

2. **Why would you use SQLite in a data analytics project?**  
   *Answer*: To store intermediate results, create a local cache of data, or practice SQL without setting up a server.

3. **What is the role of a cursor in database programming?**  
   *Answer*: A cursor acts as a pointer or handle to execute SQL statements and fetch results from the database.

---

### Assignment and Mini Project

**Assignment 9.1** – Schema design:
```python
# Create a database called 'school.db'
# Create two tables:
# 1. students: id (INTEGER), name (TEXT), age (INTEGER), grade (REAL)
# 2. courses: id (INTEGER), course_name (TEXT), teacher (TEXT)
# Ensure the tables are only created if they don't exist already.
# Print the tables created.
```

---

### Summary and Revision Notes

- SQLite is built into Python (`import sqlite3`).
- `sqlite3.connect('file.db')` connects to or creates a database.
- `cursor = conn.cursor()` creates a cursor for SQL execution.
- `cursor.execute(sql_string)` runs SQL commands.
- `conn.commit()` saves changes.
- `conn.close()` closes the connection.

---

## Lesson 9.2 – Connecting to Databases

### Concept Explanation

While SQLite is our primary focus, in the real world you will connect to various databases. The connection process is conceptually the same, but requires different drivers/libraries.

**Common databases and their Python drivers**:

| **Database** | **Python Library** | **Connection Example** |
|--------------|--------------------|------------------------|
| **SQLite** | `sqlite3` (built-in) | `sqlite3.connect('file.db')` |
| **PostgreSQL** | `psycopg2` or `psycopg` | `psycopg2.connect(host='localhost', dbname='db', user='user', password='pass')` |
| **MySQL** | `mysql-connector-python` or `pymysql` | `mysql.connector.connect(host='localhost', user='user', password='pass', database='db')` |
| **SQL Server** | `pyodbc` | `pyodbc.connect('DRIVER={ODBC Driver 17}; SERVER=localhost; DATABASE=db; UID=user; PWD=pass')` |

**Key concepts**:
- **Connection Object**: Represents the session with the database.
- **Connection Parameters**: Host, port, username, password, database name.
- **Connection String**: A single string that encapsulates all parameters (common for ODBC).

**Secure practices**:
- Never hardcode credentials in your script. Use environment variables or config files.

---

### Importance and Real-World Use Cases

- **Why it matters**: Understanding how to configure connections allows you to tap into any enterprise data source.

- **Use cases**:
  - Connecting to an Amazon Redshift data warehouse using `psycopg2` to pull marketing data.
  - Connecting to an on-premise SQL Server via `pyodbc` to extract financial reports.

---

### Step-by-Step Demonstration

**Connecting to SQLite (Recap)**:
```python
import sqlite3

# Standard connection
conn = sqlite3.connect('company.db')
# Optionally, check if connection is open
print(f"Connection opened: {conn.total_changes}")  # Total changes since connection
```

**Connecting to SQLite using a Context Manager (Recommended)**:
```python
with sqlite3.connect('company.db') as conn:
    cursor = conn.cursor()
    cursor.execute("SELECT name FROM sqlite_master WHERE type='table';")
    tables = cursor.fetchall()
    print(f"Tables in company.db: {tables}")
# Connection is automatically closed after the 'with' block
```

**Connecting to PostgreSQL (Conceptual - requires psycopg2)**:
```python
# Uncomment to use (requires pip install psycopg2-binary)
# import psycopg2
# import os
#
# conn = psycopg2.connect(
#     host=os.getenv('DB_HOST', 'localhost'),
#     dbname=os.getenv('DB_NAME', 'sales_db'),
#     user=os.getenv('DB_USER', 'admin'),
#     password=os.getenv('DB_PASSWORD', 'secret')
# )
# cursor = conn.cursor()
```

**Using Environment Variables (Best Practice)**:
```python
import os

# In the terminal: export DB_FILE='company.db'
# On Windows: set DB_FILE=company.db
db_path = os.getenv('DB_FILE', 'default.db')
print(f"Connecting to: {db_path}")
conn = sqlite3.connect(db_path)
```

---

### Practical Examples

- **Example 1**: Using a context manager (`with`) to automatically handle connection closure.
- **Example 2**: Reading credentials from environment variables for security.

---

### Hands-on Coding Exercises

**Exercise 9.2** – Context manager connection:
```python
# 1. Use the 'with' statement to connect to your 'company.db'
# 2. Inside the block, create a cursor and print the list of tables
# 3. Verify that the connection is automatically closed after the block
```

---

### Mini Quiz

1. What is the recommended way to handle database connections to ensure they are always closed?
2. Which Python library is used to connect to PostgreSQL?
3. Why should you not hardcode credentials into your script?
4. What does `os.getenv` do?
5. What is the difference between `sqlite3.connect('company.db')` and `sqlite3.connect(':memory:')`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Hardcoding passwords and usernames | Use environment variables or a secrets manager |
| Forgetting to close connections | Use `with` statements |
| Not handling connection errors | Use `try-except` to catch `sqlite3.Error` |
| Using the same connection for multiple operations without isolation | Create new connections or use transactions wisely |

---

### Interview Questions

1. **How would you connect to a PostgreSQL database from Python?**  
   *Answer*: Using the `psycopg2` library and the `psycopg2.connect()` function with appropriate host, dbname, user, and password parameters.

2. **What is the advantage of using a connection context manager (`with`)?**  
   *Answer*: It automatically closes the connection when exiting the block, even if an error occurs, preventing resource leaks.

3. **How do you securely manage database credentials in a Python application?**  
   *Answer*: By using environment variables (e.g., `os.getenv`), configuration files excluded from version control, or a dedicated secrets management service.

---

### Assignment and Mini Project

**Assignment 9.2** – Connection manager:
```python
# 1. Create a function called `get_db_connection(db_file)` that returns a connection.
# 2. Create a function called `execute_query(db_file, sql_query)` that uses the context manager to:
#    - Connect to the database.
#    - Execute the provided SQL query.
#    - Fetch all results and return them.
# 3. Test it by fetching all table names from 'company.db'.
```

---

### Summary and Revision Notes

- `sqlite3.connect()` connects to SQLite.
- Use `with` for automatic resource cleanup.
- Use environment variables (`os.getenv`) for credentials.
- Different databases require different Python libraries (drivers).

---

## Lesson 9.3 – Executing SQL Queries

### Concept Explanation

Once you have a connection, you execute SQL queries using a **cursor**. You can execute `SELECT` queries to read data, or `INSERT`, `UPDATE`, `DELETE` queries to modify data.

**Key methods**:
- `cursor.execute(sql)`: Executes a single SQL statement.
- `cursor.executemany(sql, parameters)`: Executes the same SQL statement with many parameter sets (efficient for bulk inserts).
- `cursor.fetchall()`: Retrieves all rows from the executed query.
- `cursor.fetchone()`: Retrieves the next row.
- `cursor.fetchmany(size)`: Retrieves the next `size` rows.

**Parameterized Queries (Security)**:
Never use string concatenation to build SQL queries. This makes you vulnerable to **SQL Injection**.
- **In SQLite**, use `?` as a placeholder.
- Example: `cursor.execute("SELECT * FROM employees WHERE name = ?", ('Alice',))`

---

### Importance and Real-World Use Cases

- **Why it matters**: Executing queries efficiently and safely is the core of database interaction. Parameterized queries are non-negotiable for security.

- **Use cases**:
  - Inserting thousands of rows using `executemany`.
  - Fetching data in chunks using `fetchmany` to avoid memory issues.
  - Safely filtering data based on user input.

---

### Step-by-Step Demonstration

**Inserting Data (Single row)**:
```python
import sqlite3

with sqlite3.connect('company.db') as conn:
    cursor = conn.cursor()

    # Insert a single employee
    cursor.execute('''
    INSERT INTO employees (name, department, salary)
    VALUES (?, ?, ?)
    ''', ('Alice Johnson', 'Engineering', 75000.00))

    # You MUST commit to save the changes
    conn.commit()
    print("Employee inserted successfully!")
```

**Inserting Data (Multiple rows using executemany)**:
```python
with sqlite3.connect('company.db') as conn:
    cursor = conn.cursor()
    
    employees_data = [
        ('Bob Smith', 'Sales', 65000),
        ('Carol White', 'Marketing', 72000),
        ('David Brown', 'Engineering', 82000)
    ]
    
    cursor.executemany('''
    INSERT INTO employees (name, department, salary)
    VALUES (?, ?, ?)
    ''', employees_data)
    
    conn.commit()
    print(f"{len(employees_data)} employees inserted!")
```

**Reading Data (SELECT)**:
```python
with sqlite3.connect('company.db') as conn:
    cursor = conn.cursor()

    # 1. fetchone()
    cursor.execute("SELECT * FROM employees")
    row = cursor.fetchone()
    print(f"First employee: {row}")

    # 2. fetchmany(2)
    rows = cursor.fetchmany(2)
    print(f"Next 2 employees: {rows}")

    # 3. fetchall()
    cursor.execute("SELECT * FROM employees")
    all_rows = cursor.fetchall()
    print(f"All employees: {all_rows}")
```

**Using Parameterized Queries (Filtering)**:
```python
def get_employees_by_department(dept_name):
    with sqlite3.connect('company.db') as conn:
        cursor = conn.cursor()
        cursor.execute("SELECT * FROM employees WHERE department = ?", (dept_name,))
        return cursor.fetchall()

print("Engineering employees:", get_employees_by_department('Engineering'))
```

**Fetching as Dictionary (Row Factory)**:
```python
def get_as_dict():
    with sqlite3.connect('company.db') as conn:
        # This makes rows accessible by column name
        conn.row_factory = sqlite3.Row
        cursor = conn.cursor()
        cursor.execute("SELECT id, name, salary FROM employees")
        rows = cursor.fetchall()
        for row in rows:
            print(f"ID: {row['id']}, Name: {row['name']}, Salary: {row['salary']}")

get_as_dict()
```

---

### Practical Examples

- **Example 1**: Bulk uploading CSV data to SQLite using `executemany`.
- **Example 2**: Writing a function to query a table based on a dynamic `WHERE` clause safely.

---

### Hands-on Coding Exercises

**Exercise 9.3** – CRUD Read:
```python
# 1. Insert 5 new products into the 'products' table (created in the previous assignment).
# 2. Write a query to select all products with a price greater than a given threshold.
# 3. Fetch the results and print them in a formatted way.
# 4. Use parameterized queries to avoid SQL injection.
```

---

### Mini Quiz

1. What is the difference between `fetchone()` and `fetchall()`?
2. Why should you use parameterized queries (`?` placeholders)?
3. What is the purpose of `executemany`?
4. What does `conn.row_factory = sqlite3.Row` do?
5. Is `commit()` required after a `SELECT` statement? Why?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Concatenating strings to build SQL queries | Always use `?` placeholders |
| Forgetting to `commit()` after `INSERT/UPDATE/DELETE` | Commit changes explicitly |
| Using `fetchall()` on a huge dataset (memory crash) | Use `fetchmany()` or iterate over the cursor |
| Assuming `fetchall()` returns a list of dicts | Use `row_factory` for dict access |

---

### Interview Questions

1. **How do you prevent SQL injection in Python?**  
   *Answer*: By using parameterized queries with placeholders (`?` for SQLite) and passing the values as a tuple or list to `execute()`.

2. **What is the advantage of `executemany` over multiple `execute` calls?**  
   *Answer*: `executemany` sends the SQL statement once and then batches the data, which significantly improves performance for bulk inserts/updates.

3. **How do you read a large result set without running out of memory?**  
   *Answer*: By using `fetchmany(size)` in a loop or iterating directly over the cursor.

---

### Assignment and Mini Project

**Assignment 9.3** – Query executor:
```python
# 1. Create a function `fetch_data(db_file, query, params=())` that executes a parameterized query and returns `fetchall()`.
# 2. Create a function `insert_data(db_file, query, data)` that inserts data using `executemany`.
# 3. Insert a list of 10 sample employees.
# 4. Fetch employees earning more than 60,000 and display their names.
```

---

### Summary and Revision Notes

- `execute()` runs a SQL query.
- Use `?` placeholders for parameters.
- `fetchone()` gets one row, `fetchmany(n)` gets `n` rows, `fetchall()` gets all rows.
- `executemany()` is for bulk operations.
- Always commit after modifying data.

---

## Lesson 9.4 – Importing SQL Data into Pandas

### Concept Explanation

This is the **killer feature** for data analysts. Instead of exporting SQL results to CSV and then loading them into Python, you can load SQL query results **directly** into a Pandas DataFrame using `pandas.read_sql_query()`.

**Key functions**:
- `pd.read_sql_query(sql, con, params=...)`: Executes a SQL query and returns a DataFrame.
- `pd.read_sql_table(table_name, con, schema=...)`: Reads an entire table (without writing SQL). Ideal for simple extractions.
- `pd.read_sql(sql, con)`: A wrapper that can handle both queries and table names.

**Why this is huge**:
- You can leverage SQL's powerful aggregation and joining capabilities to pre-process data, then bring the clean, aggregated result into Pandas for plotting or further analysis.

---

### Importance and Real-World Use Cases

- **Why it matters**: Data analysts often need to query large databases. SQL databases are optimised for filtering and aggregation (much faster than Pandas for large datasets). Pulling pre-aggregated data into Pandas saves memory and time.

- **Use cases**:
  - A **data analyst** writes a complex SQL query joining 5 tables to create a sales summary by region, loads it into Pandas, and creates a dashboard.
  - A **data scientist** writes a SQL query to sample 10% of a 100-million-row table and loads it into Pandas for model prototyping.

---

### Step-by-Step Demonstration

```python
import sqlite3
import pandas as pd

# Create a connection
conn = sqlite3.connect('company.db')

# 1. Reading a simple query into a DataFrame
df_employees = pd.read_sql_query("SELECT * FROM employees", conn)
print("Employees DataFrame:")
print(df_employees.head())

# 2. Reading with parameters (filtering)
df_high_earners = pd.read_sql_query(
    "SELECT * FROM employees WHERE salary > ?",
    conn,
    params=(70000,)
)
print("\nHigh earners (salary > 70000):")
print(df_high_earners)

# 3. Reading an aggregated query (JOIN and GROUP BY)
# First, let's create a departments table and populate it for this example.
cursor = conn.cursor()
cursor.execute("DROP TABLE IF EXISTS departments")
cursor.execute("CREATE TABLE departments (id INTEGER PRIMARY KEY, name TEXT, location TEXT)")
cursor.executemany("INSERT INTO departments (id, name, location) VALUES (?, ?, ?)", [
    (1, 'Engineering', 'Building A'),
    (2, 'Sales', 'Building B'),
    (3, 'Marketing', 'Building C')
])
conn.commit()

# Join employees with departments
df_joined = pd.read_sql_query("""
    SELECT e.name, e.salary, d.name as dept_name, d.location
    FROM employees e
    LEFT JOIN departments d ON e.department = d.name
""", conn)

print("\nJoined Employee-Department Data:")
print(df_joined)

# 4. Using `pd.read_sql_table` (simpler for whole tables)
df_depts = pd.read_sql_table('departments', conn)
print("\nDepartments Table via read_sql_table:")
print(df_depts)

# 5. Customizing the index
df_with_index = pd.read_sql_query("SELECT id, name, salary FROM employees", conn, index_col='id')
print("\nEmployees with ID as index:")
print(df_with_index)

# Close connection (if not using 'with')
conn.close()
```

**Practical Pipeline**:
```python
# Simulating a production ETL step
def load_sales_summary():
    conn = sqlite3.connect('company.db')
    query = """
    SELECT 
        department, 
        COUNT(*) as emp_count, 
        AVG(salary) as avg_salary
    FROM employees
    GROUP BY department
    ORDER BY avg_salary DESC
    """
    df = pd.read_sql_query(query, conn)
    conn.close()
    return df

summary = load_sales_summary()
print("\nDepartment Summary:")
print(summary)
```

---

### Practical Examples

- **Example 1**: Pulling a fact table joined with dimension tables directly into a Pandas DataFrame for plotting.
- **Example 2**: Scheduling a Python script that runs a SQL query, loads it into Pandas, and exports the results to Excel.

---

### Hands-on Coding Exercises

**Exercise 9.4** – SQL to Pandas:
```python
# 1. Connect to 'company.db'
# 2. Use pd.read_sql_query to fetch employees with salary > 60000
# 3. Calculate the average salary of employees per department using Pandas (groupby)
# 4. Print the average salary per department
# 5. Plot a bar chart of average salary per department
```

---

### Mini Quiz

1. Which Pandas function is used to execute a SQL query and return a DataFrame?
2. How do you pass parameters to a SQL query in `pd.read_sql_query`?
3. What is the advantage of using SQL for aggregation over Pandas for very large datasets?
4. What is the difference between `pd.read_sql_query` and `pd.read_sql_table`?
5. How do you set a specific column as the index of the resulting DataFrame?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Loading entire tables into Pandas when you only need a few columns | Select only the columns you need in the SQL query |
| Not using parameters (`params=`) in `read_sql_query` | Use `params` to prevent injection and parse correct types |
| Forgetting to close the connection after loading | Use `with sqlite3.connect(...) as conn:` |
| Performing complex row-wise operations in Pandas that could be done in SQL | Push filtering, joins, and aggregations to the SQL layer |

---

### Interview Questions

1. **How do you connect a Pandas DataFrame to a database table?**  
   *Answer*: You can use `pd.read_sql_query()` to execute a query and retrieve data, or `pd.read_sql_table()` to fetch an entire table. You can also use `df.to_sql()` to write a DataFrame back to the database (covered in the next lesson).

2. **What is the benefit of aggregating data in SQL before loading it into Pandas?**  
   *Answer*: SQL databases are highly optimised for aggregation and indexing. Aggregating in SQL reduces the amount of data transferred over the network and into memory, significantly improving performance.

3. **Can you write a DataFrame back to a SQL database?**  
   *Answer*: Yes, using the `df.to_sql(table_name, con)` method.

---

### Assignment and Mini Project

**Assignment 9.4** – Sales report pipeline:
```python
# 1. Create a 'sales' table in a SQLite database with columns: sale_id, product, region, amount, sale_date.
# 2. Populate it with 50 random sales records.
# 3. Write a SQL query that calculates total sales by region and product.
# 4. Load the result into a Pandas DataFrame.
# 5. Use Matplotlib to create a bar chart showing total sales by region.
# 6. Save the DataFrame to a CSV file.
```

---

### Summary and Revision Notes

- `pd.read_sql_query(sql, conn)` loads SQL results into a DataFrame.
- Use the `params` argument for safe parameterised queries.
- Push heavy lifting (aggregations, joins) to SQL to reduce memory usage.
- Use `pd.read_sql_table` for quick whole-table reads.

---

## Lesson 9.5 – CRUD Operations

### Concept Explanation

**CRUD** stands for **Create, Read, Update, Delete**. While you will mostly "Read" as an analyst, understanding how to Create, Update, and Delete data programmatically is essential for building robust data pipelines or data validation tools.

**Key points**:
- **Create**: `INSERT INTO` (covered in 9.3).
- **Read**: `SELECT` (covered in 9.3 & 9.4).
- **Update**: `UPDATE table SET column = value WHERE condition`.
- **Delete**: `DELETE FROM table WHERE condition`.

**Transaction Control**:
- `conn.execute("BEGIN")` (SQLite starts transactions automatically).
- `conn.commit()` permanently saves changes.
- `conn.rollback()` undoes changes if an error occurs.

---

### Importance and Real-World Use Cases

- **Why it matters**: You might need to:
  - Clean up duplicate records (DELETE).
  - Correct erroneous data (UPDATE).
  - Write a Python script to migrate data from one database to another (CREATE/INSERT).

- **Use cases**:
  - A **data engineer** writes a Python script that updates daily batch loads.
  - An **analyst** creates a temporary table to store intermediate results.

---

### Step-by-Step Demonstration

```python
import sqlite3

def get_connection():
    return sqlite3.connect('company.db')

# 1. UPDATE operation
def update_salary(employee_id, new_salary):
    conn = get_connection()
    cursor = conn.cursor()
    try:
        cursor.execute("UPDATE employees SET salary = ? WHERE id = ?", (new_salary, employee_id))
        conn.commit()
        print(f"Employee {employee_id} salary updated to {new_salary}")
    except sqlite3.Error as e:
        print(f"Error occurred: {e}")
        conn.rollback()
    finally:
        conn.close()

update_salary(1, 85000)

# Verify the update
conn = get_connection()
df = pd.read_sql_query("SELECT id, name, salary FROM employees WHERE id = 1", conn)
conn.close()
print(df)

# 2. DELETE operation (careful!)
def delete_employee(employee_id):
    conn = get_connection()
    cursor = conn.cursor()
    try:
        cursor.execute("DELETE FROM employees WHERE id = ?", (employee_id,))
        conn.commit()
        print(f"Employee {employee_id} deleted successfully.")
    except sqlite3.Error as e:
        print(f"Error: {e}")
        conn.rollback()
    finally:
        conn.close()

# Let's add Bob first to delete him
conn = get_connection()
conn.execute("INSERT INTO employees (name, department, salary) VALUES (?, ?, ?)", ('Bob Temp', 'HR', 40000))
conn.commit()
conn.close()

delete_employee(4)  # Assuming Bob's ID is 4 (adjust based on your data)

# 3. Using df.to_sql (Create table from DataFrame)
print("\n--- Creating Table from DataFrame ---")
# Create a new DataFrame
new_data = pd.DataFrame({
    'name': ['Zara', 'Tim'],
    'department': ['Finance', 'Finance'],
    'salary': [90000, 88000]
})

conn = get_connection()
# if_exists='append' adds to the table, 'replace' drops and recreates
new_data.to_sql('employees', conn, if_exists='append', index=False)
conn.close()

# Verify the new data
conn = get_connection()
df_check = pd.read_sql_query("SELECT * FROM employees WHERE department = 'Finance'", conn)
conn.close()
print("Finance department employees:")
print(df_check)
```

**Transaction Example (Rollback)**:
```python
def safe_update_bonuses(bonus_percent):
    conn = get_connection()
    cursor = conn.cursor()
    try:
        # Attempt to update all salaries
        cursor.execute("UPDATE employees SET salary = salary * ?", (1 + bonus_percent,))
        
        # Simulate a check: if any salary goes above 200k, rollback
        cursor.execute("SELECT COUNT(*) FROM employees WHERE salary > 200000")
        count = cursor.fetchone()[0]
        if count > 0:
            raise ValueError(f"Transaction would create {count} salaries > 200k. Rolling back.")
        
        conn.commit()
        print(f"Bonuses applied successfully!")
    except Exception as e:
        print(f"Error: {e}")
        conn.rollback()
    finally:
        conn.close()

safe_update_bonuses(0.5)  # 50% bonus might trigger the guard
```

---

### Practical Examples

- **Example 1**: Updating product prices based on a new pricing list provided in an Excel file (load Excel -> loop -> UPDATE).
- **Example 2**: Deleting temporary staging tables after a pipeline completes.

---

### Hands-on Coding Exercises

**Exercise 9.5** – Update and Delete:
```python
# 1. Insert 3 new employees.
# 2. Write a function that updates the salary of an employee by ID.
# 3. Write a function that deletes an employee by ID.
# 4. Test both functions.
# 5. Write a function that increases the salary of all employees in a specific department by a given percentage.
```

---

### Mini Quiz

1. What does `conn.rollback()` do?
2. What is the difference between `if_exists='append'` and `if_exists='replace'` in `df.to_sql`?
3. Why is `try-except` important in update/delete operations?
4. How do you safely increase every employee's salary by 10%?
5. Can you use `df.to_sql` to create a new table? How?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting the `WHERE` clause in `UPDATE` or `DELETE` (updates all rows!) | Always double-check your `WHERE` clause; perhaps test with `SELECT` first |
| Not wrapping multiple updates in a transaction | Use transactions to ensure all-or-nothing execution |
| Using `df.to_sql` with `if_exists='replace'` on a production table | Use `append` for production; `replace` is dangerous |

---

### Interview Questions

1. **How do you perform a transaction in SQLite?**  
   *Answer*: Transactions are started automatically, but you can control them with `conn.commit()` and `conn.rollback()`.

2. **What is the risk of an `UPDATE` without a `WHERE` clause?**  
   *Answer*: It will update every row in the table, which could be catastrophic in a production environment.

3. **How do you write a DataFrame to a SQL table?**  
   *Answer*: Using the `df.to_sql(table_name, connection)` method.

---

### Assignment and Mini Project

**Assignment 9.5** – Data cleaning script:
```python
# 1. Load a CSV file (or create a small DataFrame) with some dirty data (e.g., negative salaries, duplicate IDs).
# 2. Write to a SQL table.
# 3. Write Python functions that:
#    - DELETE rows with negative salaries.
#    - UPDATE rows where the department is NULL to 'Unknown'.
# 4. Check the table after each operation.
```

---

### Summary and Revision Notes

- **CREATE**: `df.to_sql()` or `INSERT`.
- **READ**: `pd.read_sql_query()`.
- **UPDATE**: `cursor.execute("UPDATE ... WHERE ...")`.
- **DELETE**: `cursor.execute("DELETE ... WHERE ...")`.
- **Transactions**: `commit()` to save, `rollback()` to undo.

---

## Lesson 9.6 – Data Analysis with SQL

### Concept Explanation

This lesson combines everything. SQL is incredibly powerful for data analysis. By integrating SQL with Python, you can use the best of both worlds: SQL's robust querying capabilities and Python's advanced analysis and visualisation libraries.

**Advanced SQL Features for Analysis**:
- **JOINs**: Combine multiple tables to get a complete picture.
- **GROUP BY**: Aggregate data (e.g., total sales per region).
- **Window Functions**: Ranking, moving averages, cumulative sums (e.g., `ROW_NUMBER()`, `RANK()`, `SUM(...) OVER(...)`).
- **Subqueries / CTEs (Common Table Expressions)**: Write modular, readable complex queries.

**Typical Workflow**:
1. Write a complex SQL query (possibly with CTEs).
2. Execute it and load the result into Pandas.
3. Perform further analysis, statistical tests, or visualisation in Python.
4. Optionally write results back to a database.

---

### Importance and Real-World Use Cases

- **Why it matters**: This is the core of the modern data stack. Analysts extract insights via SQL, then use Python for statistical validation and visual communication.

- **Use cases**:
  - Running a churn analysis: SQL joins customer data with transaction data to calculate churn rates, then Python creates visualisations.
  - Sales forecasting: SQL aggregates historical sales by month, Python applies an ARIMA model.

---

### Step-by-Step Demonstration

**Setting up a realistic dataset**:
```python
import sqlite3
import pandas as pd
import numpy as np

conn = sqlite3.connect('analytics.db')
cursor = conn.cursor()

# Drop and recreate tables
cursor.execute('DROP TABLE IF EXISTS sales')
cursor.execute('DROP TABLE IF EXISTS products')
cursor.execute('DROP TABLE IF EXISTS regions')

# Products table
cursor.execute('''
CREATE TABLE products (
    product_id INTEGER PRIMARY KEY,
    product_name TEXT,
    category TEXT,
    unit_price REAL
)
''')

# Regions table
cursor.execute('''
CREATE TABLE regions (
    region_id INTEGER PRIMARY KEY,
    region_name TEXT,
    country TEXT
)
''')

# Sales table (fact table)
cursor.execute('''
CREATE TABLE sales (
    sale_id INTEGER PRIMARY KEY,
    sale_date TEXT,
    product_id INTEGER,
    region_id INTEGER,
    units_sold INTEGER,
    FOREIGN KEY(product_id) REFERENCES products(product_id),
    FOREIGN KEY(region_id) REFERENCES regions(region_id)
)
''')

# Populate data
np.random.seed(42)
products = [
    (1, 'Laptop', 'Electronics', 1200),
    (2, 'Phone', 'Electronics', 800),
    (3, 'Desk', 'Furniture', 450),
    (4, 'Chair', 'Furniture', 200),
    (5, 'Monitor', 'Electronics', 300)
]
regions = [
    (1, 'North America', 'USA'),
    (2, 'Europe', 'UK'),
    (3, 'Asia Pacific', 'Singapore')
]

cursor.executemany("INSERT INTO products VALUES (?,?,?,?)", products)
cursor.executemany("INSERT INTO regions VALUES (?,?,?)", regions)

# Generate 1000 sales records
sales_data = []
for i in range(1, 1001):
    date = f'2024-{np.random.randint(1,13):02d}-{np.random.randint(1,29):02d}'
    product_id = np.random.randint(1, 6)
    region_id = np.random.randint(1, 4)
    units = np.random.randint(1, 10)
    sales_data.append((i, date, product_id, region_id, units))

cursor.executemany("INSERT INTO sales (sale_id, sale_date, product_id, region_id, units_sold) VALUES (?,?,?,?,?)", sales_data)
conn.commit()
```

**1. Complex Query with JOIN and GROUP BY**:
```python
query = """
SELECT 
    p.category,
    r.region_name,
    SUM(s.units_sold) AS total_units,
    SUM(s.units_sold * p.unit_price) AS total_revenue
FROM sales s
JOIN products p ON s.product_id = p.product_id
JOIN regions r ON s.region_id = r.region_id
GROUP BY p.category, r.region_name
ORDER BY total_revenue DESC
"""

df_summary = pd.read_sql_query(query, conn)
print("Sales Summary by Category and Region:")
print(df_summary)
```

**2. Time Series Analysis (Monthly Revenue)**:
```python
time_query = """
SELECT 
    strftime('%Y-%m', sale_date) AS month,
    SUM(units_sold * unit_price) AS monthly_revenue
FROM sales s
JOIN products p ON s.product_id = p.product_id
GROUP BY month
ORDER BY month
"""

df_monthly = pd.read_sql_query(time_query, conn)
print("\nMonthly Revenue:")
print(df_monthly)

# Visualise in Python
import matplotlib.pyplot as plt
df_monthly['monthly_revenue'].plot(kind='line', marker='o')
plt.title('Monthly Revenue Trend')
plt.xlabel('Month')
plt.ylabel('Revenue ($)')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

**3. Window Functions (Ranking Products by Revenue)**:
```python
rank_query = """
WITH product_revenue AS (
    SELECT 
        p.product_name,
        SUM(s.units_sold * p.unit_price) AS revenue
    FROM sales s
    JOIN products p ON s.product_id = p.product_id
    GROUP BY p.product_name
)
SELECT 
    product_name,
    revenue,
    RANK() OVER (ORDER BY revenue DESC) as rank
FROM product_revenue
ORDER BY rank
"""

df_rank = pd.read_sql_query(rank_query, conn)
print("\nProduct Ranking by Revenue:")
print(df_rank)
```

**4. Calculating Market Share (Percentage of Total)**:
```python
share_query = """
WITH totals AS (
    SELECT SUM(units_sold * unit_price) AS total_revenue
    FROM sales s
    JOIN products p ON s.product_id = p.product_id
)
SELECT 
    p.product_name,
    SUM(s.units_sold * p.unit_price) AS revenue,
    ROUND(100.0 * SUM(s.units_sold * p.unit_price) / (SELECT total_revenue FROM totals), 2) AS market_share_pct
FROM sales s
JOIN products p ON s.product_id = p.product_id
GROUP BY p.product_name
ORDER BY market_share_pct DESC
"""

df_share = pd.read_sql_query(share_query, conn)
print("\nProduct Market Share:")
print(df_share)
```

---

### Practical Examples

- **Example 1**: Analysing website traffic data where clickstream logs are stored in a SQL table.
- **Example 2**: Generating an executive dashboard that pulls KPIs (revenue, churn, growth) via SQL and plots them in Python.

---

### Hands-on Coding Exercises

**Exercise 9.6** – Advanced Analysis:
```python
# 1. Write a query that calculates the total revenue per country.
# 2. Write a query that finds the top 2 best-selling products (by units sold).
# 3. Write a query that calculates the month-over-month growth rate.
# 4. Load all results into Pandas DataFrames.
# 5. Create a bar chart showing revenue per country.
# 6. Create a line chart showing monthly revenue growth.
```

---

### Mini Quiz

1. What is a Common Table Expression (CTE) in SQL?
2. What is the purpose of the `OVER` clause in window functions?
3. How can you calculate a percentage of a total in SQL?
4. Why might you choose to use a CTE instead of a subquery?
5. What is a foreign key constraint?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Writing extremely long, unreadable SQL queries | Use CTEs (`WITH ... AS`) to break down complex logic |
| Doing complex row-by-row processing in Python that SQL could do | Push as much aggregation and transformation to SQL as possible |
| Not testing the SQL query directly in a database tool before putting it in Python | Use a SQL GUI (like DBeaver) to test queries first |
| Ignoring NULL values in aggregations | Use `COALESCE` or handle NULLs explicitly |

---

### Interview Questions

1. **What is the difference between `WHERE` and `HAVING`?**  
   *Answer*: `WHERE` filters rows before aggregation, while `HAVING` filters after aggregation (used with `GROUP BY`).

2. **Explain the difference between a window function and a GROUP BY.**  
   *Answer*: `GROUP BY` collapses rows into a single aggregated row per group. A window function performs a calculation across a set of rows related to the current row without collapsing the rows.

3. **How do you identify duplicate records in a SQL table?**  
   *Answer*: Using `GROUP BY` columns and `HAVING COUNT(*) > 1`.

---

### Assignment and Mini Project

**Assignment 9.6** – End-to-end analytics pipeline:
```python
# 1. Create the 'analytics.db' schema above if you haven't.
# 2. Write a Python script that:
#    a. Executes a SQL query to calculate total revenue by category and region.
#    b. Executes a SQL query to find the top 3 selling products overall.
#    c. Executes a SQL query to calculate average units sold per transaction.
#    d. Loads all results into Pandas DataFrames.
#    e. Creates a single dashboard (subplots) showing:
#       - A bar chart of revenue by category and region (grouped bar).
#       - A horizontal bar chart of the top 3 products.
#       - A summary card (print) with the average units sold.
```

**Mini Project** – Sales Dashboard System:
Build a Python program that:
1. Generates the `analytics.db` with 5000+ sales records (add more variety).
2. Contains a function `run_analysis()` that:
   - Fetches Sales by Region.
   - Fetches Top Products by Revenue.
   - Fetches Monthly Sales Trend.
3. Automates the creation of a professional 2x2 subplot dashboard using Matplotlib/Seaborn.
4. Saves the dashboard as a PNG file.
5. Exports the summary DataFrames to an Excel file with separate sheets.

---

### Summary and Revision Notes

- SQL is excellent for joining, aggregating, and windowing.
- CTEs (`WITH`) make complex queries readable.
- Use `pd.read_sql_query` to bring clean, aggregated data into Python.
- Combine SQL's data processing power with Python's visualisation and statistical capabilities.

---

## Final Phase 9 Assessment

Now that you have completed all lessons, test your overall understanding.

### Self-Evaluation Checklist

- I can create SQLite databases and tables.

- I can connect to databases using context managers.

- I can execute `SELECT`, `INSERT`, `UPDATE`, and `DELETE` safely using parameterized queries.

- I can load SQL query results directly into Pandas DataFrames.

- I can use `df.to_sql` to write DataFrames to databases.

- I can write complex SQL queries (JOINs, GROUP BY, CTEs, Window Functions) and integrate them with Python.


---

### Answers to Mini Quizzes

**Lesson 9.1**: 1. It's just a name. 2. `sqlite3`. 3. To execute SQL commands and fetch results. 4. It prevents an error if the table already exists. 5. `commit()` saves changes; without it, changes are temporary.

**Lesson 9.2**: 1. `with sqlite3.connect(...) as conn`. 2. `psycopg2`. 3. To keep credentials secret. 4. It reads an environment variable. 5. `:memory:` creates an in-memory database (temporary).

**Lesson 9.3**: 1. `fetchone()` returns one row, `fetchall()` returns all. 2. To prevent SQL injection. 3. To insert/update multiple rows efficiently. 4. It allows fetching rows as dictionaries. 5. No, `SELECT` doesn't change data, so `commit()` is not required.

**Lesson 9.4**: 1. `pd.read_sql_query`. 2. Using the `params` argument. 3. SQL is optimised for aggregation, reducing memory/network. 4. `read_sql_query` uses a SQL string; `read_sql_table` reads a whole table directly. 5. Use the `index_col` parameter.

**Lesson 9.5**: 1. It undoes changes since the last `commit()`. 2. `append` adds to the table; `replace` drops and recreates. 3. To catch errors and rollback to maintain data integrity. 4. `UPDATE employees SET salary = salary * 1.1`. 5. Yes, by setting `if_exists='replace'` or connecting to a new/empty database.

**Lesson 9.6**: 1. A temporary named result set used within a query. 2. It defines the window (set of rows) the function operates on. 3. Using a subquery or a window function with `SUM() OVER()`. 4. CTEs are more readable and can be referenced multiple times. 5. A constraint that ensures values in one table match values in another.

---

**Congratulations!** You have completed Phase 9. You are now proficient in connecting Python to SQL databases, performing CRUD operations, and seamlessly integrating SQL's power with Pandas. Keep up the momentum!
