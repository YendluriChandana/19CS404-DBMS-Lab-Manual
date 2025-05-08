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
-- Paste Question 1 here

```sql
-- Paste your SQL code below for Question 1
```

![image](https://github.com/user-attachments/assets/647dbedb-636d-42c5-b902-1bcecd994360)


**Output:**

![image](https://github.com/user-attachments/assets/32d2f9a7-cd0c-42e3-b5c7-a4703a7e85b6)


**Question 3**
---
-- Paste Question 3 here

```sql
-- Paste your SQL code below for Question 3
```

![image](https://github.com/user-attachments/assets/a75729c2-8d27-433e-9d0d-2331cc860fd6)


**Output:**


![image](https://github.com/user-attachments/assets/c76a53ff-1bc6-42e4-ac77-52afbe8b98e8)


**Question 4**
---
-- Paste Question 4 here

```sql
-- Paste your SQL code below for Question 4
```

![image](https://github.com/user-attachments/assets/a25f6f41-5acc-4fdd-9848-ee238b2b4181)


**Output:**


![image](https://github.com/user-attachments/assets/504d67ca-8b48-4ba2-b122-2a92eef6a250)


**Question 5**
---
-- Paste Question 5 here

```sql
-- Paste your SQL code below for Question 5
```


![image](https://github.com/user-attachments/assets/066556bd-b395-49cb-86bb-1f361a9f5c2f)


**Output:**


![image](https://github.com/user-attachments/assets/b1590955-fedb-44a5-857a-0073fb85792a)


**Question 6**
---
-- Paste Question 6 here

```sql
-- Paste your SQL code below for Question 6
```

![image](https://github.com/user-attachments/assets/8646cd02-bf5d-4215-98d5-e88773dc6bd7)


**Output:**

![image](https://github.com/user-attachments/assets/06922205-9e08-4b9b-a3d8-af9aa4a1db6a)


**Question 7**
---
-- Paste Question 7 here

```sql
-- Paste your SQL code below for Question 7
```

![image](https://github.com/user-attachments/assets/7f7e7207-b62c-431c-b40c-4e750b53b633)


**Output:**


![image](https://github.com/user-attachments/assets/8c67c27e-2087-480b-bd88-df015154f3ed)



**Question 8**
---
-- Paste Question 8 here

```sql
-- Paste your SQL code below for Question 8
```

![image](https://github.com/user-attachments/assets/a866f06a-a4a1-4dec-ae24-8bcd2e3c2394)


**Output:**


![image](https://github.com/user-attachments/assets/3eda3cff-27d4-44be-9dcd-bbecc1893416)



**Question 9**
---
-- Paste Question 9 here

```sql
-- Paste your SQL code below for Question 9
```

![image](https://github.com/user-attachments/assets/a5fe3ae9-3a04-44eb-b583-df8a460a6bc0)


**Output:**


![image](https://github.com/user-attachments/assets/1f80f8bc-bc96-4973-add7-3f0b6dfc9628)



**Question 10**
---
-- Paste Question 10 here

```sql
-- Paste your SQL code below for Question 10
```

![image](https://github.com/user-attachments/assets/f2ff8ffb-46ef-45d9-8fa4-eed01aa81884)


**Output:**

![image](https://github.com/user-attachments/assets/3c11bde5-dfae-4ff9-9074-4c29e87f7023)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
