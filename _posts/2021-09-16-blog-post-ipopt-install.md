---
title: 'Installation of Ipopt'
date: 2021-09-16
permalink: /posts/install-ipopt
tags:
    - code
---

*This blog post aims to provide a detailed guide of installing and configuring the solver Ipopt with C++ interface.*

[Ipopt](https://github.com/coin-or/Ipopt) is an extremely powerful solver for nonlinear optimization problems.
While its convergence relies on the convexity of the problem, it has achieved numerical success even for nonconvex problems.

For the installation, we need
* A release version of  [Ipopt](https://github.com/coin-or/Ipopt/releases), and
* the g++ in [GCC Compiler](https://gcc.gnu.org) that would be used for the C++ project calling Ipopt.

Optionally, the following linear solvers can be integrated to further improve the performance of Ipopt if available.
* [HSL](https://www.hsl.rl.ac.uk)
* [Pardiso](https://www.pardiso-project.org)

Change to the directory of Ipopt
```bash
cd <directory of downloaded Ipopt files>
```
and run
```bash
./configure --prefix=<Ipopt installation directory> ADD_CFLAGS=-fopenmp ADD_FFLAGS=-fopenmp ADD_CXXFLAGS=-fopenmp 
```
where the `<Ipopt installation directory>` is the customized installation directory, e.g., under the home directory.
If not specified, then the current directory would be the installation directory.
The flags `-fopenmp` enables [OpenMP](https://www.openmp.org) for parallelization which is used in parallel linear solvers of HSL (e.g., MA57).
To configure Pardiso, one need to add further
```bash
./configure --with-pardiso="$HOME/Pardiso/libpardiso600-GNU720-X86-64.so -lgomp" --with-blas-lib="${BLAS}" --with-lapack-lib="${LAPACK}"
```
where `${BLAS}` and `${LAPACK}` are the environment variables pointing to the paths of the library files Blas and Lapack. 
After the configuration, we can use
```bash
make
make test
make install
```
for installation.

To compile a C++ program calling Ipopt with Pardiso, use
  ```bash
g++ <source/objects files> -o <executable> -L<Path to directory of PARDISO> -lpardiso600-GNU720-X86-64 -L<Path to directory of LAPACK/BLAS> -l<Fast LAPACK and BLAS libraries> -lgfortran -fopenmp -lpthread -lm
  ``` 
(where LAPACK and BLAS libraries can be specified through absolution path without `-l`).

To run the binary compiled from C++, export the necessary environment variables with
```bash
export OMP_NUM_THREADS=<Number of threads for the program>
```
for the number of threads used by OpenMP, and
```bash
export PARDISO_LIC_PATH=<Path to the license file of Pardiso>
```
if Pardiso is also integrated.



