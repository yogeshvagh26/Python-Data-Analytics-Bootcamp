# Phase 12: Real-World Data Analytics Projects

Welcome to the **final phase** of your Python for Data Analytics journey! You have mastered the tools, techniques, and concepts needed to become a proficient data analyst. Now, it's time to put everything together and build **real-world projects** that demonstrate your skills.

This phase is different from the others. Instead of learning new concepts, you will apply everything you've learned to solve practical business problems. Each project is designed to simulate a real-world scenario that you would encounter as a data analyst, data scientist, or BI developer.

**Why projects matter**:
- **Portfolio building**: These projects will form the foundation of your data analytics portfolio.
- **Skill reinforcement**: Applying your skills to real problems solidifies your learning.
- **Interview preparation**: Many interview questions are based on projects like these.
- **Business acumen**: You'll learn to translate business problems into data solutions.

The projects cover a wide range of industries and analytics domains:

1. **Sales Analysis Dashboard** – Understand revenue, trends, and product performance.
2. **Customer Segmentation Analysis** – Group customers based on behaviour.
3. **HR Analytics** – Analyse employee data for retention and performance insights.
4. **Financial Data Analysis** – Analyse financial statements and metrics.
5. **Stock Market Data Analysis** – Analyse stock prices and returns.
6. **COVID-19 Data Analysis** – Analyse pandemic trends and patterns.
7. **IPL Data Analysis** – Analyse cricket match data.
8. **Retail Business Analysis** – Analyse retail sales and operations.
9. **E-commerce Sales Dashboard** – Analyse online sales and customer behaviour.
10. **Marketing Campaign Analysis** – Measure campaign performance and ROI.

Each project includes:
- A clear business problem statement.
- Step-by-step guidance.
- Code examples.
- Visualisations.
- Key insights and recommendations.
- Hands-on exercises.

Let's build your portfolio!

---

## Project 12.1 – Sales Analysis Dashboard

### Concept Explanation

A **Sales Analysis Dashboard** helps businesses understand their revenue, product performance, regional trends, and sales team effectiveness. It answers questions like:
- What are our top-selling products?
- Which regions generate the most revenue?
- How are sales trending over time?
- Which sales reps are performing best?

**Key metrics**:
- **Revenue**: Total sales, average order value, growth rate.
- **Products**: Top-selling products, product categories.
- **Regions**: Sales by region, country, city.
- **Time**: Monthly, quarterly, yearly trends.
- **Sales Reps**: Performance by rep, team.

**Tools**: Pandas, Matplotlib, Seaborn, Plotly (optional).

---

### Importance and Real-World Use Cases

- **Why it matters**: Sales is the lifeblood of any organisation. A sales dashboard provides leadership with real-time visibility into performance, enabling data-driven decisions.

- **Use cases**:
  - A **sales director** uses the dashboard to identify underperforming regions.
  - A **product manager** tracks product performance to guide R&D.
  - A **CEO** monitors overall revenue trends.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from datetime import datetime, timedelta

# 1. Generate simulated sales data
np.random.seed(42)

# Create a date range
dates = pd.date_range('2024-01-01', '2024-12-31', freq='D')

# Generate data
products = ['Product A', 'Product B', 'Product C', 'Product D', 'Product E']
regions = ['North', 'South', 'East', 'West']
sales_reps = ['Alice', 'Bob', 'Charlie', 'Diana', 'Eve']

data = {
    'Date': np.random.choice(dates, 5000),
    'Product': np.random.choice(products, 5000, p=[0.3, 0.25, 0.2, 0.15, 0.1]),
    'Region': np.random.choice(regions, 5000),
    'Sales_Rep': np.random.choice(sales_reps, 5000),
    'Quantity': np.random.randint(1, 20, 5000),
    'Unit_Price': np.random.randint(50, 500, 5000)
}

df = pd.DataFrame(data)
df['Revenue'] = df['Quantity'] * df['Unit_Price']
df['Month'] = df['Date'].dt.month
df['Quarter'] = df['Date'].dt.quarter

print("Sales Data Preview:")
print(df.head())
print(f"\nDataset shape: {df.shape}")

# 2. Exploratory Data Analysis
print("\n" + "=" * 60)
print("SALES DATA ANALYSIS")
print("=" * 60)

# Total revenue
total_revenue = df['Revenue'].sum()
avg_order_value = df['Revenue'].mean()
total_transactions = len(df)

print(f"Total Revenue: ${total_revenue:,.2f}")
print(f"Average Order Value: ${avg_order_value:,.2f}")
print(f"Total Transactions: {total_transactions:,}")

# Revenue by product
product_revenue = df.groupby('Product')['Revenue'].sum().sort_values(ascending=False)
print("\nRevenue by Product:")
print(product_revenue)

# Revenue by region
region_revenue = df.groupby('Region')['Revenue'].sum().sort_values(ascending=False)
print("\nRevenue by Region:")
print(region_revenue)

# Revenue by month
monthly_revenue = df.groupby('Month')['Revenue'].sum()
print("\nMonthly Revenue:")
print(monthly_revenue)

# 3. Visualisations
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
fig.suptitle('Sales Performance Dashboard', fontsize=16, fontweight='bold')

# 1. Revenue by Product (Top 5)
product_revenue.sort_values(ascending=True).tail(5).plot(kind='barh', ax=axes[0, 0], color='skyblue')
axes[0, 0].set_title('Revenue by Product')
axes[0, 0].set_xlabel('Revenue ($)')
axes[0, 0].set_ylabel('Product')

# 2. Revenue by Region
region_revenue.plot(kind='bar', ax=axes[0, 1], color='lightgreen')
axes[0, 1].set_title('Revenue by Region')
axes[0, 1].set_ylabel('Revenue ($)')
axes[0, 1].set_xlabel('Region')

# 3. Monthly Revenue Trend
monthly_revenue.plot(kind='line', marker='o', ax=axes[1, 0], color='darkblue', linewidth=2)
axes[1, 0].set_title('Monthly Revenue Trend')
axes[1, 0].set_xlabel('Month')
axes[1, 0].set_ylabel('Revenue ($)')
axes[1, 0].grid(True, alpha=0.3)

# 4. Revenue by Sales Rep
rep_revenue = df.groupby('Sales_Rep')['Revenue'].sum().sort_values(ascending=True)
rep_revenue.plot(kind='barh', ax=axes[1, 1], color='coral')
axes[1, 1].set_title('Revenue by Sales Rep')
axes[1, 1].set_xlabel('Revenue ($)')
axes[1, 1].set_ylabel('Sales Rep')

plt.tight_layout()
plt.show()

# 4. Additional KPIs
print("\n" + "=" * 60)
print("KEY PERFORMANCE INDICATORS")
print("=" * 60)

# Top product
top_product = product_revenue.idxmax()
top_product_revenue = product_revenue.max()
print(f"Top Product: {top_product} (${top_product_revenue:,.2f})")

# Top region
top_region = region_revenue.idxmax()
top_region_revenue = region_revenue.max()
print(f"Top Region: {top_region} (${top_region_revenue:,.2f})")

# Top sales rep
top_rep = rep_revenue.idxmax()
top_rep_revenue = rep_revenue.max()
print(f"Top Sales Rep: {top_rep} (${top_rep_revenue:,.2f})")

# Monthly growth
if len(monthly_revenue) > 1:
    growth = (monthly_revenue.iloc[-1] - monthly_revenue.iloc[0]) / monthly_revenue.iloc[0] * 100
    print(f"Yearly Growth: {growth:.1f}%")

# 5. Insights and Recommendations
print("\n" + "=" * 60)
print("KEY INSIGHTS AND RECOMMENDATIONS")
print("=" * 60)

insights = [
    f"Product {top_product} is the top performer with ${top_product_revenue:,.2f} in revenue.",
    f"Region {top_region} generates the most revenue.",
    f"Sales Rep {top_rep} is the top performer.",
    f"Total revenue for the period: ${total_revenue:,.2f}.",
    f"Average order value: ${avg_order_value:,.2f}."
]

for i, insight in enumerate(insights, 1):
    print(f"{i}. {insight}")

print("\nRecommendations:")
print("1. Focus marketing efforts on top-performing products.")
print("2. Investigate underperforming regions for opportunities.")
print("3. Recognise and reward top sales reps.")
print("4. Analyse monthly trends to identify seasonal patterns.")
print("5. Consider upselling strategies to increase average order value.")

# 6. Save the dashboard data
summary_df = pd.DataFrame({
    'Metric': ['Total Revenue', 'Avg Order Value', 'Total Transactions', 'Top Product', 'Top Region', 'Top Sales Rep'],
    'Value': [
        f'${total_revenue:,.2f}',
        f'${avg_order_value:,.2f}',
        f'{total_transactions:,}',
        top_product,
        top_region,
        top_rep
    ]
})

summary_df.to_csv('sales_dashboard_summary.csv', index=False)
print("\nDashboard summary saved to 'sales_dashboard_summary.csv'")
```

**Building a Complete Dashboard with Plotly**:

```python
# Optional: Create an interactive dashboard with Plotly
import plotly.express as px
import plotly.subplots as sp
import plotly.graph_objects as go

# Create subplots
fig = sp.make_subplots(
    rows=2, cols=2,
    subplot_titles=('Revenue by Product', 'Revenue by Region', 'Monthly Revenue Trend', 'Revenue by Sales Rep')
)

# Add traces
# Product revenue
fig.add_trace(
    go.Bar(x=product_revenue.index, y=product_revenue.values, name='Product Revenue'),
    row=1, col=1
)

# Region revenue
fig.add_trace(
    go.Bar(x=region_revenue.index, y=region_revenue.values, name='Region Revenue', marker_color='lightgreen'),
    row=1, col=2
)

# Monthly trend
fig.add_trace(
    go.Scatter(x=monthly_revenue.index, y=monthly_revenue.values, mode='lines+markers', name='Monthly Revenue'),
    row=2, col=1
)

# Sales rep revenue
fig.add_trace(
    go.Bar(x=rep_revenue.index, y=rep_revenue.values, name='Sales Rep Revenue', marker_color='coral'),
    row=2, col=2
)

