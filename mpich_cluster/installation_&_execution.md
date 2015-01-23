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

nano -w .bashrc


source .bashrc

sudo nano -w /etc/environment

**Running a minimal MPI Program**
cd /mirror

nano machinelist

nano -w mpi_hello.c

mpicc mpi_hello.c -o mpi_hello

mpiexec -n 6 -f machinelist /mirror/mpi_hello

**Running a better MPI Program (C)**

cd /mirror

nano -w mpi_world.c

* MPI provides functions:
* **MPI_Comm_size** reports the number of processes.
* **MPI_Comm_rank** reports the rank, a number between 0 and size-1, identifying the calling process



mpicc mpi_world.c -o mpi_world

mpiexec -n 6 -f machinelist /mirror/mpi_world

