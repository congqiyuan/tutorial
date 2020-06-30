# Installation & Execution

**On studentN2:**

sudo apt-get install build-essential autoconf automake gfortran -y

cd /mirror

scp student@10.42.0.1:/home/coc-server/ganglia/mpi/mpich-3.1.tar.gz .

* Don’t ignore the last “.”

tar xvf mpich-3.1.tar.gz

mkdir mpich3

cd mpich-3.1

./configure --prefix=/mirror/mpich3

* The prefix option defines which folder will MPICH be installed, we want to install MPICH in NFS folder

make

sudo make install

* This command will copy the compiled file to the prefixed folder

vim .bashrc

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/14.png)

source .bashrc

sudo vim /etc/environment

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/15.png)

\*\*\*\*

**Running a minimal MPI Program**

cd /mirror

vim machinelist

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/16.png)

scp student@10.42.0.1:/home/coc-server/ganglia/mpi/[mpi\_hello.c](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/mpi_hello.c) . \( Don’t ignore the last “.” \)

mpicc mpi\_hello.c -o mpi\_hello

mpiexec -n 6 -f machinelist /mirror/mpi\_hello

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/18.png)

\*\*\*\*

**Running a better MPI Program \(C\)**

cd /mirror

scp student@10.42.0.1:/home/coc-server/ganglia/mpi/[mpi\_world.c](https://raw.githubusercontent.com/congqiyuan/tutorial/master/ganglia_cluster/mpi_world.c) . \( Don’t ignore the last “.” \)

mpicc mpi\_world.c -o mpi\_world

mpiexec -n 6 -f machinelist /mirror/mpi\_world

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/20.png)

