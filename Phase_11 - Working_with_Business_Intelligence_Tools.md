# Phase 11: Working with Business Intelligence Tools

Welcome to **Phase 11** – the bridge between Python and the world of Business Intelligence (BI) tools! You have now mastered Python for data analytics, statistics, automation, and SQL integration. But in the real world, you often need to connect your Python workflows to the BI platforms that your stakeholders use every day: **Excel**, **Power BI**, and **Tableau**.

This phase is about making Python the **engine** that powers your BI ecosystem. You will learn how to:
- Use Python to supercharge Excel (automating reports, applying advanced analytics).
- Connect Python directly to **Power BI** using Python visuals and dataflows.
- Integrate Python with **Tableau** for data preparation and advanced calculations.
- Export professional reports from Python to formats that BI tools consume.
- Build end-to-end analytics workflows that combine Python's power with BI's visualisation capabilities.

By the end of this phase, you will be able to seamlessly integrate Python into your organisation's BI stack, making you an invaluable asset in any data team.

Let's bridge the gap!

---

## Lesson 11.1 – Python with Excel

### Concept Explanation

Excel is the most widely used data tool in the world. While it has limitations with large datasets and complex calculations, combining Excel with Python gives you the best of both worlds: Excel's accessibility and Python's power.

**Key integration points**:
1. **Reading Excel files**: Load data from Excel into Pandas for cleaning and analysis.
2. **Writing Excel files**: Export Python results back to Excel with formatting.
3. **Excel Automation**: Use Python to automate repetitive Excel tasks (formatting, formula insertion, chart creation).
4. **Excel as a reporting layer**: Use Python to calculate complex metrics and output them to a beautifully formatted Excel report.
5. **Excel Add-Ins**: Use `xlwings` to control Excel from Python (run macros, write formulas, etc.).

**Key libraries**:
- **`pandas`**: Read/write Excel files.
- **`openpyxl`**: Advanced Excel formatting and manipulation.
- **`xlwings`**: Control the Excel application (run macros, interact with open workbooks).
- **`xlsxwriter`**: Create Excel files with advanced formatting and charts.

---

### Importance and Real-World Use Cases

- **Why it matters**: Excel is the lingua franca of business. Many stakeholders expect reports in Excel format. Automating Excel with Python saves hours of manual work.

- **Use cases**:
  - A **financial analyst** uses Python to pull data from a database, perform complex calculations, and generate a formatted Excel report with charts.
  - A **data analyst** uses Python to clean and transform messy Excel files from multiple departments and consolidate them.
  - A **consultant** uses Python to generate Excel dashboards with pivot tables and conditional formatting.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
from openpyxl import load_workbook
from openpyxl.styles import Font, PatternFill, Border, Side, Alignment
from openpyxl.utils.dataframe import dataframe_to_rows
import xlsxwriter
from datetime import datetime

# 1. Reading Excel files
def read_excel_with_pandas(filename, sheet_name=0):
    """Read an Excel file into a pandas DataFrame."""
    try:
        df = pd.read_excel(filename, sheet_name=sheet_name)
        print(f"Successfully loaded {len(df)} rows from {filename}")
        return df
    except Exception as e:
        print(f"Error reading Excel file: {e}")
        return None

# 2. Writing a simple Excel report
def create_simple_excel_report(data, filename):
    """Create a simple Excel report from a DataFrame."""
    df = pd.DataFrame(data)
    
    with pd.ExcelWriter(filename, engine='xlsxwriter') as writer:
        df.to_excel(writer, sheet_name='Data', index=False)
        
        # Access the workbook and worksheet
        workbook = writer.book
        worksheet = writer.sheets['Data']
        
        # Add a chart
        chart = workbook.add_chart({'type': 'column'})
        chart.add_series({
            'values': f'=Data!$B$2:$B${len(df)+1}',
            'categories': f'=Data!$A$2:$A${len(df)+1}',
            'name': 'Sales'
        })
        chart.set_title({'name': 'Sales by Product'})
        chart.set_x_axis({'name': 'Product'})
        chart.set_y_axis({'name': 'Sales'})
        worksheet.insert_chart('D2', chart)
        
        # Auto-fit columns
        for i, col in enumerate(df.columns):
            max_len = max(df[col].astype(str).map(len).max(), len(col)) + 2
            worksheet.set_column(i, i, max_len)
    
    print(f"Excel report saved as {filename}")

# 3. Creating a formatted Excel report with openpyxl
def create_formatted_excel_report(df, filename, sheet_name='Report'):
    """Create a professionally formatted Excel report using openpyxl."""
    
    # Create a workbook
    wb = load_workbook(filename) if os.path.exists(filename) else openpyxl.Workbook()
    ws = wb.active
    ws.title = sheet_name
    
    # Write headers
    headers = list(df.columns)
    for col_idx, header in enumerate(headers, 1):
        cell = ws.cell(row=1, column=col_idx, value=header)
        cell.font = Font(bold=True, color='FFFFFF', size=11)
        cell.fill = PatternFill(start_color='4472C4', end_color='4472C4', fill_type='solid')
        cell.alignment = Alignment(horizontal='center')
    
    # Write data
    for row_idx, row in enumerate(df.values, 2):
        for col_idx, value in enumerate(row, 1):
            cell = ws.cell(row=row_idx, column=col_idx, value=value)
            if isinstance(value, (int, float)):
                cell.number_format = '#,##0.00'
            cell.alignment = Alignment(horizontal='center' if isinstance(value, (int, float)) else 'left')
    
    # Apply borders
    thin_border = Border(
        left=Side(style='thin'),
        right=Side(style='thin'),
        top=Side(style='thin'),
        bottom=Side(style='thin')
    )
    for row in ws.iter_rows(min_row=1, max_row=len(df)+1, min_col=1, max_col=len(headers)):
        for cell in row:
            cell.border = thin_border
    
    # Auto-fit columns
    for col in ws.columns:
        max_length = 0
        for cell in col:
            try:
                if len(str(cell.value)) > max_length:
                    max_length = len(str(cell.value))
            except:
                pass
        adjusted_width = min(max_length + 2, 50)
        ws.column_dimensions[col[0].column_letter].width = adjusted_width
    
    wb.save(filename)
    print(f"Formatted report saved as {filename}")

