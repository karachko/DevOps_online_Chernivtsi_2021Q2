
# TASK 3.1 #
## PART 1 ##
1. I installed MySql server on Ubuntu 18.04
- sudo apt update
- sudo apt install mysql-server
- I checked that mysql had been started 
- sudo netstat -tap | grep mysql
```
tcp        0      0 localhost:33060         0.0.0.0:*               LISTEN      3143/mysqld
tcp        0      0 localhost:mysql         0.0.0.0:*               LISTEN      3143/mysqld

```
- I lanched to mysql 
    - sudo mysql
3.I chose the subject area - pharmacies
- I created table PHARMACY with the list of pharmacies(PH_ID- the unique identifier of PHARMACY,PH_Name-the nameof PHARMACY)

|PH_ID     |PH_Name    |PRIMARY KEY|
|----------|-----------|-----------|
|smallint  |VARCHAR(30)|PH_ID      |

- I created table PREPARATION with the list of preparations in pharmacy(PR_ID- the unique identifier of preparation,PR_Name-the nameof preparation,PHARMACY_ID- the unique identifier of PHARMACY)
- 
|PR_ID     |PR_Name    |PHARMACY_ID|PRIMARY KEY|FOREIGN KEY|
|----------|-----------|-----------|-----------|-----------|
|smallint  |VARCHAR(30)|smallint   |PR_ID      |PHARMACY_ID|

- I created table CLIENT with the list of clients in pharmacy(C_ID- the unique identifier of client,PR_ID- the unique identifier of preparation,PR_Name-the nameof preparation,PHARMACY_ID- the unique identifier of PHARMACY,C_NameF the first name of client,C_NameL the last name of client)
- 
|C_ID      |PR_ID      | PR_Name   | C_NameF   |C_NameL    |PHARMACY_ID|PRIMARY KEY|FOREIGN KEY|
|----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|
|smallint  |smallint   |VARCHAR(30)|VARCHAR(30)|VARCHAR(30)|smallint   |C_ID        |PR_ID     |

4. I created tables
- CREATE DATABASE PHARMNETWORK CHARACTER SET utf8 COLLATE utf8_general_ci;
CHARACTER SET
Определение кодировки таблиц базы данных.
COLLATE
Определение порядка сортировки данных.
- USE PHARMNETWORK
- CREATE TABLE PHARMACY(PH_ID smallint,  PH_Name VARCHAR(30) NOT NULL, PRIMARY KEY(PH_ID));
-  CREATE TABLE PREPARATION (
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
5. I filled in tables 
- INSERT PHARMACY(PH_ID, PH_Name) 
- VALUES ('1', 'Stay_helphy');
- INSERT PHARMACY(PH_ID, PH_Name) 
- VALUES ('2', 'Bless_yourself');

- INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name) 
- VALUES ('1','101', 'Amizon');
- INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name)  
- VALUES ('1','102', 'VitaminD');
- INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name)  
- VALUES ('1','103', 'VitaminZinc');
- INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name)  
- VALUES ('1','104', 'VitaminC');

- INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name) 
- VALUES ('2','201', 'Amizon');
- INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name)  
- VALUES ('2','202', 'VitaminD');
- INSERT PREPARATION(PHARMACY_ID, PR_ID, PR_Name)  
- VALUES ('2','204', 'VitaminC');

- INSERT CLIENT(PHARMACY_ID, PR_Name, C_ID, C_NameF, C_NameL) 
- VALUES ('1', 'Amizon', '345', 'Ivan', 'Ivanov');
- INSERT CLIENT(PHARMACY_ID, PR_Name, C_ID, C_NameF, C_NameL) 
- VALUES ('2', 'Amizon', '2345', 'Ivan', 'Ivanov');
- INSERT CLIENT(PHARMACY_ID, PR_Name, C_ID, C_NameF, C_NameL) 
- VALUES ('1', 'Amizon', '346', 'Petro', 'Petrov');
- INSERT CLIENT(PHARMACY_ID, PR_Name, C_ID, C_NameF, C_NameL) 
- VALUES ('2', 'Amizon', '3462', 'Petro', 'Petrov');
6.  I constructed and executed SELECT
- SELECT * FROM CLIENT WHERE C_NameL = 'Petrov';
- 
![select-were.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/select-were.jpg)
- SELECT * FROM PHARMACY
GROUP BY PH_ID;

(select-groupby.jpg)![select-groupby.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/select-groupby.jpg)
- SELECT * FROM PREPARATION WHERE PHARMACY_ID = 1
ORDER BY PR_Name;

(select-order-by.jpg)![select-groupby.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/select-order-by.jpg)
7.
- DDL 
   - I added a new column with Price (table Preparation , database PHARMNETWORK )
   - USE PHARMNETWORK
   - ALTER TABLE PREPARATION
   - ADD PR_PRICE INT NOT NULL;
   - (ddl.jpg)![ddl.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/ddl.jpg)
- DML(I deleted the preparation VitaminZinc )
    - DELETE FROM PREPARATION 
    - WHERE PR_Name = 'VitaminZinc';
-DCL
    -  I allowed GRANT UPDATE to user Newuser
    - CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
    - GRANT UPDATE ON PREPARATION TO'newuser'@'localhost;
   
 8. I set up **Create GRANT ALL PRIVILEGES** for newuser
- GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
- quit
- sudo mysql -u newuser -p
- use PHARMNETWORK
- SELECT * FROM PREPARATION WHERE PHARMACY_ID = 1 ORDER BY PR_Name;
- (81.jpg)![81.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/81.jpg)
 
- sudo mysql
- REVOKE ALL PRIVILEGES ON * . * FROM 'newuser'@'localhost';
- quit
- sudo mysql -u newuser -p
- (82.jpq)![82.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/82.jpg)

9. GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
- quit
- sudo mysql -u newuser -p
- use PHARMNETWORK
- SELECT * FROM CLIENT WHERE C_NameL = 'Petrov';
- 
![select-were.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/select-were.jpg)

## PART 2 ##
10. I backed-up the database PHARMNETWORK
- In the terminal :  sudo mysqldump PHARMNETWORK > /home/karachko/PHARMNETWORK_28032021.sql
(10.1.jpg)![10.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/10.1.jpg)
11. I deleted the table CLIENT
- sudo mysql
- use PHARMNETWORK
- DROP TABLE CLIENT;
- The message``` "Query OK, 0 rows affected (46.07 sec)"``` had been displayed
- I did the select quary from the table CLIENT ````mysql> SELECT * FROM CLIENT WHERE C_NameL = 'Petrov';
ERROR 1146 (42S02): Table 'PHARMNETWORK.CLIENT' doesn't exist```
mysql>
12.
- I restored  DATABASE PHARMNETWORK
- sudo mysql
- DROP DATABASE PHARMNETWORK
- CREATE DATABASE PHARMNETWORK 
- In the terminal :sudo mysql PHARMNETWORK < /home/karachko/PHARMNETWORK_28032021.sql
- sudo mysql
- use PHARMNETWORK
show tables;
(12.jpg)![12.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/12.jpg)
SELECT * FROM CLIENT WHERE C_NameL = 'Petrov';
(12.1.jpg)![12.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/12.1.jpg)
13. I Transfered my local database to RDS AWS
- I opened Amazon RDS-Dashboard-Create database
- I selected-Engine options-My SQL
- I chose Templates-Free tier
- I chose DB instance identifier karachkodb
    - master username -admin
    - password - df4tn2gw
- I chose Connectivity
    - Public access-Yes
    - VPC security group-  (create vpc-mysql,  vpc -default vpc-966ad6eb,VPC security groups-vpc-mysql( inbound roule type- my sql,protocol-3306, ip -my IP 109.229.12.151/32)-Save rules)
   
   
- MY Endpoint
karachkodb.cfmlgo87dbxs.us-east-1.rds.amazonaws.com
14.
- On my VM with Ubuntu in CLI (to connected with my Amazon RDS karachkodb)i entered 
 mysql -h karachkodb.cfmlgo87dbxs.us-east-1.rds.amazonaws.com -P 3306 -u admin -p
- I successfully lanched in mysql  
- I checked (Did the base karachkodb exist?).SHOW databases; ![show-database.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/show-database.jpg)



- The karachkodb had not existed. I tried to create my database on AWS RDW in anyways, but the karachkodb had not existed. I thought maybe it was the Frie Tier version. This is did not allow to show the databases(or it was the error in AWS RDS). All my settings in AWS RDS were from the instructions from the AWS site.
- On my VM with Ubuntu in CLI (to connected with my Amazon RDS karachkodb) i entered 
-  mysql -h karachkodb.cfmlgo87dbxs.us-east-1.rds.amazonaws.com -P 3306 -u admin -p
 - I created the new database DATABASE1
- CREATE DATABASE DATABASE1
 - I uploaded PHARMNETWORK_28032021.sql to DATABASE1
- mysql -u admin -p -h karachkodb.cfmlgo87dbxs.us-east-1.rds.amazonaws.com -D DATABASE1 < /home/karachko/PHARMNETWORK_28032021.sql 

15. I executed SELECT operator
- mysql -h karachkodb.cfmlgo87dbxs.us-east-1.rds.amazonaws.com -P 3306 -u admin -p
- SELECT * FROM PHARMACY
- ![selectfromfarmacy.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/selectfromfarmacy.jpg)
16. I created the dump
- mysqldump --databases DATABASE1 -h karachkodb.cfmlgo87dbxs.us-east-1.rds.amazonaws.com -u admin -P 3306 -p > rds.sql
- ![mysqldump.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/mysqldump.jpg)
- The dump of Database1 had been created
- ![rdssql.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/rdssql.jpg)
## PART 3 ##
17. I created an Amazon DynamoDB table(Amazon DynamoDB-create table)
    - Table name - Music
    - Primary key - Artist
    - Add sort key-Title 
    - I unchecked **Use default settings.** in the Table setting
    - I pushed the button "Create"
18. I added date into the table Music
    - I chose name Music- Item-create Item (Artist: No One You Know; Title: My Dog Spot
Artist: No One You Know; Title: Somewhere Down The Road
Artist: The Acme Band; Title: Still in Love
Artist: The Acme Band; Title: Look Out, World
)
19. I did Query an Amazon DynamoDB table using Query and Scan.
- I chose table name Music- Items - I changed Scan to Query. I chose Partition key No One You Know
- I pushed the button Start search
- (dynamodb.jpg)![dynamodb.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m3/dynamodb.jpg)
- I changed Query to Scan.
- I set up filter to Artist and value to The Acme Band
- I pushed the button Start search
