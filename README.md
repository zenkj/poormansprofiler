# poor man's profiler

According to [PoorMan'sProfiler](http://poormansprofiler.org), pmp and it's
java version, jpmp, are created. pmp relies on gdb to sample the stack frames
of all threads, and jpmp relies on jstack from jdk to sample the java stack
frames of all java threads.

pmpflame and jpmpflame use [Brendan Gregg's flamegraph](https://github.com/brendangregg/FlameGraph)
to generate flamegraph for the stack sampling.

## Usage

```
$ pmp my-program >my-pragram.stack
sampling 1...
sampling 2...
sampling 3...
sampling 4...
sampling 5...
sampling 6...
sampling 7...
sampling 8...
sampling 9...
sampling 10...
$ 
```
According to the configuration of your Linux system, sudo may be needed.

```
$ jpmp 68799 > my-java-program.stack
sampling 1...
sampling 2...
sampling 3...
sampling 4...
sampling 5...
sampling 6...
sampling 7...
sampling 8...
sampling 9...
sampling 10...
$ 
```
68799 is the process id of java program. Only runnable threads are sampled. If all
java threads need to be sample, use jpmp -a 68799.

```
$ pmpflame my-program
sampling 1...
sampling 2...
sampling 3...
sampling 4...
sampling 5...
sampling 6...
sampling 7...
sampling 8...
sampling 9...
sampling 10...
$ 
```

A flame graph svg file named <my-program>-<pid>.svg is generated.


```
$ jpmpflame 68799
sampling 1...
sampling 2...
sampling 3...
sampling 4...
sampling 5...
sampling 6...
sampling 7...
sampling 8...
sampling 9...
sampling 10...
$ 
```
A flame graph svg file named 68799.svg is generated. -a option can be used too.

