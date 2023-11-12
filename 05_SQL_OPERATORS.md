# Unraveling SQL Operators: A Comprehensive Guide

In the vast landscape of SQL, mastering operators is like acquiring a diverse set of tools for manipulating and extracting information from your database. Let's embark on a journey through arithmetic, bitwise, comparison, logical, and string operators, exploring their syntax and real-world applications.

## Arithmetic Operators:

### Addition Operator `+`:

The addition operator sums up numeric values.

```sql
SELECT 5 + 4;
-- Result: 9
```

### Subtraction Operator `-`:

Subtracts one number from another.

```sql
SELECT 10 - 11;
-- Result: -1
```

### Multiplication Operator `*`:

Multiplies two numbers together.

```sql
SELECT 10 * 10;
-- Result: 100
```

### Division Operator `/`:

Divides one numeric value by another.

```sql
SELECT 10 / 2;
-- Result: 5
```

### Remainder/Modulus `%`:

Returns the remainder of one number divided by another.

```sql
SELECT 10 % 4;
-- Result: 2
```

## Bitwise Operators:

### Bitwise AND `&`:

Performs a bit-by-bit comparison, returning 1s where both input expressions have 1s.

```sql
SELECT 5 & 3;
-- Result: 1
```

### Bitwise OR `|`:

Performs a bit-by-bit comparison, returning 1s where either input expression has 1s.

```sql
SELECT 5 | 3;
-- Result: 7
```

### Bitwise XOR `^`:

Performs a bit-by-bit comparison, returning 1s where either input expression has 1s but not both.

```sql
SELECT 5 ^ 3;
-- Result: 6
```

### Bitwise NOT `~`:

Inverts all bits of an expression, changing 0s to 1s and vice versa.

```sql
SELECT ~3;
-- Result: -4
```

### Left Shift `<<`:

Shifts all bits to the left by a specified number of positions.

```sql
SELECT 5 << 1;
-- Result: 10
```

### Right Shift `>>`:

Shifts all bits to the right by a specified number of positions.

```sql
SELECT 5 >> 1;
-- Result: 2
```

## Comparison Operators:

Consider a table named `Employees`:

| ID | Name   | SALARY |
|----|--------|--------|
| 1  | John   | 45000  |
| 2  | Jane   | 50000  |
| 3  | Bob    | 55000  |
| 4  | Alice  | 60000  |

### Equal to `=`:

Returns true if two expressions are equal.

```sql
SELECT Name FROM Employees WHERE SALARY = 50000;
-- Result: Jane
```

### Not equal to `<>` or `!=`:

Returns true if two expressions are not equal.

```sql
SELECT Name FROM Employees WHERE SALARY != 50000;
-- Result: John, Bob, Alice
```

### Greater than `>`:

Returns true if the first expression is greater than the second.

```sql
SELECT Name FROM Employees WHERE SALARY > 50000;
-- Result: Bob, Alice
```

### Less than `<`:

Returns true if the first expression is less than the second.

```sql
SELECT Name FROM Employees WHERE SALARY < 50000;
-- Result: John
```

### Greater than or equal to `>=`:

Returns true if the first expression is greater than or equal to the second.

```sql
SELECT Name FROM Employees WHERE SALARY >= 55000;
-- Result: Bob, Alice
```

### Less than or equal to `<=`:

Returns true if the first expression is less than or equal to the second.

```sql
SELECT Name FROM Employees WHERE SALARY <= 50000;
-- Result: John, Jane
```

## Logical Operators:

Consider a table named `users`:

| first_name | last_name | age | location |
|------------|-----------|-----|----------|
| John       | Doe       | 35  | New York  |
| Jane       | Smith     | 40  | London   |
| Bob        | Johnson   | 45  | Paris    |
| Alice      | Brown     | 50  | London   |
| Charlie    | Wilson    | 30  | Tokyo    |

### ALL Operator:

Returns TRUE if all subquery values meet the specified condition.

```sql
SELECT first_name, last_name, age, location 
FROM users 
WHERE age > ALL (SELECT age FROM users WHERE location = 'London');
-- Result: Bob Johnson (45, Paris) and Alice Brown (50, London)
```

### ANY/SOME Operator:

Returns TRUE if any subquery values meet the specified condition.

```sql
SELECT first_name 
FROM users 
WHERE age > ANY (SELECT age FROM users);
-- Result: John, Jane, Bob, Alice
```

### AND Operator:

Returns TRUE if all conditions separated by AND are true.

```sql
SELECT * 
FROM users 
WHERE age = 50 AND location = 'London';
-- Result: Alice Brown (50, London)
```

### BETWEEN Operator:

Filters results within a specified range.

```sql
SELECT * 
FROM users 
WHERE age BETWEEN 40 AND 50;
-- Result: Jane Smith (40, London), Bob Johnson (45, Paris), Alice Brown (50, London)
```

### EXISTS Operator:

Filters data based on the presence of any record in a subquery.

```sql
SELECT * 
FROM users 
WHERE EXISTS (SELECT 1 FROM users WHERE location = 'London');
-- Result: Jane Smith (40, London), Alice Brown (50, London)
```

### IN Operator:

Includes multiple values in the WHERE clause.

```sql
SELECT * 
FROM users 
WHERE first_name IN ('Bob', 'Fred', 'Harry');
-- Result: Bob Johnson (45, Paris)
```

### NOT Operator:

Returns results if the condition or conditions are not true.

```sql
SELECT * 
FROM users 
WHERE first_name NOT IN ('Bob', 'Fred', 'Harry');
-- Result: John Doe (35, New York), Jane Smith (40, London), Alice Brown (50, London), Charlie Wilson (30, Tokyo)
```

### OR Operator:

Returns TRUE if any conditions separated by OR are true.

```sql
SELECT * 
FROM users 
WHERE age = 30 OR location = 'London';
-- Result: Jane Smith (40, London), Alice Brown (50, London), Charlie Wilson (30, Tokyo)
```

### IS NULL Operator:

Filters results with a value of NULL.

```sql
SELECT * 
FROM users 
WHERE age IS NULL;
-- Empty result, as no record has age column NULL
```

## String Operators:

Consider a table named `users`:

| first_name | last_name | age | location |
|------------|-----------|-----|----------|
| John       | Doe       | 35  | New York  |
| Jane       | Smith     | 40  | London   |
| Bob        | Johnson   | 45  | Paris    |
| Alice      | Brown     | 50

  | London   |
| Charlie    | Wilson    | 30  | Tokyo    |

### LIKE Operator:

Searches for a specified pattern in a column.

```sql
SELECT * 
FROM users 
WHERE first_name LIKE '%Bob%';
-- Result: Bob Johnson (45, Paris)
```

### NOT LIKE Operator:

Searches for a specified pattern and returns the opposite of the LIKE operator.

```sql
SELECT * 
FROM users 
WHERE first_name NOT LIKE 'J%';
-- Result: John Doe (35, New York), Jane Smith (40, London)
```

### Concatenation Operator `||`:

Combines two or more strings into a single string.

```sql
SELECT first_name || ' ' || last_name AS full_name 
FROM users;
-- Result: John Doe, Jane Smith, Bob Johnson, Alice Brown, Charlie Wilson
```

With this comprehensive guide to SQL operators, you now have a powerful toolkit to manipulate, filter, and extract valuable insights from your database. Dive into these operators, experiment with different scenarios, and elevate your SQL proficiency. 

### Happy querying!