# 4. Using xlwings to control Excel (conceptual)
def use_xlwings_example():
    """Use xlwings to interact with an open Excel workbook."""
    # Note: Requires xlwings to be installed and Excel to be open
    # import xlwings as xw
    
    # wb = xw.Book.active
    # ws = wb.sheets[0]
    # ws.range('A1').value = 'Hello from Python!'
    # ws.range('A1').color = (255, 0, 0)  # Red background
    # wb.save()
    print("xlwings example (requires Excel open)")

# 5. Excel automation: consolidating multiple files
def consolidate_excel_files(folder, output_file):
    """Consolidate all Excel files in a folder into a single file."""
    import glob
    import os
    
    all_data = []
    file_list = glob.glob(os.path.join(folder, '*.xlsx'))
    
    for file_path in file_list:
        df = pd.read_excel(file_path)
        df['Source_File'] = os.path.basename(file_path)
        all_data.append(df)
        print(f"Loaded {os.path.basename(file_path)}")
    
    if all_data:
        combined = pd.concat(all_data, ignore_index=True)
        combined.to_excel(output_file, index=False)
        print(f"Consolidated {len(file_list)} files into {output_file}")
    else:
        print("No Excel files found.")
```

**Practical Example: Monthly Sales Report Generator**:

```python
def generate_monthly_sales_report():
    """Generate a formatted monthly sales report."""
    
    # 1. Load data (simulated)
    np.random.seed(42)
    months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun']
    products = ['Product A', 'Product B', 'Product C', 'Product D']
    
    data = {
        'Month': np.repeat(months, 4),
        'Product': np.tile(products, 6),
        'Sales': np.random.randint(1000, 5000, 24),
        'Units': np.random.randint(10, 100, 24),
        'Region': np.random.choice(['North', 'South', 'East', 'West'], 24)
    }
    df = pd.DataFrame(data)
    
    # 2. Calculate summary
    summary = df.groupby('Month')['Sales'].sum().reset_index()
    summary.columns = ['Month', 'Total_Sales']
    
    # 3. Create Excel report
    with pd.ExcelWriter('monthly_sales_report.xlsx', engine='xlsxwriter') as writer:
        # Raw data sheet
        df.to_excel(writer, sheet_name='Raw Data', index=False)
        
        # Summary sheet
        summary.to_excel(writer, sheet_name='Summary', index=False)
        
        # Pivot table sheet
        pivot = pd.pivot_table(df, values='Sales', index='Month', columns='Product', aggfunc='sum')
        pivot.to_excel(writer, sheet_name='Pivot')
        
        # Format the summary sheet
        workbook = writer.book
        worksheet = writer.sheets['Summary']
        
        # Add a chart
        chart = workbook.add_chart({'type': 'column'})
        chart.add_series({
            'values': '=Summary!$B$2:$B$7',
            'categories': '=Summary!$A$2:$A$7',
            'name': 'Total Sales'
        })
        chart.set_title({'name': 'Monthly Sales Trend'})
        chart.set_x_axis({'name': 'Month'})
        chart.set_y_axis({'name': 'Sales ($)'})
        worksheet.insert_chart('D2', chart)
    
    print("Monthly sales report generated successfully!")
```

---

### Practical Examples

- **Example 1**: A financial analyst uses Python to generate a formatted Excel report with charts and pivot tables.
- **Example 2**: A data analyst uses Python to consolidate monthly reports from multiple departments.
- **Example 3**: A business analyst uses Python to clean and transform messy Excel data.

---

### Hands-on Coding Exercises

**Exercise 11.1** – Excel automation:
```python
# 1. Load a dataset (e.g., 'tips' or 'titanic').
# 2. Create an Excel report with:
#    - Raw data sheet.
#    - Summary statistics sheet.
#    - A chart of a key metric.
#    - Professional formatting (headers, borders, column widths).
# 3. Save the report.
```

---

### Mini Quiz

1. What are the main libraries for working with Excel in Python?
2. How do you read an Excel file into a Pandas DataFrame?
3. What is the advantage of using `openpyxl` over `pandas` for Excel?
4. How do you add a chart to an Excel file using `xlsxwriter`?
5. What is `xlwings` used for?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using pandas for complex Excel formatting | Use `openpyxl` or `xlsxwriter` for formatting |
| Hardcoding file paths | Use `os.path.join()` or `pathlib` |
| Not handling large Excel files | Use `chunksize` or `read_excel` with `nrows` |
| Forgetting to close ExcelWriter | Use `with` statements |

---

### Interview Questions

1. **How do you automate Excel reporting with Python?**  
   *Answer*: By using `pandas` to process data and `openpyxl` or `xlsxwriter` to format and output Excel files with charts, formulas, and styles.

2. **What is the difference between `openpyxl` and `xlsxwriter`?**  
   *Answer*: `openpyxl` can read and write `.xlsx` files and supports modifying existing files. `xlsxwriter` is write-only but offers more advanced formatting and chart options.

3. **How do you add a formula to an Excel cell using Python?**  
   *Answer*: Using `openpyxl`, you can set the cell value to a formula string: `ws['A1'] = '=SUM(B1:B10)'`.

---

### Assignment and Mini Project

**Assignment 11.1** – Excel report generator:
```python
# 1. Load the 'titanic' dataset.
# 2. Create an Excel report with:
#    - A raw data sheet.
#    - A summary sheet with descriptive statistics.
#    - A pivot table of survival by class and sex.
#    - A chart showing survival rate by class.
#    - Professional formatting (colours, borders, column widths).
# 3. Save the report with a timestamp in the filename.
```

---

### Summary and Revision Notes

- `pandas` for reading/writing Excel.
- `openpyxl` for advanced formatting.
- `xlsxwriter` for creating Excel files with charts.
- `xlwings` for controlling the Excel application.
- Always use `with` statements for file operations.

---

## Lesson 11.2 – Python with Power BI

### Concept Explanation

**Power BI** is a leading business intelligence tool from Microsoft. Python integration with Power BI has become increasingly powerful, allowing you to use Python for:
- **Data Preparation**: Use Python scripts in Power Query to clean and transform data.
- **Visualisations**: Create custom Python visuals using Matplotlib, Seaborn, or Plotly.
- **Data Analysis**: Run advanced analytics (statistics, machine learning) directly in Power BI.
- **Automation**: Use Python scripts to refresh data, generate reports, and push data to Power BI datasets.

**Key integration points**:
1. **Python in Power Query**: Run Python scripts during data loading.
2. **Python Visuals**: Create custom visuals using Python libraries.
3. **Power BI REST API**: Programmatically manage datasets, reports, and refreshes.
4. **Power BI Dataflows**: Use Python to push data into Power BI.

**Important**: Python integration in Power BI Desktop is enabled via the **Python scripting** feature (available in Power BI Desktop). The Python environment must be installed and configured.

---

### Importance and Real-World Use Cases

- **Why it matters**: Power BI is excellent for visualisation and reporting, but it has limitations with complex data transformations and advanced analytics. Python fills these gaps.

- **Use cases**:
  - A **data analyst** uses Python in Power Query to perform complex data transformations (e.g., sentiment analysis, anomaly detection).
  - A **data scientist** creates custom Python visuals for advanced visualisations not available in Power BI.
  - A **BI developer** uses Python to automate Power BI dataset refreshes via the REST API.

---

### Step-by-Step Demonstration

```python
# 1. Python in Power Query (conceptual)
# In Power Query Editor, you can add a Python script step:

