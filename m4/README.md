4. I created my own VM in the AWS cloud and connect to it
- I selected Light sail from All services
- I selected platform Linux/Unix (1.jpg)
- I downloded Default SSH key pair (LightsailDefaultKey-eu-west-2.pem)
- I pressed the button Create Instance
- I selected new Light sail instance from Instances and seected WorldPress-1
- From drop-down list I select Connect(2.jpg)
- I connected to the instance WorldPress-1(3.jpg)
5. I selected EC2 from All services
- I selected Key Pair from Network&Security and pressed Create key pair
- I entered the Name-Ec2Key and File Format ppk and pressed Create key pair
- I Opened the Amazon EC2 console
- I selected Launch instance
- I selected Amazon Linux 2 AMI(4.jpg)
- I chose Instant Type t2.micro
- I selected Auto-assign Public IP-Enable
- I selected Launch  and key pair Ec2Key
- I creted user ec2user
- I Connected to your Linux instance from Windows using PuTTY(1.1 In the setting Hostname i entered Public Ip of created instance.  1.2.In the setting SSH-Auth-Private key i selected my Ec2Key)

6. I select Elastic Block Store-Snapshots-create snapshot
- I selected resource type- Instance,instance ID-i-072d1bb432f7905d5,descriotion mysnapshot
- The screenshot had been created (6.jpg)                  
7.  I select Elastic Block Store- Volumes > Create Volume
- I entered Size 1- Gb,  and pressed Create Volume.the volume vol-01015f4bcb4c1f5e2 has been created
- I stopped my instance i-0a20fc4f992584ccd
- I selected Elastic Block Store- Volumes and rightclicked on my created volume and selected Attached volume.   Instance i-01ab1016ea4edc96e. Device- Disk_D
he message was appeared Error attaching volume: Value (Disk_D) for parameter device is invalid. Disk_D is not a valid EBS device name.
- Changed the name of device to /dev/sdf
- The volume has been created(7.jpg)
- in the terminal(EC2 Instance Connect)
 
- Format the new partition as an ext3 file system type:
- sudo /sbin/mkfs -t ext3 /dev/sdf
- I cteated the mounted point 
- sudo mkdir -p /mnt/Disk_D 
- I mounted the new partishion Disk_D
- sudo mount /dev/sdf /mnt/Disk_D
- cd /mnt/Disk_D
- touch file 1.txt

8.Delete The EC2 Instance(i selected the instance(i-0d1c10dadcd03b627) and chose Instance state-Terminate instance)


I select Elastic Block Store-Snapshots-

- right-click on the snapshot snap-0a9c23abae5a9ce74(it is the snapshot of the instance(i-0d1c10dadcd03b627) ) and chose in the menu Actions-Create Image(9.jpg). I fulfilled the field Name -NewVM, description- RestoreVM, Vitualization type-Hardware-assistent virtualization and pressed the button Create. 
The imade In the Images-AMIs had been created(10.jpg)
I pressed the Launch and created the new VM from the image
9.
- I selected Elastic Block Store- Volumes 
- I selected vol-060084c2a8de22001 with Disk_D and select detach volume
- I selected vol-060084c2a8de22001 with Disk_D and select atttach volume to the new - instance and selected the created instance
10.
I created my own VM in the AWS cloud and connect to it
- I selected Light sail from All services
- I selected platform Linux/Unix (1.jpg)
- I downloded Default SSH key pair (LightsailDefaultKey-eu-west-2.pem)
- I pressed the button Create Instance
- I selected new Light sail instance from Instances and seected WorldPress-1
- From drop-down list I select Connect(2.jpg)
- I connected to the instance WorldPress-1(3.jpg)
- On the Instances tab of the Lightsail home page, chose the SSH quick-connect icon for WorldPress-1 instance.
- After the browser-based SSH client window opens, enter the following command to retrieve the default application password:
cat $HOME/bitnami_application_password
Make note of the password displayed on the screen.
 - In a browser, go to:
http://35.178.110.82/wp-login.php
Log into your instance. 
Choose the Networking tab, then choose Create static IP.- and create statistic IP
On the Networking tab of the Lightsail home page, choose Create DNS zone. and create DNS zone
11. 
- I selected Storedge-S3- and pushed the button- Create buscket. I fullfilled fields with - Buscket name -"mybucketkarachko" and pushed the button- Create buscket
(12.jpg)
- In the menu Amazon S3 I chose Buckets and clicked on the mybucketkarachko
- To upload files in the buckets i pushed the button- Upload. I pushed the button- Add files and selected the file, pushed the button Open,pushed the button -Upload-. The file had been uploded to the bucket(14.jpg)
- To download file in mybucketkarachko, I selected 1.jpg and selected Download 
12. 
-I created the new user AWS IAM. I selected AWS management console - IAM. I clecked on user and presssed the button Add user. i fullfiled fields with(Username-AWS_Admin, Access type-Programmatic Access). I chose Attach existing policies directly- AdministratorAccess on the next page.I pushed the button Next tags-Review-Create User.I pushed the button Downloaded .csv
-I downloaded and installe AWSCLI64.msi.I launched CMD in Windows. I executed the command
aws configure. I entered Access Key Id, Secret Access Key from the credentials.csv.Default region name - us-east-1 and Default output format -json. I entered aws s3 cp "D:\2.jpg" s3://mybucketkarachko/ in CMD. The file 2.jpg had been downloaded on the server in mybucketkarachko
13. 
I review the 10-minute example and explored the possibilities of creating my own domain
and domain name for my site.
14.
I  Started with Amazon Elastic Container Service (Amazon ECS) using Fargate.
I chose container sample-app(image:httpd:2.4),presssed the button Next,selected Load Balancer type -Application Load Balancer,presssed the button Create. I pressed the button View service (17.jpg).I clicked tne EC2Co-Defau-V0B43JYXVZRL in the Load Balancing(18.jpg). I selected EC2Co-EcsEl-W62ISGHEKYA(EC2-Load Balncing-Load Balancers)(19.jpg)
and copied DNS name EC2Co-EcsEl-W62ISGHEKYA-767129557.us-east-1.elb.amazonaws.com in the browser. I opened that link(20.jpg)
15.
- I created the bucked with name-devopsnk.ua and AWS Region EU(Stockholm)(S3-Create buscket). In the S3-buckets I selected devopsnk.ua -Proreties.Under Static website hosting, I chose Edit.Under Static website hosting, I chose Enable. On the page Edit static website hosting I checked the Static website hosting to Enable. I fullfilled fields(Index document-index.html,Error document-404.html).I pushed the button Save Changes
- I chose the buscket devopsnk.ua in Amazon S3-buckets. I chose-Permision.Under Block public access (bucket settings), I choose Edit. I unchecked "Block all public access".I pushed the button Save Changes.Under Bucket Policy, I choose Edit.I copied the the bucket policy, and paste it in the Bucket policy editor.``` {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::devopsnk.ua/*"
            ]
        }
    ]
}```
I pushed the button Save Changes
- I uploded configured files(index.html, foto, style.css) and uploaded to the bucket "devopsnk.ua"
- I uploded configured 404.html and uploaded to the bucket "devopsnk.ua"
- Under Static website hosting, I chose your Bucket website endpoin thttp://devopsnk.ua.s3-website.eu-north-1.amazonaws.com/.