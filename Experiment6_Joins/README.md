# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

## Question 1 
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c") and the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the same city as the salesman.
```
SELECT 
    c.cust_name AS "cust_name",
    s.name AS "name"
FROM 
    customer c
LEFT JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city = s.city;
```
Output:

![image](https://github.com/user-attachments/assets/ff9ed027-cec3-4a3b-8d9f-22e3399b2d8e)


## Question 2
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

Sample table: customer

customer_id | cust_name | city | grade | salesman_id -------------+----------------+------------+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002 3008 | Julian Green | London | 300 | 5002 3004 | Fabian Johnson | Paris | 300 | 5006 3009 | Geoff Cameron | Berlin | 100 | 5003 3003 | Jozy Altidor | Moscow | 200 | 5007 3001 | Brad Guzan | London | | 5005 Sample table: orders

ord_no purch_amt ord_date customer_id salesman_id

70001 150.5 2012-10-05 3005 5002 70009 270.65 2012-09-10 3001 5005 70002 65.26 2012-10-05 3002 5001 70004 110.5 2012-08-17 3009 5003 70007 948.5 2012-09-10 3005 5002 70005 2400.6 2012-07-27 3007 5001 70008 5760 2012-09-10 3002 5001 70010 1983.43 2012-10-10 3004 5006 70003 2480.4 2012-10-10 3009 5003 70012 250.45 2012-06-27 3008 5002 70011 75.29 2012-08-17 3003 5007 70013 3045.6 2012-04-25 3002 5001
```
SELECT 
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
WHERE 
    o.purch_amt BETWEEN 500 AND 2000;
```
## Output:
![image](https://github.com/user-attachments/assets/f368cc81-d141-4f2b-9020-3d5632d04aac)


## Question 3 
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

Sample table: salesman

salesman_id | name | city | commission -------------+------------+----------+------------ 5001 | James Hoog | New York | 0.15 5002 | Nail Knite | Paris | 0.13 5005 | Pit Alex | London | 0.11 5006 | Mc Lyon | Paris | 0.14 5007 | Paul Adam | Rome | 0.13 5003 | Lauson Hen | San Jose | 0.12 Sample table: customer

customer_id | cust_name | city | grade | salesman_id -------------+----------------+------------+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002 3008 | Julian Green | London | 300 | 5002 3004 | Fabian Johnson | Paris | 300 | 5006 3009 | Geoff Cameron | Berlin | 100 | 5003 3003 | Jozy Altidor | Moscow | 200 | 5007 3001 | Brad Guzan | London | | 5005
```
SELECT 
    s.name AS Salesman, 
    c.cust_name, 
    c.city
FROM 
    salesman s
JOIN 
    customer c ON s.city = c.city;
```
## Output:

![image](https://github.com/user-attachments/assets/8b630637-3799-47f8-843e-756ab4a4a272)


## Question 4 
Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n"), with an inner join on the "department_id" column and a condition filtering for nurses in the 'Pediatrics' department.
```
SELECT 
    n.*
FROM 
    nurses n
INNER JOIN 
    departments d ON n.department_id = d.department_id
WHERE 
    d.department_name = 'Pediatrics';
```
## Output:

![image](https://github.com/user-attachments/assets/bdad837f-a6df-45cc-9516-35100a97deb4)


## Question 5
Write the SQL query that achieves the selection of all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.
```
SELECT 
    t.*
FROM 
    test_results t
INNER JOIN 
    patients p ON t.patient_id = p.patient_id
WHERE 
    p.first_name = 'Alice';
```
## Output:

![image](https://github.com/user-attachments/assets/e7742a35-d9a9-4bf0-bcd8-38457fc7e4b1)


## Question 6
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.
```
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission AS "commission"
FROM 
    customer c
INNER JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city AND 
    s.commission > 0.12;
```
## Output:

![image](https://github.com/user-attachments/assets/9e5fe38a-6ac8-4b26-b7d2-2459020be777)


## Question 7 Write the SQL query that achieves the selection of the date of birth from the "patients" table (aliased as "p") and all columns from the "appointments" table (aliased as "a"), with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.
```
SELECT 
    p.date_of_birth,
    a.*
FROM 
    patients p
INNER JOIN 
    appointments a ON p.patient_id = a.patient_id
WHERE 
    p.first_name = 'Alice';
```
## Output:

![image](https://github.com/user-attachments/assets/4b50b60e-0c89-4f58-98aa-0b77a724c654)


## Question 8 
Write the SQL query that achieves the selection of the "cust_name" and "city" columns from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for customers in the city 'London'.
```
SELECT 
    c.cust_name, 
    c.city, 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
WHERE 
    c.city = 'London';
```
## Output:

![image](https://github.com/user-attachments/assets/29511150-962e-423f-9905-4a0161287d33)


## Question 9
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission.
```
SELECT 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt, 
    c.cust_name AS "Customer Name", 
    c.grade, 
    s.name AS "Salesman", 
    s.commission
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id;
```
## Output:

![image](https://github.com/user-attachments/assets/01f685a3-ebf9-4beb-8215-e201cf1b019b)


## Question 10 
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with an order date between '2012-07-01' and '2012-07-30'.
```
select c.customer_id , c.cust_name , c.city , c.grade , c.salesman_id 
from CUSTOMER C
LEFT JOIN ORDERS o
ON o.customer_id = c.customer_id
where 
    ord_date BETWEEN '2012-07-01' AND '2012-07-30'
```
## Output:

![image](https://github.com/user-attachments/assets/2493e5e3-9e0b-4543-a69c-226d24f70273)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