# Example Python script in Power Query:
"""
import pandas as pd

# The dataset is passed as 'dataset'
df = dataset

# Perform transformations
df['Sales_Squared'] = df['Sales'] ** 2
df['Profit_Ratio'] = df['Profit'] / df['Sales']

# Return the transformed dataset
output = df
"""

# 2. Python Visual in Power BI (conceptual)
# In Power BI Desktop, add a Python visual:
"""
import matplotlib.pyplot as plt
import seaborn as sns

# The dataset is passed as 'dataset'
plt.figure(figsize=(10, 6))
sns.barplot(data=dataset, x='Category', y='Sales')
plt.title('Sales by Category')
plt.xticks(rotation=45)

# The plot is automatically displayed
plt.show()
"""

# 3. Using Power BI REST API to manage datasets
def create_powerbi_dataset(dataset_name, table_data):
    """Create a dataset in Power BI using the REST API."""
    import requests
    import json
    
    # Power BI REST API endpoint
    url = "https://api.powerbi.com/v1.0/myorg/datasets"
    
    # Headers (requires authentication token)
    headers = {
        "Authorization": "Bearer YOUR_ACCESS_TOKEN",
        "Content-Type": "application/json"
    }
    
    # Dataset definition
    dataset = {
        "name": dataset_name,
        "tables": [
            {
                "name": "SalesData",
                "columns": [
                    {"name": "Category", "dataType": "String"},
                    {"name": "Sales", "dataType": "Double"}
                ]
            }
        ]
    }
    
    # response = requests.post(url, headers=headers, json=dataset)
    # print(f"Dataset created: {response.status_code}")
    print(f"Conceptual: Would create dataset '{dataset_name}'")

# 4. Pushing data to Power BI using REST API
def push_data_to_powerbi(dataset_id, table_name, data):
    """Push data to a Power BI dataset."""
    import requests
    import json
    
    url = f"https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/tables/{table_name}/rows"
    
    headers = {
        "Authorization": "Bearer YOUR_ACCESS_TOKEN",
        "Content-Type": "application/json"
    }
    
    payload = {
        "rows": data
    }
    
    # response = requests.post(url, headers=headers, json=payload)
    # print(f"Data pushed: {response.status_code}")
    print("Conceptual: Would push data to Power BI")

# 5. Automating Power BI refreshes
def trigger_powerbi_refresh(dataset_id):
    """Trigger a refresh of a Power BI dataset."""
    import requests
    
    url = f"https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/refreshes"
    
    headers = {
        "Authorization": "Bearer YOUR_ACCESS_TOKEN"
    }
    
    # response = requests.post(url, headers=headers)
    # print(f"Refresh triggered: {response.status_code}")
    print("Conceptual: Would trigger Power BI refresh")

# 6. Python script for Power BI Dataflow (conceptual)
def clean_data_for_powerbi(df):
    """Clean data before loading to Power BI."""
    # Remove duplicates
    df = df.drop_duplicates()
    
    # Handle missing values
    df = df.fillna({
        'Sales': 0,
        'Quantity': 0,
        'Category': 'Unknown'
    })
    
    # Add calculated columns
    df['Total'] = df['Sales'] * df['Quantity']
    
    return df
