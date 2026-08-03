# SQL Intermediate - Problem 4 Solutions

---

# Problem 4.1

**Problem Link:**  
https://www.codechef.com/learn/course/sql-intermediate/SQ00BS01/problems/ASQL01D?tab=statement

## Question 1

**Question:**  
List the `customer_name` and `order_date` for all customers who have placed orders.

### Answer

```sql
SELECT c.customer_name, o.order_date
FROM customers c
INNER JOIN orders o
ON c.customer_id = o.customer_id;
```

---

## Question 2

**Question:**  
List all customer names and their corresponding `product_name` from orders, if they have any. Include customers even if they haven't placed any orders.

### Answer

```sql
SELECT c.customer_name, o.product_name
FROM customers c
LEFT JOIN orders o
ON c.customer_id = o.customer_id;
```

---

## Question 3

**Question:**  
Display the `product_name` and `order_date` for all the products that are ordered.

### Answer

```sql
SELECT p.product_name, o.order_date
FROM products p
INNER JOIN orders o
ON p.product_name = o.product_name;
```

---

# Problem 4.2

**Problem Link:**  
https://www.codechef.com/learn/course/sql-intermediate/SQ00BS01/problems/GSQ63?tab=statement

## Question 1

**Question:**  
JOIN the `student` and `course` tables using `Course_id` to match both the tables and output the joined table.

### Answer

```sql
SELECT *
FROM student
JOIN course
ON student.Course_id = course.Course_id;
```

---

## Question 2

**Question:**  
LEFT JOIN the `student` and `course` tables using `Course_id` to match both the tables and output the joined table.

### Answer

```sql
SELECT *
FROM student
LEFT JOIN course
ON student.Course_id = course.Course_id;
```

---

# Problem 4.3

**Problem Link:**  
https://www.codechef.com/learn/course/sql-intermediate/SQ00BS01/problems/ASQL01B?tab=Submissions

## Question

**Question:**  
FULL OUTER JOIN the `student` and `course` tables using `Course_id` to match the tables. Output the joined table.

### Answer

```sql
SELECT *
FROM student
FULL OUTER JOIN course
ON student.Course_id = course.Course_id;
```

---

# Problem 4.4

**Problem Link:**  
https://www.codechef.com/learn/course/sql-intermediate/SQ00BS01/problems/ASQL01E?tab=Submissions

## Question 1

**Question:**  
Get all of the orders table and also the details of the respective customers if they exist. Use the `customers` and `orders` tables.

### Answer

```sql
SELECT c.customer_name, o.*
FROM customers c
RIGHT JOIN orders o
ON c.customer_id = o.customer_id;
```

---

## Question 2

**Question:**  
Create a combined list of all products and all categories. Include all product names and all category names. Where there's a match, show both; otherwise, use `NULL`s.

### Answer

```sql
SELECT p.product_name, c.category_name
FROM products p
FULL OUTER JOIN categories c
ON p.category_id = c.category_id;
```

---

## Question 3

**Question:**  
Display `category_name`, along with all `product_name` and `price` from all the categories present in the `categories` table.

### Answer

```sql
SELECT c.category_name, p.product_name, p.price
FROM products p
RIGHT JOIN categories c
ON p.category_id = c.category_id;
```

---

# Problem 4.5

**Problem Link:**  
https://www.codechef.com/learn/course/sql-intermediate/SQ00BS01/problems/ASQL01F?tab=statement

## Question 1

**Question:**  
Display a list of employee names along with their manager's names. Use the `employees` table provided.

### Answer

```sql
SELECT e1.employee_name AS Employee, e2.employee_name AS Manager
FROM employees e1
LEFT JOIN employees e2
ON e1.manager_id = e2.employee_id;
```

---

## Question 2

**Question:**  
Show every possible combination of `customer_name` from the `customers` table and `product_name` from the `products` table.

### Answer

```sql
SELECT c.customer_name, p.product_name
FROM customers c
CROSS JOIN products p;
```

---

# Problem 4.6

**Problem Link:**  
https://www.codechef.com/learn/course/sql-intermediate/SQ00BS01/problems/ASQL01C

## Question 1

**Question:**  
Display pairs of students who belong to the same department.

### Answer

```sql
SELECT
    s1.St_id,
    s1.St_Name,
    s1.Department,
    s2.St_id,
    s2.St_Name,
    s2.Department
FROM student AS s1
INNER JOIN student AS s2
ON s1.Department = s2.Department
AND s1.St_id != s2.St_id;
```

---

## Question 2

**Question:**  
Display the details of students who share the same `Course_id` with another student.

### Answer

```sql
SELECT DISTINCT
    s1.St_id,
    s1.St_Name,
    s1.Course_id
FROM student AS s1
INNER JOIN student AS s2
ON s1.Course_id = s2.Course_id
AND s1.St_id != s2.St_id
ORDER BY s1.Course_id;
```