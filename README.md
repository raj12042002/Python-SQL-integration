# Python-SQL-integration
Python Application         |         | Database Connector         |         | SQL Database (MySQL/PostgreSQL/SQLite) import mysql.connector  conn = mysql.connector.connect(     host="localhost",     user="root",     password="password",     database="company" )  print("Connected Successfully")

### Python-SQL Integration

**Definition:**
Python-SQL Integration refers to connecting Python applications with SQL databases to perform operations such as creating tables, inserting data, updating records, deleting records, and retrieving information.

Python acts as the application layer, while SQL databases (MySQL, PostgreSQL, SQLite, SQL Server, Oracle) store and manage the data.

---

## Why Use Python-SQL Integration?

* Automate database operations
* Build web applications
* Generate reports and analytics
* Process large datasets
* Perform CRUD operations (Create, Read, Update, Delete)
* Monitor server and application data

---

## Architecture

```text
Python Application
        |
        |
Database Connector
        |
        |
SQL Database
(MySQL/PostgreSQL/SQLite)
```

---

## Example Using SQLite

### Step 1: Connect to Database

```python
import sqlite3

conn = sqlite3.connect("employee.db")

print("Database Connected Successfully")
```

---

### Step 2: Create Table

```python
import sqlite3

conn = sqlite3.connect("employee.db")

cursor = conn.cursor()

cursor.execute("""
CREATE TABLE IF NOT EXISTS employees(
id INTEGER PRIMARY KEY,
name TEXT,
salary INTEGER
)
""")

conn.commit()

print("Table Created Successfully")
```

---

### Step 3: Insert Data

```python
import sqlite3

conn = sqlite3.connect("employee.db")

cursor = conn.cursor()

cursor.execute("""
INSERT INTO employees(name,salary)
VALUES('Rahul',50000)
""")

conn.commit()

print("Data Inserted Successfully")
```

---

### Step 4: Retrieve Data

```python
import sqlite3

conn = sqlite3.connect("employee.db")

cursor = conn.cursor()

cursor.execute("SELECT * FROM employees")

rows = cursor.fetchall()

for row in rows:
    print(row)
```

**Output**

```text
(1, 'Rahul', 50000)
```

---

### Step 5: Update Data

```python
cursor.execute("""
UPDATE employees
SET salary=60000
WHERE id=1
""")

conn.commit()
```

---

### Step 6: Delete Data

```python
cursor.execute("""
DELETE FROM employees
WHERE id=1
""")

conn.commit()
```

---

## MySQL Integration Example

### Install Package

```bash
pip install mysql-connector-python
```

### Connect MySQL Database

```python
import mysql.connector

conn = mysql.connector.connect(
    host="localhost",
    user="root",
    password="password",
    database="company"
)

print("Connected Successfully")
```

---

## DevOps Monitoring Example

Store Linux Server Monitoring Data into SQL Database.

### Python

```python
import sqlite3
import psutil

cpu = psutil.cpu_percent()
memory = psutil.virtual_memory().percent
disk = psutil.disk_usage('/').percent

conn = sqlite3.connect("monitor.db")

cursor = conn.cursor()

cursor.execute("""
CREATE TABLE IF NOT EXISTS metrics(
cpu REAL,
memory REAL,
disk REAL
)
""")

cursor.execute("""
INSERT INTO metrics(cpu,memory,disk)
VALUES(?,?,?)
""",(cpu,memory,disk))

conn.commit()

print("Metrics Stored Successfully")
```

---

### SQL Query

```sql
SELECT *
FROM metrics;
```

---

## Interview Answer

**Q: What is Python-SQL Integration?**

**Answer:**
Python-SQL Integration is the process of connecting Python applications with SQL databases to perform database operations such as inserting, retrieving, updating, and deleting data. Python uses database connectors like `sqlite3`, `mysql-connector-python`, `psycopg2`, or `SQLAlchemy` to communicate with databases. It is widely used in web development, automation, data analysis, reporting, and DevOps monitoring solutions.

### Short Interview Answer

> Python-SQL Integration allows Python programs to interact with SQL databases for storing, retrieving, updating, and managing data. It is commonly used for automation, reporting, analytics, and application development.



# Complete SQL & MySQL with Python-SQL Integration (Codes Included)

## 1. Getting Started with SQL and MySQL

### What is SQL?

SQL (Structured Query Language) is used to communicate with databases.

### Structured Data Example

```text
Employee Table
+----+--------+--------+
| ID | Name   | Salary |
+----+--------+--------+
| 1  | Rahul  | 50000  |
| 2  | Amit   | 60000  |
+----+--------+--------+
```

### Unstructured Data Example

```text
Images
Videos
PDF Files
Emails
Social Media Posts
```

---

# 2. DDL (Data Definition Language)

