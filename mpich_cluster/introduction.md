# Introduction

A process is \(traditionally\) a program counter and address space. Processes may have multiple threads \(program counters and associated stacks\) sharing a single address space. MPI is for communication among processes, which have separate address spaces. A _**Message Passing Model**_ is an application that passes messages among processes in order to perform a task. MPI is an abbreviation of _**Message Passing Interface**_. This standard interface would allow programmers to write parallel applications that were portable to all major parallel architectures. MPICH is a high performance and widely portable implementation of the Message Passing Interface \(MPI\) standard.

![](https://raw.githubusercontent.com/congqiyuan/tutorial/master/mpich_cluster/2.png)