```

**Setting up Python in Power BI Desktop**:

```python
# Steps to set up Python for Power BI:
"""
1. Install Python (3.7+ recommended).
2. Install required libraries: pandas, matplotlib, seaborn, numpy, scikit-learn, etc.
3. In Power BI Desktop:
   - Go to File > Options and Settings > Options.
   - In the Python scripting section, set the Python home directory.
   - Restart Power BI Desktop.
4. You can now use Python scripts in Power Query and Python visuals.
"""
```

**Practical Example: Advanced Python Visual in Power BI**:

```python
# Python visual in Power BI for advanced analytics
"""
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.ensemble import RandomForestRegressor

# dataset is provided by Power BI
df = dataset

# 1. Data preparation
X = df[['Feature1', 'Feature2', 'Feature3']]
y = df['Target']

# 2. Model training (simple example)
model = RandomForestRegressor(n_estimators=100)
model.fit(X, y)

# 3. Feature importance plot
importance = model.feature_importances_
features = X.columns

plt.figure(figsize=(10, 6))
plt.bar(features, importance)
plt.title('Feature Importance')
plt.xlabel('Features')
plt.ylabel('Importance')
plt.show()
"""
```

---

### Practical Examples

- **Example 1**: Using Python in Power Query to clean and transform data before loading.
- **Example 2**: Creating custom Python visuals for advanced visualisations.
- **Example 3**: Automating Power BI dataset refreshes using the REST API.

---

### Hands-on Coding Exercises

**Exercise 11.2** – Python in Power BI:
```python
# 1. Install Python and required libraries.
# 2. In Power BI Desktop, enable Python scripting.
# 3. Create a Python visual that plots a histogram of a numeric column.
# 4. Create a Python script in Power Query that adds a calculated column.
```

---

### Mini Quiz

1. How do you enable Python in Power BI Desktop?
2. What is the purpose of Python in Power Query?
3. How do you create a Python visual in Power BI?
4. What is the Power BI REST API used for?
5. Why would you use Python for data preparation in Power BI?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not installing required Python libraries | Install all libraries needed for your scripts |
| Forgetting to set the Python home directory | Configure Python in Power BI options |
| Using Python for simple transformations that Power Query can do | Use Python for complex transformations only |
| Not handling errors in Python scripts | Add error handling to your Python code |

---

### Interview Questions

1. **How do you integrate Python with Power BI?**  
   *Answer*: Through Python scripting in Power Query for data transformation, Python visuals for custom visualisations, and the Power BI REST API for automation and data management.

2. **What are the advantages of using Python in Power BI?**  
   *Answer*: Python provides advanced data transformation capabilities, custom visualisations, and access to a wide range of analytics libraries.

3. **How do you automate Power BI refreshes with Python?**  
   *Answer*: Using the Power BI REST API to trigger refreshes programmatically.

---

### Assignment and Mini Project

**Assignment 11.2** – Power BI Python integration:
```python
# 1. Install Python and set up Power BI Desktop for Python scripting.
# 2. Load a dataset into Power BI.
# 3. Create a Python script in Power Query that:
#    - Removes duplicates.
#    - Handles missing values.
#    - Adds a calculated column.
# 4. Create a Python visual that:
#    - Creates a scatter plot with a regression line.
#    - Uses Seaborn for styling.
# 5. Publish the report to Power BI Service (if available).
```

---

### Summary and Revision Notes

- Python can be used in Power Query for data transformation.
- Python visuals allow custom visualisations in Power BI.
- The Power BI REST API enables automation and data management.
- Configure Python in Power BI Desktop under Options.

---

## Lesson 11.3 – Python with Tableau

### Concept Explanation

Tableau is a leading data visualisation tool. Python integration with Tableau has grown significantly, especially with **Tableau Prep** and **Tableau Server**.

**Key integration points**:
1. **Tableau Prep**: Use Python scripts for advanced data preparation (via Prep's Python integration).
2. **Tableau Calculations**: Use Python to create complex calculations (though limited).
3. **Tableau Server REST API**: Programmatically manage Tableau content.
4. **Data Extraction**: Use Python to generate `.hyper` extracts for Tableau.
5. **External Services**: Use TabPy (Tableau Python Server) for advanced analytics and predictive modelling.

**TabPy (Tableau Python Server)**:
- TabPy is a Tableau extension that allows you to run Python scripts from Tableau calculated fields.
- This enables predictive analytics, statistical modelling, and complex calculations directly in Tableau.

---

### Importance and Real-World Use Cases

- **Why it matters**: Tableau is excellent for visualisation, but Python provides advanced analytics that Tableau cannot perform natively.

- **Use cases**:
  - A **data analyst** uses TabPy to calculate customer lifetime value (CLV) directly in Tableau.
  - A **data scientist** uses Python in Tableau Prep for advanced data cleaning.
  - A **BI developer** uses the Tableau REST API to automate content management.

---

### Step-by-Step Demonstration

```python
# 1. Tableau Prep Python Integration (conceptual)
# In Tableau Prep, you can add a Python script step:
"""
import pandas as pd

# The data is passed as 'df'
df = dataset

# Perform transformations
df['Sales_Flag'] = df['Sales'].apply(lambda x: 'High' if x > 1000 else 'Low')

# Return the transformed data
output = df
"""

# 2. TabPy - Tableau Python Server (conceptual)
# Install TabPy: pip install tabpy
# Start TabPy: tabpy

# Python script for TabPy endpoint:
"""
from tabpy.tabpy_tools.client import Client

# Define a function
def predict_sales(input_data):
    # Simple linear prediction
    return [x * 1.1 for x in input_data]

# Deploy to TabPy
client = Client()
client.deploy('predict_sales', predict_sales, 'Sales prediction function')
"""

# 3. Using TabPy in Tableau
# In Tableau, create a calculated field:
"""
SCRIPT_REAL("
import numpy as np
return np.mean(_arg1)
", SUM([Sales]))
"""

# 4. Tableau REST API for automation
def manage_tableau_content():
    """Manage Tableau content using the REST API."""
    import requests
    import json
    
    # Tableau Server/Cloud URL
    base_url = "https://your-tableau-server.com/api/3.21"
    
    # Authentication (requires personal access token or username/password)
    headers = {
        "Content-Type": "application/json"
        # "X-Tableau-Auth": "YOUR_TOKEN"
    }
    
    # Get projects
    # response = requests.get(f"{base_url}/sites/site-id/projects", headers=headers)
    # print(f"Projects: {response.json()}")
    
    print("Conceptual: Would interact with Tableau REST API")

# 5. Generating Tableau Hyper Extracts with Python
def create_tableau_hyper_extract(df, output_file):
    """Create a Tableau .hyper extract file from a DataFrame."""
    import pandas as pd
    # Note: Requires tableauhyperapi library
    # from tableauhyperapi import HyperProcess, Connection, CreateMode, TableDefinition
    
    # This is a simplified conceptual example
    """
    with HyperProcess(Telemetry(Telemetry.SEND_USAGE_DATA_TO_TABLEAU)) as hyper:
        with Connection(endpoint=hyper.endpoint,
                        database=output_file,
                        create_mode=CreateMode.CREATE_AND_REPLACE) as connection:
            # Create table and insert data
            # ...
    """
    print(f"Conceptual: Would create Tableau extract at {output_file}")
    return output_file

