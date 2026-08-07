# SQL Set Operations

## Problem 2.1 – UNION

**Problem Link:**  
https://www.codechef.com/learn/course/sql-intermediate/SQ00BS02/problems/GSQ66?tab=solution

### Solution

```sql
SELECT *
FROM Arts

UNION

SELECT *
FROM Science;
```

---

## Problem 2.2 – UNION ALL

**Problem Link:**  
https://www.codechef.com/learn/course/sql-intermediate/SQ00BS07/problems/GSQ78A

### Solution

```sql
SELECT emp_name
FROM employee

UNION ALL

SELECT emp_name
FROM pt_employee;
```

---

## Problem 2.3 – INTERSECT

**Problem Link:**  
https://www.codechef.com/learn/course/sql-intermediate/SQ00BS06/problems/GSQ76

### Solution

```sql
SELECT f_name
FROM fruit

INTERSECT

SELECT inv_name
FROM inventory;
```

---

## Problem 2.4 – EXCEPT

**Problem Link:**  
https://www.codechef.com/learn/course/sql-intermediate/SQ00BS06/problems/GSQ77

### Solution

```sql
SELECT f_name
FROM fruit

EXCEPT

SELECT inv_name
FROM inventory;
```