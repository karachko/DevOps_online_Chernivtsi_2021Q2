# TASK 4.2 #
## TASK1 #
1. I created the network for 2 buildings
- The first building with 2 groups of 5 PC's. 
    - Everyone PC's(The first building, the first group, the first foor) was assigned the IP-adress 
    - PC0 192.168.0.1
    - PC1 192.168.0.2
    - PC2 192.168.0.3
    - PC3 192.168.0.4
    - PC4 192.168.0.5
    - Everyone PC's(The first building, the second group, the second foor) was assigned the IP-adress 
    - PC0(1) 192.168.0.6
    - PC1(1) 192.168.0.7
    - PC2(1) 192.168.0.8
    - PC3(1) 192.168.0.9
    - PC4(1) 192.168.0.10
    - all PC's from the first group was connected with Switch0 via (Copper Straight-through)).
    - all PC's from the second group was connected with Switch0(1) via (Copper Straight-through)).
-  The second building with 2 groups of 5 PC's. 
    - Everyone PC's(The second  building, the first group, the first foor) was assigned the IP-adress 
    - PC0(2) 192.168.0.11
    - PC1(2) 192.168.0.12
    - PC2(2) 192.168.0.13
    - PC3(2) 192.168.0.14
    - PC4(2) 192.168.0.15
    - Everyone PC's(The second  building, the second group, the second foor) was assigned the IP-adress 
    - PC0(3) 192.168.0.16
    - PC1(3) 192.168.0.17
    - PC2(3) 192.168.0.18
    - PC3(3) 192.168.0.19
    - PC4(3) 192.168.0.20
    - all PC's from the first group was connected with Switch0(2) via (Copper Straight-through)).
    - all PC's from the second group was connected with Switch0(3) via (Copper Straight-through)).
- The Switch0 was connected with Switch1 via (Copper Cross-Over)).
- The Switch0(1) was connected with Switch1 via (Copper Cross-Over)).
- The Switch0(2) was connected with Switch1 via (Copper Cross-Over)). 
- The Switch0(3) was connected with Switch1 via (Copper Cross-Over)).

2. 
 - ![4-2-1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.2/4-2-1.jpg)
 
3. I checked the work of the network
 - ![4-2-2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.2/4-2-2.jpg)
 - ![4-2-2-3.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.2/4-2-2-3.jpg)
 
## TASK2 ##
1. I created the network for 1 buildings with 4 floor. All floor's includs 2 group of PC's(The first group-3 PC's, the second group -5  PC's)
- I created 8 subnets with the mask(/27)
- ![27maska.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.2/task4.2.2/27maska.jpg)
- ![27-8-subnet.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.2/task4.2.2/27-8-subnet.jpg)

- The 1 floor with 2 group of PC's(The first group-3 PC's, the second group -5  PC's).
    - Everyone PC's(The 1 floor, the first group) was assigned the IP-adress 
    - PC0 192.168.0.1/27
    - PC1 192.168.0.2/27
    - PC2 192.168.0.3/27
    - Everyone PC's(The 1 floor, the second group) was assigned the IP-adress 
    - PC0(2) 192.168.0.33/27
    - PC1(2) 192.168.0.34/27
    - PC2(2) 192.168.0.35/27
    - PC3(2) 192.168.0.36/27
    - PC4(2) 192.168.0.37/27
    - all PC's from the first group was connected with Switch0 via (Copper Straight-through)).
    - all PC's from the second group was connected with Switch0(2) via (Copper Straight-through)).
    - Switch0(port Fa4/1) was connected with Router2(port Fa 9/0, ip adress 192.164.0.4/27 ) via Fiber.
    - Switch0(2)(port Fa4/1) was connected with Router2(port Fa 5/0, ip adress 192.164.0.38/27) via Fiber.
 
- The 2 floor with 2 group of PC's(The first group-3 PC's, the second group -5  PC's).
    - Everyone PC's(The 2 floor, the first group) was assigned the IP-adress 
    - PC0(1) 192.168.0.65/27
    - PC1(1) 192.168.0.66/27
    - PC2(1) 192.168.0.67/27
    - Everyone PC's(The 2 floor, the second group) was assigned the IP-adress 
    - PC0(3) 192.168.0.97/27
    - PC1(3) 192.168.0.98/27
    - PC2(3) 192.168.0.99/27
    - PC3(3) 192.168.0.100/27
    - PC4(3) 192.168.0.101/27
    - all PC's from the first group was connected with Switch0(1) via (Copper Straight-through)).
    - all PC's from the second group was connected with Switch0(3) via (Copper Straight-through)).
    - Switch0(1)(port Fa4/1) was connected with Router2(port Fa 8/0, ip adress 192.164.0.68/27 ) via Fiber.
    - Switch0(3)(port Fa4/1) was connected with Router2(port Fa 4/0, ip adress 192.164.0.102/27) via Fiber

