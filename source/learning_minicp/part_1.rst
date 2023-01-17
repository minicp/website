*****************************************************************
Part 1: Overview of CP, Filtering, Search, Consistency, Fixpoint
*****************************************************************

We propose a set of exercises to extend MiniCP with useful features.
By doing these exercises you will gradually progress in your understanding of CP.
For each exercise, we ask you to implement JUnit tests to make sure that
your implementation works as expected.
If you don't test each feature independently you take the risk to
lose a lot of time finding very difficult bugs.


*We ask you not to publish your solutions on a public repository.
The instructors interested to get the source code of
our solutions can contact us.*

Slides
======

* `Lectures on Youtube <https://www.youtube.com/playlist?list=PLq6RpCDkJMyoH9ujmz6TBoAwT5Ax8RwqE>`_

* `Overview of CP, Filtering, Search, Consistency, Fix-point <https://www.icloud.com/keynote/0ccu9JZiD8ZEhSsB-LnQiRcwA#01-intro>`_

Theoretical Questions
=====================

* `Fixpoint Algorithm <https://inginious.org/course/minicp/fix-point>`_
* `Consistency <https://inginious.org/course/minicp/consistencies>`_

Forking MiniCP to Do the Programming Exercices
===============================================

`Follow the tutorial
<https://inginious.org/course/minicp/minicp-install-1>`_ and then clone your repository.

:ref:`Then follow this tutorial to import it in your IDE <install>`.

Less-or-equal Reified Constraint
================================

Implement `IsLessOrEqual.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/IsLessOrEqual.java>`_.

This is a propagator for the constraint :math:`b \Leftrightarrow x \leq c`, which is called the `reified constraint` (or: `reification`) of the constraint :math:`x \leq c`: it holds if the value of Boolean variable :math:`b` is true if and only if the value of variable :math:`x` is less than or equal to the value :math:`c`.

For example, the constraint holds for

.. math::

    \text{Dom}(b) = \{\mathit{true}\} , \text{Dom}(x) = \{4\}, c = 5

and

.. math::

    \text{Dom}(b) = \{\mathit{false}\}, \text{Dom}(x) = \{4\}, c = 2


but is violated for

.. math::

    \text{Dom}(b) = \{\mathit{true}\} , \text{Dom}(x) = \{5\}, c = 4

and violated for 

.. math::

    \text{Dom}(b) = \{\mathit{false}\}, \text{Dom}(x) = \{2\}, c = 4


where the function :math:`\text{Dom}` returns the domain of the given variable.

**Hint**: use `IsEqual.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/IsEqual.java>`_ as a reference when implementing the constraint.

Verify that your implementation passes the tests of `IsLessOrEqualTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/constraints/IsEqualTest.java>`_.
