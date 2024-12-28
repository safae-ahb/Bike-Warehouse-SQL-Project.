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

- **Addresses**: Contains information about addresses:

    ![image alt]( https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/Adresses%20Table.PNG)
 
- **BusinessPartners**: Contains details about business partners:
  
   ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/BusinessPartners%20Table.PNG)
  
- **Employees**: Contains employee information:

![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/Employees%20Table.PNG)
  
- **ProductCategories** & **ProductCategoryText**: Describe product categories and their descriptions:
    ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/ProductCategories%20Table.PNG) .     ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/ProductCategory%20Text%20Table.PNG)

  
- **Products** & **ProductTexts**: Contain product details and product descriptions:
  ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/ProductTexts%20Table.PNG)
   ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/Products%20Table.PNG)
  
- **SalesOrderItems**: Contains details of individual items within a sales order:
  ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/SalesOrderItemsTable.PNG)
  
- **SalesOrders**: Contains information about sales orders:
  ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/SalesOrders%20Table.PNG)

## Key SQL Queries

### 1. Data Cleaning and Transformation:

- **Addresses Table**:
   - Checking for duplicates `ADDRESSID`.
   
- **BusinessPartners Table**:
   - Handled duplicates, missing or incorrect data.
   - Dropped the unnecessary FAXNUMBER column because it was empty.

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
Addresses are linked to Business Partners and Employees.
Combined Product Categories are linked to Products and Employees.
This relational model helps ensure that the data can be queried effectively and that all analysis is based on a solid data foundation.

### 3. Business Insights:

- **Top-selling Products**:
   - Identified products with the highest sales quantities and total sales revenue.
     
     ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/Highest%20sales%20quantities.PNG)

The top-performing product is BX-1013 (Category BX) with a metric of 510, while the lowest is RC-1051 (Category RC) with a metric of 154.
Category BX stands out with several high-performing products, including BX-1013 (510) and BX-1015 (329). Category RC shows more variation, with RC-1055 (315) and RC-1051 (154), the lowest value in the dataset. Category CC also has a mix, with CC-1023 (440) being the highest in its category.
 
 - Identified products with the highest total sales revenue.

    ![image alt]( https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/Highest%20total%20sales%20revenue..PNG)

   The top-performing product is EB-1137 (Category EB) with 345,625, and the lowest is BX-1016 (Category BX) with 10,606.75.
   Category EB leads with products like EB-1137 and EB-1134 . Category RC has strong performers like RC-1054 (221,334.75) but also lower ones like RC-1051 (63,412.125). Category BX shows a mix, with BX-1013 (37,716) being the highest and BX-1016 (10,606.75) the lowest.


- **Sales Performance by Product Category**:
   - Analyzed the top-performing product categories based on total sales revenue and order counts.

  ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/Top%20performing%20product%20categories%20based%20on%20total%20sales.PNG)

The top-performing category is EB with 1,153,425, followed by RC with 999,419.75.
Other categories include MB (354,662), CC (173,026.875), and HB (160,953.625). The lowest-performing category is CB with 46,550.

  ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/Top-performing%20product%20categories%20based%20on%20order%20counts.PNG)

The top-performing category is EB with 331, followed by BX with 319 and RC with 306.
Other categories include HB (243), MB (172), CC (157), CB (153), DB (139), and the lowest-performing category is RO with 110.

- **Employee Sales Performance**:
   - Tracked the highest sales volume and revenue for each employee.

  ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/Employee%20Sales%20Performance%201.PNG)
  
William Mussen leads with the highest score, followed by Javas Hegde and Philipp Egger. Other top performers include Pénélope Duperré and Haseena al Yousuf.
At the lower end, Roberta Holloway and Willard Chatman have some of the lowest scores, with Kenneth Weise having the smallest value of 155.

  ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/Employee%20Sales%20Performance%202.PNG)

  The ranking of employees by total revenue matches their ranking by sales volume . For example, William Mussen and Javas Hegde have the highest total revenues, while at the lower end, Roberta Holloway and Kenneth Weise have the smallest totals.

- **Customer Segmentation**:
   - Identified business partners with the highest number of orders and the highest total sales value by location.

  ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/Customer%20Segmentation%201.PNG)
  The ranking of business partners by sales volume is as follows:

The top business partners with the highest sales volume are Bike World Inc (14), followed by Amaze Bikes Inc, MX Bike, and Move by Bike (13 each).
On the lower end, Trek Cycle AG and Carefree Cycles are among the partners with the smallest sales volume (3 each).

  ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/Customer%20Segmentation%202.PNG)

  The top locations with the highest total revenue are Mumbai (IN) with 304,612, followed by Jebel Ali Free Zone (DU) with 159,812.625 and Ocala (US) with 158,440.625.
On the lower end, Berlin Mariendorf (DE) has the smallest total revenue with 21,233.625, followed by Talgarth (GB) with 27,811.

- **Sales Trends Over Time**:
   - Analyzed sales trends over the past months and years.

  ![image alt](https://github.com/safae-ahb/Bike-Warehouse-SQL-Project./blob/main/Sales%20Trends%20Over%20Time%201.PNG)

 The total revenue for the years 2018 and 2019, listed by month, is as follows:
In 2018, The month with the highest revenue was July with 234,312.75. On the lower end, January had the lowest total.
For 2019, January recorded a total of 191,072, while February showed a higher total at 217,406.875. June saw a total of 143,820.25, which was the lowest for the year.

## Technologies Used

- **SQL**: Structured Query Language for querying and transforming data.
- **SAP Bikes Sales Database**: A relational database containing sales data for the bike warehouse.

## License

This project is licensed under the MIT License.

