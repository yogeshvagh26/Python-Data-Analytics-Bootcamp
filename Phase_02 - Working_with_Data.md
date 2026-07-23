# Phase 2: Working with Data

Welcome to **Phase 2** of your Python for Data Analytics journey! In Phase 1, you learned the fundamentals of Python programming – variables, data types, loops, functions, and file handling. Now, we move to the heart of data analytics: **reading, writing, and working with real-world data formats**.

In this phase, you'll learn how to:
- Read and write **CSV files** – the most common data format in analytics.
- Work with **Excel files** (.xlsx, .xls) – the business world's favourite spreadsheet format.
- Handle **JSON files** – the standard for web APIs and modern data exchange.
- Process **text files** – including log files and unstructured data.
- Build a complete **data pipeline** – read, process, and write data.
- Connect to **APIs** – pull live data from the internet.
- **Download online data** – automate data collection from the web.

By the end of this phase, you'll be able to load, process, and save data from virtually any source – a skill that forms the foundation of every data analytics project.

Let's dive in!

---

## Lesson 2.1 – CSV Files

### Concept Explanation

**CSV (Comma-Separated Values)** is the most widely used file format for storing and exchanging tabular data. It is simple, human-readable, and supported by virtually every data tool.

**Key characteristics**:
- Each row is a record.
- Each column is separated by a delimiter (usually a comma, but can be semicolon, tab, etc.).
- The first row often contains column headers.
- Files are plain text, making them easy to read and edit.

**Why CSV is important in data analytics**:
- Almost every data analysis tool (Excel, Tableau, Power BI, R, pandas) supports CSV.
- It's the standard format for exporting data from databases and other systems.
- It's lightweight and easy to share.

**Python's `csv` module**:
- Built-in module for reading and writing CSV files.
- Provides `csv.reader()` and `csv.writer()` functions.
- Handles different delimiters, quoting, and escape characters.

