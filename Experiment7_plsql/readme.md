# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## NAME: Nikhil H
## REG.NO: 212224040219

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers
## Steps:
1. Declare two numeric variables and initialize them.
2. Use an IF statement to compare the values.
3. Display the greater number using DBMS_OUTPUT.PUT_LINE.
## Expected Output:
Greater number is: 80
## Program:
```
DECLARE
    num1 NUMBER := 80;  -- First number
    num2 NUMBER := 50;  -- Second number
BEGIN
    IF num1 > num2 THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
    END IF;
END;
```
## Output:
![image](https://github.com/user-attachments/assets/1bc3a150-941a-4fd4-9808-819ff732fd15)

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55
## Program:
```
SET SERVEROUTPUT ON;

DECLARE
    n NUMBER := 10;       -- Number up to which sum is calculated
    i NUMBER := 1;        -- Loop counter
    total_sum NUMBER := 0; -- To store the sum
BEGIN
    WHILE i <= n LOOP
        total_sum := total_sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || total_sum);
END;
```
## Output:
![image](https://github.com/user-attachments/assets/f7bc37f8-0155-4ee2-ba78-2873aed05fa3)

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8
## Program:
```
SET SERVEROUTPUT ON;

DECLARE
    n NUMBER := 7;     -- Number of terms in the series
    a NUMBER := 0;     -- First term
    b NUMBER := 1;     -- Second term
    c NUMBER;          -- Next term
    i NUMBER := 3;     -- Counter starting from 3 since first two terms are already known
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence:');
    DBMS_OUTPUT.PUT_LINE(a);
    DBMS_OUTPUT.PUT_LINE(b);

    WHILE i <= n LOOP
        c := a + b;
        DBMS_OUTPUT.PUT_LINE(c);
        a := b;
        b := c;
        i := i + 1;
    END LOOP;
END;
```
## Output:
![image](https://github.com/user-attachments/assets/27d45d8b-1201-45a8-b6c8-eabb7e9c0594)

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351
## Program:
```
SET SERVEROUTPUT ON;

DECLARE
    n NUMBER := 1535;       -- Original number
    original NUMBER := 1535;-- To keep the original number for display
    reversed NUMBER := 0;   -- To store the reversed number
    digit NUMBER;           -- To extract each digit
BEGIN
    WHILE n > 0 LOOP
        digit := MOD(n, 10);              -- Get the last digit
        reversed := reversed * 10 + digit;-- Build the reversed number
        n := TRUNC(n / 10);               -- Remove the last digit
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('n = ' || original);
    DBMS_OUTPUT.PUT_LINE('Reversed number is ' || reversed);
END;
```
## Output:
![image](https://github.com/user-attachments/assets/3196f759-ca57-493d-888a-d3d2f4904635)

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15
## Program:
```
SET SERVEROUTPUT ON;

DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
    largest NUMBER;
BEGIN
    IF a >= b AND a >= c THEN
        largest := a;
    ELSIF b >= a AND b >= c THEN
        largest := b;
    ELSE
        largest := c;
    END IF;

    DBMS_OUTPUT.PUT_LINE('a = ' || a || ', b = ' || b || ', c = ' || c);
    DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || largest);
END;
```
## Output:
![image](https://github.com/user-attachments/assets/101333eb-64a2-4a7c-9a20-3708e49e2d7a)

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.


