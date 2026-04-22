# Customer-Cohort-Retention-Analysis
Cohort analysis using SQL and Power BI
**Project Overview**

This project focuses on analyzing customer retention behavior using cohort analysis. By grouping customers based on their first purchase month, the project tracks how customer engagement changes over time. The insights are visualized using Power BI dashboards to understand retention trends and customer drop-off patterns.

**Objectives**
Analyze customer retention over time
Identify patterns in customer behavior
Measure how many customers return after their first purchase
Build an interactive dashboard for business insights

**🛠️ Tools & Technologies**
SQL Server → Data cleaning, transformation, cohort logic
Power BI → Data visualization and dashboard creation

**🧹 Data Cleaning (SQL)**

Performed multiple steps to ensure data quality:

Removed records with NULL CustomerID
Filtered invalid data:
Quantity > 0
UnitPrice > 0
Removed duplicate records using ROW_NUMBER()
Final cleaned dataset: 392,669 records

**Cohort Analysis Logic**

1. Cohort Creation
Identified each customer’s first purchase date
Converted it into month-level cohort using:
DATEFROMPARTS(YEAR(MIN(InvoiceDate)), MONTH(MIN(InvoiceDate)), 1)
2. Cohort Index
Calculated months since first purchase:
DATEDIFF(MONTH, Cohort_Date, InvoiceDate) + 1

**Example:**

Cohort_Date	InvoiceDate	Cohort_Index
Jan 2022	Jan 2022	1
Jan 2022	Feb 2022	2
3. Retention Calculation
Retention Rate = (Customers in Month X / Customers in Month 1) * 100
Used DECIMAL(5,2) for precision
Stored results in temp table

**Key Insights**

Customer retention declines over time
First month always shows 100% retention
Significant drop observed after Month 1
Some cohorts perform better than others → indicates behavioral differences

**📈 Power BI Dashboard**

🔹 Customer Retention Heatmap
Shows % of users returning each month
Color gradient highlights retention intensity
🔹 Cohort Table
Displays actual customer counts
Helps compare cohort size and drop-off

**Key Observations**
Early drop-off indicates low initial engagement
Stable cohorts suggest better customer loyalty
Retention trends can help improve marketing and product strategy

**Business Impact**

Identify customer churn patterns
Improve customer retention strategies
Support data-driven decision making

**Dashboard Preview**

<img width="745" height="359" alt="image" src="https://github.com/user-attachments/assets/1fa7559f-ca44-4e66-b0ab-e3585211f14b" />

**Future Improvements**

Add churn rate analysis
Perform revenue-based cohort analysis
Build interactive filters (country, segment)
Use DAX measures for dynamic insights

**Conclusion**

This project demonstrates how cohort analysis can be used to track customer behavior over time. By combining SQL for data processing and Power BI for visualization, it provides actionable insights into customer retention and engagement.
