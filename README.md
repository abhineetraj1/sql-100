# Answer to 100-SQL questions

Question is available in the given pdf

1. Display the details of all employees:
```
SELECT * FROM emp;
```

2. Display the department information from department table:
```
SELECT * FROM dept;
```

3. Display the name and job for all the employees:
```
SELECT ename, job FROM emp;
```

4. Display the name and salary for all the employees:
```
SELECT ename, sal FROM emp;
```

5. Display the employee number and total salary for all the employees:
```
SELECT empno, sal + comm AS total_salary FROM emp;
```

6. Display the employee name and annual salary for all employees:
```
SELECT ename, sal * 12 AS annual_salary FROM emp;
```

7. Display the names of all the employees who are working in department number 10:
```
SELECT ename FROM emp WHERE deptno = 10;
```

8. Display the names of all the employees who are working as clerks and drawing a salary more than 3000:
```
SELECT ename FROM emp WHERE job = 'CLERK' AND sal > 3000;
```

9. Display the employee number and name who are earning comm:
```
SELECT empno, ename FROM emp WHERE comm > 0;
```

10. Display the employee number and name who do not earn any comm:
```
SELECT empno, ename FROM emp WHERE comm = 0;
```

11. Display the names of employees who are working as clerks, salesmen or analysts:
```
SELECT ename FROM emp WHERE job IN ('CLERK', 'SALESMAN', 'ANALYST');
```

12. Display the names of the employees who are working in the company for the past 5 years:
```
SELECT ename FROM emp WHERE hiredate > SYSDATE - 5/365;
```

13. Display the list of employees who have joined the company before 30-JUN-90 or after 31-DEC-90:
```
SELECT ename FROM emp
WHERE hiredate < TO_DATE('30-JUN-1990', 'DD-MON-YYYY')
OR hiredate > TO_DATE('31-DEC-1990', 'DD-MON-YYYY');
```

14. Display current Date:
```
SELECT SYSDATE AS current_date FROM DUAL;
```

15. Display the list of all users in your database (use catalog table):
```
SELECT username FROM dba_users;
```

16. Display the names of all tables from current user:
```
SELECT table_name FROM user_tables;
```

17. Display the name of the current user:
```
SELECT USER FROM DUAL;
```

18. Display the names of employees working in department number 10 or 20 or 40 or employees working as CLERKS, SALESMAN or ANALYST:
```
SELECT ename FROM emp
WHERE deptno IN (10, 20, 40)
OR job IN ('CLERK', 'SALESMAN', 'ANALYST');
```

19. Display the names of employees whose name starts with alphabet S:
```
SELECT ename FROM emp WHERE ename LIKE 'S%';
```

20. Display the Employee names for employees whose name ends with alphabet S:
```
SELECT ename FROM emp WHERE ename LIKE '%S';
```

21. Display the names of employees whose names have second alphabet A in their names:
```
SELECT ename FROM emp WHERE SUBSTR(ename, 2, 1) = 'A';
```

22. Select the names of the employee whose names is exactly five characters in length:
```
SELECT ename FROM emp WHERE LENGTH(ename) = 5;
```

23. Display the names of the employee who are not working as MANAGERS:
```
SELECT ename FROM emp WHERE job <> 'MANAGER';
```

24. Display the names of the employee who are not working as SALESMAN OR CLERK OR ANALYST:
```
SELECT ename FROM emp
WHERE job NOT IN ('SALESMAN', 'CLERK', 'ANALYST');
```

25. Display all rows from EMP table. The system should wait after every screen full of data:
```
SET LINESIZE 100;  -- Adjust LINESIZE for desired number of rows per screen
SELECT * FROM emp;
```

26. Display the total number of employee working in the company.

```
SELECT COUNT(*) AS total_employees FROM emp;
```

27. Display the total salary being paid to all employees.

```
SELECT SUM(sal) AS total_salary FROM emp;
```

28. Display the maximum salary from emp table.

```
SELECT MAX(sal) AS max_salary FROM emp;
```

29. Display the minimum salary from emp table.

```
SELECT MIN(sal) AS min_salary FROM emp;
```

30. Display the average salary from emp table.

```
SELECT AVG(sal) AS average_salary FROM emp;
```

31. Display the maximum salary being paid to CLERK.

```
SELECT MAX(sal) AS max_clerk_salary FROM emp WHERE job = 'CLERK';
```

32. Display the maximum salary being paid to depart number 20.

```
SELECT MAX(sal) AS max_dept20_salary FROM emp WHERE deptno = 20;
```

33. Display the minimum salary being paid to any SALESMAN.

```
SELECT MIN(sal) AS min_salesman_salary FROM emp WHERE job = 'SALESMAN';
```

