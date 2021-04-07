# TASK 4.3 #

1. I created the network, that included 
    - The 5 PC's. 
        - Everyone PC's was assigned the IP-address 
        - PC0 192.168.0.1
        - PC1 192.168.0.2
        - PC2 192.168.0.3
        - PC3 192.168.0.4
        - PC4 192.168.0.5
     - Server0 - ip address 192.168.0.6
     - all PC's and Server0 were connected with Switch0 via (Copper Straight-through)).
     - Switch0(port Eth8/1) was connected with Router0(port Fa 1/0, ip address 192.168.0.7 ) via (Copper Straight-through).
     - Server1 - ip address 192.168.1.1
     - Server1(port Fa0) was connected with Router0(port Fa 0/0, ip address 192.168.1.2 ) via (Copper Cross-over).
     - Ports of the Router(Fa1/0,Fa0/0) were switched on (On)
   ![4.3.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.3/4.3.1.jpg)
   
2.The secret password was assigned on the Router0.
-  ![enable-secret.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.3/enable-secret.jpg)

3. I configured RIP protocol on the Router0.
-  ![rip.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.3/rip.jpg)
4. Everyone PC's and Servers ,from each network ,was assigned the default gateway.
 
5. I checked the work of the network
 - ![succeseful.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.3/succeseful.jpg)
 
