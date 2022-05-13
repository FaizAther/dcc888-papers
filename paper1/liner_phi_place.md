# Linear time algorithm for placing PHI nodes (Discussion v.0.0.0)

## The problem that the paper discusses (X)

### What is the specific problem that the paper solves

The paper solves partial redundancy elimination with profiling information. Basically we want to move code away from redundant paths, using a profiler to assign a cost to each change that we perform in the program code.

### What is the specific problem that the paper solves (PHI)

The paper provides a way to place phi nodes (for static single assignment form, SSA) in linear time as opposed to previous methods that require pre-computing dominance frontiers.

### Why is this problem important

Partial redundancy elimination is important because it tends to speedup code. Moreover, by leaving this task to the compiler, the developer is free to focus on algorithms, instead of on micro-optimizations. A testimony of this important is the fact that PRE is taught in many compiler textbooks, and virtually every compiler implements some variation of it.

### Why is this problem important (PHI)

Phi nodes are used in SSA form that is beneficial to speed up dataflow analysis on basic blocks, this can be used to find bugs, security flaws and in general make code more robust rather than relying on someone to manually verify it.

### Who will benefit immediately from the solution of this problem

The main profiter is the compiler's back-end. This optimization may be implemented immediately in industrial strength compilers. In particular, this optimization was tailored to just-in-time compilers; hence, we believe that it can be used to improve the user experience that interpreters of dynamic languages such as Python and JavaScript provide.

### Who will benefit immediately from the solution of this problem (PHI)

Dataflow analysis is the cornerstone for code analysis, speeding up the SSA form that makes dataflow analysis faster will help to speedup analysis time.
Code analysis is used in coding environments to assist programmers.

### What is the theory upon which the problem is defined?

The paper is grounded by the theory of data-flow analyses. Indeed, throughout the paper the authors assume that the reader is familiar with concepts such as lattices, available expressions and very busy expressions. There is also a bit of graph theory in the paper, as the authors assume that the reader is familiar with the min-cut problem, and with maximal flow networks.

### What is the theory upon which the problem is defined? (PHI)

Since we are dealing with the internal represantation of a program as nodes, inevitable we must deal with graph-theory and graph algorithms.

## The context of the paper (X)

### What is the general context of the paper?

This is a compiler's paper. It deals with partial redundancy elimination that is a classic compiler optimization. In an ideal world, compilers should take care of micro-optimizations; hence, freeing developers of this details.

### What is the general context of the paper? (PHI)

Compilers, static single assignment form used in dataflow analysis for code optimization, bugs and security flaw detections to name a few things.

### Since when is this context source of research?

Partial Redundancy Elimination has been around for, at least, four decades. Profiling became a big part of the compiler's technology in the late eights, early nineties, with the advent of the www, and the rise of the interpreted languages.

### Since when is this context source of research? (PHI)

