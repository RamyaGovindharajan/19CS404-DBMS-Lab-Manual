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

**Question 1**
--
How many prescriptions were written by each doctor?

```sql
select DoctorID, count(*) as TotalPrescriptions from Prescriptions
group by DoctorID;
```

**Output:**

<img width="720" height="742" alt="image" src="https://github.com/user-attachments/assets/07128162-d878-4b9a-8011-d53d141f4862" />

**Question 2**
---
What is the total number of appointments scheduled for each day?

```sql
select DATE(AppointmentDateTime)AS AppointmentDate,
COUNT(*) As TotalAppointments
FROM Appointments
GROUP BY DATE(AppointmentDateTime);
```

**Output:**

<img width="817" height="641" alt="image" src="https://github.com/user-attachments/assets/60e2a543-2e9f-43b0-a967-6dbe5b17e1be" />

**Question 3**
---
What is the total number of appointments scheduled by each doctor?

```sql
select DoctorID, count(AppointmentID) as TotalAppointments from Appointments
group by DoctorID;
```

**Output:**

<img width="680" height="618" alt="image" src="https://github.com/user-attachments/assets/fdf0096a-9e87-4017-8359-85b29b2cea93" />

**Question 4**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

```sql
SELECT
SUM(purch_amt)AS TOTAL
FROM orders;
```

**Output:**

<img width="452" height="382" alt="image" src="https://github.com/user-attachments/assets/073d6081-c650-467d-9cd5-ee00d013736c" />

**Question 5**
---
Write a SQL query to find the average length of email addresses (in characters):

```sql
SELECT
AVG(LENGTH(email))AS avg_email_length
FROM customer;
```

**Output:**

<img width="480" height="380" alt="image" src="https://github.com/user-attachments/assets/40415578-a75d-4955-b202-8a029bef2159" />

**Question 6**
---
Write a SQL query to find the shortest email address in the customer table?

```sql
SELECT name,email, LENGTH(email) AS min_email_length
FROM customer
ORDER BY LENGTH(email)
LIMIT 1;
```

**Output:**

<img width="1021" height="373" alt="image" src="https://github.com/user-attachments/assets/69b8c6c3-0378-4889-ab79-ee228c9437c7" />

**Question 7**
---
Write a SQL query to find the minimum purchase amount.

```sql
SELECT MIN(purch_amt)AS MINIMUM
FROM orders;
```

**Output:**

<img width="361" height="386" alt="image" src="https://github.com/user-attachments/assets/f56ab3d5-0d31-453e-930b-8a65e1fda2e0" />

**Question 8**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

```sql
SELECT (age/5)*5 AS age_group,
SUM(salary)
FROM customer1
GROUP BY (age/5)*5
HAVING SUM(salary)>5000;
```

**Output:**

<img width="605" height="431" alt="image" src="https://github.com/user-attachments/assets/7771f4d0-1e42-4ed6-adba-a590a91419b9" />

**Question 9**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.

```sql
SELECT (age/5)*5 AS age_group,
AVG(age)
FROM customer1
GROUP BY (age/5)*5
HAVING AVG(age)<24;
```

**Output:**

<img width="565" height="377" alt="image" src="https://github.com/user-attachments/assets/49921cb4-2034-480b-bead-16b959f4e98e" />

**Question 10**
---
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

```sql
SELECT city, SUM(income) AS Income
FROM employee
GROUP BY city
HAVING SUM(income)>200000;
```

**Output:**

<img width="572" height="596" alt="image" src="https://github.com/user-attachments/assets/dfd76562-f76e-417b-a423-30da1e9ac39c" />

**SEB Grades:**

<img width="1144" height="104" alt="image" src="https://github.com/user-attachments/assets/2a1a3d34-5dfe-4292-95df-a208a1326908" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
