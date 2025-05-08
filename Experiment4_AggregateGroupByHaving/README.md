# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

## Question 1

How many patients have expired insurance coverage for each insurance company?
Sample table:Insurance Table

![image](https://github.com/user-attachments/assets/e7a956ce-6373-4ef0-af3f-49397aa39634)

```
select InsuranceCompany,count(*) as TotalExpiredPatients

from Insurance

group by InsuranceCompany;
```
## Output:

![image](https://github.com/user-attachments/assets/aeaec9a0-7c3e-4fe7-a16b-8519544beee7)


## Question 2

How many prescriptions were written by each doctor? Sample tablePrescriptions Table

![image](https://github.com/user-attachments/assets/87cefa15-e2fa-4326-badf-a9eba0dcdbaf)

```
SELECT DoctorID,count(*) as TotalPrescriptions

from Prescriptions

group by DoctorID;
```
## Output:

![image](https://github.com/user-attachments/assets/55f15c9e-d5ca-449e-af42-d68ab71ead70)

## Question 3

What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table

![image](https://github.com/user-attachments/assets/aa2f31be-5cee-4b35-8f6f-7dd9b2d53b92)


## Output:

![image](https://github.com/user-attachments/assets/d8d8554d-98cd-4ffb-af0a-bfbcb224601a)


## Question 4

Write a SQL query to find the Fruit with the lowest available quantity.

![image](https://github.com/user-attachments/assets/de52878a-2ffb-41a9-bc72-195a76e0cfa5)

```
select name as fruit_name , min(inventory) as lowest_quantity

from fruits;
```
## Output:

![image](https://github.com/user-attachments/assets/77c4dc18-3ddb-450a-943f-876fae4d7da3)


## Question 5

Write a SQL query to calculate total available amount of fruits that has a price greater than 0.5 . Return total Count.

Note: Inventory attribute contains amount of fruits

![image](https://github.com/user-attachments/assets/7b5d9e02-ef00-4bbd-b727-cd53aa78e752)

```
select sum(inventory) as total_available_amount

from fruits

where price>0.5;
```
## Output:

![image](https://github.com/user-attachments/assets/3be4e066-2bee-4b47-861e-68fa89ede6b7)


## Question 6

Write a SQL query to find the average salary of all employees?

![image](https://github.com/user-attachments/assets/aedeef06-dd20-4778-935d-ceb42738d030)

```
select avg(income) as Average_Salary

from employee;
```
## Output:

![image](https://github.com/user-attachments/assets/90b1f83f-dd08-4764-8c54-e63eddcfb344)


## Question 7

Write a SQL query to determine the number of customers who received at least one grade for their activity.

![image](https://github.com/user-attachments/assets/53670d39-ed29-41f1-b349-e6cee687f202)

```
SELECT COUNT(customer_id) AS COUNT

FROM customer

where grade is not null;
```
## Output:

![image](https://github.com/user-attachments/assets/7763733f-5927-48d8-8ad4-ac6617403b42)


## Question 8

Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.

![image](https://github.com/user-attachments/assets/711c76b9-f3f9-4129-92e2-276f5fbb9b3c)

```
select category_id,sum(price) as Total_Cost

from products

group by category_id

having Total_Cost>50;
```
## Output:

![image](https://github.com/user-attachments/assets/8bb4dc44-9307-49a7-810b-6da9a6c72626)

## Question 9

Write a SQL query to find the difference between the maximum and minimum price of fruits?

![image](https://github.com/user-attachments/assets/3b0e954f-944b-476c-9265-c20ac0f5397d)

```
select (max(price)-min(price)) as price_diff

from fruits;
```
### Output:

![image](https://github.com/user-attachments/assets/833cf95f-58f0-4d9d-8095-c9f6a2712348)


## Question 10

Write a SQL query to find the average length of names for people living in Chennai?

![image](https://github.com/user-attachments/assets/b5f4c03c-c2fb-43a0-b5d1-a63e18d8559f)

```
select avg(length(name)) as avg_name_length

from customer

where city like '%Chennai%';
```
## Output:

![image](https://github.com/user-attachments/assets/a3c297cb-840a-4f1e-857b-dd83ce34547b)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
