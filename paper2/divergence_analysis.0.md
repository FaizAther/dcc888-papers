# Linear time algorithm for placing PHI nodes (Discusssion) (v.0.0.0)

## The problem that the paper discusses (X)

### What is the specific problem that the paper solves (DA) (X)

Introduction of a static analysis that discovers data, control divergence (called, Divergence Analysis) to produce code for better register reousrce management in SIMD execution model.

### What is the specific problem that the paper solves (PR)

The paper solves partial redundancy elimination with profiling information. Basically we want to move code away from redundant paths, using a profiler to assign a cost to each change that we perform in the program code.

### Why is this problem important (DA) (X)

To generate faster code for GPU's on the SIMD execution model.

### Why is this problem important (PR)

Partial redundancy elimination is important because it tends to speedup code. Moreover, by leaving this task to the compiler, the developer is free to focus on algorithms, instead of on micro-optimizations. A testimony of this important is the fact that PRE is taught in many compiler textbooks, and virtually every compiler implements some variation of it.

### Who will benefit immediately from the solution of this problem (DA) (X)

GPU's are being used for more general purpose programming these days for their thredded execution model (parellel execution) for speed up in performance. General programming and industrial applications of software tools.

### Who will benefit immediately from the solution of this problem (PR)

The main profiter is the compiler's back-end. This optimization may be implemented immediately in industrial strength compilers. In particular, this optimization was tailored to just-in-time compilers; hence, we believe that it can be used to improve the user experience that interpreters of dynamic languages such as Python and JavaScript provide.

### What is the theory upon which the problem is defined? (DA) (X)

Static Analysis is the study of a program source code for compiler optimization phase of the code generation pipline.

### What is the theory upon which the problem is defined? (PR)

The paper is grounded by the theory of data-flow analyses. Indeed, throughout the paper the authors assume that the reader is familiar with concepts such as lattices, available expressions and very busy expressions. There is also a bit of graph theory in the paper, as the authors assume that the reader is familiar with the min-cut problem, and with maximal flow networks.

## The context of the paper (X)

### What is the general context of the paper? (DA) (X)

Compiler paper. Deals with providing compilers with techniques that help them understand and improve divergent code.

### What is the general context of the paper? (PR)

This is a compiler's paper. It deals with partial redundancy elimination that is a classic compiler optimization. In an ideal world, compilers should take care of micro-optimizations; hence, freeing developers of this details.

### Since when is this context source of research? (DA) (X)

The authors have mentioned several material and have pointed out the close links this paper mentioning the key differences in detail.
Automatic optimizations have been around for deacdes, the authors have mentioned various papers from the 1960's, 1990's and early 2000's.

### Since when is this context source of research? (PR)

Partial Redundancy Elimination has been around for, at least, four decades. Profiling became a big part of the compiler's technology in the late eights, early nineties, with the advent of the www, and the rise of the interpreted languages.

### Is there any book that provides an in-depth overview of this problem? (DA) (X)

Chapter 10 Instruction-level parallelism from the Dragon's book.

### Is there any book that provides an in-depth overview of this problem? (PR)

Yes. As an example, we can find about partial redundancy elimination in the Dragon's book, chapter 9. In that book, PRE is used to illustrate how different data-flow analyses can be combined together.

### What can we find about this context in wikipedia? (DA) (X)

<https://en.wikipedia.org/wiki/Data_dependency>.

### What can we find about this context in wikipedia? (PR)