fig.update_layout(height=800, width=1200, title_text='Sales Dashboard')
fig.show()
```

---

### Hands-on Coding Exercises

**Exercise 12.1** – Sales analysis:
```python
# 1. Load the sales data (or generate your own).
# 2. Calculate:
#    - Total revenue by product category.
#    - Average revenue per transaction.
#    - Monthly growth rate.
#    - Top 5 products by revenue.
# 3. Create a dashboard with 4 visualisations.
# 4. Write a summary report with key insights.
```

---

### Mini Quiz

1. What are the key metrics in a sales dashboard?
2. How do you calculate average order value?
3. Why is monthly trend analysis important?
4. What visualisations are most useful for sales data?
5. How do you identify top-performing sales reps?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Ignoring seasonal patterns | Analyse monthly trends to identify seasonality |
| Not segmenting by region/product | Segment to understand performance drivers |
| Using only total revenue | Include other metrics like growth rate, avg order value |
| Not visualising data | Use charts to communicate insights effectively |

---

### Interview Questions

1. **How would you design a sales dashboard for a retail company?**  
   *Answer*: I would include KPIs (total revenue, avg order value), a trend chart, product performance, regional breakdown, and sales rep performance. I'd use interactive filters for date ranges and product categories.

2. **What metrics would you track to measure sales performance?**  
   *Answer*: Total revenue, growth rate, average order value, customer acquisition cost, customer lifetime value, and conversion rate.

3. **How do you identify underperforming products?**  
   *Answer*: By comparing revenue, sales volume, and profit margins across products, and benchmarking against targets.

---

### Assignment and Mini Project

**Project 12.1 – Complete Sales Dashboard**:
```python
# Build a complete sales analysis dashboard that:
# 1. Loads/Generates sales data.
# 2. Calculates all key metrics.
# 3. Creates visualisations for:
#    - Revenue trend over time.
#    - Revenue by product category.
#    - Revenue by region.
#    - Revenue by sales rep.
# 4. Generates a summary report with insights.
# 5. Exports the dashboard data to CSV.
# 6. Saves the visualisations as images.
```

---

## Project 12.2 – Customer Segmentation Analysis

### Concept Explanation

**Customer Segmentation** is the process of dividing customers into groups based on shared characteristics. It helps businesses:
- Personalise marketing messages.
- Identify high-value customers.
- Improve customer retention.
- Optimise product offerings.

**Common segmentation methods**:
1. **Demographic**: Age, gender, income, location.
2. **Behavioural**: Purchase frequency, spending, product preferences.
3. **Psychographic**: Lifestyle, interests, values.
4. **RFM Analysis**: Recency, Frequency, Monetary.

**RFM Analysis**:
- **Recency**: How recently did the customer purchase?
- **Frequency**: How often do they purchase?
- **Monetary**: How much do they spend?

---

### Importance and Real-World Use Cases

- **Why it matters**: Not all customers are the same. Segmentation allows businesses to tailor their approach to different customer groups, maximising ROI.

- **Use cases**:
  - A **marketing team** targets high-value customers with exclusive offers.
  - A **product team** designs products for specific segments.
  - A **customer success team** focuses on retaining at-risk customers.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from datetime import datetime, timedelta

# 1. Generate customer transaction data
np.random.seed(42)

# Create customer data
n_customers = 500
customers = pd.DataFrame({
    'Customer_ID': range(1, n_customers + 1),
    'Age': np.random.randint(18, 70, n_customers),
    'Gender': np.random.choice(['Male', 'Female'], n_customers),
    'Income': np.random.randint(30000, 150000, n_customers)
})

# Generate transactions
n_transactions = 10000
transaction_data = {
    'Customer_ID': np.random.choice(customers['Customer_ID'], n_transactions),
    'Transaction_Date': pd.date_range('2024-01-01', '2024-12-31', periods=n_transactions),
    'Amount': np.random.randint(50, 500, n_transactions)
}
transactions = pd.DataFrame(transaction_data)

# Calculate customer metrics
customer_metrics = transactions.groupby('Customer_ID').agg({
    'Transaction_Date': lambda x: (datetime.now() - x.max()).days,  # Recency
    'Transaction_Date': 'count',  # Frequency
    'Amount': 'sum'  # Monetary
}).rename(columns={
    'Transaction_Date': 'Recency',
    'Amount': 'Monetary'
})
customer_metrics['Frequency'] = transactions.groupby('Customer_ID')['Transaction_Date'].count()

# Merge with customer data
customer_data = customers.merge(customer_metrics, on='Customer_ID')

print("Customer Data Preview:")
print(customer_data.head())

# 2. RFM Analysis
print("\n" + "=" * 60)
print("RFM ANALYSIS")
print("=" * 60)

# Create RFM scores
# Recency: Lower is better (more recent)
r_labels = ['5', '4', '3', '2', '1']
customer_data['R_Score'] = pd.qcut(customer_data['Recency'], q=5, labels=r_labels)

# Frequency: Higher is better
f_labels = ['1', '2', '3', '4', '5']
customer_data['F_Score'] = pd.qcut(customer_data['Frequency'].rank(method='first'), q=5, labels=f_labels)

# Monetary: Higher is better
m_labels = ['1', '2', '3', '4', '5']
customer_data['M_Score'] = pd.qcut(customer_data['Monetary'].rank(method='first'), q=5, labels=m_labels)

# Combined RFM score
customer_data['RFM_Score'] = (
    customer_data['R_Score'].astype(str) +
    customer_data['F_Score'].astype(str) +
    customer_data['M_Score'].astype(str)
)

# 3. Segment customers
def classify_customer(row):
    """Classify customers based on RFM scores."""
    r, f, m = int(row['R_Score']), int(row['F_Score']), int(row['M_Score'])
    
    if r >= 4 and f >= 4 and m >= 4:
        return 'Champions'
    elif r >= 3 and f >= 3 and m >= 3:
        return 'Loyal'
    elif r <= 2 and f >= 3 and m >= 3:
        return 'At Risk'
    elif r <= 2 and f <= 2 and m <= 2:
        return 'Lost'
    elif r >= 4 and f <= 2 and m <= 2:
        return 'New'
    else:
        return 'Regular'

customer_data['Segment'] = customer_data.apply(classify_customer, axis=1)

print("\nCustomer Segments:")
print(customer_data['Segment'].value_counts())

# 4. Segment Analysis
print("\n" + "=" * 60)
print("SEGMENT ANALYSIS")
print("=" * 60)

segment_metrics = customer_data.groupby('Segment').agg({
    'Customer_ID': 'count',
    'Recency': 'mean',
    'Frequency': 'mean',
    'Monetary': 'mean'
}).rename(columns={'Customer_ID': 'Count'})

print(segment_metrics)

# 5. Visualisations
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
fig.suptitle('Customer Segmentation Analysis', fontsize=16, fontweight='bold')

# 1. Segment distribution
segment_counts = customer_data['Segment'].value_counts()
segment_counts.plot(kind='bar', ax=axes[0, 0], color='skyblue')
axes[0, 0].set_title('Customer Segments')
axes[0, 0].set_xlabel('Segment')
axes[0, 0].set_ylabel('Number of Customers')

# 2. Average Monetary by Segment
segment_metrics['Monetary'].sort_values().plot(kind='barh', ax=axes[0, 1], color='lightgreen')
axes[0, 1].set_title('Average Spend by Segment')
axes[0, 1].set_xlabel('Average Monetary')

# 3. RFM Heatmap (average scores by segment)
rfm_segment = customer_data.groupby('Segment').agg({
    'R_Score': lambda x: x.astype(int).mean(),
    'F_Score': lambda x: x.astype(int).mean(),
    'M_Score': lambda x: x.astype(int).mean()
})
sns.heatmap(rfm_segment, annot=True, cmap='YlOrRd', ax=axes[1, 0])
axes[1, 0].set_title('RFM Scores by Segment')

# 4. Customer distribution by income and monetary
scatter = axes[1, 1].scatter(
    customer_data['Income'],
    customer_data['Monetary'],
    c=pd.Categorical(customer_data['Segment']).codes,
    alpha=0.6,
    cmap='viridis'
)
axes[1, 1].set_title('Income vs Spend')
axes[1, 1].set_xlabel('Income')
axes[1, 1].set_ylabel('Monetary')
plt.colorbar(scatter, ax=axes[1, 1], label='Segment')

plt.tight_layout()
plt.show()

# 6. Insights and Recommendations
print("\n" + "=" * 60)
print("KEY INSIGHTS AND RECOMMENDATIONS")
print("=" * 60)

print(f"Total Customers: {len(customer_data)}")
print(f"Top Segment: {customer_data['Segment'].value_counts().index[0]}")

print("\nSegment Insights:")
for segment, count in segment_counts.items():
    avg_spend = segment_metrics.loc[segment, 'Monetary']
    print(f"- {segment}: {count} customers, Avg Spend: ${avg_spend:,.2f}")

print("\nRecommendations:")
print("1. Champions: Reward loyalty with exclusive offers and VIP programmes.")
print("2. Loyal: Encourage with upsell/cross-sell opportunities.")
print("3. At Risk: Re-engage with special offers and personal communication.")
print("4. Lost: Consider win-back campaigns.")
print("5. New: Nurture with welcome offers to build loyalty.")

# 7. Save results
customer_data.to_csv('customer_segmentation_results.csv', index=False)
print("\nResults saved to 'customer_segmentation_results.csv'")
```

---

### Hands-on Coding Exercises

**Exercise 12.2** – Customer segmentation:
```python
# 1. Load customer transaction data.
# 2. Calculate RFM scores for each customer.
# 3. Segment customers into at least 5 groups.
# 4. Analyse each segment's behaviour.
# 5. Create visualisations of the segments.
# 6. Write recommendations for each segment.
```

---

### Mini Quiz

1. What does RFM stand for?
2. What is the purpose of customer segmentation?
3. How do you calculate recency?
4. What is the difference between frequency and monetary?
5. How do you classify customers into segments?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using only one metric for segmentation | Use multiple metrics (RFM) |
| Not updating segments regularly | Recalculate segments periodically |
| Ignoring behavioural data | Include behavioural data for richer segments |
| Over-segmenting | Keep segments actionable (5-8 segments) |

---

### Interview Questions

1. **What is RFM analysis and why is it useful?**  
   *Answer*: RFM analysis segments customers based on Recency, Frequency, and Monetary value. It helps businesses identify high-value customers and those at risk of churn.

2. **How do you segment customers for a marketing campaign?**  
   *Answer*: I would use RFM analysis, demographic data, and behavioural data to create meaningful segments, then tailor marketing messages to each segment.

3. **What metrics would you use to identify high-value customers?**  
   *Answer*: Lifetime value, purchase frequency, average order value, and recency of last purchase.

---

### Assignment and Mini Project

**Project 12.2 – Customer Segmentation Dashboard**:
```python
# Build a complete customer segmentation dashboard that:
# 1. Loads customer transaction data.
# 2. Calculates RFM scores.
# 3. Segments customers.
# 4. Creates visualisations.
# 5. Generates insights and recommendations.
# 6. Exports the results.
```

---

## Project 12.3 – HR Analytics

### Concept Explanation

**HR Analytics** uses data to understand and improve workforce management. It helps organisations:
- Reduce employee turnover.
- Improve hiring processes.
- Enhance employee engagement.
- Optimise workforce planning.

**Key metrics**:
- **Attrition Rate**: Percentage of employees leaving.
- **Headcount**: Total employees, by department, location.
- **Average Tenure**: Average years of service.
- **Satisfaction Scores**: Employee engagement.
- **Hiring Metrics**: Time-to-hire, cost-per-hire.
- **Diversity**: Gender, ethnicity, age distribution.

---

### Importance and Real-World Use Cases

- **Why it matters**: People are an organisation's greatest asset. HR analytics helps retain talent and improve productivity.

- **Use cases**:
  - A **HR Director** monitors attrition and identifies high-turnover departments.
  - A **Talent Acquisition Manager** optimises hiring processes.
  - A **Diversity Officer** tracks diversity metrics.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from datetime import datetime, timedelta

# 1. Generate HR data
np.random.seed(42)

n_employees = 500
departments = ['Engineering', 'Sales', 'Marketing', 'HR', 'Finance', 'Operations']
job_levels = ['Junior', 'Mid', 'Senior', 'Manager', 'Director']
locations = ['New York', 'London', 'Tokyo', 'Sydney', 'Berlin']

