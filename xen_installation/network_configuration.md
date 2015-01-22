# Network Configuration

Next we need to setup our system so that we can attach virtual machines to the external network. This is done by creating a virtual switch within dom0 that takes packets from the virtual machines and forwards them onto the physical network so they can see the Internet and other machines on your network. The piece of software we use to do this is called the Linux bridge and its core components reside inside the Linux kernel. In this case the “bridge” is effectively our virtual switch. The Ubuntu kernels are compiled with the Linux bridging module so all we need to do is install the control utilities------bridge-utils.

### Network bridge



### Network bridge in our project

sudo apt-get install bridge-utils

sudo nano -w /etc/network/interfaces

sudo reboot

ssh student@studentN

ifconfig

brctl show

