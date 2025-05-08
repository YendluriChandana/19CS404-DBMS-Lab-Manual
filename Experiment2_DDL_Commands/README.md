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
## Question 1

Write a SQL query to Add a new column State as text in the Student_details table.

![image](https://github.com/user-attachments/assets/5d7a6e5b-6ba2-4240-ba1d-31b29547c97d)

```
ALTER TABLE Student_details ADD COLUMN State TEXT;
```
## Output:

![image](https://github.com/user-attachments/assets/6cb003d0-87bb-40da-acf7-862494137d13)


## Question 2

Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values. 
![image](https://github.com/user-attachments/assets/92d97d2d-2ac7-41a1-a214-ec27805eea0b)

```
INSERT INTO Employee(EmployeeID,Name,Position)

VALUES('4','Emily White','Analyst');
```
## Output:

![image](https://github.com/user-attachments/assets/a649c323-ee4c-4822-a92a-ded1248aaea7)


## Question 3

Insert all employees from Former_employees into Employee

![image](https://github.com/user-attachments/assets/9a26979b-f501-4972-a478-3a6a9ac7480d)

```
INSERT into Employee(EmployeeID,Name,Department,Salary)

SELECT EmployeeID,Name,Department,Salary FROM Former_employees;
```
## Output:

![image](https://github.com/user-attachments/assets/39b5e8e3-c901-4c79-8a75-d1e5b2fe4d66)


## Question 4

Create a table named Customers with the following columns:

![image](https://github.com/user-attachments/assets/e31d57bc-0014-41be-a17d-9bf087eb4244)

```
CREATE TABLE Customers(

CustomerID INTEGER,

Name TEXT,

Email TEXT,

JoinDate DATETIME );
```
## Output:

![image](https://github.com/user-attachments/assets/f409977b-05f5-48f8-8580-61d4b5b82d87)


## Question 5

Write an SQL query to add a new column email of type TEXT to the Student_details table, and ensure that this column cannot contain NULL values and make default value as 'Invalid'

![image](https://github.com/user-attachments/assets/c19b5fdf-4c75-40a8-baa4-2061818b5f86)

```
ALTER TABLE Student_details

ADD COLUMN email TEXT not NULL default'Invalid';
```
## Output:

![image](https://github.com/user-attachments/assets/b72df767-0517-43bf-9466-4bce8d4810af)


## Question 6

Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.

InvoiceDate as DATE.

Amount as REAL should be greater than 0.

DueDate as DATE should be greater than the InvoiceDate.

OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

![image](https://github.com/user-attachments/assets/6a0f1456-613e-482c-8cab-8910e4a73b40)

```

CREATE TABLE Invoices(

InvoiceID INTEGER primary key,

InvoiceDate DATE,

Amount REAL CHECK(Amount>=0),

DueDate DATE CHECK(DueDate>=InvoiceDate),

OrderID INTEGER,

foreign key (OrderID) references Orders(OrderID) );
```
## Output:

![image](https://github.com/user-attachments/assets/dba9a422-8b10-45f2-9c68-43709ab5a7dc)


## Question 7

Create a table named Products with the following constraints:

ProductID should be the primary key.

ProductName should be NOT NULL.

Price is of real datatype and should be greater than 0.

Stock is of integer datatype and should be greater than or equal to 0.

![image](https://github.com/user-attachments/assets/9b287a80-c907-45e8-ac08-7a8f535b9939)

```
CREATE TABLE Products(

ProductID INTEGER primary key,

ProductName not NULL,

Price REAL CHECK (Price>0),

Stock INTEGER CHECK (Stock>=0) );
```
## Output:

![image](https://github.com/user-attachments/assets/a36440d7-80dc-49b4-819d-b0e426d31300)


## Question 8

Create a table named Orders with the following constraints:

OrderID as INTEGER should be the primary key.

OrderDate as DATE should be not NULL.

CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

![image](https://github.com/user-attachments/assets/5e497072-364f-45fa-b7b6-cc4b13a4821b)

```

CREATE TABLE Orders(

OrderID INTEGER primary key,

OrderDate DATE not NULL,

CustomerID INTEGER,

foreign key (CustomerID) references Customers(CustomerID) );
```
## Output:

![image](https://github.com/user-attachments/assets/88efbb72-0399-4e32-956e-23e0571d2461)


## Question 9

Create a table named Department with the following constraints:

DepartmentID as INTEGER should be the primary key.

DepartmentName as TEXT should be unique and not NULL.

Location as TEXT.

![image](https://github.com/user-attachments/assets/5708326b-6921-488d-bebe-1e9803f012f4)

```

CREATE TABLE Department(

DepartmentID INTEGER primary key,

DepartmentName TEXT UNIQUE not NULL,

Location TEXT );
```
## Output:

![image](https://github.com/user-attachments/assets/cfd3f219-8056-4f1e-ab86-6df451ca81f2)


## Question 10

In the Books table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

![image](https://github.com/user-attachments/assets/8d173306-7768-4b0d-a52f-fd0262039a3c)

```
INSERT INTO Books(ISBN, Title, Author, Publisher, Year)

VALUES('978-1234567890', 'Introduction to AI', 'John Doe', null, null);

INSERT INTO Books(ISBN, Title, Author, Publisher, Year)

VALUES('978-9876543210', 'Deep Learning', 'Jane Doe', 'TechPress', '2022');

INSERT INTO Books(ISBN, Title, Author, Publisher, Year)

VALUES('978-1122334455', 'Cybersecurity Essentials', 'Alice Smith', null, 2021);
```
## Output:

![image](https://github.com/user-attachments/assets/447fed2c-d41a-43a0-9630-836df4125802)

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
