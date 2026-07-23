# Phase 10: Automation

Welcome to **Phase 10** – the final technical phase of your Python for Data Analytics journey! You have mastered data collection, cleaning, analysis, visualisation, statistics, and SQL integration. Now, you will learn how to **automate** these tasks, turning your scripts into efficient, self-running workflows.

In the real world, data professionals spend a significant amount of time on repetitive tasks:
- Downloading and cleaning data files every morning.
- Generating and emailing reports to stakeholders.
- Updating Excel dashboards.
- Monitoring data sources for updates.

**Automation** is the skill that transforms you from a data analyst who writes scripts to a data engineer who builds systems. In this phase, you will learn how to:
- Automate file and folder management.
- Read, write, and format Excel files without opening Excel.
- Send automated emails with attachments.
- Generate professional reports (PDF, HTML, Excel).
- Schedule scripts to run at specific times.
- Build data collection pipelines that fetch data from APIs and databases.

Let's make your data workflows run themselves!

---

## Lesson 10.1 – File Automation

### Concept Explanation

File automation involves programmatically managing files and folders – moving, copying, renaming, archiving, and cleaning up data files. This is essential for building robust data pipelines.

**Key Python libraries**:
- **`os`** – interacting with the operating system (file paths, environment variables).
- **`shutil`** – high-level file operations (copy, move, delete).
- **`glob`** – finding files matching a pattern.
- **`pathlib`** – modern object-oriented file path handling (recommended for new code).

**Common automation tasks**:
1. **Moving files**: Organising downloaded files into folders.
2. **Renaming files**: Standardising file names (e.g., adding dates).
3. **Deleting old files**: Archiving or deleting files older than a threshold.
4. **Merging files**: Combining multiple CSV files into one.
5. **Watching folders**: Monitoring a directory for new files (advanced).

---

### Importance and Real-World Use Cases

- **Why it matters**: Data files are messy. Automation saves hours of manual organisation and reduces the risk of human error.

- **Use cases**:
  - A **data engineer** writes a script that moves incoming CSV files from a landing folder to an archive folder after processing.
  - An **analyst** creates a script that automatically renames daily sales reports with the current date.
  - A **data scientist** builds a script that cleans up old model files to save disk space.

---

### Step-by-Step Demonstration

```python
import os
import shutil
import glob
from pathlib import Path
import datetime

# 1. Creating and managing directories
# Create a new folder called 'data'
os.makedirs('data', exist_ok=True)

# Check if folder exists
if os.path.exists('data'):
    print("Folder exists")

# 2. Getting file paths
# Get the current working directory
cwd = os.getcwd()
print(f"Current working directory: {cwd}")

# Join paths (cross-platform)
file_path = os.path.join('data', 'sales.csv')
print(f"File path: {file_path}")

# 3. Renaming files
# Create a dummy file
with open('temp.txt', 'w') as f:
    f.write("This is a temporary file")

# Rename it with a date
today = datetime.datetime.now().strftime("%Y%m%d")
new_name = f"temp_{today}.txt"
os.rename('temp.txt', new_name)
print(f"Renamed to: {new_name}")

# 4. Moving files
# Create a folder for archived files
os.makedirs('archive', exist_ok=True)
shutil.move(new_name, os.path.join('archive', new_name))
print("Moved file to archive folder")

# 5. Copying files
shutil.copy('data/sales.csv', 'data/sales_backup.csv')
print("File copied")

# 6. Finding files with glob
# Find all CSV files
csv_files = glob.glob('data/*.csv')
print(f"CSV files in data: {csv_files}")

# 7. Using pathlib (modern approach)
data_dir = Path('data')
for file_path in data_dir.glob('*.csv'):
    print(f"Found: {file_path.name}")

# 8. Deleting files older than N days
def delete_old_files(folder, days_old):
    """Delete files older than a specified number of days."""
    now = datetime.datetime.now()
    for item in os.listdir(folder):
        item_path = os.path.join(folder, item)
        if os.path.isfile(item_path):
            file_age = datetime.datetime.fromtimestamp(os.path.getmtime(item_path))
            age = (now - file_age).days
            if age > days_old:
                os.remove(item_path)
                print(f"Deleted: {item} (age: {age} days)")

# delete_old_files('archive', 30)  # Uncomment to run (careful!)
```

**Automating File Organisation**:

```python
def organise_files_by_type(folder):
    """Organise files into subfolders by extension."""
    ext_folders = {
        '.csv': 'csv_files',
        '.xlsx': 'excel_files',
        '.json': 'json_files',
        '.txt': 'text_files',
        '.pdf': 'pdf_files',
        '.png': 'images',
        '.jpg': 'images'
    }
    
    for item in os.listdir(folder):
        item_path = os.path.join(folder, item)
        if os.path.isfile(item_path):
            ext = os.path.splitext(item)[1].lower()
            target_folder = ext_folders.get(ext, 'other')
            target_path = os.path.join(folder, target_folder)
            os.makedirs(target_path, exist_ok=True)
            shutil.move(item_path, os.path.join(target_path, item))
            print(f"Moved {item} to {target_folder}")

# organise_files_by_type('downloads')
```

---

### Practical Examples

- **Example 1**: A script that scans a folder, renames all files with a date prefix, and moves them to an archive.
- **Example 2**: A script that deletes temporary files older than 7 days.

---

### Hands-on Coding Exercises

**Exercise 10.1** – File manager:
```python
# 1. Create a folder called 'test_files'
# 2. Create 5 dummy files with different extensions (.txt, .csv, .json)
# 3. Write a function that:
#    - Lists all files in the folder.
#    - Moves all .txt files to a 'text' subfolder.
#    - Moves all .csv files to a 'csv' subfolder.
#    - Deletes any file older than 1 day (simulate by using a timestamp).
```

---

### Mini Quiz

1. What is the difference between `os.rename()` and `shutil.move()`?
2. How do you check if a file exists in Python?
3. What is the purpose of `glob.glob()`?
4. What is `pathlib` and why is it recommended?
5. How do you get the last modified time of a file?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Hardcoding file paths | Use `os.path.join()` or `pathlib` for cross-platform compatibility |
| Not checking if a file exists before operating on it | Use `os.path.exists()` or `Path.exists()` |
| Deleting files without verification | Add a dry-run mode or confirmation step |
| Using `os` for everything | Use `pathlib` for modern, cleaner code |

---

### Interview Questions

1. **How do you list all CSV files in a directory?**  
   *Answer*: Using `glob.glob('*.csv')` or `Path('.').glob('*.csv')`.

