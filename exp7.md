# Experiment 7

## Aim
To perform advanced SQL queries using aggregate functions, grouping, formatting and date calculations.

---

## Theory
SQL provides powerful functions for data analysis and reporting.

- **GROUP BY** is used to group records.
- **COUNT(), SUM(), MAX(), MIN()** are aggregate functions.
- **TO_CHAR()** is used for formatting.
- Date functions help in calculations like days remaining, last Sunday etc.

---

## Queries
```sql
-- 1. Days remaining in current year
SELECT TO_DATE('31-DEC-' || TO_CHAR(SYSDATE,'YYYY'),'DD-MON-YYYY') - SYSDATE AS DAYS_LEFT
FROM DUAL;

-- 2. Highest, lowest salary and difference
SELECT MAX(SAL) AS MAX_SAL,
       MIN(SAL) AS MIN_SAL,
       MAX(SAL) - MIN(SAL) AS DIFFERENCE
FROM EMPLOYEE;

-- 3. Employees whose commission > 25% of salary
SELECT ENAME
FROM EMPLOYEE
WHERE COMM > (SAL * 0.25);

-- 4. Salary in dollar format
SELECT ENAME, TO_CHAR(SAL,'$9999') AS SALARY
FROM EMPLOYEE;

-- 5. Matrix query (pivot style)
SELECT JOB,
       SUM(DECODE(DEPTNO,10,SAL)) AS DEPT10,
       SUM(DECODE(DEPTNO,20,SAL)) AS DEPT20,
       SUM(DECODE(DEPTNO,30,SAL)) AS DEPT30,
       SUM(SAL) AS TOTAL
FROM EMPLOYEE
GROUP BY JOB;

-- 6. Total employees and hired by year
SELECT COUNT(*) AS TOTAL,
       SUM(DECODE(TO_CHAR(HIREDATE,'YYYY'),'1980',1,0)) AS Y1980,
       SUM(DECODE(TO_CHAR(HIREDATE,'YYYY'),'1981',1,0)) AS Y1981,
       SUM(DECODE(TO_CHAR(HIREDATE,'YYYY'),'1982',1,0)) AS Y1982,
       SUM(DECODE(TO_CHAR(HIREDATE,'YYYY'),'1983',1,0)) AS Y1983
FROM EMPLOYEE;

-- 7. Last Sunday of current month
SELECT NEXT_DAY(LAST_DAY(SYSDATE)-7,'SUNDAY') FROM DUAL;

-- 8. Department wise employee count
SELECT DEPTNO, COUNT(*) AS TOTAL_EMP
FROM EMPLOYEE
GROUP BY DEPTNO;

-- 9. Job wise employee count
SELECT JOB, COUNT(*) AS TOTAL_EMP
FROM EMPLOYEE
GROUP BY JOB;

-- 10. Department wise total salary
SELECT DEPTNO, SUM(SAL) AS TOTAL_SALARY
FROM EMPLOYEE
GROUP BY DEPTNO;

```
---


