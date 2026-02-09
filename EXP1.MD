SHOW DATABASE
```sql
MariaDB [(none)]> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| iilm_gn            |
| information_schema |
| movie              |
| mysql              |
| performance_schema |
| phpmyadmin         |
| test               |
+--------------------+
7 rows in set (0.092 sec)

```
CREATING TABLE 
```sql
 USE movie;

SHOW TABLES;
+-----------------+
| Tables_in_movie |
+-----------------+
| movies          |
+-----------------+

DESC movies;
+----------------+-------------+------+-----+----------+-------+
| Field          | Type        | Null | Key | Default  | Extra |
+----------------+-------------+------+-----+----------+-------+
| movie_id       | int(11)     | NO   | PRI | NULL     |       |
| moviename      | varchar(50) | NO   | UNI | NULL     |       |
| category       | varchar(30) | NO   |     | NULL     |       |
| release_date   | date        | NO   |     | NULL     |       |
| productioncost | float(10,2) | YES  |     | NULL     |       |
| businesscost   | float(10,2) | YES  |     | 0.00     |       |
| status         | char(12)    | YES  |     | Released |       |
+----------------+-------------+------+-----+----------+-------+

```
INSERTING VALUES
```sql
 INSERT INTO movies VALUES
     (1,'hindi_movie','musical','2018-04-23',124500,13000,'Released'),
     (2,'tamil_movie','action','2016-05-17',112000,118000,'Released'),
     (3,'english-movie','horror','2017-08-06',245000,360000,'Released'),
     (4,'bengali_movie','adventure','2017-01-04',72000,100000,'Released'),
     (5,'telugu_movie','action',NULL,100000,NULL,'UnReleased'),
     (6,'punjabi_movie','comedy',NULL,30500,NULL,'UnReleased');

```
a. List business done by the movies showing only MovieID, MovieName and BusinessCost.
```sql
SELECT movie_id,moviename,businesscost
    FROM movies;
+-------------+--------------------+-------------------+
|   movie_id      | moviename     | businesscost  |
+-------------+--------------------+-------------------+
|        1        | hindi_movie   |     13000.00  |
|        2        | tamil_movie   |    118000.00  |
|        3        | english-movie |    360000.00  |
|        4        | bengali_movie |    100000.00  |
|        5        | telugu_movie  |         NULL  |
|        6        | punjabi_movie |         NULL  |
+-------------+---------------------+------------------+

```
b. List the different categories of movies. (USE THE DISTINCT KEYWORD)
```sql
 SELECT DISTINCT category
 FROM movies;
+--------------+
| category  |
+-------------+
| musical   |
| action    |
| horror    |
| adventure |
| comedy    |
+---------------+

```
c. Find the net profit of each movie showing its ID, Name and Net Profit. Make sure that the new column name is labelled as NetProfit. Is this column now a part of the MOVIE relation. If no, then what name is coined for such columns? What can you say about the profit of a movie which has not yet released? Does your query result show profit as zero?
```sql
 SELECT movie_id,
     moviename,
     (businesscost-productioncost) AS NetProfit
     FROM movies;
+-------------+--------------------+---------------+
| movie_id        | moviename     | NetProfit  |
+-------------+--------------------+---------------+
|        1        | hindi_movie   | -111500.00 |
|        2        | tamil_movie   |    6000.00 |
|        3        | english-movie |  115000.00 |
|        4        | bengali_movie |   28000.00 |
|        5        | telugu_movie  |       NULL |
|        6        | punjabi_movie |       NULL |
+-------------+----------------------+--------------+

```
d.List all movies with ProductionCost greater than 80,000 and less than 1,25,000 showing ID, Name and ProductionCost.
```sql
SELECT movie_id,moviename,productioncost
    FROM movies
    WHERE productioncost > 80000
    AND productioncost < 125000;
+-------------+-------------------+----------------------+
| movie_id        | moviename    | productioncost |
+-------------+--------------------+---------------------+
|        1        | hindi_movie  |      124500.00 |
|        2        | tamil_movie  |      112000.00 |
|        5        | telugu_movie |      100000.00 |
+-------------+--------------------+--------------------+

```
e.List all movies which fall in the category of Comedy or Action.
```sql
SELECT *
     FROM movies
     WHERE category IN ('comedy','action');
+--------------+-------------------+-------------+-------------------+---------------------+-----------------+
| movie_id        | moviename     | category | release_date | productioncost | businesscost | status     |
+-------------+--------------------+-------------+-------------------+----------------------+----------------+
|        2        | tamil_movie   | action    | 2016-05-17  |      112000.00 |    118000.00 | Released   |
|        5        | telugu_movie  | action    | 0000-00-00  |      100000.00 |         NULL | UnReleased |
|        6        | punjabi_movie | comedy    | 0000-00-00  |       30500.00 |         NULL | UnReleased |
+-------------+---------------------+-------------+------------------+----------------------+----------------+

```
f. List all movies which fall in the category of Comedy or Action
```sql
SELECT *
     FROM movies
     WHERE release_date IS NULL;
+-------------+--------------------+-------------+------------------+---------------------+------------------+
| movie_id        | moviename     | category | release_date | productioncost | businesscost | status     |
+-------------+--------------------+-------------+-------------------+---------------------+-----------------+
|        5        | telugu_movie  | action   | 0000-00-00   |      100000.00  |     NULL     | UnReleased|
|        6        | punjabi_movie | comedy   | 0000-00-00   |       30500.00  |     NULL     | UnReleased|
+-------------+---------------------+-------------+-------------------+----------------------+---------------+

```