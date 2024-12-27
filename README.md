# Bike Warehouse SQL Project

This project involves analyzing and transforming data from a bike warehouse database using SQL. The goal is to clean, transform, and query the data to generate insights about products, employees, customers, sales, and trends.

## Overview

The `SAP Bikes Sales` database contains various tables that represent business data for a bike warehouse, such as information on products, sales, employees, business partners, and more. This project focuses on cleaning and transforming data, optimizing database schema, and generating SQL queries to gain business insights.

### Key SQL Operations:
1. **Data Cleaning & Transformation**: 
   - Remove duplicate records from key tables.
   - Drop unnecessary columns and handle null values.
   - Populate new columns based on existing data.
   - Merge related tables to create new insights.
   
2. **Business Insights Queries**:
   - **Top-selling Products**: Identify products with the highest sales quantities and total revenue.
   - **Sales Performance by Product Category**: Analyze revenue and order counts by product category.
   - **Employee Sales Performance**: Track employees' contribution to sales volumes and revenue.
   - **Customer Segmentation**: Examine the number of orders placed by business partners and their total sales value.
   - **Sales Trends**: Analyze sales trends over time and calculate average order values.

## Tables Involved

- **Addresses**: Contains information about addresses.
- **BusinessPartners**: Contains details about business partners.
- **Employees**: Contains employee information.
- **ProductCategories** & **ProductCategoryText**: Describe product categories and their descriptions.
- **Products** & **ProductTexts**: Contain product details and product descriptions.
- **SalesOrderItems**: Contains details of individual items within a sales order.
- **SalesOrders**: Contains information about sales orders.

## Key SQL Queries

### 1. Data Cleaning and Transformation:

- **Addresses Table**:
   - Removed duplicate `ADDRESSID`.
   
- **BusinessPartners Table**:
   - Dropped unnecessary `FAXNUMBER` column.
   - Removed duplicates and handled missing or incorrect data.

- **Employee Table**:
   - Dropped unnecessary columns.
   - Populated `NAME_INITIALS` based on employee's first, middle, and last name initials.
   - Fixed column type issues.

- **Product Categories and Product Texts**:
   - Merged `ProductCategories` and `ProductCategoryText` tables into a new `CombinedProductCategories` table for easy analysis.

- **Products Table**:
   - Dropped irrelevant columns such as `WIDTH`, `DEPTH`, `HEIGHT`, etc.

- **Sales Order Items Table**:
   - Fixed null values in `GROSSAMOUNT` and created a `TOTALGROSSAMOUNT` column to track sales volume.
 
 ### 2. Database Diagram and Relationships
In addition to the data cleaning and analysis, a database diagram has been created to visualize the relationships between different tables in the SAP Bikes database. This diagram provides a clear understanding of how the tables are connected and how data flows through the system.

![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/Diagram.PNG?raw=true)


The key relationships include:

Sales Orders are linked to Business Partners and Employees.
Sales Order Items are linked to Sales Orders and Products.
Addresses are linked to Business Partners.
Product Categories are linked to Products.
This relational model helps ensure that the data can be queried effectively and that all analysis is based on a solid data foundation.

### 3. Business Insights:

- **Top-selling Products**:
   - Identified products with the highest sales quantities and total sales revenue.

```sql
SELECT 
    Products.PRODUCTID, 
    SUM(SalesOrderItems.QUANTITY) AS TotalQuantity
FROM 
    SalesOrderItems
JOIN 
    Products ON SalesOrderItems.PRODUCTID = Products.PRODUCTID
GROUP BY 
    Products.PRODUCTID
ORDER BY 
    TotalQuantity DESC;
```

- **Sales Performance by Product Category**:
   - Analyzed the top-performing product categories based on total sales revenue and order counts.



- **Employee Sales Performance**:
   - Tracked the highest sales volume and revenue for each employee.



- **Customer Segmentation**:
   - Identified business partners with the highest number of orders and the highest total sales value by location.



- **Sales Trends Over Time**:
   - Analyzed sales trends over the past months and years, including calculating the average order value by month or quarter.



## Technologies Used

- **SQL**: Structured Query Language for querying and transforming data.
- **SAP Bikes Sales Database**: A relational database containing sales data for the bike warehouse.

## License

This project is licensed under the MIT License.

