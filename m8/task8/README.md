## Part1 ##
- **Coping a file(index.html is created by the system) from Jenkins to the web-server** 

1.I installed EC2-Jenkins and Jenkins
I selected EC2 from All services on AWS
- I selected Ubuntu Server 18.04 LTS
- I chose Instant Type t2.micro
- I pressed the button Next
- I pressed the button Next
- I pressed the button Add Tag
- I filled out the fields (key - name, value - jenkins)
- I pressed the button Next
- I selected Add Rule and filled out the fields (Type - Custom TCP, Protocol - TCP, Port Range -8080,Source -Anywere 0.0.0.0/0, ::/0)
- I pressed the button Launch
- I selected Create key pair
- I entered the KeyJenkins and pressed the button Download Key Pair KeyJenkins.pem.
2.I installed Jenkins on EC2-Jenkins
- wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
- sudo nano /etc/apt/sources.list
- #Add next string after last row in the editing file
- deb https://pkg.jenkins.io/debian-stable binary/
- #And save changes
- sudo apt-get update
- java -version
- sudo apt-get install openjdk-8-jdk
- sudo apt-get install jenkins
- service jenkins status


- sudo systemctl start jenkins
- sudo systemctl status jenkins
- sudo ufw allow 8080
- sudo cat /var/lib/jenkins/secrets/initialAdminPassword

- I lanched the Jenkins by opening http://3.89.137.52:8080/ in the browser
- I enetered the Administraion password (sudo cat /var/lib/jenkins/secrets/initialAdminPassword)

- I enetered the Administraion password
- I enetered the student login 

