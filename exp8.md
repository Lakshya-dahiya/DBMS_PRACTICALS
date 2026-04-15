# Experiment 8

## Aim
To perform SQL queries using JOIN operations, subqueries, and conditions.

---

## Theory
SQL JOIN operations combine data from multiple tables.

---

## Queries

```sql
-- 1
SELECT e.ename, d.dname
FROM employee e
JOIN department d ON e.deptno = d.deptno;

-- 2
SELECT e.ename, m.ename AS Manager
FROM employee e
JOIN employee m ON e.mgr = m.empno
WHERE m.ename = 'JONES';

-- 3
SELECT e.ename, e.job, d.dname, m.ename, s.grade
FROM employee e
JOIN department d ON e.deptno = d.deptno
JOIN employee m ON e.mgr = m.empno
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal;

-- 4
SELECT e.ename, e.job, d.dname, s.grade, e.sal
FROM employee e
JOIN department d ON e.deptno = d.deptno
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
WHERE e.job <> 'CLERK'
ORDER BY e.sal DESC;

-- 5
SELECT e.ename, e.job, COALESCE(m.ename, 'NO MANAGER')
FROM employee e
LEFT JOIN employee m ON e.mgr = m.empno;

-- 6
SELECT e.ename, (e.sal*12)
FROM employee e
WHERE (e.sal*12)=36000 OR e.job<>'CLERK';

-- 7
SELECT e.ename, (e.sal*12)
FROM employee e
WHERE (e.sal*12)=30000 AND e.job<>'CLERK';

-- 8
SELECT e.empno, e.ename, COALESCE(m.ename,'NO MANAGER')
FROM employee e
LEFT JOIN employee m ON e.mgr = m.empno;

-- 9
SELECT d.deptno, d.dname, SUM(e.sal)
FROM employee e
JOIN department d ON e.deptno = d.deptno
GROUP BY d.deptno, d.dname;

-- 10
SELECT e.empno, e.ename, d.location
FROM employee e
JOIN department d ON e.deptno = d.deptno;

-- 11
SELECT e.ename, d.dname
FROM employee e
JOIN department d ON e.deptno = d.deptno;
```
