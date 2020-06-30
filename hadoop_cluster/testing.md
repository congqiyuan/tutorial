# Testing

## Test the Mapreduce with an examplar :

**On the Master Node \(student3-x1\):**

cd /opt

scp student@10.42.0.1:/home/coc-server/hadoop/file.txt .

hadoop fs -mkdir /input

hadoop fs -put file.txt /input

cd /opt/hadoop-2.6.0 /share/hadoop/mapreduce

hadoop jar hadoop-mapreduce-examples-2.6.0.jar wordcount /input /output

hadoop fs -ls /output

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/17.png)

hadoop fs -text /output/part-r-00000

## Compile your own program:

cd /opt

mkdir wordcount

cd worccount

mkdir wordcount\_classes

scp student@10.42.0.1:/home/coc-server/hadoop/WordCount.java .

javac -cp /opt/hadoop-2.6.0/share/hadoop/mapreduce/hadoop-mapreduce-client-core-2.6.0.jar:/opt/hadoop-2.6.0/share/hadoop/common/hadoop-common-2.6.0.jar:/opt/hadoop-2.6.0/share/hadoop/common/lib/hadoop-annotations-2.6.0.jar -d wordcount\_classes WordCount.java

jar -cvf wordcount.jar -C wordcount\_classes/ .

hadoop jar wordcount.jar org.myorg.WordCount /input /output1

hadoop fs -ls /output1

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/18.png)

hadoop fs -text /output1/part-00000

## TeraSort

To run the terasort benchmark, three separate steps are required. In general the rows are 100 bytes long, thus the total amount of data written is 100 times the number of rows \(i.e. to write 500 MB of data, use 5000000 rows\). You will also need to specify input and output directories in HDFS.

cd /opt/hadoop-2.6.0/share/hadoop/mapreduce

* Run teragen to generate rows of random data to sort.

yarn jar hadoop-mapreduce-examples-2.6.0.jar teragen 5000000 /terainput

* Run terasort to sort the database.

yarn jar hadoop-mapreduce-examples-2.6.0.jar terasort /terainput /teraoutput

yarn jar hadoop-mapreduce-examples-2.6.0.jar terasort -Dmapreduce.job.maps=5 /teraoutput /teravalidate1

yarn jar hadoop-mapreduce-examples-2.6.0.jar terasort -Dmapreduce.job.reduces=5 /teraoutput /teravalidate2

yarn jar hadoop-mapreduce-examples-2.6.0.jar terasort -Dmapreduce.job.maps=5 -Dmapreduce.job.reduces=5 /teraoutput /teravalidate3

* Run teravalidate to validate the sorted Teragen.

yarn jar hadoop-mapreduce-examples-2.6.0.jar teravalidate /teraoutput /teravalidate

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/19.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/hadoop_cluster/20.png)

