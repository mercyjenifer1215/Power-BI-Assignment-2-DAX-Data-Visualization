# 📊 Project Title: Sales Performance Analysis Using Power BI

This Power BI project focuses on analysing sales performance using DAX calculations and interactive visualizations to understand sales trends, profit margins, product performance, and regional sales distribution.

## 📑 Table of Contents

- [Project Overview](#-project-overview)
- [Data Sources & Architecture](#-data-sources--architecture)
- [Data Transformation (ETL)](#-data-transformation-etl)
- [Data Model & DAX](#-data-model--dax)
- [Dashboard Features](#-dashboard-features)
- [Key Insights](#-key-insights)
- [How To Use](#-how-to-use)

---

## 🎯 Project Overview

- **Business Problem:** Understanding sales performance, comparing actual sales with targets, and identifying high-performing products and regions.
- **Objective:** To create an interactive Power BI dashboard that helps analyse sales, profit, quantity, monthly trends, and order distribution.
- **Target Audience:** Business owners, sales managers, business analysts, and management teams.

## 🗃️ Data Sources & Architecture

- **Source Systems:** Sales dataset provided in Excel/CSV format.
- **Data Tables Used:**
  - Order Details
  - List of Orders
  - Sales Target
  - Order ID Lookup (created for relationship management)
- **Data Volume:** Based on the provided sales dataset containing 500 distinct orders.
- **Storage Mode:** Import Mode (Power BI Desktop).

## ⚙️ Data Transformation (ETL)

- **Tool Used:** Power Query Editor.
- **Key Transformations:**
  - Imported the sales datasets into Power BI.
  - Checked and corrected column data types.
  - Converted Order Date into the Date data type.
  - Created a separate Order ID Lookup table to manage duplicate Order IDs.
  - Established relationships between the tables.
  - Checked the data to ensure accurate calculations and reporting.

## 🧠 Data Model & DAX

- **Model Type:** Relational Data Model.
- **Fact Table:** Order Details.
- **Other Tables:** List of Orders, Sales Target, and Order ID Lookup.

### Key DAX Calculations

**1. Category Type – Calculated Column**

```dax
Category Type =
'Order Details'[Category] & " - " &
'Order Details'[Sub-Category]
```

**2. Revenue per Order – Calculated Column**

```dax
Revenue per Order =
'Order Details'[Amount] *
'Order Details'[Quantity]
```

**3. Sales Category – Calculated Column**

```dax
Sales Category =
IF(
    'Order Details'[Amount] >
    AVERAGE('Order Details'[Amount]),
    "Above Average",
    "Below Average"
)
```

**4. Total Sales**

```dax
Total Sales =
SUM('Order Details'[Amount])
```

**5. Order Count**

```dax
Order Count =
DISTINCTCOUNT('List of Orders'[Order ID])
```

**6. Total Profit**

```dax
Total Profit =
SUM('Order Details'[Profit])
```

**7. Total Quantity**

```dax
Total Quantity =
SUM('Order Details'[Quantity])
```

**8. Sales Target**

```dax
Sales Target =
SUM('Sales target'[Target])
```

**9. Minimum Target**

```dax
Minimum Target =
MIN('Sales target'[Target])
```

**10. Year-to-Date Sales**

```dax
YTD Sales =
TOTALYTD(
    [Total Sales],
    'List of Orders'[Order Date]
)
```

**11. Max Profit Margin**

```dax
Max Profit Margin =
MAXX(
    'Order Details',
    DIVIDE(
        'Order Details'[Profit],
        'Order Details'[Amount]
    )
)
```

## 🖥️ Dashboard Features

The Power BI report includes the following visualizations:

### 1. Sales Target Achievement by Category
- Clustered Column Chart.
- Compares actual sales with sales targets across different categories.
- Helps identify categories that meet or fall below their targets.

### 2. Max Profit Margin by Sub-Category
- Donut Chart.
- Displays the maximum profit margin for different product sub-categories.
- Helps identify sub-categories with higher profit margins.

### 3. Monthly Sales Trend
- Line Chart.
- Displays monthly sales performance over time.
- Helps identify sales patterns and monthly fluctuations.

### 4. Profit vs Quantity by Sub-Category
- Scatter Chart.
- Compares profit and quantity sold across sub-categories.
- Helps understand the relationship between sales volume and profitability.

### 5. Total Sales Amount and Sales Target
- Card Visuals.
- Displays total sales amount and overall sales target.
- Provides a quick comparison of sales performance.

### 6. Minimum Target by Category
- Table Visual.
- Displays the minimum target for each category.
- Helps compare minimum sales targets.

### 7. Sales Performance Matrix
- Matrix Visual.
- Compares actual sales with sales targets across categories and months.
- Helps analyse monthly category-wise sales performance.

### 8. Geographic Sales Analysis
- Map Visual.
- Displays sales distribution across different cities.
- Helps identify regional sales patterns.

### 9. Sales Distribution by Sub-Category
- Treemap Visual.
- Represents sales distribution using different-sized rectangular blocks.
- Larger blocks indicate higher sales contributions.

### 10. Order Count Analysis by State
- Funnel Chart.
- Displays order counts across different states.
- Helps identify states with higher and lower order volumes.

## 💡 Key Insights

- **Sales Performance:** Comparing actual sales with targets helps identify category-wise performance.
- **Monthly Trends:** Monthly sales analysis helps understand changes in sales over time.
- **Product Performance:** Donut charts and treemaps help identify sub-categories contributing more to total sales.
- **Profitability:** Profit margin and scatter chart analysis help understand product profitability.
- **Regional Performance:** Map visualization helps identify cities contributing to sales.
- **Order Distribution:** Funnel charts help compare order counts across different states.

### Recommendations

- Focus more on product categories that generate higher sales.
- Review categories that are not achieving their sales targets.
- Monitor monthly sales trends to improve sales planning.
- Analyse low-profit sub-categories and identify improvement opportunities.
- Focus on regions and states that generate higher sales and order volumes.

## 🚀 How To Use

1. **Prerequisites:** Install Microsoft Power BI Desktop.
2. **Project Files:** Open the provided `.pbix` Power BI project file.
3. **Data Sources:** Ensure the original Excel/CSV files are available.
4. **Data Refresh:** If the source files are moved, update their locations under Data Source Settings.
5. **Explore Dashboard:** Open the report pages and interact with the charts, cards, tables, maps, and matrix visuals.
6. **Analyse Results:** Use the visualizations to understand sales performance and identify business insights.

---

## 📝 Conclusion

This project helped me understand how to use Power BI for data analysis and visualization. I learned how to create calculated columns, write DAX measures, manage table relationships, and build different types of charts. The dashboard provides a clear view of sales performance, product profitability, monthly trends, and regional sales distribution. Overall, this project improved my analytical thinking and practical knowledge of Power BI.
