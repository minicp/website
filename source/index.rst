

.. highlight:: java
   :linenothreshold: 4


####################################################
MiniCP: A lightweight Constraint Programming Solver
####################################################


What is MiniCP
==============

The success of the MiniSAT solver has largely contributed to the dissemination of (CDCL) SAT solvers.
The MiniSAT solver has a neat and minimalist architecture that is well documented.
We believed the CP community was missing such a solver that would permit newcomers to demystify and learn the internals of CP technology. 
Therefore we developped MiniCP, a white-box bottom-up teaching framework for CP implemented in Java. 
MiniCP is voluntarily missing many features that you would find in a commercial or complete open-source solver. 
The implementation, although inspired by state-of-the-art solvers, is not focused on efficiency but rather on readability to convey the concepts as clearly as possible.
MiniCP is small and well tested.


Learn MiniCP and Constraint Programming
=================================================


There is an EdX MOOC `Constraint Programming <https://www.edx.org/course/constraint-programming>`_
but all the videos and programming exercises are now available freely from this page.

In this course, we will learn, using MiniCP, the basics of constraint programming: a paradigm that aims to reduce the cost of developing and solving combinatorial problems through extensive reuse of code, whose design is open-ended, but also through pruning techniques of the search space by reasoning at the level of constraints.

During the proposed projects, you will extend MiniCP in functionality in order to solve more and more complex combinatorial problems, especially in scheduling and vehicle routing. You will also develop global constraints, implement search strategies, model problems, and measure the impact of modeling choices on the efficiency of the solution.

Each of the 10 modules first introduces the concepts through videos, then a programming project is proposed to put these concepts into practice.


Exercises and Assessment
------------------------
For each module, participants are required to complete:

* **Programming Exercises:** Hands-on implementation of solver components and models in MiniCP.
* **Reasoning Exercises:** Short theoretical questions and puzzles to test your understanding of the concepts.

All exercises and project submissions are managed through the **INGInious** platform:
`Access the Exercises <https://inginious.org/course/mooc-cp>`_


Videos
---------------

00: Course Trailer
^^^^^^^^^^^^^^^^^^^^^^^^^

* **Link:** `Trailer <https://youtu.be/bImEVjXXHJI>`_
* **Summary:** A brief introductory video providing an overview of the course goals and what participants can expect to learn about Constraint Programming.

01: CP Intro and Tiny CSP
^^^^^^^^^^^^^^^^^^^^^^^^^
* **Link:** `Video Playlist <https://www.youtube.com/playlist?list=PLSvZlHG3ywyOHIk1dpZJZtpSCqSLOdRdS>`_
* **Slides:** :download:`01-intro-cp.pdf <_static/slides/01-intro-cp.pdf>`
* **Summary:** Introduces the foundations of CP using the N-Queens problem. It progresses from a basic "generate and filter" approach to early failure detection, and finally to the implementation of **Tiny-CSP**. Key concepts include fix-points, domains, state restoration, and declarative programming. It concludes with an introduction to the graph-coloring problem.

02: Mini-CP Internals
^^^^^^^^^^^^^^^^^^^^^
* **Link:** `Video Playlist <https://youtube.com/playlist?list=PLSvZlHG3ywyPMRL3dQqyAStRDBd2yjE3J>`_
* **Slides:** :download:`02-minicp-architecture.pdf <_static/slides/02-minicp-architecture.pdf>`
* **Summary:** Explores the "dark side" or internal architecture of a real CP solver. Topics include the implementation of efficient **sparse-set** domains, variable change notification, the fix-point engine, and Depth-First Search (DFS). It also covers critical state-restoration mechanisms like **trailing** and the StateManager.

03: Implementing Constraints
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
* **Link:** `Video Playlist <https://www.youtube.com/playlist?list=PLSvZlHG3ywyPBY35rNt567Db33yi_AtqH>`_
* **Slides:** :download:`03-sum-element-constraint.pdf <_static/slides/03-sum-element-constraint.pdf>`
* **Summary:** Focuses on the design and implementation of core constraints. It distinguishes between **Domain and Bound consistency** and examines specific constraints like Sum and Element (1D and 2D). Additional topics include idempotency, variable views, boolean variables, reified/logical constraints, and their application to problems like Stable Matching.

04: Table Constraints
^^^^^^^^^^^^^^^^^^^^^
* **Link:** `Video Playlist <https://www.youtube.com/playlist?list=PLSvZlHG3ywyNvzVeuGtNY7t_WAofh-81M>`_
* **Slides:** :download:`04-table-constraints.pdf <_static/slides/04-table-constraints.pdf>`
* **Summary:** Dedicated to the **Table constraint**, the most flexible constraint in CP capable of modeling any relationship. The module covers practical applications like the Eternity II puzzle and automata-based modeling, as well as high-performance filtering algorithms such as **STR** and **Compact-table**.