# 6. Automating Tableau Refresh
def refresh_tableau_data_source(data_source_id):
    """Refresh a Tableau data source via REST API."""
    print(f"Conceptual: Would refresh Tableau data source {data_source_id}")

# 7. Python in Tableau Calculations (via TabPy)
def tableau_advanced_calculations():
    """
    Examples of Python calculations in Tableau using TabPy.
    
    SCRIPT_REAL("import numpy as np; return np.mean(_arg1)", SUM([Sales]))
    
    SCRIPT_STR("
        import pandas as pd
        df = pd.DataFrame({'x': _arg1, 'y': _arg2})
        # ... perform analysis ...
        return result
    ", SUM([Sales]), SUM([Profit]))
    """
    print("Conceptual: TabPy enables Python calculations in Tableau")
```

**Practical Example: Setting Up TabPy**:

```python
# Terminal commands for TabPy setup:
"""
# Install TabPy
pip install tabpy

# Start TabPy server
tabpy

# TabPy will run on http://localhost:9004
# In Tableau Desktop, add this as a server connection
"""

# Deploy a function to TabPy
def deploy_tabpy_function():
    """Deploy a custom function to TabPy."""
    from tabpy.tabpy_tools.client import Client
    
    client = Client()
    
    # Define a function
    def calculate_custom_kpi(sales, profit):
        import numpy as np
        return np.mean(profit / sales) * 100
    
    # Deploy the function
    client.deploy('custom_kpi', calculate_custom_kpi, 'Custom KPI calculation')
    print("Function deployed to TabPy")

# Tableau calculated field using TabPy:
"""
SCRIPT_REAL("
return _arg1 / _arg2 * 100
", SUM([Profit]), SUM([Sales])
)
"""
```

---

### Practical Examples

- **Example 1**: Using TabPy to calculate predictive analytics in Tableau.
- **Example 2**: Using Python in Tableau Prep for advanced data cleaning.
- **Example 3**: Automating Tableau Server management with the REST API.

---

### Hands-on Coding Exercises

**Exercise 11.3** – Tableau integration:
```python
# 1. Install TabPy and start the server.
# 2. Connect Tableau Desktop to TabPy.
# 3. Create a calculated field in Tableau using Python.
# 4. Deploy a custom function to TabPy.
```

---

### Mini Quiz

1. What is TabPy and what is it used for?
2. How do you use Python in Tableau Prep?
3. What is the Tableau REST API used for?
4. How do you create a .hyper extract with Python?
5. Why would you use Python with Tableau?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not having the required Python libraries | Install all dependencies |
| Using Python for simple Tableau calculations | Use Tableau's native calculations when possible |
| Not securing the TabPy server | Use authentication and HTTPS |
| Overcomplicating Tableau Prep with Python | Use Python only for complex transformations |

---

### Interview Questions

1. **How do you integrate Python with Tableau?**  
   *Answer*: Through TabPy for Python calculations, Tableau Prep for data preparation, and the Tableau REST API for automation.

2. **What is TabPy and how does it work?**  
   *Answer*: TabPy (Tableau Python Server) is a server that allows Tableau to execute Python scripts from calculated fields. It enables advanced analytics within Tableau.

3. **How do you automate Tableau content management?**  
   *Answer*: Using the Tableau REST API to programmatically manage projects, workbooks, and data sources.

---

### Assignment and Mini Project

**Assignment 11.3** – Tableau Python integration:
```python
# 1. Install TabPy and start the server.
# 2. In Tableau Desktop, connect to TabPy.
# 3. Create a calculated field that uses Python to calculate a moving average.
# 4. Deploy a custom function to TabPy that calculates customer segments.
# 5. Create a dashboard in Tableau that uses the Python calculation.
```

---

### Summary and Revision Notes

- TabPy enables Python calculations in Tableau.
- Python can be used in Tableau Prep for data preparation.
- The Tableau REST API allows automation.
- Use Python for advanced analytics that Tableau cannot perform natively.

---

## Lesson 11.4 – Exporting Reports

### Concept Explanation

Exporting reports is a critical part of any analytics workflow. Python makes it easy to export data and reports in various formats that BI tools can consume.

**Key export formats**:
1. **CSV**: The universal data exchange format.
2. **Excel**: For business users.
3. **PDF**: For professional reports.
4. **HTML**: For web-based dashboards.
5. **JSON**: For APIs and web applications.
6. **Tableau Hyper**: For direct Tableau consumption.
7. **Power BI Dataset**: For Power BI.

---

### Importance and Real-World Use Cases

- **Why it matters**: Reports need to be shared with stakeholders in formats they can use. Python's export capabilities ensure you can deliver data in the right format.

- **Use cases**:
  - A **data analyst** exports a CSV file for Tableau ingestion.
  - A **financial analyst** exports a PDF report for board meetings.
  - A **marketing analyst** exports an HTML dashboard for web viewing.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
from pathlib import Path
import matplotlib.pyplot as plt
from reportlab.lib.pagesizes import letter
from reportlab.platypus import SimpleDocTemplate, Table, TableStyle, Paragraph, Spacer, Image
from reportlab.lib.styles import getSampleStyleSheet
from reportlab.lib import colors

# 1. Export to CSV
def export_to_csv(df, filename):
    """Export DataFrame to CSV."""
    df.to_csv(filename, index=False)
    print(f"Exported to {filename}")

# 2. Export to Excel
def export_to_excel(df, filename, sheet_name='Data'):
    """Export DataFrame to Excel."""
    with pd.ExcelWriter(filename, engine='xlsxwriter') as writer:
        df.to_excel(writer, sheet_name=sheet_name, index=False)
    print(f"Exported to {filename}")

# 3. Export to JSON
def export_to_json(df, filename):
    """Export DataFrame to JSON."""
    df.to_json(filename, orient='records', indent=2)
    print(f"Exported to {filename}")

# 4. Export to HTML
def export_to_html(df, filename, title='Report'):
    """Export DataFrame to HTML."""
    html = f"""
    <!DOCTYPE html>
    <html>
    <head>
        <title>{title}</title>
        <style>
            body {{ font-family: Arial, sans-serif; margin: 40px; }}
            table {{ border-collapse: collapse; width: 100%; }}
            th {{ background-color: #3498db; color: white; padding: 10px; }}
            td {{ padding: 10px; border-bottom: 1px solid #ddd; }}
        </style>
    </head>
    <body>
        <h1>{title}</h1>
        {df.to_html(index=False)}
    </body>
    </html>
    """
    with open(filename, 'w') as f:
        f.write(html)
    print(f"Exported to {filename}")

# 5. Export to PDF (using reportlab)
def export_to_pdf(df, filename, title='Report'):
    """Export DataFrame to PDF."""
    doc = SimpleDocTemplate(filename, pagesize=letter)
    styles = getSampleStyleSheet()
    story = []
    
    # Title
    story.append(Paragraph(title, styles['Heading1']))
    story.append(Spacer(1, 12))
    
    # Data table
    table_data = [df.columns.tolist()] + df.values.tolist()
    table = Table(table_data)
    table.setStyle(TableStyle([
        ('BACKGROUND', (0, 0), (-1, 0), colors.grey),
        ('TEXTCOLOR', (0, 0), (-1, 0), colors.whitesmoke),
        ('ALIGN', (0, 0), (-1, -1), 'CENTER'),
        ('FONTNAME', (0, 0), (-1, 0), 'Helvetica-Bold'),
        ('GRID', (0, 0), (-1, -1), 1, colors.black),
    ]))
    story.append(table)
    
    doc.build(story)
    print(f"Exported to {filename}")

# 6. Export to Parquet
def export_to_parquet(df, filename):
    """Export DataFrame to Parquet."""
    df.to_parquet(filename, index=False)
    print(f"Exported to {filename}")

# 7. Export to Tableau Hyper (conceptual)
def export_to_hyper(df, filename):
    """Export DataFrame to Tableau Hyper format."""
    # Requires tableauhyperapi library
    # from tableauhyperapi import HyperProcess, Connection, CreateMode
    print(f"Conceptual: Would export to Tableau Hyper at {filename}")

# 8. Export all formats
def export_report(df, base_name, output_dir='exports'):
    """Export a report in multiple formats."""
    output_dir = Path(output_dir)
    output_dir.mkdir(exist_ok=True)
    
    exports = {
        'csv': f"{base_name}.csv",
        'excel': f"{base_name}.xlsx",
        'json': f"{base_name}.json",
        'html': f"{base_name}.html",
        'parquet': f"{base_name}.parquet"
    }
    
    for fmt, filename in exports.items():
        filepath = output_dir / filename
        if fmt == 'csv':
            export_to_csv(df, filepath)
        elif fmt == 'excel':
            export_to_excel(df, filepath)
        elif fmt == 'json':
            export_to_json(df, filepath)
        elif fmt == 'html':
            export_to_html(df, filepath)
        elif fmt == 'parquet':
            export_to_parquet(df, filepath)
    
    print(f"All exports saved to {output_dir}")

# Practical example
def generate_and_export_report():
    """Generate a report and export it in multiple formats."""
    # Generate sample data
    np.random.seed(42)
    df = pd.DataFrame({
        'Product': ['A', 'B', 'C', 'D', 'E'],
        'Sales': np.random.randint(100, 500, 5),
        'Profit': np.random.randint(10, 100, 5)
    })
    
    # Export in multiple formats
    export_report(df, 'sales_report')
```

