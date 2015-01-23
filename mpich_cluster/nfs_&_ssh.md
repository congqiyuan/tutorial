# NFS & SSH

###NFS
NFS (Network File System) allows a system to share directories and files with others over a network. By using NFS, users and programs can access files on remote systems almost as if they were local files.


On studentN2:

sudo apt-get install nfs-server

sudo mkdir /mirror

sudo chown student:student /mirror

sudo nano –w /etc/exports

sudo /etc/init.d/nfs-kernel-server start

On all the virtual machines:

sudo apt-get install nfs-client

sudo mkdir /mirror

sudo chown student:student /mirror

sudo mount studentN2:/mirror /mirror

sudo nano –w /etc/fstab

Note:
The file /etc/fstab is used to auto-mount, for details, please google.




###SSH Without Password

On studentN2:

Add the ip and hostname of your virtual machines into /etc/hosts

sudo nano -w /etc/hosts

ssh-keygen -t rsa

(Copy the generated key file to all the virtual machines:)

sudo ssh-copy-id student@<hostname>

Test connection from studentN2:



