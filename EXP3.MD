SHOWING DATABASES
```sql
 SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| test               |
+--------------------+
```
CREATE DATABASE WITH YOUR NAME 
```sql
 CREATE DATABASE omisha;
Query OK 
```
SHOW THE DATABSE THAT YOU HAVE CREATED 
```sql
SHOW DATABASES;
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
USE THE DATABASE THAT YOU HAVE CREATED
```sql
USE omisha;
Database changed
```
CREATE TABLE WITH NAME DEPARTMENT
```sql
 CREATE TABLE DEPARTMENT (
      Deptno INT(2) PRIMARY KEY,
      Dname VARCHAR2(15) NOT NULL
    );
```
CREATE TABLE WITH NAME EMPLOYEE
```sql

CREATE TABLE EMPLOYEE (
    EMPNO INT PRIMARY KEY,
    ENAME VARCHAR2(20) NOT NULL,
    JOB VARCHAR2(20),
    MGR INT,
    HIREDATE DATE,
    SAL DECIMAL(10,2),
    COMM DECIMAL(10,2),
    DEPTNO INT,
    FOREIGN KEY (DEPTNO) REFERENCES DEPARTMENT(Deptno)
    );
```
INSERTING VALUES IN DEPARTMENT TABLE
```sql
INSERT INTO DEPARTMENT VALUES
    (10, 'RESEARCH'),
    (20, 'ACCOUNTING'),
    (30, 'SALES'),
    (40, 'OPERATIONS');
```
INSERTING VALUES IN EMPLOYEE TABLE
```sql
 INSERT INTO EMPLOYEE VALUES
     (7369,'SMITH','CLERK',7902,'1980-12-17',800,NULL,20),
     (7499,'ALLEN','SALESMAN',7698,'1981-02-20',1600,300,30),
     (7521,'WARD','SALESMAN',7698,'1981-02-22',1250,300,30),
     (7566,'JONES','MANAGER',7839,'1981-04-02',2975,NULL,20),
     (7654,'MARTIN','SALESMAN',7698,'1981-09-28',1250,1400,30),
     (7698,'BLAKE','MANAGER',7839,'1981-05-01',2850,NULL,30),
     (7782,'CLARK','MANAGER',7839,'1981-06-09',2450,NULL,10),
     (7788,'SCOTT','ANALYST',7566,'1982-12-09',3000,NULL,40),
     (7839,'KING','PRESIDENT',NULL,'1981-11-17',5000,NULL,20),
     (7844,'TURNER','SALESMAN',7698,'1981-09-08',1500,0,30),
     (7876,'ADAMS','CLERK',7788,'1983-01-12',1100,NULL,20),
     (7900,'JAMES','CLERK',7698,'1981-12-03',950,NULL,30),
     (7902,'FORD','ANALYST',7566,'1981-12-03',3000,NULL,20),
     (7934,'MILLER','CLERK',7782,'1982-01-23',1300,NULL,10);
```
Create Employee_master table with data using EMPLOYEE table
```sql
CREATE TABLE Employee_master AS
SELECT * FROM Employee;
```
Delete all records from Employee_master where DeptNo is 10
```sql
DELETE FROM Employee_master
WHERE DEPTNO = 10;
```
Update 10% hike in salary of DEPTNO 20 in Employee_master
```sql
UPDATE Employee_master
SET SAL = SAL + (SAL * 0.10)
WHERE DEPTNO = 20;
```
Alter SAL with size (12,2) in Employee_master
```sql
 ALTER TABLE Employee_master
MODIFY SAL DECIMAL(12,2);
```
Drop Employee_master table
```sql
DROP TABLE Employee_master;
Query OK 
```