It appears dataflow is attributed to Vyssotsky at Bell Labs 1960s.
The main paper referenced is Cytron et al from 1989.
Based on information form the ACM library can be found Ron Cytron, Jeanne Ferrante, Barry K. Rosen, Mark N. Wegman, and F. Kenneth Zadeck. 1991. Efficiently computing static single assignment form and the control dependence graph. ACM Trans. Program. Lang. Syst. 13, 4 (Oct. 1991), 451–490. [acm link](<https://doi.org/10.1145/115372.115320>) and then this paper appeared in 1995.
Before SSA form, use-def chains were used in intermediate representation.
*(See question: What is the most seminal paper in this field of research?)*

### Is there any book that provides an in-depth overview of this problem?

Yes. As an example, we can find about partial redundancy elimination in the Dragon's book, chapter 9. In that book, PRE is used to illustrate how different data-flow analyses can be combined together.

### Is there any book that provides an in-depth overview of this problem? (PHI)

The dragon book mentions SSA form and PHI nodes and it also has a section about calculating dominator nodes as well as dominance forntiers. An algorithm for placing PHI nodes non trivially is not aparent.

### What can we find about this context in wikipedia?

There is an entire article about partial redundancy elimination in the wikipedia, available at [link1](<http://www.XXX>). There is also an article about profiling at [link2](<http://www.XXX>)

### What can we find about this context in wikipedia? (PHI)

There is a section on SSA form, but not on linear time placement of phi nodes.

## The Solution (X)

### What is the key idea used to solve the problem?

The authors have developed a new algorithm based on the min-cut problem to solve partial redundancy elimination with profiling. They assign weights to the edges of the data-dependence graph of a program, and then find a min-cut in this graph. This cut determines the points where expressions should be moved in.

### What is the key idea used to solve the problem? (PHI)

Identification of key properties of a flow graph of a program. No need for precomputing dominance forntiers and as a consequence of the algorithm the paper presents it calculated the dominance frontier that can be used in other aspects of the phases of dataflow analysis in linear time according to the claims (see algorithm).

### Why is this specific idea different from what had been done before?

No particular paper seems to have addressed the problem of doing partial redundancy elimination in SSA form programs using profiling information. By joining these two ideas: SSA form and profiling, the authors proposed something new.

### Why is this specific idea different from what had been done before? (PHI)

This paper employes the same principle but with a different approach ensuring a linear time instead of a potentially being quadratic.

### Is there any algorithm involved in the solution?

There is the algorithm to solve the min-cut problem in directed graphs. This algorithm has polynomial time solution. It models the min-cut problem as a flow problem.

### Is there any algorithm involved in the solution? (PHI)

Yes, there are multiple cleverly algorithms, that use graph traversal and properties of based on graph theory to justify properties on the internal representation of the program to validate their claims.

### Is the solution exact, or does it approximate an optimal? In the latter case, what would be the price of finding the optimal?

The solution is exact. Of course, the exact solution relies on profiling information. However, profiling is only good if it reflects the actual future runs of a program.

### Is the solution exact, or does it approximate an optimal? In the latter case, what would be the price of finding the optimal? (PHI)

The solution is exact accompanied with a proof of correctness and argument for complexity as compared to the authors argument that the Cytron et al. paper's implementation was complicated and partial description was provided.

## The Organization of the Paper (X)

## How was the abstract organized?

The abstract is organized in the traditional "context - problem - solution - results" style. The context goes from XX to YY. The problem goes from XX to YY. The solution goes from XX to YY, and the results go from XX to YY.

## How was the abstract organized? (PHI)

"Context - Problem - Solution - Comparision - Results"

## How was the introduction organized?

The introduction is organized in six paragraphs, that also follow the "context - problem - solution - results" style. The authors have also talked quite a lot about related works, explaining why their work deserves to be published. I believe they chose this strategy because they are attacking an old problem, and they need to convince the readers that this problem still offers room for innovation.

## How was the introduction organized? (PHI)

Six paragraphs of:

1. Context/(Current techiniques)
2. Problem
3. Solution
4. Notation/(Internal details)
5. Implementation/Results
6. Implications/(Sections overview)

This paper aims to argue for improvement of a step in the SSA form used in the seminal paper on intermediate reoresentation, this is why a lot of detail is given in comparision to the seminal paper.

## What is discussed in each section of the paper?

The paper has six sections, which are divided as follows: - 1 Introduction - 2 Background - 3 Description of the solution - 4 Comparison with most similar approach - 5 Experiments - 6 Conclusion and future work.

## What is discussed in each section of the paper? (PHI)

The paper has eight sections, which are divided as follows:

1. Introduction
2. Background and Notation
3. DJ Graphs and their properties
4. Algorithm for placing phi nodes
5. Correctness and Complexity
6. Implementation and Experiments
7. Related work
8. Conclusion

## What was left for the conclusion?

In the conclusion the authors repeated most of the contents of the abstract, this time in the past. They re-emphasized the main contributions of the paper, and mentioned some future work that they would like to purse.

## What was left for the conclusion? (PHI)

Reiteration of the introduction and emphisas on the simplcity of techinque used as well as implications, implementation, results and speedup. Ending with references to companion papers where solution is used in other dataflow problems.

## The Written Style (X)

### Can you give a title to each paragraph in the introduction?

1) The need for speed in dynamic languages;
2) Why achieving this speed without dynamic information is so difficult;
3) The previous attempts to integrate PRE, SSA form and profiling;
4) Our key contribution: PRE + SSA + profiling
5) How the min-cut algorithm solves our problem;
6) Summary of experiments.