2. **How do you delete a file older than 30 days?**  
   *Answer*: Get the file's modification time using `os.path.getmtime()`, calculate the age, and delete it if it exceeds the threshold.

3. **What is the advantage of `pathlib` over `os.path`?**  
   *Answer*: `pathlib` provides an object-oriented interface, is more readable, and handles cross-platform paths better.

---

### Assignment and Mini Project

**Assignment 10.1** – File organiser:
```python
# 1. Create a folder with mixed file types (.txt, .csv, .xlsx, .pdf, .jpg).
# 2. Write a script that:
#    - Creates subfolders for each file type.
#    - Moves each file to its corresponding subfolder.
#    - Prints a summary of what was moved.
# 3. Use both os and pathlib in the script.
```

---

### Summary and Revision Notes

- `os` and `shutil` handle file operations.
- `glob` finds files by pattern.
- `pathlib` is modern and recommended for new code.
- Always check file existence before operations.
- Use `datetime` for time-based automation.

---

## Lesson 10.2 – Excel Automation

### Concept Explanation

Excel is ubiquitous in business. Automating Excel tasks – reading, writing, formatting, and applying formulas – is one of the most valuable automation skills.

**Key Python libraries**:
- **`openpyxl`**: Read/write `.xlsx` files. Supports styles, formulas, charts, and pivot tables.
- **`pandas`**: High-level read/write with `pd.read_excel()` and `df.to_excel()`.
- **`xlwings`**: Automates Excel applications (runs macros, interacts with workbooks).
- **`xlsxwriter`**: Creates `.xlsx` files with advanced formatting (charts, conditional formatting).

**Common automation tasks**:
1. **Reading Excel files**: Extracting data into DataFrames.
2. **Writing Excel files**: Creating reports with multiple sheets.
3. **Applying formatting**: Adding colours, borders, and fonts.
4. **Adding formulas**: Using Excel formulas in cells.
5. **Creating charts**: Adding charts directly in Excel.
6. **Merging sheets**: Combining multiple sheets into one.

---

### Importance and Real-World Use Cases

- **Why it matters**: Many stakeholders prefer Excel reports. Automating Excel tasks saves hours of manual data entry and formatting.

- **Use cases**:
  - A **financial analyst** generates a weekly budget report with formatted Excel sheets.
  - A **data analyst** creates a dashboard with multiple sheets and embedded charts.
  - A **consultant** merges multiple Excel files into a single master file.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import openpyxl
from openpyxl.styles import Font, PatternFill, Border, Side
from openpyxl.utils.dataframe import dataframe_to_rows
from openpyxl.chart import BarChart, Reference

# 1. Reading Excel files with pandas
df = pd.read_excel('sample.xlsx', sheet_name='Sheet1')
print("DataFrame from Excel:")
print(df.head())

# 2. Writing a simple Excel file with pandas
df.to_excel('output.xlsx', index=False, sheet_name='Data')

# 3. Writing to multiple sheets
with pd.ExcelWriter('multi_sheet.xlsx') as writer:
    df.to_excel(writer, sheet_name='Sheet1', index=False)
    df.describe().to_excel(writer, sheet_name='Summary', index=True)

print("Multi-sheet Excel file created.")

# 4. Advanced formatting with openpyxl
def create_formatted_report(filename):
    wb = openpyxl.Workbook()
    ws = wb.active
    ws.title = 'Report'

    # Sample data
    data = [
        ['Product', 'Sales', 'Quantity', 'Profit'],
        ['Product A', 1200, 10, 240],
        ['Product B', 1800, 15, 540],
        ['Product C', 900, 8, 180],
        ['Product D', 1500, 12, 300],
    ]

    # Write data
    for row in data:
        ws.append(row)

    # Styling
    # Header style
    header_font = Font(bold=True, color='FFFFFF')
    header_fill = PatternFill(start_color='4472C4', end_color='4472C4', fill_type='solid')
    
    for col in range(1, 5):
        cell = ws.cell(row=1, column=col)
        cell.font = header_font
        cell.fill = header_fill

    # Borders
    thin_border = Border(
        left=Side(style='thin'),
        right=Side(style='thin'),
        top=Side(style='thin'),
        bottom=Side(style='thin')
    )
    
    for row in ws.iter_rows(min_row=1, max_row=len(data), min_col=1, max_col=4):
        for cell in row:
            cell.border = thin_border

    # Column widths
    ws.column_dimensions['A'].width = 15
    ws.column_dimensions['B'].width = 12
    ws.column_dimensions['C'].width = 12
    ws.column_dimensions['D'].width = 12

    # 5. Adding a chart
    chart = BarChart()
    chart.title = "Sales by Product"
    chart.x_axis.title = "Product"
    chart.y_axis.title = "Sales"

    data_ref = Reference(ws, min_col=2, min_row=1, max_row=len(data), max_col=2)
    categories = Reference(ws, min_col=1, min_row=2, max_row=len(data))
    
    chart.add_data(data_ref, titles_from_data=True)
    chart.set_categories(categories)
    
    ws.add_chart(chart, "F2")

    wb.save(filename)
    print(f"Formatted report saved as {filename}")

create_formatted_report('formatted_report.xlsx')

# 6. Reading multiple Excel files and merging
def merge_excel_files(folder, output_file):
    """Merge all Excel files in a folder into a single file."""
    all_data = []
    for file in Path(folder).glob('*.xlsx'):
        df = pd.read_excel(file)
        df['Source'] = file.name
        all_data.append(df)
    
    if all_data:
        combined = pd.concat(all_data, ignore_index=True)
        combined.to_excel(output_file, index=False)
        print(f"Merged {len(all_data)} files into {output_file}")
    else:
        print("No Excel files found.")

# merge_excel_files('excel_folder', 'merged.xlsx')
```

**Using openpyxl for Formula Automation**:

```python
def add_formulas():
    wb = openpyxl.Workbook()
    ws = wb.active
    
    data = [
        ['Item', 'Price', 'Quantity', 'Total'],
        ['Widget A', 10, 5],
        ['Widget B', 20, 3],
        ['Widget C', 15, 8],
    ]
    
    for row in data:
        ws.append(row)
    
    # Add formula to calculate total (Price * Quantity)
    ws['D2'] = '=B2*C2'
    ws['D3'] = '=B3*C3'
    ws['D4'] = '=B4*C4'
    
    # Add formula for grand total
    ws['D5'] = '=SUM(D2:D4)'
    
    wb.save('formulas.xlsx')
    print("Excel with formulas created.")

