# Mastering Subqueries in SQL: A Comprehensive Guide

## Introduction to Subqueries:

In the vast landscape of SQL, subqueries emerge as a powerful tool, offering a dynamic way to retrieve and manipulate data. In this comprehensive guide, we will unravel the mysteries of subqueries, exploring their types, practical examples, and applications across various SQL statements.

## What is a Subquery?

A subquery, also known as a nested query or inner query, is a query embedded within another SQL statement. It allows you to retrieve data from one or more tables based on the result of a query.

## Practical Example of Subquery:

Consider a scenario where you want to find all employees who earn more than the average salary. A subquery can help achieve this by calculating the average salary and then comparing it with individual salaries.

```sql
SELECT emp_name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

### Types of Subqueries:

Subqueries come in various flavors, each serving a specific purpose. Let's explore the three main types:

#### 1. Independent Subquery - Scalar Subquery:

**Details:**

A scalar subquery returns a single value and is independent of the outer query.

**Example #1:**

```sql
SELECT emp_name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

**Example #2:**

```sql
SELECT product_name, price
FROM products
WHERE price = (SELECT MAX(price) FROM products);
```

**Example #3:**

```sql
SELECT customer_name
FROM customers
WHERE customer_id = (SELECT MIN(customer_id) FROM customers);
```

**Example #4:**

```sql
SELECT order_id, order_date
FROM orders
WHERE order_date = (SELECT MAX(order_date) FROM orders);
```

**Output Before:**

| emp_name | salary |
|----------|--------|
| John     | 45000  |
| Jane     | 50000  |
| Bob      | 55000  |
| Alice    | 60000  |

**Output After:**

| emp_name | salary |
|----------|--------|
| Bob      | 55000  |
| Alice    | 60000  |

#### 2. Independent Subquery - Row Subquery:

**Details:**

A row subquery returns multiple rows but only one column. It is independent of the outer query.

**Example #1:**

```sql
SELECT emp_name, department
FROM employees
WHERE (department, salary) = (SELECT department, MAX(salary) FROM employees GROUP BY department);
```

**Example #2:**

```sql
SELECT product_name, price
FROM products
WHERE (price, category) IN (SELECT MAX(price), category FROM products GROUP BY category);
```

**Example #3:**

```sql
SELECT customer_name, order_date
FROM customers
WHERE (order_date, customer_id) = (SELECT MAX(order_date), customer_id FROM orders GROUP BY customer_id);
```

**Output Before:**

| emp_name | department | salary |
|----------|------------|--------|
| John     | HR         | 45000  |
| Jane     | IT         | 50000  |
| Bob      | Sales      | 55000  |
| Alice    | IT         | 60000  |

**Output After:**

| emp_name | department | salary |
|----------|------------|--------|
| John     | HR         | 45000  |
| Jane     | IT         | 50000  |
| Bob      | Sales      | 55000  |
| Alice    | IT         | 60000  |

#### 3. Independent Subquery - Table Subquery:

**Details:**

A table subquery returns multiple rows and multiple columns. It is independent of the outer query.

**Example #1:**

```sql
SELECT *
FROM employees
WHERE (department, salary) IN (SELECT department, MAX(salary) FROM employees GROUP BY department);
```

**Example #2:**

```sql
SELECT *
FROM products
WHERE (price, category) IN (SELECT MAX(price), category FROM products GROUP BY category);
```

**Example #3:**

```sql
SELECT *
FROM customers
WHERE (order_date, customer_id) IN (SELECT MAX(order_date), customer_id FROM orders GROUP BY customer_id);
```

**Output Before:**

| emp_id | emp_name | department | salary |
|--------|----------|------------|--------|
| 1      | John     | HR         | 45000  |
| 2      | Jane     | IT         | 50000  |
| 3      | Bob      | Sales      | 55000  |
| 4      | Alice    | IT         | 60000  |

**Output After:**

| emp_id | emp_name | department | salary |
|--------|----------|------------|--------|
| 3      | Bob      | Sales      | 55000  |
| 4      | Alice    | IT         | 60000  |

#### 4. Correlated Subquery:

**Details:**

A correlated subquery is related to the outer query and references columns from the outer query.

**Example #1:**

```sql
SELECT emp_name, salary
FROM employees e1
WHERE salary > (SELECT AVG(salary) FROM employees e2 WHERE e1.department = e2.department);
```

**Example #2:**

```sql
SELECT product_name, price
FROM products p1
WHERE price = (SELECT MAX(price) FROM products p2 WHERE p1.category = p2.category);
```

**Output Before:**

| emp_name | salary |
|----------|--------|
| John     | 45000  |
| Jane     | 50000  |
| Bob      | 55000  |
| Alice    | 60000  |

**Output After:**

| emp_name | salary |
|----------|--------|
| Bob      | 55000  |
| Alice    | 60000  |

