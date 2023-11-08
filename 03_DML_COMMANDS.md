## 03_DML_COMMANDS
# DML COMMANDS
Let's break down DML(Data Manipulation Language) commands, its syntax, and illustrate the before and after effects with tables.

## **Summary of CRUD:**

### **INSERT Query:**

#### **INSERT query:**
Adds new records to a table.

```sql
INSERT INTO Students (StudentID, Name, Age) VALUES (1, 'Alice', 20);
```

Before:
| StudentID | Name  | Age |
|-----------|-------|-----|
|           |       |     |

After:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alice | 20  |

#### **INSERT query variation:**
Variations of the INSERT query for different scenarios.

```sql
INSERT INTO Students (Name, Age) VALUES ('Bob', 22);
```

Before:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alice | 20  |

After:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alice | 20  |
|           | Bob   | 22  |

#### **INSERT multiple values:**
Inserts multiple records in a single query.

```sql
INSERT INTO Students (Name, Age) VALUES ('Charlie', 21), ('David', 23);
```

Before:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alice | 20  |
| 2         | Bob   | 22  |

After:
| StudentID | Name    | Age |
|-----------|---------|-----|
| 1         | Alice   | 20  |
| 2         | Bob     | 22  |
|           | Charlie | 21  |
|           | David   | 23  |

### **SELECT Query:**

#### **Import data into MySQL Workbench:**
Bringing external data into the database.

Before:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alice | 20  |
| 2         | Bob   | 22  |

After (with imported data):
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alice | 20  |
| 2         | Bob   | 22  |
| 3         | Carol | 25  |
| 4         | Dave  | 23  |

#### **SELECT all columns:**
Retrieves all columns from a table.

```sql
SELECT * FROM Students;
```

Result:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alice | 20  |
| 2         | Bob   | 22  |
| 3         | Carol | 25  |
| 4         | Dave  | 23  |

#### **Filter columns:**
Selects specific columns.

```sql
SELECT Name, Age FROM Students;
```

Result:
| Name  | Age |
|-------|-----|
| Alice | 20  |
| Bob   | 22  |
| Carol | 25  |
| Dave  | 23  |

#### **Alias | Renaming columns:**
Renames columns using aliases.

```sql
SELECT Name AS StudentName, Age AS StudentAge FROM Students;
```
`Explanation`: This renames the Name column as StudentName and the Age column as StudentAge for better clarity.

Result:
| StudentName | StudentAge |
|-------------|------------|
| Alice       | 20         |
| Bob         | 22         |
| Carol       | 25         |
| Dave        | 23         |

#### **Create expression using columns:**
Performs calculations within the SELECT statement.

```sql
SELECT Name, Age, Age + 5 AS FutureAge FROM Students;
```

`Result`:
| Name  | Age | FutureAge |
|-------|-----|-----------|
| Alice | 20  | 25        |
| Bob   | 22  | 27        |
| Carol | 25  | 30        |
| Dave  | 23  | 28        |

#### **Constant value:**
Includes constant values in the result.

```sql
SELECT Name, 'Adult' AS AgeGroup FROM Students WHERE Age >= 18;
```

Result:
| Name  | AgeGroup |
|-------|----------|
| Alice | Adult    |
| Bob   | Adult    |
| Carol | Adult    |
| Dave  | Adult    |

#### **DISTINCT (unique) values from a column:**
Retrieves unique values from a column.

```sql
SELECT DISTINCT Age FROM Students;
```

Result:
| Age |
|-----|
| 20  |
| 22  |
| 25  |
| 23  |

#### **DISTINCT combinations:**
Retrieves unique combinations of columns.

```sql
SELECT DISTINCT Name, Age FROM Students;
```

Result:
| Name  | Age |
|-------|-----|
| Alice | 20  |
| Bob   | 22  |
| Carol | 25  |
| Dave  | 23  |

#### **Filter rows WHERE clause:**
Applies conditions to filter rows.

```sql
SELECT * FROM Students WHERE Age >= 21;
```

Result:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 2         | Bob   | 22  |
| 3         | Carol | 25  |
| 4         | Dave  | 23 

 |

#### **Operator Example 1:**
Various examples utilizing operators.

#### **Example 2 with BETWEEN operator:**
```sql
SELECT * FROM Students WHERE Age BETWEEN 20 AND 25;
```

Result:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alice | 20  |
| 2         | Bob   | 22  |
| 3         | Carol | 25  |
| 4         | Dave  | 23  |

#### **Operator Example 3:**
```sql
SELECT * FROM Students WHERE Name LIKE 'A%';
```

Result:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alice | 20  |

#### **Operator Example 4:**
```sql
SELECT * FROM Students WHERE Name IN ('Alice', 'Bob');
```