05: AllDifferent Constraint
^^^^^^^^^^^^^^^^^^^^^^^^^^^
* **Link:** `Video Playlist <https://www.youtube.com/playlist?list=PLSvZlHG3ywyOYHEPmuK85vLMAcIGFpnuK>`_
* **Slides:** :download:`05-alldifferent.pdf <_static/slides/05-alldifferent.pdf>`
* **Summary:** Analyzes one of the most famous global constraints. It covers simple decomposition methods, faster filtering heuristics, and the advanced graph-based algorithm used to achieve full **Domain Consistency**.

06: Routing and Optimization
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
* **Link:** `Video Playlist <https://www.youtube.com/playlist?list=PLSvZlHG3ywyO3sqSCxdCO2D6ZAHJ5z7pQ>`_
* **Slides:** :download:`06-circuit-optim-lns.pdf <_static/slides/06-circuit-optim-lns.pdf>`
* **Summary:** Transitions into optimization and Vehicle Routing Problems (VRP). It details the **Circuit constraint**, including subtour elimination. It also introduces **Large Neighborhood Search (LNS)**, a powerful technique for finding high-quality solutions quickly.

07: Cumulative Scheduling
^^^^^^^^^^^^^^^^^^^^^^^^^
* **Link:** `Video Playlist <https://www.youtube.com/playlist?list=PLSvZlHG3ywyPx1QcTbUyQkI3_0kpTaZoA>`_
* **Slides:** :download:`07-cumulative-scheduling.pdf <_static/slides/07-cumulative-scheduling.pdf>`
* **Summary:** Explores scheduling through the **Cumulative constraint**. It covers feasibility checking using the sweep-line algorithm, updating activity time windows (time-table filtering), and applications in producer-consumer and packing problems.

08: Disjunctive Scheduling
^^^^^^^^^^^^^^^^^^^^^^^^^^
* **Link:** `Video Playlist <https://www.youtube.com/watch?v=lShc9CiRvwM&list=PLSvZlHG3ywyN7rnj_1RJyB2705v6Oydsz>`_
* **Slides:** :download:`08-disjunctive-scheduling.pdf <_static/slides/08-disjunctive-scheduling.pdf>`
* **Summary:** Focuses on resources with a capacity of one (disjunctive resources), as seen in the Jobshop problem. It introduces the **Theta tree** data structure to implement efficient filtering algorithms like Overload Checker and Not-Last.

09: Black-box Search
^^^^^^^^^^^^^^^^^^^^
* **Link:** `Video Playlist <https://www.youtube.com/playlist?list=PLSvZlHG3ywyNq4GvR9ONyyOV1qHcgnVCu>`_
* **Slides:** :download:`09-black-box-search.pdf <_static/slides/09-black-box-search.pdf>`
* **Summary:** Discusses how to automate the "Search" component of CP. It covers the **First-fail principle**, various heuristics (Impact-based, Activity-based, Conflict-based), and search tree strategies like Discrepancy Search and Restarts.

10: Advanced Modeling
^^^^^^^^^^^^^^^^^^^^^
* **Link:** `Video Playlist <https://youtube.com/playlist?list=PLSvZlHG3ywyPfJ2Q4GCMkX8a_1mZkNU2n>`_
* **Slides:** :download:`10-modeling-symmetries.pdf <_static/slides/10-modeling-symmetries.pdf>`
* **Summary:** Covers the "art" of modeling, featuring the Bin-Packing and Steel Mill Slab problems. Topics include **symmetry breaking**, redundant constraints, and the **watched literal** technique. It also introduces modeling languages like **MiniZinc** and **PyCSP3**.



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


* EdX MOOC, `INGI2365 <https://www.edx.org/course/constraint-programming>`_, teachers: Pierre Schaus, Laurent Michel, Pascal Van Hentenryck.
* UCLouvain, Belgium, `INGI2365 <https://uclouvain.be/en-cours-2022-linfo2365>`_, teacher: Pierre Schaus.
* Uppsala University, Sweden, `course 1DL442 <https://www.uu.se/en/admissions/freestanding-courses/course-syllabus/?kKod=1DL442>`_, teacher: Pierre Flener.
* ACP, `Summer School 2017 <https://school.a4cp.org/summer2017/>`_, Porquerolles, France, teacher: Pierre Schaus.
* ACP, `Summer School 2019 <https://school.a4cp.org/summer2019/>`_, Vienna, Austria, teacher: Pierre Schaus.
* ACP, `Summer School 2025 <https://school.a4cp.org/summer2025/>`_, Cotonu, Benin, teacher: Pierre Schaus.


About
*******


`Pierre Schaus <http://www.info.ucl.ac.be/~pschaus/>`_ is Professor at UCLouvain.

`Laurent Michel <http://ash.engr.uconn.edu/~ldm/work/>`_ is Professor at the University of Connecticut.

`Pascal Van Hentenryck <http://pwp.gatech.edu/pascal-van-hentenryck/>`_ is Professor at Georgia Tech.




