# Creating VMs


### xen-tools

Ubuntu contains a number of tools for creating Xen Project guests. The easiest of which is known as xen-tools. This software suite manages the downloading and installing of guest operating systems based DomUs. In this guide we are going to use xen-tools to prepare an Ubuntu paravirtualized domU.

<br/>


sudo apt-get install xen-tools -y

sudo vim /etc/xen-tools/xen-tools.conf

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/10.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/11.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/12.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/13.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/14.png)

<br/>
<br/>



### Create the virtual machine

sudo mkdir /home/xen

sudo chmod 777 /home/xen

sudo mkdir /usr/lib/xen

sudo ln -s /usr/lib/xen-4.4 /usr/lib/xen

sudo xen-create-image --hostname=studentN-x1 --mac=macAddress

* Please refer to [Virtual Machine Mac Address List](https://raw.githubusercontent.com/congqiyuan/tutorial/master/virtual_machine_mac_address.txt)


* The installing progress will take a little long time. While the installing progress, you need to **enter the root password**

<br/>
<br/>



### Create the guest domain

sudo xl create /etc/xen/studentN-x1.cfg -c

* The -c flag above instructs Xen to attach a console to the guest system so that we see output as the system boots.

* Login as **root** and input the password you set when creating the image.

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/15.png)

<br/>


adduser student

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/16.png)

<br/>

sudo apt-get install vim -y

sudo vim /etc/sudoers

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/17.png)

<br/>



* Create studentN-x2 in the same way.

* Add user “student” as well.

* Edit /etc/sudoers to grant privilege to “student” as well.

<br/>


* Finally you should have this:

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/18.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/19.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/20.png)






