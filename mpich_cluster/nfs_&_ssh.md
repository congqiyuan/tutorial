# NFS & SSH

###NFS
NFS (Network File System) allows a system to share directories and files with others over a network. By using NFS, users and programs can access files on remote systems almost as if they were local files.

<br/>

**On studentN2:**

sudo apt-get install nfs-server

sudo mkdir /mirror

sudo chown student:student /mirror

sudo nano –w /etc/exports
![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/3.png)

<br/>
sudo /etc/init.d/nfs-kernel-server start

<br/>

**On all the virtual machines:**

sudo apt-get install nfs-client

sudo mkdir /mirror

sudo chown student:student /mirror

sudo mount studentN2:/mirror /mirror

sudo nano –w /etc/fstab

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/4.png)


* Note:The file /etc/fstab is used to auto-mount, for details, please google.

<br/>
<br/>
<br/>



###SSH Without Password

**On studentN2:**

sudo nano -w /etc/hosts

* Add the ip and hostname of your virtual machines into /etc/hosts

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/5.png)

<br/>

ssh-keygen -t rsa

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/6.png)

<br/>

* Copy the generated key file to **all the virtual machines:**student1-x1, student1-x2, student2-x2, student2-x2, student3-x1, student3-x2

sudo ssh-copy-id student@**hostname**

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/7.png)

<br/>
<br/>

**Test connection from studentN2:**

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/8.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/9.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/10.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/11.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/12.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/13.png)

<br/>
