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

![438551416-1ff73ec5-f6a1-4e70-9010-161c6f3772f6](https://github.com/user-attachments/assets/c1464946-e338-4482-a37a-9e974707c8d0)


```sql
INSERT INTO Employee(EmployeeID,Name,Position)
values(5,           'George Clark',  'Consultant');

INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
values(7,           'Noah Davis',    'Manager',     'HR',          60000);

INSERT INTO Employee(EmployeeID,Name,Position,Department)
values(8,           'Ava Miller',    'Consultant',  'IT');
```

**Output:**

![Screenshot 2025-04-29 135905](https://github.com/user-attachments/assets/f09cfe13-4c32-4525-88b5-200cc62db38c)


**Question 2**

![Screenshot 2025-04-29 135957](https://github.com/user-attachments/assets/89362ef2-7347-4a99-aa1c-7021ecc12fc0)


```sql
CREATE TABLE Attendance (  
    AttendanceID INTEGER PRIMARY KEY,  
    EmployeeID INTEGER,  
    AttendanceDate DATE,  
    Status TEXT CHECK (Status IN ('Present', 'Absent', 'Leave')),  
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)  
);
```

**Output:**

![Screenshot 2025-04-29 140044](https://github.com/user-attachments/assets/ea7d306d-ccae-4760-b795-fd6d95471246)

**Question 3**

![Screenshot 2025-04-29 140105](https://github.com/user-attachments/assets/c356bc6b-95e8-4e1a-ab15-993de8bfb0e7)


```sql
ALTER TABLE Employees
ADD COLUMN Date_of_joining Date;

ALTER TABLE Employees
RENAME COLUMN job_title To Designation;
```

**Output:**

![Screenshot 2025-04-29 140140](https://github.com/user-attachments/assets/540a0cd5-1c58-44a6-b5d1-461c2f1d3061)

**Question 4**

![Screenshot 2025-04-29 140203](https://github.com/user-attachments/assets/835d84fe-f0d1-47e9-8237-21adedcb9ef8)

```sql
 CREATE TABLE jobs (  
    job_id INTEGER PRIMARY KEY,  
    job_title TEXT NOT NULL DEFAULT '',  
    min_salary INTEGER NOT NULL DEFAULT 8000,  
    max_salary INTEGER DEFAULT NULL  
);
```

**Output:**

![Screenshot 2025-04-29 140239](https://github.com/user-attachments/assets/5b8aa32d-a4d8-4031-9fbb-8245826c8c15)

**Question 5**

![Screenshot 2025-04-29 140257](https://github.com/user-attachments/assets/16ca9945-2244-4155-98c0-e372f37d5549)


```sql
CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
```

**Output:**

![Screenshot 2025-04-29 140326](https://github.com/user-attachments/assets/029c84ce-53fa-44e5-bb01-265bbb42c218)

**Question 6**

![Screenshot 2025-04-29 140343](https://github.com/user-attachments/assets/4dfff7cf-c343-49db-a90e-50b9887375b3)


```sql
select *from Out_of_print_books
union all
select *from Books
```

**Output:**

![Screenshot 2025-04-29 140412](https://github.com/user-attachments/assets/ef84a6de-e751-4f35-9ca6-47f67bb25f98)

**Question 7**

![Screenshot 2025-04-29 140429](https://github.com/user-attachments/assets/91973c99-84ed-4c37-b54d-80aa249be42a)


```sql
CREATE TABLE item (  
    item_id TEXT PRIMARY KEY,  
    item_desc TEXT NOT NULL,  
    rate INTEGER NOT NULL,  
    icom_id TEXT CHECK(4),  
    FOREIGN KEY (icom_id) REFERENCES company(com_id)  
    ON UPDATE CASCADE  
    ON DELETE CASCADE  
);
```

**Output:**

![Screenshot 2025-04-29 140458](https://github.com/user-attachments/assets/6bd2fef6-e71f-44d2-942f-18d6f69a3c32)

**Question 8**

![Screenshot 2025-04-29 140518](https://github.com/user-attachments/assets/64410896-26df-4cd7-8ea8-5b2c3597619a)


```sql
ALTER TABLE employee
ADD COLUMN designation varchar(50);
```

**Output:**

![Screenshot 2025-04-29 140542](https://github.com/user-attachments/assets/24b23b95-201e-4b61-9bc7-488b29aaa32f)

**Question 9**

![Screenshot 2025-04-29 140600](https://github.com/user-attachments/assets/b0d4226a-12ac-4680-ace3-50a728b10b23)


```sql
INSERT INTO Products (ProductID, Name, Category)  
VALUES (104, 'Tablet', 'Electronics');
```

**Output:**

![Screenshot 2025-04-29 140627](https://github.com/user-attachments/assets/3deaf30b-c9fc-4c55-9e06-1df30e22f006)

**Question 10**

![Screenshot 2025-04-29 140646](https://github.com/user-attachments/assets/d9f81474-362b-46a5-8aad-c574d2a73add)


```sql
CREATE TABLE Employees(
EmployeeID INTEGER primary key,
FirstName INTEGER NOT NULL,
LastName INTEGER NOT NULL,
Email VARCHAR(50) unique,
Salary CHECK (Salary>0),
DepartmentID INTEGER,
foreign key(DepartmentID) references Departments(DepartmentID)
);
```

**Output:**

![Screenshot 2025-04-29 140715](https://github.com/user-attachments/assets/09ac0268-5a30-4a0c-813b-c381b28b1dd6)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