add_formulas()
```

---

### Practical Examples

- **Example 1**: Generating a monthly sales report with formatted tables and charts.
- **Example 2**: Consolidating weekly Excel reports from multiple departments.
- **Example 3**: Applying conditional formatting to highlight low-performing products.

---

### Hands-on Coding Exercises

**Exercise 10.2** – Excel report generator:
```python
# 1. Load a dataset (e.g., 'tips' or 'titanic').
# 2. Write a function that:
#    - Creates an Excel file with three sheets:
#      a. Raw data.
#      b. Summary statistics (using pandas .describe()).
#      c. Pivot table (e.g., average tip by day).
#    - Formats the header row with bold text and a background color.
#    - Adds a bar chart to the summary sheet.
# 3. Save the file.
```

---

### Mini Quiz

1. What is the difference between `openpyxl` and `pandas` for Excel operations?
2. How do you write to multiple sheets in an Excel file?
3. How do you add a formula to a cell using `openpyxl`?
4. What is the purpose of `ExcelWriter`?
5. How do you merge multiple Excel files?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using pandas for complex formatting (it's limited) | Use `openpyxl` for advanced formatting |
| Writing large DataFrames without chunking | Use `pd.read_excel()` with `chunksize` for large files |
| Forgetting to close the Excel writer | Use `with pd.ExcelWriter(...) as writer:` |
| Hardcoding sheet names | Use variables or detect sheet names dynamically |

---

### Interview Questions

1. **How do you create an Excel file with multiple sheets using Python?**  
   *Answer*: Using `pd.ExcelWriter` with multiple `to_excel()` calls, or using `openpyxl` to create and manage sheets.

2. **How do you format cells in an Excel file using Python?**  
   *Answer*: Using `openpyxl`, you can access cells and apply `Font`, `PatternFill`, `Border`, etc.

3. **How do you add a chart to an Excel file?**  
   *Answer*: Using `openpyxl.chart` to create `BarChart`, `LineChart`, etc., and then adding it to a worksheet.

---

### Assignment and Mini Project

**Assignment 10.2** – Automated reporting:
```python
# 1. Download or create a dataset (e.g., sales data).
# 2. Write a script that:
#    - Loads the data.
#    - Creates an Excel file with:
#      a. A raw data sheet.
#      b. A summary sheet with mean, median, min, max by category.
#      c. A pivot table sheet.
#    - Formats the summary sheet with a professional style.
#    - Adds a bar chart for total sales by category.
# 3. Save the file with a timestamp in the filename.
```

---

### Summary and Revision Notes

- `pandas` for simple read/write.
- `openpyxl` for advanced formatting, formulas, and charts.
- Use `ExcelWriter` for multiple sheets.
- Always use `with` statements for file writing.

---

## Lesson 10.3 – Email Automation

### Concept Explanation

Sending automated emails is a powerful way to distribute reports, notifications, and alerts. Python's `smtplib` library allows you to send emails programmatically.

**Key libraries**:
- **`smtplib`**: The core library for sending emails via SMTP.
- **`email`**: For constructing email messages (headers, body, attachments).
- **`yagmail`** / **`sendgrid`**: Higher-level libraries (optional).

**Email components**:
- **Sender**: The email address that sends the email.
- **Recipient**: The email address(es) receiving the email.
- **Subject**: The subject line.
- **Body**: The content (plain text or HTML).
- **Attachments**: Files attached to the email.

**Security considerations**:
- Never hardcode passwords in your script.
- Use **App Passwords** (for Gmail) or **SMTP authentication**.
- Use **environment variables** for credentials.

---

### Importance and Real-World Use Cases

- **Why it matters**: Email automation saves time and ensures stakeholders receive reports on time, every time.

- **Use cases**:
  - A **data analyst** sends a daily sales report to the sales team.
  - A **data engineer** sends a notification when a data pipeline finishes.
  - A **marketing analyst** sends a weekly campaign performance summary.

---

### Step-by-Step Demonstration

```python
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
from email.mime.base import MIMEBase
from email import encoders
import os
from pathlib import Path

# 1. Basic email (plain text)
def send_basic_email(sender, recipient, subject, body):
    try:
        # Set up SMTP server (Gmail example)
        server = smtplib.SMTP('smtp.gmail.com', 587)
        server.starttls()  # Secure connection
        
        # Login (use environment variables for security)
        # In production: sender = os.getenv('EMAIL_USER')
        # password = os.getenv('EMAIL_PASSWORD')
        password = 'your_password_here'  # Replace with actual or use env vars
        server.login(sender, password)
        
        # Create message
        msg = MIMEMultipart()
        msg['From'] = sender
        msg['To'] = recipient
        msg['Subject'] = subject
        msg.attach(MIMEText(body, 'plain'))
        
        # Send email
        server.send_message(msg)
        server.quit()
        print("Email sent successfully!")
        return True
    except Exception as e:
        print(f"Error sending email: {e}")
        return False

# 2. Email with HTML body
def send_html_email(sender, recipient, subject, html_body):
    try:
        server = smtplib.SMTP('smtp.gmail.com', 587)
        server.starttls()
        password = 'your_password_here'
        server.login(sender, password)
        
        msg = MIMEMultipart()
        msg['From'] = sender
        msg['To'] = recipient
        msg['Subject'] = subject
        msg.attach(MIMEText(html_body, 'html'))
        
        server.send_message(msg)
        server.quit()
        print("HTML email sent successfully!")
        return True
    except Exception as e:
        print(f"Error: {e}")
        return False

# 3. Email with attachment
def send_email_with_attachment(sender, recipient, subject, body, file_path):
    try:
        server = smtplib.SMTP('smtp.gmail.com', 587)
        server.starttls()
        password = 'your_password_here'
        server.login(sender, password)
        
        msg = MIMEMultipart()
        msg['From'] = sender
        msg['To'] = recipient
        msg['Subject'] = subject
        
        # Attach body
        msg.attach(MIMEText(body, 'plain'))
        
        # Attach file
        with open(file_path, 'rb') as attachment:
            part = MIMEBase('application', 'octet-stream')
            part.set_payload(attachment.read())
            encoders.encode_base64(part)
            part.add_header(
                'Content-Disposition',
                f'attachment; filename={Path(file_path).name}'
            )
            msg.attach(part)
        
        server.send_message(msg)
        server.quit()
        print(f"Email with attachment sent successfully!")
        return True
    except Exception as e:
        print(f"Error: {e}")
        return False

