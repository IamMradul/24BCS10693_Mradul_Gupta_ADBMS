# 5.1 American Revenue Percentage

**Problem:** https://www.codechef.com/learn/course/sql-intermediate/SQ00BS09/problems/GSQ85D?tab=statement

## Solution

```sql
SELECT
    ROUND(
        (100 * SUM(CASE WHEN cuisine = 'American' THEN price ELSE 0 END))
        / SUM(price),
        2
    ) AS American_Revenue
FROM Orders;
```

---

# 5.2 Invalid Tweets

**Problem:** https://leetcode.com/problems/invalid-tweets/description/?envType=study-plan-v2&envId=top-sql-50

## Solution

```sql
SELECT tweet_id
FROM Tweets
WHERE LENGTH(content) > 15;
```

---

# 5.3 Conditional Statements in PostgreSQL (PL/pgSQL)

## 1. IF THEN

```sql
DO $$
DECLARE
    AGE INT := 19;

BEGIN
    IF AGE >= 18 THEN
        RAISE NOTICE 'Your age is % and you are eligible to vote', AGE;
    END IF;

    RAISE NOTICE 'You are inside begin end block';
END;
$$;
```

---

## 2. IF ELSE

```sql
DO $$
DECLARE
    AGE INT := 17;

BEGIN
    IF AGE >= 18 THEN
        RAISE NOTICE 'Your age is % and you are eligible to vote', AGE;
    ELSE
        RAISE NOTICE 'Your age is % and you are not eligible to vote', AGE;
    END IF;

    RAISE NOTICE 'You are inside begin end block';
END;
$$;
```

---

## 3. IF ELSIF ELSE

```sql
DO $$
DECLARE
    VAL INT := 17;

BEGIN
    IF VAL >= 0 AND VAL <= 10 THEN
        RAISE NOTICE 'Value is % and in range between 1 to 10', VAL;

    ELSIF VAL > 10 AND VAL <= 20 THEN
        RAISE NOTICE 'Value is % and in range between 11 to 20', VAL;

    ELSE
        RAISE NOTICE 'Value is % and is greater than 20', VAL;
    END IF;

    RAISE NOTICE 'You are inside begin end block';
END;
$$;
```