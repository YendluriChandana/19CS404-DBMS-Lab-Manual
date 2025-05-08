# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```
## Question 1

Write a SQL query to List departments with names longer than the average length

Departments Table
```
SELECT department_id,department_name
from Departments
WHERE LENGTH (department_name)>
(
SELECT AVG(LENGTH(department_name))
FROM Departments
)
```
## Output:

![image](https://github.com/user-attachments/assets/9c2b4ba1-9a2c-45e9-be67-8ce4805a1adb)

## Question 2

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $1500.

Sample table: CUSTOMERS

ID NAME AGE ADDRESS SALARY

1 Ramesh 32 Ahmedabad 2000 2 Khilan 25 Delhi 1500 3 Kaushik 23 Kota 2000 4 Chaitali 25 Mumbai 6500 5 Hardik 27 Bhopal 8500 6 Komal 22 Hyderabad 4500

7 Muffy 24 Indore 10000
```
SELECT * 
FROM CUSTOMERS
WHERE SALARY > 1500;
```
## Output:

![image](https://github.com/user-attachments/assets/9017092a-5f4d-44cd-b5cb-2934dfdede2e)

## Question 3

Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh
```
SELECT id,name,age,city,income
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 250000
);
```
## Output:

![image](https://github.com/user-attachments/assets/88b58130-9f3d-43ca-8a5e-66c92be7baa3)


## Question 4

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30

Sample table: CUSTOMERS

ID NAME AGE ADDRESS SALARY

1 Ramesh 32 Ahmedabad 2000 2 Khilan 25 Delhi 1500 3 Kaushik 23 Kota 2000 4 Chaitali 25 Mumbai 6500 5 Hardik 27 Bhopal 8500 6 Komal 22 Hyderabad 4500

7 Muffy 24 Indore 10000
```
SELECT * 
FROM CUSTOMERS
WHERE AGE < 30;
```
## Output:

![image](https://github.com/user-attachments/assets/8e85abe6-f548-4b96-824a-b62351a0960b)


## Question 5

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

Sample table: CUSTOMERS

ID NAME AGE ADDRESS SALARY

1 Ramesh 32 Ahmedabad 2000 2 Khilan 25 Delhi 1500 3 Kaushik 23 Kota 2000 4 Chaitali 25 Mumbai 6500 5 Hardik 27 Bhopal 8500 6 Komal 22 Hyderabad 4500

7 Muffy 24 Indore 10000
```
SELECT * 
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';
```
## Output:

![image](https://github.com/user-attachments/assets/dd3796a3-784b-41ab-893a-89eb6737decc)


## Question 6

From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.

salesman table

name type

salesman_id numeric(5) name varchar(30) city varchar(15) commission decimal(5,2)

customer table

name type

customer_id int cust_name text city text grade int salesman_id int
```
SELECT s.salesman_id, s.name
FROM salesman s
JOIN customer c ON s.salesman_id = c.salesman_id
GROUP BY s.salesman_id, s.name
HAVING COUNT(c.customer_id) > 1;
```
## Output:

![image](https://github.com/user-attachments/assets/1458d098-6564-40e7-bbbb-ffbc8e43eb7e)

## Question 7

Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.

salesman table

name type

salesman_id numeric(5) name varchar(30) city varchar(15) commission decimal(5,2)

customer table

name type

customer_id int cust_name text city text grade int salesman_id int
```
SELECT *
FROM customer
WHERE customer_id = (
    SELECT s.salesman_id - 2001
    FROM salesman s
    WHERE s.name = 'Mc Lyon'
);
```
## Output:
![image](https://github.com/user-attachments/assets/742cf297-f16d-4b35-88c3-cdf5c7a0905b)

## Question 8

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.

Sample table: CUSTOMERS
```

ID NAME AGE ADDRESS SALARY

1 Ramesh 32 Ahmedabad 2000 2 Khilan 25 Delhi 1500 3 Kaushik 23 Kota 2000 4 Chaitali 25 Mumbai 6500 5 Hardik 27 Bhopal 8500 6 Komal 22 Hyderabad 4500

7 Muffy 24 Indore 10000

SELECT * 
FROM CUSTOMERS
WHERE SALARY > 4500;
```
## Output:

![image](https://github.com/user-attachments/assets/7903a549-fb9c-4932-88b3-4b1735558c01)


## Question 9

Write a SQL query to Retrieve the names of customers who have a phone number that is not shared with any other customer.

SAMPLE TABLE: customer
```
name type

id INTEGER name TEXT city TEXT email TEXT phone INTEGER

SELECT name
FROM customer
WHERE phone NOT IN (
    SELECT phone
    FROM customer
    GROUP BY phone
    HAVING COUNT(*) > 1
);
```
## Output:

![image](https://github.com/user-attachments/assets/900910f6-3933-425a-b130-072719d12729)


## Question 10

Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.
```
SELECT *
FROM Grades g
WHERE grade = (
    SELECT MAX(grade)
    FROM Grades
    WHERE subject = g.subject
    GROUP BY subject
);
```
## Output:

![image](https://github.com/user-attachments/assets/23ef9db0-bfb8-4961-a51d-4a5567393b20)


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
