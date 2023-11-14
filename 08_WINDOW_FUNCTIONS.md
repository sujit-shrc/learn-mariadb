# Unveiling the Power of Window Functions in SQL

## Introduction to Window Functions:

In the realm of SQL, window functions stand as a powerful tool for performing calculations across a set of table rows related to the current row. These functions operate within a specific "window" or "frame" of rows, providing a dynamic way to analyze and derive insights from your data. In this comprehensive guide, we will explore various window functions and their applications through practical examples.

## Aggregate Function with OVER() (Example #1):

**Example:**

```sql
SELECT emp_name, salary, SUM(salary) OVER() AS total_salary
FROM employees;
```

**Output Before:**

| emp_name | salary |
|----------|--------|
| John     | 45000  |
| Jane     | 50000  |
| Bob      | 55000  |
| Alice    | 60000  |

**Output After:**

| emp_name | salary | total_salary |
|----------|--------|--------------|
| John     | 45000  | 210000       |
| Jane     | 50000  | 210000       |
| Bob      | 55000  | 210000       |
| Alice    | 60000  | 210000       |

## Example #2:

```sql
SELECT emp_name, salary, AVG(salary) OVER() AS avg_salary
FROM employees;
```

**Output Before:**

| emp_name | salary |
|----------|--------|
| John     | 45000  |
| Jane     | 50000  |
| Bob      | 55000  |
| Alice    | 60000  |

**Output After:**

| emp_name | salary | avg_salary |
|----------|--------|------------|
| John     | 45000  | 52500      |
| Jane     | 50000  | 52500      |
| Bob      | 55000  | 52500      |
| Alice    | 60000  | 52500      |

## Example #3:

```sql
SELECT emp_name, salary, MAX(salary) OVER() AS max_salary
FROM employees;
```

**Output Before:**

| emp_name | salary |
|----------|--------|
| John     | 45000  |
| Jane     | 50000  |
| Bob      | 55000  |
| Alice    | 60000  |

**Output After:**

| emp_name | salary | max_salary |
|----------|--------|------------|
| John     | 45000  | 60000      |
| Jane     | 50000  | 60000      |
| Bob      | 55000  | 60000      |
| Alice    | 60000  | 60000      |

## RANK():

```sql
SELECT emp_name, salary, RANK() OVER(ORDER BY salary DESC) AS salary_rank
FROM employees;
```

**Output Before:**

| emp_name | salary |
|----------|--------|
| John     | 45000  |
| Jane     | 50000  |
| Bob      | 55000  |
| Alice    | 60000  |

**Output After:**

| emp_name | salary | salary_rank |
|----------|--------|-------------|
| Alice    | 60000  | 1           |
| Bob      | 55000  | 2           |
| Jane     | 50000  | 3           |
| John     | 45000  | 4           |

## DENSE_RANK():

```sql
SELECT emp_name, salary, DENSE_RANK() OVER(ORDER BY salary DESC) AS dense_salary_rank
FROM employees;
```

**Output Before:**

| emp_name | salary |
|----------|--------|
| John     | 45000  |
| Jane     | 50000  |
| Bob      | 55000  |
| Alice    | 60000  |

**Output After:**

| emp_name | salary | dense_salary_rank |
|----------|--------|-------------------|
| Alice    | 60000  | 1                 |
| Bob      | 55000  | 2                 |
| Jane     | 50000  | 3                 |
| John     | 45000  | 4                 |

## ROW_NUMBER():

```sql
SELECT emp_name, salary, ROW_NUMBER() OVER(ORDER BY salary DESC) AS row_number
FROM employees;
```

**Output Before:**

| emp_name | salary |
|----------|--------|
| John     | 45000  |
| Jane     | 50000  |
| Bob      | 55000  |
| Alice    | 60000  |

**Output After:**

| emp_name | salary | row_number |
|----------|--------|------------|
| Alice    | 60000  | 1          |
| Bob      | 55000  | 2          |
| Jane     | 50000  | 3          |
|

 John     | 45000  | 4          |

## Short Summary of the Above 3 Window Functions:

- **RANK():** Assigns a unique rank to each distinct row within the result set, with gaps between ranks when values are equal.
  
- **DENSE_RANK():** Similar to RANK(), but without gaps between ranks for equal values. Ranks are consecutive.

- **ROW_NUMBER():** Assigns a unique number to each row within the result set, without considering equality of values.

## Example #4:

```sql
SELECT emp_name, salary,
       FIRST_VALUE(salary) OVER(ORDER BY salary DESC) AS first_salary,
       LAST_VALUE(salary) OVER(ORDER BY salary DESC) AS last_salary
FROM employees;
```

**Output Before:**

| emp_name | salary |
|----------|--------|
| John     | 45000  |
| Jane     | 50000  |
| Bob      | 55000  |
| Alice    | 60000  |

**Output After:**

| emp_name | salary | first_salary | last_salary |
|----------|--------|--------------|-------------|
| Alice    | 60000  | 60000        | 60000       |
| Bob      | 55000  | 60000        | 60000       |
| Jane     | 50000  | 60000        | 60000       |
| John     | 45000  | 60000        | 60000       |

## Concept of Frames:

- **Frames:** The set of rows within a partition, which determines the range of rows used for calculations in window functions.

## NTH_VALUE():

```sql
SELECT emp_name, salary, NTH_VALUE(salary, 2) OVER(ORDER BY salary DESC) AS second_highest_salary
FROM employees;
```

**Output Before:**

| emp_name | salary |
|----------|--------|
| John     | 45000  |
| Jane     | 50000  |
| Bob      | 55000  |
| Alice    | 60000  |

**Output After:**

| emp_name | salary | second_highest_salary |
|----------|--------|------------------------|
| Alice    | 60000  | 55000                  |
| Bob      | 55000  | 55000                  |
| Jane     | 50000  | 55000                  |
| John     | 45000  | 55000                  |

## Example #5:

```sql
SELECT emp_name, salary,
       LAG(salary) OVER(ORDER BY salary DESC) AS previous_salary,
       LEAD(salary) OVER(ORDER BY salary DESC) AS next_salary
FROM employees;
```

**Output Before:**

| emp_name | salary |
|----------|--------|
| John     | 45000  |
| Jane     | 50000  |
| Bob      | 55000  |
| Alice    | 60000  |

**Output After:**

| emp_name | salary | previous_salary | next_salary |
|----------|--------|------------------|-------------|
| Alice    | 60000  | 55000            | NULL        |
| Bob      | 55000  | 50000            | 60000       |
| Jane     | 50000  | 45000            | 55000       |
| John     | 45000  | NULL             | 50000       |

## Example #6:

```sql
SELECT emp_name, salary,
       RANK() OVER(PARTITION BY department ORDER BY salary DESC) AS department_rank
FROM employees;
```

**Output Before:**

| emp_name | salary | department |
|----------|--------|------------|
| John     | 45000  | HR         |
| Jane     | 50000  | IT         |
| Bob      | 55000  | IT         |
| Alice    | 60000  | Sales      |

**Output After:**

| emp_name | salary | department | department_rank |
|----------|--------|------------|-----------------|
| John     | 45000  | HR         | 1               |
| Jane     | 50000  | IT         | 2               |
| Bob      | 55000  | IT         | 3               |
| Alice    | 60000  | Sales      | 1               |

## Summary of the Session:

In this session, we dived deep into the realm of window functions in SQL, exploring their diverse applications. From basic aggregate functions with `OVER()` to advanced functions like `RANK()`, `DENSE_RANK()`, and `ROW_NUMBER()`, we deciphered their roles in data analysis. We demystified the concept of frames, examined functions like `FIRST_VALUE()` and `LAST_VALUE()`, and delved into the versatility of `NTH_VALUE()`. The session concluded with a practical understanding of `LAG()` and `LEAD()` for analyzing previous and next values.

Window functions add a layer of sophistication to your SQL queries, allowing you to perform complex calculations and gain deeper insights into your data. As you embark on your SQL journey, don't forget to wield the power of window functions, optimizing your analytical capabilities.

Happy querying!