# 4. Sending to multiple recipients
def send_bulk_email(sender, recipients, subject, body):
    try:
        server = smtplib.SMTP('smtp.gmail.com', 587)
        server.starttls()
        password = 'your_password_here'
        server.login(sender, password)
        
        msg = MIMEMultipart()
        msg['From'] = sender
        msg['To'] = ', '.join(recipients)
        msg['Subject'] = subject
        msg.attach(MIMEText(body, 'plain'))
        
        server.send_message(msg)
        server.quit()
        print(f"Email sent to {len(recipients)} recipients!")
        return True
    except Exception as e:
        print(f"Error: {e}")
        return False

# 5. Using environment variables (best practice)
"""
import os
sender = os.getenv('EMAIL_USER')
password = os.getenv('EMAIL_PASSWORD')
recipient = os.getenv('EMAIL_RECIPIENT')
"""

# 6. Creating a beautiful HTML email
def create_html_report(report_data):
    html = f"""
    <html>
    <head>
        <style>
            body {{ font-family: Arial, sans-serif; }}
            h2 {{ color: #2c3e50; }}
            table {{ border-collapse: collapse; width: 100%; }}
            th {{ background-color: #3498db; color: white; padding: 8px; }}
            td {{ padding: 8px; border-bottom: 1px solid #ddd; }}
        </style>
    </head>
    <body>
        <h2>📊 Weekly Sales Report</h2>
        <p>Hello Team,</p>
        <p>Here is your weekly sales summary:</p>
        <table>
            <tr><th>Region</th><th>Sales</th><th>Growth</th></tr>
            <tr><td>North</td><td>$12,000</td><td>+5%</td></tr>
            <tr><td>South</td><td>$8,500</td><td>+2%</td></tr>
            <tr><td>East</td><td>$15,200</td><td>+8%</td></tr>
            <tr><td>West</td><td>$10,800</td><td>-1%</td></tr>
        </table>
        <p>Best regards,<br>Data Team</p>
    </body>
    </html>
    """
    return html
```

**Practical Example: Automated Report Email**:

```python
def send_daily_report():
    """Generate a report and send it via email."""
    # 1. Generate report (example)
    df = pd.read_csv('sales_data.csv')
    summary = df.groupby('region')['sales'].sum().to_string()
    
    # 2. Create email content
    subject = f"Daily Sales Report - {datetime.datetime.now().strftime('%Y-%m-%d')}"
    body = f"""
    Hello Team,
    
    Here is today's sales summary:
    
    {summary}
    
    Regards,
    Data Automation
    """
    
    # 3. Send email (using environment variables)
    # sender = os.getenv('EMAIL_USER')
    # recipient = os.getenv('EMAIL_RECIPIENT')
    # send_basic_email(sender, recipient, subject, body)
    print("Report email ready to send")
