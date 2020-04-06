# Format converstion
Convert .gr format to METIS format using the following code:

https://github.com/gladcolor/Graphs/blob/master/CS786_to_Metis.ipynb

METIS format [discription](https://people.sc.fsu.edu/~jburkardt/data/metis_graph/metis_graph.html):

1. ASCII

2. a graph of N nodes is stored in a file of N+1 lines;

3. the first line lists the number of nodes and the number of edges;

4. If the first line contains more than two values, the extra values indicate the weights;

5. each subsequent line lists the "neighbors" of a node;

6. comment lines begin with a "%" sign;

# TriangleCounting
OpenMP-based parallel program for counting the number of triangles in a sparse graph.


## Build requirements
 - CMake 2.8, found at http://www.cmake.org/, as well as GNU make. 
 - Download, build, and install [GKlib](https://github.com/KarypisLab/GKlib).

Assuming that the above are available, two commands should suffice to 
build the software:
```
make config 
make
```

## Configuring the build
It is primarily configured by passing options to make config. For example:
```
make config cc=icc
```

would configure it to be built using icc.

Configuration options are:
```
cc=[compiler]     - The C compiler to use [default: gcc]
prefix=[PATH]     - Set the installation prefix [default: ~/local]
gklib_path=[PATH] - Where GKlib was installed [default: ~/local]
openmp=not-set    - To build a serial version
```

## Building and installing
To build and install, run the following
```
make
make install
```

## Other make commands
    make uninstall 
         Removes all files installed by 'make install'.
   
    make clean 
         Removes all object files but retains the configuration options.
   
    make distclean 
         Performs clean and completely removes the build directory.


## Runing the program 
By default, the binary, called _gktc_, will be installed in ~/local/bin.
For usage information just type
```
gktc -help

Usage: gktc [options] infile

 Options
  -iftype=text
     Specifies the format of the input file.
     Possible values are:
        metis   Metis format [default]
        tsv     tsv format (i, j, v)

  -nthreads=int
     Specifies the number of threads to use.
     The default value is set to the value returned by omp_get_max_threads().

  -help
     Prints this message.
```

The program supports two formats for its input files: 
- The one used by the [Metis](http://www.cs.umn.edu/~metis) graph 
  partitioning program.
- The tsv format used by the graphs in the 
  [GraphChallenge 2017](http://graphchallenge.mit.edu/) competition.
Note that the graph has to be undirected and it needs to include both pairs of
edges (i.e., (u,v) and (v,u)).
 
 

