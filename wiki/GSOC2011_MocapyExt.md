---
title: GSOC2011 MocapyExt
permalink: wiki/GSOC2011_MocapyExt
layout: wiki
---

BioPython is a very popular library in Bioinformatics and Computational
Biology. Mocapy++ is a machine learning toolkit for training and using
Bayesian networks. However, Mocapy++ is implemented in C++ and its
monolithic architecture does not provide any mechanism to plug-in new
node types (probability distributions/densities) without prior source
code conversion to C++ and the recompilation of the library. The goal of
the MocapyExt project is to develop an easy-to-use plug-in system for
Mocapy++, which would allow to load and test probability distributions
on the fly. If a user is working in C++, the user could load/embed
arbitrary probability distributions in Mocapy++ and then proceed to use
them in a familiar manner.

Introduction
------------

Mocapy++ is an open source toolkit that is freely available under the
GNU General Public Licence (GPL) from
[SourceForge](http://sourceforge.net/projects/mocapy). Mocapy++ is used
for parameter learning and inference in dynamic Bayesian networks
(DBNs), which encode probabilistic relationships among random variables
in a domain. The library supports a wide spectrum of DBN architectures
and probability distributions, including distributions from directional
statistics; notably, Kent distribution on the sphere and the bivariate
von Mises distribution on the torus, which have proven to be useful in
formulating probabilistic models of protein and RNA structure. This
makes Mocapy++ especially suitable for biomolecular structure
prediction.

The goal of the MocapyExt project is to develop a plugin interface for
Mocapy++. This plugin interface will allow to quickly implement and test
new probability distributions and thus save development time and effort
as it then becomes possible to extend Mocapy++ without undue
modifications and subsequent recompilations.

Author & Mentors
----------------

[Justinas V. Daugmaudis](User%3AJustinas_Daugmaudis "wikilink")
vygis.d@gmail.com

**Mentors**

  
Thomas Hamelryck

Eric Talevich

Work Plan
---------

'''Gain understanding of S-EM and directional statistics '''

-   Review the course material in SCI-B2-1011-Structural bioinformatics;

<!-- -->

-   Study the theory for Markov chain Monte Carlo methods and dynamic
    Bayesian networks;

<!-- -->

-   Supplement the base knowledge by reading relevant papers.

'''Study of Mocapy++ use cases '''

-   Study the Mocapy++ implementation of Stochastic Expectation
    Maximization (S-EM) and parameter learning of Bayesian networks;

<!-- -->

-   Review examples distributed with Mocapy++ library.

'''Study of Mocapy++ internals and code '''

-   Distill the relevant concepts for nodes and densities. Currently,
    there are no such concepts defined within the Mocapy++ framework;

<!-- -->

-   Compare with other examples that implement
    probability distributions.

'''Design of Mocapy++ plugin interface '''

-   Plugin module has to implement the model of
    NodeConcept/DensityConcept;

<!-- -->

-   All the models have to be uniformly accessible through the
    plugin system.

'''Implement Mocapy++ plugin module '''

-   Implement test cases in C++ using the new plugin interface;

<!-- -->

-   Provide Python bindings for the defined interface;

<!-- -->

-   Implement test cases in Python. Verify that this plugin system can
    be used transparently in Python.

'''Experiment with the modular Mocapy++ architecture '''

-   Create sample applications that showcase the advantages of
    modularity that is provided by the plugin system in Mocapy++;

<!-- -->

-   Measure performance.

Schedule
--------

'''Week 1-2 \[May 23th -- June 5th\] '''

Design of interface strategy: it is hard to overstate the importance of
the plugin API feeling "natural" to a Mocapy++ user. So much of the time
will be devoted to the design of the interface.

'''Week 3-5 \[June 6th -- June 19th\] '''

Implement the plugin module.

'''Week 6-7 \[June 20th -- June 30th\] '''

Implement some examples that would showcase Mocapy++ plugin system in
action; for example, how to use externally implemented logistic
distribution.

'''Week 7-8 (Midterm) \[July 1st -- July 10th\] '''

-   Thorough testing and consolidating the features. Writing the
    documentation for each feature.

<!-- -->

-   Mid-term Evaluations. Discuss with the mentor the state of the
    project and adjust the schedule to comply with project's needs.

'''Week 9-10 \[July 11th -- July 24th\] '''

Example applications. Should focus on the type reflection capabilities
of the plugin module.

'''Week 11-12 \[July 25th -- August 7th\] '''

Update the documentation to reflect the new functions. Also document the
examples, do any scrub work of code, etc. Planned 'pencils down' date.

'''Week 13-14 \[August 8th -- August 21st\] '''

Introduce the bindings to the wider audiences, gather the opinions and
the reviews in community.

'''Week 15 \[August 22nd\] '''

The end of the project.

Source Code
-----------

Hosted at [the gSoC11 Mocapy
branch](http://mocapy.svn.sourceforge.net/viewvc/mocapy/branches/gSoC11/)

Progress
--------

'''Use cases '''

-   Plugin registration

A user provides a name of a python library, a name of class and a set of
factual arguments necessary for the construction of the model of the
class. The MocapyExt library in turn then returns an instance of the new
class.

`plugin`<DensityBase>` p("density.py", "ClassName");`  
`boost::shared_ptr`<DensityBase>` n = p.create(/argument_list/);`