![image](https://github.com/user-attachments/assets/1471bb61-22d5-4542-a62f-31861eb43e40)
**
Welcome to **Day 3 of SQL Mastery!** Today, we focus on **aggregation and grouping**, which are essential for summarizing and analyzing data in large datasets. These techniques help in understanding trends, calculating totals, and finding insights within structured data.

## **What You Will Learn Today**
✅ How to count records using `COUNT()`.  
✅ How to calculate totals using `SUM()`.  
✅ How to find averages using `AVG()`.  
✅ How to identify maximum and minimum values using `MAX()` & `MIN()`.  
✅ How to filter grouped results using `HAVING`.  
✅ How to use `ANY`, `ALL`, and `EXCEPT` for advanced filtering.  

---

## 📝 **Exercises**

### **1️⃣ Count the number of employees in each department.**
```sql
SELECT departmentid, COUNT(*) AS EmployeeCount 
FROM employees 
GROUP BY departmentid;
```
✅ **Why?** `COUNT(*)` counts the number of employees in each department.

### **2️⃣ Get the total salary paid per department.**
```sql
SELECT departmentid, SUM(salary) AS TotalSalary 
FROM employees 
GROUP BY departmentid;
```
✅ **Why?** `SUM(salary)` calculates the total payroll for each department.

### **3️⃣ Find the average salary in each department.**
```sql
SELECT departmentid, AVG(salary) AS AverageSalary 
FROM employees 
GROUP BY departmentid;
```
✅ **Why?** `AVG(salary)` helps understand salary trends within departments.

### **4️⃣ Retrieve the highest and lowest salary in each department.**
```sql
SELECT departmentid, MAX(salary) AS HighestSalary, MIN(salary) AS LowestSalary 
FROM employees 
GROUP BY departmentid;
```
✅ **Why?** Helps identify salary ranges within departments.

### **5️⃣ Find departments where the average salary is greater than $80,000 (HAVING).**
```sql
SELECT departmentid, AVG(salary) AS AverageSalary 
FROM employees 
GROUP BY departmentid 
HAVING AVG(salary) > 80000;
```
✅ **Why?** `HAVING` filters aggregated results based on a condition.

### **6️⃣ Get the total salary paid per department, but only for departments with more than 3 employees.**
```sql
SELECT departmentid, SUM(salary) AS TotalSalary 
FROM employees 
GROUP BY departmentid 
HAVING COUNT(*) > 3;
```
✅ **Why?** `HAVING` ensures only departments with at least 3 employees are included.

### **7️⃣ Find the department with the highest number of employees.**
```sql
SELECT departmentid, COUNT(*) AS EmployeeCount 
FROM employees 
GROUP BY departmentid 
ORDER BY EmployeeCount DESC 
LIMIT 1;
```
✅ **Why?** Sorting and limiting results finds the largest department.

### **8️⃣ Retrieve employees whose salary is greater than the average salary of their department.**
```sql
SELECT * FROM employees e 
WHERE salary > (SELECT AVG(salary) FROM employees WHERE departmentid = e.departmentid);
```
✅ **Why?** Helps identify high earners in each department.

### **9️⃣ Get employees who earn more than any employee in the ‘Marketing’ department (ANY).**
```sql
SELECT * FROM employees 
WHERE salary > ANY (SELECT salary FROM employees WHERE departmentid = (SELECT departmentid FROM departments WHERE name = 'Marketing'));
```
✅ **Why?** `ANY` allows comparison against multiple values in a subquery.

### **🔟 Find employees who earn more than all employees in the ‘HR’ department (ALL).**
```sql
SELECT * FROM employees 
WHERE salary > ALL (SELECT salary FROM employees WHERE departmentid = (SELECT departmentid FROM departments WHERE name = 'HR'));
```
✅ **Why?** `ALL` ensures employees earn more than the highest salary in HR.

### **1️⃣1️⃣ Find employees who are not in the ‘Engineering’ department using EXCEPT.**
```sql
SELECT * FROM employees 
EXCEPT 
SELECT * FROM employees WHERE departmentid = (SELECT departmentid FROM departments WHERE name = 'Engineering');
```
✅ **Why?** `EXCEPT` returns records not present in the second query.

### **1️⃣2️⃣ Get the department(s) with the lowest total salary (HAVING & MIN).**
```sql
SELECT departmentid, SUM(salary) AS TotalSalary 
FROM employees 
GROUP BY departmentid 
HAVING SUM(salary) = (SELECT MIN(TotalSalary) FROM (SELECT departmentid, SUM(salary) AS TotalSalary FROM employees GROUP BY departmentid) AS dept_salaries);
```
✅ **Why?** Identifies the lowest-paid department.

### **1️⃣3️⃣ Retrieve the count of employees in each department, but only show departments where at least one employee earns more than $100,000 (HAVING).**
```sql
SELECT departmentid, COUNT(*) AS EmployeeCount 
FROM employees 
GROUP BY departmentid 
HAVING MAX(salary) > 100000;
```
✅ **Why?** Ensures departments with high earners are displayed.

### **1️⃣4️⃣ Find departments that do not have any employees (EXCEPT).**
```sql
SELECT departmentid FROM departments 
EXCEPT 
SELECT DISTINCT departmentid FROM employees;
```
✅ **Why?** Identifies empty departments.

### **1️⃣5️⃣ Retrieve employees who work in a department where at least one person earns more than $90,000 (ANY).**
```sql
SELECT * FROM employees 
WHERE departmentid = ANY (SELECT departmentid FROM employees WHERE salary > 90000);
```
✅ **Why?** Finds employees in departments with high earners.

---

## 🎯 **What You Achieved Today**
✅ You learned how to group and summarize data using SQL.  
✅ You practiced filtering grouped results using `HAVING`.  
✅ You explored `ANY`, `ALL`, and `EXCEPT` for advanced data comparisons.  

🛠 **Next Step:** Continue practicing aggregation with real-world datasets! 🚀
