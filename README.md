# Apache Spark WordCount Example

This repository contains a simple example of how to use **Apache Spark** to perform a word count on a text file using **Scala**.

---

## Table of Contents
- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Spark WordCount Commands](#spark-wordcount-commands)
- [How It Works](#how-it-works)
- [Execution](#execution)
- [Output](#output)

---

## Overview
WordCount is a classic example in big data processing that demonstrates how to read a text file, split it into words, and count the occurrences of each word using **Apache Spark**.

This example uses **Spark RDDs (Resilient Distributed Datasets)** in Scala.

---

## Prerequisites
- Apache Spark installed
- Java installed (version compatible with Spark)
- Scala installed
- IDE or terminal to run `spark-shell`

---

## Spark WordCount Commands

```scala
// Load the text file as an RDD with 2 partitions
val rdd = sc.textFile("C:/Users/nived/OneDrive/Documents/Wordcount.txt", 2)

// Split each line into words
val words = rdd.flatMap(line => line.split(" "))

// Map each word to a tuple (word, 1) and reduce by key to count occurrences
val wordCounts = words.map(word => (word, 1))
                      .reduceByKey(_ + _)

// Collect and print the result
wordCounts.collect().foreach(println)

```
## Output

- The result will look something like this:

("Spark", 3)
("WordCount", 2)
("Example", 1)
...
