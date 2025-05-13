---
layout: distill
title: Induction
description: A look at inductive proofs
tags: Math
giscus_comments: false
date: 2025-04-19
featured: true
mermaid:
  enabled: false
  zoomable: false
code_diff: false
map: true
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

bibliography: 2025-04-19-induction.bib

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).
toc:
  - name: Introduction
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
The most interesting and complex puzzles we as humans can describe are defined in advanced mathematics
    <d-footnote> Worth noting that this is a personal opinion not a fact </d-footnote>.
We tackle these puzzles using the axioms of mathematics and logical language defined by proof theory.
It is proof theory that I am reviewing right now in an attempt to cement my understanding of different proofing methods.
In particular that of induction caught my interest (Enough to write a paper about it).
The model of proofing known as induction is not unique to mathematics,
    It has been used in philosophy as a kind of argument strategy in an obscured fashion.
Here I will (attempt) to focus solely on the mathematical method of proof,
    as the philosophical equivalent seems less rigorously defined.

# What is mathematical induction

# The history of mathematical induction
It is evident from previous research that the exact inventor of the mathematical induction method is debated.
Here I examine each debated inventor (or first user) and their influence on the method.
## Maurolycus
Born in the late thirteenth century Francesco Maurolico is not only a talented mathematician,
    but the master of mint, head architect of defences, and a professor in Sicily<d-cite key="enc_maurolico"></d-cite>.
For the remainder of this paper I will use the Latin translation of his name _Maurolycus_ as this is the version used by historic mathematicians.
It is said by Bussey in <d-cite key="bussey_1917"></d-cite> that Georg Cantor named Maurolycus as using the proof technique of induction first.
The exact quote used by Bussey from Cantor:

> Mr. G. Vacca pointed out that Maurolycus had already described
> the method in detail and used it in his Arithmetic of 1575. However,
> Pascal was the first to take it from Maurolycus. There can be no doubt
> about this, since in 1659 Pascal explicitly cited Maurolycus, who had
> proved this very theorem by means of complete induction.
> (translated from German to English)

\begin{equation}\label{maurolycus_simple}
    2 (\frac{n(n+1)}{2}) - n = n^2
\end{equation}

Here Cantor makes reference to Eq \eqref{maurolycus_simple} that was in a Pascal article siting Maurolycus.
A  rigorouse examination of work by Maurolycus is present in <d-cite key="bussey_1917"></d-cite>,
    its a rather interesting article with far to much depth for a blog post.

## Gersonides
An interesting and rather isolated theory from <d-cite key="rabinovitch_1970"></d-cite> is that induction was first used by _Rabbi Levi ben Gershon_.
Known to me only as his Greek translated name Gersonides,
    Levi ben Gershon is a French-Jewish philosopher from the early fourteenth century<d-cite key="tamar_2020"></d-cite>.
Work from Gersonides is presented in <d-cite key="rabinovitch_1970"></d-cite> pointing to his use of induction in the proof of mathematical theorems.
In particular proposition 63 of the _Maasei Hoshev_ which describes a method of determining the number of permutations of sets.

>Proposition 63: the number of permutations of a given number of different elements be some fixed number,
>$P_n$ then the permutations of a set of different elements numbering one more than the given number are
>as many as the  product of the former number of permutations by the successor to the given number.

While the proof of this proposition is not provided it is stated that the use of induction is implied.
In particular the definition of proof by induction is weakened in the beginning of <d-cite key="rabinovitch_1970"></d-cite>.
Stating that older proofs often used "quasi general" inductive techniques,
    or proofs that only worked for select cases<d-footnote>
    This seems normal to me as theorems start by examining special cases then becoming more general over time.</d-footnote>.
If these quasi general processes are used knowingly it is not made obvious to the reader in <d-cite key="rabinovitch_1970"></d-cite>.
In fact there is indication that the quasi general induction is a symptom of older notation.
The notation used by Gersonides for instance is not powerful enough to represent sequential elements of a set.

$$
\begin{equation} \label{eq:modern-note}
    \begin{split}
        S &\leftarrow \{ 0,1,2,3,4,5, \dots \}, \quad n &\in \mathbb{N} \\
        S_n &\in S \implies S_{n+1} \in S
    \end{split}
\end{equation}
$$

We see in equation \eqref{eq:modern-note} our notation is powerful enough to define a set and then define unique elements of that set abstractly.
This is seen in $S_n$ representing some nth element of the set $S$.
Knowing that $S$ is the set $$ \mathbb{N}_0 $$
    <d-footnote> no good argument has been brought to me presenting the natural numbers as including zero thus
        $mathbb{N}_0$ is the set of natural numbers with the edition of zero.</d-footnote>
    this implies $S_{n+1}$ is the subsequent element to $S_n$ which by definition is included in $S$.

The same statement in the notation Gersonides is described using is thus:
_Given a set $S$ such that it contains the natural numbers and zero.
We can infer that any element $m$ of this set $S$ has a subsequent element $n$ also contained in $S$._
The idea of abstracting the elements of sets into separate simply indexable space such as $S_0, S_1, S_2$,
    came later.
In particular in the writings of Gersonides each element in question required a unique identifier such as $m$ or $n$.
It is obvious why this would become cumbersome during a procedure such as induction.
Thus <d-cite key="rabinovitch_1970"></d-cite> describes the methods used as inductive in nature regardless of their quasi generality.
We see in <d-cite key="rabinovitch_1970"></d-cite> that Maurolycus reviewed Gersonides work stating:

> With great liberality, the procedure may perhaps be called complete induction,
> although the peculiar formal structure of complete induction is missing
> (translated using Google translate)

This is to say that Gersonides technique of "rising step-by-step" or _Hadragah_ is similar to the process of complete induction as a recursive process.
In particular it is a process of continuously proving sequential events inferring a proposition,
    without the rigorous structure of complete induction.

## Pascal
Blaise Pascal is a mathematician from the mid seventeenth century <d-cite key="ernest_1982"></d-cite>.
The inventor of Pascals triangle which explores different orders of figurate numbers,
    that is orders of binomial coefficients <d-cite key="lodder_2017"></d-cite>.
It is in the paper _Trait ́e du triangle arithm ́etique_ that we find Pascal using the technique of complete induction <d-cite key="bussey_1917"></d-cite>.
I would be remiss not to explore Pascals triangle,
    thus allow me a mild tangent here to describe the genius that is Pascals triangle.

### The Triangle
The structure itself is well known however some of the intricacies eluded either my memory or my education.
The triangle is designed to describe figurate numbers<d-cite key="lodder_2017"></d-cite>.

> [F]igurate numbers count the number of dots in regularly shaped figures, such as line segments, triangles, pyramids, etc. <d-cite key="lodder_2017"></d-cite> 

It is these numbers that form Pascal refers to as "orders" of numbers and we describe as dimensions.
Figurate numbers can be found in any dimension ($lim_{0\to\infty}$),
    thus requiring a recursive definition.
We can describe the first three orders here.

* Numbers of the first order represent the _dots_ of a shape in a single dimension and thus are all a unit or $$ \{1,1,1,1,1\} $$
* Numbers of the second order represent the _dots_ of a shape in two dimensions and thus are the natural numbers $\mathbb{N}$
* Numbers of the third order represent the _dots_ of a shape in three dimensions and thus are the triangular numbers $$ \{1,3,6,10\} $$

Pascals triangle describes all of these in a recursive definition dependent on the structure of the triangle and the _generator_.
In particular the _generator_ is the first number inserted into the triangle that will act as the value of the unit.
All other numbers of the triangle are a sum of the numbers preceding them either row or column independent.
We can describe any (non-extrema) index of the triangle as a cell.
In particular we can think of all these cells in the structure of a matrix.
Thus the formula for creation of each new cell ($C$) is described by Eq \eqref{pascal_formula}.

$$
\begin{equation} \label{pascal_formula}
C_{n,m} = A_{n-1,m} + B_{n,m-1}
\end{equation}
$$

### Use of induction

Returning to our original point that Pascal used complete induction to prove that the formula for his triangle would always create figurate numbers.
The evidence for this can be found in Pascals _twelfth consequence_<d-cite key="bussey_1917"></d-cite>.
In particular the twelfth consequence states precisely that the triangle will always produce figurate numbers.
In the treatise mentioned above Pascal described consequences of the triangle,
    these are better thought of today as intricacies of his triangle.
In fact the first few consequences (namely one through three) seem to state the obvious.
In the twelfth consequence described in <d-cite key="lodder_2017"></d-cite>,
    Pascal forms a proper complete induction structure based around the relation of certain elements.

>In every arithmetical triangle, of two contiguous cells in the same base the upper is to the lower as the
>number of cells from the upper to the top of the base is to the number of cells from the lower to the
>bottom of the base, inclusive<d-cite key="lodder_2017"></d-cite>.

Pascal refers to a base here as a subset of numbers within the triangle itself.
For more clarity I have included an image of pascals triangle below,
    taken from <d-cite key="lodder_2017"></d-cite>.

{% include figure.liquid loading="eager" path="assets/img/pascals_triangle.png" class="img-fluid rounded z-depth-1" zoomable=true %}

In Pascals triangle we can see a diagonal set of lines from one extrema to another.
A single example of this line can be seen in the line $\lambda , D$,
    This line is describing a single base.
In particular for the base described by $\lambda, D$,
    its contents are shown as $$ \{ D, B, \theta, \lambda \} $$.
Thus Pascal is stating that the relation between any two contiguous elements of a single base is dependent on their distance from their respective extrema.

$$
\begin{equation}
    \begin{split}
        A = \{ D, B, \theta, \lambda \} \\
        B : \theta \triangleq 1 : 1
    \end{split}
\end{equation}
$$

This makes sense given that $B \& \theta$ are reciprocals,
    values pascals describes as always being equal.
With a similar example Pascals base case is proven.
The next step is somewhat tricky as one must assume something not so obvious (the tool of complete induction).
He goes on to say that the rule follows in the next base (an obvious truth).
Then he states that necessarily if the rule is true at any base, it must be true at its successor.

> [T]hat if this proportion is found in any base, it will necessarily be found in the following base. <d-cite key="lodder_2017"></d-cite>

This supposes that if one can prove that its true for some base $x$ then it will by definition be true for all subsequent bases of $x$.
The final pieces of the proof are predictable and unimportant to this paper, as it discourages you from reading <d-cite key="lodder_2017"></d-cite>.

## Fermat


## Peano

# References
<dt-appendix></dt-appendix> 