# Generate employee data
employees = pd.DataFrame({
    'Employee_ID': range(1, n_employees + 1),
    'Department': np.random.choice(departments, n_employees),
    'Job_Level': np.random.choice(job_levels, n_employees, p=[0.3, 0.35, 0.2, 0.1, 0.05]),
    'Location': np.random.choice(locations, n_employees),
    'Gender': np.random.choice(['Male', 'Female'], n_employees),
    'Age': np.random.randint(22, 65, n_employees),
    'Salary': np.random.randint(40000, 120000, n_employees),
    'Hire_Date': pd.date_range('2018-01-01', '2024-06-01', periods=n_employees),
    'Performance_Score': np.random.uniform(1, 5, n_employees).round(1)
})

# Determine termination status (20% attrition)
terminated = np.random.choice([True, False], n_employees, p=[0.2, 0.8])
employees['Terminated'] = terminated

# Termination dates for terminated employees
employees.loc[terminated, 'Termination_Date'] = pd.date_range('2023-01-01', '2024-06-01', periods=sum(terminated))

# 2. Calculate HR metrics
print("=" * 60)
print("HR ANALYTICS DASHBOARD")
print("=" * 60)

total_employees = len(employees)
active_employees = len(employees[~employees['Terminated']])
terminated_employees = employees['Terminated'].sum()
attrition_rate = (terminated_employees / total_employees) * 100

print(f"Total Employees: {total_employees}")
print(f"Active Employees: {active_employees}")
print(f"Terminated Employees: {terminated_employees}")
print(f"Attrition Rate: {attrition_rate:.1f}%")

# Average tenure
employees['Tenure_Years'] = (pd.Timestamp.now() - employees['Hire_Date']).dt.days / 365.25
avg_tenure = employees['Tenure_Years'].mean()
print(f"Average Tenure: {avg_tenure:.1f} years")

# 3. Department Analysis
print("\n" + "=" * 60)
print("DEPARTMENT ANALYSIS")
print("=" * 60)

dept_stats = employees.groupby('Department').agg({
    'Employee_ID': 'count',
    'Terminated': 'sum',
    'Salary': 'mean',
    'Performance_Score': 'mean',
    'Tenure_Years': 'mean'
}).rename(columns={'Employee_ID': 'Total'})

dept_stats['Attrition_Rate'] = (dept_stats['Terminated'] / dept_stats['Total']) * 100
print(dept_stats)

# 4. Visualisations
fig, axes = plt.subplots(2, 3, figsize=(15, 10))
fig.suptitle('HR Analytics Dashboard', fontsize=16, fontweight='bold')

# 1. Attrition by Department
attrition_by_dept = employees[employees['Terminated']].groupby('Department')['Employee_ID'].count()
total_by_dept = employees.groupby('Department')['Employee_ID'].count()
attrition_pct = (attrition_by_dept / total_by_dept * 100).sort_values(ascending=False)
attrition_pct.plot(kind='bar', ax=axes[0, 0], color='coral')
axes[0, 0].set_title('Attrition Rate by Department')
axes[0, 0].set_xlabel('Department')
axes[0, 0].set_ylabel('Attrition Rate (%)')

# 2. Salary Distribution
sns.histplot(employees['Salary'], kde=True, ax=axes[0, 1], color='skyblue')
axes[0, 1].set_title('Salary Distribution')
axes[0, 1].set_xlabel('Salary')
axes[0, 1].set_ylabel('Count')

# 3. Performance Score by Department
sns.boxplot(data=employees, x='Department', y='Performance_Score', ax=axes[0, 2])
axes[0, 2].set_title('Performance Scores by Department')
axes[0, 2].tick_params(axis='x', rotation=45)

# 4. Tenure by Job Level
tenure_by_level = employees.groupby('Job_Level')['Tenure_Years'].mean().sort_values()
tenure_by_level.plot(kind='bar', ax=axes[1, 0], color='lightgreen')
axes[1, 0].set_title('Average Tenure by Job Level')
axes[1, 0].set_xlabel('Job Level')
axes[1, 0].set_ylabel('Average Tenure (Years)')

# 5. Gender Distribution
gender_counts = employees['Gender'].value_counts()
gender_counts.plot(kind='pie', autopct='%1.1f%%', ax=axes[1, 1])
axes[1, 1].set_title('Gender Distribution')
axes[1, 1].set_ylabel('')

# 6. Attrition by Age Group
employees['Age_Group'] = pd.cut(employees['Age'], bins=[20, 30, 40, 50, 60, 70], labels=['20-29', '30-39', '40-49', '50-59', '60-69'])
attrition_by_age = employees[employees['Terminated']].groupby('Age_Group')['Employee_ID'].count()
total_by_age = employees.groupby('Age_Group')['Employee_ID'].count()
attrition_age_pct = (attrition_by_age / total_by_age * 100).fillna(0)
attrition_age_pct.plot(kind='bar', ax=axes[1, 2], color='orange')
axes[1, 2].set_title('Attrition by Age Group')
axes[1, 2].set_xlabel('Age Group')
axes[1, 2].set_ylabel('Attrition Rate (%)')

plt.tight_layout()
plt.show()

# 5. Insights and Recommendations
print("\n" + "=" * 60)
print("KEY INSIGHTS AND RECOMMENDATIONS")
print("=" * 60)

# Highest attrition department
highest_attrition_dept = attrition_pct.idxmax()
highest_attrition_rate = attrition_pct.max()
print(f"Highest Attrition Department: {highest_attrition_dept} ({highest_attrition_rate:.1f}%)")

# Lowest attrition department
lowest_attrition_dept = attrition_pct.idxmin()
lowest_attrition_rate = attrition_pct.min()
print(f"Lowest Attrition Department: {lowest_attrition_dept} ({lowest_attrition_rate:.1f}%)")

# Average performance
avg_performance = employees['Performance_Score'].mean()
print(f"Average Performance Score: {avg_performance:.1f}")

# Gender diversity
gender_pct = (employees['Gender'].value_counts() / len(employees) * 100)
print(f"Gender Diversity: {gender_pct['Female']:.1f}% Female, {gender_pct['Male']:.1f}% Male")

print("\nRecommendations:")
print("1. Investigate high-attrition departments for root causes.")
print("2. Implement retention programs for high-risk age groups.")
print("3. Review compensation for departments with high turnover.")
print("4. Improve career development for junior employees.")
print("5. Focus on diversity and inclusion initiatives.")

# 6. Save results
employees.to_csv('hr_analytics_data.csv', index=False)
dept_stats.to_csv('department_metrics.csv')
print("\nData saved to 'hr_analytics_data.csv' and 'department_metrics.csv'")
```

---

### Hands-on Coding Exercises

**Exercise 12.3** – HR analytics:
```python
# 1. Load/Generate HR data.
# 2. Calculate attrition by department, age group, job level.
# 3. Analyse salary distribution.
# 4. Measure average tenure.
# 5. Create visualisations.
# 6. Generate insights and recommendations.
```

---

### Mini Quiz

1. What is attrition rate?
2. How do you calculate average tenure?
3. What are the key drivers of attrition?
4. Why is performance score important?
5. How can HR analytics improve retention?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Ignoring exit interviews | Use exit interview data for insights |
| Not tracking employee engagement | Include engagement survey data |
| Focusing only on quantitative data | Include qualitative feedback |
| Not acting on insights | Implement changes based on data |

---

### Interview Questions

1. **What metrics would you track in an HR dashboard?**  
   *Answer*: Attrition rate, headcount by department, average tenure, diversity metrics, hiring metrics, and performance scores.

2. **How do you identify high-turnover departments?**  
   *Answer*: By calculating attrition rates per department and comparing to benchmarks.

3. **What actions would you take to reduce attrition?**  
   *Answer*: Investigate root causes, improve compensation, enhance career development, and implement employee engagement programmes.

---

### Assignment and Mini Project

**Project 12.3 – HR Analytics Dashboard**:
```python
# Build a complete HR analytics dashboard that:
# 1. Loads HR data.
# 2. Calculates key metrics.
# 3. Analyses attrition by department, age group, job level.
# 4. Creates visualisations.
# 5. Generates insights and recommendations.
# 6. Exports the results.
```

---

## Project 12.4 – Financial Data Analysis

### Concept Explanation

**Financial Data Analysis** involves analysing financial statements, market data, and company performance. It helps investors, analysts, and executives make informed decisions.

**Key metrics**:
- **Revenue**: Top-line growth.
- **Profit**: Net income, operating profit.
- **Margins**: Gross margin, operating margin, net margin.
- **Ratios**: PE ratio, ROE, ROA, current ratio, debt-to-equity.
- **Growth**: Revenue growth, earnings growth.
- **Valuation**: Market cap, enterprise value.

**Data sources**:
- Financial statements (income statement, balance sheet, cash flow).
- Stock price data.
- Economic indicators.

---

### Importance and Real-World Use Cases

- **Why it matters**: Financial analysis is crucial for investment decisions, company valuation, and strategic planning.

- **Use cases**:
  - An **investment analyst** evaluates company performance for stock recommendations.
  - A **CFO** monitors financial health and plans budgets.
  - A **financial controller** identifies cost-saving opportunities.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# 1. Generate financial data
np.random.seed(42)

# Simulate company financials over 5 years
years = range(2019, 2025)
companies = ['Company A', 'Company B', 'Company C', 'Company D']

# Create financial data
financials = []
for company in companies:
    # Base revenue with some growth
    base_revenue = np.random.randint(1000, 5000, 1)[0]
    growth_rate = np.random.uniform(0.05, 0.15, 1)[0]
    
    for year in years:
        revenue = base_revenue * (1 + growth_rate) ** (year - 2019) + np.random.randint(-100, 100)
        cogs = revenue * np.random.uniform(0.4, 0.6, 1)[0]
        operating_expenses = revenue * np.random.uniform(0.2, 0.35, 1)[0]
        operating_income = revenue - cogs - operating_expenses
        net_income = operating_income * (1 - np.random.uniform(0.2, 0.3, 1)[0])
        
        financials.append({
            'Company': company,
            'Year': year,
            'Revenue': revenue,
            'COGS': cogs,
            'Operating_Expenses': operating_expenses,
            'Operating_Income': operating_income,
            'Net_Income': net_income,
            'Assets': np.random.randint(5000, 20000, 1)[0],
            'Liabilities': np.random.randint(2000, 10000, 1)[0],
            'Equity': np.random.randint(3000, 12000, 1)[0]
        })

df = pd.DataFrame(financials)

print("Financial Data Preview:")
print(df.head())

# 2. Calculate financial metrics
print("\n" + "=" * 60)
print("FINANCIAL ANALYSIS")
print("=" * 60)

# Company summary
company_summary = df.groupby('Company').agg({
    'Revenue': ['mean', 'sum'],
    'Net_Income': ['mean', 'sum'],
    'Operating_Income': ['mean', 'sum']
}).round(2)

print("Company Summary:")
print(company_summary)

# 3. Calculate ratios
# Gross Margin
df['Gross_Margin'] = (df['Revenue'] - df['COGS']) / df['Revenue'] * 100

# Operating Margin
df['Operating_Margin'] = df['Operating_Income'] / df['Revenue'] * 100

# Net Margin
df['Net_Margin'] = df['Net_Income'] / df['Revenue'] * 100

# ROE (Return on Equity)
df['ROE'] = df['Net_Income'] / df['Equity'] * 100

# Debt-to-Equity
df['Debt_to_Equity'] = df['Liabilities'] / df['Equity']

print("\nFinancial Ratios:")
print(df[['Company', 'Year', 'Gross_Margin', 'Operating_Margin', 'Net_Margin', 'ROE', 'Debt_to_Equity']].head())

# 4. Visualisations
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
fig.suptitle('Financial Analysis Dashboard', fontsize=16, fontweight='bold')

# 1. Revenue Trend by Company
for company in df['Company'].unique():
    company_data = df[df['Company'] == company]
    axes[0, 0].plot(company_data['Year'], company_data['Revenue'], marker='o', label=company)
axes[0, 0].set_title('Revenue Trend by Company')
axes[0, 0].set_xlabel('Year')
axes[0, 0].set_ylabel('Revenue')
axes[0, 0].legend()

# 2. Profit Margins by Company
margin_data = df.groupby('Company')[['Gross_Margin', 'Operating_Margin', 'Net_Margin']].mean()
margin_data.plot(kind='bar', ax=axes[0, 1])
axes[0, 1].set_title('Average Margins by Company')
axes[0, 1].set_xlabel('Company')
axes[0, 1].set_ylabel('Margin (%)')
axes[0, 1].legend()

# 3. Revenue vs Net Income (Scatter)
for company in df['Company'].unique():
    company_data = df[df['Company'] == company]
    axes[1, 0].scatter(company_data['Revenue'], company_data['Net_Income'], label=company, s=100)
axes[1, 0].set_title('Revenue vs Net Income')
axes[1, 0].set_xlabel('Revenue')
axes[1, 0].set_ylabel('Net Income')
axes[1, 0].legend()

# 4. Financial Health Heatmap (ROE, Debt-to-Equity)
heatmap_data = df.groupby('Company')[['ROE', 'Debt_to_Equity']].mean()
sns.heatmap(heatmap_data, annot=True, cmap='RdYlGn', center=0, ax=axes[1, 1])
axes[1, 1].set_title('Financial Health: ROE & Debt-to-Equity')

plt.tight_layout()
plt.show()

# 5. Insights and Recommendations
print("\n" + "=" * 60)
print("KEY INSIGHTS AND RECOMMENDATIONS")
print("=" * 60)

# Best performing company (highest net income)
best_company = df.groupby('Company')['Net_Income'].mean().idxmax()
print(f"Best Performing Company: {best_company}")

# Highest growth company
company_growth = df.groupby('Company')['Revenue'].pct_change().mean() * 100
highest_growth = company_growth.idxmax()
print(f"Highest Growth Company: {highest_growth}")

# Most profitable company (highest net margin)
best_margin = df.groupby('Company')['Net_Margin'].mean().idxmax()
print(f"Most Profitable Company: {best_margin}")

print("\nRecommendations:")
print("1. Invest in high-growth, high-margin companies.")
print("2. Investigate companies with high debt-to-equity ratios.")
print("3. Monitor revenue and profit trends for early warning signs.")
print("4. Compare financial ratios to industry benchmarks.")

# 6. Save results
df.to_csv('financial_analysis.csv', index=False)
print("\nData saved to 'financial_analysis.csv'")
```

