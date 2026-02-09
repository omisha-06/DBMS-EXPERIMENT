SHOW DATABASES
```sql SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| omisha             |
| performance_schema |
| phpmyadmin         |
| test               |
+--------------------+
```
USE DATABASE NAME
```sql
 USE omisha;
 ```
Display the Employees who joined before 30-June-1980 or after 31-Dec-1981
 ```sql
 SELECT ENAME, HIREDATE
    FROM EMPLOYEE
    WHERE HIREDATE < '30-JUN-1980'
    OR HIREDATE > '31-DEC-1981';
+--------+------------+
| ENAME  | HIREDATE   |
+--------+------------+
| SMITH  | 1980-12-17 |
| ALLEN  | 1981-02-20 |
| WARD   | 1981-02-22 |
| JONES  | 1981-04-02 |
| MARTIN | 1981-09-28 |
| BLAKE  | 1981-05-01 |
| CLARK  | 1981-06-09 |
| SCOTT  | 1982-12-09 |
| KING   | 1981-11-17 |
| TURNER | 1981-09-08 |
| ADAMS  | 1983-01-12 |
| JAMES  | 1981-12-03 |
| FORD   | 1981-12-03 |
| MILLER | 1982-01-23 |
+--------+------------+
 ```
 Employees whose second letter is ‘A’
 ```sql
  SELECT ENAME
     FROM EMPLOYEE
     WHERE ENAME LIKE '_A%';
+--------+
| ENAME  |
+--------+
| WARD   |
| MARTIN |
| JAMES  |
+--------+
 ```
 Employees whose name is exactly 5 characters
 ```sql
  [omisha]> SELECT ENAME
     FROM EMPLOYEE
     WHERE LENGTH(ENAME) = 5;
+-------+
| ENAME |
+-------+
| SMITH |
| ALLEN |
| JONES |
| BLAKE |
| CLARK |
| SCOTT |
| ADAMS |
| JAMES |
+-------+
 ```
 Employees whose second last letter is ‘E’
 ```sql
 SELECT ENAME
      FROM EMPLOYEE
      WHERE ENAME LIKE '%E_';
+--------+
| ENAME  |
+--------+
| ALLEN  |
| JONES  |
| TURNER |
| JAMES  |
| MILLER |
+--------+
 ```
 Employees who are NOT working as SALESMAN, CLERK, or ANALYST
 ```sql
  SELECT ENAME, JOB
    FROM EMPLOYEE
    WHERE JOB NOT IN ('SALESMAN', 'CLERK', 'ANALYST');
+-------+-----------+
| ENAME | JOB       |
+-------+-----------+
| JONES | MANAGER   |
| BLAKE | MANAGER   |
| CLARK | MANAGER   |
| KING  | PRESIDENT |
+-------+-----------+
 ```
 Employee name with annual salary (SAL * 12), highest first
 ```sql
  SELECT ENAME, SAL * 12 AS ANNUAL_SALARY
      FROM EMPLOYEE
      ORDER BY ANNUAL_SALARY DESC;
+--------+---------------+
| ENAME  | ANNUAL_SALARY |
+--------+---------------+
| KING   |      60000.00 |
| SCOTT  |      36000.00 |
| FORD   |      36000.00 |
| JONES  |      35700.00 |
| BLAKE  |      34200.00 |
| CLARK  |      29400.00 |
| ALLEN  |      19200.00 |
| TURNER |      18000.00 |
| MILLER |      15600.00 |
| MARTIN |      15000.00 |
| WARD   |      15000.00 |
| ADAMS  |      13200.00 |
| JAMES  |      11400.00 |
| SMITH  |       9600.00 |
+--------+---------------+
 ```
 Name, SAL, HRA, DA, PF, TOTAL (ordered by TOTAL)
 ```sql
  SELECT ENAME,
    ->        SAL,
    ->        SAL * 0.15 AS HRA,
    ->        SAL * 0.10 AS DA,
    ->        SAL * 0.05 AS PF,
    ->        (SAL + (SAL * 0.15) + (SAL * 0.10) - (SAL * 0.05)) AS TOTAL
    -> FROM EMPLOYEE
    -> ORDER BY TOTAL;
+--------+---------+----------+----------+----------+-----------+
| ENAME  | SAL     | HRA      | DA       | PF       | TOTAL     |
+--------+---------+----------+----------+----------+-----------+
| SMITH  |  800.00 | 120.0000 |  80.0000 |  40.0000 |  960.0000 |
| JAMES  |  950.00 | 142.5000 |  95.0000 |  47.5000 | 1140.0000 |
| ADAMS  | 1100.00 | 165.0000 | 110.0000 |  55.0000 | 1320.0000 |
| WARD   | 1250.00 | 187.5000 | 125.0000 |  62.5000 | 1500.0000 |
| MARTIN | 1250.00 | 187.5000 | 125.0000 |  62.5000 | 1500.0000 |
| MILLER | 1300.00 | 195.0000 | 130.0000 |  65.0000 | 1560.0000 |
| TURNER | 1500.00 | 225.0000 | 150.0000 |  75.0000 | 1800.0000 |
| ALLEN  | 1600.00 | 240.0000 | 160.0000 |  80.0000 | 1920.0000 |
| CLARK  | 2450.00 | 367.5000 | 245.0000 | 122.5000 | 2940.0000 |
| BLAKE  | 2850.00 | 427.5000 | 285.0000 | 142.5000 | 3420.0000 |
| JONES  | 2975.00 | 446.2500 | 297.5000 | 148.7500 | 3570.0000 |
| FORD   | 3000.00 | 450.0000 | 300.0000 | 150.0000 | 3600.0000 |
| SCOTT  | 3000.00 | 450.0000 | 300.0000 | 150.0000 | 3600.0000 |
| KING   | 5000.00 | 750.0000 | 500.0000 | 250.0000 | 6000.0000 |
+--------+---------+----------+----------+----------+-----------+
```
Increase salary by 10% for employees who do NOT get commission
```sql

[omisha]> UPDATE EMPLOYEE
    -> SET SAL = SAL * 1.10
    -> WHERE COMM IS NULL OR COMM = 0;

[omisha]> SELECT ENAME, SAL, COMM FROM EMPLOYEE;
+--------+---------+---------+
| ENAME  | SAL     | COMM    |
+--------+---------+---------+
| SMITH  |  880.00 |    NULL |
| ALLEN  | 1600.00 |  300.00 |
| WARD   | 1250.00 |  300.00 |
| JONES  | 3272.50 |    NULL |
| MARTIN | 1250.00 | 1400.00 |
| BLAKE  | 3135.00 |    NULL |
| CLARK  | 2695.00 |    NULL |
| SCOTT  | 3300.00 |    NULL |
| KING   | 5500.00 |    NULL |
| TURNER | 1650.00 |    0.00 |
| ADAMS  | 1210.00 |    NULL |
| JAMES  | 1045.00 |    NULL |
| FORD   | 3300.00 |    NULL |
| MILLER | 1430.00 |    NULL |
+--------+---------+---------+
```
Employees whose salary becomes more than 3000 after 20% increment
```sql
 [omisha]> SELECT ENAME, SAL, SAL * 1.20 AS NEW_SAL
    -> FROM EMPLOYEE
    -> WHERE SAL * 1.20 > 3000;
+-------+---------+-----------+
| ENAME | SAL     | NEW_SAL   |
+-------+---------+-----------+
| JONES | 3272.50 | 3927.0000 |
| BLAKE | 3135.00 | 3762.0000 |
| CLARK | 2695.00 | 3234.0000 |
| SCOTT | 3300.00 | 3960.0000 |
| KING  | 5500.00 | 6600.0000 |
| FORD  | 3300.00 | 3960.0000 |
+-------+---------+-----------+
```
Employees whose salary has at least 3 digits
```sql
[omisha]> SELECT ENAME, SAL
    -> FROM EMPLOYEE
    -> WHERE SAL >= 100;
+--------+---------+
| ENAME  | SAL     |
+--------+---------+
| SMITH  |  880.00 |
| ALLEN  | 1600.00 |
| WARD   | 1250.00 |
| JONES  | 3272.50 |
| MARTIN | 1250.00 |
| BLAKE  | 3135.00 |
| CLARK  | 2695.00 |
| SCOTT  | 3300.00 |
| KING   | 5500.00 |
| TURNER | 1650.00 |
| ADAMS  | 1210.00 |
| JAMES  | 1045.00 |
| FORD   | 3300.00 |
| MILLER | 1430.00 |
+--------+---------+
```

