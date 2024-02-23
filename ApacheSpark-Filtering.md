# Introduction to Apache Spark Architecture <br>

Notes in this file are from the course [Introduction to Apache Spark Architecture](https://customer-academy.databricks.com/). <br>

## Lesson 1: Filtering <br>
* A cluster is a group of nodes. <br>
* Nodes are the individual machines within a cluster (generally a VM). <br>
* With [Databricks](https://www.databricks.com/), the driver (a JVM) and each executor (each a JVM) all run in their nodes. <br>
* Rarely are significant performance improvements made by tweaking Spark configuration settings. <br>

### Driver <br>
* Runs the Spark application. <br>
* Assigns tasks to slots in an executor. <br>
* Coordinates the work between tasks. <br>
* Receives the results, if any. <br>

### Executors <br>
* Provides an environment in which tasks can be run. <br>
* Leverages the JVM to execute many threads. <br>
* Executors share machine-level resources. <br>

### Slots/Cores/Threads <br>
* The lowest unit of parallelization. <br>
* Generally interchangeable terms, but "slot" is the most accurate term. <br>
* Executes a set of transformations against a partition as directed by the driver. <br>

### Parallelization <br>
* Scale horizontally by adding more executors. <br>
* Scale vertically by adding cores to each executor. <br>

### Partitions <br>
* A ~128 MB chunk of the larger dataset. <br>
* Each task processes one and only one partition. <br>
* The size and record splits are decided by the driver. <br>
* The initial size is partially adjustable with various configuration options. <br>

### Applications, Jobs, Stages, and Tasks <br>
* The hierarchy into which work is subdivided. <br>
* One Spark action results in one or more jobs. <br>
* The number of stages depends on the operations submitted with the application. <br>
* Tasks are the smallest unit of work. <br>
* Tasks share executor (JVM) level resources. <br>

## Quiz Answers:
1. In this course, we use the analogy of students sitting in a classroom counting candies to help illustrate the concept behind distributed computing.
With this analogy in mind, match each word on the left to its corresponding word on the right.
* Driver -> The instructor
* Cluster -> Collectively, the instructor, students, and their respective resources
* Partitions -> The small bags of candies
* Tasks -> Specific instructions assigned to a single student to process a specific bag of candies
* Dataset -> The larger bag of candies
* Executor -> The table at which students are working
* Job -> The request to eliminate all the brown candies & place the remaining candies on the table
* Slots/Threads/Core -> The students

2. What is the relationship between applications, jobs, stages, and tasks?
* Application: Consists of zero or more jobs
* Job: Consists of one or more stages
* Stage: Consists of one or more task
* Task: A single unit of work against a single partition of data

3. Which part of the Spark architecture is responsible for deciding which task processes which piece of data?
* Driver

4. Against how many partitions can a single task execute its instructions?
* One partition

5. If you have 3 executors and each executor has 3 slots, what is the maximum number of tasks that can be executed at any one time?
* 9

6. Which part of the Spark architecture is responsible for deciding how to subdivide the larger dataset into at 128 MB chunks?
* Driver

7. What term identifies the smallest unit of work in a Spark application?
* Task

8. Which term identifies the environment in which a task is executed?
* Executor

9. While technically different, which three terms are generally considered to be synonymous?
* Core/Thread/Slot

9. Which two parts of the Spark architecture are run inside of a Java Virtual Machine (JVM)?
* Driver and Executor

