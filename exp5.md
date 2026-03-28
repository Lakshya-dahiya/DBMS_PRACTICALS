# Experiment 5

## Aim
To perform SQL aggregate functions and string operations on EMPLOYEE table.

---

## Theory
SQL provides aggregate functions and string functions for data analysis.

- **COUNT()** counts rows
- **SUM()** calculates total
- **MAX() / MIN()** find highest and lowest values
- **AVG()** calculates average
- **UPPER(), LOWER(), INITCAP()** are string functions
- **LENGTH()** gives length of string

---

## Queries
```sql
-- 1. Total number of employees
SELECT COUNT(*) AS TOTAL_EMPLOYEES
FROM EMPLOYEE;

-- 2. Total salary of all employees
SELECT SUM(SAL) AS TOTAL_SALARY
FROM EMPLOYEE;

-- 3. Maximum salary
SELECT MAX(SAL) AS MAX_SALARY
FROM EMPLOYEE;

-- 4. Minimum salary
SELECT MIN(SAL) AS MIN_SALARY
FROM EMPLOYEE;

-- 5. Average salary
SELECT AVG(SAL) AS AVG_SALARY
FROM EMPLOYEE;

-- 6. Maximum salary of clerk
SELECT MAX(SAL)
FROM EMPLOYEE
WHERE JOB = 'CLERK';

-- 7. Maximum salary in dept 20
SELECT MAX(SAL)
FROM EMPLOYEE
WHERE DEPTNO = 20;

-- 8. Minimum salary of salesman
SELECT MIN(SAL)
FROM EMPLOYEE
WHERE JOB = 'SALESMAN';

-- 9. Average salary of managers
SELECT AVG(SAL)
FROM EMPLOYEE
WHERE JOB = 'MANAGER';

-- 10. Total salary of analyst in dept 40
SELECT SUM(SAL)
FROM EMPLOYEE
WHERE JOB = 'ANALYST' AND DEPTNO = 40;

-- 11. Names in uppercase
SELECT UPPER(ENAME)
FROM EMPLOYEE;

-- 12. Names in lowercase
SELECT LOWER(ENAME)
FROM EMPLOYEE;

-- 13. Names in proper case
SELECT INITCAP(ENAME)
FROM EMPLOYEE;

-- 14. Length of your name
SELECT LENGTH('LAKSHYA') AS NAME_LENGTH
FROM DUAL;

-- 15. Length of all employee names
SELECT ENAME, LENGTH(ENAME)
FROM EMPLOYEE;

```
---


