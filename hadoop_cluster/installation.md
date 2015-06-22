# Installation

### Download hadoop-2.6.0 (Master Node)


su hduser

sudo chown hduser:hadoop -R /opt

cd /opt

scp student@10.42.0.1:/home/coc-server/hadoop/hadoop-2.6.0.tar.gz .

tar -xzvf hadoop-2.6.0.tar.gz

cd /opt/hadoop-2.6.0/lib

scp -r student@10.42.0.1:/home/coc-server/hadoop/native/* .

* Note: Hadoop has native implementations of certain components for performance reasons and for non-availability of Java implementations. These components are available in a single, dynamically-linked native library called the native hadoop library. The pre-built 32-bit i386-Linux native hadoop library is available as part of the hadoop distribution and is located in the lib/native directory. But there are no pre-buit 64-bit native hadoop library. So I compiled the library for you.

<br/>
<br/>



### Update Hadoop configuration files (Master Node)

sudo vim /etc/profile

* Edit this file for All the Nodes

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/4.png)

<br/>

source /etc/profile

cd /opt/hadoop-2.6.0/etc/hadoop/

vim hadoop-env.sh

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/5.png)

vim core-site.xml


<br/>

vim hdfs-site.xml


<br/>

vim yarn-site.xml

<br/>


cp mapred-site.xml.template mapred-site.xml

vim mapred-site.xml


<br/>


vim masters


<br/>

vim slaves



<br/>

sudo mkdir -p /var/hadoop/hdfs/namenode
sudo chown hduser:hadoop -R /var/hadoop

**Applying specific configuration for Slave Nodes : **

sudo mkdir -p /var/hadoop/hdfs/datanode

sudo chown hduser:hadoop -R /var/hadoop/

sudo mkdir /opt/hadoop-2.6.0

sudo chown hduser:hadoop -R /opt/hadoop-2.6.0


**Copying ssh key for Setting up passwordless ssh access from Master to Slave node :  (On Master Node)**

su hduser

ssh-copy-id -i $HOME/.ssh/id_rsa.pub hduser@studentN1-x1

ssh-copy-id -i $HOME/.ssh/id_rsa.pub hduser@studentN1-x2

ssh-copy-id -i $HOME/.ssh/id_rsa.pub hduser@studentN2-x1

ssh-copy-id -i $HOME/.ssh/id_rsa.pub hduser@studentN2-x2

ssh-copy-id -i $HOME/.ssh/id_rsa.pub hduser@studentN2-x2


sudo rsync -avxP /opt/hadoop-2.6.0/ hduser@studentN1-x1:/opt/hadoop-2.6.0

sudo rsync -avxP /opt/hadoop-2.6.0/ hduser@studentN1-x2:/opt/hadoop-2.6.0

sudo rsync -avxP /opt/hadoop-2.6.0/ hduser@studentN2-x1:/opt/hadoop-2.6.0

sudo rsync -avxP /opt/hadoop-2.6.0/ hduser@studentN2-x2:/opt/hadoop-2.6.0

sudo rsync -avxP /opt/hadoop-2.6.0/ hduser@studentN3-x2:/opt/hadoop-2.6.0

* The above command will share the files stored within hadoop folder to Slave nodes with location – /opt/hadoop-2.6.0. So, you don’t need to again download as well as setup the above configuration in rest of all nodes. You just need Java and rsync to be installed over all nodes.

### Fromat Namenode (MasterNode)
source /etc/profile

hdfs namenode -format

### Start all hadooop daemons(MasterNode)
start-dfs.sh

start-yarn.sh

mr-jobhistory-daemon.sh start historyserver


<br/>
<br/>

### Track/Monitor/Verify (All Noes)
jps


Connect to you CSVPN first!
ssh student@202.45.128.135
ssh -Nf -L 202.45.128.135:<100xx>:localhost:8088 student@studentN3-x1
ssh -Nf -L 202.45.128.135:<100xx>:localhost:50070 student@studentN3-x1
ssh -Nf -L 202.45.128.135:<100xx>:localhost:19888 student@studentN3-x1


For ResourceManager:

For NameNode:

For JobHistoryServer:

### Stop the Cluster (Not now)
stop-yarn.sh

stop-dfs.sh

mr-jobhistory-daemon.sh stop historyserver

* You can do this after the Testing


