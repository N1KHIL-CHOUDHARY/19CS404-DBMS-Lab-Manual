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
--Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
-- update employees set salary=salary+500 , email='updated' where (job_id='SA_REP' and commission_pct>0.15);
```

**Output:**

<img width="1215" height="542" alt="image" src="https://github.com/user-attachments/assets/accaa629-679a-49c1-88eb-933a237f13f7" />


**Question 2**
---
-- Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
-- update PRODUCTS set reorder_lvl=reorder_lvl*0.70 where product_name like '%cream%' and quantity>reorder_lvl;
```

**Output:**

<img width="1215" height="498" alt="image" src="https://github.com/user-attachments/assets/c13f48dd-80df-4c07-921e-5039c88252a2" />


**Question 3**
---
-- Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
-- update Products set quantity=quantity*1.10;
```

**Output:**

<img width="1230" height="637" alt="image" src="https://github.com/user-attachments/assets/ee1fe2f1-e289-4b1a-a773-5fa20a811827" />


**Question 4**
---
--For products with a profit % less than 30% of selling price, update the selling price to provide a profit margin of 35% over cost price of the product in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
--update products set sell_price = CAST(1.35*cost_price AS INT)where((sell_price - cost_price)/ sell_price)*100 < 30;
```

**Output:**

<img width="1218" height="522" alt="image" src="https://github.com/user-attachments/assets/717974e7-bc1b-47d3-8a64-41232a13b306" />


**Question 5**
---
-- Write a SQL statement to Update the per_unit_price to 25 and total_price accordingly in purchases table where purchase_date is '2022-08-15' and product_id is 12.

```sql
-- update purchases  set per_unit_price = 25 , total_price = 25*quantity where purchase_date = '2022-08-15' and product_id = 12;
```

**Output:**

<img width="1232" height="555" alt="image" src="https://github.com/user-attachments/assets/89a619bf-eadd-4398-abd2-456e5a1d31ac" />


**Question 6**
---
-- Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.

```sql
-- delete from Customer where WORKING_AREA = 'New York';
```

**Output:**

<img width="1233" height="718" alt="image" src="https://github.com/user-attachments/assets/ce12dbbd-2d3a-4466-a062-a4c905ef7e92" />


**Question 7**
---
--Write a SQL query to Delete customers with 'CUST_COUNTRY' 'UK' and 'WORKING_AREA' 'London' whose 'GRADE' is less than 3

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00

```sql
-- delete from Customer where CUST_COUNTRY='UK' and WORKING_AREA='London' and GRADE<3;
```

**Output:**

<img width="1247" height="520" alt="image" src="https://github.com/user-attachments/assets/52d70e92-b14e-4d56-ad92-1872716c8f2d" />


**Question 8**
---
-- Write a SQL query to Delete customers from 'customer' table where 'GRADE' is odd.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBB
```sql
-- delete from Customer where GRADE %2=1;
```

**Output:**

<img width="1234" height="447" alt="image" src="https://github.com/user-attachments/assets/3a6f5e27-017c-4530-b734-8541aed94038" />


**Question 9**
---
-- Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
-- delete from doctors where specialization = 'Pediatrics' and first_name = 'Michael';
```

**Output:**

<img width="1244" height="469" alt="image" src="https://github.com/user-attachments/assets/8a634b59-fa3c-4495-8bfc-d0d393363bcf" />


**Question 10**
---
-- Write a SQL query to Delete All Doctors whose ID ranges from 2 to 4.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
-- delete from Doctors where doctor_id between 2 and 4;
```

**Output:**

<img width="1236" height="880" alt="image" src="https://github.com/user-attachments/assets/6869ae3b-90a1-42df-a170-19e425f2260c" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