```

---

### Practical Examples

- **Example 1**: Sending a daily report email with an attached CSV.
- **Example 2**: Sending a notification email when a script completes.
- **Example 3**: Sending a formatted HTML email with inline tables.

---

### Hands-on Coding Exercises

**Exercise 10.3** – Email sender:
```python
# 1. Create a function that sends a plain text email.
# 2. Create a function that sends an HTML email with a formatted table.
# 3. Create a function that sends an email with an attachment.
# 4. Use environment variables for credentials.
# 5. Test with a test email account.
```

---

### Mini Quiz

1. What library is used for sending emails in Python?
2. Why should you use environment variables for email credentials?
3. What is the purpose of `starttls()`?
4. How do you attach a file to an email?
5. What is the difference between `MIMEText` and `MIMEMultipart`?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Hardcoding passwords in the script | Use environment variables or a secrets manager |
| Not using `starttls()` | Always use TLS/SSL for security |
| Sending large attachments without compression | Compress files or use cloud storage links |
| Not handling email errors | Use try-except and log errors |

---

### Interview Questions

1. **How do you send an email from a Python script?**  
   *Answer*: Using `smtplib` and `email` libraries. Connect to the SMTP server, log in, compose the email, and send it.

2. **How do you send an email with an attachment?**  
   *Answer*: Use `MIMEBase` to encode the attachment, add it to the email, and send via `smtplib`.

3. **Why is it important to secure email credentials?**  
   *Answer*: To prevent unauthorised access to email accounts and potential security breaches.

---

### Assignment and Mini Project

**Assignment 10.3** – Automated report email:
```python
# 1. Load a dataset and generate a summary DataFrame.
# 2. Create an HTML email with:
#    - A title.
#    - A summary table from the data.
#    - A simple chart (saved as PNG) attached to the email.
# 3. Send the email to a test address.
```

---

### Summary and Revision Notes

- `smtplib` for sending emails.
- `email.mime` for constructing email messages.
- Use environment variables for credentials (`os.getenv`).
- `starttls()` secures the connection.
- Attach files using `MIMEBase`.

---

## Lesson 10.4 – Report Generation

### Concept Explanation

Report generation is the process of automatically creating formatted documents (PDF, HTML, Excel) from data. This is one of the most valuable automation tasks for data analysts.

**Key libraries**:
- **`pandas`**: Creating data summaries.
- **`matplotlib` / `seaborn`**: Creating charts for reports.
- **`reportlab`**: Creating PDF reports.
- **`jinja2`**: Templating for HTML reports.
- **`weasyprint`**: Converting HTML to PDF.

**Common report types**:
1. **HTML reports**: Great for web-based dashboards and emails.
2. **PDF reports**: Professional, print-ready documents.
3. **Excel reports**: For stakeholders who need data to manipulate.

---

### Importance and Real-World Use Cases

- **Why it matters**: Report generation saves countless hours of manual copy-pasting and formatting. It ensures consistency and punctuality.

- **Use cases**:
  - A **financial analyst** generates a monthly PDF report for the board.
  - A **marketing analyst** creates an HTML report with charts for the team.
  - A **data scientist** generates a model evaluation report.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from datetime import datetime
import os

# 1. Prepare data
def prepare_data():
    # Load and summarise data
    df = pd.read_csv('sales_data.csv')
    summary = df.groupby('category')['sales'].agg(['sum', 'mean', 'count']).reset_index()
    summary.columns = ['Category', 'Total Sales', 'Average Sales', 'Count']
    return df, summary

# 2. Create charts
def create_charts(df, output_dir):
    """Create and save charts for the report."""
    os.makedirs(output_dir, exist_ok=True)
    
    # Chart 1: Sales by category
    plt.figure(figsize=(10, 6))
    df.groupby('category')['sales'].sum().plot(kind='bar', color='skyblue')
    plt.title('Total Sales by Category')
    plt.xlabel('Category')
    plt.ylabel('Total Sales')
    plt.tight_layout()
    plt.savefig(os.path.join(output_dir, 'sales_by_category.png'))
    plt.close()
    
    # Chart 2: Sales trend
    if 'date' in df.columns:
        df['date'] = pd.to_datetime(df['date'])
        daily = df.groupby('date')['sales'].sum()
        plt.figure(figsize=(12, 6))
        daily.plot(color='darkblue')
        plt.title('Daily Sales Trend')
        plt.xlabel('Date')
        plt.ylabel('Sales')
        plt.tight_layout()
        plt.savefig(os.path.join(output_dir, 'sales_trend.png'))
        plt.close()

# 3. Generate HTML report
def generate_html_report(summary, output_file):
    """Generate an HTML report from data."""
    html = f"""
    <!DOCTYPE html>
    <html>
    <head>
        <title>Sales Report</title>
        <style>
            body {{ font-family: Arial, sans-serif; margin: 40px; }}
            h1 {{ color: #2c3e50; }}
            table {{ border-collapse: collapse; width: 100%; margin: 20px 0; }}
            th {{ background-color: #3498db; color: white; padding: 10px; }}
            td {{ padding: 10px; border-bottom: 1px solid #ddd; }}
            .chart {{ margin: 20px 0; }}
            .footer {{ margin-top: 40px; font-size: 12px; color: #7f8c8d; }}
        </style>
    </head>
    <body>
        <h1>📊 Sales Performance Report</h1>
        <p><strong>Generated:</strong> {datetime.now().strftime('%Y-%m-%d %H:%M')}</p>
        
        <h2>Summary</h2>
        <table>
            <tr><th>Category</th><th>Total Sales</th><th>Average Sales</th><th>Count</th></tr>
            {''.join(f'<tr><td>{row["Category"]}</td><td>${row["Total Sales"]:,.2f}</td><td>${row["Average Sales"]:,.2f}</td><td>{row["Count"]}</td></tr>' for _, row in summary.iterrows())}
        </table>
        
        <h2>Visualisations</h2>
        <div class="chart">
            <img src="sales_by_category.png" style="max-width: 100%;">
        </div>
        <div class="chart">
            <img src="sales_trend.png" style="max-width: 100%;">
        </div>
        
        <div class="footer">
            <p>This report was automatically generated.</p>
        </div>
    </body>
    </html>
    """
    
    with open(output_file, 'w') as f:
        f.write(html)
    print(f"HTML report saved as {output_file}")

# 4. Generate PDF report (using reportlab)
def generate_pdf_report(summary, output_file):
    """Generate a PDF report using reportlab."""
    from reportlab.lib.pagesizes import letter
    from reportlab.platypus import SimpleDocTemplate, Table, TableStyle, Paragraph, Spacer, Image
    from reportlab.lib.styles import getSampleStyleSheet, ParagraphStyle
    from reportlab.lib import colors
    from reportlab.lib.units import inch
    
    doc = SimpleDocTemplate(output_file, pagesize=letter)
    styles = getSampleStyleSheet()
    story = []
    
    # Title
    title_style = ParagraphStyle('Title', parent=styles['Heading1'], fontSize=24, alignment=1)
    story.append(Paragraph("Sales Performance Report", title_style))
    story.append(Spacer(1, 12))
    
    # Date
    story.append(Paragraph(f"Generated: {datetime.now().strftime('%Y-%m-%d')}", styles['Normal']))
    story.append(Spacer(1, 12))
    
    # Table
    table_data = [['Category', 'Total Sales', 'Average Sales', 'Count']]
    for _, row in summary.iterrows():
        table_data.append([
            row['Category'],
            f"${row['Total Sales']:,.2f}",
            f"${row['Average Sales']:,.2f}",
            str(row['Count'])
        ])
    
    table = Table(table_data, colWidths=[1.5*inch, 1.5*inch, 1.5*inch, 1*inch])
    table.setStyle(TableStyle([
        ('BACKGROUND', (0, 0), (-1, 0), colors.grey),
        ('TEXTCOLOR', (0, 0), (-1, 0), colors.whitesmoke),
        ('ALIGN', (0, 0), (-1, -1), 'CENTER'),
        ('FONTNAME', (0, 0), (-1, 0), 'Helvetica-Bold'),
        ('FONTSIZE', (0, 0), (-1, 0), 12),
        ('BOTTOMPADDING', (0, 0), (-1, 0), 12),
        ('BACKGROUND', (0, 1), (-1, -1), colors.beige),
        ('GRID', (0, 0), (-1, -1), 1, colors.black),
    ]))
    story.append(table)
    
    # Build PDF
    doc.build(story)
    print(f"PDF report saved as {output_file}")

# 5. Main pipeline
def generate_full_report():
    """Generate all report components."""
    # Prepare data
    df, summary = prepare_data()
    
    # Create charts
    create_charts(df, 'report_images')
    
    # Generate reports
    generate_html_report(summary, 'sales_report.html')
    
    try:
        generate_pdf_report(summary, 'sales_report.pdf')
    except ImportError:
        print("reportlab not installed. PDF generation skipped.")
    
    print("Report generation complete!")

# generate_full_report()
```

**Creating an Excel Report**:

```python
def create_excel_report(df, output_file):
    """Create a comprehensive Excel report."""
    with pd.ExcelWriter(output_file, engine='openpyxl') as writer:
        # Raw data
        df.to_excel(writer, sheet_name='Raw Data', index=False)
        
        # Summary
        summary = df.groupby('category')['sales'].agg(['sum', 'mean', 'count']).reset_index()
        summary.columns = ['Category', 'Total', 'Average', 'Count']
        summary.to_excel(writer, sheet_name='Summary', index=False)
        
        # Pivot table
        pivot = pd.pivot_table(df, values='sales', index='region', columns='category', aggfunc='sum')
        pivot.to_excel(writer, sheet_name='Pivot')
        
        # Monthly summary (if date column exists)
        if 'date' in df.columns:
            df['month'] = pd.to_datetime(df['date']).dt.month
            monthly = df.groupby('month')['sales'].sum().reset_index()
            monthly.to_excel(writer, sheet_name='Monthly', index=False)
    
    print(f"Excel report saved as {output_file}")
```

