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
Write a SQL statement to Update the grade of all customers in Chennai city as  5. 

Customer table (customer_id,cust_name,city,grade,salesman_id)

```sql
UPDATE Customer
SET grade=5
WHERE city='Chennai';
```

**Output:**

<img width="1231" height="545" alt="image" src="https://github.com/user-attachments/assets/0345cc11-b30e-4c4e-91dc-b5d82a18a669" />

**Question 2**
---
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)

```sql
UPDATE suppliers
SET supplier_name='A1 Suppliers'
WHERE supplier_ID=8;
```

**Output:**

<img width="1216" height="460" alt="image" src="https://github.com/user-attachments/assets/f3925fd1-a169-44b1-bc9f-78d6fb11c098" />

**Question 3**
---
Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.
```sql
UPDATE products
SET reorder_lvl=CAST(reorder_lvl*0.7 AS INT)
WHERE cost_price>50
AND quantity < 100;
```

**Output:**

<img width="1210" height="521" alt="image" src="https://github.com/user-attachments/assets/454e7b70-bc10-4578-8e55-666cef0cae61" />

**Question 4**
---
Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.
```sql
UPDATE products
SET reorder_lvl=CAST(reorder_lvl*0.7 AS INT)
WHERE product_name LIKE'%CREAM%'
AND quantity > reorder_lvl;
```

**Output:**

<img width="1217" height="575" alt="image" src="https://github.com/user-attachments/assets/2eab2c5b-42c7-4eb4-8150-571370457613" />

**Question 5**
---
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.

```sql
UPDATE employees
SET hire_date='2024-01-24'
WHERE department_id=50;
```

**Output:**

<img width="1221" height="361" alt="image" src="https://github.com/user-attachments/assets/ccd5fc46-5446-4802-9c2c-851fbba5b9e1" />

**Question 6**
---
Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000

```sql
DELETE FROM Customer
WHERE grade=2
AND cust_name LIKE'M%'
AND payment_amt<3000;
```

**Output:**

<img width="1216" height="475" alt="image" src="https://github.com/user-attachments/assets/ebb9dfcc-6599-4ac8-b05c-5ba0d33d32cd" />

**Question 7**
---
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

```sql
DELETE FROM Surgeries
WHERE surgery_date='2024-02-28';
```

**Output:**

<img width="1215" height="445" alt="image" src="https://github.com/user-attachments/assets/232a1570-9726-48f3-b54c-b24dc60f8dba" />

**Question 8**
---
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.
```sql
DELETE FROM doctors
WHERE specialization IN('Pediatrics','Cardiology')
AND last_name='Brown';
```

**Output:**

<img width="1226" height="811" alt="image" src="https://github.com/user-attachments/assets/14c1e86b-6da4-457b-863f-eb74ecdacc06" />

**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

```sql
DELETE FROM Customer
WHERE grade>=2;
```

**Output:**

<img width="628" height="515" alt="image" src="https://github.com/user-attachments/assets/24466c8e-39f6-4bd5-827d-1ead6b50eae6" />


**Question 10**
---
Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'

```sql
DELETE FROM Doctors
WHERE specialization='Cardiology';
```

**Output:**
<img width="1070" height="324" alt="image" src="https://github.com/user-attachments/assets/773cca62-3f48-4710-aa37-3bbc1f11cf85" />


**SEB Grade**
<img width="1325" height="73" alt="image" src="https://github.com/user-attachments/assets/564b1b4d-3b9e-49fd-b23b-81a8be72d3f4" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
