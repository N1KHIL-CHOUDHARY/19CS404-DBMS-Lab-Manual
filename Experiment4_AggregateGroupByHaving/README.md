# Experiment 4: Aggregate Functions, Group By and Having Clause

## NAME: Nikhil H
## REG.NO: 212224040219

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
-- How many appointments are scheduled for each patient?

```sql
-- SELECT PatientID , count(AppointmentID) as TotalAppointments
FROM Appointments 
group by PatientID
ORDER BY PatientID
```

**Output:**

![image](https://github.com/user-attachments/assets/c6fc55d9-d0f2-4bd5-9f37-031bfaa8a064)

**Question 2**
---
-- What is the average duration of insurance coverage for patients covered by each insurance company? 

```sql
-- SELECT InsuranceCompany, AVG(enddate - startdate) AS AvgCoverageDurationDays
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**

![image](https://github.com/user-attachments/assets/146996dc-b11b-4d32-a416-1363b749fc70)

**Question 3**
---
-- How many prescriptions were written in each frequency category (e.g., once daily, twice daily)? 

```sql
-- select Frequency, count(PatientID) as TotalPrescriptions
FROM Prescriptions
group by Frequency;
```

**Output:**

![image](https://github.com/user-attachments/assets/c0bff40e-f88d-42bc-a8d2-a0790c66f765)

**Question 4**
---
-- Write a SQL query to find the average salary of all employees?

```sql
-- SELECT AVG(income) AS Average_Salary 
FROM employee;
```

**Output:**

![image](https://github.com/user-attachments/assets/338edc65-45d5-4808-9499-9be884d9878a)

**Question 5**
---
-- Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

```sql
-- SELECT count(distinct salesman_id) AS COUNT
FROM orders;
```

**Output:**

![image](https://github.com/user-attachments/assets/faf627ff-1d61-437a-be90-6a2c300b885c)

**Question 6**
---
-- Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

```sql
-- SELECT COUNT(id) AS COUNT FROM customer 
WHERE city != 'Noida';
```

**Output:**

![image](https://github.com/user-attachments/assets/9cec0969-1b57-4d63-8520-ce9d54a168bc)

**Question 7**
---
-- Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

```sql
-- SELECT MAX(age) - MIN(age) AS age_difference 
FROM employee;
```

**Output:**

![image](https://github.com/user-attachments/assets/2db69714-9ff2-467e-970f-c1113a4801dd)

**Question 8**
---
--Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.

```sql
-- SELECT jdate, MIN(workhour) 
FROM employee1 
GROUP BY jdate 
HAVING MIN(workhour) < 10;
```

**Output:**

![image](https://github.com/user-attachments/assets/add35670-4fe4-46e8-8456-f140e3d683e3)

**Question 9**
---
-- Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

```sql
-- SELECT jdate, SUM(workhour)
FROM employee1 
GROUP BY jdate
HAVING SUM(workhour) >= 40;
```

**Output:**

![image](https://github.com/user-attachments/assets/1c6e000f-0cb5-41f5-9358-3ca1f6c4d36a)

**Question 10**
---
-- Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 400,000.

```sql
-- SELECT age, MIN(income) 
FROM employee 
GROUP BY age
HAVING MIN(income) < 400000;
```

**Output:**

![image](https://github.com/user-attachments/assets/803d818b-9d1f-4472-93f6-4eaf2daa37fc)

SEB:

<img width="1008" height="158" alt="image" src="https://github.com/user-attachments/assets/146fc103-f804-4ff4-8f6f-cff63001ee81" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
