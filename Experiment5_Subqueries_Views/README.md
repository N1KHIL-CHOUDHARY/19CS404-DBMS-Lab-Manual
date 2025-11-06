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

**Question 1**
--
![image](https://github.com/user-attachments/assets/7e18cbd1-ce85-41e2-aa77-1e1ef74f70de)

**Program:**
```sql
select * from medications where dosage=(select min(dosage) from medications);
```

**Output:**
![image](https://github.com/user-attachments/assets/c1aef925-2de4-4a3e-9647-2c5234a89a4b)


**Question 2**
---
![image](https://github.com/user-attachments/assets/316c35ad-7645-471a-b513-82128ef2246a)

**Program:**
```sql
select name,city from customer where city in (select city from customer where id in (3,7));
```

**Output:**
![image](https://github.com/user-attachments/assets/a13dcaae-bd8c-49ba-930d-d5fd34f80a68)


**Question 3**
---
![image](https://github.com/user-attachments/assets/c99a954e-3477-4bbe-adb5-90d467237be4)

**Program:**
```sql
select * from medications where dosage=(select max(dosage) from medications);
```

**Output:**
![image](https://github.com/user-attachments/assets/2186c8f4-829a-44d0-8da9-c5240c46ad56)


**Question 4**
---
![image](https://github.com/user-attachments/assets/1c762597-41fd-4aa3-bd8d-b835d370c158)

**Program:**
```sql
select * from departments where length(department_name)>(select avg(length(department_name)) from departments);
```

**Output:**
![image](https://github.com/user-attachments/assets/80f22f5d-e66f-46a6-ab13-3d0ac87feeec)


**Question 5**
---
![image](https://github.com/user-attachments/assets/eed5d9db-5f80-4e37-a0a1-cd7a5b416b4b)

**Program:**
```sql
select * from orders where purch_amt > (select avg(purch_amt) from orders where ord_date='2012-10-10');
```

**Output:**
![image](https://github.com/user-attachments/assets/ae644a5c-1872-432c-b52f-9fb59661ec7e)


**Question 6**
---
![image](https://github.com/user-attachments/assets/d782ea69-48e5-4ffb-a59b-b50cd6b55ac3)

**Program:**
```sql
select * from customers where salary=1500;
```

**Output:**
![image](https://github.com/user-attachments/assets/152ef40f-0ecc-45b6-a7b0-47f9bf295a95)


**Question 7**
---
![image](https://github.com/user-attachments/assets/b20f144e-005e-477e-bae8-cf4cc3a19ead)

**Program:**
```sql
select name from customer where phone in (select phone from customer group by phone having count(*)=1);
```

**Output:**
![image](https://github.com/user-attachments/assets/7d990ebf-91e8-41e4-b4de-fbc068101538)


**Question 8**
---
![image](https://github.com/user-attachments/assets/37bd1a9b-e841-40e5-9428-1a308b1b03fe)

**Program:**
```sql
select * from employee where age < (select avg(age) from employee where income>250000);
```

**Output:**
![image](https://github.com/user-attachments/assets/e4cfcd23-f1f5-4090-a17b-517c365e2631)


**Question 9**
---
![image](https://github.com/user-attachments/assets/5f9a89ab-2819-47f4-b227-96fa22237cb8)

**Program:**
```sql
select * from customers where salary>1500;
```

**Output:**
![image](https://github.com/user-attachments/assets/7d607947-8a9d-466a-aae0-8e710d22ca06)


**Question 10**
---
![image](https://github.com/user-attachments/assets/1337f0aa-8c5f-4b5b-9f83-6fcea6b1b7b8)

**Program:**
```sql
SELECT grade, COUNT(*) 
FROM customer 
WHERE grade > (SELECT AVG(grade) 
               FROM customer 
               WHERE city = 'New York')
GROUP BY grade;

```


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.

