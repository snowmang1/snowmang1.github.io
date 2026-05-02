---
layout: distill
title: The Completeness Axiom
description: A shallow investigation of a single axiom of the Real numbers leading to a realization about the Complex numbers
tags: math set-theory
giscus_comments: false
date: 2026-03-28
featured: true
mermaid:
  enabled: true
  zoomable: true
code_diff: false
map: true
chart:
  chartjs: false
  echarts: false
  vega_lite: false
tikzjax: true
typograms: false

authors:
    - name: Evan Drake
      url: "https://snowmang1.github.io/"
      affiliations:
        name: Butte College

bibliography: 2026-03-28-number_line.bib

citation: true

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).
toc:
  - name: Abstract
  - name: Introduction
  - name: Cantor's Cauchy sets
  - name: Dedekind's cuts
    # if a section has subsections, you can add them as follows:
    # subsections:
    #   - name: Example Child Subsection 1
    #   - name: Example Child Subsection 2

# Below is an example of injecting additional post-specific styles.
# If you use this post as a template, delete this _styles block.
# _styles:
# Can be used for custom style elements
---
# Abstract
<!-- <d-cite key="noguchi"></d-cite> -->
<!-- <d-cite key="washington_cuts"></d-cite> -->
<!-- <d-cite key="richmond"></d-cite> -->
<!-- <d-cite key="cummings"></d-cite> -->

It is the case that the numbers we as mathematicians use constantly have no gaps in measurable distance
    between sequential elements.
Why is this the case?
In particular why is it obvious that the numbers used for (almost) all of mathematics provably have no measurable gaps.
I have made it my business to relearn analysis in more depth and I found myself coming back to this question.
There is an axiom of completeness associated with $\mathbb{R}$,
    necessarily this axiom is made obvious via any construction of $\mathbb{R}$.
Here I will investigate this central axiom and make an attempt to examine its finer details.
With this newly discovered intuition I investigate $\mathbb{C}$ to address the same question,
    with particular interest to the contrasting answer.

# Introduction
Intuition is key to every field of mathematics,
    one does more and more problems until their intuition blossoms.
If one builds their intuition upon assumptions that are not completely understood,
    this can be dangerous to later concepts.
Thus is the purpose of my investigation into $\mathbb{R}$.
The axiom did not entirely make sense to me which I found interesting enough to write about.
That axiom being the axiom of completeness for the real numbers.
This axioms states simply that the real numbers are complete,
    meaning there is no measurable gap between any two sequential elements.

\begin{equation} \label{comp-axiom}
    (\forall a, b \in \mathbb{R}) \land (\nexists c \in \mathbb{R} \mid a < c < b)
    \implies \forall \epsilon > 0, |a - b| < \epsilon
\end{equation}

It is particularly interesting that it is vacuously proven through both common constructions of $\mathbb{R}$.
Reading through <d-cite key="cummings"></d-cite> it becomes intuitive that the real numbers are complete.
However my intuition seemed semantically contaminated,
    building intuition atop naive trust in the author seemed irresponsible<d-footnote>
Though it does provide an interesting thought to the question of inductive learning. </d-footnote>.
Thus I stepped back once I finished my reading,
    I began to ask why the completeness axiom is obvious from a proof of construction.
The course of action from there somewhat obviously is to understand the various proofs of construction.
There exist two major construction methods Dedekind cuts and Cantor's Cauchy construction.
Digressing momentarily into the rational numbers and my point of curiosity,
    we then continue to the constructions.

# Rationals & My Quandary
When we intuit numbers in general we think of the naturals first (naturally).
These being the numbers beginning at one incrementing to infinity at a step of one.
After we have pondered the naturals for some time we can begin to understand,
    there exist natural<d-footnote>
        I can not help myself from making puns with natural numbers, apologies.</d-footnote>
    gaps between the natural numbers.
In particular, there is no numbers that exist to represent that expression $1 - 1$ or $1 - 2$.
Thus we discover both zero and the negative natural numbers<d-footnote> I am over simplifying it significantly </d-footnote>, $\mathbb{Z}$.
Once we have discovered $\mathbb{Z}$ our work begins to get rather interesting.
In discovering $\mathbb{Z}$ we have a ring closed under addition, subtraction, & multiplication;
    However, division presents a problem.
Thus we begin to create a definition of numbers which are closed under division,
    something describable in the following way.