---

### Practical Examples

- **Example 1**: Exporting a CSV for Tableau ingestion.
- **Example 2**: Exporting a PDF report for stakeholders.
- **Example 3**: Exporting an HTML dashboard for web viewing.

---

### Hands-on Coding Exercises

**Exercise 11.4** – Report exporter:
```python
# 1. Load a dataset.
# 2. Create functions to export to CSV, Excel, JSON, HTML, and PDF.
# 3. Export the dataset in all formats.
# 4. Verify each file was created.
```

---

### Mini Quiz

1. What are the common export formats for data reports?
2. How do you export a DataFrame to CSV?
3. How do you export a DataFrame to Excel with formatting?
4. What is the advantage of exporting to Parquet?
5. How do you export a report to PDF?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not including `index=False` in CSV export | Always use `index=False` unless the index is meaningful |
| Using absolute paths for exports | Use `pathlib` or relative paths |
| Not handling different file encodings | Use `encoding='utf-8'` for text files |
| Forgetting to install required libraries | Install reportlab, openpyxl, etc. |

---

### Interview Questions

1. **How do you export a Pandas DataFrame to CSV?**  
   *Answer*: Using `df.to_csv('filename.csv', index=False)`.

2. **How do you export a DataFrame to a formatted Excel file?**  
   *Answer*: Using `pd.ExcelWriter` with `xlsxwriter` or `openpyxl`.

3. **What are the advantages of exporting to Parquet?**  
   *Answer*: Parquet is a columnar storage format that offers better compression and performance for large datasets.

---

### Assignment and Mini Project

**Assignment 11.4** – Multi-format exporter:
```python
# 1. Load a dataset (e.g., 'titanic').
# 2. Create a function that exports the dataset to:
#    - CSV.
#    - Excel.
#    - HTML.
#    - PDF.
# 3. Save all exports in a folder named 'exports'.
# 4. Add a timestamp to each filename.
```

---

### Summary and Revision Notes

- CSV: Universal data exchange format.
- Excel: For business users.
- HTML: For web views.
- PDF: For professional reports.
- JSON: For APIs.
- Parquet: For large datasets.

---

## Lesson 11.5 – Integrating Analytics Workflows

### Concept Explanation

This final lesson brings everything together. An **integrated analytics workflow** combines Python, SQL, BI tools, and automation into a seamless pipeline.

