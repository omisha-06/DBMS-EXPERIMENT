SHOW DATABASES
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
CREATE DATABASES
```sql
CREATE DATABASE iilm_gn;
 SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| iilm_gn            |
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| test               |
+--------------------+
```
USE DATABASE AND CREATE TABLE 
```sql
USE iilm_gn;
 SHOW TABLES;

CREATE TABLE students(
        stu_id INT PRIMARY KEY,
        first_name VARCHAR(50) NOT NULL,
        last_name VARCHAR(50) NOT NULL,
        email VARCHAR(100) NOT NULL UNIQUE,
        dob DATE NOT NULL,
        course VARCHAR(50) NOT NULL,
        fees FLOAT(8,2) CHECK (fees > 0));

```
DESCRIBE TABLE 
```sql
DESC students;
+--------------+------------------+------+-----+-----------+--------+
| Field          |    Type         | Null | Key | Default | Extra |
+--------------+------------------+------+-----+-----------+-------+
| stu_id         |    int(11)      | NO| PRI    | NULL    |         |
| first_name     | varchar(50)     | NO|        | NULL    |         |
| last_name      | varchar(50)     | NO|        | NULL    |         |
| email          | varchar(100)    | NO| UNI    | NULL    |         |
| dob            |    date         | NO|        | NULL    |         |
| course         |  varchar(50)    | NO|        | NULL    |         |
| fees           | float(8,2)      | YES|       | NULL    |         |
+----------------+-----------------+------+-----+---------+---------+

```
INSERT VALUES INTO THE TABLE
```sql
INSERT INTO students (stu_id,first_name,last_name,email,dob,course,fees) VALUES
     ( 1,'AMAN','KUMAR','aman@gmail.com','2005-05-10','python',180000),
     (2,'RIYA','SHARMA','riya@gmail.com','2006-01-15','java',200000),
     (3,'ROHAN','SINGH','rohan@gmail.com','2005-12-20','c++',150000),
     (4,'NEHA','GUPTA','neha@gmail.com','2006-03-18','python',175000),
     (5,'ARJUN','MEHTA','arjun@gmail.com','2005-07-22','java',210000),
     (6,'PRIYA','VERMA','priya@gmail.com','2006-11-30','c',140000),
     (7,'KARAN','MALHOTRA','karan@gmail.com','2005-09-25','python',190000),
     (8,'SNEHA','REDDY','sneha@gmail.com','2006-02-14','java',220000),
     (9,'VIKAS','YADAV','vikas@gmail.com','2005-08-05','c++',160000),
     (10,'POOJA','NAIR','pooja@gmail.com','2006-04-09','python',185000);

```
SHOW TABLE WITH FULLY INSERTED VALUES
```sql
SELECT * FROM students;
+---------+----------------+---------------+-----------------+------------+-------------+
| stu_id | first_name | last_name | email             | dob        | course | fees      |
+--------+-----------------+---------------+------------------+------------+------------+
|      1 | AMAN       | KUMAR     | aman@gmail.com    | 2005-05-10 | python | 180000.00 |
|      2 | RIYA       | SHARMA    | riya@gmail.com    | 2006-01-15 | java   | 200000.00 |
|      3 | ROHAN      | SINGH     | rohan@gmail.com   | 2005-12-20 | c++    | 150000.00 |
|      4 | NEHA       | GUPTA     | neha@gmail.com    | 2006-03-18 | python | 175000.00 |
|      5 | ARJUN      | MEHTA     | arjun@gmail.com   | 2005-07-22 | java   | 210000.00 |
|      6 | PRIYA      | VERMA     | priya@gmail.com   | 2006-11-30 | c      | 140000.00 |
|      7 | KARAN      | MALHOTRA  | karan@gmail.com   | 2005-09-25 | python | 190000.00 |
|      8 | SNEHA      | REDDY     | sneha@gmail.com   | 2006-02-14 | java   | 220000.00 |
|      9 | VIKAS      | YADAV     | vikas@gmail.com   | 2005-08-05 | c++    | 160000.00 |
|     10 | POOJA      | NAIR      | pooja@gmail.com   | 2006-04-09 | python | 185000.00 |
+--------+------------+-----------+-------------------+------------+--------+-----------+

```