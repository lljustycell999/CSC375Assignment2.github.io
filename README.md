# CSC 375 Assignment 2 Benchmarking Results - Justyce Countryman

## **About this page** ##
This page will discuss the benchmarking results of running a concurrent program using the Java Microbenchmark Harness (JMH) through two different means, a non-concurrent data structure with a locking scheme and a concurrent data structure that comes directly from the Java library.

## **Context of Programming Project** ##
The purpose of my project is to generate a random semester schedule of six courses based on a .txt file that (hopefully) contains all SUNY Oswego courses. The courses will be held in either a HashMap with a ReadWriteLock or a ConcurrentHashMap. Each benchmark will use 32 threads and each of those threads will have the same probability of either reading from the data structure six times to create a schedule of random classes or writing a new course to the data structure. If the HashMap with the ReadWriteLock method is used, threads will be controlled by acquiring and releasing readLock and writeLock, with data consumption or production occurring in between. If the ConcurrentHashMap is chosen, the reading or writing will happen within a synchronized function instead, which still ensures thread safety.

## **What are the Different Loads?** ##
For each platform, there will be graphs from four benchmarks. The benchmarks are based on four different fixed probabilities that the threads have of reading or writing. The platforms are run from my 2020 13" MacBook Pro M1 with 16GB of RAM and 8 cores (4 performance and 4 efficiency). The platforms include running straight from my computer, using the rho server, and using the gee server.

## **Load 1: ≈ 99% Reads** ##

## **Load 2: ≈ 90% Reads** ##

## **Load 3: ≈ 75% Reads** ##

## **Load 4: ≈ 50% Reads** ##

## **Conclusion** ##
