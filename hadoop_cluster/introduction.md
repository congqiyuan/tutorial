# Prerequisites

## Installing Oracle Java 8

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install python-software-properties -y

sudo apt-get install software-properties-common -y

sudo add-apt-repository ppa:webupd8team/java -y

sudo apt-get update -y

sudo apt-get install oracle-java8-installer -y

## Creating a Hadoop user for accessing HDFS and MapReduce

* To avoid security issues, we recommend to setup new Hadoop user group and user account to deal with all Hadoop related activities.

sudo addgroup hadoop

sudo adduser --ingroup hadoop hduser

sudo usermod -a -G sudo hduser

## Configuring SSH

* SSH \(“Secure SHell”\) is a protocol for securely accessing one machine from another. Hadoop uses SSH for accessing another slaves nodes to start and manage all HDFS and MapReduce daemons.

sudo apt-get install openssh-server

* Once you installed SSH on your machine, you can connect to other machine or allow other machines to connect with this machine. However we have this single machine, we can try connecting with this same machine by SSH. To do this, we need to copy generated RSA key pairs to authorized\_keys file of Slave Nodes.

su hduser ssh-keygen -t rsa -P ""

cat $HOME/.ssh/id\_rsa.pub &gt;&gt; $HOME/.ssh/authorized\_keys

cat $HOME/.ssh/id\_rsa.pub &gt;&gt; $HOME/.ssh/known\_hosts

* Install rsync for sharing hadoop source with rest all Machines,

sudo apt-get install rsync

## Disabling ipv6

* Since Hadoop doesn’t work on IPv6, we should disable it. One of another reason is also that it has been developed and tested on IPv4 stacks. Hadoop nodes will be able to communicate if we are having IPv4 cluster.

sudo vim /etc/sysctl.conf

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/2.png)

## Edit hosts

sudo vim /etc/hosts

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/3.png)

* To make above changes reflected, we need to reboot all of the Nodes.

sudo reboot

