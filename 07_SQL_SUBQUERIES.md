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