34. Display the average salary drawn by MANAGERS.

```
SELECT AVG(sal) AS avg_manager_salary FROM emp WHERE job = 'MANAGER';
```

35. Display the total salary drawn by ANALYST working in depart number 40.

```
SELECT SUM(sal) AS total_analyst_salary FROM emp 
WHERE job = 'ANALYST' AND deptno = 40;
```

36. Display the names of the employee in order of salary i.e the name of the employee earning lowest salary should salary appear first.

```
SELECT ename FROM emp ORDER BY sal;
```

37. Display the names of the employee in descending order of salary.

```
SELECT ename FROM emp ORDER BY sal DESC;
```

38. Display the names of the employee in order of employee name.

```
SELECT ename FROM emp ORDER BY ename;
```

39. Display empno, ename, deptno, sal sort the output first base on deptno and within deptno by sal.

```
SELECT empno, ename, deptno, sal FROM emp ORDER BY deptno, sal;
```

40. Display the name of the employee along with their annual salary(sal*12).The name of the employee earning highest annual salary should apper first.

```
SELECT ename, sal * 12 AS annual_salary FROM emp ORDER BY annual_salary DESC;
```

41. Display name,salary,hra,pf,da,total salary for each employee. The output should be in the order of total salary,hra 15% of salary,da 10% of salary,pf 5% salary,total salary will be(salary+hra+da)-pf.

```
SELECT ename, sal, sal * 0.15 AS hra, sal * 0.1 AS da, sal * 0.05 AS pf, 
(sal + sal * 0.15 + sal * 0.1) - (sal * 0.05) AS total_salary
FROM emp
ORDER BY total_salary DESC;
```

42. Display depart numbers and total number of employees working in each department.

```
SELECT deptno, COUNT(*) AS total_employee FROM emp GROUP BY deptno;
```

43. Display the various jobs and total number of employees within each job group.

```
SELECT job, COUNT(*) AS total_employee FROM emp GROUP BY job;
```

44. Display the depart numbers and total salary for each department.

```
SELECT deptno, SUM(sal) AS total_salary FROM emp GROUP BY deptno;
```

45. Display the depart numbers and max salary for each department.

```
SELECT deptno, MAX(sal) AS max_salary FROM emp GROUP BY deptno;
```

46. Display the various jobs and total salary for each job

```
SELECT job, SUM(sal) AS total_salary FROM emp GROUP BY job;
```

 47. Display the various jobs and total number of employees within each job group (duplicate of question 43).

```
SELECT job, COUNT(*) AS total_employee FROM emp GROUP BY job;
```

48. Display the depart numbers with more than three employees in each dept.

```
SELECT deptno FROM emp
GROUP BY deptno
HAVING COUNT(*) > 3;
```

49. Display the various jobs along with total salary for each of the jobs where total salary is greater than 40000.

```
SELECT job, SUM(sal) AS total_salary FROM emp
GROUP BY job
HAVING SUM(sal) > 40000;
```


50. Display the various jobs along with total number of employees in each job.The output should contain only those jobs with more than three employees.

```
SELECT job, COUNT(*) AS total_employee FROM emp
GROUP BY job
HAVING COUNT(*) > 3;
```

51. Display the name of the employee who earns highest salary.

```
SELECT ename FROM emp
ORDER BY sal DESC
FETCH FIRST 1 ROW ONLY;
```

52. Display the employee number and name for employee working as clerk and earning highest salary among clerks.

```
SELECT empno, ename FROM emp
WHERE job = 'CLERK'
ORDER BY sal DESC
FETCH FIRST 1 ROW ONLY;
```

53. Display the names of salesman who earns a salary more than the highest salary of any clerk.

```
SELECT ename FROM emp
WHERE job = 'SALESMAN'
AND sal > (SELECT MAX(sal) FROM emp WHERE job = 'CLERK');
```

54. a) Display the names of clerks who earn a salary more than the lowest salary of any salesman.

```
SELECT ename FROM emp
WHERE job = 'CLERK'
AND sal > (SELECT MIN(sal) FROM emp WHERE job = 'SALESMAN');
```

b) Display the names of employees who earn a salary more than that of Jones or that of salary greater than that of Scott.

```
SELECT ename FROM emp
WHERE sal > (SELECT sal FROM emp WHERE ename = 'JONES')
OR sal > (SELECT sal FROM emp WHERE ename = 'SCOTT');
```

55. Display the names of the employees who earn highest salary in their respective job groups.

```
SELECT e.ename, e.sal
FROM emp e
INNER JOIN (
  SELECT job, MAX(sal) AS max_salary
  FROM emp
  GROUP BY job
) j ON e.job = j.job AND e.sal = j.max_salary;
```

