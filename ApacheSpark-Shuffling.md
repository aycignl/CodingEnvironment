# Introduction to Apache Spark Architecture <br>

Notes in this file are from the course [Introduction to Apache Spark Architecture](https://customer-academy.databricks.com/). <br>

## Lesson 3: Shuffling <br>
* Shuffling is the process of rearranging data within a cluster between stages.
* Triggered by "wide" operations (there is no pre-defined list for the wide operations in the doc):
  * Re-partitioning
  * ByKey operations (except counting)
  * Joins, the worse being cross joins
  * Sorting
  * Distinct
  * GroupBy
* Try to group wide transformations together for the best automatic optimization
  * Aim for: narrow, narrow, wide, wide, wide, narrow
  * Avoid: narrow, wide, narrow, wide, narrow, wide
* One of the most significant, yet often unavoidable, causes of performance degradation
* Just because it's slow, it doesn't mean that it's bad (don't polish the cannonball)

## Quiz Answers: <br>
1. In scenario #3, which was the last action taken in the conclusion of stage #1?
* The new dataset was written to disk as shuffle files

2. Which key factors relate to the performance hit associated with wide transformations?
* The pre-processing of each partition to conform to a data structure suitable to the corresponding wide transformation.
* The writing of shuffle data from disk.
* The reading of shuffle data from disk.
* The reading of shuffle data from one executor into another.
* The post-processing of each partition to conclude the shuffle operation. <br>
(all of the above)

3. For the following question, identify which operations are narrow and which are wide.
* Cross Join -> Wide
* Union -> Narrow
* Repartition -> Wide
* Sample -> Narrow
* Distinct -> Wide
* Join -> Wide
* Map -> Narrow
* Filter -> Narrow
* Sort -> Wide
* Coalesce -> Narrow
* Group By -> Wide

4. Given the correct strategy, the shuffle operation for any wide transformations can be avoided
* False

5. Because of the performance cost associated with wide transformations, namely the cost of their respective shuffle operations, wide transformations should be avoided altogether.
* False

6. One can assist the Catalyst Optimizer's optimization processes by executing multiple wide transformations back-to-back.
* True
