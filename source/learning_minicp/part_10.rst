*****************************************************************
Part 10: Disjunctive Scheduling
*****************************************************************

*We ask you not to publish your solutions on a public repository.
The instructors interested to get the source code of
our solutions can contact us.*

Slides
======

* `Lectures on Youtube <https://youtube.com/playlist?list=PLq6RpCDkJMyrAHSnNczQgftZO83TNJG_k>`_


* `Disjunctive Scheduling Slides <https://www.icloud.com/keynote/0afShCNGJqQiScHO6b3iHaUzA#10-disjunctive-scheduling>`_


Theoretical Questions
=====================

* `Disjunctive Scheduling <https://inginious.org/course/minicp/disjunctive>`_

* `Theta Trees <https://inginious.org/course/minicp/theta-trees>`_

Decomposing the Disjunctive Constraint
=======================================================

Your task is to make the Disjunctive constraint more efficient than by using the Cumulative constraint with unit capacity:

* Implement the constraint `IsLessOrEqualVar.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/IsLessOrEqualVar.java>`_
  for the reification `b iff x <= y`, where `b`, `x`, and `y` are variables.
  This will be useful for implementing the decomposition of the Disjunctive constraint.
* Test your implementation in `IsLessOrEqualVarTest.java. <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/constraints/IsLessOrEqualVarTest.java>`_.
* Implement the decomposition with reified constraints for `Disjunctive.java. <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/Disjunctive.java>`_.
  For each pair of tasks, :math:`i` and :math:`j`, with :math:`i \neq j`, the binary decomposition constrains the two tasks not to overlap in time:
  
  * either task :math:`i` ends before task :math:`j` starts (:math:`b_{ij} \Leftrightarrow e_i \leq s_j`) or
  * task :math:`j` ends before task :math:`i` starts (:math:`b_{ji} \Leftrightarrow e_j \leq s_i`),
  
  with :math:`b_{ij} \neq b_{ji}`.
  
  .. image:: ../_static/cumulative-decomposition.png
      :width: 574
      :alt: cumulative decomposition
      :align: center
  
  
  Task `j` cannot end before task `i` starts since :math:`e_j \leq s_i` does not hold (:math:`b_{ji} = \mathit{false}`).

* Verify that your implementation passes the tests `testAllDiffDisjunctive`, `testNotRemovingSolutions`, and `testBinaryDecomposition` of `DisjunctiveTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/constraints/DisjunctiveTest.java>`_.
* Test whether, as expected, this decomposition prunes more than the formulation with timetable filtering for the Cumulative constraint.
  For example, observe on `JobShop.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/examples/JobShop.java>`_ that the number of backtracks is reduced with the decomposition compared to the formulation with Cumulative.
  Test for instance on the small instance `data/jobshop/sascha/jobshop-4-4-2` with 4 jobs, 4 machines, and 16 activities.


The Global Disjunctive Constraint: Overload Checker, Detectable Precedence, and Not-First-Not-Last
=========================================================================================================================

* Read and make sure you understand the implementation `ThetaTree.java. <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/ThetaTree.java>`_.
  Some unit tests are implemented in `ThetaTreeTest.java. <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/constraints/ThetaTreeTest.java>`_.
  To make sure you understand it, add a unit test with 4 activities and compare the results with a manual computation.
* Overload checking, detectable precedences, not-first-not-last, and edge finding only filter one side of the activities.
  To get the symmetrical filtering, implement the mirroring activities trick similarly to `Cumulative.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/Cumulative.java>`_.
* **Hint**: overload checking, detectable precedences, and not-last all require an array `permEst` that is a permutation of the indices of the activities sorted increasingly by their earliest starting times
  (`permEst[0]` holds the activity with the smallest earliest starting time, while `permEst[n - 1]` holds the activity with the greatest earliest starting time), as well as an
  array `rankEst` that is the inverse of `permEst` (if `permEst[j] = i`, then `rankEst[i] = j`).
  
  Create a helper method that sorts the array `permEst` and updates the array `rankEst` (both arrays are preferably instance variables of the `Disjunctive` class).
* Implement the overload checker in `Disjunctive.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/Disjunctive.java>`_.
  
  Verify that your implementation passes the test `testOverloadChecker` of `DisjunctiveTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/constraints/DisjunctiveTest.java>`_.
* The overload checker should already make a big difference to prune the search tree.  Make sure that larger job-shop instances are now solved faster; for instance, `data/jobshop/sascha/jobshop-6-6-0` should now become easy to solve.
* Implement detectable precedences in `Disjunctive.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/Disjunctive.java>`_.
  
  **Note:** given activity `i`, when updating the temporary earliest start time integer value: 
  
  .. math::
    
    est^{\prime}_{i} \leftarrow \max (est_{i}, ect_{\theta \setminus \{i\}})

  if the activity `i` has already been added to the theta tree, then it must first be removed before updating :math:`est^{\prime}_{i}` and reinserted again after updating :math:`est^{\prime}_{i}` (as indicated by :math:`\theta \setminus \{i\}`).

  Verify that your implementation passes the test `testDetectablePrecedence` of `DisjunctiveTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/constraints/DisjunctiveTest.java>`_.

* Implement not-first-not-last in `Disjunctive.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/Disjunctive.java>`_.

  Make sure your implementation passes the test `testNotLast` of `DisjunctiveTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/constraints/DisjunctiveTest.java>`_.
  
* Make sure your implementation passes all tests in `DisjunctiveTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/constraints/DisjunctiveTest.java>`_.
* (optional) Implement edge finding in `Disjunctive.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/Disjunctive.java>`_ (you will also need to implement the ThetaLambdaTree data structure).
