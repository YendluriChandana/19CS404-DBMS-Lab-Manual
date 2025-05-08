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
## Question 1

Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

![image](https://github.com/user-attachments/assets/ca99ba75-3f43-4b06-bc86-01b8376ccc56)

```

update PRODUCTS

set reorder_lvl=reorder_lvl*0.7

where product_name like '%cream%'

and quantity>reorder_lvl;
```
## Output:

![image](https://github.com/user-attachments/assets/300c92ab-68c7-475f-b993-e13c1004adc0)


## Question 2

Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

![image](https://github.com/user-attachments/assets/de29b555-7708-40f4-9edc-7e11d3bdb360)

```
update Suppliers

set address= '58 Lakeview, Magnolia'

where supplier_id=5;
```
## Output:

![image](https://github.com/user-attachments/assets/52779475-0939-4242-b557-7b36eb5ad7ae)

## Question 3

Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

![image](https://github.com/user-attachments/assets/a1294f9f-6a89-47e5-bc49-f569770cdc43)

```
update Products

set sell_price=sell_price*1.15

where quantity<50

and supplier_id=10;
```
## Output:

![image](https://github.com/user-attachments/assets/e73eea98-6729-4ed1-8fdc-18e78e440442)


## Question 4

For Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

![image](https://github.com/user-attachments/assets/24550324-b900-4471-bee5-c0571a951167)

```
update Products

set sell_price=sell_price*1.15

where quantity<50

and supplier_id=10;
```
## Output:

![image](https://github.com/user-attachments/assets/40656f7f-a8ed-4364-8d6b-6a03b4c25f0d)


## Question 5

For Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

![image](https://github.com/user-attachments/assets/d650e2f9-7e7b-4e9b-b563-f89781c60c17)

```
update SALES

set sell_price=sell_price+3

where product_id in(select product_id

from PRODUCTS

where supplier_id=4 );
```
## Output:

![image](https://github.com/user-attachments/assets/be036bc9-f7e2-44e3-9617-66786d8eb793)


## Question 6

Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

![image](https://github.com/user-attachments/assets/c0733286-73ed-4bf4-aeeb-eecdba9d04fb)

```
UPDATE Employees

set salary=salary*2

where department_id=20

and job_id like '%MAN';
```
## Output:

![image](https://github.com/user-attachments/assets/e13c1c79-763d-40d0-9cb2-92cf80124b58)


## Question 7

Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

![image](https://github.com/user-attachments/assets/db4eb244-b658-4bc7-b50e-c77a29a2542e)

```
delete from Surgeries

where surgery_date='2024-02-28';
```
## Output:

![image](https://github.com/user-attachments/assets/9b43c798-c59e-4023-ac35-4dd5ae32a5a0)


## Question 8

Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

![image](https://github.com/user-attachments/assets/ce8198dd-0759-4717-af2d-24b178dfa9a4)

```
delete from Customer

where CUST_CITY!='New York'

and OUTSTANDING_AMT>5000;
```
## Output:

![image](https://github.com/user-attachments/assets/c4c9fad6-09a3-4e0e-99e4-fdcb0fcf1fc9)


## Question 9

Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.

![image](https://github.com/user-attachments/assets/3782bedc-5b50-46fd-bc96-7de435b15f70)

```
delete from Doctors

where Specialization in ('Pediatrics','Cardiology')

and last_name like '%Brown%';
```
## Output:

![image](https://github.com/user-attachments/assets/577d8cee-6808-48c0-81d7-2883b6fb5ef3)


## Question 10

Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

![image](https://github.com/user-attachments/assets/a8cdd413-2d94-4597-a26c-e364f7939174)

```
delete from Customer

where GRADE>=2;
```
## Output:

![image](https://github.com/user-attachments/assets/fba2d683-405d-427f-92a2-0f329b80235b)



## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
