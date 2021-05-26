# PART1 #
1.I installed EC2-AnsibleMaster
I selected EC2 from All services on AWS
- I selected Ubuntu Server 18.04 LTS
- I chose Instant Type t2.micro
- I pressed the button Next
- I pressed the button Next
- I pressed the button Add Tag
- I filled out the fields (key - name, value - AnsibleMaster)
- I pressed the button Next
- I selected Add Rule and filled out the fields (Type - SSH, Protocol - TCP, Port Range -22,Source -Anywere 0.0.0.0/0, ::/0)
- I pressed the button Launch
- I selected Create key pair
- I entered the AnsibleMaster and pressed the button Download Key AnsibleMaster.pem.
- sudo usermod -aG sudo ubuntu
2. 
- I copied the AnsibleMaster.pem from local machine to EC2-AnsibleMaster,using Moba Xterm, in the folder /home/ubuntu/.ssh
- I copied the AnsibleClient1.pem from local machine to EC2-AnsibleMaster,using Moba Xterm, in the folder /home/ubuntu/.ssh

3.I installed EC2-AnsibleClient1
- I selected EC2 from All services on AWS
- I selected Ubuntu Server 18.04 LTS
- I chose Instant Type t2.micro
- I pressed the button Next
- I pressed the button Next
- I pressed the button Add Tag
- I filled out the fields (key - name, value - AnsibleClient1)
- I pressed the button Next
- I selected Add Rule and filled out the fields (Type - SSH, Protocol - TCP, Port Range -22,Source -Anywere 0.0.0.0/0, ::/0)
- I pressed the button Launch
- I selected Create key pair
- I entered the AnsibleClient1 and pressed the button Download Key AnsibleClient1.pem.
- sudo usermod -aG sudo ubuntu

4. On the EC2-AnsibleMaster

- sudo chmod 400 /home/ubuntu/.ssh/AnsibleClient1.pem
- ssh -i /home/ubuntu/.ssh/AnsibleClient1.pem ubuntu@52.54.144.164


5. On the EC2-AnsibleMaster
- I installed Ansible
- sudo apt-add-repository ppa:ansible/ansible
- sudo apt update
- sudo apt install ansible
- ansible --version

- I installed Python
- sudo apt install python-pip
- sudo pip install ansible
- ansible --version
7.  On the EC2-AnsibleMaster
- mkdir ansible
- cd ansible
- nano hosts.txt
```
[staging_servers]
linux1 ansible_host=52.54.144.164 ansible_user=ubuntu ansible_ssh_private_key_f$
```
- ansible -i hosts.txt all  -m ping
(pingsuccess.jpg)
-  ![pingsuccess.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m10/task10/pingsuccess.jpg)

8. I installed EC2-AnsibleClient2
- I selected EC2 from All services on AWS
- I selected Amazon Linux 2 AMI (HVM)- Free tier eligible
- I chose Instant Type t2.micro
- I pressed the button Next
- I pressed the button Next
- I pressed the button Add Tag
- I filled out the fields (key - name, value - AnsibleClient2)
- I pressed the button Next
- I selected Add Rule and filled out the fields (Type - SSH, Protocol - TCP, Port Range -22,Source -Anywere 0.0.0.0/0, ::/0)
- I pressed the button Launch
- I selected Create key pair
- I entered the AnsibleClient2key and pressed the button Download Key AnsibleClient2key.pem.

- I copied the AnsibleClient2key.pem from local machine to EC2-AnsibleMaster,using Moba Xterm, in the folder /home/ubuntu/.ssh
- sudo chmod 400 /home/ubuntu/.ssh/AnsibleClient2key.pem
- ssh -i /home/ubuntu/.ssh/AnsibleClient2key.pem ec2-user@34.227.61.238
9.
- On the EC2-AnsibleMaster
- nano hosts.txt
-
```
[staging_servers]
linux1 ansible_host=52.54.144.164 ansible_user=ubuntu
ansible_ssh_private_key_file=/home/ubuntu/.ssh/AnsibleClient1.pem
[production]
linux2 ansible_host=34.227.61.238 ansible_user=ec2-user
ansible_ssh_private_key_file=/home/ubuntu/.ssh/AnsibleClient2key.pem

```
-
- ansible -i hosts.txt all  -m ping
(pingsuccess1.jpg)

-  !pingsuccess.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m10/task10/pingsuccess.jpg)
10. On the EC2-AnsibleMaster
- nano ansible.cfg

```
[defaults]
host_key_checking = false
inventory         = ./hosts.txt

```
- ansible all -m ping

(pingsuccess2.jpg)

11. I installed EC2-AnsibleClient3
- I selected EC2 from All services on AWS
- I selected Amazon Linux 2 AMI (HVM)- Free tier eligible
- I chose Instant Type t2.micro
- I pressed the button Next
- I pressed the button Next
- I pressed the button Add Tag
- I filled out the fields (key - name, value - AnsibleClient2)
- I pressed the button Next
- I selected Add Rule and filled out the fields (Type - SSH, Protocol - TCP, Port Range -22,Source -Anywere 0.0.0.0/0, ::/0)
- I pressed the button Launch
- I selected Create key pair
- I entered the AnsibleClient3key and pressed the button Download Key AnsibleClient3key.pem.

