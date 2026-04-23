# EXPERIMENT 9

## Aim
To perform SQL queries using subqueries, aggregate functions, and conditions to retrieve meaningful information from the employee database.

## Theory
This experiment focuses on advanced SQL queries using subqueries, comparison operators (ANY, ALL), aggregate functions like MAX, MIN, AVG, and joins. These queries help in analyzing employee data such as highest salary, department-wise maximum salary, and comparisons between employees.

---

## Queries

### 1. Display employee name who earns highest salary
```sql
SELECT ename
FROM employee
WHERE sal = (SELECT MAX(sal) FROM employee);
```

---

### 2. Display employee number and name of clerk earning highest salary
```sql
SELECT empno, ename
FROM employee
WHERE job = 'CLERK'
AND sal = (
    SELECT MAX(sal)
    FROM employee
    WHERE job = 'CLERK'
);
```

---

### 3. Display names of salesman earning more than highest clerk salary
```sql
SELECT ename
FROM employee
WHERE job = 'SALESMAN'
AND sal > (
    SELECT MAX(sal)
    FROM employee
    WHERE job = 'CLERK'
);
```

---

### 4. Display clerks earning more than James but less than Scott
```sql
SELECT ename
FROM employee
WHERE job = 'CLERK'
AND sal > (SELECT sal FROM employee WHERE ename = 'JAMES')
AND sal < (SELECT sal FROM employee WHERE ename = 'SCOTT');
```

---

### 5. Display employees earning more than James OR Scott
```sql
SELECT ename
FROM employee
WHERE sal > (SELECT sal FROM employee WHERE ename = 'JAMES')
OR sal > (SELECT sal FROM employee WHERE ename = 'SCOTT');
```

---

### 6. Display employees with highest salary in each department
```sql
SELECT ename, deptno, sal
FROM employee e
WHERE sal = (
    SELECT MAX(sal)
    FROM employee
    WHERE deptno = e.deptno
);
```

---

### 7. Display employees with highest salary in each job group
```sql
SELECT ename, job, sal
FROM employee e
WHERE sal = (
    SELECT MAX(sal)
    FROM employee
    WHERE job = e.job
);
```

---

### 8. Display employees working in ACCOUNTING department
```sql
SELECT ename
FROM employee
WHERE deptno = (
    SELECT deptno
    FROM department
    WHERE dname = 'ACCOUNTING'
);
```

---

### 9. Display employees working in CHENNAI
```sql
SELECT e.ename
FROM employee e
JOIN department d ON e.deptno = d.deptno
WHERE d.location = 'CHENNAI';
```

---

### 10. Display job groups having total salary greater than max manager salary
```sql
SELECT job
FROM employee
GROUP BY job
HAVING SUM(sal) > (
    SELECT MAX(sal)
    FROM employee
    WHERE job = 'MANAGER'
);
```

---

## Result
All queries executed successfully and desired outputs were obtained.
