*****************************************************************
Part 2: Domains, Variables, Constraints
*****************************************************************

*We ask you not to publish your solutions on a public repository.
The instructors interested to get the source code of
our solutions can contact us.*

Slides
======

* `Lectures on Youtube <https://youtube.com/playlist?list=PLq6RpCDkJMypEq5qeLBz8xFTdtAkNr56I>`_

* `Domains and Variables <https://www.icloud.com/keynote/0d8bL8fMVoxodgnQvYx_LHwxA#02-domains-variables-constraints>`_

Theoretical Questions
=====================

* `Domains and Sparse Sets <https://inginious.org/course/minicp/domains>`_

Domain with an Arbitrary Set of Values
=================================================================================

Implement the missing constructor in `IntVarImpl.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/core/IntVarImpl.java>`_:


.. code-block:: java

    public IntVarImpl(Solver cp, Set<Integer> values) {
        throw new NotImplementedException();
    }

Create a dense domain and then remove all values not present in the set `values`.

Verify that your implementation passes the tests of `IntVarTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/core/IntVarTest.java>`_.

Implement a Domain Iterator
======================================

Many filtering algorithms require iteration over the values of a domain.

A naive (and correct) way of iterating over the values of a domain is:


.. code-block:: java

    for (int v = x.min(); v <= x.max(); x++) {
        if (x.contains(i)) {
            // do something
        }
    }

This method is rather inefficient as it will (possibly) iterate over values that are not present in the domain.
Instead, the `fillArray` method from `StateSparseSet.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/state/StateSparseSet.java>`_
allows filling an array only with the values present in the sparse set.
Additionally, if the offset is 0, then the very efficient method `System.arraycopy` can be used.

If the array that stores the returned array of the method `fillArray` is an instance variable, then it will not be garbage collected by the java garbage collector, resulting in a very efficient implementation.
It is important for efficiency to avoid creating objects on the heap (such as arrays) at each execution of propagators that need to be garbage collected, 
as the `propagate()` method of a constraint can be called thousands of times every second.

Since the implementation using `fillArray` iterates on a copy of the array containing the domain, any modification on the actual domain will not carry over to the copy, and vice versa, remving and 
`ConcurrentModificationException` exceptions that might otherwise have been thrown.

To do:

* Improve the efficiency of `fillArray` from `StateSparseSet.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/state/StateSparseSet.java>`_, using `System.arraycopy` where possible.
* Implement `public int fillArray(int [] dest)` in `IntVarImpl.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/core/IntVarImpl.java>`_.
* Verify that your implementation passes the tests of `IntVarTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/core/IntVarTest.java>`_ and `StateSparseSetTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/state/StateSparseSetTest.java>`_. Additionally, add more tests to `IntVarTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/core/IntVarTest.java>`_.

The Absolute Value Constraint
==============================

Implement `Absolute.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/Absolute.java>`_.

Several directions of implementation are possible:

1. The full domain-consistent version (use the `fillArray` method to iterate over domains).
2. A hybrid domain-bound consistent one.

Verify that your implementation passes the tests of `AbsoluteTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/constraints/AbsoluteTest.java>`_.


The Maximum Constraint
==============================

Implement `Maximum.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/Maximum.java>`_.

Implement a bound-consistent filtering algorithm.

**Hint**: Given :math:`y = \max (X)`, where :math:`X` is an array of variables, what are the lower and upper bounds of :math:`y`?

Verify that your implementation passes the tests of `MaximumTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/constraints/MaximumTest.java>`_.
