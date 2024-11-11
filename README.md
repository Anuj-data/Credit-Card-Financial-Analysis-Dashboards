# Credit Card Transactions Report Dashboard 📊

## Introduction 🎯
This project focuses on developing a comprehensive Power BI dashboard that provides real-time insights into key performance metrics and trends for credit card operations. The dashboard enables stakeholders to monitor and analyze critical aspects of credit card transactions, revenue, customer demographics, and other related metrics to improve decision-making.

## Background 🏦
The Credit Card Transactions Report Dashboard aggregates data from various customer and transaction records. By using advanced data analysis techniques and visualizations, it offers a clear, concise view of credit card performance and spending behaviors. The dashboard enables users to evaluate metrics such as revenue by expense type, customer demographics, transaction patterns, and more.

## Tools I Used 🛠️
- **SQL**: Used for querying and manipulating data from the underlying databases.
- **PostgreSQL**: Served as the database to manage and store data, especially for large transaction datasets.
- **Git and GitHub**: Version control and project management tools to collaborate, share, and track the progress of the project.
- **Power BI**: The primary tool for creating interactive dashboards and visualizations.

## The Analysis 🔍
### Key Metrics and DAX Queries
1. **Age Group**: Categorizes customers into different age ranges based on their birth date.
   ```DAX
   AgeGroup = SWITCH(
       TRUE(),
       'public cust_detail'[customer_age] < 30, "20-30",
       'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
       'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
       'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
       'public cust_detail'[customer_age] >= 60, "60+",
       "unknown"
   ) ```
   
1. **Income group**:Income Group: Classifies customers based on their income brackets.

```DAX
Copy code
IncomeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[income] < 35000, "Low",
    'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
    'public cust_detail'[income] >= 70000, "High",
    "unknown"
)
```

3. **Weekly Revenue Calculation**:  DAX formulas to calculate revenue per week and compare it to the previous week.
```DAX
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

Current_week_Revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]))
)

Previous_week_Revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))
```
# Credit Card Customer Dashboard Insights

## Key Insights 💡

### Quarterly Revenue and Transactions
- Revenue and transactions are stable, peaking in Q3 due to increased seasonal spending.

### Revenue by Expense Type
- Highest revenue from bills, followed by entertainment and fuel. Strong spending on travel and food reflects diverse habits.

### Revenue by Education Level
- Graduates lead in revenue, suggesting a link between education and spending capacity.

### Revenue by Job Type
- Business professionals contribute the most revenue, followed by white-collar and self-employed individuals.

### Customer Acquisition Cost by Card Category
- Blue card holders have the highest acquisition cost, with lower costs for Silver, Gold, and Platinum.

### Revenue by Chip Usage
- Swipe transactions generate the highest revenue, followed by chip and online transactions, indicating a preference for in-person card swipes.

### Revenue and Transaction Summary by Card Type
- Blue card holders dominate in revenue, transactions, and interest earned; Platinum and Gold show lower revenue.

### Income and Revenue by Job Type
- Highest revenue from businessmen, followed by white-collar and self-employed individuals.

### Income Groups
- High-income group contributes significantly more revenue than mid and low-income groups.

### Revenue by Age Group
- Customers aged 50-60 generate the highest revenue, followed by those aged 30-40 and 60+.

### Dependent Count
- Most customers have no or few dependents, impacting spending patterns.

### Education Level
- Graduates generate the most revenue, suggesting a correlation with financial activity.

### Top Revenue States
- Texas, New York, and California lead in revenue, likely due to population size or economic activity.

### Marital Status
- Married customers contribute the most revenue, reflecting household-level spending.

## What I Learned 📚
- **Power BI Skills**: Gained hands-on experience with advanced features like DAX formulas and dynamic visualizations.
- **Data Analysis**: Enhanced ability to analyze large datasets using SQL and Power BI.
- **Business Insights**: Linked customer behavior with transaction trends to provide actionable insights.

## Conclusions ✅
This project demonstrates the effectiveness of combining SQL for data processing with Power BI for visualization. The dashboard provides valuable insights into revenue streams, customer demographics, and transaction patterns, aiding stakeholders in decision-making.

## Additional Insights 🔎
- **Revenue Growth**: 28.8% increase in Week 53 (Dec 31).
- **Customer Demographics**: Males and high-income groups contribute more to revenue.
- **Geographic Concentration**: TX, NY, and CA lead in transactions and revenue.

## Closing Thoughts ✨
This project was a valuable experience in data analysis and visualization. The insights can support targeted marketing, customer engagement, and revenue growth strategies. I look forward to enhancing the dashboard further.


