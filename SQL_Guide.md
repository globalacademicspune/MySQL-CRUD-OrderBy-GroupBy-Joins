# MySQL Installation and SQL Operations Guide

## Step 1: Update System Packages

```bash
sudo apt update
sudo apt upgrade -y
```

---

## Step 2: Install MySQL Server

```bash
sudo apt install mysql-server -y
```

Verify MySQL service:

```bash
sudo systemctl status mysql
```

---

## Step 3: Secure MySQL Installation

```bash
sudo mysql_secure_installation
```

---

## Step 4: Login to MySQL

```bash
sudo mysql
```

Configure root password:

```sql
ALTER USER 'root'@'localhost'
IDENTIFIED WITH mysql_native_password BY 'aws';

FLUSH PRIVILEGES;
```

Exit and reconnect:

```bash
mysql -u root -p
```

---

## Step 5: Create Databases

View existing databases:

```sql
SHOW DATABASES;
```

Create five databases:

```sql
CREATE DATABASE shop;
CREATE DATABASE shop1;
CREATE DATABASE shop2;
CREATE DATABASE shop3;
CREATE DATABASE shop4;
```

Verify:

```sql
SHOW DATABASES;
```

---

## Step 6: Select Database

```sql
USE shop;
```

---

## Step 7: Create Customers Table

```sql
CREATE TABLE customers (
    customer_id INT,
    customer_name VARCHAR(50),
    country VARCHAR(50)
);
```

Insert data:

```sql
INSERT INTO customers VALUES (1,'Zaid','India');
INSERT INTO customers VALUES (2,'Anas','UK');
INSERT INTO customers VALUES (3,'Rahul','USA');
```

Display records:

```sql
SELECT * FROM customers;
```

---

## Step 8: Create Employee Table

```sql
CREATE TABLE employee (
    emp_id INT,
    emp_name VARCHAR(50),
    gender VARCHAR(50)
);
```

Insert data:

```sql
INSERT INTO employee VALUES (1,'Ahad','Male');
INSERT INTO employee VALUES (2,'Abdul','Male');
INSERT INTO employee VALUES (3,'Rakul','Female');
```

Display records:

```sql
SELECT * FROM employee;
```

---

## Step 9: Create Orders Table

```sql
CREATE TABLE orders (
    order_id INT,
    customer_id INT,
    emp_id INT
);
```

Insert data:

```sql
INSERT INTO orders VALUES (1,1,5);
INSERT INTO orders VALUES (2,2,9);
INSERT INTO orders VALUES (3,3,6);
```

Display records:

```sql
SELECT * FROM orders;
```

---

## Step 10: ORDER BY Example

Sort orders in descending order:

```sql
SELECT *
FROM orders
ORDER BY order_id DESC;
```

---

## Step 11: GROUP BY Example

Count customers by country:

```sql
SELECT country,
       COUNT(customer_id) AS total_customers
FROM customers
GROUP BY country;
```

---

## Step 12: WHERE Clause Example

Retrieve customers from India:

```sql
SELECT *
FROM customers
WHERE country = 'India';
```

---

## Step 13: INNER JOIN Example

Display customer details with order information:

```sql
SELECT c.customer_name,
       c.country,
       o.order_id
FROM customers AS c
INNER JOIN orders AS o
ON c.customer_id = o.customer_id;
```

---

## Step 14: RIGHT JOIN Example

Display all employees and matching orders:

```sql
SELECT orders.order_id,
       employee.emp_name
FROM orders
RIGHT JOIN employee
ON orders.emp_id = employee.emp_id;
```

---

## Step 15: LEFT JOIN Example

Display all customers and matching orders:

```sql
SELECT customers.customer_name,
       orders.order_id
FROM customers
LEFT JOIN orders
ON customers.customer_id = orders.customer_id;
```

---

## Step 16: CROSS JOIN Example

Display Cartesian product of customers and orders:

```sql
SELECT customers.customer_name,
       customers.country,
       orders.order_id
FROM customers
CROSS JOIN orders;
```

---

## Step 17: Verify Tables

```sql
SHOW TABLES;
```

Display data:

```sql
SELECT * FROM customers;
SELECT * FROM employee;
SELECT * FROM orders;
```