There is an entire article about partial redundancy elimination in the wikipedia, available at [www.XXX](<http://www.XXX>). There is also an article about profiling at [www.XXX](<http://www.XXX>).

## The Solution (X)

### What is the key idea used to solve the problem? (DA) (X)

Static Analysis.

### What is the key idea used to solve the problem? (PR)

The authors have developed a new algorithm based on the min-cut problem to solve partial redundancy elimination with profiling. They assign weights to the edges of the data-dependence graph of a program, and then find a min-cut in this graph. This cut determines the points where expressions should be moved in.

### Why is this specific idea different from what had been done before? (DA) (X)

The authors claim that their work improves on a similar techinque was proposed by researches at Saarland Universie (DE) called vectorization analysis.
They support their claim by providing evidance in the form of raw register pressure numbers making the claim that the said technique miss catagorizes some cases of divergent variables.

### Why is this specific idea different from what had been done before? (PR)

No particular paper seems to have addressed the problem of doing partial redundancy elimination in SSA form programs using profiling information. By joining these two ideas: SSA form and profiling, the authors proposed something new.

### Is there any algorithm involved in the solution? (DA) (X)

Builds upon several other works for example converting to gated static single assignment form.
The authors have introduced a language and operational semantics, rules for the language as well as a constraint system accompanied with proofs (structual induction).

### Is there any algorithm involved in the solution? (PR)

There is the algorithm to solve the min-cut problem in directed graphs. This algorithm has polynomial time solution. It models the min-cut problem as a flow problem.

### Is the solution exact, or does it approximate an optimal? In the latter case, what would be the price of finding the optimal? (DA) (X)

Approximate. Two techniques are described in the paper, the latter being more precise.

### Is the solution exact, or does it approximate an optimal? In the latter case, what would be the price of finding the optimal? (PR)

The solution is exact. Of course, the exact solution relies on profiling information. However, profiling is only good if it reflects the actual future runs of a program.

## The Organization of the Paper (X)

### How was the abstract organized? (DA) (X)

"Context - Problem - Solution - Results".

### How was the abstract organized? (PR)

The abstract is organized in the traditional "context - problem - solution - results" style. The context goes from XX to YY. The problem goes from XX to YY. The solution goes from XX to YY, and the results go from XX to YY.

### How was the introduction organized? (DA) (X)

Eight paragraphs:

1. Inroduction
2. Context
3. Background Concepts
4. Problem definition
5. Key concept
6. Precision
7. Artifacts
8. References

### How was the introduction organized? (PR)

The introduction is organized in six paragraphs, that also follow the "context - problem - solution - results" style. The authors have also talked quite a lot about related works, explaining why their work deserves to be published. I believe they chose this strategy because they are attacking an old problem, and they need to convince the readers that this problem still offers room for innovation.

### What is discussed in each section of the paper? (DA) (X)

1. Introduction
2. Background
3. Divergence Analysis
4. Divergence Aware Register Spiller
5. Expreiments
6. Conclusion
7. Acknowledgement
8. References

### What is discussed in each section of the paper? (PR)

The paper has six sections, which are divided as follows: - 1 Introduction - 2 Background - 3 Description of the solution - 4 Comparison with most similar approach - 5 Experiments - 6 Conclusion and future work.

### What was left for the conclusion? (DA) (X)

Reiteration of the problem statement, and referencing speific sections of the article where they provided solutions.
The authors pointed out that their work can be expanded upon to provided a better user experience for programmers, they have identified that their work helps compilation but not the programmer and they have left hints for further work in this regard.
Ending with why their work is important.

### What was left for the conclusion? (PR)

In the conclusion the authors repeated most of the contents of the abstract, this time in the past. They re-emphasized the main contributions of the paper, and mentioned some future work that they would like to purse.

## The Written Style (X)

### Can you give a title to each paragraph in the introduction? (DA) (X)

1. *Inroduction*: GPU programming and usage trends;
2. *Context*: GPUs: Parallel execution model;
3. *Background Concepts*: Data and control divergence and how it relates to GPU instruction generation?;
4. *Problem definition*: Purpose of this work;
5. *Key concept*: Why is Divergence analysis important and current techniques;
6. *Precision*: A more precise solution with comparision;
7. *Artifacts*: Benchmarks, statistics and avalibility of artifacts;
8. *References*: Impact and presentation of work.

### Can you give a title to each paragraph in the introduction? (PR)

1) The need for speed in dynamic languages; 2) Why achieving this speed without dynamic information is so difficult; 3) The previous attempts to integrate PRE, SSA form and profiling; 4) Our key contribution: PRE + SSA + profiling 5) How the min-cut algorithm solves our problem; 6) Summary of experiments.

### Can you find examples of sentence topics to every paragraph in the introduction? (DA) (X)

1. *Inroduction*: and novel programming abstractionsare developed for them;
2. *Context*: However, divergences may happen in less regular applications;
3. *Background Concepts*: A thread identiﬁer, for instance, is inherentlydivergent;
4. *Problem definition*: The main goal of this article is to provide compilers with techniques that help themunderstand and improve divergent code;
5. *Key concept*: The divergence analysis is important in different ways.;
6. *Precision*: Second, in order to more precisely identify divergences;
7. *Artifacts*: our implementation of the divergenceanalysis runs in linear time;
8. *References*: work in divergence analysis for SIMD ar-chitectures.