---

### Hands-on Coding Exercises

**Exercise 12.4** – Financial analysis:
```python
# 1. Load/Generate financial data.
# 2. Calculate key financial ratios.
# 3. Analyse revenue and profit trends.
# 4. Create visualisations.
# 5. Identify best-performing companies.
# 6. Generate recommendations.
```

---

### Mini Quiz

1. What is gross margin?
2. How do you calculate operating margin?
3. What does ROE measure?
4. What is debt-to-equity ratio?
5. Why are financial ratios important?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Ignoring industry benchmarks | Compare to industry averages |
| Focusing only on revenue | Include profitability and efficiency metrics |
| Not adjusting for seasonality | Use YoY comparisons |
| Ignoring cash flow | Include cash flow analysis |

---

### Interview Questions

1. **What financial metrics would you track for a company?**  
   *Answer*: Revenue growth, profit margins, ROE, debt-to-equity, and cash flow.

2. **How do you evaluate a company's financial health?**  
   *Answer*: By analysing profitability, liquidity, solvency, and efficiency ratios.

3. **What is the difference between gross margin and net margin?**  
   *Answer*: Gross margin is revenue minus COGS. Net margin is net income divided by revenue.

---

### Assignment and Mini Project

**Project 12.4 – Financial Dashboard**:
```python
# Build a complete financial analysis dashboard that:
# 1. Loads financial data.
# 2. Calculates key financial ratios.
# 3. Creates visualisations.
# 4. Compares companies.
# 5. Generates insights and recommendations.
# 6. Exports the results.
```

---

## Project 12.5 – Stock Market Data Analysis

### Concept Explanation

**Stock Market Data Analysis** involves analysing historical stock prices, returns, and volatility to inform investment decisions.

**Key concepts**:
- **Returns**: Daily, monthly, annual returns.
- **Volatility**: Standard deviation of returns.
- **Moving Averages**: SMA, EMA for trend analysis.
- **Risk Metrics**: Sharpe ratio, beta.
- **Technical Indicators**: RSI, MACD, Bollinger Bands.

**Data source**: Yahoo Finance (`yfinance` library).

---

### Importance and Real-World Use Cases

- **Why it matters**: Stock market analysis helps investors make informed decisions, manage risk, and optimise portfolios.

- **Use cases**:
  - A **financial analyst** analyses stock performance for investment recommendations.
  - A **portfolio manager** monitors portfolio risk.
  - A **trader** identifies technical patterns.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import yfinance as yf

# 1. Download stock data
tickers = ['AAPL', 'MSFT', 'GOOGL', 'AMZN', 'TSLA']
start_date = '2023-01-01'
end_date = '2024-12-31'

print("Downloading stock data...")
stock_data = yf.download(tickers, start=start_date, end=end_date)['Adj Close']
stock_data = stock_data.dropna()

print(f"Data shape: {stock_data.shape}")
print(stock_data.head())

# 2. Calculate returns
returns = stock_data.pct_change().dropna()
print("\n" + "=" * 60)
print("STOCK PERFORMANCE ANALYSIS")
print("=" * 60)

# Summary statistics
summary_stats = returns.describe()
print("Return Summary Statistics:")
print(summary_stats)

# 3. Calculate metrics
annual_returns = returns.mean() * 252 * 100
annual_volatility = returns.std() * np.sqrt(252) * 100
sharpe_ratio = annual_returns / annual_volatility

metrics_df = pd.DataFrame({
    'Annual Return (%)': annual_returns,
    'Annual Volatility (%)': annual_volatility,
    'Sharpe Ratio': sharpe_ratio
}).sort_values('Sharpe Ratio', ascending=False)

print("\nPerformance Metrics:")
print(metrics_df)

# 4. Visualisations
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
fig.suptitle('Stock Market Analysis Dashboard', fontsize=16, fontweight='bold')

# 1. Stock Price Trends
stock_data.plot(ax=axes[0, 0])
axes[0, 0].set_title('Stock Price Trends')
axes[0, 0].set_xlabel('Date')
axes[0, 0].set_ylabel('Price ($)')
axes[0, 0].legend(loc='upper left')

# 2. Cumulative Returns
cumulative_returns = (1 + returns).cumprod() - 1
cumulative_returns.plot(ax=axes[0, 1])
axes[0, 1].set_title('Cumulative Returns')
axes[0, 1].set_xlabel('Date')
axes[0, 1].set_ylabel('Cumulative Return')
axes[0, 1].legend(loc='upper left')

# 3. Risk-Return Scatter
axes[1, 0].scatter(annual_volatility, annual_returns, s=100)
for i, ticker in enumerate(tickers):
    axes[1, 0].annotate(ticker, (annual_volatility.iloc[i], annual_returns.iloc[i]))
axes[1, 0].set_title('Risk-Return Trade-off')
axes[1, 0].set_xlabel('Annual Volatility (%)')
axes[1, 0].set_ylabel('Annual Return (%)')
axes[1, 0].grid(True, alpha=0.3)

# 4. Correlation Heatmap
correlation = returns.corr()
sns.heatmap(correlation, annot=True, cmap='coolwarm', center=0, ax=axes[1, 1])
axes[1, 1].set_title('Stock Correlation Matrix')

plt.tight_layout()
plt.show()

# 5. Moving Averages Example (for a single stock)
ticker = 'AAPL'
data = stock_data[ticker]

# Calculate SMAs
sma_20 = data.rolling(20).mean()
sma_50 = data.rolling(50).mean()

plt.figure(figsize=(12, 6))
plt.plot(data.index, data, label=f'{ticker} Price', linewidth=2)
plt.plot(data.index, sma_20, label='SMA 20', linestyle='--')
plt.plot(data.index, sma_50, label='SMA 50', linestyle='--')
plt.title(f'{ticker} Price with Moving Averages')
plt.xlabel('Date')
plt.ylabel('Price ($)')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()

# 6. Insights and Recommendations
print("\n" + "=" * 60)
print("KEY INSIGHTS AND RECOMMENDATIONS")
print("=" * 60)

best_ticker = metrics_df['Sharpe Ratio'].idxmax()
print(f"Best Risk-Adjusted Return: {best_ticker} (Sharpe: {metrics_df.loc[best_ticker, 'Sharpe Ratio']:.2f})")

highest_return_ticker = metrics_df['Annual Return (%)'].idxmax()
print(f"Highest Return: {highest_return_ticker} ({metrics_df.loc[highest_return_ticker, 'Annual Return (%)']:.1f}%)")

lowest_volatility_ticker = metrics_df['Annual Volatility (%)'].idxmin()
print(f"Lowest Volatility: {lowest_volatility_ticker} ({metrics_df.loc[lowest_volatility_ticker, 'Annual Volatility (%)']:.1f}%)")

print("\nRecommendations:")
print("1. Consider stocks with high Sharpe ratios for better risk-adjusted returns.")
print("2. Diversify across stocks with low correlation.")
print("3. Use moving averages to identify trends.")
print("4. Monitor volatility for risk management.")