3. I selected EC2-Apache from All services
- I selected Ubuntu Server 18.04 LTS 
- I chose Instant Type t2.micro
- I pressed the button Next
- I pressed the button Next
- I pressed the button Add Tag
- I filled out the fields (key - name, value - Apache)
- I pressed the button Next
- I selected Create key pair
- I entered the Name-KeyApache and pressed the button Download Key Pair KeyApache.pem. 
4. I installed apache on EC2-Apache (http://34.229.156.25/)
- sudo apt update
- sudo apt install apache2
- sudo ufw app list
- sudo ufw status
- sudo systemctl status apache2

5. 
- I created user student on the Jenkins
- sudo useradd student
- sudo passwd student
- sudo mkdir /home/student
- sudo chown student:student /home/student

- I created user student  on the Apache
- sudo useradd student
- sudo passwd student
- sudo mkdir /home/student
- sudo chown student:student /home/student
- sudo chgrp -R student /var/www
- sudo chmod -R g+rw /var/www

6. 
- On the Jenkins sever
- I executed (su - student)
- I created the pair of keys with (ssh-keygen). In the folder .ssh the keys(id_rsa and id_rsa.pub) were cteated.

- On the Apache Server I installed ssh (sudo apt-get install ssh)
- sudo nano /etc/ssh/sshd_config (AllowUsers student, PasswordAuthentication yes , PubkeyAuthentication yes)
- sudo systemctl restart sshd

- On the Jenkins sever
- I copied public key to /home/student/.ssh/authorized_keys using the command 
ssh-copy-id student@34.229.156.25
-  (ssh-copy.jpg) 
-  ![ssh-copy.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m8/task8/ssh-copy.jpg)

- On the Jenkins sever(I copied the keys to /var/lib/jenkins/.ssh/)
- cd  /var/lib/jenkins/
- sudo mkdir .ssh
- sudo cp /home/student/.ssh/id_rsa  /var/lib/jenkins/.ssh/
- sudo cp /home/student/.ssh/id_rsa.pub  /var/lib/jenkins/.ssh/
- sudo chown -R jenkins:jenkins /var/lib/jenkins/.ssh

7.

I launched Jenkins http://http://3.89.137.52/:8080 in the browser

I cteated the job1 with Build(Execute shell) and executed it
```
cat <<EOF > index.html
<!doctype html>
<html>

  <head>
  <link rel="stylesheet" href="style.css">
    <title>EPAM_DevOps_online_Spring_2021</title>
  </head>
  <body>
  
     <strong><h1><p>EPAM_DevOps_online_Spring_2021</p></h1>
    
  
<h2><p>The list of Amazon services</p></h2>
  <ul>
  <li>Identity and Access Management (IAM)</li>
  <li>Amazon Lightsail</li>
  <li> Amazon EC2</li>
  <li> Amazon S3</li>
  <li> Amazon Elastic Container Service (Amazon ECS)</li>
  <li> Amazon Route 53</li>
</ul> </p>

  <h2><p>The list with links of completed labs</p></h2> 
  <ul>
  <li><a href="https://aws.amazon.com/ru/getting-started/hands-on/launch-a-virtual-machine/">Launch a Linux Virtual Machine with Amazon Lightsail</a></li>
  <li><a href="https://aws.amazon.com/ru/getting-started/hands-on/backup-files-to-amazon-s3/">Store and Retrieve a File
with Amazon S3</a></li>
  <li> <a href="https://aws.amazon.com/ru/getting-started/hands-on/backup-to-s3-cli/?nc1=h_ls">Batch upload files to the cloud
to Amazon S3 using the AWS CLI </a></li>
  <li> <a href="https://aws.amazon.com/getting-started/hands-on/get-a-domain/?nc1=h_ls">Register a Domain Name
with Amazon Route 53 </a></li>
<li> <a href="https://aws.amazon.com/getting-started/hands-on/deploy-docker-containers/?nc1=h_ls">Deploy Docker Containers
on Amazon Elastic Container Service (Amazon ECS)</a></li>
<li> <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html">Configuring a static website on Amazon S3</a></li>
</ul>
  </body>
  
</html>
EOF
```
- The version of build was succusseful

I changed job1 by adding at the end 
scp -v -o StrictHostKeyChecking=no index.html student@34.229.156.25:/var/www/html
(successjob.jpg)
  - ![successjob.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m8/task8/successjob.jpg)



## Part2 ##
-**Coping a file(index.html is created by the system) from Jenkins to the web-server by using plugin - Publish over SSH**

1.I installed “Publish Over SSH" plugin in Jenkins
- On the server Jenkins I executed command (cat id_rsa)

- I opened the settings http://54.147.14.191:8080/configure
- In the section **Publish over SSH** I entered private key from the outputing of command (cat id_rsa)

- I selected **SSH Servers**- **Add**(Name-Apache,Hostname-3.94.100.195, Username-student, remote directory /var/www/html) 
- I pushed the button **Test Configuration** - Success and Save.
(publishoversshsuccess.jpg)
- ![publishoversshsuccess.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m8/task8/publishoversshsuccess.jpg)

- I created the job2 with Build(Execute shell) and executed it
- Сборка-Выполнить команду shell
- 
```
cat <<EOF > index.html
<!doctype html>
<html>

  <head>
  <link rel="stylesheet" href="style.css">
    <title>EPAM_DevOps_online_Spring_2021</title>
  </head>
  <body>
  
     <strong><h1><p>EPAM_DevOps_online_Spring_2021</p></h1>
    
  
<h2><p>The list of Amazon services</p></h2>
  <ul>
  <li>Identity and Access Management (IAM)</li>
  <li>Amazon Lightsail</li>
  <li> Amazon EC2</li>
  <li> Amazon S3</li>
  <li> Amazon Elastic Container Service (Amazon ECS)</li>
  <li> Amazon Route 53</li>
</ul> </p>

  <h2><p>The list with links of completed labs</p></h2> 
  <ul>
  <li><a href="https://aws.amazon.com/ru/getting-started/hands-on/launch-a-virtual-machine/">Launch a Linux Virtual Machine with Amazon Lightsail</a></li>
  <li><a href="https://aws.amazon.com/ru/getting-started/hands-on/backup-files-to-amazon-s3/">Store and Retrieve a File
with Amazon S3</a></li>
  <li> <a href="https://aws.amazon.com/ru/getting-started/hands-on/backup-to-s3-cli/?nc1=h_ls">Batch upload files to the cloud
to Amazon S3 using the AWS CLI </a></li>
  <li> <a href="https://aws.amazon.com/getting-started/hands-on/get-a-domain/?nc1=h_ls">Register a Domain Name
with Amazon Route 53 </a></li>
<li> <a href="https://aws.amazon.com/getting-started/hands-on/deploy-docker-containers/?nc1=h_ls">Deploy Docker Containers
on Amazon Elastic Container Service (Amazon ECS)</a></li>
<li> <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html">Configuring a static website on Amazon S3</a></li>
</ul>
  </body>
  
</html>
EOF
```
- Послесборочные операции-Send build artifacts over SSH-SSH Server(Name-Apache, Source files -*) Save
- I executed the job2
(posrez1.jpg)
- ![posrez1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m8/task8/posrez1.jpg)

(htmlresult.jpg)
- ![htmlresult.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m8/task8/htmlresult.jpg)

## Part3 ##
- **Coping a file(index.html ) from Git to the GitHub**

- On the VM with Ubuntu or on the machine with ubuntu for windows
- sudo useradd student
- sudo passwd student
- sudo mkdir /home/student
- sudo mkdir /home/student/.ssh
- sudo chown student:student /home/student
- sudo usermod -aG sudo student
- su - student
- ssh-keygen

- On the Github-Setting-SSH and GPG keys
- SSH keys-NeWSSHkey
- Title-GitPublicKey
- Key (cat id_rsa.pub from server with git)
- Add ssh key

- On the VM with Ubuntu or on the machine with ubuntu for windows
ssh -T git@github.com
The message was displayed 

```
The authenticity of host 'github.com (140.82.121.3)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com,140.82.121.3' (RSA) to the list of known hosts.
Hi karachko! You've successfully authenticated, but GitHub does not provide shell access.
```

- On the GitHub https://github.com/karachko/laba
- In the branch laba I selected Code-Clone-SSH -  git@github.com:karachko/laba.git

- On the VM with Ubuntu or on the machine with ubuntu for windows
- cd /home/student
- git clone git@github.com:karachko/laba.git
- cd laba
- ls -la
- I changed index.html On the VM with Ubuntu or on the machine with ubuntu for windows (<strong><h1><p>The html has been changed</p></h1>)
- git config --global user.email "natakarachko@gmail.com"
- git config --global user.name "karachko"
- git add index.html
- git commit -m "html has been changed"
- git push

(htmlchanged.jpg)
- ![htmlchanged.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m8/task8/htmlchanged.jpg)


## Part4 ##
- **Coping a file(index.html ) from GitHub to Jenkins. from Jenkins to webserver**
- On the Jenkins sever
- (jenkins keys)
- cat id_rsa
- I cteated the job3 with Управление исходным кодом - Git 
- Repository URL - git@github.com:karachko/laba.git
- Credentials -Add 
- Kind-SSH Username with private key
- ID-github-ssh
- Description-github-ssh
- Username-karachko
- Private Key-Enter directly-Key(cat id_rsa from Jenkins)

- On the Gihub Setting-SSH and GPG keys - New SSH keys
- (jenkins keys)
- cat id_rsa.pub

- I created the job3-Управление исходным кодом-Branch Specifier (blank for 'any')

- Сборка-выполнить команду shell
- scp -v -o StrictHostKeyChecking=no index.html student@3.94.100.195:/var/www/html

(hasbeenchanged.jpg)
- ![hasbeenchanged.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m8/task8/hasbeenchanged.jpg)

## Part5 ##
- **pipeline with Jenkins**
- I installed the plagin Pipeline
- I selected (Создать Item. Name-Pipeline and the type of task Pipeline)
- I selected (Pipeline-Definition-Pipeline script)

```
pipeline {
    agent any

    stages {
        stage('Сборка') {
            steps {
                echo 'Выполняем команды для сборки'
                
            }
        }
        stage('Тестирование') {
            steps {
                echo 'Тестируем нашу сборку'
            }
        }
        stage('Развертывание') {
            steps {
                echo 'Переносим код в рабочую среду или создаем артефакт'
                build job: 'job1'
            }
        }
    }
}
```

- I selected (Use Groovy Sandbox)
- I pushed Save
- I pushed (Build now)
(pipeline1.jpg)
- ![pipeline1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m8/task8/pipeline1.jpg)

## Part6 ##
- **Maven with Jenkins**
- On the Jenkins sever
- sudo cp /home/ubuntu/pom.xml /var/lib/jenkins/workspace/testmaven


- I opened http://50.19.133.58:8080/configureTools/
- I selected Maven-Add Maven
- name maven 3.6.3
- Install automatically
- Install from Apache 3.6.3

- On the https://github.com/karachko/laba I created files(App.java,AppTest.java,pom.xml)

- App.java

```
package com.mycompany.app;

public class App {
    public static void main(String[] argv) {
        System.out.println("Hello world");
    }
}
```

- AppTest.java
 
```
package com.mycompany.app;

import static org.junit.Assert.assertTrue;
import org.junit.Test;


/**
 * Unit test for simple App.
 */
public class AppTest
{
    /**
     * Rigourous Test :-)
     */
    public void shouldAnswerWithTrue()
    {
        assertTrue( true );
    }
}
```

- pom.xml

```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
 
  <groupId>com.mycompany.app</groupId>
  <artifactId>my-app</artifactId>
  <version>1.0-SNAPSHOT</version>
 
  <properties>
    <maven.compiler.source>1.7</maven.compiler.source>
    <maven.compiler.target>1.7</maven.compiler.target>
  </properties>
 
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.12</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
</project>
```
- On the Jenkins sever
- I create new job -testmaven
- GitHub project-Project url-git@github.com:karachko/laba.git/
- Управление исходным кодом-Git(Repository- URLgit@github.com:karachko/laba.git,Credentials-karachko(github-ssh))
- Branch Specifier-blank
- Среда сборки-Delete workspace before build starts
- Сборка(Версия Maven-maven 3.6.3, цели-clean test)

- Build test maven

(maven.jpg)
- ![maven.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m8/task8/maven.jpg)