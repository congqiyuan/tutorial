# Installation

### **Installation on studentN1:**

sudo apt-get install apache2 php5 php5-json

sudo apt-get install ganglia-monitor rrdtool gmetad ganglia-webfrontend

* While the installing, you need to confirm to restart apache

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/7.png)


<br/>

cd /etc/ganglia-webfrontend

sudo cp apache.conf /etc/apache2/sites-enabled/ganglia.conf

<br/>

sudo vim /etc/ganglia/gmetad.conf

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/8.png)

<br/>

sudo vim /etc/ganglia/gmod.conf

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/9.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/10.png)

<br/>
<br/>

### **Installation on: studentN1-x1, studentN1-x2, studentN2-x1, studentN2-x2, studentN3-x1, studentN3-x2**

sudo apt-get install ganglia-monitor

sudo vim /etc/ganglia/gmond.conf

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/11.png)

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/12.png)

<br/>
<br/>


### **Testing your monitoring system:**

**On studentN1:**

sudo /etc/init.d/ganglia-monitor start

sudo /etc/init.d/gmetad start

sudo /etc/init.d/apache2 restart

<br/>

**On studentN1-x1, studentN1-x2, studentN2-x1,
studentN2-x2, studentN3-x1, studentN3-x2:**

sudo /etc/init.d/ganglia-monitor start

<br/>

**On studentN1:**

gstat -a

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/13.png)

<br/>

Open firefox with http://localhost/ganglia

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/14.png)

<br/>