# 7. Save results
metrics_df.to_csv('stock_metrics.csv')
print("\nData saved to 'stock_metrics.csv'")
```

---

### Hands-on Coding Exercises

**Exercise 12.5** – Stock analysis:
```python
# 1. Download stock data for 5 companies.
# 2. Calculate daily returns.
# 3. Calculate annual returns and volatility.
# 4. Create visualisations.
# 5. Calculate Sharpe ratios.
# 6. Identify the best-performing stock.
```

---

### Mini Quiz

1. What is the Sharpe ratio?
2. How do you calculate annual returns from daily returns?
3. What is volatility?
4. What is the purpose of moving averages?
5. Why is correlation important in portfolio management?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Using only price data | Include volume and fundamental data |
| Ignoring transaction costs | Account for costs in returns |
| Not diversifying | Use correlation analysis for diversification |
| Over-relying on historical data | Combine with fundamental analysis |

---

### Interview Questions

1. **How do you evaluate a stock's performance?**  
   *Answer*: By analysing returns, volatility, Sharpe ratio, and comparing to benchmarks.

2. **What is the Sharpe ratio and why is it important?**  
   *Answer*: The Sharpe ratio measures risk-adjusted returns. It helps compare investments with different risk levels.

3. **How do you build a diversified portfolio?**  
   *Answer*: By selecting assets with low correlation to reduce overall portfolio risk.

---

### Assignment and Mini Project

**Project 12.5 – Stock Analysis Dashboard**:
```python
# Build a complete stock analysis dashboard that:
# 1. Downloads stock data.
# 2. Calculates returns, volatility, Sharpe ratio.
# 3. Creates visualisations.
# 4. Identifies best-performing stocks.
# 5. Generates recommendations.
# 6. Exports the results.
```

---

## Project 12.6 – COVID-19 Data Analysis

### Concept Explanation

**COVID-19 Data Analysis** involves analysing pandemic trends, case counts, deaths, and vaccination rates to understand the spread and impact of the virus.

**Key metrics**:
- **Cases**: Daily new cases, cumulative cases.
- **Deaths**: Daily deaths, cumulative deaths.
- **Recovery**: Recovery rates.
- **Vaccination**: Doses administered, vaccination rates.
- **Growth Rates**: Reproduction number (R0), case growth rates.

**Data sources**:
- Johns Hopkins University (JHU) COVID-19 data.
- Our World in Data.
- WHO COVID-19 dashboard.

---

### Importance and Real-World Use Cases

- **Why it matters**: COVID-19 data analysis helps public health officials, governments, and researchers understand the pandemic and make informed decisions.

- **Use cases**:
  - A **public health official** monitors case trends and adjusts restrictions.
  - A **researcher** studies the effectiveness of interventions.
  - A **journalist** reports on pandemic developments.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import requests
from datetime import datetime, timedelta

# 1. Download COVID-19 data (Our World in Data)
print("Downloading COVID-19 data...")
url = "https://raw.githubusercontent.com/owid/covid-19-data/master/public/data/owid-covid-data.csv"
df = pd.read_csv(url)

print(f"Data shape: {df.shape}")
print(df.head())

# Filter for recent data and key countries
countries = ['United States', 'India', 'Brazil', 'United Kingdom', 'Germany', 'South Africa']
df_filtered = df[df['location'].isin(countries)]

# Select key columns
cols = ['location', 'date', 'total_cases', 'new_cases', 'total_deaths', 'new_deaths', 
        'people_vaccinated', 'people_fully_vaccinated', 'population']
df_filtered = df_filtered[cols]

# Convert date to datetime
df_filtered['date'] = pd.to_datetime(df_filtered['date'])

print("\n" + "=" * 60)
print("COVID-19 DATA ANALYSIS")
print("=" * 60)

# Latest statistics
latest_date = df_filtered['date'].max()
latest_data = df_filtered[df_filtered['date'] == latest_date]

print(f"Latest Date: {latest_date}")
print("\nLatest Statistics:")
print(latest_data[['location', 'total_cases', 'total_deaths', 'people_fully_vaccinated']].head())

# 2. Calculate metrics
# Vaccination rate
latest_data['Vaccination_Rate'] = (latest_data['people_fully_vaccinated'] / latest_data['population']) * 100

# Case fatality rate
latest_data['Case_Fatality_Rate'] = (latest_data['total_deaths'] / latest_data['total_cases']) * 100

print("\nVaccination and Fatality Rates:")
print(latest_data[['location', 'Vaccination_Rate', 'Case_Fatality_Rate']].head())

# 3. Visualisations
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
fig.suptitle('COVID-19 Analysis Dashboard', fontsize=16, fontweight='bold')

# 1. Total Cases by Country
latest_data_sorted = latest_data.sort_values('total_cases', ascending=False).head(10)
sns.barplot(data=latest_data_sorted, x='location', y='total_cases', ax=axes[0, 0])
axes[0, 0].set_title('Total Cases by Country')
axes[0, 0].set_xlabel('Country')
axes[0, 0].set_ylabel('Total Cases')
axes[0, 0].tick_params(axis='x', rotation=45)

# 2. Vaccination Rate by Country
latest_data_sorted_vax = latest_data.sort_values('Vaccination_Rate', ascending=False).head(10)
sns.barplot(data=latest_data_sorted_vax, x='location', y='Vaccination_Rate', ax=axes[0, 1])
axes[0, 1].set_title('Vaccination Rate by Country')
axes[0, 1].set_xlabel('Country')
axes[0, 1].set_ylabel('Vaccination Rate (%)')
axes[0, 1].tick_params(axis='x', rotation=45)

# 3. Daily New Cases (United States)
us_data = df_filtered[df_filtered['location'] == 'United States'].tail(90)
axes[1, 0].plot(us_data['date'], us_data['new_cases'], color='blue', linewidth=2)
axes[1, 0].set_title('US Daily New Cases (Last 90 Days)')
axes[1, 0].set_xlabel('Date')
axes[1, 0].set_ylabel('New Cases')
axes[1, 0].tick_params(axis='x', rotation=45)

# 4. Total Cases vs Deaths
sns.scatterplot(data=latest_data, x='total_cases', y='total_deaths', size='population', 
                sizes=(50, 500), alpha=0.7, ax=axes[1, 1])
for _, row in latest_data.iterrows():
    axes[1, 1].annotate(row['location'], (row['total_cases'], row['total_deaths']), fontsize=8)
axes[1, 1].set_title('Total Cases vs Total Deaths')
axes[1, 1].set_xlabel('Total Cases')
axes[1, 1].set_ylabel('Total Deaths')

plt.tight_layout()
plt.show()

# 4. Time Series Analysis for a country
country = 'India'
country_data = df_filtered[df_filtered['location'] == country].tail(200)

fig, axes = plt.subplots(2, 1, figsize=(12, 8))

# Daily cases
axes[0].plot(country_data['date'], country_data['new_cases'], color='red', linewidth=2)
axes[0].set_title(f'Daily New Cases - {country}')
axes[0].set_xlabel('Date')
axes[0].set_ylabel('New Cases')
axes[0].grid(True, alpha=0.3)

# Daily deaths
axes[1].plot(country_data['date'], country_data['new_deaths'], color='darkred', linewidth=2)
axes[1].set_title(f'Daily New Deaths - {country}')
axes[1].set_xlabel('Date')
axes[1].set_ylabel('New Deaths')
axes[1].grid(True, alpha=0.3)

plt.tight_layout()
plt.show()

# 5. Insights and Recommendations
print("\n" + "=" * 60)
print("KEY INSIGHTS AND RECOMMENDATIONS")
print("=" * 60)

# Highest cases
highest_cases = latest_data.loc[latest_data['total_cases'].idxmax(), 'location']
print(f"Highest Total Cases: {highest_cases}")

# Highest vaccination rate
highest_vax = latest_data.loc[latest_data['Vaccination_Rate'].idxmax(), 'location']
print(f"Highest Vaccination Rate: {highest_vax} ({latest_data['Vaccination_Rate'].max():.1f}%)")

# Lowest vaccination rate
lowest_vax = latest_data.loc[latest_data['Vaccination_Rate'].idxmin(), 'location']
print(f"Lowest Vaccination Rate: {lowest_vax} ({latest_data['Vaccination_Rate'].min():.1f}%)")

print("\nRecommendations:")
print("1. Continue vaccination campaigns to achieve herd immunity.")
print("2. Monitor countries with high case loads for new variants.")
print("3. Share data and best practices between countries.")
print("4. Focus public health messaging on high-risk populations.")

# 6. Save results
latest_data.to_csv('covid_analysis.csv', index=False)
print("\nData saved to 'covid_analysis.csv'")
```

---

### Hands-on Coding Exercises

**Exercise 12.6** – COVID-19 analysis:
```python
# 1. Download COVID-19 data.
# 2. Analyse total cases, deaths, and vaccination rates.
# 3. Create visualisations.
# 4. Identify trends and patterns.
# 5. Generate recommendations.
```

---

### Mini Quiz

1. What is the case fatality rate?
2. What is the vaccination rate?
3. Why is daily new cases an important metric?
4. What does the reproduction number (R0) measure?
5. How can data analysis help pandemic response?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Ignoring population size | Use per capita metrics |
| Not adjusting for reporting delays | Account for data lags |
| Using only global data | Analyse regional differences |
| Not comparing to benchmarks | Compare to global averages |

---

### Interview Questions

1. **What metrics would you track in a COVID-19 dashboard?**  
   *Answer*: Total cases, daily new cases, total deaths, vaccination rates, and case fatality rates.

2. **How do you compare COVID-19 impact across countries?**  
   *Answer*: Use per capita metrics (cases per million, deaths per million) and vaccination rates.

3. **What insights can data analysis provide for pandemic response?**  
   *Answer*: Identify hotspots, measure intervention effectiveness, and guide resource allocation.

---

### Assignment and Mini Project

**Project 12.6 – COVID-19 Dashboard**:
```python
# Build a complete COVID-19 dashboard that:
# 1. Downloads COVID-19 data.
# 2. Analyses cases, deaths, and vaccination rates.
# 3. Creates visualisations.
# 4. Identifies trends and insights.
# 5. Generates recommendations.
# 6. Exports the results.
```

---

## Project 12.7 – IPL Data Analysis

### Concept Explanation

**IPL (Indian Premier League)** data analysis involves analysing cricket match data to understand player performance, team strategies, and match outcomes.

**Key metrics**:
- **Team Performance**: Wins, losses, points, net run rate.
- **Batsman Performance**: Runs, strike rate, centuries, averages.
- **Bowler Performance**: Wickets, economy rate, strike rate.
- **Match Patterns**: Toss decisions, home/away performance, chasing trends.

**Data sources**:
- Kaggle IPL datasets.
- ESPN Cricinfo.

---

### Importance and Real-World Use Cases

- **Why it matters**: Sports analytics is a growing field. IPL data analysis helps teams, coaches, and broadcasters understand performance.

- **Use cases**:
  - A **team analyst** identifies strengths and weaknesses.
  - A **fantasy player** makes informed selections.
  - A **broadcaster** provides data-driven commentary.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import requests
from io import StringIO

# 1. Load IPL data (if available)
# Note: For this demonstration, we'll generate simulated IPL data

# Sample dataset creation
np.random.seed(42)

teams = ['Mumbai Indians', 'Chennai Super Kings', 'Royal Challengers Bangalore', 
         'Kolkata Knight Riders', 'Sunrisers Hyderabad', 'Delhi Capitals', 
         'Rajasthan Royals', 'Punjab Kings']

matches = []
for i in range(100):
    team1 = np.random.choice(teams)
    team2 = np.random.choice([t for t in teams if t != team1])
    winner = np.random.choice([team1, team2])
    margin = np.random.randint(1, 50)
    venue = np.random.choice(['Wankhede', 'Eden Gardens', 'Chinnaswamy', 'Narendra Modi', 'Chepauk'])
    
    matches.append({
        'Match_ID': i + 1,
        'Team1': team1,
        'Team2': team2,
        'Winner': winner,
        'Margin': margin,
        'Venue': venue,
        'Toss_Winner': np.random.choice([team1, team2]),
        'Toss_Decision': np.random.choice(['bat', 'bowl'])
    })