### Can you give a title to each paragraph in the introduction? (PHI)

1) The phases of dataflow where placing of phi nodes is important;
2) Identification of redundancy in present techniuqe;
3) Optimization in the algorithm for placing phi nodes;
4) Introduction to notation used in solution;
5) Implementation and comparision of both techinuqes;
6) Potential further usecases and overview of sections;

### Can you find examples of sentence topics to every paragraph in the introduction?

In the first paragraph, we have the sentence topic in the first clause: "Partial Redundancy Elimination is one of the most important compiler optimizations". In the second paragraph ....

### Can you find examples of sentence topics to every paragraph in the introduction? (PHI)

1. The algorithms for computing these intermediate representations have one common step- computing program points where data flow information must be “merged”, the so called **phi-nodes** *(2nd sentence)*
1. The time complexity of the original algorithm depends on the size of the dominance frontier. Although the size of the dominance frontier is **linear** for many programs (as was noted by Cytron et al.), ... *(1st sentance)*
1. In this paper, we present **a linear time algorithm for computing the desired set of phi-nodes for N**. without precomputing the domtnance frontiers for all the nodes. *(1st sentence)*
1. The levels of the nodes in the dominator tree are used to order the computation of dominance frontiers of those nodes which are essential to **compute the final set of phi-nodes** in a bottom-up fashion. *(3rd sentence)*
1. Again our algorithm exhibited **a linear behavior** compared to the quadratic behavior of the original algorithm. *(6th sentence)*
1. The significance of the algorithm presented in this paper goes beyond to merely computing **phi-nodes** for SEGS or SSA form. *(1st sentence)*

### Can you give examples of techniques used to connect different paragraphs?

The authors sometimes mention a challenge in the last sentence of the paragraph, and talk about this challenge in the next paragraph. They also start some paragraphs but repeating the idea in the previous, but this time linking it with other concepts. For instance, in the third paragraph of the intro, we have "While there is a consensus that dynamic languages require better compilation technologies, the compiler writers seem to have been unable to apply the most successful techniques described in the literature onto these languages."

### Can you give examples of techniques used to connect different paragraphs? (PHI)

The discussion of an aspect of the paper topic in one paragraph flows into the second paragraph where the aspect is touched on in a different light but also the issue presented in the previous paragprah is elaborated on.
For example:

1. Again our algorithm exhibited a linear behavior compared to the quadratic behavior of the original algorithm. *(Section 1, paragraph 5)*
2. The significance of the algorithm presented in this paper goes beyond to merely computing phi-nodes for SEGS or SSA form. *(Section 1, paragraph 6)*

### Can you find examples of declarative, illustrative and enumerative paragraphs?

Yes. The first paragraph of the introduction is clearly a declarative paragraph, because the authors start it with a thesis topic, e.g., "Partial Redundancy Elimination is one of the most important compiler optimizations", and then provide arguments that justify this thesis. The second paragraph of section 2 is illustrative. The authors are, in this case, explaining how classical PRE is unable to cope with a specific program. Finally, the first paragraph of the related works section (Section 4) is enumerative, as the authors are listing a number of previous attempts to solve the PRE problem in dynamic languages.

### Can you find examples of declarative, illustrative and enumerative paragraphs? (PHI)

* Declarative
  * (Section 1, Paragraph 1):
    * (Sentence 1)
    Static Single Assignment (SSA) form [CFR+ 91], Sparse Evaluation Graphs (SEGS) [CCF91 ], and other related intermediate representations have been successfully used for efficient data flow analysis and program transformations...
    *(Continuies on to provide support with reference to other works.)*