## CREATE DATABASE

```sql
CREATE DATABASE company;
```

## USE DATABASE

```sql
USE company;
```

## CREATE TABLE

```sql
CREATE TABLE employee(
id INT PRIMARY KEY,
name VARCHAR(50),
salary INT
);
```

---

## ALTER TABLE

Add Column

```sql
ALTER TABLE employee
ADD department VARCHAR(30);
```

Modify Column

```sql
ALTER TABLE employee
MODIFY salary BIGINT;
```

---

## DROP TABLE

```sql
DROP TABLE employee;
```

---

## TRUNCATE TABLE

```sql
TRUNCATE TABLE employee;
```

---

## RENAME TABLE

```sql
RENAME TABLE employee TO emp;
```

---

# Constraints

## Primary Key

```sql
CREATE TABLE student(
id INT PRIMARY KEY,
name VARCHAR(50)
);
```

---

## Foreign Key

```sql
CREATE TABLE department(
dept_id INT PRIMARY KEY,
dept_name VARCHAR(50)
);

CREATE TABLE employee(
emp_id INT PRIMARY KEY,
emp_name VARCHAR(50),
dept_id INT,
FOREIGN KEY(dept_id)
REFERENCES department(dept_id)
);
```

---

## NOT NULL

```sql
CREATE TABLE customer(
id INT,
name VARCHAR(50) NOT NULL
);
```

---

## UNIQUE

```sql
CREATE TABLE users(
id INT,
email VARCHAR(100) UNIQUE
);
```

---

# 3. DML Commands

## INSERT

```sql
INSERT INTO employee
VALUES(1,'Rahul',50000);
```

---

## SELECT

```sql
SELECT * FROM employee;
```

---

## WHERE

```sql
SELECT *
FROM employee
WHERE salary > 40000;
```

---

## AND

```sql
SELECT *
FROM employee
WHERE salary > 40000
AND department='IT';
```

---

## OR

```sql
SELECT *
FROM employee
WHERE department='IT'
OR department='HR';
```

---

## NOT

```sql
SELECT *
FROM employee
WHERE NOT department='HR';
```

---

## UPDATE

```sql
UPDATE employee
SET salary=70000
WHERE id=1;
```

---

## DELETE

```sql
DELETE FROM employee
WHERE id=1;
```

---

## MERGE (SQL Server)

```sql
MERGE target_table t
USING source_table s
ON t.id=s.id
WHEN MATCHED THEN
UPDATE SET t.name=s.name
WHEN NOT MATCHED THEN
INSERT(id,name)
VALUES(s.id,s.name);
```

---

# 4. TCL (Transaction Control Language)

## COMMIT

```sql
COMMIT;
```

---

## ROLLBACK

```sql
ROLLBACK;
```

---

# DCL (Data Control Language)

## GRANT

```sql
GRANT SELECT,INSERT
ON employee
TO user1;
```

---

## REVOKE

```sql
REVOKE INSERT
ON employee
FROM user1;
```

---

## DENY (SQL Server)

```sql
DENY DELETE
ON employee
TO user1;
```

---

# 5. Aggregate Functions

## COUNT

```sql
SELECT COUNT(*)
FROM employee;
```

---

## SUM

```sql
SELECT SUM(salary)
FROM employee;
```

---

## AVG

```sql
SELECT AVG(salary)
FROM employee;
```

---

## MIN

```sql
SELECT MIN(salary)
FROM employee;
```

---

## MAX

```sql
SELECT MAX(salary)
FROM employee;
```

---

# GROUP BY

```sql
SELECT department,
COUNT(*)
FROM employee
GROUP BY department;
```

---

# ORDER BY

```sql
SELECT *
FROM employee
ORDER BY salary DESC;
```

---

# HAVING

```sql
SELECT department,
AVG(salary)
FROM employee
GROUP BY department
HAVING AVG(salary)>50000;
```

---

# 6. Joins

## Inner Join

```sql
SELECT e.emp_name,
d.dept_name
FROM employee e
INNER JOIN department d
ON e.dept_id=d.dept_id;
```

---

## Left Join

```sql
SELECT *
FROM employee e
LEFT JOIN department d
ON e.dept_id=d.dept_id;
```

---

## Right Join

```sql
SELECT *
FROM employee e
RIGHT JOIN department d
ON e.dept_id=d.dept_id;
```

---

## Full Outer Join

```sql
SELECT *
FROM employee e
FULL OUTER JOIN department d
ON e.dept_id=d.dept_id;
```

---

## Cross Join

```sql
SELECT *
FROM employee
CROSS JOIN department;
```

---

# 7. Connecting MySQL Database in Python

Install Connector

```bash
pip install mysql-connector-python
```

---

## Connect Database

