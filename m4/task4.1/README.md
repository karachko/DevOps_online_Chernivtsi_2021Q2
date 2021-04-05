# TASK 4.1 #

1. I created the new project with 4 PS and 1 HUB(all PS were connected with HUB via (Copper Straight-through)).
2. 
 - ![1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/1.jpg)
3. Everyone PC was assigned the IP-adress 
- PC0 192.168.0.1
- PC1 192.168.0.2
- PC2 192.168.0.3
- PC3 192.168.0.4
 - ![31.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/31.jpg)
 
4. I pressed the button **ADD SIMPLE PDU** . I clicked on PCO and after on PC1
 - ![33.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/33.jpg)
 - ![4.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/4.jpg)
 - The transfer of the package was successful.
5. I selected the **Simulation**, chose **Event List**. I pressed the button **Auto Capture / Play**
- The simulation of ICMP packeges' work was launched.
- ![5.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/5.jpg)
- ![51.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/51.jpg)
6. I was monitoring the packages 
- ![6.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/6.jpg)
7. I compare the information from **Simulation** and **PDU information**
- ![7.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/7.jpg)
- ![71.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/71.jpg)
8. I was deleted the IP adress from everyone PC. The transfer of the packages was failed.
- ![8.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/8.jpg)
9. I created the new project with PC0-PC5, Server,2 Hubs. HUB0 was connected wih HUB1 via (Copper Cross-over).
10 . Everyone PC was assigned the IP-adress
- PC0 192.168.0.1
- PC1 192.168.0.2
- PC2 192.168.0.3
- PC3 192.168.0.4
- PC4 192.168.0.6
- PC5 192.168.0.7
- Server 192.168.0.5
- the mask was : 255.255.255.0.
11. I checked work of network 
- ![11.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/11.jpg)
12. I created the new project with PC0-PC3, and 1 Switch. (all PS were connected with Switch via (Copper Straight-through))
13. I compared the topology(HUB-PC0-PC3) and (Switch-PC0-PC3).The switch sends an information packet to the same computer for which it is intended.When one of the computers connected to the hub sends information, it is sent to all computers on the network, and then each of them understands whether the information packet was sent to him or not. Accordingly, the addressee receives and processes this packet, and all others are simply ignored. This structure of work has many disadvantages. Not only can one computer “clog” the bandwidth of all devices connected to the hub, but also intercepting other people's packets in such conditions is not difficult.
14. I created the new project with PC0-PC7, and 2 Switches. (all PS were connected with Switch via (Copper Straight-through)).Switche0 was connected wih Switche1 via (Copper Cross-over).
15. I added neccecery ports on the Switch
- ![15.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/15.jpg)
16.  Everyone PC and Server were assigned the IP-adress
- PC0 192.168.0.1
- PC1 192.168.0.2
- PC2 192.168.0.3
- PC3 192.168.0.4
- PC4 192.168.0.5
- PC5 192.168.0.6
- PC6 192.168.0.7
- the mask was : 255.255.255.0.
17. I checked work of network 
- ![17.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/17.jpg)
18. I devided this network on two networks and conected it via Router-PT with several ports
The hubs and switch were conected via **Fiber**
19. Everyone (РС4 – РС7) was assigned the IP-adress
- PC4 192.168.1.1
- PC5 192.168.1.2
- PC6 192.168.1.3
- PC7 192.168.1.4
- the mask was : 255.255.255.0.
20. Ports of switch were switched on  (On) and  assigned the IP-adress( 192.168.0.5, and another 192.168.1.5)
- ![20.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/20.jpg)
21. Everyone PC ,from the first network (192.168.0.),was assigned  the **default gateway** 192.168.0.5 
- Everyone PC ,from the second network (192.168.1.),was assigned  the **defaultgateway** 192.168.1.5 
22.  I checked work of network 
- ![22.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/22.jpg)
- ![23.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m4/task4.1/23.jpg)
23. 
Switch and router - the difference between them:

The switch lacks a WAN port, since it only works on the local network. The router is engaged in the transfer of data between different networks, and the switch cannot do this.
The switch lacks Wi-Fi, it only switches packets on the Ethernet network.
Perhaps the lack of remote control and, accordingly, all the functions that can be configured, as well as statistics.
A switch usually has more LAN ports than a router.

