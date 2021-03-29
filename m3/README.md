
(1.jpg)![1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m1/task2.2/1.jpg)
1. I installed MySql server on Ubuntu 18.04
sudo apt update
sudo apt install mysql-server
I cheched that mysql had been started 
sudo netstat -tap | grep mysql
```
tcp        0      0 localhost:33060         0.0.0.0:*               LISTEN      3143/mysqld
tcp        0      0 localhost:mysql         0.0.0.0:*               LISTEN      3143/mysqld

```
I entered to mysql 
sudo mysql
3.
4. 
- CREATE DATABASE PHARMNETWORK CHARACTER SET utf8 COLLATE utf8_general_ci;
CHARACTER SET
Определение кодировки таблиц базы данных.
COLLATE
Определение порядка сортировки данных.
- USE PHARMNETWORK
- CREATE TABLE PHARMACY(PH_ID smallint,  PH_Name VARCHAR(30) NOT NULL, PRIMARY KEY(PH_ID));
- 
 CREATE TABLE PREPARATION (
    PR_ID smallint,
    PHARMACY_ID smallint,
    PR_Name VARCHAR(30) NOT NULL,
    PRIMARY KEY (PR_ID),
    FOREIGN KEY (PHARMACY_ID) REFERENCES PHARMACY(PH_ID)); 
- CREATE TABLE CLIENT (C_ID smallint,
    PHARMACY_ID smallint,
    PR_ID smallint,
    PR_Name VARCHAR(30) NOT NULL,
    C_NameF VARCHAR(30) NOT NULL,
    C_NameL VARCHAR(30) NOT NULL,
    PRIMARY KEY (C_ID),
    FOREIGN KEY (PR_ID) REFERENCES PREPARATION(PR_ID)
    ); 
5.
I filled in tables 
INSERT PHARMACY(PH_ID, PH_Name) 
VALUES ('1', 'Stay_helphy');
INSERT PHARMACY(PH_ID, PH_Name) 
VALUES ('2', 'Bless_yourself');

INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name) 
VALUES ('1','101', 'Amizon');
INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name)  
VALUES ('1','102', 'VitaminD');
INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name)  
VALUES ('1','103', 'VitaminZinc');
INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name)  
VALUES ('1','104', 'VitaminC');

INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name) 
VALUES ('2','201', 'Amizon');
INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name)  
VALUES ('2','202', 'VitaminD');
INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name)  
VALUES ('2','204', 'VitaminC');

INSERT CLIENT(PHARMACY_ID, PR_Name, C_ID, C_NameF, C_NameL) 
VALUES ('1', 'Amizon', '345', 'Ivan', 'Ivanov');
INSERT CLIENT(PHARMACY_ID, PR_Name, C_ID, C_NameF, C_NameL) 
VALUES ('2', 'Amizon', '2345', 'Ivan', 'Ivanov');
INSERT CLIENT(PHARMACY_ID, PR_Name, C_ID, C_NameF, C_NameL) 
VALUES ('1', 'Amizon', '346', 'Petro', 'Petrov');
INSERT CLIENT(PHARMACY_ID, PR_Name, C_ID, C_NameF, C_NameL) 
VALUES ('2', 'Amizon', '3462', 'Petro', 'Petrov');
6.  SELECT * FROM CLIENT WHERE C_NameL = 'Petrov';
(select-were.jpg)
SELECT * FROM PHARMACY
GROUP BY PH_ID;
(select-groupby.jpg)
SELECT * FROM PREPARATION WHERE PHARMACY_ID = 1
ORDER BY PR_Name;
(select-order-by.jpg)
7.
-DDL
Adding a new column Price (table Preparation , database PHARMNETWORK )
USE PHARMNETWORK
ALTER TABLE PREPARATION
ADD PR_PRICE INT NOT NULL;(ddl.jpg)
-DML
DELETE FROM PREPARATION 
WHERE PR_Name = 'VitaminZinc';
-DCL
GRANT
 CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
  GRANT UPDATE ON PREPARATION TO'newuser'@'localhost;
sudo mysql -u newuser -p
https://www.digitalocean.com/community/tutorials/mysql-ru

8.
1)GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
quit
sudo mysql -u newuser -p
use PHARMNETWORK
SELECT * FROM PREPARATION WHERE PHARMACY_ID = 1 ORDER BY PR_Name;
(8.1.jpg)
2) sudo mysql
REVOKE ALL PRIVILEGES ON * . * FROM 'newuser'@'localhost';
quit
sudo mysql -u newuser -p
(8.2.jpq)

PART 2
10. 

In the terminal :  sudo mysqldump PHARMNETWORK > /home/karachko/PHARMNETWORK_28032021.sql
(10.1.jpg)
11.
- sudo mysql
- use PHARMNETWORK
- DROP TABLE CLIENT;
- ```The message "Query OK, 0 rows affected (46.07 sec)"``` had been displayed
- I did the select quary from the table CLIENT ````mysql> SELECT * FROM CLIENT WHERE C_NameL = 'Petrov';
ERROR 1146 (42S02): Table 'PHARMNETWORK.CLIENT' doesn't exist```
mysql>
12.

- I restored  DATABASE PHARMNETWORK

sudo mysql
DROP DATABASE PHARMNETWORK
CREATE DATABASE PHARMNETWORK 
In the terminal :sudo mysql PHARMNETWORK < /home/karachko/PHARMNETWORK_28032021.sql
sudo mysql
use PHARMNETWORK
show tables;
(12.jpg)
SELECT * FROM CLIENT WHERE C_NameL = 'Petrov';
(12.1.jpg)
13.
Amazon RDS-Dashboard-Create database
- Engine options-My SQL
- Templates-Free tier
- Setting-DB instance identifier database-1
master username admin
password df4tn2gw
- Connectivity
1)Public access-Yes
2)VPC security group-  (create vpc-mysql,  vpc -default vpc-966ad6eb,VPC security groups-vpc-mysql( inbound roule type- my sql,protocol-3306, ip -my IP 109.229.12.151/32
Save rules)
3) Availability zone -us-east-1a

 mysql -h database-1.cfmlgo87dbxs.us-east-1.rds.amazonaws.com -P 3306 -u admin -p
Перевірила зв'язок з базою
CREATE DATABASE DB1
SHOW databases;

Завантажила в базу DB1 базу PHARMNETWORK
mysql -u admin -p -h database-1.cfmlgo87dbxs.us-east-1.rds.amazonaws.com -D DB1 < /home/karachko/PHARMNETWORK_28032021.sql 


 SELECT * FROM PHARMACY
(db1.jpg-select1db1.jpg)

mysqldump --databases database1 -h database-1.cfmlgo87dbxs.us-east-1.rds.amazonaws.com -u karachko -P 3306 -p > rds.sql
mysqldump -P 3306 -h database-1.cfmlgo87dbxs.us-east-1.rds.amazonaws.com -u dbuser — password=karachko database1 | pv -W > dumpfile