---

### Practical Examples

- **Example 1**: A daily sales report with charts and tables.
- **Example 2**: A monthly KPI dashboard sent via email.
- **Example 3**: A project status report with visualisations.

---

### Hands-on Coding Exercises

**Exercise 10.4** – Report generation:
```python
# 1. Load a dataset (e.g., 'titanic' or any dataset).
# 2. Create an HTML report with:
#    - Summary statistics.
#    - A bar chart of a categorical variable.
#    - A histogram of a numeric variable.
# 3. Save the report and open it in a browser.
```

---

### Mini Quiz

1. What is the purpose of report generation?
2. How do you create charts for a report?
3. What are the advantages of HTML reports over PDF?
4. How do you create a PDF report in Python?
5. What is the role of templates in report generation?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Hardcoding values in reports | Use templating and variables |
| Not including timestamps | Always add a timestamp for versioning |
| Forgetting to close plot figures | Use `plt.close()` to free memory |
| Using absolute paths for images | Use relative paths for portability |

---

### Interview Questions

1. **How would you generate a daily sales report automatically?**  
   *Answer*: I would write a script that runs daily, pulls data from a database or CSV, creates charts, and generates an HTML or PDF report, then emails it to stakeholders.

2. **What tools would you use to generate PDF reports?**  
   *Answer*: `reportlab` for direct PDF creation, or `weasyprint`/`wkhtmltopdf` to convert HTML to PDF.

3. **How do you include dynamic data in a report?**  
   *Answer*: Using templates (like Jinja2) that populate with data from DataFrames.

---

### Assignment and Mini Project

**Assignment 10.4** – Report generator:
```python
# 1. Build a complete report generation pipeline that:
#    - Loads data.
#    - Creates charts.
#    - Generates an HTML report with a table and chart.
#    - Generates a PDF version.
#    - Saves both with a timestamp in the filename.
```

---

### Summary and Revision Notes

- HTML reports are great for email and web.
- PDF reports are professional and print-ready.
- `matplotlib` creates charts.
- `reportlab` creates PDFs.
- Always include timestamps in report filenames.

---

## Lesson 10.5 – Scheduled Tasks

### Concept Explanation

Scheduling tasks allows your scripts to run automatically at specified times – daily, weekly, or hourly. This is the essence of automation: scripts that run without manual intervention.

**Methods for scheduling Python scripts**:

| **Method** | **Platform** | **Best For** |
|------------|--------------|--------------|
| **`schedule`** (Python library) | Cross-platform | Lightweight, in-script scheduling |
| **Cron (Linux/macOS)** | Unix/Linux/macOS | Production-ready, system-level |
| **Task Scheduler (Windows)** | Windows | Enterprise Windows environments |
| **Airflow / Prefect** | Cross-platform | Complex workflow orchestration |
| **Cloud services (AWS Lambda, GCP Cloud Functions)** | Cloud | Serverless, event-driven |

**The `schedule` library**:
- Simple and lightweight.
- Runs within a loop in your script.
- Perfect for small, self-contained scripts.

---

### Importance and Real-World Use Cases

- **Why it matters**: Scheduled tasks transform manual scripts into automated workflows that run reliably without human intervention.

- **Use cases**:
  - A **data analyst** schedules a script to run every morning at 6 AM to generate the daily sales report.
  - A **data engineer** schedules a pipeline to run hourly to ingest streaming data.
  - A **machine learning engineer** schedules a model retraining job weekly.

---

### Step-by-Step Demonstration

```python
# 1. Using the 'schedule' library
import schedule
import time
import datetime

def job():
    """The task to be scheduled."""
    print(f"Running job at {datetime.datetime.now()}")
    # Your actual task here (e.g., generate report, send email, etc.)

# Schedule the job
# Run every day at 9:00 AM
schedule.every().day.at("09:00").do(job)

# Run every hour
schedule.every().hour.do(job)

# Run every 10 minutes
schedule.every(10).minutes.do(job)

# Run every Monday at 8:00 AM
schedule.every().monday.at("08:00").do(job)

# Run on weekdays
schedule.every().monday.do(job)
schedule.every().wednesday.do(job)

# Run a specific function once
schedule.every().day.at("12:00").do(job)

print("Scheduler started. Press Ctrl+C to stop.")
try:
    while True:
        schedule.run_pending()
        time.sleep(1)
except KeyboardInterrupt:
    print("Scheduler stopped.")

# 2. Scheduling with cron (Linux/macOS)
"""
# Edit cron jobs: crontab -e

# Run daily at 6 AM
0 6 * * * /usr/bin/python3 /path/to/your_script.py

# Run hourly
0 * * * * /usr/bin/python3 /path/to/your_script.py

# Run every Monday at 8 AM
0 8 * * 1 /usr/bin/python3 /path/to/your_script.py
"""

# 3. Scheduling with Windows Task Scheduler (conceptual)
"""
# Create a batch file (run_script.bat)
@echo off
python C:\path\to\your_script.py

# In Task Scheduler, create a new task:
# - Trigger: Daily at 6:00 AM
# - Action: Start the batch file
"""

# 4. Creating a complete scheduled script
def main_script():
    print("=" * 60)
    print(f"SCHEDULED TASK RUNNING: {datetime.datetime.now()}")
    print("=" * 60)
    
    # Your actual automation tasks
    # 1. Download data
    # 2. Process data
    # 3. Generate report
    # 4. Send email
    print("Task completed successfully!")

if __name__ == "__main__":
    # Schedule the main script
    schedule.every().day.at("06:00").do(main_script)
    
    print("Automated pipeline scheduled. Running every day at 6:00 AM.")
    
    while True:
        schedule.run_pending()
        time.sleep(60)  # Check every minute
```

**Using `schedule` with Multiple Jobs**:

```python
def daily_report():
    print("Generating daily report...")
    # Report generation code

def hourly_check():
    print("Running hourly data check...")
    # Data validation code

def weekly_cleanup():
    print("Cleaning up old files...")
    # Cleanup code

# Schedule different jobs
schedule.every().day.at("06:00").do(daily_report)
schedule.every().hour.do(hourly_check)
schedule.every().sunday.at("00:00").do(weekly_cleanup)

print("Scheduler running...")
while True:
    schedule.run_pending()
    time.sleep(60)
```

**A Complete Automation Script**:

