# Experiment 4

## Aim
To perform advanced SQL queries on EMPLOYEE table using conditions, pattern matching, calculations, ordering and update operations.

---

## Theory
SQL is used to manipulate and retrieve data efficiently.

- **WHERE** clause filters data based on conditions.
- **LIKE** is used for pattern matching.
- **ORDER BY** sorts the result.
- Arithmetic operations can be applied on columns.
- **UPDATE** is used to modify existing records.

---

## Queries
```sql
-- 1. Display employees who joined before 30-June-80 or after 31-Dec-81
SELECT *
FROM EMPLOYEE
WHERE HIREDATE < '30-JUN-80'
   OR HIREDATE > '31-DEC-81';

-- 2. Display employees whose second letter is A
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '_A%';

-- 3. Display employees whose name is exactly five characters
SELECT ENAME
FROM EMPLOYEE
WHERE LENGTH(ENAME) = 5;

-- 4. Display employees whose second letter is A
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '_A%';

-- 5. Display employees who are not clerk, salesman or analyst
SELECT ENAME
FROM EMPLOYEE
WHERE JOB NOT IN ('CLERK','SALESMAN','ANALYST');

-- 6. Display employee name with annual salary in descending order
SELECT ENAME, (SAL*12) AS ANNUAL_SALARY
FROM EMPLOYEE
ORDER BY ANNUAL_SALARY DESC;

-- 7. Display name, sal, hra, da, pf, total salary
SELECT ENAME, SAL,
       (SAL*0.15) AS HRA,
       (SAL*0.10) AS DA,
       (SAL*0.05) AS PF,
       (SAL + (SAL*0.15) + (SAL*0.10) - (SAL*0.05)) AS TOTAL_SAL
FROM EMPLOYEE;

-- 8. Update salary by 10% increment where no commission
UPDATE EMPLOYEE
SET SAL = SAL + (SAL*0.10)
WHERE COMM IS NULL;

-- 9. Display employees whose salary is more than 3000 after 20% increment
SELECT ENAME, SAL*1.20 AS UPDATED_SAL
FROM EMPLOYEE
WHERE SAL*1.20 > 3000;

-- 10. Display employees whose salary has at least 3 digits
SELECT ENAME, SAL
FROM EMPLOYEE
WHERE SAL >= 100;

```
---


