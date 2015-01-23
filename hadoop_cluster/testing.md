# Testing

### Basic Testing
**On the master node:**

su hduser

source /etc/profile

hdfs namenode -format

* Format HDFS when start the cluser for the first time

start-all.sh

jps



**On the slave nodes:**

su hduser

jps


### Test Mapreduce with an examplar :

**On the Master Node (student3-x1):**

cd /opt

touch helloworld.txt

nano -w helloworld.txt


hadoop fs -mkdir /input

hadoop fs -put helloworld.txt /input

cd /opt/hadoop-2.6.0/share/hadoop/mapreduce

hadoop jar hadoop-mapreduce-examples-2.6.0.jar
wordcount /input /output

hadoop fs -ls /output

hadoop fs -text /output/part-r-00000



### Compile your own program:

cd /opt

mkdir wordcount

scp student@10.42.0.1:/home/coc-server/hadoop/WordCount.java .

( Don’t leave the last point out )

cd worccount

mkdir wordcount_classes

javac -cp /opt/hadoop-2.6.0/share/hadoop/mapreduce/hadoop-mapreduce-client-core-2.6.0.jar:/opt/hadoop-2.6.0/share/hadoop/common/hadoop-common-2.6.0.jar:/opt/hadoop-2.6.0/share/hadoop/common/lib/hadoop-annotations-2.6.0.jar -d wordcount_classes WordCount.java

hadoop fs -put WordCount.java /input


jar -cvf wordcount.jar -C wordcount_classes/ .

* Don’t leave the last point out

hadoop jar wordcount.jar org.myorg.WordCount /input /output1

hadoop fs -ls /output1


hadoop fs -text /output1/part-00000