- I copied the AnsibleClient3key.pem from local machine to EC2-AnsibleMaster,using Moba Xterm, in the folder /home/ubuntu/.ssh
- sudo chmod 400 /home/ubuntu/.ssh/AnsibleClient3key.pem
- ssh -i /home/ubuntu/.ssh/AnsibleClient3key.pem ec2-user@3.89.209.24

12. On the EC2-AnsibleMaster
- nano hosts.txt

```
[staging_servers]
linux1 ansible_host=52.54.144.164 ansible_user=ubuntu
ansible_ssh_private_key_file=/home/ubuntu/.ssh/AnsibleClient1.pem

[test]
linux3 ansible_host=3.89.209.24 ansible_user=ec2-user
ansible_ssh_private_key_file=/home/ubuntu/.ssh/AnsibleClient3key.pem

[production]
linux2 ansible_host=34.227.61.238 ansible_user=ec2-user
ansible_ssh_private_key_file=/home/ubuntu/.ssh/AnsibleClient2key.pem

```

- ansible all -m ping
- (pingsuccess3.jpg)

13. On the EC2-AnsibleMaster
- ansible-inventory --list
- (inventorylist.jpg)

- ansible-inventory --graph

- ansible all -m shell -a "uptime"
- (uptime.jpg)

- ansible all -m shell -a "ls /home"

- echo HelloWorld! > hello.txt
-  ansible all -m copy -a "src=hello.txt dest=/home" -b
- (hello.jpg)

- ansible all -m shell -a "ls -la /home"
- (helloonclients.jpg)

- ansible all -m file -a "path=/home/hello.txt state=absent" -b
- (absenthello.jpg)

- nano hosts.txt

```
[staging_servers]
linux1 ansible_host=52.54.144.164 ansible_user=ubuntu
ansible_ssh_private_key_file=/home/ubuntu/.ssh/AnsibleClient1.pem

[test]
linux3 ansible_host=3.89.209.24
ansible_ssh_private_key_file=/home/ubuntu/.ssh/AnsibleClient3key.pem

[production]
linux2 ansible_host=34.227.61.238
ansible_ssh_private_key_file=/home/ubuntu/.ssh/AnsibleClient2key.pem

[test_prod:children]
test
production

[test_prod:vars]
ansible_user=ec2-user

```
ansible all -m yum -a "name=httpd state=latest" -b
ansible all -m apt -a "name=apache2 state=latest" -b
- ansible test_prod -m service -a "name=httpd state=started enabled=yes" -b
- (work1.jpg)
- (work2.jpg)

- ansible production -m yum -a "name=httpd state=removed" -b

# PART2 #
1.Task: Test connection to all servers, owned by your organization.
Assumed, that you have credentials to do this action 
- playbook1.yml
-
```
---
- name: Connection Testing
  hosts: all
  become: yes
  
  tasks:
  
  - name: Ping servers
    ping:

```
- ansible-playbook playbook1.yml

- (playbook1.jpg)

2. Task: Install Apache Web Server on all servers, owned by your organization.
Also needed to start Apache Web Server and enable it during boot
(Linux1- with ubuntu, (linux 2 and linux 3)- with amazon linux)
- playbook2.yml
-
```
---
- name: Install Apache Web Server on AMI Linux
  hosts: all
  become: yes

  tasks:
  - name: Install Apache Web Server
    yum:  name=httpd state=latest

  - name: Start Apache and enable it during boot
    service: name=httpd state=started enabled=yes

```
- ansible-playbook playbook2.yml

- (playbook2.jpg)

3a. Task: Install Apache Web Server on all servers, owned by your organization.
Also needed to start Apache Web Server and enable it during boot.
Also needed to change default index.html

- nano index.html
- 
```
<html>
<header><title>Be smart</title></header>
<body>
Hello world of DevOps!
</body>
</html>
```
- playbook3a.yml
-
```

---
- name: Install Apache Web Server on AMI Linux. Upload web page example
  hosts: all
  become: yes
  
  
  vars:
    source_file: index.html
    destin_file: /var/www/html
    
    
  tasks:
  - name: Install Apache Web Server
    yum:  name=httpd state=latest

  - name: Copy index.html to target server
    copy: src={{ source_file }} dest={{ destin_file }} mode=0555
    
  - name: Start Apache and enable it during boot
    service: name=httpd state=started enabled=yes

```
- ansible-playbook playbook3a.yml

- (playbook3a.jpg)

3b.

- playbook3b.yml
-
```
---
- name: Install Apache Web Server on AMI Linux. Upload web page example
  hosts: all
  become: yes
  
  
  vars:
    source_file: index.html
    destin_file: /var/www/html
    
    
  tasks:
  - name: Install Apache Web Server
    yum:  name=httpd state=latest

  - name: Copy index.html to target server
    copy: src={{ source_file }} dest={{ destin_file }} mode=0555
    notify: Restart Apache
    
  - name: Start Apache and enable it during boot
    service: name=httpd state=started enabled=yes
    
  handlers:
  - name: Restart Apache
    service: name=httpd state=restarted

```
- ansible-playbook playbook3b.yml

