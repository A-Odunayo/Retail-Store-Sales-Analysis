# Retail Sales Analysis

## Project Overview

This project involves a detailed analysis of sales data from a retail store. The goal is to identify top-selling products, assess regional performance, and uncover monthly sales trends. The findings are presented through an interactive Power BI dashboard with key visuals.

## Data Source

The data for this analysis is sourced from ["the retail store's sales database,"(https://github.com/A-Odunayo/Capstone-Project/blob/main/Sales%20Data.csv)]. It includes transactional data on sales, products, and customers, enabling comprehensive performance analysis.

## Project Structure

The project consists of three main components, each managed in Excel, SQL, and Power BI.

### Tools and Technologies

- **Excel**: Initial data exploration, including pivot tables and metric calculations.
- **SQL**: Complex queries to retrieve and summarize targeted insights.
- **Power BI**: Interactive dashboard to visually present insights.

### Folder Structure
Retail_Sales_Analysis/
├── Excel/
│   └── Sales_Analysis.xlsx               # Pivot tables, formulas, and exploratory analysis
├── SQL/
│   ├── total_sales_by_category.sql       # Query for total sales by product category
│   ├── transactions_by_region.sql        # Query for count of sales transactions by region
│   ├── highest_selling_product.sql       # Query for highest-selling product by total sales value
│   ├── total_revenue_per_product.sql     # Query for total revenue per product
│   ├── monthly_sales_totals.sql          # Query for monthly sales totals for the current year
│   ├── top_5_customers.sql               # Query for top 5 customers by purchase amount
│   ├── sales_percentage_by_region.sql    # Query to calculate percentage of total sales by region
│   └── products_no_sales_last_quarter.sql # Query to identify products with no sales in the last quarter
├── PowerBI/
│   └── Sales_Dashboard.pbix              # Power BI dashboard file for visual insights
├── screenshots/                          # Folder for visual screenshots
└── README.md                             # Project overview and instructions

## Data Cleaning and Preparation

Before analysis, the data underwent several cleaning and preparation steps:

1. **Handling Missing Values**: Identified and addressed missing values in key fields (e.g., sales amounts, product IDs).
2. **Data Type Conversion**: Ensured that fields were in the correct format (e.g., converting date fields to Date format, numerical fields to Numeric format).
3. **Removing Duplicates**: Checked for and removed any duplicate records in the dataset to ensure accuracy.
4. **Outlier Detection**: Analyzed the data for outliers and anomalies, addressing them as necessary.
5. **Data Transformation**: Created new calculated fields, such as total sales and revenue, to facilitate analysis.

## Data Exploration

The exploratory data analysis (EDA) phase included:

1. **Descriptive Statistics**: Generated summary statistics (mean, median, mode, standard deviation) for numerical variables to understand distributions.
2. **Data Visualizations**: Created initial visualizations (histograms, box plots) to identify patterns and trends in the data.
3. **Correlations**: Examined correlations between different variables (e.g., sales vs. region, sales vs. product category) to identify relationships.
4. **Segment Analysis**: Analyzed data segments (e.g., by region, product category) to uncover insights and inform business decisions.

## Analysis Details

### 1. Excel

The **Excel** workbook includes:
- **Pivot Tables**: Summarize total sales by product, region, and month.
  - **Product Sales by Category**: 
    ![Product Sales by Category](./screenshots/excel_sales_by_category.png)
  - **Regional Sales**:
    ![Regional Sales](./screenshots/excel_regional_sales.png)
  - **Monthly Sales Trends**:
    ![Monthly Sales Trends](./screenshots/excel_monthly_sales_trends.png)

- **Calculated Metrics**:
  - Average sales per product.
  - Total revenue by region.
  - **Top Products**:
    ![Top Products](./screenshots/excel_top_products.png)

### 2. SQL Queries

The **SQL** queries aim to answer specific business questions:
- **Total Sales by Product Category**: Product performance by category.
- **Sales Transactions by Region**: Count of sales transactions per region.
- **Highest-Selling Product**: Product with the highest sales value.
- **Total Revenue per Product**: Revenue by each product.
- **Monthly Sales Totals**: Monthly sales for the current year.
- **Top 5 Customers by Purchase Amount**:
  ![Top 5 Customers](./screenshots/sql_top_5_customers.png)
- **Sales Percentage by Region**: Each region's contribution to total sales.
- **Products with No Sales in Last Quarter**: Products without sales in the last quarter.

### 3. Power BI Dashboard

The **Power BI** dashboard showcases key insights in an interactive, visual format:
- **Sales Overview**: Includes total sales and key performance metrics.
  ![Sales Overview](./screenshots/powerbi_sales_overview.png)
- **Top-Performing Products**: Highest-selling products by total sales.
  ![Top-Performing Products](./screenshots/powerbi_top_products.png)
- **Regional Breakdown**: Sales distribution by region.
  ![Regional Breakdown](./screenshots/powerbi_regional_breakdown.png)
- **Monthly Trends**: Visualization of sales trends over months.
  ![Monthly Trends](./screenshots/powerbi_monthly_trends.png)

## Visualizations

### Excel
- **Pivot Table Visualizations**:
  - **Product Sales by Category**: A bar chart showing sales by product category.
  - **Regional Sales**: Heat map to display sales differences across regions.
  - **Monthly Sales Trends**: Line graph for monthly sales patterns.

- **Calculated Metrics**:
  - **Conditional Formatting**: Highlights high-performing regions and products.
  - **Top Products**: Bar chart for easy comparison.

### SQL (for Power BI)
- Export SQL query results into Power BI for advanced visualizations:
  - **Total Sales by Product Category**: Pie chart for visualizing category proportions.
  - **Sales Transactions by Region**: Map visual to display sales density by region.
  - **Monthly Sales Totals**: Line or column chart for monthly sales tracking.
  - **Top 5 Customers**: Horizontal bar chart to represent top customers visually.

### Power BI Dashboard
- **Overview Cards**: KPI cards to show key metrics such as total sales, average sales, and revenue by region.
- **Top-Performing Products**: Horizontal bar chart to rank products by sales.
- **Regional Sales**: Map or stacked bar chart for regional performance insights.
- **Monthly Sales Trends**: Line chart to show trends across months interactively.

## Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/Retail_Sales_Analysis.git
Open the Excel Workbook:

Explore Sales_Analysis.xlsx in the Excel folder for pivot tables, metrics, and visualizations.
Run SQL Queries:

Import the data into your SQL environment and execute the queries from the SQL folder. Export the results to Power BI if needed.
Power BI Dashboard:

Open Sales_Dashboard.pbix in Power BI to interact with and customize the dashboard visuals.
