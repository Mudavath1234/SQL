# SQL
Lab Practice Commands
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| B192476            |
| DBMS               |
| DBMS_lab2          |
| Department         |
| Employee           |
| Students           |
| Uday               |
| db                 |
| dbms_lab3          |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
13 rows in set (0.07 sec)

mysql> use DBMS
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+----------------+
| Tables_in_DBMS |
+----------------+
| Boats          |
| Reserves       |
| sailors        |
+----------------+
3 rows in set (0.00 sec)

mysql> create table employee(id int,name varchar(20),age int,salary int);
Query OK, 0 rows affected (0.77 sec)

mysql> show tables
    -> ;
+----------------+
| Tables_in_DBMS |
+----------------+
| Boats          |
| Reserves       |
| employee       |
| sailors        |
+----------------+
4 rows in set (0.01 sec)

mysql> desc employee;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int         | YES  |     | NULL    |       |
| name   | varchar(20) | YES  |     | NULL    |       |
| age    | int         | YES  |     | NULL    |       |
| salary | int         | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> alter table employee add column email varchar(20);
Query OK, 0 rows affected (0.63 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc employee;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int         | YES  |     | NULL    |       |
| name   | varchar(20) | YES  |     | NULL    |       |
| age    | int         | YES  |     | NULL    |       |
| salary | int         | YES  |     | NULL    |       |
| email  | varchar(20) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> alter table employee rename column age to year_of_exp;
Query OK, 0 rows affected (0.58 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc employee;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| id          | int         | YES  |     | NULL    |       |
| name        | varchar(20) | YES  |     | NULL    |       |
| year_of_exp | int         | YES  |     | NULL    |       |
| salary      | int         | YES  |     | NULL    |       |
| email       | varchar(20) | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
5 rows in set (0.01 sec)

mysql> alter table employee drop column salary;
Query OK, 0 rows affected (0.51 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc employee;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| id          | int         | YES  |     | NULL    |       |
| name        | varchar(20) | YES  |     | NULL    |       |
| year_of_exp | int         | YES  |     | NULL    |       |
| email       | varchar(20) | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
4 rows in set (0.01 sec)

mysql> create table department(id int,name varchar(20));
Query OK, 0 rows affected (1.17 sec)

mysql> alter table employee add primary key(id);
Query OK, 0 rows affected (1.31 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc employee;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| id          | int         | NO   | PRI | NULL    |       |
| name        | varchar(20) | YES  |     | NULL    |       |
| year_of_exp | int         | YES  |     | NULL    |       |
| email       | varchar(20) | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
4 rows in set (0.01 sec)

mysql> desc department;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | YES  |     | NULL    |       |
| name  | varchar(20) | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.01 sec)

mysql> alter table employee add column dept_id int foreign key(dept_id) references department(id);
mysql> alter table employee add column dept_id int;
Query OK, 0 rows affected (0.45 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc employee;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| id          | int         | NO   | PRI | NULL    |       |
| name        | varchar(20) | YES  |     | NULL    |       |
| year_of_exp | int         | YES  |     | NULL    |       |
| email       | varchar(20) | YES  |     | NULL    |       |
| dept_id     | int         | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> desc employee;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| id          | int         | NO   | PRI | NULL    |       |
| name        | varchar(20) | YES  |     | NULL    |       |
| year_of_exp | int         | YES  |     | NULL    |       |
| email       | varchar(20) | YES  |     | NULL    |       |
| dept_id     | int         | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> select * from department;
Empty set (0.00 sec)

mysql> desc department
    -> ;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | YES  |     | NULL    |       |
| name  | varchar(20) | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> alter table department add primary key(id);
Query OK, 0 rows affected (1.84 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table employee add foreign key(dept_id) references department(id);
Query OK, 0 rows affected (1.73 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table employee add constraint email unique;
mysql> alter table employee add unique(email);
Query OK, 0 rows affected (0.69 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc employee;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| id          | int         | NO   | PRI | NULL    |       |
| name        | varchar(20) | YES  |     | NULL    |       |
| year_of_exp | int         | YES  |     | NULL    |       |
| email       | varchar(20) | YES  | UNI | NULL    |       |
| dept_id     | int         | YES  | MUL | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
5 rows in set (0.01 sec)

mysql> drop table employee;
Query OK, 0 rows affected (0.66 sec)

mysql> truncate table department;
Query OK, 0 rows affected (1.13 sec)

mysql> desc employee;
ERROR 1146 (42S02): Table 'DBMS.employee' doesn't exist
mysql> desc department;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | NO   | PRI | NULL    |       |
| name  | varchar(20) | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.01 sec)

mysql> create table customer(id int,name varchar(20),email varchar(20),phone_number varchar(13));
Query OK, 0 rows affected (0.98 sec)

mysql> desc customer;
+--------------+-------------+------+-----+---------+-------+
| Field        | Type        | Null | Key | Default | Extra |
+--------------+-------------+------+-----+---------+-------+
| id           | int         | YES  |     | NULL    |       |
| name         | varchar(20) | YES  |     | NULL    |       |
| email        | varchar(20) | YES  |     | NULL    |       |
| phone_number | varchar(13) | YES  |     | NULL    |       |
+--------------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> alter table customer add column address text;
Query OK, 0 rows affected (1.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc customer;
+--------------+-------------+------+-----+---------+-------+
| Field        | Type        | Null | Key | Default | Extra |
+--------------+-------------+------+-----+---------+-------+
| id           | int         | YES  |     | NULL    |       |
| name         | varchar(20) | YES  |     | NULL    |       |
| email        | varchar(20) | YES  |     | NULL    |       |
| phone_number | varchar(13) | YES  |     | NULL    |       |
| address      | text        | YES  |     | NULL    |       |
+--------------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> alter table customer rename column phone_number to contact_num;
Query OK, 0 rows affected (0.50 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc customer;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| id          | int         | YES  |     | NULL    |       |
| name        | varchar(20) | YES  |     | NULL    |       |
| email       | varchar(20) | YES  |     | NULL    |       |
| contact_num | varchar(13) | YES  |     | NULL    |       |
| address     | text        | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> alter table customer drop column email;
Query OK, 0 rows affected (0.66 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc customer;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| id          | int         | YES  |     | NULL    |       |
| name        | varchar(20) | YES  |     | NULL    |       |
| contact_num | varchar(13) | YES  |     | NULL    |       |
| address     | text        | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> create table orders(id int,c_id int,p_name varchar(10),o_date date);
Query OK, 0 rows affected (1.97 sec)

mysql> show tables;
+----------------+
| Tables_in_DBMS |
+----------------+
| Boats          |
| Reserves       |
| customer       |
| department     |
| orders         |
| sailors        |
+----------------+
6 rows in set (0.00 sec)

mysql> desc orders;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int         | YES  |     | NULL    |       |
| c_id   | int         | YES  |     | NULL    |       |
| p_name | varchar(10) | YES  |     | NULL    |       |
| o_date | date        | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
4 rows in set (0.01 sec)

mysql> desc customer;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| id          | int         | YES  |     | NULL    |       |
| name        | varchar(20) | YES  |     | NULL    |       |
| contact_num | varchar(13) | YES  |     | NULL    |       |
| address     | text        | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
4 rows in set (0.01 sec)

mysql> alter table customer add primary key(id);
Query OK, 0 rows affected (1.32 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table orders add foreign key(c_id) references customer(id);
Query OK, 0 rows affected (2.89 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table customer add unique(name);
Query OK, 0 rows affected (0.43 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> drop table orders;
Query OK, 0 rows affected (0.47 sec)

mysql> truncate table customer;
Query OK, 0 rows affected (1.04 sec)

mysql> create table supplier(id int,name varchar(20),address text,c_number varchar(13));
Query OK, 0 rows affected (0.67 sec)

mysql> alter table supplier add column email varchar(20);
Query OK, 0 rows affected (0.45 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc supplier;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| id       | int         | YES  |     | NULL    |       |
| name     | varchar(20) | YES  |     | NULL    |       |
| address  | text        | YES  |     | NULL    |       |
| c_number | varchar(13) | YES  |     | NULL    |       |
| email    | varchar(20) | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> alter table supplier rename column address to location;
Query OK, 0 rows affected (0.52 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc supplier;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| id       | int         | YES  |     | NULL    |       |
| name     | varchar(20) | YES  |     | NULL    |       |
| location | text        | YES  |     | NULL    |       |
| c_number | varchar(13) | YES  |     | NULL    |       |
| email    | varchar(20) | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> alter table supplier add primary key(id);
Query OK, 0 rows affected (1.62 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc supplier;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| id       | int         | NO   | PRI | NULL    |       |
| name     | varchar(20) | YES  |     | NULL    |       |
| location | text        | YES  |     | NULL    |       |
| c_number | varchar(13) | YES  |     | NULL    |       |
| email    | varchar(20) | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> alter table supplier add unique(name);
Query OK, 0 rows affected (0.49 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc supplier;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| id       | int         | NO   | PRI | NULL    |       |
| name     | varchar(20) | YES  | UNI | NULL    |       |
| location | text        | YES  |     | NULL    |       |
| c_number | varchar(13) | YES  |     | NULL    |       |
| email    | varchar(20) | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> create table invoices(id int,c_id int,amount int,d_date date);
Query OK, 0 rows affected (0.83 sec)

mysql> desc invoices;
+--------+------+------+-----+---------+-------+
| Field  | Type | Null | Key | Default | Extra |
+--------+------+------+-----+---------+-------+
| id     | int  | YES  |     | NULL    |       |
| c_id   | int  | YES  |     | NULL    |       |
| amount | int  | YES  |     | NULL    |       |
| d_date | date | YES  |     | NULL    |       |
+--------+------+------+-----+---------+-------+
4 rows in set (0.01 sec)

mysql> alter table invoices add column p_date date;
Query OK, 0 rows affected (0.49 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc invoices;
+--------+------+------+-----+---------+-------+
| Field  | Type | Null | Key | Default | Extra |
+--------+------+------+-----+---------+-------+
| id     | int  | YES  |     | NULL    |       |
| c_id   | int  | YES  |     | NULL    |       |
| amount | int  | YES  |     | NULL    |       |
| d_date | date | YES  |     | NULL    |       |
| p_date | date | YES  |     | NULL    |       |
+--------+------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> alter table invoices rename column amount to invoice_amount;
Query OK, 0 rows affected (0.44 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc invoices;
+----------------+------+------+-----+---------+-------+
| Field          | Type | Null | Key | Default | Extra |
+----------------+------+------+-----+---------+-------+
| id             | int  | YES  |     | NULL    |       |
| c_id           | int  | YES  |     | NULL    |       |
| invoice_amount | int  | YES  |     | NULL    |       |
| d_date         | date | YES  |     | NULL    |       |
| p_date         | date | YES  |     | NULL    |       |
+----------------+------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> alter table invoices drop column d_date;
Query OK, 0 rows affected (0.68 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc invoices;
+----------------+------+------+-----+---------+-------+
| Field          | Type | Null | Key | Default | Extra |
+----------------+------+------+-----+---------+-------+
| id             | int  | YES  |     | NULL    |       |
| c_id           | int  | YES  |     | NULL    |       |
| invoice_amount | int  | YES  |     | NULL    |       |
| p_date         | date | YES  |     | NULL    |       |
+----------------+------+------+-----+---------+-------+
4 rows in set (0.01 sec)

mysql> create table payment(id int,in_id int,amount int,pay_date date); 
Query OK, 0 rows affected (1.37 sec)

mysql> desc payment;
+----------+------+------+-----+---------+-------+
| Field    | Type | Null | Key | Default | Extra |
+----------+------+------+-----+---------+-------+
| id       | int  | YES  |     | NULL    |       |
| in_id    | int  | YES  |     | NULL    |       |
| amount   | int  | YES  |     | NULL    |       |
| pay_date | date | YES  |     | NULL    |       |
+----------+------+------+-----+---------+-------+
4 rows in set (0.01 sec)

mysql> alter table invoices add primary key(id);
Query OK, 0 rows affected (1.42 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc invoices;
+----------------+------+------+-----+---------+-------+
| Field          | Type | Null | Key | Default | Extra |
+----------------+------+------+-----+---------+-------+
| id             | int  | NO   | PRI | NULL    |       |
| c_id           | int  | YES  |     | NULL    |       |
| invoice_amount | int  | YES  |     | NULL    |       |
| p_date         | date | YES  |     | NULL    |       |
+----------------+------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> alter table invoices add unique(id);
Query OK, 0 rows affected (0.40 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc invoices;
+----------------+------+------+-----+---------+-------+
| Field          | Type | Null | Key | Default | Extra |
+----------------+------+------+-----+---------+-------+
| id             | int  | NO   | PRI | NULL    |       |
| c_id           | int  | YES  |     | NULL    |       |
| invoice_amount | int  | YES  |     | NULL    |       |
| p_date         | date | YES  |     | NULL    |       |
+----------------+------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> desc payment;
+----------+------+------+-----+---------+-------+
| Field    | Type | Null | Key | Default | Extra |
+----------+------+------+-----+---------+-------+
| id       | int  | YES  |     | NULL    |       |
| in_id    | int  | YES  |     | NULL    |       |
| amount   | int  | YES  |     | NULL    |       |
| pay_date | date | YES  |     | NULL    |       |
+----------+------+------+-----+---------+-------+
4 rows in set (0.01 sec)

mysql> alter table payment add foreign key(in_id) references invoices(id); 
Query OK, 0 rows affected (2.15 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table invoices add check(invoice_amount>0);
Query OK, 0 rows affected (2.30 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc invoices;
+----------------+------+------+-----+---------+-------+
| Field          | Type | Null | Key | Default | Extra |
+----------------+------+------+-----+---------+-------+
| id             | int  | NO   | PRI | NULL    |       |
| c_id           | int  | YES  |     | NULL    |       |
| invoice_amount | int  | YES  |     | NULL    |       |
| p_date         | date | YES  |     | NULL    |       |
+----------------+------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> drop table payment;
Query OK, 0 rows affected (0.42 sec)

mysql> truncate table invoices;
Query OK, 0 rows affected (1.77 sec)