```python
# report_automation.py
import schedule
import time
import datetime
import pandas as pd
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText

def generate_report():
    """Generate daily sales report."""
    print(f"Generating report at {datetime.datetime.now()}")
    
    # 1. Load data
    df = pd.read_csv('sales_data.csv')
    
    # 2. Process data
    summary = df.groupby('region')['sales'].sum().to_string()
    
    # 3. Create email
    sender = os.getenv('EMAIL_USER')
    recipient = os.getenv('EMAIL_RECIPIENT')
    subject = f"Daily Sales Report - {datetime.datetime.now().strftime('%Y-%m-%d')}"
    body = f"""
    Hello Team,
    
    Here is today's sales summary:
    
    {summary}
    
    Regards,
    Automation Bot
    """
    
    # 4. Send email (simplified)
    print(f"Email ready to send to {recipient}")
    print(f"Subject: {subject}")
    print(f"Body: {body}")
    print("Report generation complete!")

if __name__ == "__main__":
    # Schedule at 8 AM daily
    schedule.every().day.at("08:00").do(generate_report)
    
    print("Report automation started. Running daily at 8:00 AM.")
    
    while True:
        schedule.run_pending()
        time.sleep(60)
```

---

### Practical Examples

- **Example 1**: A script that runs daily at 6 AM to download and process data.
- **Example 2**: A script that runs weekly to archive old files.
- **Example 3**: A script that runs hourly to check for new data.

---

### Hands-on Coding Exercises

**Exercise 10.5** – Scheduler:
```python
# 1. Write a function that prints "Hello, World!".
# 2. Schedule it to run every minute.
# 3. Schedule a second function to run every 5 minutes.
# 4. Add a function that runs at a specific time (e.g., 3:00 PM).
# 5. Run the scheduler for 5 minutes and observe the output.
```

---

### Mini Quiz

1. What is the `schedule` library used for?
2. How do you schedule a script to run daily at 6 AM?
3. What is the difference between cron and the `schedule` library?
4. How do you stop a scheduled script?
5. Why is it important to use `time.sleep()` in a scheduler loop?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Running the scheduler in a loop without a pause | Use `time.sleep()` to prevent CPU overload |
| Not logging scheduler events | Add logging for debugging |
| Using `schedule` in production without error handling | Implement try-except and retry logic |
| Not considering time zones | Use UTC or specify timezone |

---

### Interview Questions

1. **How do you schedule a Python script to run daily?**  
   *Answer*: Using cron on Linux/macOS, Task Scheduler on Windows, or the `schedule` library with a while loop.

2. **What is the difference between cron and the `schedule` library?**  
   *Answer*: `schedule` is a Python library that runs within a script. Cron is an operating-system-level scheduler that executes scripts independently.

3. **How do you ensure a scheduled script runs reliably?**  
   *Answer*: Implement logging, error handling, and alerting for failures.

---

### Assignment and Mini Project

**Assignment 10.5** – Automation scheduler:
```python
# 1. Write a Python script that:
#    - Downloads a public CSV file.
#    - Processes it (e.g., calculates summary statistics).
#    - Saves a summary report.
#    - Sends an email notification.
# 2. Schedule it to run daily at a specific time using the schedule library.
# 3. Log all activities.
```

---

### Summary and Revision Notes

- `schedule` library for in-script scheduling.
- Cron for Unix/Linux systems.
- Task Scheduler for Windows.
- Always add logging and error handling.
- Use `time.sleep()` to prevent CPU overload.

---

## Lesson 10.6 – Data Collection Scripts

### Concept Explanation

Data collection scripts automate the process of gathering data from various sources – APIs, websites, databases, and files. They are the foundation of any data pipeline.

**Common data collection methods**:
1. **API calls**: Fetching data from REST APIs.
2. **Web scraping**: Extracting data from websites (using BeautifulSoup, Scrapy).
3. **Database queries**: Pulling data from SQL databases.
4. **File downloads**: Downloading CSV, Excel, or JSON files from URLs.
5. **File watching**: Monitoring folders for new files.

**Key libraries**:
- **`requests`**: API calls and file downloads.
- **`beautifulsoup4`**: Web scraping.
- **`pandas`**: Reading data files.
- **`sqlalchemy`**: Database connections.

---

### Importance and Real-World Use Cases

- **Why it matters**: Data collection is the first step in any analytics pipeline. Automation ensures data is collected reliably and on time.

- **Use cases**:
  - A **data analyst** collects daily stock prices from an API.
  - A **data engineer** scrapes product data from an e-commerce website.
  - A **marketing analyst** pulls campaign data from a CRM database.

---

### Step-by-Step Demonstration

```python
import requests
import pandas as pd
import json
import time
from pathlib import Path

# 1. Collecting data from an API
def fetch_weather_data(api_key, city):
    """Fetch weather data from OpenWeatherMap API."""
    url = f'https://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric'
    
    try:
        response = requests.get(url)
        response.raise_for_status()
        data = response.json()
        
        return {
            'city': data['name'],
            'temperature': data['main']['temp'],
            'humidity': data['main']['humidity'],
            'conditions': data['weather'][0]['description'],
            'timestamp': pd.Timestamp.now()
        }
    except requests.exceptions.RequestException as e:
        print(f"Error fetching weather: {e}")
        return None

# 2. Collecting data from multiple sources
def collect_all_data():
    """Collect data from multiple sources."""
    data = {}
    
    # Weather data (example)
    # data['weather'] = fetch_weather_data('YOUR_API_KEY', 'London')
    
    # Stock data (example with Alpha Vantage)
    # data['stocks'] = fetch_stock_data('YOUR_API_KEY', 'AAPL')
    
    # File download (example)
    # download_csv('https://example.com/data.csv', 'data.csv')
    
    return data

# 3. Downloading CSV files
def download_csv(url, output_file):
    """Download a CSV file from a URL."""
    try:
        response = requests.get(url)
        response.raise_for_status()
        
        with open(output_file, 'wb') as f:
            f.write(response.content)
        print(f"Downloaded {output_file}")
        return True
    except Exception as e:
        print(f"Error downloading: {e}")
        return False

# 4. Collecting data from a database (using SQLite)
def collect_from_db(db_file, query):
    """Collect data from a SQLite database."""
    import sqlite3
    
    try:
        conn = sqlite3.connect(db_file)
        df = pd.read_sql_query(query, conn)
        conn.close()
        return df
    except Exception as e:
        print(f"Database error: {e}")
        return None

# 5. Data collection pipeline with scheduling
def daily_data_pipeline():
    """Complete data collection pipeline."""
    print("Starting daily data collection...")
    
    # Step 1: Download CSV
    # download_csv('https://example.com/daily_sales.csv', 'daily_sales.csv')
    
    # Step 2: Load and process data
    # df = pd.read_csv('daily_sales.csv')
    
    # Step 3: Clean and transform
    # df_cleaned = clean_data(df)
    
    # Step 4: Save to database
    # save_to_db(df_cleaned)
    
    # Step 5: Archive raw file
    # shutil.move('daily_sales.csv', 'archive/')
    
    print("Data collection complete!")

# 6. Building a reusable data collector
class DataCollector:
    """A reusable data collection class."""
    
    def __init__(self, output_dir='data'):
        self.output_dir = Path(output_dir)
        self.output_dir.mkdir(exist_ok=True)
    
    def fetch_api(self, url, params=None, headers=None):
        """Fetch data from an API."""
        try:
            response = requests.get(url, params=params, headers=headers)
            response.raise_for_status()
            return response.json()
        except Exception as e:
            print(f"API error: {e}")
            return None
    
    def fetch_csv(self, url, filename):
        """Download a CSV file."""
        response = requests.get(url)
        if response.status_code == 200:
            filepath = self.output_dir / filename
            with open(filepath, 'wb') as f:
                f.write(response.content)
            print(f"Saved {filename}")
            return filepath
        else:
            print(f"Failed to download {filename}")
            return None
    
    def fetch_all_sources(self, sources):
        """Fetch from multiple sources."""
        results = {}
        for name, source in sources.items():
            if source['type'] == 'csv':
                results[name] = self.fetch_csv(source['url'], source['filename'])
            elif source['type'] == 'api':
                results[name] = self.fetch_api(source['url'])
        return results

# Usage example
# collector = DataCollector('collected_data')
# collector.fetch_csv('https://example.com/data.csv', 'data.csv')
```