df_matches = pd.DataFrame(matches)

# Player performance data
players = ['Virat Kohli', 'MS Dhoni', 'Rohit Sharma', 'Rashid Khan', 'Jasprit Bumrah',
           'Suryakumar Yadav', 'KL Rahul', 'Jos Buttler', 'Andre Russell', 'Dinesh Karthik']

player_stats = []
for player in players:
    for i in range(20):
        player_stats.append({
            'Player': player,
            'Match_ID': np.random.randint(1, 101),
            'Runs': np.random.randint(0, 120),
            'Balls_Faced': np.random.randint(0, 80),
            'Wickets': np.random.randint(0, 5),
            'Overs_Bowled': np.random.randint(0, 4),
            'Runs_Conceded': np.random.randint(0, 50)
        })

df_player_stats = pd.DataFrame(player_stats)

print("IPL Data Preview:")
print(df_matches.head())

# 2. Team Analysis
print("\n" + "=" * 60)
print("IPL TEAM ANALYSIS")
print("=" * 60)

team_wins = df_matches['Winner'].value_counts()
team_matches = pd.concat([df_matches['Team1'], df_matches['Team2']]).value_counts()
team_win_rate = (team_wins / team_matches * 100).sort_values(ascending=False)

print("Team Win Rates:")
print(team_win_rate)

# 3. Player Analysis
print("\n" + "=" * 60)
print("IPL PLAYER ANALYSIS")
print("=" * 60)

# Batsman stats
batsman_stats = df_player_stats.groupby('Player').agg({
    'Runs': 'sum',
    'Balls_Faced': 'sum',
    'Match_ID': 'count'
}).rename(columns={'Match_ID': 'Innings'})

batsman_stats['Average'] = batsman_stats['Runs'] / batsman_stats['Innings']
batsman_stats['Strike_Rate'] = (batsman_stats['Runs'] / batsman_stats['Balls_Faced']) * 100
batsman_stats = batsman_stats.sort_values('Runs', ascending=False)

print("Top Batsmen:")
print(batsman_stats.head())

# Bowler stats
bowler_stats = df_player_stats.groupby('Player').agg({
    'Wickets': 'sum',
    'Overs_Bowled': 'sum',
    'Runs_Conceded': 'sum',
    'Match_ID': 'count'
}).rename(columns={'Match_ID': 'Matches'})

bowler_stats['Economy_Rate'] = bowler_stats['Runs_Conceded'] / bowler_stats['Overs_Bowled']
bowler_stats = bowler_stats.sort_values('Wickets', ascending=False)

print("\nTop Bowlers:")
print(bowler_stats.head())

# 4. Visualisations
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
fig.suptitle('IPL Analysis Dashboard', fontsize=16, fontweight='bold')

# 1. Team Win Rates
team_win_rate.sort_values().plot(kind='barh', ax=axes[0, 0], color='skyblue')
axes[0, 0].set_title('Team Win Rates')
axes[0, 0].set_xlabel('Win Rate (%)')
axes[0, 0].set_ylabel('Team')

# 2. Top Batsmen
batsman_stats.head(10)['Runs'].sort_values().plot(kind='barh', ax=axes[0, 1], color='lightgreen')
axes[0, 1].set_title('Top 10 Batsmen (Runs)')
axes[0, 1].set_xlabel('Runs')
axes[0, 1].set_ylabel('Player')

# 3. Top Bowlers
bowler_stats.head(10)['Wickets'].sort_values().plot(kind='barh', ax=axes[1, 0], color='coral')
axes[1, 0].set_title('Top 10 Bowlers (Wickets)')
axes[1, 0].set_xlabel('Wickets')
axes[1, 0].set_ylabel('Player')

# 4. Venue Analysis
venue_matches = df_matches['Venue'].value_counts()
venue_matches.plot(kind='bar', ax=axes[1, 1], color='purple', alpha=0.7)
axes[1, 1].set_title('Matches by Venue')
axes[1, 1].set_xlabel('Venue')
axes[1, 1].set_ylabel('Number of Matches')
axes[1, 1].tick_params(axis='x', rotation=45)

plt.tight_layout()
plt.show()

# 5. Insights and Recommendations
print("\n" + "=" * 60)
print("KEY INSIGHTS AND RECOMMENDATIONS")
print("=" * 60)

best_team = team_win_rate.idxmax()
best_team_rate = team_win_rate.max()
print(f"Best Team: {best_team} ({best_team_rate:.1f}% win rate)")

best_batsman = batsman_stats['Runs'].idxmax()
best_batsman_runs = batsman_stats['Runs'].max()
print(f"Best Batsman: {best_batsman} ({best_batsman_runs} runs)")

best_bowler = bowler_stats['Wickets'].idxmax()
best_bowler_wickets = bowler_stats['Wickets'].max()
print(f"Best Bowler: {best_bowler} ({best_bowler_wickets} wickets)")

print("\nRecommendations:")
print("1. Teams should analyse winning patterns and strategies.")
print("2. Batsmen should focus on improving strike rate.")
print("3. Bowlers should work on maintaining low economy rates.")
print("4. Teams should consider venue-specific strategies.")

# 6. Save results
df_matches.to_csv('ipl_matches.csv', index=False)
df_player_stats.to_csv('ipl_player_stats.csv', index=False)
print("\nData saved to 'ipl_matches.csv' and 'ipl_player_stats.csv'")
```

---

### Hands-on Coding Exercises

**Exercise 12.7** – IPL analysis:
```python
# 1. Load/Generate IPL data.
# 2. Analyse team performance.
# 3. Analyse player performance.
# 4. Create visualisations.
# 5. Generate insights.
```

---

### Mini Quiz

1. What is the win rate in cricket?
2. What is strike rate in batting?
3. What is economy rate in bowling?
4. Why is venue analysis important?
5. What metrics are used to evaluate batsmen?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Ignoring sample size | Consider number of matches played |
| Not adjusting for opposition strength | Include quality of opposition |
| Using only basic statistics | Include advanced metrics (e.g., impact score) |
| Not considering match context | Include match importance (playoffs, final) |

---

### Interview Questions

1. **How would you analyse a cricket team's performance?**  
   *Answer*: By analysing win rates, batting averages, bowling economy, and performance in different conditions.

2. **What metrics are important for evaluating batsmen?**  
   *Answer*: Runs scored, batting average, strike rate, and centuries/half-centuries.

3. **How do you identify the most valuable player in a team?**  
   *Answer*: By using all-round performance metrics (runs + wickets) and impact on match outcomes.

---

### Assignment and Mini Project

**Project 12.7 – IPL Dashboard**:
```python
# Build a complete IPL dashboard that:
# 1. Loads/Generates IPL data.
# 2. Analyses team and player performance.
# 3. Creates visualisations.
# 4. Generates insights.
# 5. Exports the results.
```

---

## Project 12.8 – Retail Business Analysis

### Concept Explanation

**Retail Business Analysis** involves analysing retail sales, inventory, customer behaviour, and store performance to optimise operations and increase profitability.

**Key metrics**:
- **Sales**: Revenue, units sold, average transaction value.
- **Inventory**: Turnover, stock-to-sales ratio, days of inventory.
- **Customers**: Footfall, conversion rate, customer lifetime value.
- **Store Performance**: Sales per square foot, growth rate.
- **Product**: Category performance, best-sellers, slow movers.

---

### Importance and Real-World Use Cases

- **Why it matters**: Retail is a competitive industry. Data analysis helps retailers understand customers, manage inventory, and improve profitability.

- **Use cases**:
  - A **store manager** monitors daily sales and inventory levels.
  - A **merchandiser** analyses product performance.
  - A **marketing team** tracks campaign effectiveness.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# 1. Generate retail data
np.random.seed(42)

stores = ['Store A', 'Store B', 'Store C', 'Store D', 'Store E']
categories = ['Electronics', 'Clothing', 'Home Goods', 'Groceries', 'Books', 'Toys']
products = ['Product A', 'Product B', 'Product C', 'Product D', 'Product E', 'Product F',
            'Product G', 'Product H', 'Product I', 'Product J']

# Generate sales data
sales_data = []
for date in pd.date_range('2024-01-01', '2024-06-30', freq='D'):
    for store in stores:
        for product in products:
            if np.random.random() > 0.3:  # 70% chance of a sale
                sales_data.append({
                    'Date': date,
                    'Store': store,
                    'Product': product,
                    'Category': np.random.choice(categories),
                    'Units_Sold': np.random.randint(1, 20),
                    'Unit_Price': np.random.randint(10, 200),
                    'Discount': np.random.randint(0, 30)
                })

df = pd.DataFrame(sales_data)
df['Revenue'] = df['Units_Sold'] * df['Unit_Price'] * (1 - df['Discount'] / 100)

print("Retail Data Preview:")
print(df.head())

# 2. Sales Analysis
print("\n" + "=" * 60)
print("RETAIL SALES ANALYSIS")
print("=" * 60)

total_revenue = df['Revenue'].sum()
avg_transaction = df['Revenue'].mean()
total_units = df['Units_Sold'].sum()

print(f"Total Revenue: ${total_revenue:,.2f}")
print(f"Average Transaction Value: ${avg_transaction:.2f}")
print(f"Total Units Sold: {total_units:,}")

# Store performance
store_performance = df.groupby('Store').agg({
    'Revenue': 'sum',
    'Units_Sold': 'sum',
    'Revenue': 'count'
}).rename(columns={'Revenue': 'Transactions'})
store_performance['Avg_Transaction'] = store_performance['Revenue'] / store_performance['Transactions']
print("\nStore Performance:")
print(store_performance)

# Category performance
category_performance = df.groupby('Category').agg({
    'Revenue': 'sum',
    'Units_Sold': 'sum'
}).sort_values('Revenue', ascending=False)
print("\nCategory Performance:")
print(category_performance)

# 3. Visualisations
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
fig.suptitle('Retail Analytics Dashboard', fontsize=16, fontweight='bold')

# 1. Revenue by Store
store_performance['Revenue'].sort_values().plot(kind='barh', ax=axes[0, 0], color='skyblue')
axes[0, 0].set_title('Revenue by Store')
axes[0, 0].set_xlabel('Revenue ($)')
axes[0, 0].set_ylabel('Store')

# 2. Revenue by Category
category_performance['Revenue'].sort_values().plot(kind='barh', ax=axes[0, 1], color='lightgreen')
axes[0, 1].set_title('Revenue by Category')
axes[0, 1].set_xlabel('Revenue ($)')
axes[0, 1].set_ylabel('Category')

# 3. Sales Trend
daily_sales = df.groupby('Date')['Revenue'].sum()
daily_sales.plot(ax=axes[1, 0], color='darkblue', linewidth=2)
axes[1, 0].set_title('Daily Sales Trend')
axes[1, 0].set_xlabel('Date')
axes[1, 0].set_ylabel('Revenue ($)')
axes[1, 0].grid(True, alpha=0.3)

# 4. Product Performance (Top 10)
product_performance = df.groupby('Product')['Revenue'].sum().sort_values(ascending=False).head(10)
product_performance.plot(kind='bar', ax=axes[1, 1], color='coral')
axes[1, 1].set_title('Top 10 Products by Revenue')
axes[1, 1].set_xlabel('Product')
axes[1, 1].set_ylabel('Revenue ($)')
axes[1, 1].tick_params(axis='x', rotation=45)

plt.tight_layout()
plt.show()

# 4. Insights and Recommendations
print("\n" + "=" * 60)
print("KEY INSIGHTS AND RECOMMENDATIONS")
print("=" * 60)

# Best store
best_store = store_performance['Revenue'].idxmax()
best_store_revenue = store_performance.loc[best_store, 'Revenue']
print(f"Best Performing Store: {best_store} (${best_store_revenue:,.2f})")

# Best category
best_category = category_performance['Revenue'].idxmax()
best_category_revenue = category_performance.loc[best_category, 'Revenue']
print(f"Best Performing Category: {best_category} (${best_category_revenue:,.2f})")

# Best product
best_product = product_performance.index[0]
best_product_revenue = product_performance.iloc[0]
print(f"Best Product: {best_product} (${best_product_revenue:,.2f})")

print("\nRecommendations:")
print("1. Focus marketing efforts on top-performing categories.")
print("2. Investigate underperforming stores for improvement opportunities.")
print("3. Analyse product trends to optimize inventory.")
print("4. Consider promotions for slow-moving products.")
print("5. Use customer data to personalise shopping experiences.")

# 5. Save results
df.to_csv('retail_sales_data.csv', index=False)
store_performance.to_csv('store_performance.csv')
category_performance.to_csv('category_performance.csv')
print("\nData saved to CSV files.")
```