56. Display the names of the employees who earn highest salaries in their respective job groups. (duplicate of question 55)

57. Display the employee names who are working in accounting department.

```
SELECT ename FROM emp
WHERE deptno IN (SELECT deptno FROM dept WHERE DNAME = 'ACCOUNTING');
```

58. Display the employee names who are working in Chicago.

```
SELECT ename FROM emp
WHERE deptno IN (SELECT deptno FROM dept WHERE LOC = 'CHICAGO');
```

59. Display the Job groups having total salary greater than the maximum salary for managers.

```
SELECT job
FROM emp
GROUP BY job
HAVING SUM(sal) > (SELECT MAX(sal) FROM emp WHERE job = 'MANAGER');
```

60. Display the names of employees from department number 10 with salary greater than that of any employee working in other department.

```
SELECT ename FROM emp e
WHERE deptno = 10
AND sal > (SELECT MAX(sal) FROM emp WHERE deptno != 10);
```

61. Display the names of the employees from department number 10 with salary greater than that of all employee working in other departments. (duplicate of question 60)

62. Display the names of the employees in Uppercase.

```
SELECT UPPER(ename) AS ename_upper FROM emp;
```

63. Display the names of the employees in Lowecase.

```
SELECT LOWER(ename) AS ename_lower FROM emp;
```

64. Display the names of the employees in Propercase.

```
SELECT INITCAP(ename) AS ename_proper FROM emp;
```

65. Display the length of Your name using appropriate function.

```
SELECT LENGTH(USER) AS username_length FROM DUAL;
```

66. Display the length of all the employee names.

```
SELECT ename, LENGTH(ename) AS ename_length FROM emp;
```

67. Select name of the employee concatenate with employee number.

```
SELECT ename || ' - ' || empno AS ename_empno FROM emp;
```

68. User appropriate function and extract 3 characters starting from 2nd characters from the following string 'Oracle'. i.e the output should be 'ac'.

```
SELECT SUBSTR('Oracle', 2, 3) AS extracted_chars FROM DUAL;
```

69. Find the First occurance of character 'a' from the following string 'Computer Maintenance Corporation'

```
SELECT INSTR('Computer Maintenance Corporation', 'a') AS first_a_position FROM DUAL;
```

70. Replace every occurrence of alphabet A with B in the string Allens(use translate function)

```
SELECT TRANSLATE('Allens', 'A', 'B') AS replaced_string FROM DUAL;
```

71. Display the information from emp table. Where job manager is found it should be displayed as boss(Use replace function).

```
SELECT ename, REPLACE(job, 'MANAGER', 'BOSS') AS modified_job
FROM emp;
```

72. Display empno,ename,deptno from emp table. Instead of display department numbers [B1] display the related department name(Use decode function).

```
SELECT empno, ename,
  DECODE(deptno, 
         B1, 'Department 1', 
         -- Add more departments with their corresponding codes here
         deptno) AS department_name
FROM emp;
```

73. Display your age in days. (This cannot be done directly in SQL)

Age cannot be calculated directly in SQL as it requires the user's date of birth, which is not typically stored. You would need to use a separate tool or application to perform this calculation.

74. Display your age in months. (This cannot be done directly in SQL)

Similar to question 73, calculating age in months requires the user's date of birth and cannot be done directly in SQL.

75. Display the current date as 15th Augest Friday Nineteen Ninety Saven.

```
SELECT TO_CHAR(SYSDATE, 'DD"th" Month YYYY" Day"') AS formatted_date FROM DUAL;
```

76. Display the following output for each row from emp table.

Unfortunately, you haven't specified the desired output format for each row. Please provide details on what specific information you want to display from the `emp` table.

77. Find the date for nearest saturday after current date.

```
SELECT NEXT_DAY(SYSDATE, 'SATURDAY') AS next_saturday FROM DUAL;
```

78. Display current time.

```
SELECT TO_CHAR(SYSDATE, 'HH24:MI:SS') AS current_time FROM DUAL;
```

79. Display the date three months Before the current date.

```
SELECT ADD_MONTHS(SYSDATE, -3) AS three_months_ago FROM DUAL;
```

80. Display the common jobs from department number 10 and 20.

```
SELECT job
FROM emp
WHERE deptno IN (10, 20)
GROUP BY job
HAVING COUNT(DISTINCT deptno) > 1;
```

81. Display the jobs found in department 10 and 20 Eliminate duplicate jobs.

```
SELECT DISTINCT job
FROM emp
WHERE deptno IN (10, 20);
```

82. Display the jobs which are unique to department 10.

```
SELECT job
FROM emp
WHERE deptno = 10
AND job NOT IN (SELECT job FROM emp WHERE deptno = 20);
```

