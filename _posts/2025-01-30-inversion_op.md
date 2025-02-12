---
layout: distill
title: Inversion Operation
description: article about a simple arithmetic inversion operation utilizing a standard AST
tags: compilers
giscus_comments: false
date: 2025-01-30
featured: false
mermaid:
  enabled: false
  zoomable: false
code_diff: false
map: false
chart:
  chartjs: false
  echarts: false
  vega_lite: false
tikzjax: false
typograms: false

authors:
  - name: Evan Drake
    url: "https://snowmang1.github.io/"
    affiliations:
      name: Butte College

bibliography: 2025-01-30-inversion_op.bib

citation: true

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).
toc:
  - name: Introduction
  - name: Literature
  - name: Implementation
  - name: Future
    # if a section has subsections, you can add them as follows:
    # subsections:
    #   - name: Example Child Subsection 1
    #   - name: Example Child Subsection 2

# Below is an example of injecting additional post-specific styles.
# If you use this post as a template, delete this _styles block.
# _styles:
# Can be used for custom style elements
---

# Introduction

For the past couple of months I have been fixated on learning the field of topology as a kind of hobby.
In that time the use of function inversion of the form $f^{-1}$ has caught my eye.
This kind of notation is seen often to describe the inverse of a function $f$, especially in <d-cite key="munkres_topo" ></d-cite>.
I became curious whether this kind of operation was as automatic in computer science.
My favorite languages these days being: Lean4 and Haskell I have gotten all to use to maths being built into a language.
As it turns out things like inversion functions are not common in CS,
    at least not *automatic inversabilty* as seen in the notation $f^{-1}$.
It may be unclear what I mean by automatic inversabilty at this point, I will go into detail later.
There is a literature examining this very topic.
Once I found that this topic was not common enough to have been widely addressed in the non-academic space I got curious about difficulty.
How difficult could it be to create a system within a compiler that could,
    in theory take any arbitrary function and give you its inverse.
I neglected to recall my usage of linear algebra where this concept of non-inversabilty was first introduced to me.
Recalling linear algebra or any calculus examining structures with dimensions greater than two we can conclude that inversabilty is difficult.
My hypothesis was simple,
    I needed to create a program that could create an inverse function automatically while limiting the resources to simulate that of a simple compiler.
I decided to limit myself to a basic AST structure that kept no real metadata but simply the lexemes and some type information.
That was the structure that it would take and create an inverse function with.
I weakened my initial statement and assumed an interpreted language so that I could assume all information is in memory at once for the experiment.
I felt it may take longer than I would like if I used something else (and Haskell is so fun to use).
Some basic pseudocode I drew up for the project before starting.

{% highlight haskell %}
Node : Operation or Lexeme
AST : Node []
-- where the AST is a tree with node equal to an operation or lexeme

f : AST -> AST
f (node []) = invert node -- leaf case
f (node ls) = AST (invert node) (map f ls)
-- f would invert the AST meaning to take the inverse of each piece recursively
-- assume that the inverse of any AST is the inverse of its parts
{% endhighlight %}

I have some initial problems with this approach.
First simply mapping $f$ over all children is begging for a stack overflow.
Secondly is my assumption that the inverse of any function body AST (thus the inverse of any function) is constructed via the inverse of its parts?
I convinced myself that speed optimization could wait until after I had seen if the idea could work.
The assumption did have me worried,
    thus I constrained the math to arithmetic where I found only edge cases where my assumption was untrue.
The edge cases though difficult to ignore can be countered with constraints.
Our problem space is currently bound by the following.

\begin{equation} \label{ax1}
    \text{Axiom 1: }AST^{-1} = [ x = x_i^{-1} | \forall x \in AST]
\end{equation}

\begin{equation} \label{ax2}
    \text{Axiom 2: Arithmetic space only}
\end{equation}

That is to make explicit my assumption that the inverse of any function AST is simply the inverse of its parts,
    thus Axiom \eqref{ax1}.
For this proof of concept I wanted to limit the math to trivialities only.
Thus my limiting the problem space to arithmetic in Axiom \eqref{ax2}.
In particular it is the case that while testing the code I only used basic operators and integers.
The basic operators being: multiply, divide, addition, subtraction.

---

# Literature

The problem of function inversion seems to be widely studied in the field of security.
The literature on encryption has a detailed history of looking into inversion of functions.
I skimmed into the security literature to no avail for my specific problem.
I found a nice overview of the encryption literature surrounding my problem in <d-cite key="corrigan-gibbs"></d-cite>.
They gave an brief history of the problem,
    I found this extremely helpful in providing a scope of the field and its previously solved (and unsolved) problems.
I however did not find anyone in this field explicitly attempting to create low level tacit creation of inverse functions more broadly.
I found the encryption field to be useful in describing the overall difficulty of inversion.
Given that I had constrained my problem space to only arithmetic and primitive operators,
    I tried to find something closer to my problem space.
Looking more deeply into programming literature I had trouble finding a literature on tacit inversion of functions.
Given that mathematics has proven inversion to not always be possible,
    one could only conclude that it is not seen as a useful tool to have a tacit inversion operation.
There is also the possibility that the difficulty of producing such a tool is greater than it is beneficial.
I did find a paper in the broader field of computer science based on exactly the sort of tacit inversion in my question.
In <d-cite key="teegen_haskell_2021"></d-cite> they design (and create) a system of inversion based entirely on the *monad*.
They use the idea of *monadic lifting* taking advantage of the non-deterministic behavior inherent in Haskellian monads.
Monadic lifting provides a framework for abstracting the inversion process for an arbitrary monad.
Meaning no matter what the operation is,
    once lifted one can simply ask to invert the monad.
Of course some characteristics of Haskell are not invertible by definition.
This paper to my knowledge provides the only implementable solution to the problem of compiler level tacit inversion <d-footnote>
    Which is amazing, I can not state enough how cool <d-cite key="teegen_haskell_2021"></d-cite> was to read</d-footnote>.
It is the case that the authors of the paper lean on the theories of logical programming to form their designs.
This has to do with them being the authors of the _Curry_ language.

---

# Implementation

I had the idea to utilize ASTs for the reasons of refreshing my understanding of the fundamental theory and to investigate newer literature.
My hypothesis being to emulate a mathematicians chalk work on the problem of inversion as it applies to arithmetic functions.
In particular my algorithm is meant to solve the equation using similar intuition.
When a mathematician is given some function $f$ such that.

\begin{equation} \label{initial_f}
    f(x) = x + 5
\end{equation}

The first thing the mathematician examines is the structure of the equation.
Here in Eq \eqref{initial_f} it is clear that $f$ performs the addition operation on $x$ and the number $5$.
The inversion is trivially found to be $f^{-1}(x) = x - 5$ such that we have simply taken the inverse of all operations in Eq \eqref{initial_f}.
This thought prompted the idea that the *inverse of an arbitrary arithmetic function is the sum inverse of that functions parts*.
The testing for this proved it to be partially correct with the exception of edge cases where operations themselves are non-invertible.
Examples of these can be seen with any equation utilizing the _modulo_ operation.
Thus giving us our third axiom for this problem (further constraining the problem space).

\begin{equation}
    \text{Axiom 3: Arithmetic functions s.t the modulo operation is not present}
\end{equation}

It turns out (In my short study) that as long as all the operations in an arithmetic equation are invertible,
    then the over all inversion is possible.
Making this a kind of "sum of its parts" problem.
Using this intuition we can derive a trivial algorithm to solve an arbitrary equation bound by our $\text{Axioms}_{1-3}$.
Such an algorithm would seemingly just perform inversion on all operations (in place).

```haskell
AST :: lexeme | operation [children]

inv :: AST -> AST
inv lexeme  = lexeme
inv (op ls) = (inverse op) (map inv ls)

inverse :: operation -> operation
inverse op = op -- hard coded inversion
```

The above code symbolizes my version one design.
Upon thinking about the idea for a few hours I came to the conclusion this would not preserve order of operations.
So I came up with a version two of the code which does a BFS-traversal prior to inversion.
This ensures a snap shot of the current state of the AST given to inversion.
This snap shot will contain a unique id ordering for each node,
    providing a way to rearrange a test structure then apply the arrangement to the AST.
I plan on introducing a kind of verification step later,
    this architecture better allows that as well as providing the ability to preserve order.
It is the case that the algorithm remains primitive in its current form,
    this allows for the easiest proof of concept.
Given that the inversion function described above can be thought of as $I$ this is our second algorithm.

\begin{equation} \label{inv_2}
    I' = (I \circ BFS)(AST)
\end{equation}

It is the case that Eq \eqref{inv_2} represents our new inversion function.
In particular it is true that the inversion function will receive not an AST,
    but a BFS searched tree structure.
A change which makes unique rearrangement and verification possible <d-footnote>
    In theory the BFS tree will hold enough information to make verification possible.</d-footnote>

If you have only ever written a tree search algorithm in an imperative language I recommend using a function language once.
It is not fun to think about the problem without the use of pointers or at least boxes.
The code I came up with is neither optimal nor pretty,
    though it does have a certain functional beauty to it.

The pseudocode for BFS is well known, and the Haskell I wrote is viewable on my [Github repo](https://github.com/snowmang1/invertible-lang).

---

# Future

I feel that there is merit in exploring the outcomes of a verification system surrounding the inversion function.
As stated in the above sections I had a thought previously about inserting verification into this function.
I see several problems with this idea in the projects current state.
It is not obvious to me that one can create a programmatic structure for a proof of inversabilty.
Such that creating this structure for an arbitrary function might be asking to much (which is what makes it sound fun).
Such a structure would need to be powerful enough to differentiate between arithmetic functions and moving forward,
    geometric functions.
The future I see for this type of inversion verification might be closer to a user defined inversion definition system.
Thus a system where the user defines a function and its proper inverse function.
This allows our verification problem to be simplified into something of a logical verification.
In conclusion (because I am now thinking whilst I write) the planned future work for this project are as follows.

* API for user defined function $f$ and inverse $f^{-1}$
* Verification for inversion function purposed output
* Relaxing $Axiom 2$

#### Notes
This project served to get me into compiler like projects again in a non-academic sense.
Thus the main proponent of this project was to do some:
    reading,
    research,
    coding,
    and writing (thus my measly three references below).
I also used this post to start my blog;
    creating a reference for current students;
    lastly to begin a personal hobby of writing about my pet projects.

#### Finishing thoughts

In the event you read this and have any thoughts on the project,
    do not hesitate to  message me on Github or email me about it.