\begin{equation} \label{rationals}
    \mathbb{Q} = \[ \frac{z}{n} \mid (\forall z \in \mathbb{Z})(\forall n \in \mathbb{N}) \]
\end{equation}

We observe from Eq. \eqref{rationals} that the rational numbers include the Integers and
    every fractional value between sequential Integers.
In the event that all numbers of a desired space are fractional $\mathbb{Q}$ presents no problem.
Once numbers such as $\pi$ and $e$ appear the problem becomes self-evident.
There does not exist a fractional form of these numbers.
Formally this concept is presented below in Eq. \eqref{rational problem}.

\begin{equation} \label{rational problem}
    (\forall a_{n},a_{n+1} \in \mathbb{Q} \mid a_{n} < a_{n+1}) (\nexists h \in \mathbb{Q} \mid a_{n} < h < a_{n+1})
    (\exists z \notin \mathbb{Q})
    \implies (a_{n} < z < a_{n+1})
\end{equation}

We observe that there exist numbers outside the Rational ring,
    numbers that exist measurably in the world.
Thus in an attempt to completely capture the numbers we can observe metrically we create another set of numbers.
A union of the Rationals designed above and those numbers which are not included in the rationals but can be detected.
The question now becomes how do we construct such a ring<d-footnote>
    Note I use the term "ring" loosely throughout the paper. As a proper definition is not assumed here. </d-footnote>
    of numbers?

# Cantor's Cauchy sets
Of the three constructions I present here this one makes the least sense to me.
Thus in perfect mathematics fashion I shall present it first.
The crux of Cantor's construction is the understanding of the Cauchy sequence.
Not a particular set but (at least in my mind) an attribute of a given set.

\begin{equation} \label{cauchy-seq}
    (\\{ a_n \\} \subset \mathbb{R})(\forall \epsilon > 0)(\exists N \in \mathbb{N}) \implies
    (|a_n - a_m| < \epsilon)(n,m > N)
\end{equation}

In Eq \eqref{cauchy-seq} we understand that a Cauchy sequence is one that after some element $a_n$ (assuming $n \le m$) changes very little.
That is all the elements of a Cauchy sequence after a particular element converge to the same number<d-cite key="rudin"></d-cite>.
This information is crucial to understand Cantor's construction in that his construction is built upon Cauchy sequences.
If one is to construct the real numbers,
    one is particularly interested in proving the existence of the irrational numbers with respect to $\mathbb{Q}$.
In particular this means the goal of any good construction is the proof of the *least-upper-bound*.
Cauchy sequences have a natural bounding,
    note by Eq \eqref{cauchy-seq} there exists some element $a_n$ by which $a_n + 1$ is not in the sequence.
In particular there exists a set $S$ such that all elements of $S$ are upper bounds of our Cauchy sequence.
That is all $x \in S$ exist such that $x$ is larger than all elements of our Cauchy sequence.
Assume $S$ to be ordered, thus there exists a minimum value of the sequence $S$.
The existence of this minimum value implies the existence of our *least-upper-bound* property.
Given the *least-upper-bound* property or the supremum we can begin work on finding the irrationals.
Given all Rational Cauchy sequences,
    we can conclude that we have the Cauchy sequences which approach the irrational numbers<d-cite key="barker"></d-cite>.

$$
\begin{equation}
    (\exists (c_n) \subset \mathbb{Q})(sup(c_n) \notin \mathbb{Q})
\end{equation}
$$

Thus by including those supremums of these sequences we can provably include all irrational values.
This is of course an oversimplification, _c'est la vie_.
Thus we can conclusively prove the completeness of $\mathbb{R}$ such that we include all rational Cauchy sequences and their respective supremum.
With this construction it should be logically impossible to have gaps in the number line.
A colloquial analogy might look something like this: "if you stand in a room with limited light,
    take into account first what you can see,
    then use what you can see to infer whats between what you can see and the walls"
    <d-footnote> while naive this was a helpful thought for me </d-footnote>.

# Dedekind's cuts
draw a line

<script type="text/tikz">
\begin{document}
  \begin{tikzpicture}
      \draw[->, thick] (-2.5,0) -- (2.5,0) {Re};
      \draw[->, thick] (0,-2.5) -- (0,2.5) {Im};
  \end{tikzpicture}
\end{document}
</script>

# Weierstrass construction

# References
<dt-appendix></dt-appendix>
