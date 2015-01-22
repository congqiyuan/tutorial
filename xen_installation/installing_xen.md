# Installing XEN

### Remote connection to your student machine

ssh {yourCSaccount}@gatekeeper.cs.hku.hk (your private password)

ssh student@202.45.128.135 (password: student)

ssh student@studentXX (password: student)

<br/>
<br/>


### Update and Upgrade your system

sudo apt-get update

sudo apt-get upgrade

<br/>
<br/>


###Install the hypervisor

sudo apt-get install xen-hypervisor-amd64

sudo reboot

ssh student@studentN

<br/>


sudo xl list

( Lists running domains, their IDs, memory, state and CPU time consumed. )

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/2.png)

<br/>


sudo xl info

( Returns the information about the hypervisor and dom0 including version, free memory etc. )

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/3.png)

<br/>



sudo nano -w /etc/xen/xend-config.sxp

(“xend-unix-server” is an option that tells xend whether or not to start the unix domain socket management server. This is required for the CLI tools to operate. Defaults to yes.)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/xen_installation/4.png)









