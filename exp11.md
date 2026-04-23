# Experiment 11

## Aim
To perform SQL queries using joins, subqueries, aggregate functions, and conditions for data retrieval and manipulation.

## Theory
This experiment uses:
- Joins (INNER JOIN, SELF JOIN)
- Subqueries for comparison
- Aggregate functions (MAX, MIN, AVG, COUNT)
- Conditions (WHERE, IN, GROUP BY, HAVING)
- DELETE operation

These help in analyzing employee data like salary comparison, manager hierarchy, and department-wise filtering.

---

## Queries

### 1. Delete employees before 31-Dec-82 and location Mumbai/Delhi
```sql
DELETE e
FROM employee e
JOIN department d ON e.deptno = d.deptno
WHERE e.hiredate < '1982-12-31'
AND d.location IN ('MUMBAI','DELHI');
```

### 2. Managers with department and location
```sql
SELECT e.ename, e.job, d.dname, d.location
FROM employee e
JOIN department d ON e.deptno = d.deptno
WHERE e.job = 'MANAGER';
```

### 3. Ford salary equals highest of his grade
```sql
SELECT e.ename, e.sal
FROM employee e
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
WHERE e.ename='FORD'
AND e.sal = s.hisal;
```

### 4. Top 5 earners
```sql
SELECT ename, sal
FROM employee
ORDER BY sal DESC
LIMIT 5;
```

### 5. Employees with highest salary
```sql
SELECT ename
FROM employee
WHERE sal = (SELECT MAX(sal) FROM employee);
```

### 6. Salary equal to average of max and min
```sql
SELECT ename, sal
FROM employee
WHERE sal = (
 (SELECT MAX(sal)+MIN(sal) FROM employee)/2
);
```

### 7. Departments having at least 3 employees
```sql
SELECT d.dname
FROM department d
JOIN employee e ON d.deptno=e.deptno
GROUP BY d.dname
HAVING COUNT(*)>=3;
```

### 8. Managers earning more than average salary
```sql
SELECT ename
FROM employee
WHERE job='MANAGER'
AND sal > (SELECT AVG(sal) FROM employee);
```

### 9. Managers earning more than avg of their employees
```sql
SELECT m.ename
FROM employee m
JOIN employee e ON m.empno=e.mgr
GROUP BY m.empno, m.ename, m.sal
HAVING m.sal > AVG(e.sal);
```

### 10. Net pay >= any employee salary
```sql
SELECT ename, sal, comm, (sal + IFNULL(comm,0)) AS net_pay
FROM employee
WHERE (sal + IFNULL(comm,0)) >= ANY (
 SELECT sal FROM employee
);
```

---

## Conclusion
Successfully executed advanced SQL queries using joins, subqueries, and aggregate functions.
