# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
-- Write an SQL command can to add a column named email of type TEXT to the customers table

```sql
ALTER TABLE customers 
ADD COLUMN email TEXT;
```

**Output:**
<img width="692" height="185" alt="1op" src="https://github.com/user-attachments/assets/33b76cd2-3e3e-4880-9a6c-8e65fd2e8b5c" />


**Question 2**
---
Insert all students from Archived_students table into the Student_details table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0
```sql
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
SELECT RollNo,Name,Gender,Subject,MARKS
FROM Archived_students;
```

**Output:**

<img width="613" height="186" alt="2op" src="https://github.com/user-attachments/assets/ce5b2a9f-42d6-4d32-9127-5923e32df8f9" />

**Question 3**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
CREATE TABLE Employees(
    EmployeeID INTEGER PRIMARY KEY,
    FirstName TEXT NOT NULL,
    LastName TEXT NOT NULL,
    Email TEXT UNIQUE,
    Salary INTEGER CHECK(Salary >0),
    DepartmentID INTEGER,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="548" height="317" alt="3op" src="https://github.com/user-attachments/assets/cdb2f601-7fa7-461a-9f8d-0c529e774a6a" />

**Question 4**
---
Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```sql
CREATE TABLE Products(
    ProductID INT PRIMARY KEY,
    ProductName TEXT UNIQUE NOT NULL,
    Price REAL CHECK(Price>0),
    StockQuantity INT CHECK(StockQuantity >=0)
);
```

**Output:**

<img width="1034" height="184" alt="4op" src="https://github.com/user-attachments/assets/867a45d5-f33c-4409-9403-f54a15ebd372" />

**Question 5**
---
Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```sql
ALTER TABLE Companies ADD COLUMN designation varchar(50);

ALTER TABLE Companies ADD COLUMN net_salary number;
```

**Output:**

<img width="697" height="279" alt="5op" src="https://github.com/user-attachments/assets/2e6d7af8-f556-4e33-bca5-810dcd0a14b6" />

**Question 6**
---
In the Books table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

ISBN             Title                      Author           Publisher   Year
---------------  -------------------------  ---------------  ----------  ----------
978-1234567890   Introduction to AI         John Doe
978-9876543210   Deep Learning              Jane Doe         TechPress   2022
978-1122334455   Cybersecurity Essentials   Alice Smith                  2021

```sql
INSERT INTO Books(ISBN,Title,Author)
VALUES ('978-1234567890','Introduction to AI','John Doe');

INSERT INTO Books(ISBN,Title,Author,Publisher,Year)
VALUES('978-9876543210','Deep Learning','Jane Doe','TechPress',2022);

INSERT INTO Books(ISBN,Title,Author,Year)
VALUES('978-1122334455','Cybersecurity Essentials','Alice Smith',2021);
```

**Output:**

<img width="810" height="190" alt="6op" src="https://github.com/user-attachments/assets/cdbe4c3a-8419-4bc2-9952-a4292a610609" />

**Question 7**
---
Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT
```sql
CREATE TABLE Locations(
    LocationID INTEGER,LocationName TEXT,Address TEXT
);
```

**Output:**

<img width="723" height="281" alt="7" src="https://github.com/user-attachments/assets/0fb164a3-cca8-49e7-8fde-007bdc25481e" />

**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

```sql
DELETE FROM Customer
WHERE CUST_CITY != 'New York'
  AND OUTSTANDING_AMT > 5000;

```

**Output:**

<img width="1088" height="370" alt="8" src="https://github.com/user-attachments/assets/600585c7-aa60-4849-bc18-b72dfef02c12" />

**Question 9**
---
Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St      

Note: The City and ZipCode columns will use their default values.

```sql

INSERT INTO Customers(CustomerID,Name,Address)
VALUES(304,'Peter Parker','Spider St');

```

**Output:**

<img width="1079" height="225" alt="9" src="https://github.com/user-attachments/assets/cdce70d6-7dee-49b3-b02f-cfc17729ad70" />

**Question 10**
---
Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```sql
CREATE TABLE Products (
    ProductID INTEGER PRIMARY KEY,
    ProductName TEXT UNIQUE NOT NULL,
    Price REAL CHECK (Price > 0),
    StockQuantity INTEGER CHECK (StockQuantity >= 0)
);

```

**Output:**

<img width="778" height="128" alt="10" src="https://github.com/user-attachments/assets/6e0b7fd9-b838-4706-bc0b-04e6e0541330" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