- The 3 floor with 2 group of PC's(The first group-3 PC's, the second group -5  PC's).
    - Everyone PC's(The 3 floor, the first group) was assigned the IP-adress 
    - PC0(4) 192.168.0.129/27
    - PC1(4) 192.168.0.130/27
    - PC2(4) 192.168.0.131/27
    - Everyone PC's(The 3 floor, the second group) was assigned the IP-adress 
    - PC0(2)(1) 192.168.0.161/27
    - PC1(2)(1) 192.168.0.162/27
    - PC2(2)(1) 192.168.0.163/27
    - PC3(2)(1) 192.168.0.164/27
    - PC4(2)(1) 192.168.0.165/27
    - all PC's from the first group was connected with Switch0(4) via (Copper Straight-through)).
    - all PC's from the second group was connected with Switch0(2)(1) via (Copper Straight-through)).
    - Switch0(4)(port Fa4/1) was connected with Router2(port Fa 7/0, ip adress 192.164.0.132/27 ) via Fiber.
    - Switch0(2)(1)(port Fa5/1) was connected with Router2(port Fa 3/0, ip adress 192.164.0.166/27) via Fiber
    

 - The 4 floor with 2 group of PC's(The first group-3 PC's, the second group -5  PC's).
    - Everyone PC's(The  floor, the first group) was assigned the IP-adress 
    - PC0(5) 192.168.0.193/27
    - PC1(5) 192.168.0.194/27
    - PC2(5) 192.168.0.195/27
    - Everyone PC's(The 3 floor, the second group) was assigned the IP-adress 
    - PC0(2)(2) 192.168.0.225/27
    - PC1(2)(2) 192.168.0.226/27
    - PC2(2)(2) 192.168.0.227/27
    - PC3(2)(2) 192.168.0.228/27
    - PC4(2)(2) 192.168.0.229/27
    - all PC's from the first group was connected with Switch0(5) via (Copper Straight-through)).
    - all PC's from the second group was connected with Switch0(2)(2) via (Copper Straight-through)).
    - Switch0(5)(port Fa4/1) was connected with Router2(port Fa 6/0, ip adress 192.164.0.196/27 ) via Fiber.
    - Switch0(2)(2)(port Fa4/1) was connected with Router2(port Fa 2/0, ip adress 192.164.0.230/27) via Fiber
-  Ports of the Router2(Fa2/0-Fa9/0) were switched on  (On)
-  Everyone PC's ,from each network ,was assigned the default gateway.
-  ![final.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.2/task4.2.2/final.jpg)
-  I checked the work of the network
-  ![succesfull1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.2/task4.2.2/successfull1.jpg)
-  ![succesfull2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.2/task4.2.2/succesfull2.jpg)

## TASK3 ##
 1. I created the network for 5 buildings
- The 1 building with 1 groups of 6 PC's. 
    - Everyone PC's was assigned the IP-adress 
    - PC0 192.168.0.1
    - PC1 192.168.0.2
    - PC2 192.168.0.3
    - PC2(1) 192.168.0.4
    - PC1(1) 192.168.0.5
    - PC3 192.168.0.6 
    - all PC's was connected with Switch0 via (Copper Straight-through)).
- The 2 building with 1 groups of 6 PC's. 
    - Everyone PC's was assigned the IP-adress 
    - PC0(2) 192.168.0.7
    - PC1(2) 192.168.0.8
    - PC2(2) 192.168.0.9
    - PC3(2) 192.168.0.10
    - PC4(2) 192.168.0.11
    - PC4 192.168.0.12
    - all PC's was connected with Switch0(2) via (Copper Straight-through)).
- The 3 building with 1 groups of 6 PC's. 
    - Everyone PC's was assigned the IP-adress 
    - PC0(3) 192.168.0.13
    - PC1(3) 192.168.0.14
    - PC2(3) 192.168.0.15
    - PC3(3) 192.168.0.16
    - PC4(3) 192.168.0.17
    - PC7 192.168.0.18
    - all PC's was connected with Switch0(2) via (Copper Straight-through)).
- The 4 building with 1 groups of 6 PC's. 
    - Everyone PC's was assigned the IP-adress 
    - PC0(2)(1) 192.168.0.19
    - PC9 192.168.0.20
    - PC5 192.168.0.21
    - PC1(2)(1) 192.168.0.22
    - PC2(2)(1) 192.168.0.23
    - PC3(2)(1) 192.168.0.24
    - all PC's was connected with Switch0(2)(1) via (Copper Straight-through)).
- The 5 building with 1 groups of 6 PC's. 
    - Everyone PC's was assigned the IP-adress 
    - PC10 192.168.0.25
    - PC0(2)(2) 192.168.0.26
    - PC1(2)(2) 192.168.0.27
    - PC2(2)(2) 192.168.0.28
    - PC3(2)(2) 192.168.0.29
    - PC4(2)(2) 192.168.0.30
    - all PC's was connected with Switch0(2)(2) via (Copper Straight-through)).
- Switch0,Switch0(2),Switch0(3),Switch0(2)(1),Switch0(2)(2) were connected with Switch1 via (Copper Cross-Over)).
- Router2(port Fa2/0 ip adress 192.168.0.31) was connected with Switch1 via (Fiber)).
-  The port of the Router2(Fa2/0) was switched on  (On)
-  Everyone PC's ,from each network ,was assigned the default gateway192.168.0.31 .
-  ![succesfull2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.2/task4.2.2/succesfull2.jpg)
