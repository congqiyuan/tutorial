# Introduction

Ganglia is a scalable distributed monitoring system for high-performance computing systems such as clusters and Grids. It is composed of three components: gmond, gmetad, and gweb.

<br/>


### **Gmod**

Gmond stands for Ganglia Monitoring Daemon. It’s a lightweight service that must be installed on each node from which you want to have metrics collected. This daemon performs the actual metrics collection on each host using a simple listen/announce protocol to share the data it gleans with its peer nodes in the cluster. Using gmond, you can collect a lot of system metrics right out of the box, such as CPU, memory, disk, network, and data about active processes. It has two kinds of wok mode.

**Multicast mode:**
Gmond’s default work mode is a multicast mode, meaning that all nodes in the cluster both send and receive metrics, and every node maintains an in-memory database— stored as a hash table—containing the metrics of all nodes in the cluster.

**Deaf & Mute mode:**
The deaf and mute parameters exist to allow some gmond nodes to act as special-purpose aggregators and relays for other gmond nodes. Mute means that the node does not transmit; it will not even collect information about itself but will aggregate the metric data from other gmond daemons in the cluster. Deaf means that the node does not receive any metrics from the network; it will not listen to state information from multicast peers, but if it is not muted, it will continue sending out its own metrics for any other node that does listen. **(In our project, we will use this mode.)**

<br/>


### **Gmetad**
Gmetad (the Ganglia Meta Daemon) is the service that collects metric data from other gmetad and gmond sources and stores their state to disk in RRD format. It also provides a simple query mechanism for collecting specific information about groups of machines and supports hierarchical delegation, making possible the creation of federated mon- itoring domains.

<br/>

### **Gweb**
Gweb is a PHP frontend in which you display all data stored by gmetad using your browser.








