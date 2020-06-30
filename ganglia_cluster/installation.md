# Installation

## **Installation on studentN1:**

sudo apt-get install apache2 php5 php5-json -y

sudo apt-get install ganglia-monitor rrdtool gmetad ganglia-webfrontend -y

* While the installing, you need to confirm to restart apache

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/7.png)

ifconfig

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/ip.png)

sudo vim /etc/hosts

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/host.png)

sudo /etc/init.d/apache2 restart

cd /etc/ganglia-webfrontend

sudo cp apache.conf /etc/apache2/sites-enabled/ganglia.conf

sudo vim /etc/ganglia/gmetad.conf

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/8.png)

sudo vim /etc/ganglia/gmond.conf

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/9.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/10.png)

## **Installation on: studentN1-x1, studentN1-x2, studentN2-x1, studentN2-x2, studentN3-x1, studentN3-x2**

sudo apt-get install ganglia-monitor -y

sudo vim /etc/ganglia/gmond.conf

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/11.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/12.png)

## **Testing your monitoring system:**

**On studentN1:**

sudo /etc/init.d/ganglia-monitor start

sudo /etc/init.d/gmetad start

sudo /etc/init.d/apache2 restart



**On studentN1-x1, studentN1-x2, studentN2-x1, studentN2-x2, studentN3-x1, studentN3-x2:**

sudo /etc/init.d/ganglia-monitor start



**On studentN1:**

gstat -a

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/13.png)

Open firefox with [http://localhost/ganglia](http://localhost/ganglia)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/14.png)

