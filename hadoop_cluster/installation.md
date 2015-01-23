# Installation

### Configuration on All the 6 Nodes

sudo apt-get update

sudo apt-get upgrade

sudo addgroup hadoop

sudo adduser --ingroup hadoop hduser

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/3.png)

<br/>

sudo nano -w /etc/sudoers

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/4.png)


sudo chown -R hduser:hadoop /opt

sudo nano -w /etc/hosts

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/5.png)

<br/>
<br/>


**JDK Installation:**

su hduser

sudo apt-get install python-software-properties -y

sudo apt-get install software-properties-common -y

sudo add-apt-repository ppa:webupd8team/java -y

sudo apt-get update

sudo apt-get install oracle-java7-installer -y

sudo nano -w /etc/profile

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/6.png)

source /etc/profile


<br/>
<br/>
<br/>
<br/>

### Configuration on Master Node ( studentN3-x1 )

su hduser

cd /opt

scp student@10.42.0.1:/home/coc-server/hadoop/hadoop-2.6.0.tar.gz .

* Don’t leave the last point out

tar xvf hadoop-2.6.0.tar.gz

cd /opt/hadoop-2.6.0/lib

scp -r student@10.42.0.1:/home/coc-server/hadoop/native .

* Don’t leave the last point out

* Notice: Hadoop has native implementations of certain components for performance reasons and for non-availability of Java implementations. These components are available in a single, dynamically-linked native library called the native hadoop library. The pre-built 32-bit i386-Linux native hadoop library is available as part of the hadoop distribution and is located in the lib/native directory. But there are no pre-buit 64-bit native hadoop library. So I compiled the library for you.

<br/>

**SSH Without Password**

ssh-keygen -t rsa -P '' -f ~/.ssh/id_rsa

cp ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys

scp -r ~/.ssh hduser@student1-x1:~/

scp -r ~/.ssh hduser@student1-x2:~/

scp -r ~/.ssh hduser@student2-x1:~/

scp -r ~/.ssh hduser@student2-x2:~/

scp -r ~/.ssh hduser@student3-x2:~/

cd /opt/hadoop-2.6.0/etc/hadoop/

nano -w hadoop-env.sh

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/7.png)

<br/>

nano -w core-site.xml

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/8.png)

<br/>

nano -w hdfs-site.xml

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/9.png)

<br/>

cp mapred-site.xml.template mapred-site.xml

nano -w mapred-site.xml

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/10.png)

<br/>

touch masters

nano -w masters



<br/>

nano -w slaves



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

sudo nano -w /etc/profile



source /etc/profile

<br/>

