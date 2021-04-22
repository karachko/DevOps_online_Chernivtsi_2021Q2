1-2.  In the VirtualBox  the new virtual machine- "V1_karachko" was created with OS - Ubuntu.
- I cloned the existing VM1 by creating the VM2 . I right-clicked on the virtual machine and selected "Clone",set the name "V2_karachko", and selected- Full Clone
- On the VM's "v1_karachko"VM "v2_karachko" i configurated netwotk settings "Internal networking"
- I Configured different network modes for VM1, VM2.
     - On the VM "v1_karachko" i ecexuted command
          - cd /etc/netplan
          - sudo nano 01-network-manager-all.yaml
          - (1.jpg)  
          - ![1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.1/1.jpg)
          - sudo netplan apply 
          - (1.1.jpg)   - ![1.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.1/1.1.jpg) 
     - On the VM "v2_karachko" i ecexuted command 
          - cd /etc/netplan
          - sudo nano 01-network-manager-all.yaml
          - addresses: -10.10.10.2/24
          - (2.jpg)  - ![2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.1/2.jpg)
          - sudo netplan apply 
          - (2.1.jpg)  - ![2.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.1/2.1.jpg)
     - I executed ping on the VM "v2_karachko" to VM "v1_karachko" 
     - The execution of the ping command was successful.
- I added the network adapter on the VM1 (NAT interface) 
- On the VM1 I opened /etc/sysctl.conf and removed the symbol # from the record net.ipv4.ip_forward=1 and saved it
    - (4.1.jpg) - ![4.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.1/4.1.jpg)
- I added on VM1 the adapter - Bridge
    - I recived the new interface 
    - (4.2.jpg) - ![4.2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.1/4.2.jpg)
-I connected to VM1 by using MobaXterm.
     -(4.3.jpg) - ![4.3.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.1/4.3.jpg)
- I configured iptables on VM1
    - sudo iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE
    - sudo /sbin/iptables-save
3. I checked the route from VM2 to Host.
    -(5.jpg) - ![5.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.1/5.jpg)
4. I checked the access to the Internet on VM2(ping 8.8.8.8)
    - (6.1.jpg) - ![6.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.1/6.jpg)
5. I determined, which resource has an IP address 8.8.8.8
    - (7.jpg) - ![7.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.1/7.jpg)
6. I determined, which IP address belongs to resource epam.com.
    - (8.jpg) - ![8.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.1/8.jpg)
7. I determine the default gateway for your HOST and display routing table  
    - (9.jpg)   - ![9.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.1/9.jpg)
8. I traced the route to google.com.
    - (10.jpg) - ![10.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.1/10.jpg)