---

### Hands-on Coding Exercises

**Exercise 12.8** – Retail analysis:
```python
# 1. Load/Generate retail data.
# 2. Analyse sales by store, category, and product.
# 3. Identify top-performing categories and products.
# 4. Create visualisations.
# 5. Generate recommendations.
```

---

### Mini Quiz

1. What is the average transaction value?
2. What metrics are used to evaluate store performance?
3. Why is product performance analysis important?
4. How do you calculate sales growth?
5. What is inventory turnover?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Ignoring seasonal patterns | Analyse seasonality for inventory planning |
| Not segmenting customers | Use customer segmentation for targeted marketing |
| Focusing only on sales | Include profit margins and costs |
| Not benchmarking against competitors | Use industry benchmarks |

---

### Interview Questions

1. **What metrics would you track in a retail dashboard?**  
   *Answer*: Sales revenue, average transaction value, units sold, store performance, and product performance.

2. **How do you identify slow-moving products?**  
   *Answer*: By analysing sales velocity and inventory turnover rates.

3. **How can data analytics improve retail operations?**  
   *Answer*: By optimising inventory, personalising marketing, and improving store performance.

---

### Assignment and Mini Project

**Project 12.8 – Retail Dashboard**:
```python
# Build a complete retail dashboard that:
# 1. Loads/Generates retail data.
# 2. Analyses sales by store, category, and product.
# 3. Creates visualisations.
# 4. Generates insights and recommendations.
# 5. Exports the results.
```

---

## Project 12.9 – E-commerce Sales Dashboard

### Concept Explanation

**E-commerce Sales Dashboard** helps online retailers understand customer behaviour, sales performance, and marketing effectiveness.

**Key metrics**:
- **Sales**: Revenue, orders, average order value.
- **Customers**: New vs returning customers, customer acquisition cost, lifetime value.
- **Products**: Top-selling products, product categories.
- **Marketing**: Channel performance, conversion rate, ROAS.
- **Behaviour**: Bounce rate, cart abandonment, session duration.

---

### Importance and Real-World Use Cases

- **Why it matters**: E-commerce generates vast amounts of data. Analysis helps optimise marketing, improve customer experience, and increase sales.

- **Use cases**:
  - A **marketing manager** optimises ad spend.
  - A **UX designer** improves website conversion.
  - A **product manager** identifies best-sellers.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# 1. Generate e-commerce data
np.random.seed(42)

# Customer data
n_customers = 500
customers = pd.DataFrame({
    'Customer_ID': range(1, n_customers + 1),
    'Segment': np.random.choice(['New', 'Returning', 'VIP'], n_customers),
    'Signup_Date': pd.date_range('2024-01-01', '2024-06-01', periods=n_customers)
})

# Orders data
n_orders = 2000
orders = pd.DataFrame({
    'Order_ID': range(1, n_orders + 1),
    'Customer_ID': np.random.choice(customers['Customer_ID'], n_orders),
    'Order_Date': pd.date_range('2024-01-01', '2024-12-31', periods=n_orders),
    'Total_Amount': np.random.randint(20, 500, n_orders),
    'Payment_Method': np.random.choice(['Credit Card', 'PayPal', 'Bank Transfer', 'Cash on Delivery'], n_orders),
    'Order_Status': np.random.choice(['Completed', 'Pending', 'Cancelled'], n_orders, p=[0.7, 0.2, 0.1])
})

# Products in orders
n_items = n_orders * 3
order_items = []
for i in range(n_orders):
    n_products = np.random.randint(1, 5)
    for j in range(n_products):
        order_items.append({
            'Order_ID': i + 1,
            'Product': np.random.choice(['Product A', 'Product B', 'Product C', 'Product D', 'Product E']),
            'Quantity': np.random.randint(1, 5),
            'Price': np.random.randint(10, 100)
        })
order_items = pd.DataFrame(order_items)
order_items['Line_Total'] = order_items['Quantity'] * order_items['Price']

# Calculate order totals
order_totals = order_items.groupby('Order_ID')['Line_Total'].sum().reset_index()
order_totals.columns = ['Order_ID', 'Calculated_Total']

print("E-commerce Data Preview:")
print(orders.head())
print("\nOrder Items Preview:")
print(order_items.head())

# 2. Sales Analysis
print("\n" + "=" * 60)
print("E-COMMERCE SALES ANALYSIS")
print("=" * 60)

total_revenue = orders['Total_Amount'].sum()
avg_order_value = orders['Total_Amount'].mean()
total_orders = len(orders)

print(f"Total Revenue: ${total_revenue:,.2f}")
print(f"Average Order Value: ${avg_order_value:.2f}")
print(f"Total Orders: {total_orders:,}")

# Customer analysis
customer_orders = orders.groupby('Customer_ID').size().reset_index(name='Order_Count')
customer_spend = orders.groupby('Customer_ID')['Total_Amount'].sum().reset_index(name='Total_Spend')
customer_metrics = customers.merge(customer_orders, on='Customer_ID', how='left').merge(customer_spend, on='Customer_ID', how='left')
customer_metrics.fillna(0, inplace=True)

avg_orders_per_customer = customer_metrics['Order_Count'].mean()
avg_spend_per_customer = customer_metrics['Total_Spend'].mean()

print(f"\nAverage Orders per Customer: {avg_orders_per_customer:.2f}")
print(f"Average Spend per Customer: ${avg_spend_per_customer:.2f}")

# Product analysis
product_sales = order_items.groupby('Product').agg({
    'Quantity': 'sum',
    'Line_Total': 'sum'
}).sort_values('Line_Total', ascending=False)

print("\nProduct Sales:")
print(product_sales)

# 3. Visualisations
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
fig.suptitle('E-commerce Dashboard', fontsize=16, fontweight='bold')

# 1. Revenue by Payment Method
payment_revenue = orders.groupby('Payment_Method')['Total_Amount'].sum().sort_values()
payment_revenue.plot(kind='barh', ax=axes[0, 0], color='skyblue')
axes[0, 0].set_title('Revenue by Payment Method')
axes[0, 0].set_xlabel('Revenue ($)')
axes[0, 0].set_ylabel('Payment Method')

# 2. Product Performance
product_sales['Line_Total'].sort_values().plot(kind='barh', ax=axes[0, 1], color='lightgreen')
axes[0, 1].set_title('Revenue by Product')
axes[0, 1].set_xlabel('Revenue ($)')
axes[0, 1].set_ylabel('Product')

# 3. Order Status Distribution
order_status = orders['Order_Status'].value_counts()
order_status.plot(kind='pie', autopct='%1.1f%%', ax=axes[1, 0])
axes[1, 0].set_title('Order Status Distribution')
axes[1, 0].set_ylabel('')

# 4. Customer Segment Analysis
segment_metrics = customers.merge(customer_orders, on='Customer_ID', how='left').merge(customer_spend, on='Customer_ID', how='left')
segment_metrics.fillna(0, inplace=True)
segment_analysis = segment_metrics.groupby('Segment').agg({
    'Customer_ID': 'count',
    'Order_Count': 'mean',
    'Total_Spend': 'mean'
}).rename(columns={'Customer_ID': 'Count'})

sns.heatmap(segment_analysis, annot=True, cmap='YlOrRd', ax=axes[1, 1])
axes[1, 1].set_title('Customer Segment Metrics')

plt.tight_layout()
plt.show()

# 4. Insights and Recommendations
print("\n" + "=" * 60)
print("KEY INSIGHTS AND RECOMMENDATIONS")
print("=" * 60)

# Top product
top_product = product_sales['Line_Total'].idxmax()
top_product_revenue = product_sales.loc[top_product, 'Line_Total']
print(f"Top Product: {top_product} (${top_product_revenue:,.2f})")

# Payment method popularity
top_payment = payment_revenue.idxmax()
print(f"Most Popular Payment Method: {top_payment}")

# Order completion rate
completion_rate = (orders['Order_Status'] == 'Completed').mean() * 100
print(f"Order Completion Rate: {completion_rate:.1f}%")

print("\nRecommendations:")
print("1. Focus on top-selling products for marketing.")
print("2. Investigate reasons for pending/cancelled orders.")
print("3. Improve customer retention for VIP segment.")
print("4. Optimise checkout process for popular payment methods.")
print("5. Use customer segmentation for personalised marketing.")