### Can you find examples of sentence topics to every paragraph in the introduction? (PR)

In the first paragraph, we have the sentence topic in the first clause: "Partial Redundancy Elimination is one of the most important compiler optimizations". In the second paragraph ....

### Can you give examples of techniques used to connect different paragraphs? (DA) (X)

The discussion of an aspect of the paper topic in one paragraph flows into the second paragraph where the aspect is touched on in a different light but also the issue presented in the previous paragprah is elaborated on. For example:

1. However, divergences may happen in less regular applications. (Section 1, paragraph 2)
2. Data divergence occurs if the same variable name is mapped to different . (Section 1, paragraph 3)

### Can you give examples of techniques used to connect different paragraphs? (PR)

The authors sometimes mention a challenge in the last sentence of the paragraph, and talk about this challenge in the next paragraph. They also start some paragraphs but repeating the idea in the previous, but this time linking it with other concepts. For instance, in the third paragraph of the intro, we have "While there is a consensus that dynamic languages require better compilation technologies, the compiler writers seem to have been unable to apply the most successful techniques described in the literature onto these languages."

### Can you find examples of declarative, illustrative and enumerative paragraphs? (DA) (X)

- Declarative (Section 1, Paragraph 1, Sentence 1)

  Increasing programmability and low hardware cost are boosting the use of graphical processing units (GPU) as a tool to run general-purpose applications.

- Illustrative (Section 1, Paragraph 6, Sentence 4)

  There exists a recent number of divergence-aware code op-timizations, such as Coutinho et al.’s [2011] branch fusion and Zhang et al.’s [2011]thread reallocation strategy.

- Enumerative (Section 4, Paragraph 1, Sentence 2)

  However, in the context of graphicsprocessing units, we have different types of memory to consider. (Register..., Shared Memory..., Local Memore..., Global Memory...).

### Can you find examples of declarative, illustrative and enumerative paragraphs? (PR)

Yes. The first paragraph of the introduction is clearly a declarative paragraph, because the authors start it with a thesis topic, e.g., "Partial Redundancy Elimination is one of the most important compiler optimizations", and then provide arguments that justify this thesis. The second paragraph of section 2 is illustrative. The authors are, in this case, explaining how classical PRE is unable to cope with a specific program. Finally, the first paragraph of the related works section (Section 4) is enumerative, as the authors are listing a number of previous attempts to solve the PRE problem in dynamic languages.

## The related works (X)

### What is the purpose of the related works section in this paper? (DA) (X)

No related work section, however there is a lot of detail in Section 2, Bacground about related works with references and key differences.

### What is the purpose of the related works section in this paper? (PR)

The main purpose of the related works section is to compare some previous attempts to solve PRE with the proposed solution. The authors do not provide a general overview of the field. They also do not talk about the history of the problem. They start with the most recent solutions, and only talk about those that most closely compare to theirs.

### What are the earliest papers about this problem? (DA) (X)

- The ILLIAC IV Computer (G H Barnes et al.) 1968

### What are the earliest papers about this problem? (PR)

The earliest paper about partial redundancy elimination seems to have been "Lazy Code Motion", by Knoop et al., but the authors do not talk about this paper in particular. I had to find it in the description of PRE, available in the wikipedia.

### What is the most seminal paper in this field of research? (DA) (X)

- TRANQUIL: a language for an array processing computer (Norman E. Abel et al.)

- The ILLIAC IV Computer (G H Barnes et al.)

- Barrier inference (Alex Aiken et al.)

### What is the most seminal paper in this field of research? (PR)

The most seminal paper seems to have been the first, "Lazy Code Motion". It has, as of March 13th of 2013, 615 citations in google scholar. Another paper that seems relatively important in this field is "A Variation of Knoop, Ruthing, and Steffen's Lazy Code Motion", which has 361 citations.

### Which good conferences have recently published papers about similar problems? (DA) (X)

- ACM Transactions on Parallel Computing (2021)

  - Pointer-Based Divergence Analysis for OpenCL 2.0 Programs (Shao-Chung Wang et al.)

- ACM Transactions on Architecture and Code Optimization (2018)

  - On-GPU Thread-Data Remapping for Branch Divergence Reduction (Huanxin Lin et al.)

### Which good conferences have recently published papers about similar problems? (PR)