**Alternative: `pandas`** (which we'll cover later):
- `pandas.read_csv()` is the most common way to read CSV files in data analytics.
- Provides powerful features like automatic type inference, handling missing values, and more.

---

### Importance and Real-World Use Cases

- **Why it matters**: CSV is the lingua franca of data analytics. Most datasets you encounter will be in CSV format. Mastering CSV handling is essential for any data professional.

- **Use cases**:
  - A **data analyst** exports sales data from a database as a CSV and loads it into Python for analysis.
  - A **financial analyst** receives monthly budget reports as CSV files and combines them.
  - A **data scientist** downloads a dataset from Kaggle (often CSV) and prepares it for machine learning.

---

### Step-by-Step Demonstration

**Reading a CSV File with `csv` Module**:

```python
import csv

# Method 1: Using csv.reader()
with open('data.csv', 'r') as file:
    reader = csv.reader(file)
    header = next(reader)  # Read the header row
    print("Header:", header)
    
    for row in reader:
        print(row)  # Each row is a list of values
```

**Reading CSV with custom delimiter (e.g., semicolon)**:

```python
with open('data_semicolon.csv', 'r') as file:
    reader = csv.reader(file, delimiter=';')
    for row in reader:
        print(row)
```

**Reading CSV with DictReader (rows as dictionaries)**:

```python
with open('data.csv', 'r') as file:
    reader = csv.DictReader(file)  # Uses header row as dictionary keys
    for row in reader:
        print(row['Name'], row['Age'], row['City'])
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
    print("CSV file written successfully!")

# Writing row by row
with open('output.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerow(['Name', 'Age', 'City'])
    writer.writerow(['Alice', 25, 'New York'])
    writer.writerow(['Bob', 30, 'London'])
```

**Writing with DictWriter (rows as dictionaries)**:

```python
import csv

data = [
    {'Name': 'Alice', 'Age': 25, 'City': 'New York'},
    {'Name': 'Bob', 'Age': 30, 'City': 'London'},
    {'Name': 'Charlie', 'Age': 35, 'City': 'Paris'}
]

with open('output.csv', 'w', newline='') as file:
    fieldnames = ['Name', 'Age', 'City']
    writer = csv.DictWriter(file, fieldnames=fieldnames)
    
    writer.writeheader()
    writer.writerows(data)
```

**Reading CSV with Pandas (preview)**:

```python
import pandas as pd

df = pd.read_csv('data.csv')
print(df.head())  # First 5 rows
print(df.info())  # Data types and null values
print(df.describe())  # Summary statistics
```

---

### Practical Examples

**Example 1: Calculating total sales from a CSV**:

```python
import csv

total_sales = 0
row_count = 0

with open('sales.csv', 'r') as file:
    reader = csv.reader(file)
    next(reader)  # Skip header
    
    for row in reader:
        # Assuming Sales is in column 2 (index 1)
        sales = float(row[1])
        total_sales += sales
        row_count += 1

print(f"Total sales: ${total_sales:,.2f}")
print(f"Number of transactions: {row_count}")
print(f"Average transaction: ${total_sales/row_count:,.2f}")
```

**Example 2: Filtering and writing to a new CSV**:

```python
import csv

with open('sales.csv', 'r') as infile, open('high_sales.csv', 'w') as outfile:
    reader = csv.reader(infile)
    writer = csv.writer(outfile)
    
    header = next(reader)
    writer.writerow(header)  # Write header to new file
    
    for row in reader:
        # If sales > 1000, keep the row
        if float(row[1]) > 1000:
            writer.writerow(row)

print("High sales records saved to high_sales.csv")
```

**Example 3: Merging multiple CSV files**:

```python
import csv

files = ['sales_jan.csv', 'sales_feb.csv', 'sales_mar.csv']
all_data = []

for file in files:
    with open(file, 'r') as f:
        reader = csv.reader(f)
        next(reader)  # Skip header (assuming all have the same header)
        for row in reader:
            all_data.append(row)

# Write combined data
with open('sales_all.csv', 'w') as f:
    writer = csv.writer(f)
    writer.writerow(['Product', 'Sales', 'Month'])  # Write header once
    writer.writerows(all_data)

print(f"Combined {len(all_data)} rows from {len(files)} files")
```

---

### Hands-on Coding Exercises

**Exercise 2.1** – Read and display CSV:
```python
# 1. Create a CSV file with sample data (or download one)
# 2. Read the CSV file using csv.reader
# 3. Print the first 5 rows
# 4. Print the column names
```

**Exercise 2.2** – Calculate statistics:
```python
# 1. Read a CSV with numeric data
# 2. Calculate:
#    - Average of a column
#    - Maximum value
#    - Minimum value
#    - Number of rows
# 3. Print the results in a formatted way
```

**Exercise 2.3** – Filter and save:
```python
# 1. Read a CSV file
# 2. Keep only rows where a value meets a condition (e.g., age > 30)
# 3. Save the filtered data to a new CSV file
```

---

### Mini Quiz

1. What does CSV stand for?
2. What is the purpose of `csv.reader()`?
3. What is the difference between `csv.reader()` and `csv.DictReader()`?
4. How do you skip the header row when reading a CSV?
5. What does the `newline=''` parameter do when writing CSV files?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to specify the delimiter for non-comma files | Always specify `delimiter` if it's not a comma |
| Not handling encoding issues | Use `encoding='utf-8'` when opening files |
| Ignoring empty or malformed rows | Use try/except to handle malformed rows |
| Reading large CSV files into memory all at once | Use row-by-row reading for large files |
| Not checking if the file exists before reading | Use `os.path.exists()` or try/except |

---

### Interview Questions

1. **How do you read a CSV file in Python?**  
   *Answer*: Using the `csv` module: `csv.reader()` for list-based reading, `csv.DictReader()` for dictionary-based reading. Alternatively, `pandas.read_csv()` for more powerful data handling.

2. **How do you handle a CSV file with a different delimiter (e.g., semicolon)?**  
   *Answer*: Specify the `delimiter` parameter: `csv.reader(file, delimiter=';')`.

3. **How would you read a very large CSV file without running out of memory?**  
   *Answer*: Use row-by-row processing with a for loop over `csv.reader()`, processing one row at a time. Or use `pandas` with chunking: `pd.read_csv('file.csv', chunksize=10000)`.

---

### Assignment and Mini Project

**Assignment 2.1** – Sales data analysis:
```python
# Download or create a sales CSV file with columns: Product, Region, Sales, Quantity
# 1. Read the CSV file
# 2. Calculate total sales by region
# 3. Calculate total sales by product
# 4. Calculate average sales per transaction
# 5. Write the summary to a new CSV file
```

**Mini Project** – Data Aggregator:
Create a Python program that:
1. Asks the user for a CSV filename.
2. Reads the CSV file.
3. Asks for the column to aggregate by (e.g., "Region").
4. Asks for the column to aggregate (e.g., "Sales").
5. Calculates the total and average for each group.
6. Writes the results to a new CSV file.
7. Handles invalid inputs gracefully.

---

### Summary and Revision Notes

- CSV is the most common data format in analytics.
- `csv.reader()` reads CSV rows as lists.
- `csv.DictReader()` reads CSV rows as dictionaries (header becomes keys).
- `csv.writer()` writes CSV rows as lists.
- `csv.DictWriter()` writes CSV rows as dictionaries.
- Always specify the delimiter if it's not a comma.
- Use `with open()` for automatic file closing.

---

## Lesson 2.2 – Excel Files

### Concept Explanation

**Excel files** (.xlsx, .xls) are widely used in business for reporting, budgeting, and data storage. While CSV is simpler, Excel files offer:
- Multiple sheets within a single file.
- Formatting, formulas, and charts.
- Better support for complex data structures.

**Python libraries for Excel**:

| **Library** | **Description** | **Features** |
|-------------|-----------------|--------------|
| `openpyxl` | Read/write Excel .xlsx files | Full Excel support, cell formatting, formulas |
| `xlrd` | Read Excel .xlsx and .xls files | Older but reliable |
| `xlsxwriter` | Write Excel .xlsx files | Advanced formatting |
| `pandas` | Read/write Excel via openpyxl/xlrd | Simplest for data analysts |

**Installation**:
```bash
pip install openpyxl pandas
```

**Key concepts**:
- **Workbook** – the entire Excel file.
- **Worksheet** – a single sheet within the workbook.
- **Cell** – a single cell (e.g., A1, B2).

---

### Importance and Real-World Use Cases

- **Why it matters**: Excel is the lingua franca of business. Financial reports, budget spreadsheets, and operational data are often stored in Excel files. Being able to read and write Excel programmatically is essential for automation.

- **Use cases**:
  - A **financial analyst** consolidates monthly budget spreadsheets from different departments.
  - A **data analyst** extracts data from a multi-sheet Excel report for analysis in Python.
  - A **consultant** generates a formatted Excel report with summaries and charts.

---

### Step-by-Step Demonstration

**Reading Excel with `pandas` (Recommended)**:

```python
import pandas as pd

# Read the first sheet
df = pd.read_excel('data.xlsx')
print(df.head())

# Read a specific sheet
df = pd.read_excel('data.xlsx', sheet_name='Sales')
print(df.head())

# Read all sheets into a dictionary
sheets = pd.read_excel('data.xlsx', sheet_name=None)
for sheet_name, data in sheets.items():
    print(f"Sheet: {sheet_name}")
    print(data.head())
```

**Reading Excel with `openpyxl`**:

```python
from openpyxl import load_workbook

# Load the workbook
workbook = load_workbook('data.xlsx')
print(workbook.sheetnames)

# Access a specific sheet
sheet = workbook['Sheet1']

# Read cell by cell
for row in sheet.iter_rows(values_only=True):
    print(row)

# Read specific cell
cell_value = sheet['A1'].value
print(f"A1: {cell_value}")

# Loop through rows and columns
for row in sheet.iter_rows(min_row=2, max_row=5, min_col=1, max_col=3, values_only=True):
    print(row)
```

**Writing Excel with `pandas`**:

```python
import pandas as pd

data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'City': ['New York', 'London', 'Paris']
}

df = pd.DataFrame(data)

# Write to a single sheet
df.to_excel('output.xlsx', index=False)

# Write to multiple sheets
with pd.ExcelWriter('output.xlsx') as writer:
    df.to_excel(writer, sheet_name='Sheet1', index=False)
    df.to_excel(writer, sheet_name='Sheet2', index=False)
```

**Writing Excel with `openpyxl`**:

```python
from openpyxl import Workbook

wb = Workbook()
sheet = wb.active
sheet.title = 'Sales'

# Write header
sheet['A1'] = 'Product'
sheet['B1'] = 'Sales'
sheet['C1'] = 'Quantity'

# Write data
data = [['Widget A', 1200, 10],
        ['Widget B', 800, 8],
        ['Widget C', 1500, 15]]

for row_num, row_data in enumerate(data, start=2):
    sheet.cell(row=row_num, column=1, value=row_data[0])
    sheet.cell(row=row_num, column=2, value=row_data[1])
    sheet.cell(row=row_num, column=3, value=row_data[2])

wb.save('output.xlsx')
print("Excel file created successfully!")
```

**Working with Multiple Sheets**:

```python
from openpyxl import load_workbook

wb = load_workbook('multi_sheet.xlsx')

# Access different sheets
sheet1 = wb['Sales']
sheet2 = wb['Budget']
sheet3 = wb['Forecast']

# Read from each sheet
for row in sheet1.iter_rows(values_only=True):
    print(row)
```

---

### Practical Examples

**Example 1: Consolidate monthly budget files**:

```python
import pandas as pd
import glob

# Get all Excel files in a folder
files = glob.glob('budgets/*.xlsx')

all_data = pd.DataFrame()

for file in files:
    df = pd.read_excel(file)
    month = file.split('/')[-1].replace('.xlsx', '')
    df['Month'] = month
    all_data = pd.concat([all_data, df], ignore_index=True)

# Save consolidated data
all_data.to_excel('consolidated_budget.xlsx', index=False)
print(f"Consolidated {len(files)} files into one Excel file")
```

**Example 2: Extract specific sheets from a multi-sheet report**:

```python
import pandas as pd

# Read all sheets
sheets = pd.read_excel('annual_report.xlsx', sheet_name=None)

# Process only sheets named 'Q1', 'Q2', 'Q3', 'Q4'
quarterly_data = {}
for sheet_name, data in sheets.items():
    if sheet_name in ['Q1', 'Q2', 'Q3', 'Q4']:
        quarterly_data[sheet_name] = data

# Combine quarterly data
combined = pd.concat(quarterly_data, ignore_index=True)
combined.to_excel('yearly_summary.xlsx', index=False)
print("Yearly summary created!")
```

---

### Hands-on Coding Exercises

**Exercise 2.4** – Read and display Excel:
```python
# 1. Create an Excel file with sample data (or download one)
# 2. Read the Excel file using pandas
# 3. Display the first 5 rows
# 4. Display the column names
# 5. Display basic statistics
```

**Exercise 2.5** – Write to Excel:
```python
# 1. Create a dictionary with sample data
# 2. Convert to a pandas DataFrame
# 3. Write the DataFrame to an Excel file
# 4. Write to a specific sheet
```

**Exercise 2.6** – Multi-sheet handling:
```python
# 1. Read an Excel file with multiple sheets
# 2. Print the sheet names
# 3. Read a specific sheet
# 4. Combine data from all sheets into a single DataFrame
# 5. Write the combined data to a new Excel file
```

---

### Mini Quiz

1. What are the two main Python libraries for Excel files?
2. What is the difference between `openpyxl` and `pandas` for Excel?
3. What is a Workbook in Excel terminology?
4. How do you read a specific sheet in pandas?
5. How do you write to multiple sheets in Excel with pandas?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to install required libraries | Install `openpyxl` and `pandas` |
| Not handling different sheet names | Use `sheet_name=None` to read all sheets |
| Not checking if the file exists | Use try/except or `os.path.exists()` |
| Writing without specifying index | Use `index=False` in `to_excel()` |
| Not using the correct engine | For `.xlsx`, `pandas` uses `openpyxl` by default |

---

### Interview Questions

1. **How do you read an Excel file in Python?**  
   *Answer*: Using `pandas.read_excel()`. You can specify the sheet name, header row, and other parameters. For more granular control, use `openpyxl`.

2. **How do you read multiple sheets from an Excel file?**  
   *Answer*: Using `pandas.read_excel(file, sheet_name=None)` returns a dictionary of DataFrames, one for each sheet.

3. **What is the difference between `xlrd` and `openpyxl`?**  
   *Answer*: `xlrd` reads older `.xls` files and newer `.xlsx` files (limited). `openpyxl` reads and writes `.xlsx` files with full feature support.

---

### Assignment and Mini Project

**Assignment 2.2** – Excel data processing:
```python
# 1. Create an Excel file with sales data (Product, Region, Sales, Quantity)
# 2. Read the Excel file
# 3. Calculate summary statistics
# 4. Write the summary to a new sheet in the same Excel file
# 5. Save the file
```

**Mini Project** – Excel Report Generator:
Create a program that:
1. Reads an Excel file containing sales data.
2. Calculates:
   - Total sales by product.
   - Total sales by region.
   - Average sales per transaction.
   - Highest and lowest sales.
3. Writes a summary report to a new sheet called "Summary".
4. Formats the summary sheet with headers, totals, and borders using `openpyxl`.

---

### Summary and Revision Notes

- Excel files are common in business.
- `pandas.read_excel()` – simplest way to read Excel.
- `openpyxl` – full control over Excel files.
- Workbooks contain worksheets (sheets).
- Use `sheet_name` to specify which sheet to read.
- Write with `to_excel()` and `ExcelWriter`.
- Excel files can hold multiple sheets, formulas, and formatting.

---

## Lesson 2.3 – JSON Files

### Concept Explanation

**JSON (JavaScript Object Notation)** is a lightweight data interchange format that is human-readable and machine-parseable. It has become the standard for web APIs and modern data exchange.

**Why JSON is important**:
- **Web APIs**: Most APIs return data in JSON format.
- **Hierarchical data**: Supports nested structures (objects within objects).
- **Language-agnostic**: Used across all programming languages.

**JSON Structure**:
```json
{
    "name": "Alice",
    "age": 25,
    "city": "New York",
    "hobbies": ["reading", "swimming"],
    "address": {
        "street": "123 Main St",
        "zip": "10001"
    }
}
```

**Key concepts**:
- **Object**: `{"key": value}` – similar to a Python dictionary.
- **Array**: `[value1, value2]` – similar to a Python list.
- **Null**: `null` – similar to Python `None`.

---

### Importance and Real-World Use Cases

- **Why it matters**: JSON is the universal data format of the web. Almost every data API returns JSON. Mastering JSON handling is essential for data analytics in the modern world.

- **Use cases**:
  - A **data analyst** pulls data from a REST API (e.g., sales data from Salesforce) in JSON format.
  - A **data engineer** processes log files stored in JSON format.
  - A **data scientist** loads JSON data from a NoSQL database like MongoDB.

---

### Step-by-Step Demonstration

**Reading JSON from a File**:

```python
import json

# Read JSON file
with open('data.json', 'r') as file:
    data = json.load(file)
    print(data)
    print(data['name'])  # Access data like a dictionary
    print(data['hobbies'])
```

**Writing JSON to a File**:

```python
import json

data = {
    "name": "Alice",
    "age": 25,
    "city": "New York",
    "hobbies": ["reading", "swimming"],
    "address": {
        "street": "123 Main St",
        "zip": "10001"
    }
}

with open('output.json', 'w') as file:
    json.dump(data, file, indent=4)  # indent makes it human-readable
    print("JSON file written successfully!")
```

**Parsing JSON from a String**:

```python
import json

# JSON string (e.g., from an API response)
json_string = '{"name": "Bob", "age": 30, "city": "London"}'

# Parse to Python dictionary
data = json.loads(json_string)
print(data['name'])  # Bob
print(data['age'])   # 30
```

**Converting Python to JSON String**:

```python
import json

data = {"name": "Charlie", "age": 35, "city": "Paris"}

# Convert to JSON string
json_string = json.dumps(data)
print(json_string)  # {"name": "Charlie", "age": 35, "city": "Paris"}

# With indentation
json_string = json.dumps(data, indent=4)
print(json_string)
```

**Working with Nested JSON**:

```python
import json

# Nested JSON data
json_data = '''
{
    "company": "TechCorp",
    "employees": [
        {"name": "Alice", "role": "Developer"},
        {"name": "Bob", "role": "Designer"},
        {"name": "Charlie", "role": "Manager"}
    ]
}
'''

data = json.loads(json_data)

print(data['company'])  # TechCorp

# Loop through employees
for employee in data['employees']:
    print(f"{employee['name']} - {employee['role']}")
```

**Handling JSON with Pandas**:

```python
import pandas as pd
import json

# Load JSON
with open('data.json', 'r') as file:
    data = json.load(file)

# Convert to DataFrame
df = pd.DataFrame(data['employees'])  # If data is a list of objects
print(df)

# Or read directly with pandas
df = pd.read_json('data.json')
print(df)
```

---

### Practical Examples

**Example 1: Processing API Response**:

```python
import json
import requests

# Sample API call (weather data)
response = requests.get('https://api.openweathermap.org/data/2.5/weather?q=London&appid=YOUR_API_KEY')

# Parse JSON response
weather_data = response.json()

print(f"City: {weather_data['name']}")
print(f"Temperature: {weather_data['main']['temp']}K")
print(f"Humidity: {weather_data['main']['humidity']}%")
print(f"Conditions: {weather_data['weather'][0]['description']}")
```

**Example 2: Flattening Nested JSON**:

```python
import json

# Sample nested JSON
json_data = '''
[
    {"id": 1, "name": "Alice", "contact": {"email": "alice@example.com", "phone": "123-4567"}},
    {"id": 2, "name": "Bob", "contact": {"email": "bob@example.com", "phone": "234-5678"}}
]
'''

data = json.loads(json_data)

# Flatten nested fields
flattened = []
for item in data:
    flattened.append({
        'id': item['id'],
        'name': item['name'],
        'email': item['contact']['email'],
        'phone': item['contact']['phone']
    })

print(flattened)
```

**Example 3: Writing JSON Line-by-Line (JSONL)**:

```python
import json

data = [
    {"name": "Alice", "age": 25},
    {"name": "Bob", "age": 30},
    {"name": "Charlie", "age": 35}
]

# Write JSONL format (one JSON object per line)
with open('output.jsonl', 'w') as file:
    for item in data:
        file.write(json.dumps(item) + '\n')

# Read JSONL back
with open('output.jsonl', 'r') as file:
    for line in file:
        item = json.loads(line)
        print(item)
```

---

### Hands-on Coding Exercises

**Exercise 2.7** – Read and parse JSON:
```python
# 1. Create a JSON file with sample data (or download one)
# 2. Read the JSON file using json.load()
# 3. Extract specific fields
# 4. Print the extracted data
```

**Exercise 2.8** – Convert JSON to CSV:
```python
# 1. Read a JSON file
# 2. Extract the data
# 3. Convert to a CSV file
# 4. The output CSV should have headers
```

**Exercise 2.9** – Work with nested JSON:
```python
# 1. Load nested JSON data
# 2. Extract specific nested fields
# 3. Flatten the nested structure
# 4. Convert to a pandas DataFrame
```

---

### Mini Quiz

1. What is JSON?
2. What is the difference between `json.load()` and `json.loads()`?
3. What is the difference between `json.dump()` and `json.dumps()`?
4. How do you handle nested JSON data in Python?
5. What is JSONL?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to import `json` | Always import the `json` module |
| Using `loads()` instead of `load()` with files | Use `load()` for files, `loads()` for strings |
| Not handling missing keys in JSON | Use `.get('key')` with a default value |
| Not using `indent` when writing – unreadable JSON | Use `indent=4` for readability |
| Assuming JSON is always valid | Use try/except for invalid JSON |

---

### Interview Questions

1. **How do you parse JSON in Python?**  
   *Answer*: Using the `json` module: `json.loads()` for strings, `json.load()` for files.

2. **What is the difference between `json.load()` and `json.loads()`?**  
   *Answer*: `json.load()` reads from a file object. `json.loads()` reads from a string.

3. **How do you handle nested JSON data?**  
   *Answer*: Access nested fields using dictionary keys: `data['key1']['key2']`. For complex nesting, you can use loops or `pandas.json_normalize()`.

---

### Assignment and Mini Project

**Assignment 2.3** – JSON to CSV converter:
```python
# 1. Read a JSON file
# 2. Extract the data (handle nested fields)
# 3. Write the data to a CSV file
# 4. Include error handling
# 5. Accept the filename from the user
```

**Mini Project** – Data Pipeline:
Create a program that:
1. Reads a JSON file containing sales data.
2. Flattens any nested structures.
3. Filters out invalid or empty records.
4. Calculates total sales, average, and counts.
5. Writes the summary to a new JSON file.
6. Writes the processed data to a CSV file.

---

### Summary and Revision Notes

- JSON is the standard for web APIs.
- Use `json.load()` to read from a file.
- Use `json.loads()` to parse from a string.
- Use `json.dump()` to write to a file.
- Use `json.dumps()` to convert to a string.
- Nested JSON can be accessed using dictionary keys.
- Handle missing keys with `.get('key', default)`.

---

## Lesson 2.4 – Text Files

### Concept Explanation

**Text files** are the most basic form of data storage. While CSV, Excel, and JSON are structured formats, text files are unstructured and can contain any type of data – from log files and configuration files to raw notes and source code.

**Common use cases for text files**:
- **Log files**: Application logs, server logs.
- **Configuration files**: `.ini`, `.cfg`, `.conf`.
- **Data ingestion**: Some APIs return data in plain text.

**Key operations**:
- Read the entire file.
- Read line by line (for large files).
- Write to a file.
- Append to a file.

**Reading Modes**:
- `r` – read (default)
- `w` – write (overwrites)
- `a` – append
- `r+` – read and write

---

### Importance and Real-World Use Cases

- **Why it matters**: Text files are everywhere. Understanding how to read, write, and process text files is essential for data analytics, especially when dealing with unstructured data like logs, reports, and configuration files.

- **Use cases**:
  - A **data analyst** processes server log files to identify errors and usage patterns.
  - A **developer** reads configuration files to load settings.
  - A **data engineer** extracts data from plain text reports.

---

### Step-by-Step Demonstration

**Reading a Text File**:

```python
# Method 1: Read entire file
with open('sample.txt', 'r') as file:
    content = file.read()
    print(content)

# Method 2: Read line by line
with open('sample.txt', 'r') as file:
    for line in file:
        print(line.strip())

# Method 3: Read all lines into a list
with open('sample.txt', 'r') as file:
    lines = file.readlines()
    print(lines)
```

**Writing to a Text File**:

```python
# Write (overwrites)
with open('output.txt', 'w') as file:
    file.write("Line 1\n")
    file.write("Line 2\n")
    file.write("Line 3\n")

# Append (adds to the end)
with open('output.txt', 'a') as file:
    file.write("Line 4\n")
    file.write("Line 5\n")
```

**Reading and Processing Log Files**:

```python
# Example: Count error messages in a log file
error_count = 0
warning_count = 0

with open('server.log', 'r') as file:
    for line in file:
        if 'ERROR' in line:
            error_count += 1
        elif 'WARNING' in line:
            warning_count += 1

print(f"Errors: {error_count}")
print(f"Warnings: {warning_count}")
```

**Extracting Data from Text Files**:

```python
# Example: Extract numbers from a text file
import re

with open('data.txt', 'r') as file:
    content = file.read()
    numbers = re.findall(r'\d+', content)  # Find all numbers
    numbers = [int(n) for n in numbers]
    print(f"Total: {sum(numbers)}")
    print(f"Average: {sum(numbers) / len(numbers):.2f}")
```

**Using `with` Statement** (Recommended):
```python
# Always use `with` for automatic file closing
with open('file.txt', 'r') as file:
    content = file.read()
# File is automatically closed here
```

**Encoding**:
```python
# Handle different encodings
with open('file.txt', 'r', encoding='utf-8') as file:
    content = file.read()

# Common encodings: 'utf-8', 'ascii', 'latin-1'
```

---

### Practical Examples

**Example 1: Log File Analyzer**:

```python
# Analyze server log and create a summary report
log_file = 'access.log'
summary = {
    'total_requests': 0,
    'unique_ips': set(),
    'status_codes': {},
    'method_counts': {'GET': 0, 'POST': 0, 'PUT': 0, 'DELETE': 0}
}

with open(log_file, 'r') as file:
    for line in file:
        if not line.strip():
            continue
        
        parts = line.split()
        summary['total_requests'] += 1
        
        # Extract IP (first part of some logs)
        summary['unique_ips'].add(parts[0])
        
        # Extract method
        if len(parts) > 5:
            method = parts[5].strip('"')
            if method in summary['method_counts']:
                summary['method_counts'][method] += 1
        
        # Extract status code (position varies)
        # This is a simplified example

print(f"Total requests: {summary['total_requests']}")
print(f"Unique IPs: {len(summary['unique_ips'])}")
print(f"Method counts: {summary['method_counts']}")
```

**Example 2: Config File Parser**:

```python
# Parse a simple config file (key=value format)
def parse_config(filename):
    config = {}
    with open(filename, 'r') as file:
        for line in file:
            line = line.strip()
            if line and not line.startswith('#'):  # Skip comments
                key, value = line.split('=', 1)
                config[key.strip()] = value.strip()
    return config

config = parse_config('config.txt')
print(config)
```

---

### Hands-on Coding Exercises

**Exercise 2.10** – Read and process a text file:
```python
# 1. Create a text file with numbers (one per line)
# 2. Read the file
# 3. Calculate the sum, average, maximum, and minimum
# 4. Print the results
```

**Exercise 2.11** – Log file analyzer:
```python
# 1. Create a simple log file with ERROR, WARNING, INFO messages
# 2. Read the log file
# 3. Count the number of each severity level
# 4. Print the counts
```

**Exercise 2.12** – Write to a text file:
```python
# 1. Ask the user for their name, age, and city
# 2. Write the information to a text file
# 3. Append another user's information
# 4. Read the file back and display it
```

---

### Mini Quiz

1. What is the difference between `r` and `w` modes?
2. What does `readlines()` return?
3. Why is the `with` statement recommended for file handling?
4. What is the purpose of the `encoding` parameter?
5. How do you append to a text file?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Forgetting to close files | Use `with` statement |
| Assuming the file exists | Use try/except for file operations |
| Ignoring encoding issues | Always specify `encoding='utf-8'` |
| Reading large files with `read()` | Use `read()` only for small files; use line-by-line for large files |
| Not stripping whitespace | Use `.strip()` to clean lines |

---

### Interview Questions

1. **How do you read a large text file efficiently in Python?**  
   *Answer*: Use line-by-line iteration: `for line in file:` to avoid loading the entire file into memory.

2. **What is the purpose of the `with` statement?**  
   *Answer*: The `with` statement automatically closes the file when the block is exited, even if an exception occurs.

3. **How do you handle different encodings when reading text files?**  
   *Answer*: Specify the `encoding` parameter: `open('file.txt', 'r', encoding='utf-8')`.

---

### Assignment and Mini Project

**Assignment 2.4** – Text file processing:
```python
# 1. Create a text file with multiple lines of data
# 2. Read the file
# 3. Count words, lines, and characters
# 4. Find the longest line
# 5. Write the summary to a new file
```

**Mini Project** – Log File Monitoring System:
Create a program that:
1. Reads a log file continuously (simulate by reading once).
2. Counts different error types (ERROR, WARNING, CRITICAL, INFO).
3. Identifies the most frequent error message.
4. Generates a summary report with:
   - Total lines processed.
   - Error counts by type.
   - Most common error message.
   - Timestamp of the summary.
5. Writes the summary to a text file.

---

### Summary and Revision Notes

- Text files are the most basic data format.
- Use `open()` with `with` for safe file handling.
- `r` – read, `w` – write, `a` – append.
- `read()` reads entire file.
- `readlines()` reads all lines into a list.
- Iterate line by line for large files.
- Always specify encoding for non-ASCII files.

---

## Lesson 2.5 – Reading and Writing Data (Combined)

### Concept Explanation

Now that you've learned how to read and write different file formats individually, it's time to combine these skills. In real-world data analytics, you'll often need to:
- Read data from one format, process it, and write it to another format.
- Combine data from multiple sources.
- Automate data pipelines.

**Common data pipelines**:
1. CSV → Process → CSV/Excel
2. Excel → Process → JSON
3. JSON → Process → CSV
4. API → Process → CSV/Excel
5. Text → Process → CSV

**Key principles**:
- **Modularity**: Write reusable functions for each operation.
- **Error handling**: Handle missing files, invalid data, and other issues.
- **Logging**: Track what the pipeline does.

---

### Importance and Real-World Use Cases

- **Why it matters**: Data rarely stays in one format. You'll often receive data in one format and need to deliver it in another. A complete data pipeline is a core skill for data analytics.

- **Use cases**:
  - A **data analyst** receives a CSV, processes it, and delivers an Excel report.
  - A **data engineer** reads JSON from an API, processes it, and loads it to a database.
  - A **business analyst** combines data from multiple CSV and Excel files into a single report.

---

### Step-by-Step Demonstration

**CSV to Excel Converter**:

```python
import pandas as pd

def csv_to_excel(csv_file, excel_file, sheet_name='Data'):
    """
    Convert a CSV file to an Excel file.
    """
    try:
        df = pd.read_csv(csv_file)
        df.to_excel(excel_file, sheet_name=sheet_name, index=False)
        print(f"Successfully converted {csv_file} to {excel_file}")
        return True
    except FileNotFoundError:
        print(f"Error: {csv_file} not found")
        return False
    except Exception as e:
        print(f"Error: {e}")
        return False

# Usage
csv_to_excel('data.csv', 'data.xlsx')
```

**JSON to CSV Converter**:

```python
import json
import csv

def json_to_csv(json_file, csv_file):
    """
    Convert a JSON file to a CSV file.
    """
    try:
        with open(json_file, 'r') as f:
            data = json.load(f)
        
        # If data is a list of dictionaries
        if isinstance(data, list):
            headers = data[0].keys()
            with open(csv_file, 'w', newline='') as f:
                writer = csv.DictWriter(f, fieldnames=headers)
                writer.writeheader()
                writer.writerows(data)
            print(f"Successfully converted {json_file} to {csv_file}")
        else:
            print("Error: JSON data is not a list of objects")
            return False
        return True
    except Exception as e:
        print(f"Error: {e}")
        return False

# Usage
json_to_csv('data.json', 'data.csv')
```

**Excel to CSV Converter**:

```python
import pandas as pd

def excel_to_csv(excel_file, csv_file, sheet_name=0):
    """
    Convert an Excel file to a CSV file.
    """
    try:
        df = pd.read_excel(excel_file, sheet_name=sheet_name)
        df.to_csv(csv_file, index=False)
        print(f"Successfully converted {excel_file} to {csv_file}")
        return True
    except Exception as e:
        print(f"Error: {e}")
        return False

# Usage
excel_to_csv('data.xlsx', 'data.csv')
```

**Multi-Format Processor**:

```python
def process_data(input_file, output_file, input_format='auto', output_format='auto'):
    """
    Process data from one format to another.
    Supports CSV, Excel, and JSON.
    """
    # Detect input format
    if input_format == 'auto':
        if input_file.endswith('.csv'):
            input_format = 'csv'
        elif input_file.endswith(('.xlsx', '.xls')):
            input_format = 'excel'
        elif input_file.endswith('.json'):
            input_format = 'json'
        else:
            print("Error: Unknown input format")
            return False
    
    # Detect output format
    if output_format == 'auto':
        if output_file.endswith('.csv'):
            output_format = 'csv'
        elif output_file.endswith(('.xlsx', '.xls')):
            output_format = 'excel'
        elif output_file.endswith('.json'):
            output_format = 'json'
        else:
            print("Error: Unknown output format")
            return False
    
    try:
        # Read input
        if input_format == 'csv':
            df = pd.read_csv(input_file)
        elif input_format == 'excel':
            df = pd.read_excel(input_file)
        elif input_format == 'json':
            df = pd.read_json(input_file)
        else:
            print(f"Error: Unsupported input format {input_format}")
            return False
        
        # Write output
        if output_format == 'csv':
            df.to_csv(output_file, index=False)
        elif output_format == 'excel':
            df.to_excel(output_file, index=False)
        elif output_format == 'json':
            df.to_json(output_file, orient='records', indent=4)
        else:
            print(f"Error: Unsupported output format {output_format}")
            return False
        
        print(f"Successfully processed {input_file} to {output_file}")
        return True
    except Exception as e:
        print(f"Error: {e}")
        return False

# Usage
process_data('sales.csv', 'sales_report.xlsx')
process_data('data.json', 'data.csv')
```

---

### Practical Examples

**Example 1: Data Pipeline with Processing**:

```python
import pandas as pd

# Step 1: Read data
def read_data():
    print("Reading sales.csv...")
    return pd.read_csv('sales.csv')

# Step 2: Process data
def process_data(df):
    print("Processing data...")
    # Add a 'Total' column
    df['Total'] = df['Quantity'] * df['Unit_Price']
    
    # Calculate sales by region
    region_summary = df.groupby('Region')['Total'].sum().reset_index()
    region_summary.columns = ['Region', 'Total_Sales']
    
    # Calculate sales by product
    product_summary = df.groupby('Product')['Total'].sum().reset_index()
    product_summary.columns = ['Product', 'Total_Sales']
    
    return region_summary, product_summary

# Step 3: Write output
def write_output(region_summary, product_summary):
    print("Writing outputs...")
    region_summary.to_excel('region_sales.xlsx', index=False)
    product_summary.to_excel('product_sales.xlsx', index=False)
    print("Outputs written successfully!")

# Main pipeline
def main():
    print("=" * 50)
    print("SALES DATA PROCESSING PIPELINE")
    print("=" * 50)
    
    try:
        df = read_data()
        region_summary, product_summary = process_data(df)
        write_output(region_summary, product_summary)
        print("Pipeline completed successfully!")
    except Exception as e:
        print(f"Pipeline failed: {e}")

if __name__ == "__main__":
    main()
```

**Example 2: Batch File Processing**:

```python
import pandas as pd
import glob
import os

def process_batch_files():
    """
    Process all CSV files in the 'input' folder.
    Combine them, add a 'Source' column, and write to a single file.
    """
    folder = 'input'
    output_file = 'combined_data.xlsx'
    
    # Find all CSV files
    csv_files = glob.glob(os.path.join(folder, '*.csv'))
    
    if not csv_files:
        print("No CSV files found in the input folder")
        return
    
    all_data = []
    
    for file in csv_files:
        print(f"Processing {file}...")
        df = pd.read_csv(file)
        df['Source'] = os.path.basename(file)  # Add source column
        all_data.append(df)
    
    # Combine all data
    combined = pd.concat(all_data, ignore_index=True)
    
    # Write output
    combined.to_excel(output_file, index=False)
    print(f"Combined {len(csv_files)} files into {output_file}")
    print(f"Total rows: {len(combined)}")

# Usage
process_batch_files()
```

---

### Hands-on Coding Exercises

**Exercise 2.13** – CSV to Excel converter:
```python
# 1. Read a CSV file using pandas
# 2. Add a new column with calculated values
# 3. Write the data to an Excel file
# 4. Include error handling
```

**Exercise 2.14** – Multi-format converter:
```python
# 1. Ask the user for input filename and output filename
# 2. Detect the formats based on file extensions
# 3. Convert from one format to another
# 4. Support CSV, Excel, and JSON
```

**Exercise 2.15** – Data pipeline:
```python
# 1. Read data from CSV
# 2. Perform some processing (filter, aggregate, etc.)
# 3. Write the results to Excel
# 4. Log the steps
```

---

### Mini Quiz

1. What is a data pipeline?
2. Why is modularity important in data processing?
3. How do you detect the format of a file based on its extension?
4. What is the advantage of using functions for each step of a pipeline?
5. How do you handle errors in a data pipeline?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Writing monolithic scripts that do everything | Break the pipeline into reusable functions |
| Not handling errors – pipeline fails unexpectedly | Use try/except at each step |
| Not logging progress – difficult to debug | Add print statements or use the `logging` module |
| Hardcoding file paths | Use variables or configuration files |
| Not validating data before processing | Check for missing values, invalid data types |

---

### Interview Questions

1. **How would you build a data pipeline in Python?**  
   *Answer*: I would create a series of functions: one for reading data, one or more for processing, and one for writing the output. I would use try/except for error handling and log each step. I would make the pipeline configurable with file paths as parameters.

2. **What are the key considerations when building a data pipeline?**  
   *Answer*: Data quality, error handling, logging, performance (for large datasets), and flexibility (ability to handle different input formats).

3. **How would you process data from multiple CSV files and combine them?**  
   *Answer*: I would use `glob` to find all CSV files in a folder, loop through them, read each into a DataFrame, add a source identifier, and concatenate them using `pd.concat()`.

---

### Assignment and Mini Project

**Assignment 2.5** – Data pipeline implementation:
```python
# Create a complete data pipeline:
# 1. Read data from a CSV file
# 2. Clean the data (remove duplicates, handle missing values)
# 3. Calculate summary statistics (total, average, min, max)
# 4. Write the summary to an Excel file
# 5. Write the cleaned data to a new CSV file
# 6. Include error handling and logging
```

**Mini Project** – Sales Data Pipeline:
Build a complete data pipeline that:
1. Reads sales data from a CSV file (or multiple files).
2. Cleans the data:
   - Remove rows with missing values.
   - Remove duplicates.
   - Convert date columns to datetime.
3. Enriches the data:
   - Calculate profit (Revenue - Cost).
   - Calculate profit margin.
   - Add a 'Year' column from the date.
4. Aggregates the data:
   - Total sales by product.
   - Total sales by region.
   - Total sales by year.
5. Writes the results to an Excel file with separate sheets for each summary.
6. Generates a summary report (text file) with key statistics.
7. Handles errors gracefully and logs progress.

---

### Summary and Revision Notes

- Data pipelines combine reading, processing, and writing data.
- Use modular functions for each step.
- Handle errors at each step with try/except.
- Log progress for debugging.
- Support multiple file formats (CSV, Excel, JSON).
- Always validate data before processing.

---

## Lesson 2.6 – Working with APIs

### Concept Explanation

**API (Application Programming Interface)** allows different software applications to communicate with each other. In data analytics, APIs are used to fetch data from external services – weather data, financial data, social media data, etc.

**Key concepts**:
- **Endpoint**: The URL where the API is accessed.
- **Request**: The call you make to the API.
- **Response**: The data returned by the API (often in JSON format).
- **HTTP Methods**:
  - `GET` – retrieve data.
  - `POST` – send data.
  - `PUT` – update data.
  - `DELETE` – delete data.
- **Authentication**: Many APIs require an API key or token.

**Common APIs for data analytics**:
- **Financial**: Alpha Vantage, Yahoo Finance.
- **Weather**: OpenWeatherMap, WeatherAPI.
- **Social**: Twitter API, Facebook Graph API.
- **News**: NewsAPI.
- **Data**: REST APIs from various data providers.

**Python library**: `requests` – the most popular library for making HTTP requests.

**Installation**:
```bash
pip install requests
```

---

### Importance and Real-World Use Cases

- **Why it matters**: APIs are the gateway to live data. They enable you to automate data collection from external sources, build real-time dashboards, and integrate with other systems.

- **Use cases**:
  - A **data analyst** pulls weather data from OpenWeatherMap to analyse sales patterns.
  - A **financial analyst** uses the Alpha Vantage API to get stock prices.
  - A **data engineer** pulls data from a company's internal API to build a data warehouse.

---

### Step-by-Step Demonstration

**Making a Simple GET Request**:

```python
import requests

# Make a GET request
response = requests.get('https://api.github.com')

# Check status
if response.status_code == 200:
    print("Success!")
    data = response.json()
    print(data)
else:
    print(f"Error: {response.status_code}")
```

**GET Request with Parameters**:

```python
import requests

# Parameters
params = {
    'q': 'python',
    'sort': 'stars'
}

response = requests.get('https://api.github.com/search/repositories', params=params)

if response.status_code == 200:
    data = response.json()
    print(f"Found {data['total_count']} repositories")
    
    for repo in data['items'][:5]:
        print(f"- {repo['name']}: {repo['stargazers_count']} stars")
```

**GET Request with API Key**:

```python
import requests

# Weather API example (requires free API key)
api_key = 'YOUR_API_KEY'
city = 'London'

url = f'https://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}'

response = requests.get(url)

if response.status_code == 200:
    data = response.json()
    print(f"City: {data['name']}")
    print(f"Temperature: {data['main']['temp'] - 273.15:.2f}°C")
    print(f"Humidity: {data['main']['humidity']}%")
else:
    print(f"Error: {response.status_code}")
```

**Handling Pagination**:

```python
import requests

def get_all_pages(base_url, params=None):
    """
    Handle API pagination by following next page links.
    """
    results = []
    url = base_url
    page = 1
    
    while url:
        print(f"Fetching page {page}...")
        response = requests.get(url, params=params)
        
        if response.status_code != 200:
            print(f"Error: {response.status_code}")
            break
        
        data = response.json()
        results.extend(data.get('items', []))
        
        # Check if there's a next page (depends on API)
        # Some APIs use 'next', others use 'page' parameter
        next_url = data.get('next')
        if next_url:
            url = next_url
        else:
            # If no next_url, try incrementing page parameter
            page += 1
            params = params or {}
            params['page'] = page
            # This is a simplified example; actual implementation depends on the API
            break
        
    return results

# Usage (GitHub API)
results = get_all_pages('https://api.github.com/search/repositories', {'q': 'python'})
print(f"Total items: {len(results)}")
```

**Error Handling in API Calls**:

```python
import requests

def safe_api_call(url, params=None, max_retries=3):
    """
    Make a safe API call with retries and error handling.
    """
    for attempt in range(max_retries):
        try:
            response = requests.get(url, params=params, timeout=10)
            response.raise_for_status()  # Raises an exception for 4xx/5xx responses
            return response.json()
        except requests.exceptions.Timeout:
            print(f"Timeout, retrying ({attempt + 1}/{max_retries})...")
        except requests.exceptions.RequestException as e:
            print(f"Request error: {e}")
            print(f"Retrying ({attempt + 1}/{max_retries})...")
        except Exception as e:
            print(f"Unexpected error: {e}")
            break
    
    print("All attempts failed")
    return None

# Usage
data = safe_api_call('https://api.github.com')
```

**Real API Example: Alpha Vantage (Stock Data)**:

```python
import requests

def get_stock_data(symbol, api_key):
    """
    Fetch stock data from Alpha Vantage API.
    """
    url = 'https://www.alphavantage.co/query'
    params = {
        'function': 'TIME_SERIES_DAILY',
        'symbol': symbol,
        'apikey': api_key
    }
    
    response = requests.get(url, params=params)
    data = response.json()
    
    if 'Time Series (Daily)' in data:
        time_series = data['Time Series (Daily)']
        dates = sorted(time_series.keys(), reverse=True)[:10]  # Last 10 days
        
        print(f"Stock: {symbol}")
        print("Date | Open | High | Low | Close")
        for date in dates:
            values = time_series[date]
            print(f"{date} | {values['1. open']} | {values['2. high']} | "
                  f"{values['3. low']} | {values['4. close']}")
    else:
        print("No data found")

# Usage (requires free API key from alphavantage.co)
# get_stock_data('AAPL', 'YOUR_API_KEY')
```

---

### Practical Examples

**Example 1: Fetching Currency Exchange Rates**:

```python
import requests

def get_exchange_rate(base_currency, target_currency):
    """
    Fetch exchange rate from an API.
    """
    url = f'https://api.exchangerate-api.com/v4/latest/{base_currency}'
    
    response = requests.get(url)
    
    if response.status_code == 200:
        data = response.json()
        if target_currency in data['rates']:
            rate = data['rates'][target_currency]
            print(f"1 {base_currency} = {rate} {target_currency}")
            return rate
        else:
            print(f"Currency {target_currency} not found")
            return None
    else:
        print(f"Error: {response.status_code}")
        return None

get_exchange_rate('USD', 'EUR')
get_exchange_rate('GBP', 'INR')
```

**Example 2: Downloading Data from a REST API**:

```python
import requests
import csv

def fetch_and_save_data(api_url, output_file):
    """
    Fetch data from an API and save it to a CSV file.
    """
    response = requests.get(api_url)
    
    if response.status_code == 200:
        data = response.json()
        
        if data:
            # Assuming data is a list of dictionaries
            headers = data[0].keys()
            
            with open(output_file, 'w', newline='') as f:
                writer = csv.DictWriter(f, fieldnames=headers)
                writer.writeheader()
                writer.writerows(data)
            
            print(f"Data saved to {output_file}")
        else:
            print("No data received")
    else:
        print(f"Error: {response.status_code}")

# Usage (with a public API)
# fetch_and_save_data('https://jsonplaceholder.typicode.com/posts', 'posts.csv')
```

---

### Hands-on Coding Exercises

**Exercise 2.16** – Simple API request:
```python
# 1. Make a GET request to the GitHub API
# 2. Print the response status code
# 3. Print the response headers
# 4. Print the JSON response
```

**Exercise 2.17** – API with parameters:
```python
# 1. Search GitHub for repositories with a specific language
# 2. Sort by stars
# 3. Print the names and star counts
```

**Exercise 2.18** – API with authentication:
```python
# 1. Sign up for a free API key (OpenWeatherMap, etc.)
# 2. Make a request using the API key
# 3. Parse the response
# 4. Print the relevant data
```

---

### Mini Quiz

1. What does API stand for?
2. What is the purpose of the `requests` library?
3. What is an API key and why is it used?
4. What is the difference between GET and POST?
5. What should you check before parsing the response?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Hardcoding API keys in the script | Use environment variables or config files |
| Not handling rate limits | Add delays between requests |
| Not checking status codes | Always check `response.status_code` |
| Not handling timeouts | Set a timeout parameter |
| Exposing sensitive data in the code | Use environment variables for sensitive data |

---

### Interview Questions

1. **How do you make an API call in Python?**  
   *Answer*: Using the `requests` library: `response = requests.get(url)`. Parse the response with `response.json()`.

2. **What are the common HTTP methods used in APIs?**  
   *Answer*: GET (retrieve), POST (create), PUT (update), DELETE (delete).

3. **How do you handle API authentication?**  
   *Answer*: Many APIs use API keys passed as parameters or in headers: `headers = {'Authorization': f'Bearer {token}'}`.

---

### Assignment and Mini Project

**Assignment 2.6** – Weather data collector:
```python
# 1. Sign up for a free OpenWeatherMap API key
# 2. Write a function that takes a city name and returns the weather
# 3. Include temperature, humidity, and conditions
# 4. Handle errors gracefully
```

**Mini Project** – Stock Data Collector:
Create a program that:
1. Fetches stock data for a given symbol from Alpha Vantage or another API.
2. Stores the historical data in a CSV file.
3. Calculates:
   - Average price.
   - Highest price.
   - Lowest price.
   - Price change over time.
4. Generates a summary report.
5. Handles API errors and rate limits.

---

### Summary and Revision Notes

- APIs allow programs to communicate with external services.
- The `requests` library is used for HTTP requests.
- GET requests retrieve data.
- POST requests send data.
- Always check the status code.
- Parse JSON responses with `.json()`.
- Use API keys for authentication.
- Handle errors and rate limits.

---

## Lesson 2.7 – Downloading Online Data

### Concept Explanation

Beyond APIs, there are many ways to download online data:
- **Direct file downloads**: CSV, Excel, JSON, PDF files hosted on websites.
- **Web scraping**: Extracting data from HTML pages (covered in later phases).
- **Data portals**: Government and open data portals with download links.

**Key approaches**:
- **`requests`**: Downloading files directly.
- **`urllib`**: Another built-in library for downloads.
- **`wget`**: A command-line tool (can be called from Python).
- **`pandas`**: Directly reading online CSVs, Excel files, and JSON.

---

### Importance and Real-World Use Cases

- **Why it matters**: Much of the data you'll work with is publicly available online. Being able to download and process this data is a fundamental skill.

- **Use cases**:
  - A **data analyst** downloads daily COVID-19 data from a government portal.
  - A **data scientist** downloads a dataset from Kaggle using the Kaggle API.
  - A **financial analyst** downloads stock price CSV files from Yahoo Finance.

---

### Step-by-Step Demonstration

**Download a CSV File from the Web**:

```python
import requests

def download_csv(url, output_file):
    """
    Download a CSV file from a URL.
    """
    response = requests.get(url)
    
    if response.status_code == 200:
        with open(output_file, 'wb') as file:
            file.write(response.content)
        print(f"Successfully downloaded {output_file}")
        return True
    else:
        print(f"Error: {response.status_code}")
        return False

# Usage
url = 'https://raw.githubusercontent.com/datasets/covid-19/main/data/countries-aggregated.csv'
download_csv(url, 'covid_data.csv')
```

**Download a CSV and Load it Directly with Pandas**:

```python
import pandas as pd

# Read CSV directly from a URL
url = 'https://raw.githubusercontent.com/datasets/covid-19/main/data/countries-aggregated.csv'
df = pd.read_csv(url)

print("Downloaded and loaded successfully!")
print(df.head())
print(f"Shape: {df.shape}")
```

**Download an Excel File from the Web**:

```python
import pandas as pd

url = 'https://example.com/data.xlsx'
df = pd.read_excel(url)  # Works with pd.read_excel for URLs
print(df.head())
```

**Download a JSON File from the Web**:

```python
import requests
import json

url = 'https://jsonplaceholder.typicode.com/posts'
response = requests.get(url)

if response.status_code == 200:
    data = response.json()
    with open('posts.json', 'w') as file:
        json.dump(data, file, indent=4)
    print("JSON file downloaded successfully!")
```

**Download a ZIP File and Extract**:

```python
import requests
import zipfile
import io

def download_and_extract_zip(url, extract_to='.'):
    """
    Download a ZIP file and extract its contents.
    """
    response = requests.get(url)
    
    if response.status_code == 200:
        with zipfile.ZipFile(io.BytesIO(response.content)) as zip_file:
            zip_file.extractall(extract_to)
        print(f"Downloaded and extracted to {extract_to}")
        return True
    else:
        print(f"Error: {response.status_code}")
        return False

# Usage (example with a public ZIP file)
# download_and_extract_zip('https://example.com/data.zip')
```

**Downloading with Authentication**:

```python
import requests

def download_with_auth(url, output_file, username, password):
    """
    Download a file with basic authentication.
    """
    response = requests.get(url, auth=(username, password))
    
    if response.status_code == 200:
        with open(output_file, 'wb') as file:
            file.write(response.content)
        print(f"Successfully downloaded {output_file}")
    else:
        print(f"Error: {response.status_code}")

# Usage (with your credentials)
# download_with_auth('https://example.com/secure/data.csv', 'data.csv', 'user', 'pass')
```

**Using Kaggle API** (requires installation):

```bash
# Install Kaggle API
pip install kaggle

# Set up API credentials (download kaggle.json from your account)
```

```python
import os
import subprocess

def download_kaggle_dataset(dataset_path, output_dir='.'):
    """
    Download a dataset from Kaggle.
    """
    os.makedirs(output_dir, exist_ok=True)
    subprocess.run(['kaggle', 'datasets', 'download', dataset_path, '-p', output_dir])
    print(f"Dataset downloaded to {output_dir}")

# Usage
# download_kaggle_dataset('alexanderfreeman/useful-python-datasets')
```

---

### Practical Examples

**Example 1: Downloading Multiple Files**:

```python
import requests
import os

def download_all(urls, output_folder='downloads'):
    """
    Download multiple files from a list of URLs.
    """
    os.makedirs(output_folder, exist_ok=True)
    
    for url in urls:
        filename = os.path.basename(url)
        filepath = os.path.join(output_folder, filename)
        
        response = requests.get(url)
        if response.status_code == 200:
            with open(filepath, 'wb') as file:
                file.write(response.content)
            print(f"Downloaded: {filename}")
        else:
            print(f"Failed: {filename} - Error {response.status_code}")

# Example
urls = [
    'https://raw.githubusercontent.com/datasets/covid-19/main/data/countries-aggregated.csv',
    'https://raw.githubusercontent.com/datasets/covid-19/main/data/time-series-19-covid-combined.csv'
]
download_all(urls)
```

**Example 2: Downloading with Progress Bar**:

```python
import requests

def download_with_progress(url, output_file):
    """
    Download a file with a progress bar.
    """
    response = requests.get(url, stream=True)
    
    if response.status_code == 200:
        total_size = int(response.headers.get('content-length', 0))
        downloaded = 0
        
        with open(output_file, 'wb') as file:
            for chunk in response.iter_content(chunk_size=8192):
                if chunk:
                    file.write(chunk)
                    downloaded += len(chunk)
                    progress = (downloaded / total_size) * 100
                    print(f"\rProgress: {progress:.1f}%", end='')
        
        print("\nDownload completed!")
        return True
    else:
        print(f"Error: {response.status_code}")
        return False

# Usage
download_with_progress('https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf', 'sample.pdf')
```

---

### Hands-on Coding Exercises

**Exercise 2.19** – Download a CSV file:
```python
# 1. Find a public CSV file online (e.g., from data.gov)
# 2. Download it using requests
# 3. Save it to your local machine
# 4. Read it back and print the first 5 rows
```

**Exercise 2.20** – Direct pandas download:
```python
# 1. Find a public CSV or Excel file online
# 2. Read it directly using pandas
# 3. Print basic statistics
# 4. Save a copy locally
```

**Exercise 2.21** – Download multiple files:
```python
# 1. Create a list of 3-5 public file URLs
# 2. Download all of them
# 3. Check each file exists
```

---

### Mini Quiz

1. How do you download a file from the web using `requests`?
2. What is the advantage of using `pandas.read_csv()` with a URL?
3. How do you download a ZIP file and extract it?
4. What is the Kaggle API used for?
5. How do you handle authentication when downloading files?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not handling download failures | Use try/except and check status codes |
| Downloading large files without chunking | Use `stream=True` and `iter_content()` for large files |
| Not respecting rate limits | Add delays between requests |
| Hardcoding URLs | Use variables or config files |
| Not checking if the file was downloaded | Verify file size after download |

---

### Interview Questions

1. **How do you download a file from the internet in Python?**  
   *Answer*: Using the `requests` library: `response = requests.get(url)`, then write the content to a file using `file.write(response.content)`.

2. **How do you download a large file without using too much memory?**  
   *Answer*: Use `stream=True` and `iter_content()` to download in chunks: `requests.get(url, stream=True)` and iterate over `response.iter_content(chunk_size=8192)`.

3. **How can you read a CSV file directly from a URL without saving it?**  
   *Answer*: Using `pandas.read_csv(url)` which reads the file directly from the web into a DataFrame.

---

### Assignment and Mini Project

**Assignment 2.7** – Data downloader:
```python
# 1. Download a public dataset from the web
# 2. Save it locally
# 3. Load it back and display basic information
# 4. Generate a summary report
```

**Mini Project** – Automated Data Download Pipeline:
Create a program that:
1. Reads a list of URLs from a configuration file.
2. Downloads each file to a specified folder.
3. Handles different file types (CSV, Excel, JSON, ZIP).
4. Extracts ZIP files automatically.
5. Logs all activities.
6. Sends a summary email (or prints a summary) with:
   - Files downloaded.
   - File sizes.
   - Any errors encountered.

---

### Summary and Revision Notes

- `requests` is used to download files from the web.
- Use `response.content` to write binary files.
- Use `pandas.read_csv()` and `pandas.read_excel()` directly with URLs.
- For large files, use `stream=True` and chunked reading.
- Handle authentication with `auth` parameter.
- Use `zipfile` for ZIP extraction.
- The Kaggle API can be used to download datasets.

---

## Final Phase 2 Assessment

Now that you have completed all lessons, test your overall understanding.

### Self-Evaluation Checklist

-  I can read and write CSV files using the `csv` module.

-  I can read and write Excel files using `pandas` and `openpyxl`.

-  I can read and write JSON files using the `json` module.

-  I can read and process text files.

-  I can build a data pipeline that reads from one format and writes to another.

-  I can make API calls using the `requests` library.

-  I can download online data from various sources.

---

### Answers to Mini Quizzes

**Lesson 2.1**: 1. Comma-Separated Values. 2. To read CSV files row by row. 3. `reader()` returns lists; `DictReader()` returns dictionaries. 4. Use `next(reader)` or skip the first row. 5. Prevents extra blank lines on Windows.

**Lesson 2.2**: 1. `openpyxl` and `pandas`. 2. `pandas` is simpler for data; `openpyxl` offers more Excel features. 3. The entire Excel file. 4. `pd.read_excel(file, sheet_name='Sheet2')`. 5. Using `pd.ExcelWriter`.

**Lesson 2.3**: 1. JavaScript Object Notation. 2. `load()` reads from file; `loads()` reads from string. 3. `dump()` writes to file; `dumps()` writes to string. 4. Use dictionary key access. 5. JSON Lines – one JSON object per line.

**Lesson 2.4**: 1. `r` = read, `w` = write (overwrites). 2. All lines as a list. 3. Auto-closes files. 4. Specifies character encoding. 5. Use `mode='a'`.

**Lesson 2.5**: 1. A series of steps that read, process, and write data. 2. Makes code reusable and testable. 3. Check the file extension. 4. Reusability and maintainability. 5. Use try/except.

**Lesson 2.6**: 1. Application Programming Interface. 2. To make HTTP requests. 3. For authentication and access control. 4. GET retrieves; POST sends. 5. The status code.

**Lesson 2.7**: 1. Using `requests.get()` and `file.write()`. 2. Reads directly without saving. 3. Use `requests` + `zipfile`. 4. To download Kaggle datasets. 5. Use the `auth` parameter.

---

**Congratulations!** You have completed Phase 2 of Python for Data Analytics. You now have a solid foundation in working with real-world data – reading, writing, and processing files in various formats, connecting to APIs, and downloading online data. Keep practising!



----




<br/><br/><br/>
<center> <b>Happy Learning! 😊</b> </center>