* Illustrative
  * (Section 1, Paragraph 2):
    * (Sentence 2)
    As Cytron and Ferrante pointed out “Since one reason for introducing ~-nodes is to eliminate potentially quadratic behavior when solving actual data flow problems, such worst case behavior during SEG or SSA construction could be problematic.
    *(Illustration with reference to seminal paper that supports this papers work.)*

* Enumerative
  * (Section 6, Paragraph 3):
    * *(Enumeration of comparision of implementation in bit-vecotr and linked list.)*

## The related works (X)

### What is the purpose of the related works section in this paper?

The main purpose of the related works section is to compare some previous attempts to solve PRE with the proposed solution. The authors do not provide a general overview of the field. They also do not talk about the history of the problem. They start with the most recent solutions, and only talk about those that most closely compare to theirs.

### What is the purpose of the related works section in this paper? (PHI)

Points out that present techiniuqes present a quadratic time issue, identifies similar work in this endivure but highlights that while other papers provide same results but they do not compute for example dominance frontiers (or are more dense that slow down dataflow) that can be used in other phases of dataflow analysis. Identifies the similariteis with Cytron et al. paper and clearly identifies the difference they have made.
Notify potential other work that can benefit from this speedup and calculating intermediate representations this paper uses.

### What are the earliest papers about this problem?

The earliest paper about partial redundancy elimination seems to have been "Lazy Code Motion", by Knoop et al., but the authors do not talk about this paper in particular. I had to find it in the description of PRE, available in the wikipedia.

### What are the earliest papers about this problem? (PHI)

The paper specifically mentions Cyton et al. in 1989 as first propose of the algorithm, while other work on sparse analysis is also mentioned as 1982 and 1987.

### What is the most seminal paper in this field of research?

The most seminal paper seems to have been the first, "Lazy Code Motion". It has, as of March 13th of 2013, 615 citations in google scholar. Another paper that seems relatively important in this field is "A Variation of Knoop, Ruthing, and Steffen's Lazy Code Motion", which has 361 citations.

### What is the most seminal paper in this field of research? (PHI)

An Efficient Method of Computing Static Single Assignment Form 1989 (Cytron, ...) 310 citation that proposed the new algorithm that is referenced heavily in this paper.

The work for SSA form is mention in Cytron et al.:

* J. Ferrante, K. J. Ottenstein, and J. D. Warren. The program dependence graph and its use in optimization. ACM pans. on Programming Languages and Systems, 9(3):319-349, July 1987. *(1921 citation)*

* B. Alpern, M. N. Wegman, and F. K. Zadeck. Detecting equality of values in programs. Conf Rec. Fifteenth ACM Symp. on Principles of Programming Languages, January 1988.

* B. K. Rosen, M. N. Wegman, and F. K. Zadeck. Global value numbers and redundant computations. Conf. Rec. Fifteenth ACM Symp. on Principles of Programming Languages, January 1988.

