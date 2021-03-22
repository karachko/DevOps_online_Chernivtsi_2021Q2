#TASK 2.1#
##PART 1. HYPERVISORS##

**The most popular hypervisors for infrastructure** virtualization are:
 - VMware vSphere
 - Microsoft Hyper-V
 - Oracle VM Server
 - Red Hat KVM
 - Citrix XenServer
**The main differences of the most popular hypervisors**
There are two types of hypervisor:
 - **A bare-metal hypervisor (Type 1)**(VMware v Sphere with ESX, KVM, Microsoft Hyper-V,Oracle VM) is a layer of software we install directly on top of a physical server and its underlying hardware.
There is no software or any operating system in between, hence the name bare-metal hypervisor. A Type 1 hypervisor is proven in providing excellent performance and stability since it does not run inside Windows or any other operating system.
- **Type 2 Hypervisor**(Oracle VM VirtualBox,VMware Workstation Pro, Parallels Desktop) runs inside of an operating system of a physical host machine. This is why we call type 2 hypervisors – hosted hypervisors. As opposed to type 1 hypervisors that run directly on the hardware, hosted hypervisors have one software layer underneath.
 In this case we have:
A physical machine.
An operating system installed on the hardware (Windows, Linux, macOS).
A type 2 hypervisor software within that operating system.
The actual instances of guest virtual machines.

##PART 2. WORK WITH VIRTUALBOX##
1. -1.2. From the official, VirtualBox was downloaded the latest stable version. The latest stable version of Ubuntu Desktop was downloaded too.  The VirtualBox and Ubuntu Desktop were installed on the computer with Windows 10
1.3 The button "Додати " was pressed.  The "Name"-"V1_karachko", "Тип"-"Linux", "Версія"- "Ubuntu" were entered, and the new virtual machine- "V1_karachko" was created.[picture 1-1-3]
1.4 I acquainted with the possibilities of VM1 control -start, stop, reboot, save state,
use Host key (Ctrl-B Power on, Ctrl-E Power off, Ctrl-R Reset the power, Ctrl-Z Suspend, 
Ctrl-N Create a new virtual machine,Ctrl-O Open a virtual machine,Ctrl-F4 Close the summary/console view for the selected virtual machine.,Ctrl-D Edit the virtual machine's configuration.) 
1.5 I cloned the existing VM1 by creating the VM2 . I right-clicked on the virtual machine and selected "Clone",set the name "V2_karachko", and selected- Full Clone[picture 1-1-5]

1.6. I selected machines (V1_karachko,V2_karachko) and selected Group from the right-click menu with the name VM

1.7 I selected  Take Snapshot from the Machine pull-down menu of the VM window.[picture 1-1-7] 

1.8. I Exported "V1_karachko"(right-clicked on the virtual machine and choose "Export to OCI")
to file "V1-karachko.ova"[picture 1-1-7] . I Imported VM from V1-karachko.ova

2
2.1  I explored VM configuration options (general settings, system settings, display,
storage, audio, network, etc.).
2.2  I Configured the USB to connect the USB ports of the host machine to the VM
[picture 2-2-2]
2.3  I configured a shared folder to exchange data between the virtual machine and
the host. In the window of a running VM, I selected Shared Folders from the Devices menu, [picture 2-3] 
2.4 I Configured different network modes for VM1, VM2.
On the VM "v1_karachko" i ecexuted command  sudo ip addr add 192.168.0.2/24 dev enp0s3
On the VM "v2_karachko" i ecexuted command  sudo ip addr add 192.168.0.3/24 dev enp0s3
On the VM's "v1_karachko"VM "v2_karachko" i configurated netwotk settings "Internal networking"[picture 2-4-3]
I executed ping on the VM "v2_karachko" to VM "v1_karachko" [picture 2-2-4]
The execution of the ping command was successful.

3.I lanched VBoxManage from the directory C:\Program Files\Oracle\VirtualBox
 and executed basic commands-showvminfo, createvm, startvm, modifyvm [picture 3]


##PART 3. WORK WITH VAGRANT##


1 I downloaded  vagrant from the site https://releases.hashicorp.com/vagrant/2.2.14/
and set up the path to Vagrant bin in the Path variable[picture 3-1-1]

2. I made the folder C:\Users\Nataliia in the powershell[picture 3-2]

3. I Initialized the environment with the default Vagrant box:
 init hashicorp/precise64
4. I ran the command "vagrant up"[picture 3-4]
5. I connected to the VM using the program MobaXterm
using SSH, IP address, and port listed above (127.0.0.1:2222). By default, login - vagrant
and password are also vagrant [picture 3-5]
6. I recorded the date and time by executing the date command[picture 3-6]
7. I Stopped and deleted  the created VM using commands("vagrant halt" and "vagrant destroy")
8. I created your own Vagrant box 

8.1. I made the folder of the project
mkdir vagrant-box && cd vagrant-box
8.2. I checked current boxes: 
vagrant box list
8.3. I created new box using Vagrant package"Nataliia_default_1616252756363_43060":
vagrant package --base Nataliia_default_1616252756363_43060
8.4. I added the image centos7 in the box as centos7-custom:
vagrant box add centos7-custom package.box
8.5. I executed the command(C:\Users\Nataliia\vagrant-box>vagrant box list)
centos/7            (virtualbox, 2004.01)
centos7-custom      (virtualbox, 0)
hashicorp/bionic64  (virtualbox, 1.0.282)
hashicorp/precise64 (virtualbox, 1.1.0)
The new box centos7-custom was apeared.
