1. I used already created internal-network for three VMs (VM1-VM3). VM1 has NAT and internal,
VM2, VM3 – internal only interfaces
2. I installed and configured DHCP server on VM1. 

2.1. I installed isc-dhcp-server
- sudo apt-get update
- sudo apt-get upgrade -y 
- sudo apt-get install isc-dhcp-server
- On the VM "v1_karachko" i ecexuted command
- cd /etc/netplan
- sudo nano 01-network-manager-all.yaml
- (1.jpg) - ![1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.2/1.jpg) 
- sudo netplan apply 
- (1.1.jpg) - ![1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.2/1.1.jpg) 
- sudo nano /etc/default/isc-dhcp-server
- I wrote in the isc-dhcp-server (INTERFACESv4="enp0s8")
- sudo nano /etc/dhcp/dhcpd.conf
- I commented the strings default-lease-time and max-lease-time
- I wrote in the dhcpd.conf the following lines
- (3.jpg) - ![3.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.2/3.jpg) 
- I executed systemctl restart isc-dhcp-server.service
- I executed systemctl status isc-dhcp-server.service
- (4.jpg)  - ![4.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.2/4.jpg) 
3.        
- On the VM "v2_karachko" i ecexuted command
- cd /etc/netplan
- sudo nano 01-network-manager-all.yaml
- (2.jpg)  - ![2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.2/2.jpg)
- sudo netplan apply 
- I executed ip a. The VM2 get the ip 10.10.10.10
 - (5.jpg)  - ![5.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.2/5.jpg)
- On the VM "v3_karachko" i ecexuted command
- cd /etc/netplan
- sudo nano 01-network-manager-all.yaml
- (6.jpg)  - ![6.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.2/6.jpg)
- sudo netplan apply 
- I executed ip a. The VM3 get the ip 10.10.10.11
- (7.jpg)  - ![7.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.2/7.jpg)

4.

4.1. I installed dnsmasq DHCP server
- sudo systemctl stop systemd-resolved
- sudo apt-get update
- sudo apt-get install  dnsmasq
- I executed systemctl status  dnsmasq
- I wrote  (interface=enp0s8) in the file /etc/dnsmasq.conf
- I wrote (dhcp-range=10.10.10.10,10.10.10.20,12h) in the file /etc/dnsmasq.conf
- I wrote (nameserver 127.0.0.1) in the file /etc/resolv.conf
- I wrote (prepend domain-name-servers 127.0.0.1;) in the file /etc/dhcp/dhclient.conf
- On the VM "v2_karachko"- I executed ip a. The VM2 get the ip 10.10.10.10
- (4.1.jpg) - ![4.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.2/4.1.jpg)
- On the VM "v3_karachko"- I executed ip a. The VM2 get the ip 10.10.10.11
- (4.2.jpg) - ![4.2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.2/4.2.jpg)

4.2. I confugured dnsmasq DNS server
- I wrote  (nameserver 10.10.10.1, nameserver 127.0.0.1, nameserver 8.8.8.8) in the file /etc/resolv.conf
- I wrote  (port=53) in the file /etc/dnsmasq.conf
- I wrote  (domain-needed) in the file /etc/dnsmasq.conf
- I wrote  (bogus-priv) in the file /etc/dnsmasq.conf
- I wrote  (listen-address=127.0.0.1,10.10.10.1) in the file /etc/dnsmasq.conf
- I wrote  (expand-hosts) in the file /etc/dnsmasq.conf
- I wrote  (domain=kifarunix-demo.com) in the file /etc/dnsmasq.conf
- I wrote  (cache-size=1000) in the file /etc/dnsmasq.conf    
- I wrote  (10.10.10.1  kifarunix-demo.com) in the file /etc/hosts
- I wrote  (10.10.10.11) in the file /etc/hosts
- I executed (dnsmasq --test) in CLI. The answer was "dnsmasq: syntax check OK."
- I executed (netstat -alnp | grep -i :53) in CLI.
- I opened the port 53 (sudo ufw allow from 10.10.10.0/24 to any port 53 proto udp)
- On the VM "v3_karachko"- I executed (ping kifarunix-demo.com) and  (nslookup kifarunix-demo.com)      
- (4.2.2.jpg) - ![4.2.2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.2/4.2.2.jpg)
- On the VM "v2_karachko"- I executed (ping kifarunix-demo.com) and  (nslookup kifarunix-demo.com)      
- (4.2.3.jpg) - ![4.2.3.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m6/task6.2/4.2.3.jpg)
- https://infoit.com.ua/linux/ubuntu/nastrojka-lokalnyx-dns-server-s-pomoshhyu-dnsmasq-v-ubuntu-20-04/
- https://www.alibabacloud.com/blog/how-to-setup-dns-server-using-bind9-on-ubuntu-16-04_594469