**Components of an integrated workflow**:
1. **Data Collection**: Python scripts collect data from APIs, databases, and files.
2. **Data Preparation**: Python (Pandas) and SQL clean and transform data.
3. **Analysis**: Python performs statistical analysis and modelling.
4. **Reporting**: Results are exported to Excel, Power BI, or Tableau.
5. **Automation**: The entire pipeline is scheduled to run automatically.
6. **Distribution**: Reports are emailed or shared via BI tools.

**Example workflow**:
1. Python script pulls sales data from a SQL database.
2. Python cleans and aggregates the data.
3. A summary report is generated in Excel.
4. The data is pushed to Power BI for visualisation.
5. A daily email is sent with the report attached.
6. The entire process runs daily at 6 AM.

---

### Importance and Real-World Use Cases

- **Why it matters**: End-to-end automation transforms manual processes into reliable, scalable systems.

- **Use cases**:
  - A **data engineer** builds a pipeline that collects data, processes it, and loads it into Power BI.
  - A **BI developer** automates the generation and distribution of daily reports.
  - A **data scientist** builds a model, schedules it to retrain, and pushes results to Tableau.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import sqlite3
import datetime
import smtplib
import schedule
import time
from pathlib import Path
import warnings
warnings.filterwarnings('ignore')

# 1. Data Collection Module
class DataCollector:
    """Collect data from various sources."""
    
    @staticmethod
    def from_sqlite(db_path, query):
        """Collect data from SQLite database."""
        conn = sqlite3.connect(db_path)
        df = pd.read_sql_query(query, conn)
        conn.close()
        return df
    
    @staticmethod
    def from_api(url, params=None):
        """Collect data from API."""
        import requests
        response = requests.get(url, params=params)
        if response.status_code == 200:
            return pd.DataFrame(response.json())
        else:
            print(f"API error: {response.status_code}")
            return None

# 2. Data Processing Module
class DataProcessor:
    """Process and clean data."""
    
    @staticmethod
    def clean_sales_data(df):
        """Clean sales data."""
        # Remove duplicates
        df = df.drop_duplicates()
        # Handle missing values
        df['Sales'] = df['Sales'].fillna(0)
        df['Quantity'] = df['Quantity'].fillna(0)
        # Add calculated columns
        df['Total'] = df['Sales'] * df['Quantity']
        # Add date column
        df['Processed_Date'] = datetime.datetime.now().date()
        return df
    
    @staticmethod
    def aggregate_sales(df):
        """Aggregate sales data."""
        summary = df.groupby('Product')['Total'].agg(['sum', 'mean', 'count']).reset_index()
        summary.columns = ['Product', 'Total_Sales', 'Average_Sales', 'Transaction_Count']
        return summary

# 3. Report Generation Module
class ReportGenerator:
    """Generate reports in various formats."""
    
    @staticmethod
    def to_excel(df, filename):
        """Export to Excel."""
        with pd.ExcelWriter(filename, engine='xlsxwriter') as writer:
            df.to_excel(writer, sheet_name='Data', index=False)
        print(f"Report generated: {filename}")
    
    @staticmethod
    def to_powerbi(df, dataset_name):
        """Push data to Power BI (conceptual)."""
        print(f"Conceptual: Pushing to Power BI dataset '{dataset_name}'")

# 4. Email Module
class EmailSender:
    """Send automated emails."""
    
    @staticmethod
    def send_report(recipient, subject, body, attachment_path):
        """Send email with report attachment."""
        print(f"Sending email to {recipient}")
        print(f"Subject: {subject}")
        print(f"Attachment: {attachment_path}")
        # Actual email sending code would go here
        print("Email sent successfully!")

# 5. Main Pipeline
class AnalyticsPipeline:
    """End-to-end analytics pipeline."""
    
    def __init__(self, config):
        self.config = config
        self.data = None
        self.processed_data = None
        self.report_path = None
    
    def run(self):
        """Run the complete pipeline."""
        print("=" * 60)
        print(f"STARTING PIPELINE: {datetime.datetime.now()}")
        print("=" * 60)
        
        try:
            # Step 1: Collect data
            print("Step 1: Collecting data...")
            # Simulated data collection
            np.random.seed(42)
            self.data = pd.DataFrame({
                'Product': np.random.choice(['A', 'B', 'C', 'D'], 1000),
                'Sales': np.random.randint(100, 1000, 1000),
                'Quantity': np.random.randint(1, 20, 1000)
            })
            print(f"Collected {len(self.data)} records")
            
            # Step 2: Process data
            print("Step 2: Processing data...")
            self.processed_data = DataProcessor.clean_sales_data(self.data)
            summary = DataProcessor.aggregate_sales(self.processed_data)
            print(f"Processed {len(self.processed_data)} records")
            
            # Step 3: Generate report
            print("Step 3: Generating report...")
            timestamp = datetime.datetime.now().strftime("%Y%m%d_%H%M%S")
            self.report_path = f"sales_report_{timestamp}.xlsx"
            ReportGenerator.to_excel(summary, self.report_path)
            
            # Step 4: Send email
            print("Step 4: Sending email...")
            subject = f"Daily Sales Report - {datetime.datetime.now().strftime('%Y-%m-%d')}"
            body = f"Attached is the daily sales report for {datetime.datetime.now().strftime('%Y-%m-%d')}."
            EmailSender.send_report(
                recipient="team@company.com",
                subject=subject,
                body=body,
                attachment_path=self.report_path
            )
            
            # Step 5: Log completion
            print("Pipeline completed successfully!")
            return True
            
        except Exception as e:
            print(f"Pipeline failed: {e}")
            return False

# 6. Scheduling the pipeline
def schedule_pipeline():
    """Schedule the analytics pipeline to run daily."""
    pipeline = AnalyticsPipeline({})
    
    # Run daily at 8:00 AM
    schedule.every().day.at("08:00").do(pipeline.run)
    
    print("Analytics pipeline scheduled.")
    print("Running daily at 8:00 AM.")
    print("Press Ctrl+C to stop.")
    
    try:
        while True:
            schedule.run_pending()
            time.sleep(60)
    except KeyboardInterrupt:
        print("\nScheduler stopped.")

