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

![438609158-53b5f3b9-c9b6-4e2b-a010-2876d7e71d58](https://github.com/user-attachments/assets/05b644bf-878c-4bbf-83c9-ef1df67c2bf3)


```sql
INSERT INTO Customers(CustomerID  ,Name, Address, Email)
SELECT CustomerID ,Name ,Address, Email FROM Old_customers;
```

**Output:**

![438610221-8cb31551-6831-454d-b418-edd48d7eb67f](https://github.com/user-attachments/assets/c8ee6f15-b7f5-40ce-9236-86f40d8ae302)

**Question 2**

![438613114-1f0eb809-77c1-44ef-afa2-8421dcb11740](https://github.com/user-attachments/assets/747472a4-2847-49c5-b6ef-3ba10a7310d8)


```sql
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id =4;
```

**Output:**

![438613192-fac16b56-8a39-4f79-85ce-bbb4c7e859c6](https://github.com/user-attachments/assets/4940badd-f9a1-435c-9bf2-6137c5e43fb9)

**Question 3**

![438613851-777ae485-23f4-4483-8715-29b910b9a718](https://github.com/user-attachments/assets/fb082927-8207-4d91-8962-ba6532dbe608)


```sql
DELETE FROM surgeries
WHERE  surgery_id =3;
```

**Output:**

![Screenshot 2025-04-29 141500](https://github.com/user-attachments/assets/a260c5a2-9b1d-4cd3-9d42-2e82fd238f4c)

**Question 4**

![image](https://github.com/user-attachments/assets/ccb5e276-48bf-4ce0-9a4b-9508a80f00c3)


```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM  customer
WHERE  grade >100;
```

**Output:**

![image](https://github.com/user-attachments/assets/567c7e88-e0db-4571-9eff-6956de9f3567)

**Question 5**

![image](https://github.com/user-attachments/assets/6a008f52-7e8d-4fa5-847f-f126a14fd26c)


```sql
SELECT ename,hiredate,DATE(hiredate ,'+100 Days') AS DateAfter100Days
FROM emp;
```

**Output:**

![image](https://github.com/user-attachments/assets/e5fea501-acd8-49ab-b033-5cf66ceca032)

**Question 6**

![image](https://github.com/user-attachments/assets/95288ceb-812c-4279-b48e-a7066b2dca77)


```sql
SELECT id,ROUND(decimal,3) AS  rounded_value
FROM Calculations;
```

**Output:**

![image](https://github.com/user-attachments/assets/b5d1e8f0-fdf0-40ca-b457-09f0e1d8eb0f)

**Question 7**

![image](https://github.com/user-attachments/assets/ed21dfcf-b669-4798-b669-5988eb66daad)


```sql
DELETE FROM Customer
WHERE LENGTH(CUST_NAME) =6;
```

**Output:**

![image](https://github.com/user-attachments/assets/9f20ae12-2d3e-4709-8af7-3ee196c3e9d6)

**Question 8**

![image](https://github.com/user-attachments/assets/93bc0611-3395-4e2e-9b92-18feec5e9be8)


```sql
UPDATE Employees 
SET salary = 8000
WHERE employee_id =105 AND salary < 5000;
```

**Output:**

![image](https://github.com/user-attachments/assets/2bc755f2-fdc9-4e0a-9900-28035de25c02)

**Question 9**

![image](https://github.com/user-attachments/assets/99207994-013e-4150-9607-50e32297efae)


```sql
SELECT id, value1, 
        CASE 
           WHEN  value1 >50 THEN 'High'
           ELSE 'Low'
        END AS  value_category
FROM Calculations;

```

**Output:**

![image](https://github.com/user-attachments/assets/1dd14d63-6e2c-4f91-a9c8-891abcc97366)

**Question 10**

![image](https://github.com/user-attachments/assets/01b9fc8a-3f69-468d-be57-35afa29395cd)


```sql
SELECT 
    product_id, 
    original_price, 
    discount_percentage,
    original_price *discount_percentage AS discount_amount
FROM 
    products
WHERE  
    original_price * discount_percentage >50;
```

**Output:**

![image](https://github.com/user-attachments/assets/59698e25-d6aa-4b62-96de-0aac3253b12b)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
