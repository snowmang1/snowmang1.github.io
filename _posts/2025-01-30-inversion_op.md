---
layout: distill
title: Inversion Operation
description: article about a simple arithmetic inversion operation utilizing a standard AST
tags: compilers programming
giscus_comments: false
date: 2025-01-30
featured: true
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
    # if a section has subsections, you can add them as follows:
    # subsections:
    #   - name: Example Child Subsection 1
    #   - name: Example Child Subsection 2
  - name: References

# Below is an example of injecting additional post-specific styles.
# If you use this post as a template, delete this _styles block.
# _styles:
# Can be used for custom style elements
---

# Introduction / Hypothesis

For the past couple of months I have been fixated on learning the field of topology as a kind of hobby.
In that time the use of inverse function $f^-1$ has caught my eye.
This kind of notation is seen often to describe the inverse of a function $f$, especially in <d-cite key="munkres_topo" ></d-cite>.
I became curious whether this kind of operation was as automatic in computer science.
My favorite languages these days being: Lean4 and Haskell I have gotten all to use to maths being built into a language.
As it turns out things like inversion functions are not common in CS at least not *automatic inversabilty* as seen in the notation $f^-1$.
It may be unclear what I mean by automatic inversabilty at this point, I will go into detail later.
There is a literature examining this very topic and I read some of those papers which I will again discuss below.
Once I found that this topic was not common enough to have been widely addressed in the non-academic space I got curious about difficulty.
How hard could it be to create a system within a compiler that could,
    in theory take any function and give you its inverse.
This is where I started of course I found that it could be incredibly difficult.
My hypothesis was simple,
    I needed to create a program that could create an inverse function automatically while limiting the resources to simulate that of a simple compiler.
I decided to limit myself to a basic AST structure that kept no real metadata but simply the lexemes and some type information.
That was the structure that would take and create an inverse function with,
    I weakened my initial statement and assumed an interpreted language so that I could still use Haskell for the experiment.
I felt it may take longer than I would like if I used something else (and Haskell is so fun to use so I thought).
Some basic pseudocode I drew up for the project before starting.

<d-code>
Node : Operation or Lexeme
AST : Node []
-- where the AST is a tree with node equal to an operation or lexeme

f : AST -> AST
f (node []) = invert node -- leaf case
f (node ls) = AST (invert node) (map f ls)
-- f would invert the AST meaning to take the inverse of each piece recursively
-- assume that the inverse of any AST is the inverse of its parts
</d-code>

I have some initial problems with this approach.
First simply mapping $f$ over all children is begging for a stack overflow.
Secondly is my assumption that the inverse of any function body AST (thus the inverse of any function) is constructed via the inverse of its parts?
I convinced myself that speed optimization could wait until after I had seen if the idea could work.
The assumption did have me worried,
    thus I constrained the math to arithmetic where I found only edge cases where my assumption was untrue.
The edge cases though difficult to ignore can be countered with constraints.
Our problem space is currently bound by the following.

\begin{equation}
    \text{Assumption 1: } AST^{-1} = [x \in AST | \sum x_i^{-1}]
\end{equation}

\begin{equation}
    \text{Assumption 2: Arithmetic space only}
\end{equation}

---

# Literature

---

# Implementation

---

# Problems with the initial setup
