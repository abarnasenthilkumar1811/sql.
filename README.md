mysql> use fss;
Database changed
mysql> create table studentprofile(rollno int(10),name varchar(10),dob date,department varchar(6),city varchar(10));
Query OK, 0 rows affected, 1 warning (0.04 sec)

mysql> create table marks(rollno int(10),name varchar(10),mark1 int(3), mark2 int(3));
Query OK, 0 rows affected, 3 warnings (0.04 sec)

mysql> insert into studentprofile values(201,'aparna','2006-02-18',bsc,coimbatore);
ERROR 1054 (42S22): Unknown column 'bsc' in 'field list'
mysql> insert into studentprofile values(201,'aparna','2006-02-18','bsc','coimbatore');
Query OK, 1 row affected (0.01 sec)

mysql> insert into studentprofile values(202,'vikas','2005-07-11','bscom','chennai'););
Query OK, 1 row affected (0.02 sec)

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 1
mysql> insert into studentprofile values(202,'vikas','2005-07-11','bscom','chennai');
Query OK, 1 row affected (0.01 sec)

mysql> insert into studentprofile values(203,'danu','2004-06-13','viscom','bombay');
Query OK, 1 row affected (0.02 sec)

mysql> insert into studentprofile values(204,'dani','2000-04-10','english','jaipur');
ERROR 1406 (22001): Data too long for column 'department' at row 1
mysql> insert into studentprofile values(204,'dani','2000-04-10','eng','jaipur');
Query OK, 1 row affected (0.02 sec)

mysql> insert into studentprofile values(205,'rosw','2010-09-01','tam','jaipur');
Query OK, 1 row affected (0.02 sec)

mysql> insert into marks values(200,'abu','200','22');
Query OK, 1 row affected (0.02 sec)

mysql> insert into marks values(100,'abi','209','20');
Query OK, 1 row affected (0.02 sec)

mysql> insert into marks values(300,'anu','206','21');
Query OK, 1 row affected (0.02 sec)

mysql> insert into marks values(400,'rani','204','18');
Query OK, 1 row affected (0.02 sec)

mysql> insert into marks values(500,'ranu','201','17');
Query OK, 1 row affected (0.02 sec)

mysql> alter table marks add total int(10);
Query OK, 0 rows affected, 1 warning (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 1

mysql> alter table studentprofile rename column dob to dateofbirth;
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc studentprofile;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| rollno      | int         | YES  |     | NULL    |       |
| name        | varchar(10) | YES  |     | NULL    |       |
| dateofbirth | date        | YES  |     | NULL    |       |
| department  | varchar(6)  | YES  |     | NULL    |       |
| city        | varchar(10) | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> desc marks;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| rollno | int         | YES  |     | NULL    |       |
| name   | varchar(10) | YES  |     | NULL    |       |
| mark1  | int         | YES  |     | NULL    |       |
| mark2  | int         | YES  |     | NULL    |       |
| total  | int         | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> show tables;
+----------------+
| Tables_in_fss  |
+----------------+
| boat           |
| marks          |
| reserves       |
| sailor         |
| studentprofile |
+----------------+
5 rows in set (0.01 sec)

mysql> update marks set total=mark1+mark2);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 1
mysql> update marks set total=total(mark1+mark2));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 1
mysql> update marks set total=sum(mark1+mark2);
ERROR 1111 (HY000): Invalid use of group function
mysql> update marks set total=total(mark1+mark2);
ERROR 1305 (42000): FUNCTION fss.total does not exist
mysql> update marks set total=mark1+mark2;
Query OK, 5 rows affected (0.02 sec)
Rows matched: 5  Changed: 5  Warnings: 0

mysql> select*from table marks;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'table marks' at line 1
mysql> select*from marks;
+--------+------+-------+-------+-------+
| rollno | name | mark1 | mark2 | total |
+--------+------+-------+-------+-------+
|    200 | abu  |   200 |    22 |   222 |
|    100 | abi  |   209 |    20 |   229 |
|    300 | anu  |   206 |    21 |   227 |
|    400 | rani |   204 |    18 |   222 |
|    500 | ranu |   201 |    17 |   218 |
+--------+------+-------+-------+-------+
5 rows in set (0.00 sec)

mysql> delete from studentprotfolio where rollno='204';
ERROR 1146 (42S02): Table 'fss.studentprotfolio' doesn't exist
mysql> delete from studentprotfile where rollno='204';
ERROR 1146 (42S02): Table 'fss.studentprotfile' doesn't exist
mysql> delete from studentprofile where rollno='204';
Query OK, 1 row affected (0.02 sec)

mysql> select*studentprofile;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'studentprofile' at line 1
mysql> select* from studentprofile;
+--------+--------+-------------+------------+------------+
| rollno | name   | dateofbirth | department | city       |
+--------+--------+-------------+------------+------------+
|    201 | aparna | 2006-02-18  | bsc        | coimbatore |
|    202 | vikas  | 2005-07-11  | bscom      | chennai    |
|    202 | vikas  | 2005-07-11  | bscom      | chennai    |
|    203 | danu   | 2004-06-13  | viscom     | bombay     |
|    205 | rosw   | 2010-09-01  | tam        | jaipur     |
+--------+--------+-------------+------------+------------+
5 rows in set (0.00 sec)

mysql> select* from marks;
+--------+------+-------+-------+-------+
| rollno | name | mark1 | mark2 | total |
+--------+------+-------+-------+-------+
|    200 | abu  |   200 |    22 |   222 |
|    100 | abi  |   209 |    20 |   229 |
|    300 | anu  |   206 |    21 |   227 |
|    400 | rani |   204 |    18 |   222 |
|    500 | ranu |   201 |    17 |   218 |
+--------+------+-------+-------+-------+
5 rows in set (0.00 sec)

mysql> rollback;
Query OK, 0 rows affected (0.00 sec)

mysql> alter table marks add column average int(10) ,add column grade varchar(10);
Query OK, 0 rows affected, 1 warning (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 1

mysql> update marks set average=mark1+mark2/2;
Query OK, 5 rows affected (0.02 sec)
Rows matched: 5  Changed: 5  Warnings: 0

mysql> select*from marks;
+--------+------+-------+-------+-------+---------+-------+
| rollno | name | mark1 | mark2 | total | average | grade |
+--------+------+-------+-------+-------+---------+-------+
|    200 | abu  |   200 |    22 |   222 |     211 | NULL  |
|    100 | abi  |   209 |    20 |   229 |     219 | NULL  |
|    300 | anu  |   206 |    21 |   227 |     217 | NULL  |
|    400 | rani |   204 |    18 |   222 |     213 | NULL  |
|    500 | ranu |   201 |    17 |   218 |     210 | NULL  |
+--------+------+-------+-------+-------+---------+-------+
5 rows in set (0.00 sec)

mysql> select  marks1,marks2 when mark1>=40 and mark2>=40 then 'pass'else 'fail' from marks;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'when mark1>=40 and mark2>=40 then 'pass'else 'fail' from marks' at line 1
mysql> update marks set grade when mark1>=40,mark2>=40 is 'pass';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'when mark1>=40,mark2>=40 is 'pass'' at line 1
mysql> update marks set grade when mark1>=40,mark2>=40 = 'pass';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'when mark1>=40,mark2>=40 = 'pass'' at line 1
mysql> ICT Academy -LEARNATHON 2023-
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ICT Academy -LEARNATHON 2023-' at line 1
mysql> 
mysql> Terminal close -- exit!
