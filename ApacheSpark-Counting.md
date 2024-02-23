# Introduction to Apache Spark Architecture <br>

Notes in this file are from the course [Introduction to Apache Spark Architecture](https://customer-academy.databricks.com/). <br>

## Lesson 2: Counting <br>

### Stages: <br>
* A stage cannot be completed until all tasks are completed. <br>
* Spark 3.x can run some stages in parallel (e.g. inputs to a join). <br>
* One long-running task can delay an entire stage from completing. <br>
* The shuffle between two stages is one of the most expensive operations in Apache Spark. <br>

## Quiz Answers:
1. In our example of counting D&B candies, which of the following operations (on the left) best describes the event (on the right)?<br>
* Count all the D&Bs -> Jobs <br>
* Produce the local count -> Stage 1 <br>
* Produce the global count -> Stage 2 <br>
* Count the number of D&Bs in a single partition -> Stage 1's four tasks <br>
* Sum all of the local counts to produce the global count -> Stage 2's only task <br>

2. Which transformations must Apache Spark execute with multiple stages? <br>
* Only those transformations that ultimately require knowledge of the entire dataset. <br>

3. Which transformations must Apache Spark execute in only one stage? <br>
* Only those transformations that can be executed with disregard to any of the other data in the global dataset. <br>

4. Transformations that can be executed in single stages are generally referred to as "wide" transformations <br>
* False

5. Transformations that must be executed across multiple stages are generally referred to as "narrow" transformations <br>
* False

6. In a job with multiple stages, subsequent stages can be started if the majority of the tasks in the previous stage have been completed <br>
* False

7. In a job with multiple stages, the execution of the secondary stages can be delayed by a single, slow-running task in the previous stage. <br>
* True
