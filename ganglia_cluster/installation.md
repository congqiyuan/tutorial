# Installation

### **Installation on studentN1:**

sudo apt-get install apache2 php5 php5-json

* While the installing, you need to confirm to restart apache

sudo apt-get install ganglia-monitor rrdtool gmetad ganglia-webfrontend

cd /etc/ganglia-webfrontend

sudo cp apache.conf /etc/apache2/sites-enabled/ganglia.conf

sudo nano -w /etc/ganglia/gmetad.conf

sudo nano -w /etc/ganglia/gmod.conf

<br/>


### **Installation on: studentN1-x1, studentN1-x2, studentN2-x1, studentN2-x2, studentN3-x1, studentN3-x2**

sudo apt-get install ganglia-monitor

sudo nano -w /etc/ganglia/gmond.conf

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

Open firefox with http://localhost/ganglia