Result:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alice | 20  |
| 2         | Bob   | 22  |

#### **Operator Example 5:**
```sql
SELECT * FROM Students WHERE Age > 22;
```

Result:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 3         | Carol | 25  |
| 4         | Dave  | 23  |

#### **Doubt clearance:**
Clarifications on doubts.

#### **Query Execution Order:**
Explains the sequence of query execution.

### **UPDATE Query:**

#### **UPDATE Query to update row(s):**
Modifies existing records.

```sql
UPDATE Students SET Age = 25 WHERE Name = 'Alice';
```

Before:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alice | 20  |
| 2         | Bob   | 22  |
| 3         | Carol | 25  |
| 4         | Dave  | 23  |

After:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alice | 25  |
| 2         | Bob   | 22  |
| 3         | Carol | 25  |
| 4         | Dave  | 23  |

#### **Update multiple columns:**
Modifies multiple columns in a single query.

```sql
UPDATE Students SET Age = 26, Name = 'Alicia' WHERE StudentID = 1;
```

Before:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alice | 25  |
| 2         | Bob   | 22  |
| 3         | Carol | 25  |
| 4         | Dave  | 23  |

After:
| StudentID | Name   | Age |
|-----------|--------|-----|
| 1         | Alicia | 26  |
| 2         | Bob    | 22  |
| 3         | Carol  | 25  |
| 4         | Dave   | 23  |

### **DELETE Query:**

#### **DELETE Query to delete row(s):**
Removes specific records from a table.

```sql
DELETE FROM Students WHERE Age > 30;
```

Before:
| StudentID | Name   | Age |
|-----------|--------|-----|
| 1         | Alicia | 26  |
| 2         | Bob    | 22  |
| 3         | Carol  | 25  |
| 4         | Dave   | 23  |

After:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Alicia| 26  |
| 2         | Bob   | 22  |
| 3         | Carol | 25  |
| 4         | Dave  | 23  |

#### **Deletion based on multiple conditions:**
Removes records based on multiple criteria.

```sql
DELETE FROM Students WHERE Age > 25 AND Name = 'Alicia';
```

Before:
| StudentID | Name   | Age |
|-----------|--------|-----|
| 1         | Alicia | 26  |
| 2         | Bob    | 22  |
| 3         | Carol  | 25  |
| 4         | Dave   | 23  |

After:
| StudentID | Name  | Age |
|-----------|-------|-----|
| 2         | Bob   | 22  |
| 3         | Carol | 25  |
| 4         | Dave  | 23  |

### **Functions in MySQL/SQL:**

#### **Info about SQL Functions:**
Overview of SQL functions.

#### **Different aggregate functions:**

- **MAX() & MIN():**
Retrieves the maximum and minimum values.

```sql
SELECT MAX(Age) AS MaxAge, MIN(Age) AS MinAge FROM Students;
```

Result:
| MaxAge | MinAge |
|--------|--------|
| 25     | 22     |

- **AVG():**
Computes the average value.

```sql
SELECT AVG(Age) AS AverageAge FROM Students;
```

Result:
| AverageAge |
|------------|
| 23.75      |

- **SUM():**
Adds up values.

```sql
SELECT SUM(Age) AS TotalAge FROM Students;
```

Result:
| TotalAge |
|----------|
| 95       |

- **COUNT():**
Counts the number of rows.

```sql
SELECT COUNT(*) AS StudentCount FROM Students;
```

Result:
| StudentCount |
|--------------|
| 4            |

- **STD() & VARIANCE():**
Calculate standard deviation and variance.

```sql
SELECT STD(Age) AS AgeStdDev, VARIANCE(Age) AS AgeVariance FROM Students;
```

Result:
| AgeStdDev | AgeVariance |
|-----------|-------------|
| 1.7078    | 2.9167      |

#### **Different scalar functions:**

- **ABS():**
Returns the absolute value.

```sql
SELECT ABS(-5) AS AbsoluteValue;
```

Result:
| AbsoluteValue |
|---------------|
| 5             |

- **ROUND():**
Rounds a numeric value.

```sql
SELECT ROUND(5.67) AS RoundedValue;
```

Result:
| RoundedValue |
|--------------|
| 6            |

- **CEIL() & FLOOR():**
Rounds up and down to the nearest integer.

```sql
SELECT CEIL(5.1) AS CeiledValue, FLOOR(5.9) AS FlooredValue;
```

Result:
| CeiledValue | FlooredValue |
|-------------|--------------|
| 6           | 5            |

This breakdown provides a detailed explanation of each command, its syntax, and the visual representation of tables before and after the execution of the commands.

"Thanks for tuning in! Until next time, happy listening and stay curious!"
Go Godspeed!!!