* Taken from: [The Way of the Computer Scientist](<https://www.sciencedirect.com/topics/computer-science/data-flow-analysis>) for dataflow analysis
  * *Vyssotsky at Bell Labs 1960s for dataflow analysis*
  * *Kildall 1973 paper, work by Hecht and Ullman for Iterative dataflow analysis*

Wikipedia also has many reference with Kendall at the top amoung many others.

### Which good conferences have recently published papers about similar problems?

Partial Redundancy Elimination is not exactly a hot topic of research. None of the good conferences that I know have published papers about this topic in the recent years. The references used in the paper also only contain old publications. The most recent is a paper by XX et al., "XXX", which was published in ASPLOS in 2005.

### Which good conferences have recently published papers about similar problems? (PHI)

* Sebastian Buchwald, Denis Lohner, and Sebastian Ullrich. 2016. Verified construction of static single assignment form. In Proceedings of the 25th International Conference on Compiler Construction (CC 2016). Association for Computing Machinery, New York, NY, USA, 67–76.

* Leonardo Filipe Rigon, Paulo Torrens, and Cristiano Vasconcellos. 2020. Inferring types and effects via static single assignment. Proceedings of the 35th Annual ACM Symposium on Applied Computing. Association for Computing Machinery, New York, NY, USA, 1314–1321.

* David Ittah, Thomas Häner, Vadym Kliuchnikov, and Torsten Hoefler. 2021. QIRO: A Static Single Assignment-based Quantum Program Representation for Optimization. ACM Transactions on Quantum Computing Just Accepted (August 2021).

## Validation (X)

### Which points do the authors try to prove with experiments?

The authors try to show that their algorithm can speedup programs, when compared to previous approaches to partial redundancy elimination. They try to show two points: their algorithm yields better performance (Table 1 and Fig. 11), and their algorithm yields smaller code sizes (Fig 12).

### Which points do the authors try to prove with experiments? (PHI)

The speed of the algorithm for different programs as well as scaled on program size compared to the original algorithm. A proof is provided in the previous section.

### Are the experiments rigorous enough?

I think the authors could have been more rigorous. They have not used confidence intervals in their results. They also have tried their approach in only one compiler, and have compared it against an algorithm that they have implemented. It would have been better, in my opinion, if they had tried to compare their algorithm against some PRE implementation available in an industrial quality compiler.

### Are the experiments rigorous enough? (PHI)

I think the proof coupled with the several programs in contrast to the original algorithm as well as provided curve with program size severs enough evidence. One needs to understand how the algorithm works and be satisfied with the proof to agree with them more.

### Which visual resources have the authors used to present data?

They use two figures with bar charts, so show speedup and code size reduction. This data is repeated in a table. The table provides results with one decimal digit of accuracy. I believe that they have used this redundancy to make sure that the reader can understand the amount of performance improvement that the new technique delivers.

### Which visual resources have the authors used to present data? (PHI)

Tables as bar graphs as well as raw values for different programs, curves (on performance with program size). Both in comparision with the original algorithm.

### Which statistical theory have the authors used in this paper?

The authors do not use much statistics in this paper. They have run each benchmark five times, and have thrashed the slowest and the fastest results. The final result is the average of the three left runs. They use arithmetic mean in all the results.

### Which statistical theory have the authors used in this paper? (PHI)

Raw performance figures with the calculated speedup and proofs as used.

## Resources (X)

### Do the authors use any particular type of notation?

They use pseudo-code to represent the algorithms. The style resembles a bit Algol. I found it a bit confusing to follow the pseudo-code.

### Do the authors use any particular type of notation? (PHI)

Simple standard psuedo-code.

### Which examples have the authors used to present their ideas?

The paper uses only one example, that is introduced in the backgrounds section, and then is used throughout the rest of the manuscript, notably in Section 3. The example is a simple program that provides some opportunities of optimization. I do not think they could have made it any simpler. The example has the virtue of showing how the proposed approach yields better results in face of profiling information.

### Which examples have the authors used to present their ideas? (PHI)

The optimization of an algorithm (by Cyton et al.) that places phi nodes with dominance frontiers is talked out extensively in the introduction and is hashed out in the Background and notations section.

### Which visual resources have the authors used to explain their points?

The authors use pseudo-code, and three elaborate figures. Fig 3 shows the dependence-graph of the running example. Fig 4 and Fig 6 illustrates different phases of the algorithm. Fig 4 shows the weights that the algorithm finds, given the profiling information, and Fig 6 shows the final solution of the problem.

### Which visual resources have the authors used to explain their points? (PHI) (O)

Use of Mathematical notation for graph algorithm accompinied with example figures of the graphs before and after the computation.
Psuedo-code as well as definitions of data structures used accompinied with example figure that shows the phi node insertion on the data structure after computation.
Figure 5, 6, 7 and show the performance details.

### (Only in case there is on-line material available to support the paper) Which material is publicly available?

The authors have made available a small prototype of their implementation. I tried to download, but it is not easy to install. Simply typing 'making' in the working directory yields a list of errors. They have left a small README.txt file that explains how to test their approach.

### (Only in case there is on-line material available to support the paper) Which material is publicly available? (PHI)

N/A.
