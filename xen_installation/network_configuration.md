# Network Configuration

Next we need to setup our system so that we can attach virtual machines to the external network. This is done by creating a virtual switch within dom0 that takes packets from the virtual machines and forwards them onto the physical network so they can see the Internet and other machines on your network. The piece of software we use to do this is called the Linux bridge and its core components reside inside the Linux kernel. In this case the “bridge” is effectively our virtual switch. The Ubuntu kernels are compiled with the Linux bridging module so all we need to do is installing the control utilities------**bridge-utils**.

<br/>
<br/>


### Network bridge

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/5.png)
<br/>
<br/>


### Network bridge in our project

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/6.png)

<br/>

sudo apt-get install bridge-utils -y

sudo vim /etc/network/interfaces

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/7.png)

<br/>


sudo reboot

ssh student@studentN

ifconfig

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/8.png)

<br/>


brctl show

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/9.png)

<br/>



