# Task 21 – Basic SQL SELECT Queries using Northwind Database

## 📌 Objective

The objective of this task was to practice basic SQL operations using the Northwind database. I worked with customer, product, order, and order detail data using MySQL Workbench.

## 🛠️ Tools Used

- MySQL
- MySQL Workbench
- Northwind Dataset

## 📂 Tables Used

- customer
- products
- orders
- order_details

## 🔍 SQL Concepts Practiced

- SELECT
- Selecting specific columns
- WHERE clause
- ORDER BY
- COUNT()
- JOIN
- Calculated columns
- LIMIT

## 💻 Queries Practiced

### 1. Select all customers:
SELECT * FROM customer;

2. Select specific customer details
SELECT customerID, companyName, city
FROM customer;

3. Filter customers by country
SELECT customerID, companyName, city, country
FROM customer
WHERE country = 'Germany';

4. Filter customers by city
SELECT customerID, companyName, city
FROM customer
WHERE city = 'London';

5. Sort customers by company name
SELECT customerID, companyName, city
FROM customer
ORDER BY companyName ASC;

6. Sort customers by city
SELECT customerID, companyName, city
FROM customer
ORDER BY city ASC;

7. Filter products by price
SELECT id, product_name, list_price
FROM products
WHERE list_price > 50;

8. Join orders with customers and order details
SELECT
    o.id AS order_id,
    o.customer_id,
    c.companyName,
    o.order_date,
    od.product_id,
    od.quantity,
    od.unit_price
FROM orders o
JOIN customer c ON o.customer_id = c.customerID
JOIN order_details od ON o.id = od.order_id
LIMIT 20;

9. Calculate total order amount
SELECT
    o.id AS order_id,
    c.companyName,
    p.product_name,
    od.quantity,
    od.unit_price,
    (od.quantity * od.unit_price) AS total_amount
FROM orders o
JOIN customer c ON o.customer_id = c.customerID
JOIN order_details od ON o.id = od.order_id
JOIN products p ON od.product_id = p.id
LIMIT 20;

10. Count total customers
SELECT COUNT(*) AS total_customers
FROM customer;
