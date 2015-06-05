# Installation & Execution

**On studentN2:**

sudo apt-get install build-essential autoconf automake gfortran

cd /mirror

scp student@10.42.0.1:/home/coc-server/ganglia/mpi/mpich-3.1.tar.gz .

* Don’t ignore the last “.”

<br/>

tar xvf mpich-3.1.tar.gz

mkdir mpich3

cd mpich-3.1

./configure --prefix=/mirror/mpich3

* The prefix option defines which folder will MPICH be installed, we want to install MPICH in NFS folder

<br/>

make

sudo make install

* This command will copy the compiled file to the prefixed folder

<br/>

vim .bashrc

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/14.png)

<br/>

source .bashrc

sudo vim /etc/environment

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/15.png)

<br/>
<br/>
<br/>

**Running a minimal MPI Program**

cd /mirror

vim machinelist

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/16.png)

<br/>

scp student@10.42.0.1:/home/coc-server/ganglia/mpi/mpi_hello.c .
( Don’t ignore the last “.” )

mpicc mpi_hello.c -o mpi_hello

mpiexec -n 6 -f machinelist /mirror/mpi_hello

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/18.png)


<br/>
<br/>
<br/>


**Running a better MPI Program (C)**

cd /mirror

scp student@10.42.0.1:/home/coc-server/ganglia/mpi/mpi_world.c .
( Don’t ignore the last “.” )

mpicc mpi_world.c -o mpi_world

mpiexec -n 6 -f machinelist /mirror/mpi_world

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/20.png)

<br/>


