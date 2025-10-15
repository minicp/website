.. _intro:




What is MiniCP
==============

The success of the MiniSAT solver has largely contributed to the dissemination of (CDCL) SAT solvers.
The MiniSAT solver has a neat and minimalist architecture that is well documented.
We believe the CP community is currently missing such a solver that would permit newcomers to demystify and learn the internals of CP technology. 
We introduce MiniCP, a white-box bottom-up teaching framework for CP implemented in Java. 
MiniCP is voluntarily missing many features that you would find in a commercial or complete open-source solver. 
The implementation, although inspired by state-of-the-art solvers, is not focused on efficiency but rather on readability to convey the concepts as clearly as possible.
MiniCP is small and well tested.


Learn MiniCP and Constraint Programming
=======================================


The best way to learn MiniCP is to subscribe to our EdX MOOC 
`Constraint Programming <https://www.edx.org/course/constraint-programming>`_

In this course, we will learn, using MiniCP, the basics of constraint programming: a paradigm that aims to reduce the cost of developing and solving combinatorial problems through extensive reuse of code, whose design is open-ended, but also through pruning techniques of the search space by reasoning at the level of constraints.

During the proposed projects, you will extend MiniCP in functionality in order to solve more and more complex combinatorial problems, especially in scheduling and vehicle routing. You will also develop global constraints, implement search strategies, model problems, and measure the impact of modeling choices on the efficiency of the solution.

Each of the 10 modules first introduces the concepts through videos, then a programming project is proposed to put these concepts into practice.


MiniCP Article
===============

The complete architecture of MiniCP is described in this `paper <_static/mini-cp.pdf>`_ (`publisher PDF <https://doi.org/10.1007/s12532-020-00190-7>`_) (`errata and delta with current source code of MiniCP <https://pierre-flener.github.io/courses/M4CO/slides/delta.txt>`_).
Please cite this paper if you use MiniCP in one of your article or if you get inspiration of it.

.. code-block:: text


        @article{cite-key,
                Author = {Michel, L. and Schaus, P. and Van Hentenryck, P.},
                Doi = {10.1007/s12532-020-00190-7},
                Id = {Michel2021},
                Isbn = {1867-2957},
                Journal = {Mathematical Programming Computation},
                Number = {1},
                Pages = {133-184},
                Title = {MiniCP: a lightweight solver for constraint programming},
                Ty = {JOUR},
                Url = {https://doi.org/10.1007/s12532-020-00190-7},
                Volume = {13},
                Year = {2021}}




Javadoc and Github Repository
====================================

* The `Javadoc API <https://minicp.github.io/minicp/>`_.
* The `Github Repo <https://github.com/minicp/minicp>`_.


Getting Help with MiniCP
========================

You'll get the greatest chance of getting answers to your questions by using the MiniCP usergroup_.

.. _usergroup: https://groups.google.com/g/mini-cp


Who Uses MiniCP?
================

If you use it for teaching or for research, please let us know and we will add you in this list.


* EdX MOOC, `INGI2365 <hhttps://www.edx.org/course/constraint-programming>`_, teachers: Pierre Schaus, Laurent Michel, Pascal Van Hentenryck.
* UCLouvain, Belgium, `INGI2365 <https://uclouvain.be/en-cours-2022-linfo2365>`_, teacher: Pierre Schaus.
* Uppsala, Sweden, `Master in CS <https://www.uu.se/en/admissions/master/selma/kursplan/?kKod=1DL442>`_, teacher: Pierre Flener.
* ACP, `Summer School 2017 <https://school.a4cp.org/summer2017/>`_, Porquerolles, France, teacher: Pierre Schaus.
* ACP, `Summer School 2019 <https://school.a4cp.org/summer2019/>`_, Vienna, Austria, teacher: Pierre Schaus.


Citing MiniCP
=============

If you find MiniCP useful for your research or teaching, then you can
cite the following paper (`PDF <https://doi.org/10.1007/s12532-020-00190-7>`_):

.. code-block:: latex

        @article{cite-key,
                Author = {Michel, L. and Schaus, P. and Van Hentenryck, P.},
                Doi = {10.1007/s12532-020-00190-7},
                Id = {Michel2021},
                Isbn = {1867-2957},
                Journal = {Mathematical Programming Computation},
                Number = {1},
                Pages = {133-184},
                Title = {MiniCP: a lightweight solver for constraint programming},
                Ty = {JOUR},
                Url = {https://doi.org/10.1007/s12532-020-00190-7},
                Volume = {13},
                Year = {2021}}


About
*******


`Laurent Michel <http://ash.engr.uconn.edu/~ldm/work/>`_ is Professor at the University of Connecticut.

`Pierre Schaus <http://www.info.ucl.ac.be/~pschaus/>`_ is Professor at UCLouvain.

`Pascal Van Hentenryck <http://pwp.gatech.edu/pascal-van-hentenryck/>`_ is Professor at Georgia Tech.




