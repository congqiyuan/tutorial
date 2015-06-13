# Prerequisites (All the 6 Nodes)

### Installing Oracle Java 8

sudo apt-get install python-software-properties -y

sudo apt-get install software-properties-common -y

sudo add-apt-repository ppa:webupd8team/java -y

sudo apt-get update -y

sudo apt-get install oracle-java8-installer -y


<br/>
<br/>

### Creating a Hadoop user for accessing HDFS and MapReduce

* To avoid security issues, we recommend to setup new Hadoop user group and user account to deal with all Hadoop related activities.

sudo addgroup hadoop

sudo adduser --ingroup hadoop hduser

sudo usermod -a -G sudo hduser

<br/>

<br/>

### Configuring SSH
* SSH (“Secure SHell”) is a protocol for securely accessing one machine from another. Hadoop uses SSH for accessing another slaves nodes to start and manage all HDFS and MapReduce daemons.

sudo apt-get install openssh-server

<br/>

* Once you installed SSH on your machine, you can connect to other machine or allow other machines to connect with this machine. However we have this single machine, we can try connecting with this same machine by SSH. To do this, we need to copy generated RSA key pairs to authorized_keys file of Slave Nodes.


su hduser
ssh-keygen -t rsa -P ""

cat $HOME/.ssh/id_rsa.pub >> $HOME/.ssh/authorized_keys

cat $HOME/.ssh/id_rsa.pub >> $HOME/.ssh/known_hosts

<br/>

* Install rsync for sharing hadoop source with rest all Machines,

sudo apt-get install rsync



<br/>
<br/>

### Disabling ipv6
* Since Hadoop doesn’t work on IPv6, we should disable it. One of another reason is also that it has been developed and tested on IPv4 stacks. Hadoop nodes will be able to communicate if we are having IPv4 cluster.


sudo vim /etc/sysctl.conf



<br/>
<br/>

### Edit hosts
sudo vim /etc/hosts




