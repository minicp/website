*****************************************************************
Part 4: Sum and Element Constraints
*****************************************************************

*We ask you not to publish your solutions on a public repository.
The instructors interested to get the source code of
our solutions can contact us.*

Slides
======

* `Lectures on Youtube <https://youtube.com/playlist?list=PLq6RpCDkJMyrUvtxIwsgTQn2PZr55Bp2i>`_

* `Sum Constraint <https://www.icloud.com/keynote/02bmdG7fW7LWPuuiOlm9vlf_g#04a-sum-constraint>`_

* `Element Constraint <https://www.icloud.com/keynote/013s60X8I6SEv_tG9OWbYj2qA#04b-element-constraints>`_

Theoretical Questions
=====================

* `Element Constraints <https://inginious.org/course/minicp/element>`_


Element1D Constraint
=================================

Given an array :math:`T` of integers and the variables :math:`y` and :math:`z`, the `Element1D` constraint enforces that :math:`z` takes the value at index
:math:`y` of :math:`T`: the relation :math:`T[y]=z` must hold (where indexing starts from 0).

Given the element constraint :math:`T=[1,3,5,7,3]`, the constraint holds for

.. math::
    
    \text{Dom}(y) = \{1\}, \text{Dom}(z) = \{3\}

and 

.. math::

    \text{Dom}(y) = \{3\}, \text{Dom}(z) = \{7\}


but is violated for

.. math::

    \text{Dom}(y) = \{0\}, \text{Dom}(z) = \{2\}

and violated for 

.. math::

    \text{Dom}(y) = \{3\}, \text{Dom}(z) = \{3\}

Implement a propagator
`Element1D.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/Element1D.java>`_
by following the ideas (also in the slides) for `Element2D`,
which however do not lead to domain consistency for both variables.

Verify that your implementation passes the tests of `Element1DTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/constraints/Element1DTest.java>`_.

Also implement a propagator
`Element1DDomainConsistent.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/Element1DDomainConsistent.java>`_
that achieves domain consistency for both variables.

Verify that your implementation passes the tests of `Element1DDCTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/constraints/Element1DDCTest.java>`_.


Element1DVar Constraint with an Array of Variables
==================================================

Implement a propagator
`Element1DVar.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/engine/constraints/Element1DVar.java>`_.
This constraint is more general than `Element1D` above,
since :math:`T` is here an array of variables.

The filtering algorithm is nontrivial,
at least if you want to do it efficiently.
Two directions of implementation are:

* The hybrid domain-bound consistent propagator
  achieves bounds consistency for :math:`z` and all the :math:`T[i]`
  but domain consistency for :math:`y` (recommended).
* The domain-consistent propagator
  achieves domain consistency for :math:`y`, :math:`z`, and all the :math:`T[i]`.

Note: given :math:`T=[x_0, x_1]`, :math:`\text{Dom}(x_0)=\{3, 4\}`, :math:`\text{Dom}(x_1)=\{4, 5\}`, :math:`\text{Dom}(y)=\{0, 1\}`, and :math:`\text{Dom}(z)={4}`, the value :math:`3` **can not** be removed from the domain of :math:`x_0`
and the value :math:`5` **can not** be removed from :math:`x_1`. However, when :math:`y` becomes fixed, say to :math:`0`, then :math:`3` is to be removed from the 
domain of :math:`x_0` (the same is true when :math:`y` becomes fixed to :math:`1`, for the value :math:`5` and the variable :math:`x_1`).

Verify that your implementation passes the tests of `Element1DVarTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/engine/constraints/Element1DVarTest.java>`_.
The tests do not verify that your propagator achieves domain
consistency for all the variables, so you have to write additional tests
in order to verify that your implementation is correct if you are implementing the domain-consistent propagator.


The Stable Matching Problem
===========================

Complete the partial model `StableMatching.java <https://github.com/minicp/minicp/blob/master/src/main/java/minicp/examples/StableMatching.java>`_.
It makes use of the `Element1DVar` constraint you have just
implemented and is also a good example of the manipulation of logical and reified constraints.
Ensure that your implementation discovers all 6 solutions to the provided instance.

Verify that your implementation passes the tests of `StableMatchingTest.java <https://github.com/minicp/minicp/blob/master/src/test/java/minicp/examples/StableMatchingTest.java>`_.
