# Experiment 10

## Aim
To perform SQL queries using subqueries, joins, and conditions to retrieve specific employee data.

## Theory
This experiment uses:
- Subqueries (ANY, ALL)
- Joins (INNER JOIN, SELF JOIN)
- Conditions (WHERE, AND, OR)
These help in comparing salaries, finding managers, and filtering data.

## Queries

### 1
SELECT ename
FROM employee
WHERE deptno = 10
AND sal > ANY (
    SELECT sal FROM employee WHERE deptno <> 10
);

### 2
SELECT e.*
FROM employee e
JOIN department d ON e.deptno = d.deptno
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
WHERE d.dname = 'SALES'
AND s.grade = 'C';

### 3
SELECT *
FROM employee
WHERE job <> 'MANAGER'
AND empno NOT IN (
    SELECT mgr FROM employee WHERE mgr IS NOT NULL
);

### 4
SELECT e.*
FROM employee e
JOIN employee m ON e.mgr = m.empno
WHERE m.ename = 'JONES';

### 5
SELECT e.ename
FROM employee e
JOIN department d ON e.deptno = d.deptno
WHERE d.dname = 'SALES';

### 6
SELECT e.ename, e.sal, m.ename AS manager, m.sal
FROM employee e
JOIN employee m ON e.mgr = m.empno
WHERE e.sal > m.sal;

### 7
SELECT e.ename, m.ename AS manager, e.deptno
FROM employee e
JOIN employee m ON e.mgr = m.empno
WHERE e.deptno = m.deptno;

### 8
SELECT e.ename, s.grade
FROM employee e
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
WHERE e.deptno IN (10,30)
AND s.grade <> 'D'
AND e.hiredate < '1982-12-31';

## Conclusion
Successfully executed queries using joins and subqueries to analyze employee data.
