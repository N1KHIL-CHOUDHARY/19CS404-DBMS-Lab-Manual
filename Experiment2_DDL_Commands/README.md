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
CREATE TABLE Table_Name(
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

<img width="826" height="465" alt="image" src="https://github.com/user-attachments/assets/553409ff-be62-4338-a809-0c84707d6687" />


```sql
INSERT INTO Customers(ID,NAME,AGE,ADDRESS,SALARY)VALUES
(1,'Ramesh',32 ,'Ahmedabad',2000),
(2,'Khilan',25,'Delhi',1500),
(3,'Kaushik',23,'Kota',2000);

```

**Output:**

<img width="1186" height="232" alt="image" src="https://github.com/user-attachments/assets/2fc25eac-2404-4744-8a29-2bb7370c32ce" />


**Question 2**
---
<img width="1066" height="253" alt="image" src="https://github.com/user-attachments/assets/0bdac749-5509-42c7-b36c-a1737947a51e" />


```sql
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)VALUES
(201,'David Lee','M ','Physics',92);
```

**Output:**

<img width="1190" height="265" alt="image" src="https://github.com/user-attachments/assets/aa3131fd-0347-495f-857a-35651cd422bb" />


**Question 3**
---
<img width="1042" height="371" alt="image" src="https://github.com/user-attachments/assets/82f096e6-5232-4dac-9549-35118f5baeb5" />


```sql
INSERT INTO Books(ISBN, Title, Author, Publisher, YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished
FROM  Out_of_print_books;
```

**Output:**

<img width="1197" height="278" alt="image" src="https://github.com/user-attachments/assets/e9693475-e560-4344-bd6c-94f1556bba8c" />

**Question 4**
---
<img width="949" height="479" alt="image" src="https://github.com/user-attachments/assets/9208595a-fbcb-4893-9cc1-3c534567a5a4" />


```sql
ALTER TABLE books
ADD COLUMN ISBN varchar(30);
ALTER TABLE books
ADD COLUMN domain_dept varchar(30);
```

**Output:**

<img width="1192" height="396" alt="image" src="https://github.com/user-attachments/assets/55959750-8793-4ec6-a9c3-1c72d1d03e90" />

**Question 5**
---
<img width="1222" height="321" alt="image" src="https://github.com/user-attachments/assets/002f72bd-0d84-40ad-9a2f-13039100ee45" />


```sql
ALTER TABLE Student_details
ADD column Email VARCHAR(50) ;
ALTER TABLE Student_details
ADD column MARKS default 0;
```

**Output:**

<img width="1203" height="233" alt="image" src="https://github.com/user-attachments/assets/33d5efff-901a-4c19-83b4-ee95c5534f52" />

**Question 6**
---
<img width="967" height="458" alt="image" src="https://github.com/user-attachments/assets/bbf89ff2-67ae-4412-ad23-e80febb895e4" />


```sql
Create table Employees
(
EmployeeID INTEGER,
FirstName TEXT,
LastName TEXT,
HireDate DATE
);
```

**Output:**

<img width="1193" height="307" alt="image" src="https://github.com/user-attachments/assets/a29e3537-6fc6-4360-b8d6-8c99371c3e27" />

**Question 7**
---
<img width="902" height="377" alt="image" src="https://github.com/user-attachments/assets/977db7e1-46db-4110-92d9-d59245a7f990" />

```sql
Create table Products
(
ProductID primary key,
ProductName NOT NULL,
Price real check(Price>0),
Stock integer check(Stock>=0)
);
```

**Output:**

<img width="1177" height="282" alt="image" src="https://github.com/user-attachments/assets/15434ae9-3e48-4185-b0c5-57f014a6336f" />

**Question 8**
---
<img width="1047" height="466" alt="image" src="https://github.com/user-attachments/assets/93645aa8-e235-451d-a9ac-aec03ca4a4ec" />


```sql
Create table item 
(
item_id TEXT primary key,
item_desc TEXT,
rate INTEGER,
icom_id TEXT  check(length(icom_id)=4),
foreign key(icom_id) references company (com_id)
on update cascade
on delete cascade
);
```

**Output:**

<img width="1196" height="363" alt="image" src="https://github.com/user-attachments/assets/70212230-542c-4dfb-93fa-46032aeb0ce9" />

**Question 9**
---
<img width="1224" height="363" alt="image" src="https://github.com/user-attachments/assets/e5388ace-4f82-40e8-9299-67a14abdb3e7" />


```sql
Create table ProjectAssignments
(
AssignmentID INTEGER primary key,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE NOT NULL,
foreign key(EmployeeID) references Employees(EmployeeID)
foreign key(ProjectID) references Projects(ProjectID)
);
```

**Output:**

<img width="1030" height="245" alt="image" src="https://github.com/user-attachments/assets/242e4c21-7a74-4fdd-9ab5-37a853953416" />

**Question 10**
---
<img width="1223" height="396" alt="image" src="https://github.com/user-attachments/assets/ad93caa4-0abb-43cd-95e3-c8fbd0b84d57" />


```sql--
Create table Department
(
DepartmentID INTEGER primary key,
DepartmentName TEXT unique not NULL,
Location TEXT
);
```

**Output:**

<img width="1162" height="292" alt="image" src="https://github.com/user-attachments/assets/8cc4939b-1b97-402d-8724-05f88e05a3f6" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

