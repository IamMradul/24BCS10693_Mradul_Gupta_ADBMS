# SQL Intermediate - Problem Set 3

## Problem 3.1
**Problem Link:** https://www.codechef.com/learn/course/sql-intermediate/SQ00BS08/problems/GSQ82

### Solution
```sql
SELECT department,
       COUNT(CASE WHEN Marks > 80 THEN 1 END) AS Dept_HighScore_Count
FROM student
GROUP BY department;
```

---

## Problem 3.2

### Create Table
```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(100) NOT NULL,
    emp_salary DECIMAL(10, 2) NOT NULL,
    emp_city VARCHAR(100) NOT NULL
);
```

### Insert Data
```sql
INSERT INTO employees (emp_id, emp_name, emp_salary, emp_city) VALUES
(101, 'Amit Sharma', 85000.00, 'Mumbai'),
(102, 'Priya Patel', 95000.00, 'Mumbai'),
(103, 'Rahul Verma', 60000.00, 'Delhi'),
(104, 'Ananya Iyer', 110000.00, 'Bangalore'),
(105, 'Vikram Singh', 55000.00, 'Delhi'),
(106, 'Sneha Reddy', 105000.00, 'Bangalore'),
(107, 'Rohan Das', 72000.00, 'Kolkata');
```

### Aggregate Functions
- `SUM()`
- `MIN()`
- `MAX()`
- `AVG()`
- `COUNT()`

---

### 1. Count the Number of Employees in Each City

#### Method 1
```sql
SELECT EMP_CITY,
       COUNT(*) AS CNT
FROM EMPLOYEES
GROUP BY EMP_CITY;
```

#### Method 2
```sql
SELECT EMP_CITY,
       COUNT(EMP_ID) AS CNT
FROM EMPLOYEES
GROUP BY EMP_CITY;
```

---

### 2. Count the Number of Employees in Each City Whose Salary is Greater Than or Equal to 90,000

```sql
SELECT EMP_CITY,
       SUM(CASE WHEN EMP_SALARY >= 90000 THEN 1 ELSE 0 END) AS CNT
FROM EMPLOYEES
GROUP BY EMP_CITY;
```

---

### 3. Count Employees with Salary ≥ 90,000 and Sort by City Name (Descending)

```sql
SELECT EMP_CITY,
       SUM(CASE WHEN EMP_SALARY >= 90000 THEN 1 ELSE 0 END) AS CNT
FROM EMPLOYEES
GROUP BY EMP_CITY
ORDER BY EMP_CITY DESC;
```

---

### 4. Count Employees with Salary ≥ 90,000 and Sort by Count (Descending)

```sql
SELECT EMP_CITY,
       SUM(CASE WHEN EMP_SALARY >= 90000 THEN 1 ELSE 0 END) AS CNT
FROM EMPLOYEES
GROUP BY EMP_CITY
ORDER BY CNT DESC, EMP_CITY DESC;
```

---

### 5. Find the Cities Having at Least Two Employees

```sql
SELECT EMP_CITY AS CNT
FROM EMPLOYEES
GROUP BY EMP_CITY
HAVING COUNT(EMP_ID) >= 2;
```

---

### 6. Find Distinct Cities

```sql
SELECT DISTINCT EMP_CITY
FROM EMPLOYEES;
```

---

## Problem 3.3
**Problem Link:** https://leetcode.com/problems/customers-who-never-order/description/

### Solution
```sql
SELECT name AS Customers
FROM Customers
WHERE id NOT IN (
    SELECT customerId
    FROM Orders
);
```