Partial Redundancy Elimination is not exactly a hot topic of research. None of the good conferences that I know have published papers about this topic in the recent years. The references used in the paper also only contain old publications. The most recent is a paper by XX et al., "XXX", which was published in ASPLOS in 2005.

## Validation (X)

### Which points do the authors try to prove with experiments? (DA) (X)

- Reporting number of divergent variables.

- Performance improvement of generated code.

- Register pressure.

### Which points do the authors try to prove with experiments? (PR)

The authors try to show that their algorithm can speedup programs, when compared to previous approaches to partial redundancy elimination. They try to show two points: their algorithm yields better performance (Table 1 and Fig. 11), and their algorithm yields smaller code sizes (Fig 12).

### Are the experiments rigorous enough? (DA) (X)

Since their work is used in an industry scenerio they have provided more than enough experiments.

### Are the experiments rigorous enough? (PR)

I think the authors could have been more rigorous. They have not used confidence intervals in their results. They also have tried their approach in only one compiler, and have compared it against an algorithm that they have implemented. It would have been better, in my opinion, if they had tried to compare their algorithm against some PRE implementation available in an industrial quality compiler.

### Which visual resources have the authors used to present data? (DA) (X)

Pi Charts, bar graphs, tables and plots.

### Which visual resources have the authors used to present data? (PR)

They use two figures with bar charts, so show speedup and code size reduction. This data is repeated in a table. The table provides results with one decimal digit of accuracy. I believe that they have used this redundancy to make sure that the reader can understand the amount of performance improvement that the new technique delivers.

### Which statistical theory have the authors used in this paper? (DA) (X)

Not much simple benchmarks, raw performance numbers.

### Which statistical theory have the authors used in this paper? (PR)

The authors do not use much statistics in this paper. They have run each benchmark five times, and have thrashed the slowest and the fastest results. The final result is the average of the three left runs. They use arithmetic mean in all the results.

## Resources (X)

### Do the authors use any particular type of notation? (DA) (X)

- C source code to describe the problem

- eBNF to define a language

- Big step operational semantics to describe the Machine

- Basic block diagram with assembly style language

- Constraint system for the divergence analysis

- Annotated assembly code

- Logic rules

### Do the authors use any particular type of notation? (PR)

They use pseudo-code to represent the algorithms. The style resembles a bit Algol. I found it a bit confusing to follow the pseudo-code.

### Which examples have the authors used to present their ideas? (DA) (X)

One simple example and one complex used throughout the section 2, Background section and in section 3, Divergence analysis. The authors have taken the exmaple forward making it very easy to follow with clarity.

### Which examples have the authors used to present their ideas? (PR)

The paper uses only one example, that is introduced in the backgrounds section, and then is used throughout the rest of the manuscript, notably in Section 3. The example is a simple program that provides some opportunities of optimization. I do not think they could have made it any simpler. The example has the virtue of showing how the proposed approach yields better results in face of profiling information.

### Which visual resources have the authors used to explain their points? (DA) (X)

- Source code: 2 programs illustrating the idea of data divergene. (Section 2: Background Fig 1)

- Basic block diagram to describe execution of 1 program from section 2. (Section 3: Divergence Analysis Fig 8)

- Conversion of the basic block diagram to GSA form. (Section 3: Divergence Analysis Fig 9)

- Example program to illustrate Higher-Degree Polonomials. (Fig 15)

- Illustrated Assembly code of Fig 1: to introduce the divergence aware register spiller. (Section 4: Divergence Analysis Register spiller Fig 16 17 19)

- Several examples of benchmarks (Pi Charts, bar graphs, tables, plots)

### Which visual resources have the authors used to explain their points? (PR)

The authors use pseudo-code, and three elaborate figures. Fig 3 shows the dependence-graph of the running example. Fig 4 and Fig 6 illustrates different phases of the algorithm. Fig 4 shows the weights that the algorithm finds, given the profiling information, and Fig 6 shows the final solution of the problem.

### (Only in case there is on-line material available to support the paper) Which material is publicly available? (DA) (X)

The code is opensource implemented in the Ocelot industry compiler. See more, (<http://simdopt.wordpress.com>) and (<https://groups.google.com/g/gpuocelot>).

### (Only in case there is on-line material available to support the paper) Which material is publicly available? (PR)

The authors have made available a small prototype of their implementation. I tried to download, but it is not easy to install. Simply typing 'making' in the working directory yields a list of errors. They have left a small README.txt file that explains how to test their approach.
