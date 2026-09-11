# PL/SQL Questions

## Question 1: Update Employee Salary Using SQL%ROWCOUNT

### Create Employee Table

```sql
CREATE TABLE EMPLOYEE (
    empId NUMBER PRIMARY KEY,
    name VARCHAR2(15) NOT NULL,
    dept VARCHAR2(10) NOT NULL,
    salary INTEGER
);
```

### Insert Records

```sql
INSERT INTO EMPLOYEE VALUES (1, 'Clark', 'Sales', 100000);
INSERT INTO EMPLOYEE VALUES (2, 'Dave', 'Accounting', 200000);
INSERT INTO EMPLOYEE VALUES (3, 'Ava', 'Sales', 150000);
```

### Fetch Records

```sql
SELECT * FROM EMPLOYEE;
```

### PL/SQL Program

Update the salary of the employee with `empId = 1` by 10% and display the number of rows affected using `SQL%ROWCOUNT`.

```sql
BEGIN

    UPDATE EMPLOYEE
    SET salary = salary * 1.1
    WHERE empId = 1;

    IF SQL%ROWCOUNT > 0 THEN
        DBMS_OUTPUT.PUT_LINE(SQL%ROWCOUNT || ' rows affected');
    ELSE
        DBMS_OUTPUT.PUT_LINE('No rows affected');
    END IF;

END;
/
```

### Output

```text
1 rows affected
```

---

# Question 2: Update Employee Salary Using Explicit Cursor

## Create Employee Table

```sql
CREATE TABLE EMPLOYEE (
    empId NUMBER PRIMARY KEY,
    name VARCHAR2(15) NOT NULL,
    dept VARCHAR2(10) NOT NULL,
    salary INTEGER
);
```

## Insert Records

```sql
INSERT INTO EMPLOYEE VALUES (1, 'Clark', 'Sales', 100000);
INSERT INTO EMPLOYEE VALUES (2, 'Dave', 'Accounting', 200000);
INSERT INTO EMPLOYEE VALUES (3, 'Ava', 'Sales', 150000);
```

## Fetch Records

```sql
SELECT * FROM EMPLOYEE;
```

## PL/SQL Program

Create an explicit cursor to fetch employee IDs and salaries. If an employee's salary is `0`, raise a custom exception. Otherwise, increase the employee's salary by 10%.

```sql
DECLARE

    CURSOR emp_cursor IS
        SELECT empId, salary
        FROM EMPLOYEE;

    V_EMP_ID EMPLOYEE.empId%TYPE;
    V_SALARY EMPLOYEE.salary%TYPE;

    SALARY_ZERO EXCEPTION;

BEGIN

    OPEN emp_cursor;

    FETCH emp_cursor INTO V_EMP_ID, V_SALARY;

    WHILE emp_cursor%FOUND LOOP

        IF V_SALARY = 0 THEN
            RAISE SALARY_ZERO;
        END IF;

        UPDATE EMPLOYEE
        SET salary = salary * 1.10
        WHERE empId = V_EMP_ID;

        FETCH emp_cursor INTO V_EMP_ID, V_SALARY;

    END LOOP;

    CLOSE emp_cursor;

EXCEPTION

    WHEN SALARY_ZERO THEN
        DBMS_OUTPUT.PUT_LINE(
            'Salary is zero. Increment not possible.'
        );

END;
/
```

---

## Important Concepts

### SQL%ROWCOUNT

`SQL%ROWCOUNT` returns the number of rows affected by the most recent SQL statement.

```sql
SQL%ROWCOUNT
```

---

### Explicit Cursor Steps

```text
DECLARE
   ↓
OPEN
   ↓
FETCH
   ↓
CHECK %FOUND
   ↓
PROCESS DATA
   ↓
FETCH NEXT ROW
   ↓
CLOSE
```

---

### Cursor Attributes

| Attribute              | Description                                         |
| ---------------------- | --------------------------------------------------- |
| `cursor_name%FOUND`    | Returns TRUE if the last FETCH returned a row       |
| `cursor_name%NOTFOUND` | Returns TRUE if the last FETCH did not return a row |
| `cursor_name%ROWCOUNT` | Returns the number of rows fetched                  |
| `cursor_name%ISOPEN`   | Returns TRUE if the cursor is open                  |

---

## Difference Between the Two Questions

| Question 1           | Question 2                   |
| -------------------- | ---------------------------- |
| Uses implicit cursor | Uses explicit cursor         |
| Uses `SQL%ROWCOUNT`  | Uses `emp_cursor%FOUND`      |
| Updates one employee | Processes multiple employees |
| Simple PL/SQL block  | Cursor-based PL/SQL block    |
| No custom exception  | Uses `SALARY_ZERO` exception |