# 7. Dashboard integration
def update_dashboards():
    """Update Power BI and Tableau dashboards (conceptual)."""
    print("Conceptual: Updating Power BI dataset...")
    print("Conceptual: Updating Tableau data source...")
    print("Dashboards updated!")

# 8. Complete workflow with logging
import logging

def setup_logging():
    """Set up logging for the pipeline."""
    logging.basicConfig(
        filename='pipeline.log',
        level=logging.INFO,
        format='%(asctime)s - %(levelname)s - %(message)s'
    )

def run_pipeline_with_logging():
    """Run the pipeline with logging."""
    setup_logging()
    logging.info("Pipeline started")
    
    pipeline = AnalyticsPipeline({})
    success = pipeline.run()
    
    if success:
        logging.info("Pipeline completed successfully")
    else:
        logging.error("Pipeline failed")
    
    return success

# 9. CLI interface
def main():
    """Command-line interface for the pipeline."""
    print("Analytics Automation Pipeline")
    print("-" * 40)
    print("Options:")
    print("1. Run pipeline once")
    print("2. Schedule pipeline (daily)")
    print("3. Update dashboards")
    print("4. Run with logging")
    
    choice = input("Enter your choice (1-4): ")
    
    if choice == '1':
        pipeline = AnalyticsPipeline({})
        pipeline.run()
    elif choice == '2':
        schedule_pipeline()
    elif choice == '3':
        update_dashboards()
    elif choice == '4':
        run_pipeline_with_logging()
    else:
        print("Invalid choice.")

if __name__ == "__main__":
    main()
```

---

### Practical Examples

- **Example 1**: A daily sales pipeline that collects data, processes it, generates a report, and updates dashboards.
- **Example 2**: A weekly customer analytics pipeline that calculates churn rates and sends a report.
- **Example 3**: A real-time data pipeline that streams data to Power BI.

---

### Hands-on Coding Exercises

**Exercise 11.5** – Complete pipeline:
```python
# 1. Build an end-to-end analytics pipeline that:
#    - Collects data from a simulated source.
#    - Processes and cleans the data.
#    - Generates a summary report.
#    - Exports the report to Excel and HTML.
#    - Sends an email notification.
# 2. Schedule the pipeline to run hourly.
```

---

### Mini Quiz

1. What are the main components of an analytics workflow?
2. Why is automation important in data analytics?
3. How do you integrate Python with Power BI in a pipeline?
4. What is the role of scheduling in automation?
5. How do you handle errors in a pipeline?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not handling errors | Implement robust error handling and retries |
| Not logging activities | Add logging for debugging and auditing |
| Hardcoding credentials | Use environment variables |
| Not validating data | Validate data quality at each step |
| Ignoring performance | Optimise for large datasets |

---

### Interview Questions

1. **How would you build an end-to-end analytics pipeline?**  
   *Answer*: I would create modular components for data collection, processing, analysis, reporting, and distribution. The pipeline would be scheduled to run automatically with error handling and logging.

2. **How do you integrate Python with BI tools in a workflow?**  
   *Answer*: By exporting processed data to formats that BI tools consume (Excel, CSV) or by using APIs to push data directly to Power BI or Tableau.

3. **What are the key considerations for an automated pipeline?**  
   *Answer*: Reliability, error handling, logging, performance, and maintainability.

---

### Assignment and Mini Project

**Final Project** – End-to-End Analytics Automation:
```python
# Build a complete analytics automation pipeline that:
# 1. Collects data from a simulated API or database.
# 2. Processes and cleans the data.
# 3. Performs analysis (summary statistics, trends).
# 4. Generates a report in Excel format with charts.
# 5. Exports the data to a format compatible with Power BI or Tableau.
# 6. Sends an email with the report attached.
# 7. Schedules the pipeline to run daily.
# 8. Includes logging and error handling.
# 9. Provides a summary of the pipeline's performance.
```

---

### Summary and Revision Notes

- Integrated workflows combine Python, SQL, BI tools, and automation.
- Modular design makes pipelines maintainable.
- Scheduling enables hands-off operation.
- Logging and error handling ensure reliability.
- Exports bridge Python and BI tools.

---

## Final Phase 11 Assessment

Now that you have completed all lessons, test your overall understanding.

### Self-Evaluation Checklist

- I can use Python to automate Excel reporting.

- I can integrate Python with Power BI.

- I can integrate Python with Tableau.

- I can export reports in multiple formats.

- I can build end-to-end analytics workflows.

---

### Answers to Mini Quizzes

**Lesson 11.1**: 1. pandas, openpyxl, xlsxwriter, xlwings. 2. `pd.read_excel()`. 3. `openpyxl` supports advanced formatting and modifying existing files. 4. Using `xlsxwriter`'s `add_chart()` method. 5. Controlling the Excel application from Python.

**Lesson 11.2**: 1. In Options → Python scripting. 2. To perform complex transformations. 3. Add a Python visual from the Visualizations pane. 4. Managing Power BI content programmatically. 5. For advanced transformations and analytics.

**Lesson 11.3**: 1. TabPy is the Tableau Python Server for Python calculations. 2. By adding a Python script step. 3. Programmatically managing Tableau content. 4. Using the `tableauhyperapi` library. 5. For advanced analytics and automation.

**Lesson 11.4**: 1. CSV, Excel, PDF, HTML, JSON, Parquet. 2. `df.to_csv('file.csv', index=False)`. 3. Using `pd.ExcelWriter` with `xlsxwriter`. 4. Better compression and performance. 5. Using `reportlab` or converting HTML.

**Lesson 11.5**: 1. Data collection, processing, analysis, reporting, distribution. 2. To save time and ensure reliability. 3. By exporting data or using APIs. 4. To run pipelines without manual intervention. 5. Using try-except and logging.

---

**Congratulations!** You have completed all phases of this comprehensive Python for Data Analytics curriculum. You are now a skilled data professional capable of building end-to-end analytics solutions and integrating them with BI tools. Continue building, learning, and applying your skills to real-world problems. Best of luck in your data analytics career!

---




<br/><br/><br/>
<center> <b>Happy Learning! 😊</b> </center>
