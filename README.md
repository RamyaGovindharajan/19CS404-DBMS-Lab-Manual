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
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
CREATE TABLE Orders(
OrderID INTEGER primary key,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY(CustomerID) references Customers(CustomerID)
);
```

**Output:**

<img width="1231" height="370" alt="image" src="https://github.com/user-attachments/assets/911b6297-86aa-43f5-9df9-f12bf46a28d7" />


**Question 2**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
CREATE TABLE Shipments(
ShipmentID INTEGER primary key,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
foreign key(SupplierID) references Suppliers(SupplierID),
foreign key(OrderID) references Orders(OrderID)
);
```

**Output:**

<img width="1221" height="307" alt="image" src="https://github.com/user-attachments/assets/6860b947-cede-4ac5-901b-e9a5e2306d70" />

**Question 3**
---
Create a table named Events with the following columns:

EventID as INTEGER
EventName as TEXT
EventDate as DATE

```sql
CREATE TABLE Events(
EventID INTEGER,
EventName TEXT,
EventDate DATE
);
```

**Output:**

<img width="1224" height="445" alt="image" src="https://github.com/user-attachments/assets/a5b52b82-c9d7-4028-8f82-4393daa13f6c" />

**Question 4**
---
Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```sql
ALTER TABLE Companies ADD COLUMN designation varchar(50);
ALTER TABLE Companies ADD COLUMN net_salary number;
```

**Output:**

<img width="1224" height="458" alt="image" src="https://github.com/user-attachments/assets/cc1f7e06-60a8-4caa-bc8d-241f72d63970" />

**Question 5**
---
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

```sql
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)values
(201,'David Lee','M','Physics',92);
```

**Output:**
<img width="1227" height="325" alt="image" src="https://github.com/user-attachments/assets/76608d2e-ade8-4da8-8211-eb882751066b" />

**Question 6**
---
Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer

```sql
ALTER TABLE customer ADD birth_date timestamp;
```

**Output:**
<img width="1222" height="410" alt="image" src="https://github.com/user-attachments/assets/b76faaac-68a9-4d24-b9fa-d44a4a08d2c1" />

**Question 7**
---
Create a new table named orders with the following specifications:
ord_id as TEXT with a length of 4.
item_id as TEXT.
ord_date as DATE.
ord_qty as INTEGER.
cost as INTEGER.
The primary key is a composite key consisting of item_id and ord_date.
ord_id and item_id should not accept NULL

```sql
CREATE TABLE orders(
ord_id TEXT CHECK(length(ord_id)=4) NOT NULL,
item_id TEXT NOT NULL,
ord_date DATE,
ord_qty INTEGER,
cost INTEGER,
primary key(item_id,ord_date)
);
```

**Output:**

<img width="1218" height="402" alt="image" src="https://github.com/user-attachments/assets/944c9bbb-7a01-4c35-8f36-24eddb237bc9" />

**Question 8**
---
Insert the following customers into the Customers table:

CustomerID | Name       |  Address  |   City     |   ZipCode
---------- | -----------| ----------|  ----------| ----------
302        | Laura Croft| 456 Elm St| Seattle    |98101
303        | Bruce Wayne| 789 Oak St| Gotham     | 10001

```sql
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode)values
(302,'Laura Croft','456 Elm St','Seattle',98101),
(303,'Bruce Wayne','789 Oak St','Gotham',10001);
```

**Output:**

<img width="1218" height="441" alt="image" src="https://github.com/user-attachments/assets/7456aab9-88fa-4a81-9e82-56ec235f4af8" />

**Question 9**
---
Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished
```sql
INSERT INTO Books(ISBN,Title,Author,Publisher,YearPublished) 
SELECT ISBN,Title,Author,Publisher,YearPublished
FROM Out_of_print_books;
```

**Output:**

<img width="1232" height="356" alt="image" src="https://github.com/user-attachments/assets/fdeb242a-5f67-4c3d-a44e-6fd510ff0dd9" />

**Question 10**
---
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.

```sql
CREATE TABLE Department(
DepartmentID INTEGER primary key,
DepartmentName TEXT unique NOT NULL,
Location TEXT
);
```

**Output:**

<img width="1223" height="341" alt="image" src="https://github.com/user-attachments/assets/2268ad5e-f5a3-483d-b0ed-41ee6ec7d654" />

**SEB Grade**

<img width="1189" height="81" alt="image" src="https://github.com/user-attachments/assets/b0cae284-e65f-46b7-9519-a86ffbbeeb94" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