# 5. Save results
orders.to_csv('ecommerce_orders.csv', index=False)
order_items.to_csv('ecommerce_order_items.csv', index=False)
print("\nData saved to CSV files.")
```

---

### Hands-on Coding Exercises

**Exercise 12.9** – E-commerce analysis:
```python
# 1. Load/Generate e-commerce data.
# 2. Analyse sales, customers, and products.
# 3. Identify top products and customer segments.
# 4. Create visualisations.
# 5. Generate recommendations.
```

---

### Mini Quiz

1. What is average order value?
2. What is customer lifetime value?
3. How do you calculate conversion rate?
4. What is a product's sales velocity?
5. Why is order status analysis important?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Ignoring customer lifetime value | Calculate and track CLV |
| Not segmenting customers | Segment for targeted marketing |
| Focusing only on revenue | Include conversion rates and margins |
| Not analysing checkout behaviour | Track cart abandonment |

---

### Interview Questions

1. **What metrics would you track in an e-commerce dashboard?**  
   *Answer*: Revenue, average order value, conversion rate, customer lifetime value, and product performance.

2. **How do you identify high-value customers?**  
   *Answer*: By analysing purchase frequency, total spend, and customer lifetime value.

3. **How can data analytics improve e-commerce sales?**  
   *Answer*: By optimising marketing spend, improving product recommendations, and personalising customer experiences.

---

### Assignment and Mini Project

**Project 12.9 – E-commerce Dashboard**:
```python
# Build a complete e-commerce dashboard that:
# 1. Loads/Generates e-commerce data.
# 2. Analyses sales, customers, products, and orders.
# 3. Creates visualisations.
# 4. Generates insights and recommendations.
# 5. Exports the results.
```

---

## Project 12.10 – Marketing Campaign Analysis

### Concept Explanation

**Marketing Campaign Analysis** helps marketers understand campaign performance, optimise spend, and improve ROI.

**Key metrics**:
- **Impressions**: Number of times an ad is shown.
- **Clicks**: Number of clicks on an ad.
- **CTR (Click-Through Rate)**: Clicks / Impressions.
- **Conversions**: Desired actions (purchases, sign-ups).
- **Conversion Rate**: Conversions / Clicks.
- **CPC (Cost Per Click)**: Cost / Clicks.
- **CPA (Cost Per Acquisition)**: Cost / Conversions.
- **ROAS (Return on Ad Spend)**: Revenue / Cost.
- **ROI**: (Revenue - Cost) / Cost.

**Channels**: Google Ads, Facebook, Email, SEO, Social Media, etc.

---

### Importance and Real-World Use Cases

- **Why it matters**: Marketing budgets are often large. Analysis helps allocate spend to the most effective channels.

- **Use cases**:
  - A **marketing manager** optimises ad spend across channels.
  - A **campaign analyst** measures campaign effectiveness.
  - A **performance marketer** improves ROI.

---

### Step-by-Step Demonstration

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# 1. Generate marketing data
np.random.seed(42)

channels = ['Google Ads', 'Facebook Ads', 'Instagram Ads', 'Email Marketing', 'SEO', 'Organic Social']
campaigns = ['Campaign A', 'Campaign B', 'Campaign C', 'Campaign D', 'Campaign E']

campaign_data = []
for campaign in campaigns:
    for channel in channels:
        impressions = np.random.randint(1000, 100000)
        clicks = int(impressions * np.random.uniform(0.01, 0.05))
        conversions = int(clicks * np.random.uniform(0.02, 0.08))
        cost = np.random.randint(1000, 50000)
        
        campaign_data.append({
            'Campaign': campaign,
            'Channel': channel,
            'Impressions': impressions,
            'Clicks': clicks,
            'Conversions': conversions,
            'Cost': cost,
            'Revenue': np.random.randint(1000, 100000)
        })

df = pd.DataFrame(campaign_data)

# Calculate metrics
df['CTR'] = (df['Clicks'] / df['Impressions']) * 100
df['Conversion_Rate'] = (df['Conversions'] / df['Clicks']) * 100
df['CPC'] = df['Cost'] / df['Clicks']
df['CPA'] = df['Cost'] / df['Conversions']
df['ROAS'] = df['Revenue'] / df['Cost']
df['ROI'] = ((df['Revenue'] - df['Cost']) / df['Cost']) * 100

print("Marketing Data Preview:")
print(df.head())

# 2. Channel Analysis
print("\n" + "=" * 60)
print("MARKETING CHANNEL ANALYSIS")
print("=" * 60)

channel_metrics = df.groupby('Channel').agg({
    'Impressions': 'sum',
    'Clicks': 'sum',
    'Conversions': 'sum',
    'Cost': 'sum',
    'Revenue': 'sum'
})

channel_metrics['CTR'] = (channel_metrics['Clicks'] / channel_metrics['Impressions']) * 100
channel_metrics['Conversion_Rate'] = (channel_metrics['Conversions'] / channel_metrics['Clicks']) * 100
channel_metrics['ROAS'] = channel_metrics['Revenue'] / channel_metrics['Cost']
channel_metrics['ROI'] = ((channel_metrics['Revenue'] - channel_metrics['Cost']) / channel_metrics['Cost']) * 100

print("Channel Performance:")
print(channel_metrics)

# 3. Campaign Analysis
print("\n" + "=" * 60)
print("CAMPAIGN ANALYSIS")
print("=" * 60)

campaign_metrics = df.groupby('Campaign').agg({
    'Impressions': 'sum',
    'Clicks': 'sum',
    'Conversions': 'sum',
    'Cost': 'sum',
    'Revenue': 'sum'
})

campaign_metrics['ROAS'] = campaign_metrics['Revenue'] / campaign_metrics['Cost']
campaign_metrics['ROI'] = ((campaign_metrics['Revenue'] - campaign_metrics['Cost']) / campaign_metrics['Cost']) * 100

print("Campaign Performance:")
print(campaign_metrics.sort_values('ROI', ascending=False))

# 4. Visualisations
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
fig.suptitle('Marketing Performance Dashboard', fontsize=16, fontweight='bold')

# 1. ROI by Channel
channel_metrics['ROI'].sort_values().plot(kind='barh', ax=axes[0, 0], color='skyblue')
axes[0, 0].set_title('ROI by Channel')
axes[0, 0].set_xlabel('ROI (%)')
axes[0, 0].set_ylabel('Channel')

# 2. ROAS by Channel
channel_metrics['ROAS'].sort_values().plot(kind='barh', ax=axes[0, 1], color='lightgreen')
axes[0, 1].set_title('ROAS by Channel')
axes[0, 1].set_xlabel('ROAS')
axes[0, 1].set_ylabel('Channel')

# 3. ROI by Campaign
campaign_metrics['ROI'].sort_values().plot(kind='bar', ax=axes[1, 0], color='coral')
axes[1, 0].set_title('ROI by Campaign')
axes[1, 0].set_xlabel('Campaign')
axes[1, 0].set_ylabel('ROI (%)')
axes[1, 0].tick_params(axis='x', rotation=45)

# 4. Spend vs Revenue Scatter
axes[1, 1].scatter(df['Cost'], df['Revenue'], alpha=0.7)
for i, row in df.iterrows():
    axes[1, 1].annotate(row['Channel'], (row['Cost'], row['Revenue']), fontsize=8)
axes[1, 1].set_title('Marketing Spend vs Revenue')
axes[1, 1].set_xlabel('Spend')
axes[1, 1].set_ylabel('Revenue')
axes[1, 1].axline((0, 0), slope=1, color='red', linestyle='--', label='1:1')
axes[1, 1].legend()

plt.tight_layout()
plt.show()

# 5. Insights and Recommendations
print("\n" + "=" * 60)
print("KEY INSIGHTS AND RECOMMENDATIONS")
print("=" * 60)

# Best channel
best_channel = channel_metrics['ROI'].idxmax()
best_channel_roi = channel_metrics.loc[best_channel, 'ROI']
print(f"Best Performing Channel: {best_channel} (ROI: {best_channel_roi:.1f}%)")

# Best campaign
best_campaign = campaign_metrics['ROI'].idxmax()
best_campaign_roi = campaign_metrics.loc[best_campaign, 'ROI']
print(f"Best Performing Campaign: {best_campaign} (ROI: {best_campaign_roi:.1f}%)")

# Highest ROAS
highest_roas = channel_metrics['ROAS'].idxmax()
highest_roas_value = channel_metrics.loc[highest_roas, 'ROAS']
print(f"Highest ROAS Channel: {highest_roas} (ROAS: {highest_roas_value:.2f}x)")

print("\nRecommendations:")
print("1. Increase budget for high-ROI channels.")
print("2. Investigate underperforming channels for optimisation.")
print("3. Scale best-performing campaigns.")
print("4. Test new creative strategies for low-performing channels.")
print("5. Use data-driven attribution to allocate budget effectively.")

# 6. Save results
df.to_csv('marketing_campaign_data.csv', index=False)
channel_metrics.to_csv('channel_metrics.csv')
campaign_metrics.to_csv('campaign_metrics.csv')
print("\nData saved to CSV files.")
```

---

### Hands-on Coding Exercises

**Exercise 12.10** – Marketing analysis:
```python
# 1. Load/Generate marketing data.
# 2. Analyse channel and campaign performance.
# 3. Calculate key metrics (ROI, ROAS, CTR, CPA).
# 4. Create visualisations.
# 5. Generate recommendations.
```

---

### Mini Quiz

1. What is ROI in marketing?
2. What is ROAS?
3. What is CTR?
4. What is CPA?
5. How do you identify the best-performing marketing channel?

---

### Common Mistakes and Best Practices

| **Common Mistakes** | **Best Practices** |
|----------------------|---------------------|
| Not including all costs | Include all campaign costs |
| Ignoring attribution | Use multi-touch attribution |
| Focusing only on last-click | Consider full customer journey |
| Not comparing to benchmarks | Use industry benchmarks |

---

### Interview Questions

1. **What metrics would you track in a marketing dashboard?**  
   *Answer*: Impressions, clicks, conversions, CTR, CPC, CPA, ROAS, and ROI.

2. **How do you determine the best-performing marketing channel?**  
   *Answer*: By comparing ROI, ROAS, and CPA across channels.

3. **How can analytics improve marketing effectiveness?**  
   *Answer*: By identifying high-performing channels, optimising spend, and personalising campaigns.

---

### Assignment and Mini Project

**Project 12.10 – Marketing Dashboard**:
```python
# Build a complete marketing dashboard that:
# 1. Loads/Generates marketing data.
# 2. Analyses channel and campaign performance.
# 3. Calculates key metrics.
# 4. Creates visualisations.
# 5. Generates insights and recommendations.
# 6. Exports the results.
```

---

## Final Phase 12 Assessment

Now that you have completed all 10 projects, test your overall understanding.

### Self-Evaluation Checklist

- I can build a sales analysis dashboard.

- I can perform customer segmentation analysis.

- I can analyse HR data.

- I can analyse financial data.

- I can analyse stock market data.

- I can analyse COVID-19 data.

- I can analyse IPL data.

- I can analyse retail business data.

- I can analyse e-commerce data.

- I can analyse marketing campaign data.


---

### Portfolio Recommendations

1. **Select your best 3-5 projects** and polish them:
   - Add clear titles and descriptions.
   - Ensure visualisations are professional and informative.
   - Include key insights and recommendations.

2. **Create a GitHub repository** with your projects:
   - Include well-documented Jupyter notebooks.
   - Add README files explaining each project.
   - Include sample datasets and outputs.

3. **Add to your LinkedIn profile**:
   - Share links to your projects.
   - Write posts about your key insights.

4. **Prepare for interviews**:
   - Practice explaining your projects.
   - Be ready to discuss your methodology and insights.
   - Highlight the business value of your analysis.

---

## Final Congratulations!

You have completed all 12 phases of this comprehensive Python for Data Analytics curriculum! You have gained skills in:

- Python programming fundamentals.
- Data manipulation with Pandas and NumPy.
- Data visualisation with Matplotlib and Seaborn.
- Exploratory Data Analysis (EDA).
- Statistics for data analytics.
- SQL integration with Python.
- Automation and scheduling.
- Business Intelligence tool integration.
- Real-world data analytics projects.

You are now well-equipped to start your career as a data analyst, data scientist, or business intelligence professional. Keep learning, keep building, and keep growing!

Best of luck in your data analytics career! 🚀


---




<br/><br/><br/>
<center> <b>Happy Learning! 😊</b> </center>
