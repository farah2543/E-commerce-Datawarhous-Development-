# E-Commerce Data Warehousing Project  


## Project Overview  
This project implements a data warehouse solution for an **e-commerce platform**. It integrates multiple data sources to support business analysis on sales, returns, marketing campaigns, products, suppliers, and customers.  

The project focuses on building:  
- **Physical model of the source system**  
- **Dimensional model** (Star Schema)  
- **ETL (Extract, Transform, Load) processes** using **SSIS**  
- **Analytical queries** for actionable insights  

---

## Dimensional Model  

### Business Processes Modeled  
1. **Sales Transactions** (by customer, marketing campaign, country, and date)  
2. **Returns Management** (by product, customer, review, and sentiment)  
3. **Product Sales** (by supplier, subcategory, and customer)  

### Fact Tables (Transactional)  
- **F_Sales**  
- **F_Returns**  
- **F_Product_Sales**  

### Dimensions  
- `Customer` *(Slowly Changing Dimension)*  
- `Country` *(Static Degenerate Dimension)*  
- `Marketing Campaign` *(Static Dimension)*  
- `Product` *(Slowly Changing Dimension)*  
- `Subcategory` *(Degenerate Dimension)*  
- `Supplier` *(Slowly Changing Dimension)*  
- `Payment Method` *(Slowly Changing Dimension)*  
- `Date` *(Confirmed Dimension)*  

### Measures  
- **actual_cost** *(Fully Additive)*  
- **amount_refunded** *(Fully Additive)*  
- **quantity** *(Semi-Additive)*  
- **rating** *(Non-Additive)*  
- **sentiment** *(Non-Additive)*  

---

## ETL Processes  

ETL pipelines are implemented in **SSIS** for:  
1. Campaign Dimension Loading  
2. Customer Dimension Loading  
3. Product Dimension Loading  
4. Supplier Dimension Loading  
5. Fact Tables Loading (Sales, Returns, Product Sales)  

Each process involves:  
- **Control Flow**  
- **Data Flow:** from source → staging area → destination  

The ETL packages are scheduled for automated deployment.  

---

## Analytical Queries  

### Examples  
### Sales Analysis  
- Total sales by country  
- Total sales by customer  
- Orders count per customer  
- Sales by date  
- Sales by marketing campaign  
- Sales by payment method  

### Returns Analysis  
- Total refunded amount by customer  
- Returns within a date range  
- Returns count per product or customer  

### Product Sales Analysis  
- Quantity sold per product, supplier, or subcategory  
- Total sales per product, supplier, or subcategory  

All queries are optimized to leverage the fact and dimension tables.  

---

## Tools & Technologies  
- **SQL Server**  
- **SSIS (SQL Server Integration Services)** for ETL  
- **SQL** for querying the data warehouse  

---

## How to Run the Project  

1. **Restore the Database:**  
   - Import the database schema and data into SQL Server.  

2. **Run ETL Packages:**  
   - Open the SSIS project and execute the ETL packages in the correct order (dimensions first, then fact tables).  

3. **Verify the Data:**  
   - Run the provided SQL queries on fact tables to ensure data is correctly loaded.  

4. **Schedule Packages:**  
   - Set up SQL Server Agent jobs to run ETL packages automatically.  

---

## Insights  

The data warehouse provides insights into:  
- Customer purchasing behavior  
- Campaign effectiveness  
- Product sales performance  
- Refund and returns analysis  

These insights help in **decision-making**, **marketing strategy**, and **supplier management**.  
