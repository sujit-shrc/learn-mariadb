## DDL COMMANDS
let's break down the key elements of software installation, database server setup, various SQL commands, and dive deep into the syntax and examples.

# Software Installation and Database Server Setup:

## Software Installation:

Before diving into the SQL universe, you need to install a database management system (DBMS) software. Popular choices include MySQL, PostgreSQL, and SQLite. Once installed, you can interact with these databases using SQL commands.

## Database Server Setup:

The database server is like the maestro directing the SQL orchestra. It handles requests, manages data, and ensures everything runs smoothly. Configuring a database server involves setting parameters such as port numbers, access controls, and security features.

# Types of SQL Commands:

## SQL Start:

SQL, or Structured Query Language, is the language used to interact with databases. It allows you to manage and manipulate data. Let's dive into various types of SQL commands:

## DDL Commands for Database - Create and Drop:

### `CREATE DATABASE`:
Creates a new database.

```sql
CREATE DATABASE MyDatabase;
```

### `DROP DATABASE`:
Deletes an existing database.

```sql
DROP DATABASE MyDatabase;
```

## DDL Commands for Table:

### `CREATE TABLE`:
Defines a new table with specified columns and data types.

```sql
CREATE TABLE Employees (
    EmployeeID INT,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    PRIMARY KEY (EmployeeID)
);
```

### `TRUNCATE TABLE`:
Removes all records from a table but retains the structure for future use.

```sql
TRUNCATE TABLE Employees;
```

### `DROP TABLE`:
Deletes an existing table.

```sql
DROP TABLE Employees;
```

## Data Integrity:

Data integrity ensures the accuracy and consistency of data in a database. Constraints play a crucial role in maintaining data integrity.

### Constraints:

### `NOT NULL` - Constraints:
Ensures a column cannot have a NULL value.

```sql
CREATE TABLE Students (
    StudentID INT NOT NULL,
    Name VARCHAR(50) NOT NULL
);
```

### `UNIQUE` - Constraints:
Ensures that all values in a column are unique.

```sql
CREATE TABLE Products (
    ProductID INT UNIQUE,
    ProductName VARCHAR(50)
);
```

### Another Way of Making Constraints:

```sql
CREATE TABLE Orders (
    OrderID INT,
    CustomerID INT,
    CONSTRAINT PK_Orders PRIMARY KEY (OrderID),
    CONSTRAINT FK_CustomerID FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

### `PRIMARY KEY` - Constraints:
Specifies a column as the primary key.

```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50)
);
```

### `AUTO INCREMENT` - Constraints:
Automatically increments the column value.

```sql
CREATE TABLE Employees (
    EmployeeID INT AUTO_INCREMENT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50)
);
```

### `CHECK` - Constraints:
Ensures that the values in a column meet a specific condition.

```sql
CREATE TABLE Employees (
    Salary INT CHECK (Salary > 0),
    Department VARCHAR(50)
);
```

### Defaults:

Sets a default value for a column.

```sql
CREATE TABLE Students (
    Grade CHAR DEFAULT 'A',
    Subject VARCHAR(50)
);
```

### `FOREIGN KEY`:
Establishes a link between two tables.

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    ProductID INT,
    FOREIGN KEY (ProductID) REFERENCES Products(ProductID)
);
```

## Referential Actions:

### `CASCADE`:
Specifies that changes in the referenced key column will cascade to the referencing column.

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    ProductID INT,
    FOREIGN KEY (ProductID) REFERENCES Products(ProductID) ON DELETE CASCADE
);
```

## `ALTER TABLE` Command:

Alters an existing table, allowing you to modify its structure.

### Adding and Deleting - Constraints:

#### Adding a Column:

```sql
ALTER TABLE Employees
ADD COLUMN Birthdate DATE;
```

#### Deleting a Column:

```sql
ALTER TABLE Employees
DROP COLUMN Birthdate;
```

These SQL commands are the building blocks of database management, allowing you to create, modify, and maintain databases with precision and control. Understanding their syntax and applications empowers you to wield the full potential of relational databases.


"Thanks for tuning in! Until next time, happy listening and stay curious!"
Go Godspeed!!!
