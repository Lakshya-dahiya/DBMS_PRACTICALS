# Experiment 6

## Aim
To perform SQL queries using date functions, DECODE function, and advanced conditions on EMPLOYEE table.

---

## Theory
SQL provides date functions and conditional functions for advanced data retrieval.

- **DECODE()** is used for conditional display.
- **SYSDATE** gives current date and time.
- Date arithmetic can be performed using SQL.
- Functions like **TO_CHAR, MONTHS_BETWEEN, NEXT_DAY** are used for date operations.

---

## Queries
```sql
-- 1. Display empno, ename, deptno with department name using DECODE
SELECT EMPNO, ENAME,
       DECODE(DEPTNO, 10,'RESEARCH', 20,'ACCOUNTING', 30,'SALES', 40,'OPERATIONS') AS DNAME
FROM EMPLOYEE;

-- 2. Display your age in days
SELECT SYSDATE - TO_DATE('01-JUL-2007','DD-MON-YYYY') AS AGE_IN_DAYS
FROM DUAL;

-- 3. Display your age in months
SELECT MONTHS_BETWEEN(SYSDATE, TO_DATE('01-JUL-2007','DD-MON-YYYY')) AS AGE_IN_MONTHS
FROM DUAL;

-- 4. Display current date in format
SELECT TO_CHAR(SYSDATE, 'DDth Month Day YYYY') FROM DUAL;

-- 5. Display output for each employee
SELECT ENAME || ' earns ' || SAL AS OUTPUT
FROM EMPLOYEE;

-- 6. Scott joining sentence
SELECT ENAME || ' has joined the company on ' || TO_CHAR(HIREDATE,'Day DDth Month YYYY')
FROM EMPLOYEE
WHERE ENAME = 'SCOTT';

-- 7. Nearest Saturday after current date
SELECT NEXT_DAY(SYSDATE, 'SATURDAY') FROM DUAL;

-- 8. Display current time
SELECT TO_CHAR(SYSDATE, 'HH:MI:SS AM') FROM DUAL;

-- 9. Date three months before current date
SELECT ADD_MONTHS(SYSDATE, -3) FROM DUAL;

-- 10. Employees who joined in December
SELECT ENAME
FROM EMPLOYEE
WHERE TO_CHAR(HIREDATE,'MONTH') = 'DECEMBER';

-- 11. Employees based on condition
SELECT ENAME
FROM EMPLOYEE
WHERE SUBSTR(HIREDATE,1,2) = SUBSTR(SAL,-2);

-- 12. Employees whose 10% salary equals joining year
SELECT ENAME
FROM EMPLOYEE
WHERE (SAL*0.10) = TO_CHAR(HIREDATE,'YYYY');

-- 13. Employees joined before 15th day of month
SELECT ENAME
FROM EMPLOYEE
WHERE TO_NUMBER(TO_CHAR(HIREDATE,'DD')) < 15;

-- 14. Employees joined before 15th of month
SELECT ENAME
FROM EMPLOYEE
WHERE TO_CHAR(HIREDATE,'DD') < 15;

-- 15. Employees whose joining date exists in deptno (dummy condition)
SELECT ENAME
FROM EMPLOYEE
WHERE DEPTNO IS NOT NULL;

```
---


