---
title: GSOC
permalink: wiki/GSOC
layout: wiki
---

Introduction
------------

The Open Bioinformatics foundation successfully [applied to participate
in the Google Summer of
Code](http://www.open-bio.org/wiki/Google_Summer_of_Code).

Please read the [GSoC page at the Open Bioinformatics
Foundation](http://www.open-bio.org/wiki/Google_Summer_of_Code) and the
[main Google Summer of Code page](http://code.google.com/soc) for more
details about the program.

Mentor List
-----------

Usually, each BioPython proposal has one or more mentors assigned to it.
Nevertheless, we encourage potential students to contact the mailing
list with their own ideas for proposals. There is therefore not a set
list of 'available' mentors, since it highly depends on which projects
are proposed every year.

Past mentors include:

-   [James Casbon](http://casbon.me/)
-   [Brad Chapman](https://github.com/chapmanb)
-   [Peter Cock](http://www.hutton.ac.uk/staff/peter-cock)
-   [Thomas Hamelryck](http://wiki.binf.ku.dk/User:Thomas_Hamelryck)
-   [Reece Hart](http://www.linkedin.com/in/reece)
-   [João Rodrigues](http://nmr.chem.uu.nl/~joao)
-   [Eric Talevich](http://etal.myweb.uga.edu/)

Proposals
---------

### 2013

The BioPython proposals for 2013 will be published here once discussed.
We encourage potential students to join the mailing lists and actively
participate in these discussions, either by submitting their own ideas
or contributing to improving existing ones.

Past Proposals
--------------

### 2012

#### [SearchIO](http://biopython.org/wiki/SearchIO)

Rationale  
Biopython has general APIs for parsing and writing assorted sequence
file formats (SeqIO), multiple sequence alignments (AlignIO),
phylogenetic trees (Phylo) and motifs (Bio.Motif). An obvious omission
is something equivalent to BioPerl's SearchIO. The goal of this proposal
is to develop an easy-to-use Python interface in the same style as
SeqIO, AlignIO, etc but for pairwise search results. This would aim to
cover EMBOSS muscle & water, BLAST XML, BLAST tabular, HMMER, Bill
Pearson's FASTA alignments, and so on.

Approach  
Much of the low level parsing code to handle these file formats already
exists in Biopython, and much as the SeqIO and AlignIO modules are
linked and share code, similar links apply to the proposed SearchIO
module when using pairwise alignment file formats. However, SearchIO
will also support pairwise search results where the pairwise sequence
alignment itself is not available (e.g. the default BLAST
tabular output). A crucial aspect of this work will be to design a
pairwise-search-result object heirachy that reflects this, probably with
a subclass inheriting from both the pairwise-search-result and the
existing MultipleSequenceAlignment object. Beyond the initial challenge
of an iterator based parsing and writing framework, random access akin
to the Bio.SeqIO.index and index\_db functionality would be most
desirable for working with large datasets.

Challenges  
The project will cover a range of important file formats from major
Bioinformatics tools, thus will require familiarity with running these
tools, and understanding their output and its meaning. Inter-converting
file formats is part of this.

Difficulty and needed skills  
Medium/Hard depending on how many objectives are attempted. The student
needs to be fluent in Python and have knowledge of the
BioPython codebase. Experience with all of the command line tools listed
would be clear advantages, as would first hand experience using
BioPerl's SearchIO. You will also need to know or learn the git version
control system.

Mentors  
[Peter Cock](http://www.hutton.ac.uk/staff/peter-cock)

#### [Representation and manipulation of genomic variants](http://arklenna.tumblr.com/tagged/gsoc2012)

Rationale  
Computational analysis of genomic variation requires the ability to
reliably communicate and manipulate variants. The goal of this project
is to provide facilities within BioPython to represent sequence
variation objects, convert them to and from common human and file
representations, and provide common manipulations on them.

Approach & Goals  

-   Object representation
    -   identify variation types to be represented (SNV, CNV, repeats,
        inversions, etc)
    -   develop internal machine representation for variation types
    -   ensure coverage of essential standards, including HGVS, GFF, VCF
-   External representations
    -   write parser and generators between objects and external string
        and file formats
-   Manipulations
    -   canonicalize variations with more than one valid representation
        (e.g., ins versus dup and left shifting repeats).
    -   develop coordinate mapping between genomic, cDNA, and protein
        sequences (HGVS)
-   Other
    -   release code to appropriate community efforts and write short
        manuscript
    -   implement web service for HGVS conversion

Difficulty and needed skills  
Easy-to-Medium depending on how many objectives are attempted. The
student will need have skills in most or all of: basic molecular biology
(genomes, transcripts, proteins), genomic variation, Python, BioPython,
Perl, BioPerl, NCBI Eutilities and/or Ensembl API. Experience with
computer grammars is highly desirable. You will also need to know or
learn the git version control system.

Mentors  
[Reece Hart](http://www.linkedin.com/in/reece)

[Brad Chapman](https://github.com/chapmanb)

[James Casbon](http://casbon.me/)

### 2011

#### [Biomolecular Interface Analysis](http://biopython.org/wiki/GSoC2011_mtrellet)

Student  
Mikael Trellet

Rationale  
Analysis of protein-protein complexes interfaces at a residue level
yields significant information on the overall binding process. Such
information can be broadly used for example in binding affinity studies,
interface design, and enzymology. To tap into it, there is a need for
tools that systematically and automatically analyze protein structures,
or that provide means to this end.
Protorop (http://www.bioinformatics.sussex.ac.uk/protorp/) is an example
of such a tool and the elevated number of citations the server has had
since its publication acknowledge its importance. However, being a
webserver, Protorop is not suited for large-scale analysis and it leaves
the community dependent on its maintainers to keep the
service available. On the other hand, Biopython’s structural biology
module, Bio.PDB, provides the ideal parsing machinery and programmatic
structures for the development of an offline, open-source library for
interface analysis. Such a library could be easily used in large-scale
analysis of protein-protein interfaces, for example in the CAPRI
experiment evaluation or in benchmark statistics. It would be also
reasonable, if time permits, to extend this module to deal with
protein-DNA or protein-RNA complexes, as Biopython supports nucleic
acids already.

Approach & Goals  

-   Add the new module backbone in current Bio.PDB code base
    -   Evaluate possible code reuse and call it into the new module
    -   Try simple calculations to be sure that there is stability
        between the different modules (parsing for example) and
        functions
-   Define a stable benchmark
    -   Select few PDB files among interface size and proteins size
        would be different
-   Extend IUPAC.Data module with residue information
    -   Deduce residues weight from Atom instead of direct dictionary
        storage
    -   Polar/charge character (dictionary or influenced by pH)
    -   Hydrophobicity scale(s)
-   Implement Extended Residue class as a subclass of Residue
-   Implement Interface object and InterfaceAnalysis module
-   Develop functions for interface analysis
    -   Calculation of interface polar character statistics (% of polar
        residues, apolar, etc)
    -   Calculation of BSA calling MSMS or HSA
    -   Calculation of SS element statistics in the interface through
        DSSP
    -   Unit tests and use of results as input for further calculations
        by other tools and scripts
-   Develop functions for Interface comparison
-   Code organization and final testing

Difficulty and needed skills  
Easy/Medium. Working knowledge of the Bio.PDB module of BioPython.
Knowledge of structural biology in general and associated file
formats (PDB).

Mentors  
[João Rodrigues](http://nmr.chem.uu.nl/~joao)

[Eric Talevich](http://etal.myweb.uga.edu/)

#### [A Python bridge for Mocapy++](http://biopython.org/wiki/GSOC2011_Mocapy)

Student  
Michele Silva

Rationale  
Discovering the structure of biomolecules is one of the biggest problems
in biology. Given an amino acid or base sequence, what is the three
dimensional structure? One approach to biomolecular structure prediction
is the construction of probabilistic models. A Bayesian network is a
probabilistic model composed of a set of variables and their joint
probability distribution, represented as a directed acyclic graph. A
dynamic Bayesian network is a Bayesian network that represents sequences
of variables. These sequences can be time-series or sequences of
symbols, such as protein sequences. Directional statistics is concerned
mainly with observations which are unit vectors in the plane or in
three-dimensional space. The sample space is typically a circle or
a sphere. There must be special directional methods which take into
account the structure of the sample spaces. The union of graphical
models and directional statistics allows the development of
probabilistic models of biomolecular structures. Through the use of
dynamic Bayesian networks with directional output it becomes possible to
construct a joint probability distribution over sequence and structure.
Biomolecular structures can be represented in a geometrically natural,
continuous space. Mocapy++ is an open source toolkit for inference and
learning using dynamic Bayesian networks that provides support for
directional statistics. Mocapy++ is excellent for constructing
probabilistic models of biomolecular structures; it has been used to
develop models of protein and RNA structure in atomic detail. Mocapy++
is used in several high-impact publications, and will form the core of
the molecular modeling package Phaistos, which will be released soon.
The goal of this project is to develop a highly useful Python interface
to Mocapy++, and to integrate that interface with the Biopython project.
Through the Bio.PDB module, Biopython provides excellent functionality
for data mining biomolecular structure databases. Integrating Mocapy++
and Biopython will allow training a probabilistic model using data
extracted from a database. Integrating Mocapy++ with Biopython will
create a powerful toolkit for researchers to quickly implement and test
new ideas, try a variety of approaches and refine their methods. It will
provide strong support for the field of biomolecular structure
prediction, design, and simulation.

Approach & Goals  
Mocapy++ is a machine learning toolkit for training and using
Bayesian networks. It has been used to develop probabilistic models of
biomolecular structures. The goal of this project is to develop a Python
interface to Mocapy++ and integrate it with Biopython. This will allow
the training of a probabilistic model using data extracted from
a database. The integration of Mocapy++ with Biopython will provide a
strong support for the field of protein structure prediction, design
and simulation.

Mentors  
[Eric Talevich](http://etal.myweb.uga.edu/)

[Thomas Hamelryck](http://wiki.binf.ku.dk/User:Thomas_Hamelryck)

#### [MocapyExt](http://biopython.org/wiki/GSOC2011_MocapyExt)

Student  
Justinas V. Daugmaudis

Rationale  
BioPython is a very popular library in Bioinformatics and
Computational Biology. Mocapy++ is a machine learning toolkit for
parameter learning and inference in dynamic Bayesian networks (DBNs),
which encode probabilistic relationships among random variables in
a domain. Mocapy++ is freely available under the GNU General Public
Licence (GPL) from SourceForge. The library supports a wide spectrum of
DBN architectures and probability distributions, including distributions
from directional statistics. Notably, Kent distribution on the sphere
and the bivariate von Mises distribution on the torus, which have proven
to be useful in formulating probabilistic models of protein and
RNA structure.

Such a highly useful and powerful library, which has been used in such
projects as TorusDBN, Basilisk, FB5HMM with great success, is the result
of the long-term effort. The original Mocapy implementation dates back
to 2004, and since then the library has been rewritten in C++. However,
C++ is a statically typed and compiled programming language, which does
not facilitate rapid prototyping. As a result, currently Mocapy++ has no
provisions for dynamic loading of custom node types, and a mechanism to
plug-in new node types that would not require to modify and recompile
the library is of interest. Such a plug-in interface would assist rapid
prototyping by allowing to quickly implement and test new probability
distributions, which, in turn, could substantially reduce development
time and effort; the user would be empowered to extend Mocapy++ without
modifications and subsequent recompilations. Recognizing this need, the
project (herein referred as MocapyEXT), with the aim to improve the
current Mocapy++ node type extension mechanism, has been proposed by T.
Hamelryck.

Approach & Goals  
The MocapyEXT project is largely an engineering effort to bring a
transparent Python plug-in interface to Mocapy++, where built-in and
dynamically loaded node types could be used in a uniform manner. Also,
externally implemented and dynamically loaded nodes could be modified by
a user and these changes will not necessitate the recompilation of the
client program, nor the accompanying Mocapy++ library. This will
facilitate rapid prototyping, ease the adaptation of currently existing
code, and improve the software interoperability whilst introducing
minimal changes to the existing Mocapy++ interface, thus facilitating a
smooth acceptance of the changes introduced by MocapyEXT.

Mentors  
[Eric Talevich](http://etal.myweb.uga.edu/)

[Thomas Hamelryck](http://wiki.binf.ku.dk/User:Thomas_Hamelryck)

### 2010

### 2009