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
* Edit this file for All Nodes

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/4.png)

<br/>

vim core-site.xml

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/8.png)

<br/>

vim hdfs-site.xml

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/9.png)

<br/>

cp mapred-site.xml.template mapred-site.xml

vim mapred-site.xml

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/10.png)

<br/>

touch masters

vim masters

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/11.png)

<br/>

vim slaves

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/12.png)

<br/>

scp -r /opt/hadoop-2.6.0 hduser@student1-x1:/opt/

scp -r /opt/hadoop-2.6.0 hduser@student1-x2:/opt/

scp -r /opt/hadoop-2.6.0 hduser@student2-x1:/opt/

scp -r /opt/hadoop-2.6.0 hduser@student2-x2:/opt/

scp -r /opt/hadoop-2.6.0 hduser@student3-x2:/opt/

<br/>
<br/>


**On all the 6 Nodes, student1-x1, student1-x2, student2-x1, student2-x2, student3-x1, student3-x2**

sudo mkdir /var/hadoop

sudo chown -R hduser:hadoop /var/hadoop

sudo vim /etc/profile

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/13.png)

source /etc/profile

<br/>

