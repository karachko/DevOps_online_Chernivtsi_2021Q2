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

8.I select Elastic Block Store-Snapshots-
- right-click on the snapshot 
- select Create volume
- The volume vol-0e8fa493fbf15961b had been created
- Attached the new volume to the instance
(8.jpg)
- Restarted the instance
9.
- I selected Elastic Block Store- Volumes 
- I selected vol-060084c2a8de22001 with Disk_D and select detach volume
- I selected vol-060084c2a8de22001 with Disk_D and select atttach volume to the new - instance and selected the created instance






 



