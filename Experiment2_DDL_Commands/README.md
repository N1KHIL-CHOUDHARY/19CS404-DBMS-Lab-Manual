# Experiment 2: DDL Commands

## NAME: Nikhil H
## REG.NO: 212224040219

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
Create a new table named item with the following specifications and constraints:
1. item_id as TEXT and as primary key.
2. item_desc as TEXT.
3. rate as INTEGER.
4. icom_id as TEXT with a length of 4.
5. icom_id is a foreign key referencing com_id in the company table.
6. The foreign key should cascade updates and deletes.
7. item_desc and rate should not accept NULL.

```sql
CREATE TABLE item(
item_id TEXT,
item_desc TEXT,
rate INT,
icom_id TEXT CHECK (LENGTH(icom_id)=4),
FOREIGN KEY (icom_id) REFERENCES company (com_id) ON UPDATE CASCADE ON DELETE CASCADE
);
```

**Output:**

![image](https://github.com/user-attachments/assets/1774f61b-0ad2-42ac-bc90-d6898da90d77)

**Question 2**
---
Insert all books from Out_of_print_books into Books
Table attributes are ISBN, Title, Author, Publisher, YearPublished

```sql
INSERT INTO Books (ISBN, Title, Author, Publisher, YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished FROM Out_of_print_books;
```

**Output:**

![image](https://github.com/user-attachments/assets/05087595-b4ac-48de-8a33-521e17655bcf)

**Question 3**
---
Write a SQL query to Add a new column Country as text in the Student_details table.
Sample table: Student_details

```sql
ALTER TABLE Student_details ADD Country TEXT;
```

**Output:**

![image](https://github.com/user-attachments/assets/38ef77ff-2e53-49c0-bedf-dfb45a5792d0)

**Question 4**
---
Create a table named Locations with the following columns:
- LocationID as INTEGER
- LocationName as TEXT
- Address as TEXT

```sql
CREATE TABLE Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT
);
```

**Output:**

![image](https://github.com/user-attachments/assets/84a70964-fbd7-40c4-b3c1-9c911755227a)


**Question 5**
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.

```sql
INSERT INTO Books (ISBN,Title,Author,Publisher,Year)
VALUES ('978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024);
```

**Output:**

![image](https://github.com/user-attachments/assets/a8b66909-54eb-4230-8331-75d1d019d542)

**Question 6**
---
In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```sql
INSERT INTO Student_details (RollNo,Name,Gender,Subject,MARKS)
VALUES (205,'Olivia Green','F',NULL,NULL),
(207,'Liam Smith','M','Mathematics',85),
(208,'Sophia Johnson','F','Science',NULL);
```

**Output:**

![image](https://github.com/user-attachments/assets/3df68d8f-9f18-477e-a9e8-396c3d78ff85)

**Question 7**
---
Create a table named Bonuses with the following constraints:
- BonusID as INTEGER should be the primary key.
- EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
- BonusAmount as REAL should be greater than 0.
- BonusDate as DATE.
- Reason as TEXT should not be NULL.

```sql
CREATE TABLE Bonuses(
BonusID INT PRIMARY KEY,
EmployeeID INT,
BonusAmount REAL,
BonusDate DATE,
Reason TEXT NOT NULL,
FOREIGN KEY (EmployeeID) REFERENCES Employees (EmployeeID),
CHECK (BonusAmount>0)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/1968df0f-cc32-4e01-886e-77891ce00096)

**Question 8**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
CREATE TABLE jobs(
job_id INTEGER,
job_title TEXT DEFAULT 'black',
min_salary INT DEFAULT 8000,
max_salary INT DEFAULT NULL
);
```

**Output:**

![image](https://github.com/user-attachments/assets/b030eb34-2af0-48ab-aef2-19fd5cb15e1f)

**Question 9**
---
Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types:
- designation as VARCHAR(50)
- net_salary as NUMBER
- dob as DATE

```sql
ALTER TABLE Companies ADD designation varchar(50);
ALTER TABLE Companies ADD net_salary number;
ALTER TABLE Companies ADD dob date;
```

**Output:**

![image](https://github.com/user-attachments/assets/2a20a718-9410-46ea-bb24-44066b1d1484)

**Question 10**
---
Create a table named Invoices with the following constraints:
- InvoiceID as INTEGER should be the primary key.
- InvoiceDate as DATE.
- Amount as REAL should be greater than 0.
- DueDate as DATE should be greater than the InvoiceDate.
- OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
Amount REAL,
DueDate DATE,
OrderID INTEGER,
FOREIGN KEY (OrderID) REFERENCES Orders (OrderID),
CHECK (LENGTH(Amount)>0),
CHECK (DueDate>InvoiceDate)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/73e63eec-ec6c-4a3f-a1c9-c065057421c2)

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

## Module 1 Grade:

<img width="1502" height="189" alt="image" src="https://github.com/user-attachments/assets/07b423f3-f372-4312-897f-e4d77a173b17" />