83. Display the details of those who do not have any person working under them.

```
SELECT e.ename
FROM emp e
LEFT JOIN emp m ON e.empno = m.mgr
WHERE m.mgr IS NULL;
```

84. Display the details of those employees who are in sales department and grade is 3.

```
SELECT * FROM emp e
WHERE deptno IN (SELECT deptno FROM dept WHERE DNAME = 'SALES')
AND grade = 3;
```

85. Display those who are not managers and who are managers any one.

i)display the managers names

```
SELECT ename FROM emp
WHERE job = 'MANAGER';
```

ii)display the who are not managers

```
SELECT ename FROM emp
WHERE job != 'MANAGER';
```

86. Display those employee whose name contains not less than 4 characters.

```
SELECT ename FROM emp
WHERE LENGTH(ename) >= 4;
```


87. Display those department whose name start with "S" while the location name ends with "K". (Incomplete query)

To complete this query, you can join the `emp`, `dept` tables, and filter based on department name starting with "S" and location name ending with "K". Here's the complete query:

```
SELECT DNAME, LOC
FROM dept
WHERE DNAME LIKE 'S%'
AND LOC LIKE '%K';
```

88. Display those employees whose manager name is JONES.

```
SELECT e.ename
FROM emp e
WHERE e.mgr = (SELECT empno FROM emp WHERE ename = 'JONES');
```

89. Display those employees whose salary is more than 3000 after giving 20% increment.

```
SELECT ename, sal * 1.2 AS increased_salary
FROM emp
WHERE sal * 1.2 > 3000;
```

90. Display all employees while their dept names:

```
SELECT e.ename, d.dname
FROM emp e
INNER JOIN dept d ON e.deptno = d.deptno;
```

91. Display ename who are working in sales dept.

```
SELECT ename
FROM emp e
INNER JOIN dept d ON e.deptno = d.deptno
WHERE d.dname = 'SALES';
```

92. Display employee name,deptname,salary and comm for those sal in between 2000 to 5000 while location is chicago.

```
SELECT e.ename, d.dname, e.sal, e.comm
FROM emp e
INNER JOIN dept d ON e.deptno = d.deptno
WHERE e.sal BETWEEN 2000 AND 5000
AND d.loc = 'CHICAGO';
```

93. Display those employees whose salary greter than his manager salary.

```
SELECT e.ename
FROM emp e
INNER JOIN emp m ON e.mgr = m.empno
WHERE e.sal > m.sal;
```

94. Display those employees who are working in the same dept where his manager is work.

```
SELECT e.ename
FROM emp e
INNER JOIN emp m ON e.mgr = m.empno
WHERE e.deptno = m.deptno;
```

95. Display those employees who are not working under any manager.

```
SELECT ename FROM emp
WHERE mgr IS NULL;
```

96. Display grade and employees name for the dept no 10 or 30 but grade is not 4 while joined the company before 31-dec-82.

```
SELECT e.ename, e.grade
FROM emp e
WHERE (deptno = 10 OR deptno = 30) 
AND grade != 4
AND hiredate < TO_DATE('31-DEC-1982', 'DD-MON-YYYY');
```

97. Update the salary of each employee by 10% increments that are not eligible for commission.

This requires a UPDATE statement but cannot be directly executed as it modifies the database. You'll need to be cautious while running such queries. Here's the example:

```
UPDATE emp
SET sal = sal * 1.1
WHERE comm IS NULL;
```

98. SELECT that employee who joined the company before 31-dec-82 while Their dept location is newyork or Chicago.

```
SELECT * FROM emp
WHERE hiredate < TO_DATE('31-DEC-1982', 'DD-MON-YYYY')
AND deptno IN (SELECT deptno FROM dept WHERE LOC IN ('NEWYORK', 'CHICAGO'));
``` 

99. DISPLAY EMPLOYEE NAME, JOB, DEPARTMENT, LOCATION FOR ALL WHO ARE WORKING AS MANAGER?

```
SELECT e.ename, e.job, d.dname, d.loc
FROM emp e
INNER JOIN dept d ON e.deptno = d.deptno
WHERE e.job = 'MANAGER';
```

100. DISPLAY THOSE EMPLOYEES WHOSE MANAGER NAME IS JONES? -- [AND ALSO DISPLAY THEIR MANAGER NAME]?

```
SELECT e.ename, m.ename AS manager_name
FROM emp e
INNER JOIN emp m ON e.mgr = m.empno
WHERE m.ename = 'JONES';
```

101. Display name and salary of ford if he exists in the emp table

```
SELECT ename, sal
FROM emp
WHERE ename = 'FORD';
```