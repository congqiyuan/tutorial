# Installing XEN

### Remote connection to your student machine

ssh {yourCSaccount}@gatekeeper.cs.hku.hk (your private password)

ssh student@202.45.128.135 (password: student)

ssh student@studentXX (password: student)


### Update and Upgrade your system

sudo apt-get update

sudo apt-get upgrade


###Install the hypervisor

sudo apt-get install xen-hypervisor-amd64

sudo reboot

ssh student@studentN

sudo xl list

sudo xl info

sudo nano -w /etc/xen/xend-config.sxp