- (playbook3b.jpg)

- ansible all -m yum -a "name=httpd state=removed" -b

3c. Task: Install Apache Web Server on all servers, owned by your organization.
Also needed to start Apache Web Server and enable it during boot.
Also needed to change default index.html. Servers are on different Linux-based OS


- playbook3c.yml
-
```
---
- name: Install Apache Web Server on AMI Linux. Upload web page example
  hosts: all
  become: yes


  vars:
    source_file: index.html
    destin_file: /var/www/html


  tasks:

  - name: Check Linux distro
    debug: var=ansible_os_family

  - name: Install Apache Web Server on RedHat Family
    yum:  name=httpd state=latest
    when: ansible_os_family == "RedHat"

  - name: Install Apache Web Server on Debian Family
    apt:  update_cache=yes name=apache2 state=latest
    when: ansible_os_family == "Debian"

  - name: Copy index.html to target server
    copy: src={{ source_file }} dest={{ destin_file }} mode=0555
    #notify: Restart Apache

  - name: Start Apache and enable it during boot
    service: name=httpd state=started enabled=yes
    when: ansible_os_family == "RedHat"

  - name: Start Apache and enable it during boot
    service: name=apache2 state=started enabled=yes
    when: ansible_os_family == "Debian"

  handlers:
  - name: Restart Apache
    service: name=httpd state=restarted
```
- ansible-playbook playbook3c.yml

- (playbook3c.jpg)

5. Task: Install Apache Web Server on all servers, owned by your organization.
Also needed to start Apache Web Server and enable it during boot.
Also needed to change default index.html. Servers are on different Linux-based OS
- playbook5.yml
-
```
---
---
- name: Install Apache Web Server on AMI Linux. Upload web page example
  hosts: all
  become: yes


  vars:
    source_dir: /home/ubuntu/ansible
    destin_dir: /var/www/html


  tasks:

  - name: Check Linux distro
    debug: var=ansible_os_family

  - block: # For RedHat

    - name: Install Apache Web Server on RedHat Family
      yum:  name=httpd state=latest

    - name: Start Apache and enable it during boot
      service: name=httpd state=started enabled=yes

    when: ansible_os_family == "RedHat"

  - block: #For Debian

    - name: Install Apache Web Server on Debian Family
      apt:  update_cache=yes name=apache2 state=latest

    - name: Start Apache and enable it during boot
      service: name=apache2 state=started enabled=yes

    when: ansible_os_family == "Debian"


  - name: Copy dir "MyWebServer" to target server
    copy: src={{ source_dir }}/{{ item }} dest={{ destin_dir }} mode=0555
    loop:
     - "index.html"
    notify:
     - Restart Apache RedHat
     - Restart Apache Debian

  handlers:
  - name: Restart Apache RedHat
    service: name=httpd state=restarted
    when: ansible_os_family == "RedHat"

  - name: Restart Apache Debian
    service: name=apache2 state=restarted
    when: ansible_os_family == "Debian"

```
- ansible-playbook playbook5.yml

- (playbook5.jpg)
6. Task: Customize WebPage on remote servers using
template and jinja

-index.j2
```
<html>
<header><title>Be smart</title></header>
<body>
Hello world of DevOps!
<br>Server Host Name is {{ ansible_hostname }}<br>
<br>Linux distro is {{ ansible_os_family }}<br>
<br>Host IP Address is {{ ansible_default_ipv4.address }}<br>
</body>
</html>

```

- playbook6.yml
-
```

---
- name: Install Apache Web Server on AMI Linux. Upload web page example
  hosts: all
  become: yes


  vars:
    source_dir: /home/ubuntu/ansible
    destin_dir: /var/www/html


  tasks:

  - name: Check Linux distro
    debug: var=ansible_os_family

  - block: # For RedHat

    - name: Install Apache Web Server on RedHat Family
      yum:  name=httpd state=latest

    - name: Start Apache and enable it during boot
      service: name=httpd state=started enabled=yes

    when: ansible_os_family == "RedHat"

  - block: #For Debian

    - name: Install Apache Web Server on Debian Family
      apt:  update_cache=yes name=apache2 state=latest

    - name: Start Apache and enable it during boot
      service: name=apache2 state=started enabled=yes

    when: ansible_os_family == "Debian"


  - name: Generate index.html using template
    template: src={{ source_dir }}/index.j2 dest={{ destin_dir }}/index.html  m$
    notify:
        - Restart Apache RedHat
        - Restart Apache Debian

    
  handlers:
  - name: Restart Apache RedHat
    service: name=httpd state=restarted
    when: ansible_os_family == "RedHat"

  - name: Restart Apache Debian
    service: name=apache2 state=restarted
    when: ansible_os_family == "Debian"

```
- ansible-playbook playbook6.yml
- (playbook6.jpg)
