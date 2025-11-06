# Experiment 6: Joins

## NAME: Nikhil H
## REG.NO: 212224040219

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

**Question 1**
--
![image](https://github.com/user-attachments/assets/6a7d531f-ab7a-4676-a915-51cf6a349ce5)

```sql
SELECT 
    customer.cust_name AS "Customer Name", 
    customer.city AS "city", 
    salesman.name AS "Salesman", 
    salesman.commission
FROM 
    customer
JOIN 
    salesman
ON 
    customer.salesman_id = salesman.salesman_id
WHERE 
    salesman.commission > 0.12;
```

**Output:**

![image](https://github.com/user-attachments/assets/17930339-1ff8-4711-a2b1-f114420b8203)

**Question 2**
---
![image](https://github.com/user-attachments/assets/d3242b2e-3391-4cb3-a605-416836846233)

```sql
SELECT 
    patients.date_of_birth, 
    appointments.*
FROM 
    patients
JOIN 
    appointments
ON 
    patients.patient_id = appointments.patient_id
WHERE 
    patients.first_name = 'Alice';
```

**Output:**

![image](https://github.com/user-attachments/assets/f39c1ec5-21f6-490f-97fa-aa19952d99b8)

**Question 3**
---
![image](https://github.com/user-attachments/assets/097557ad-6d0d-4e7c-b56e-8bff11cd916f)

```sql
SELECT 
    orders.ord_no, 
    orders.ord_date, 
    orders.purch_amt, 
    customer.cust_name AS "Customer Name", 
    customer.grade, 
    salesman.name AS "Salesman", 
    salesman.commission
FROM 
    orders
JOIN 
    customer ON orders.customer_id = customer.customer_id
JOIN 
    salesman ON orders.salesman_id = salesman.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/1bb423b5-b96f-453c-8285-9846debb43d7)

**Question 4**
---
![image](https://github.com/user-attachments/assets/cc381617-fa50-4692-96e2-8bffba32000c)

```sql
SELECT 
    customer.cust_name, 
    customer.city, 
    customer.grade, 
    salesman.name AS "Salesman", 
    salesman.city AS "city"
FROM 
    customer
JOIN 
    salesman ON customer.salesman_id = salesman.salesman_id
WHERE 
    customer.grade < 300
ORDER BY 
    customer.customer_id ASC;
```

**Output:**

![image](https://github.com/user-attachments/assets/d0cfb6e4-ef2e-43e5-b0e9-5a2874ba62b7)

**Question 5**
---
![image](https://github.com/user-attachments/assets/64fc32f2-45b3-4f9d-9954-cb543e52f9a4)

```sql
SELECT 
    s.name
FROM 
    salesman AS s
LEFT JOIN 
    customer AS c ON s.salesman_id = c.salesman_id
WHERE 
    c.city = 'London';
```

**Output:**

![image](https://github.com/user-attachments/assets/6d8fbe7c-6d7e-4108-a9d9-4f40df26eadd)

**Question 6**
---
![image](https://github.com/user-attachments/assets/3676007b-6cbb-4aaa-be38-be3b7490a343)

```sql
SELECT 
    c.cust_name
FROM 
    customer AS c
LEFT JOIN 
    orders AS o ON c.customer_id = o.customer_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/04dc1a46-1a8c-434a-ba1b-0a2ec097d8de)

**Question 7**
---
![image](https://github.com/user-attachments/assets/975eee13-6675-4d54-b674-ec9078a29105)

```sql
SELECT 
    p.first_name AS patient_name, 
    t.*
FROM 
    patients AS p
INNER JOIN 
    test_results AS t ON p.patient_id = t.patient_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/67823836-4e83-4be1-a1ae-a33de5189991)

**Question 8**
---
![image](https://github.com/user-attachments/assets/2cd468b9-1846-4cad-a2ae-49cfc5db6f79)

```sql
SELECT 
    c.cust_name, 
    c.city AS city, 
    c.grade, 
    s.name AS Salesman, 
    s.city AS city
FROM 
    customer c
LEFT JOIN 
    salesman s 
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;
```

**Output:**

![image](https://github.com/user-attachments/assets/71369dc3-8140-495d-bfd5-3528da1c1715)

**Question 9**
---
![image](https://github.com/user-attachments/assets/1c055a9f-cf86-4140-8ae1-0578c3d74740)

```sql
SELECT 
    p.admission_date, 
    s.surgery_date
FROM 
    patients p
INNER JOIN 
    surgeries s 
ON 
    p.patient_id = s.patient_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/7a9059e3-1ca2-43bc-9473-ff3cd0245120)

**Question 10**
---
![image](https://github.com/user-attachments/assets/6e570580-23be-4f6e-86db-1f7a43afc23c)

```sql
SELECT 
    c.cust_name AS "Customer Name", 
    c.city, 
    s.name AS "Salesman", 
    s.commission
FROM 
    customer c
JOIN 
    salesman s 
ON 
    c.salesman_id = s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/f2ed3a8d-50ee-4576-b936-9dfde3589de2)

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.

## Module 5 Score

<img width="1070" height="97" alt="image" src="https://github.com/user-attachments/assets/d2ee3ec4-e1fc-40cd-a191-6d32764507de" />