```python
import mysql.connector

conn=mysql.connector.connect(
host="localhost",
user="root",
password="root123",
database="company"
)

print("Connected Successfully")
```

---

## Create Table Using Python

```python
import mysql.connector

conn=mysql.connector.connect(
host="localhost",
user="root",
password="root123",
database="company"
)

cursor=conn.cursor()

cursor.execute("""
CREATE TABLE employee(
id INT PRIMARY KEY,
name VARCHAR(50),
salary INT
)
""")

conn.commit()
```

---

## Insert Data

```python
cursor.execute("""
INSERT INTO employee
VALUES(1,'Rahul',50000)
""")

conn.commit()
```

---

## Fetch Data

```python
cursor.execute(
"SELECT * FROM employee"
)

rows=cursor.fetchall()

for row in rows:
    print(row)
```

---

## Update Data

```python
cursor.execute("""
UPDATE employee
SET salary=60000
WHERE id=1
""")

conn.commit()
```

---

## Delete Data

```python
cursor.execute("""
DELETE FROM employee
WHERE id=1
""")

conn.commit()
```

---

# 8. SQL Mini Project

## Employee Management System

### Create Table

```sql
CREATE TABLE employees(
id INT PRIMARY KEY,
name VARCHAR(50),
department VARCHAR(30),
salary INT
);
```

### Insert Data

```sql
INSERT INTO employees
VALUES
(1,'Rahul','IT',50000),
(2,'Amit','HR',45000),
(3,'Neha','IT',70000);
```

---

### Report Queries

Highest Salary

```sql
SELECT *
FROM employees
ORDER BY salary DESC
LIMIT 1;
```

Average Salary

```sql
SELECT AVG(salary)
FROM employees;
```

Department Wise Salary

```sql
SELECT department,
AVG(salary)
FROM employees
GROUP BY department;
```

---

# 9. Database Design Project

## Library Management System

### Books

```sql
CREATE TABLE books(
book_id INT PRIMARY KEY,
title VARCHAR(100),
author VARCHAR(100)
);
```

### Members

```sql
CREATE TABLE members(
member_id INT PRIMARY KEY,
name VARCHAR(50)
);
```

### Issue Books

```sql
CREATE TABLE issue_book(
issue_id INT PRIMARY KEY,
book_id INT,
member_id INT,
FOREIGN KEY(book_id)
REFERENCES books(book_id),
FOREIGN KEY(member_id)
REFERENCES members(member_id)
);
```

---

# 10. SQL Data Analysis Project

### Total Employees

```sql
SELECT COUNT(*)
FROM employees;
```

### Highest Salary

```sql
SELECT MAX(salary)
FROM employees;
```

### Lowest Salary

```sql
SELECT MIN(salary)
FROM employees;
```

### Average Salary

```sql
SELECT AVG(salary)
FROM employees;
```

### Department Wise Count

```sql
SELECT department,
COUNT(*)
FROM employees
GROUP BY department;
```

---

# 11. Python-SQL Integration Project (DevOps Monitoring)

## Create Monitoring Table

```sql
CREATE TABLE server_metrics(
id INT AUTO_INCREMENT PRIMARY KEY,
cpu FLOAT,
memory FLOAT,
disk FLOAT,
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## Python Monitoring Script

```python
import mysql.connector
import psutil

cpu=psutil.cpu_percent()
memory=psutil.virtual_memory().percent
disk=psutil.disk_usage('/').percent

conn=mysql.connector.connect(
host='localhost',
user='root',
password='root123',
database='company'
)

cursor=conn.cursor()

cursor.execute("""
INSERT INTO server_metrics
(cpu,memory,disk)
VALUES(%s,%s,%s)
""",(cpu,memory,disk))

conn.commit()

print("Metrics Stored")
```

---

## Analysis Query

```sql
SELECT
AVG(cpu) AS avg_cpu,
AVG(memory) AS avg_memory,
AVG(disk) AS avg_disk
FROM server_metrics;
```
**SQL basics → DDL → DML → TCL/DCL → Joins → MySQL → Python Integration → Mini Projects → Data Analysis → DevOps Monitoring Project** with working code examples.


# Handling Errors and Exceptions in Python (Hinglish)

## Error Kya Hota Hai?

Error ek problem hoti hai jo program ko successfully run hone se rok deti hai.

### Example

```python
print(10/0)
```

Output:

```text
ZeroDivisionError: division by zero
```

Yaha program crash ho jayega kyunki kisi number ko 0 se divide nahi kar sakte.

---

# Exception Kya Hota Hai?

Exception ek runtime error hai jo program execute hone ke dauran aata hai.

Examples:

* ZeroDivisionError
* ValueError
* TypeError
* IndexError
* KeyError
* FileNotFoundError

---

# Why Exception Handling?

Without Exception Handling:

```python
num = int(input("Enter Number: "))
print(100/num)
```

Agar user 0 enter kare:

```text
ZeroDivisionError
```

Program immediately band ho jayega.

Exception Handling use karne se program crash nahi hota.

---

# Try and Except Block

### Syntax

```python
try:
    # risky code
