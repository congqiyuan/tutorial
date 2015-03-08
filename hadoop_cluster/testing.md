# Testing

### Basic Testing
**On the master node:**

su hduser

source /etc/profile

hdfs namenode -format

* Format HDFS when start the cluser for the first time

start-all.sh

jps

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/14.png)

<br/>

**On the slave nodes:**

su hduser

jps

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/15.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/16.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/17.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/18.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/19.png)

<br/>
<br/>
<br/>

### Test Mapreduce with an examplar :

**On the Master Node (student3-x1):**

cd /opt

touch helloworld.txt

vim helloworld.txt

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/20.png)

<br/>
hadoop fs -mkdir /input

hadoop fs -put helloworld.txt /input

cd /opt/hadoop-2.6.0/share/hadoop/mapreduce

hadoop jar hadoop-mapreduce-examples-2.6.0.jar
wordcount /input /output

hadoop fs -ls /output

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/21.png)

<br/>
hadoop fs -text /output/part-r-00000

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/22.png)

<br/>
<br/>
<br/>

### Compile your own program:

cd /opt

mkdir wordcount

scp student@10.42.0.1:/home/coc-server/hadoop/WordCount.java .

* Don’t leave the last point out

cd worccount

mkdir wordcount_classes

javac -cp /opt/hadoop-2.6.0/share/hadoop/mapreduce/hadoop-mapreduce-client-core-2.6.0.jar:/opt/hadoop-2.6.0/share/hadoop/common/hadoop-common-2.6.0.jar:/opt/hadoop-2.6.0/share/hadoop/common/lib/hadoop-annotations-2.6.0.jar -d wordcount_classes WordCount.java

hadoop fs -put WordCount.java /input


jar -cvf wordcount.jar -C wordcount_classes/ .

* Don’t leave the last point out

hadoop jar wordcount.jar org.myorg.WordCount /input /output1

hadoop fs -ls /output1

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/23.png)

<br/>
hadoop fs -text /output1/part-00000

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/24.png)

<br/>
