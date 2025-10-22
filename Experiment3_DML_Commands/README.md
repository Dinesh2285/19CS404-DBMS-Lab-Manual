# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
UPDATE Employees
SET hire_date = '2024-01-24'
WHERE department_id = 50;

```

**Output:**

<img width="956" height="138" alt="image" src="https://github.com/user-attachments/assets/7285bee2-f436-43cf-9a2a-140d335e309d" />


**Question 2**
---
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
UPDATE PRODUCTS
SET reorder_lvl = 40
WHERE category = 'Grocery';

```

**Output:**

<img width="775" height="224" alt="image" src="https://github.com/user-attachments/assets/26207eb5-dd0c-4dde-bebf-d37e5fb08354" />

**Question 3**
---
Update the 'Selling_Price' to add 10% extra margin for all products supplied by the supplier with id 6.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql

UPDATE PRODUCTS
SET sell_price = ROUND(sell_price * 1.10, 0)
WHERE supplier_id = 6;

```

**Output:**

<img width="735" height="333" alt="image" src="https://github.com/user-attachments/assets/431deccf-4500-4408-a710-9beda67294ed" />

**Question 4**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
UPDATE Employees
SET salary = salary * 2
WHERE department_id = 20
  AND job_id LIKE '%MAN';

```

**Output:**

<img width="856" height="186" alt="image" src="https://github.com/user-attachments/assets/e009d58d-178f-42bb-8849-6663a6deb7e7" />

**Question 5**
---
Write a SQL statement to change salary of employee to 8000 whose Employee ID is 105, if the existing salary is less than 5000.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
UPDATE Employees
SET salary = 8000
WHERE employee_id = 105 AND salary < 5000;

```

**Output:**

<img width="723" height="101" alt="image" src="https://github.com/user-attachments/assets/0ffd5105-8a5d-48ae-950c-f763671918c4" />

**Question 6**
---
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date

```sql
DELETE FROM Surgeries
WHERE surgery_date = '2024-02-28';

```

**Output:**

<img width="922" height="213" alt="image" src="https://github.com/user-attachments/assets/345a9ff6-3cdc-4dad-a15e-5a36f4d27ff0" />

**Question 7**
---

Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.


```sql

DELETE FROM customer
WHERE GRADE != 3;

```

**Output:**

<img width="484" height="332" alt="image" src="https://github.com/user-attachments/assets/af2d2fb2-8552-40dd-8786-4ea3f61bd616" />

**Question 8**
---
Write a SQL query to Delete customers with 'CUST_COUNTRY' 'UK' and 'WORKING_AREA' 'London' whose 'GRADE' is less than 3

```sql

DELETE FROM Customer
WHERE CUST_COUNTRY = 'UK'
  AND WORKING_AREA = 'London'
  AND GRADE < 3;

```

**Output:**

<img width="1090" height="281" alt="image" src="https://github.com/user-attachments/assets/98a8e514-58b1-402d-baa2-441229ff1c7f" />

**Question 9**
---
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM Doctors
WHERE doctor_id = 1;

```

**Output:**

<img width="928" height="118" alt="image" src="https://github.com/user-attachments/assets/e70855a8-d249-4961-8b74-8da63cc16d2c" />

**Question 10**
---

Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

```sql

DELETE FROM Customer
WHERE CUST_CITY != 'New York'
  AND OUTSTANDING_AMT > 5000;

```

**Output:**

<img width="1087" height="369" alt="image" src="https://github.com/user-attachments/assets/1459d31d-a182-47ed-9054-aff5a259b85e" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