**Example: Collecting Data from Multiple Sources**:

```python
def collect_market_data():
    """Collect market data from various sources."""
    collector = DataCollector('market_data')
    
    sources = {
        'stock_prices': {
            'type': 'api',
            'url': 'https://api.example.com/stocks'
        },
        'market_summary': {
            'type': 'csv',
            'url': 'https://api.example.com/market_summary.csv',
            'filename': 'market_summary.csv'
        }
    }
    
    return collector.fetch_all_sources(sources)
```

---

### Practical Examples

- **Example 1**: A script that collects daily weather data from an API and stores it in a CSV.
- **Example 2**: A script that downloads multiple CSV files from a website.
- **Example 3**: A script that collects data from a database and saves it to a file.

---

### Hands-on Coding Exercises

**Exercise 10.6** – Data collector:
```python
# 1. Write a function that fetches data from a public API (e.g., JSONPlaceholder).
# 2. Write a function that downloads a CSV file from a URL.
# 3. Write a function that reads data from a SQLite database.
# 4. Combine these into a single data collection pipeline.
# 5. Save the collected data to a CSV file.
```

---

### Mini Quiz

1. What library is used for API calls?
2. How do you download a file from the internet?
3. What is the purpose of a data collection pipeline?
4. How do you handle API rate limits?
5. Why is error handling important in data collection?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not handling API rate limits | Add delays between requests |
| Not checking response status codes | Always check `response.status_code` |
| Not logging failures | Log all errors for debugging |
| Hardcoding API keys | Use environment variables |
| Not handling data format changes | Use versioning or schema validation |

---

### Interview Questions

1. **How do you collect data from an API?**  
   *Answer*: Using the `requests` library to make HTTP requests, handling authentication, and parsing the JSON response.

2. **How do you handle API rate limits?**  
   *Answer*: By adding delays (`time.sleep()`) between requests or using exponential backoff.

3. **How do you build a robust data collection pipeline?**  
   *Answer*: With error handling, logging, retries, and scheduling.

---

### Assignment and Mini Project

**Assignment 10.6** – Data collector:
```python
# 1. Build a data collection script that:
#    - Fetches data from a public API (e.g., weather, news, or stocks).
#    - Downloads a CSV file from a URL.
#    - Saves both to a 'data' folder.
#    - Handles errors gracefully.
#    - Logs all activities.
```

---

### Summary and Revision Notes

- `requests` for API calls and downloads.
- Handle rate limits with delays.
- Always validate and log responses.
- Use environment variables for sensitive credentials.
- Build reusable collectors for common tasks.

---

## Final Phase 10 Assessment

Now that you have completed all lessons, test your overall understanding.

### Self-Evaluation Checklist

- I can automate file and folder management.

- I can create and format Excel reports.

- I can send automated emails with attachments.

- I can generate HTML and PDF reports.

- I can schedule scripts to run automatically.

- I can build data collection pipelines.


---

### Answers to Mini Quizzes

**Lesson 10.1**: 1. `os.rename()` renames; `shutil.move()` moves. 2. `os.path.exists()`. 3. Finds files matching a pattern. 4. Modern object-oriented path handling. 5. `os.path.getmtime()` or `Path.stat().st_mtime`.

**Lesson 10.2**: 1. Pandas for simple read/write; openpyxl for advanced formatting. 2. Using `pd.ExcelWriter`. 3. `ws['A1'] = '=SUM(B1:B10)'`. 4. Manages multiple sheets. 5. Use `pd.concat()`.

**Lesson 10.3**: 1. `smtplib`. 2. To keep credentials secure. 3. Secures the SMTP connection. 4. Using `MIMEBase`. 5. `MIMEText` is plain text; `MIMEMultipart` supports attachments.

**Lesson 10.4**: 1. To create formatted documents automatically. 2. Using `matplotlib`. 3. HTML is interactive, PDF is printable. 4. Using `reportlab` or converting HTML. 5. To separate structure from content.

**Lesson 10.5**: 1. In-script scheduling. 2. `schedule.every().day.at("06:00").do(job)`. 3. `schedule` runs in Python, cron is system-level. 4. Keyboard interrupt or process termination. 5. To prevent CPU overload.

**Lesson 10.6**: 1. `requests`. 2. `requests.get(url)` and write content. 3. To automate data gathering. 4. Add delays. 5. To handle failures gracefully.

---

**Congratulations!** You have completed all phases of this comprehensive Python for Data Analytics curriculum. You now have the skills to build end-to-end data pipelines, automate workflows, and deliver insights at scale. Keep building!


---




<br/><br/><br/>
<center> <b>Happy Learning! 😊</b> </center>


