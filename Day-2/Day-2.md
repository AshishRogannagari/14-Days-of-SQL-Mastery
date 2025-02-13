# 🚀 Day 2: SQL Conditional & Null Handling Exercises

## **Introduction**
Welcome to **Day 2 of SQL Mastery!** Today, we focus on handling conditional logic and working with NULL values in SQL. These techniques are essential for real-world data analysis and reporting, ensuring your queries return meaningful insights even with incomplete or complex datasets. 

![image](https://github.com/user-attachments/assets/f609cd8b-9455-48f4-a4a7-1be25f40b384)

## **What You Will Learn Today**
✅ How to filter records using `BETWEEN`, `IN`, and `IS NULL` operators.  
✅ How to apply conditional logic with `CASE`, `COALESCE`, and `NULLIF`.  
✅ How to check for existence of related records using `EXISTS` and `NOT EXISTS`.  
✅ How to work with missing or unknown values efficiently.  

---

## 📝 **Exercises**

### **1️⃣ Retrieve employees hired between 2018 and 2021.**
```sql
SELECT * FROM employees WHERE hiredate BETWEEN '2018-01-01' AND '2021-12-31';
```
✅ **Why?** `BETWEEN` is useful for filtering data within a date range.

### **2️⃣ Find employees whose salary is between $50,000 and $90,000.**
```sql
SELECT * FROM employees WHERE salary BETWEEN 50000 AND 90000;
```
✅ **Why?** `BETWEEN` helps to filter numerical values within a specified range.

### **3️⃣ Get employees who do not belong to any department (DepartmentID IS NULL).**
```sql
SELECT * FROM employees WHERE departmentid IS NULL;
```
✅ **Why?** `IS NULL` is used to find records where a column has no value.

### **4️⃣ Retrieve employees who have a manager assigned (ManagerID IS NOT NULL).**
```sql
SELECT * FROM employees WHERE managerid IS NOT NULL;
```
✅ **Why?** `IS NOT NULL` ensures we only get employees who have a manager assigned.

### **5️⃣ Find employees earning more than $100,000 OR hired before 2015.**
```sql
SELECT * FROM employees WHERE salary > 100000 OR hiredate < '2015-01-01';
```
✅ **Why?** The `OR` operator lets you combine multiple conditions.

### **6️⃣ Get employees in the ‘Engineering’ department AND earning more than $70,000.**
```sql
SELECT * FROM employees WHERE departmentid = (SELECT departmentid FROM departments WHERE name = 'Engineering') AND salary > 70000;
```
✅ **Why?** This query filters employees based on department and salary using a subquery.

### **7️⃣ Retrieve employees in ‘Marketing’ OR ‘Finance’ hired after 2017.**
```sql
SELECT * FROM employees WHERE departmentid IN (SELECT departmentid FROM departments WHERE name IN ('Marketing', 'Finance')) AND hiredate > '2017-12-31';
```
✅ **Why?** `IN` helps match multiple values from another table.

### **8️⃣ Show employees who do NOT work in the ‘HR’ department.**
```sql
SELECT * FROM employees WHERE departmentid <> (SELECT departmentid FROM departments WHERE name = 'HR');
```
✅ **Why?** The `<>` operator helps exclude specific values.

### **9️⃣ Classify employees’ salaries as ‘High’, ‘Medium’, or ‘Low’ using CASE.**
```sql
SELECT firstname, lastname, salary,
       CASE 
           WHEN salary > 80000 THEN 'High'
           WHEN salary BETWEEN 50000 AND 80000 THEN 'Medium'
           ELSE 'Low' 
       END AS SalaryCategory
FROM employees;
```
✅ **Why?** `CASE` allows dynamic categorization of records.

### **🔟 Replace NULL manager IDs with 'No Manager' using COALESCE.**
```sql
SELECT firstname, lastname, COALESCE(managerid, 'No Manager') AS Manager FROM employees;
```
✅ **Why?** `COALESCE` replaces NULL values with a default value.

### **1️⃣1️⃣ Return NULL if two employees have the same salary using NULLIF.**
```sql
SELECT employeeid, firstname, salary, NULLIF(salary, (SELECT salary FROM employees WHERE employeeid <> e.employeeid LIMIT 1)) AS UniqueSalary FROM employees e;
```
✅ **Why?** `NULLIF` returns NULL if the given values are equal.

### **1️⃣2️⃣ Find employees whose email is missing (IS NULL).**
```sql
SELECT * FROM employees WHERE email IS NULL;
```
✅ **Why?** Helps identify employees missing contact information.

### **1️⃣3️⃣ Retrieve employees who have an entry in the Salaries table (EXISTS).**
```sql
SELECT * FROM employees WHERE EXISTS (SELECT 1 FROM salaries WHERE salaries.employeeid = employees.employeeid);
```
✅ **Why?** `EXISTS` is used for checking related records.

### **1️⃣4️⃣ Get employees who do NOT have salary details in the Salaries table (NOT EXISTS).**
```sql
SELECT * FROM employees WHERE NOT EXISTS (SELECT 1 FROM salaries WHERE salaries.employeeid = employees.employeeid);
```
✅ **Why?** `NOT EXISTS` helps find missing records in related tables.

### **1️⃣5️⃣ Find employees who have a DepartmentID but the department does NOT exist in the Departments table (NOT EXISTS).**
```sql
SELECT * FROM employees WHERE departmentid IS NOT NULL AND NOT EXISTS (SELECT 1 FROM departments WHERE departments.departmentid = employees.departmentid);
```
✅ **Why?** Helps detect orphaned records where foreign key relations are missing.

---

## 🎯 **What You Achieved Today**
✅ You learned how to handle NULL values effectively.  
✅ You practiced advanced filtering using conditional operators.  
✅ You explored `CASE`, `COALESCE`, `NULLIF`, `EXISTS`, and `NOT EXISTS` to handle dynamic data scenarios.  

🛠 **Next Step:** Continue practicing with different datasets and scenarios to strengthen your SQL skills! 🚀

