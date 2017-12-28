cppipm
=====
C++ implementation of the Interior Point Method (CPPIPM)

Fork of https://github.com/YimingYAN/cppipm to allow for simple 
building with CMake.

Also removed eigen from this repo.

### Requirements
* [Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page), "*a C++ template library for linear algebra: matrices, vectors, numerical solvers, and related algorithms*". 
Eigen forms the linear algebra core of this software.

### Compiling
    mkdir build
    cd build
    cmake..
    make 
    
Run tests

    make run_tests

### How to use
QP:

```
  Algorithm* test = new cppipm(Q,A,b,c); test -> solve();
```

LP:

```
  Algorithm* test = new cppipm(A,b,c);  test -> solve(); 
```

Or:

```
  Algorithm* test = new cppipm(otherProblem);  test -> solve();
```

### Example
See test.cpp

----
Yiming Yan
