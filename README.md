# CSC 375 Assignment 2 Benchmarking Results - Justyce Countryman

## **About this page** ##
This page will discuss the benchmarking results of running a concurrent program using the Java Microbenchmark Harness (JMH) through two different means, a non-concurrent data structure with a locking scheme and a concurrent data structure that comes directly from the Java library.

## **Context of Programming Project** ##
The purpose of my project is to generate a random semester schedule of six courses based on a .txt file that (hopefully) contains all SUNY Oswego courses. The courses will be held in either a HashMap with a ReadWriteLock or a ConcurrentHashMap. Each benchmark will use 32 threads and each of those threads will have the same probability of either reading from the data structure six times to create a schedule of random classes or writing a new course to the data structure. If the HashMap with the ReadWriteLock method is used, threads will be controlled by acquiring and releasing readLock and writeLock, with data consumption or production occurring in between. If the ConcurrentHashMap is chosen, the reading or writing will happen within a synchronized function instead, which still ensures thread safety.

## **What are the Different Loads?** ##
For each platform, there will be graphs from four benchmarks. The benchmarks are based on four different fixed probabilities that the threads have of reading or writing. The platforms are run from my 2020 13" MacBook Pro M1 with 16GB of RAM and 8 cores (4 performance and 4 efficiency). The platforms include running straight from my computer, using the rho server, and using the gee server.

## **Load 1: ≈ 99% Reads** ##
<img width="1327" alt="CSC375Load1" src="https://github.com/lljustycell999/CSC375Assignment2.github.io/assets/123667513/2a23a015-401d-46fe-bd10-da8fcff7e52b">

## **Load 2: ≈ 90% Reads** ##
<img width="1330" alt="CSC375Load2" src="https://github.com/lljustycell999/CSC375Assignment2.github.io/assets/123667513/fd58045c-5f27-43ff-8711-6e92e9db9300">

## **Load 3: ≈ 75% Reads** ##
<img width="1333" alt="CSC375Load3" src="https://github.com/lljustycell999/CSC375Assignment2.github.io/assets/123667513/9b08e23c-5edd-4f84-b245-f9131bb1c116">

## **Load 4: ≈ 50% Reads** ##
<img width="1333" alt="CSC375Load4" src="https://github.com/lljustycell999/CSC375Assignment2.github.io/assets/123667513/3d6e4bc8-8363-46e9-9619-deb260ce5bf1">

## **Conclusion** ##
It is clear that the ConcurrentHashMap from the Java library is able to perform more operations in a given timeframe than the HashMap with the custom-made ReadWriteLock. In Rho, each test had the ConcurrentHashMap scoring about 10 to 13 times higher than the HashMap with the ReadWriteLock. In Gee, the ConcurrentHashMap still reigned supreme, but only scoring about 4.5 times higher. Finally, my MacBook Pro gave results that first favored the ConcurrentHashMap by about 39 to 47 percent, yet the 50/50 split between reads and writes resulted in the ReadWriteLock method winning with a 13 percent increase in operations. Nevertheless, the big picture indicates the ConcurrentHashMap should still always be the parallel data structure to use in nearly all cases, even if the program does more writes than reads.  
