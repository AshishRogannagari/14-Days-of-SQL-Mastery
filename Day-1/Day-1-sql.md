# SQL Practice: Mastering Essential Queries

## Introduction
Structured Query Language (SQL) is a powerful tool used to interact with relational databases. This repository contains SQL queries to help you practice and understand different SQL operations. 

### **What You Will Learn**
We will focus on different categories of SQL operations, including:
1. **Basic Data Retrieval** – Using `SELECT`, `DISTINCT`, `WHERE`, and `ORDER BY`.
2. **Filtering Data** – Applying conditions with `WHERE`, `LIKE`, `BETWEEN`, and `IN`.
3. **Sorting and Limiting Results** – Using `ORDER BY` and `LIMIT`.
4. **Aggregations & Grouping** – `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()`, and `GROUP BY`.
5. **Advanced Queries** – `HAVING`, `OFFSET`, and working with NULL values.

---

## **Setting Up the Database**

### **1️⃣ Creating the Employees Table**
```sql
CREATE TABLE employees (
    employeeid INT PRIMARY KEY AUTO_INCREMENT,
    firstname VARCHAR(50) NOT NULL,
    lastname VARCHAR(50) NOT NULL,
    salary DECIMAL(10,2) NOT NULL,
    hiredate DATE NOT NULL,
    departmentid INT,
    managerid INT
);
```

### **2️⃣ Inserting Sample Data**
```sql
INSERT INTO employees (firstname, lastname, salary, hiredate, departmentid, managerid) VALUES
('John', 'Doe', 60000, '2018-06-15', 1, NULL),
('Jane', 'Smith', 75000, '2017-03-20', 2, 1),
('Robert', 'Johnson', 50000, '2019-09-10', 1, 1),
('Emily', 'Davis', 85000, '2015-05-30', 3, 2),
('Michael', 'Brown', 40000, '2021-07-25', 2, 2);
```

---

## **SQL Queries for Practice**

### **1️⃣ Basic Data Retrieval**
- Retrieve all employees' first name, last name, salary, and hire date:
  ```sql
  SELECT firstname, lastname, salary, hiredate FROM employees;
  ```
- Get unique department IDs from employees:
  ```sql
  SELECT DISTINCT departmentid FROM employees;
  ```

### **2️⃣ Filtering Data**
- Find employees who earn more than $50,000:
  ```sql
  SELECT firstname, salary FROM employees WHERE salary >= 50000;
  ```
- Get employees hired before 2020 but earning more than $80,000:
  ```sql
  SELECT firstname, hiredate, salary FROM employees WHERE hiredate < '2020-01-01' AND salary > 80000;
  ```
- Retrieve employees from DepartmentID 2 OR who earn less than $40,000:
  ```sql
  SELECT * FROM employees WHERE departmentid = 2 OR salary < 40000;
  ```

### **3️⃣ Sorting & Limiting Results**
- Show the top 5 highest-paid employees:
  ```sql
  SELECT firstname, salary FROM employees ORDER BY salary DESC LIMIT 5;
  ```
- Get the oldest 3 employees (by hire date):
  ```sql
  SELECT firstname, hiredate FROM employees ORDER BY hiredate ASC LIMIT 3;
  ```

### **4️⃣ Aggregations & Grouping**
- Count the number of employees:
  ```sql
  SELECT COUNT(*) AS EmployeeCount FROM employees;
  ```
- Find the total salary of all employees:
  ```sql
  SELECT SUM(salary) FROM employees;
  ```
- Get the average salary of all employees:
  ```sql
  SELECT AVG(salary) AS AvgSalary FROM employees;
  ```
- Find the highest and lowest salary:
  ```sql
  SELECT MIN(salary) AS MinSalary, MAX(salary) AS MaxSalary FROM employees;
  ```
- Find the average salary per department:
  ```sql
  SELECT departmentid, AVG(salary) FROM employees GROUP BY departmentid;
  ```
- Count how many employees are in each department:
  ```sql
  SELECT departmentid, COUNT(*) FROM employees GROUP BY departmentid;
  ```
- Get departments with an average salary greater than $70,000:
  ```sql
  SELECT departmentid, AVG(salary) FROM employees GROUP BY departmentid HAVING AVG(salary) > 70000;
  ```

### **5️⃣ Advanced Queries**
- Find the 5th highest salary:
  ```sql
  SELECT DISTINCT salary FROM employees ORDER BY salary DESC LIMIT 1 OFFSET 4;
  ```
- Find employees who do not have a manager:
  ```sql
  SELECT * FROM employees WHERE managerid IS NULL;
  ```
- Retrieve employees whose first names start with ‘J’:
  ```sql
  SELECT firstname FROM employees WHERE firstname LIKE 'J%';
  ```
- Get employees hired in the year 2020:
  ```sql
  SELECT * FROM employees WHERE YEAR(hiredate) = 2020;
  ```
- Count the number of employees in each department and sort them in descending order:
  ```sql
  SELECT departmentid, COUNT(*) AS EmployeeCount FROM employees GROUP BY departmentid ORDER BY EmployeeCount DESC;
  ```
- Get the highest salary for each department:
  ```sql
  SELECT departmentid, MAX(salary) AS HighestSalary FROM employees GROUP BY departmentid;
  ```

---

## **How to Use**
1. Copy and paste these queries into an SQL database (MySQL, PostgreSQL, or any SQL-supported tool).
2. Modify the queries based on your dataset requirements.
3. Practice and tweak queries to explore different functionalities.

**Happy Querying! 🚀**
