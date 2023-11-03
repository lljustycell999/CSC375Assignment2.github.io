# CSC 375 Assignment 2 - Benchmarking Results

## **About this page** ##
This page will discuss the benchmarking results of running a concurrent program using the Java Microbenchmark Harness (JMH) through two different means, a non-concurrent data structure with a locking scheme and a concurrent data structure that comes directly from the Java library.

## **Context of Programming Project** ##
The purpose of my project is to generate a random semester schedule of six courses based on a .txt file that (hopefully) contains all SUNY Oswego courses. The courses will be held in either a HashMap with a ReadWriteLock or a ConcurrentHashMap. Each benchmark will use 32 threads and each of those threads will have the same probability of either reading from the data structure six times to create a schedule of random classes or writing a new course to the data structure. If the HashMap with the ReadWriteLock method is used, threads will be controlled by acquiring and releasing readLock and writeLock, with data consumption or production occurring in between. If the ConcurrentHashMap is chosen, the reading or writing will happen within a synchronized function instead, which still ensures thread safety.

## **What are the Different Loads?** ##
For each platform, there will be graphs from three benchmarks. The benchmarks are based on three different fixed probabilities that the threads have of reading or writing.
