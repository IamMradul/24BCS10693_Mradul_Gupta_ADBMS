# Experiment 6.1: Create a Simple View

## Create the `employees` Table

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(100) NOT NULL,
    emp_salary DECIMAL(10, 2) NOT NULL,
    emp_city VARCHAR(100) NOT NULL
);
```

## Insert Data into the Table

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

## Display All Employees

```sql
SELECT * FROM employees;
```

## Create a Simple View

```sql
CREATE VIEW EMP_KRG AS 
SELECT emp_id, emp_name
FROM employees;
```

## Display the View

```sql
SELECT * FROM EMP_KRG;
```

## Delete a Record from the View

```sql
DELETE FROM EMP_KRG
WHERE emp_id = 101;
```

## Display the Updated View

```sql
SELECT * FROM EMP_KRG;
```

---

# Experiment 6.2: Create a Materialized View

## Create a Materialized View

```sql
CREATE MATERIALIZED VIEW EMP_KRG_MAT AS 
SELECT emp_id, emp_name
FROM employees
WITH NO DATA;
```

## Display the Materialized View

```sql
SELECT * FROM EMP_KRG_MAT;
```

## Refresh the Materialized View

```sql
REFRESH MATERIALIZED VIEW EMP_KRG_MAT;
```

## Display the Refreshed Materialized View

```sql
SELECT * FROM EMP_KRG_MAT;
```