except:
    # error handling code
```

### Example

```python
try:
    num = int(input("Enter Number: "))
    print(100/num)

except:
    print("Some Error Occurred")
```

Output:

```text
Enter Number: 0
Some Error Occurred
```

---

# Specific Exception Handling

### ZeroDivisionError

```python
try:
    num = int(input("Enter Number: "))
    print(100/num)

except ZeroDivisionError:
    print("Cannot divide by zero")
```

Output:

```text
Cannot divide by zero
```

---

# Multiple Exceptions

```python
try:
    num = int(input("Enter Number: "))
    print(100/num)

except ZeroDivisionError:
    print("Division by Zero Error")

except ValueError:
    print("Invalid Input")
```

Output:

```text
Enter Number: abc

Invalid Input
```

---

# Using Else Block

Else tab execute hota hai jab koi exception nahi aati.

```python
try:
    num = int(input("Enter Number: "))
    result = 100/num

except ZeroDivisionError:
    print("Cannot divide by zero")

else:
    print("Result =", result)
```

Output:

```text
Enter Number: 10
Result = 10.0
```

---

# Using Finally Block

Finally block hamesha execute hota hai.

Chahe exception aaye ya na aaye.

```python
try:
    print("Program Started")

except:
    print("Error")

finally:
    print("Program Ended")
```

Output:

```text
Program Started
Program Ended
```

---

# Complete Example

```python
try:
    num = int(input("Enter Number: "))

    result = 100/num

except ZeroDivisionError:
    print("Number cannot be zero")

except ValueError:
    print("Enter only numeric value")

else:
    print("Result =", result)

finally:
    print("Execution Completed")
```

---

# File Handling Exception

```python
try:
    file = open("data.txt","r")

except FileNotFoundError:
    print("File Not Found")
```

Output:

```text
File Not Found
```

---

# IndexError Example

```python
try:
    lst = [10,20,30]

    print(lst[5])

except IndexError:
    print("Index Out Of Range")
```

Output:

```text
Index Out Of Range
```

---

# KeyError Example

```python
try:
    student = {
        "name":"Rahul"
    }

    print(student["age"])

except KeyError:
    print("Key Not Found")
```

Output:

```text
Key Not Found
```

---

# TypeError Example

```python
try:
    result = "10" + 10

except TypeError:
    print("Cannot add string and integer")
```

Output:

```text
Cannot add string and integer
```

---

# Raising Custom Exception

Hum khud bhi exception generate kar sakte hain.

```python
age = int(input("Enter Age: "))

if age < 18:
    raise Exception("Not Eligible")

print("Eligible")
```

Output:

```text
Exception: Not Eligible
```

---

# Custom Exception Class

```python
class InvalidAgeError(Exception):
    pass

age = 15

if age < 18:
    raise InvalidAgeError(
        "Age must be 18 or above"
    )
```

---

# Interview Questions & Answers

### Q1. What is an Exception?

**Answer:**
Exception is a runtime error that occurs during program execution and can interrupt the normal flow of the program.

**Hinglish:**
Exception ek runtime error hai jo program execute hote waqt aata hai aur program ke normal flow ko rok sakta hai.

---

### Q2. What is the difference between Error and Exception?

| Error           | Exception         |
| --------------- | ----------------- |
| Serious problem | Runtime problem   |
| Hard to recover | Can be handled    |
| Program crashes | Program continues |

---

### Q3. Why use Try-Except?

**Answer:**
Try-Except is used to handle runtime errors and prevent program crashes.

**Hinglish:**
Try-Except runtime errors ko handle karne ke liye use hota hai taki program crash na ho.

---

### Q4. What is Finally Block?

**Answer:**
Finally block always executes whether exception occurs or not.

**Hinglish:**
Finally block hamesha execute hota hai chahe exception aaye ya na aaye.

---

### Q5. What is Raise?

**Answer:**
Raise keyword is used to manually generate an exception.

**Hinglish:**
Raise keyword ka use khud se exception generate karne ke liye kiya jata hai.

---

# Real-Life Example

Imagine:

```text
ATM Machine
```

Normal Flow:

```text
Insert Card
Enter PIN
Withdraw Money
```

Exception:

```text
Wrong PIN
```

Instead of crashing:

```text
"Invalid PIN, Please Try Again"
```

Yahi Exception Handling ka purpose hai.

---

# One-Line Interview Answer

**"Exception Handling in Python is a mechanism used to detect and handle runtime errors using try, except, else, finally, and raise statements, ensuring that the program continues to run smoothly without crashing."**


