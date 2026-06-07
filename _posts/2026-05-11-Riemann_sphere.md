---
layout: distill
title: Riemann Sphere's and Computability
description: article 
tags: Math
giscus_comments: false
date: 2026-05-11
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
tikzjax: true
typograms: false

authors: Evan Drake
url: "https://snowmang1.github.io/"
affiliations:
  name: Butte College

bibliography: 2026-05-11-Riemann_sphere.bib

citation: true

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).
toc:
  - name: Introduction
  - name: Background
  - subsections:
    - name: Riemann Sphere
    - name: Computable analysis
  - name: Computable Regions of Riemann sphere

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
Here I explore computable regions of the Riemann sphere $\hat{\mathbb{C}}$.
I begin with recalling that definition of $\hat{\mathbb{C}}$ from complex analysis,
    with particular emphasis on stereographic projection.
Then I examine computable analysis,
    in particular how computability is defined on complete separable metric spaces according to _TTE_.

# Background
I assume knowledge of $\mathbb{C}$.
In particular,
    I assume that readers understand the representation of complex numbers and basic arithmetic in $\mathbb{C}$.
I also assume knowledge of basic real analysis.

## Riemann Sphere
The Riemann sphere is that projection of the extended complex plane that allows for natural inverses of elements<d-cite key="needham"></d-cite>.
In particular the Riemann sphere ($\mathbb{S}^2$) is that sphere created when all points of $\mathbb{C}$ are mapped to the unit sphere via *stereographic projection*<d-cite key="needham"></d-cite>.
Stereographic projection describes the process of mapping a unit sphere (denoted $S$) to some plane.
Here we will assume the plane to be the extended complex plane $$\hat{\mathbb{C}}$$ or $\mathbb{C} \cup \infty$.
The inclusion of infinity allows descriptions of limits in $\mathbb{C}$ while via stereographic projection we can describe $$\hat{\mathbb{C}}$$ as a metric space<d-cite key="conway"></d-cite>.
In particular stereographic projection describes a sphere ($S$) at the origin of $$\hat{\mathbb{C}}$$ such that the plane bisects $S$ on its equator, see figure 1.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/single_z.svg"
    dark="/assets/img/tikz/stereographic_proj/single_z_light.svg"
    alt="Stereographic projection 3D fig"
    caption="Figure 1: Stereographic projection, 3D view"
%}

Using the north pole of $S$ denoted $N$, we can create a geometric intuition for distance among points of $$\hat{\mathbb{C}}$$.
Thus using stereographic projection we can describe a metric space on $$\hat{\mathbb{C}}$$, see <d-cite key="conway"></d-cite>.
This metric space is created by forming a straight, infinite line between $N$ and all points $$z \in \hat{\mathbb{C}}$$, see figure 2.
It is trivial to intuit that all but one of these lines will pass through the sphere again before reaching $$\hat{\mathbb{C}}$$.
In particular we label the intersection $Z$ in figure 2,
    the only value that will not produce an intersection point $Z$ is $$\infty \in \hat{\mathbb{C}}$$.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/profile.svg"
    dark="/assets/img/tikz/stereographic_proj/profile_light.svg"
    alt="Stereographic projection 2D fig"
    caption="Figure 2: Stereographic projection, 2D view"
%}

The metric space $(\hat{\mathbb{C}}, d)$ is defined in three dimensional space by the coordinate functions in Eq $\eqref{sphere-intersection-equations}$.
That is, Each point $Z$ on the sphere correlates to some point $z \in \mathbb{C}$;
    Such that $Z = (x_1, x_2, x_3)$.
Such a metric space necessitates the presence of a metric function $d$ defined by Eq $\eqref{sphere-d}$ <d-cite key="conway"></d-cite>.

$$
\begin{equation} \label{sphere-d}

d(z, z') = \frac{2|z - z'|}
{\sqrt{(1 + |z|^2)(1 + |z'|^2)}}, (z, z' \in \mathbb{C})

\end{equation}
$$

$$
\begin{equation} \label{sphere-intersection-equations}
\begin{aligned}
    x_1 &= \frac{z + \bar{z}}{|z|^2+1} \\
    x_2 &= \frac{-i(z - \bar{z})}{|z|^2+1} \\
    x_3 &= \frac{|z|^2-1}{|z|^2+1}
\end{aligned}
\end{equation}
$$

It is the case that there is only one point that does not produce an intersection.
In particular it should be the case that when $(z_n) \rightarrow \infty$ we should see the equation approach $N$.
As $N$ is located at $(0,0,1)$ in this orientation we can continue by testing each equation for $(z_n) \rightarrow \infty$.
That is when $(z_n) \rightarrow \infty$ we notice the following:
1. $x_1 \rightarrow 0$, as the numerator is lower order than the denominator.
2. $x_2 \rightarrow 0$, as the numerator is lower order than the denominator.
3. $x_3 \rightarrow 1$, as the numerator and denominator are of equivalent order.

The stereographic projection defines a formal metric space.
A metric space as defined in <d-cite key="conway"></d-cite>,
    is that space fulfilling the following requirements for the metric function $d$ and any points of the space $x,y,z$.

1. $d(x,y) \ge 0$
2. $d(x,y) = 0 \iff x = y$
3. $d(x,y) = d(y,x)$
4. $d(x,z) \le d(x,y) + d(y,z)$

In stereographic projection that metric $d$ is the defined via Eq $\eqref{sphere-d}$ between two points $Z_a$ and $Z_b$.

It is the case that $d$ is non-negative for any $z \in \mathbb{C}$.
That is the numerator is bound to a positive value multiplied by two and the denominator is addition of two square positive complex numbers.
Unless of course $z = z'$,
    which results in a zero numerator, thus zero.
The commutativity of $d$ is true,
    as the only problem would be the numerator term $2|z - z'|$.
In particular the absolute value term which will always result in an absolute measure, assuring commutativity.
The triangular inequality is given as $d$ inherits that those qualities of $\mathbb{R}^3$.

In the last section we showed stereographic projection to produce the description of a metric space over $$\hat{\mathbb{C}}$$.
Notice that we did this only through description of the sphere,
    not ignoring the plane but simply not needing to use it.
We call this particular sphere $S^2$ or the Riemann sphere,
    as it is that co-domain of the bijection between $$\hat{\mathbb{C}}$$ and $S^2$ derived from stereographic projection.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/riemann_sphere.svg"
    dark="/assets/img/tikz/stereographic_proj/riemann_sphere_light.svg"
    alt="Riemann sphere 3D"
    caption="Figure 3: Riemann sphere"
%}

Let us here after define a _region_ to be some open, connected subset of $S^2$.
In particular here I mean those open, connected subsets of a Riemann sphere.

## Computable analysis
_Computable analysis_ investigates those theorems and functions of classical analysis,
    with particular interest in their computability.
In particular we will find that their exists axioms of computability specifically tied to constructions of classical analysis.
It is with these axioms and theorems of computability that we will examine the Riemann sphere in coming sections.
The most basic idea in computability is that distinction of which math can be described as _computable_.
Thus we define computability as those mathematical constructions which can be described mechanistically <d-cite key="soare"></d-cite>.
In particular,
    we say these constructions are Turning-computable if they can be recreated using a Turing-machine or some equivalent logic <d-cite key="soare"></d-cite>.
In the case of analysis we normally find sets described by functions,
    thus we need a definition emphasizing sets and functions.
In particular,
    <d-cite key="brattka"></d-cite> calls a function computable if "every approximation of the output can be made using an approximation of the input".
We can infer that a computable function would describe an enumerable set.
More specifically an enumerable set is the set for which there exists a function that can enumerate it.
Notably we say that a set $A \subset \mathbb{N}$ is recursive if there exists a function which can decide if some element $k$ belongs in $A$ or not <d-cite key="brattka"></d-cite>.
We can also say that any _recursively enumerable_ set is computable,
    As there exists a function which can estimate the values of the set with some outputs.
The above is taken from basic computability,
    mostly assumed knowledge for discussing computable analysis.
Here will require definitions of computability as it pertains to non-discrete space.
In particular,
    Here we describe those computable regions of a Riemann sphere.
Notably the Riemann sphere is an object belonging to a continuous space,
    particularly $\mathbb{C}$.
To this end,
    I utilize prescribe to those theories found in _Type 2 theory of effectivity_ (TTE) <d-cite key="weihrauch_article"></d-cite> <d-cite key="weihrauch_book"></d-cite>.
In particular TTE has definitions specifically for metric spaces.
Concluding this section will be a list of basic theorems to do with computability.

1. Recursively enumerable sets are computable.
2. Functions are computable given there inputs can be estimated using their outputs.
3. Computability is defined using Turing-machine (or equivalent) logic in Discrete space.

# Computable Regions of Riemann sphere
Computability here, describes those processes which can be enumerated via mechanistic logic.
Thus for any given Region of the Riemann sphere ($\hat{\mathbb{C}}$) to be considered computable it would have to be describable in some mechanistic logic.
In particular it is true that such a region would need to be describable to a Turing machine <d-cite key="weihrauch_article"></d-cite>.
This would make that Region Turing computable.
It is the case that Turing machines exist only in discrete space,
    such that the infinite expansion (completeness) of continuous space is undefined within such a logic.
Thus to define such a region of $\hat{\mathbb{C}}$ to a Turing machine that region would notably need to be limited to a countable subset of $\hat{\mathbb{C}}$.
The above was my original thoughts on the problem,
    thankfully it seems I was wrong (sort of).
In particular, <d-cite key="weihrauch_article"></d-cite> <d-cite key="weihrauch_book"></d-cite>
    describes TTE as a form of logic making metric spaces computable.
That is TTE projects $\mathbb{N}$ onto such subsets $M$ of a metric space $X$ such that $\mathbb{N}$ is describable to Turing machine thus implying the computability $M$.
Under TTE, a computable metric space be defined as the following four tuple $$\bar{M} := (M, d, A, \alpha)$$:

1. $(M, d)$ the metric space
2. $A \subset M$, where $A$ is a dense subset
3. $\alpha : \mathbb{N} \rightarrow A$ is a total numbering of $A$
4. $$D_< : \{ \langle i,j,k \rangle \mid  d( \alpha (i), \alpha (j) ) < v_\mathbb{Q}(k) \} $$ is recursively enumerable

Note that the total numbers of $A$ is simply $\mathbb{N}$ projected onto the $A$,
    that is $A$ is a countable set.
The fourth rule is describing that the distance between any two elements,
    with relation to an associated numbering of the rationals.
In particular this rule is only accounting for a single side of the distance,
    allowing for arbitrary precision of distances <d-cite key="weihrauch_article"></d-cite>.
Notably we can also assume that the metric space on $\mathbb{R}$ is computable for a given $(\mathbb{R}, d, \mathbb{Q}, v_\mathbb{Q})$.
There exists a concept of computable continuous sets in <d-cite key="weihrauch_article"></d-cite>,
    though it seems to specific to use here.
Given the above four rules and the knowledge that $(\mathbb{R}, d, \mathbb{Q}, v_\mathbb{Q})$ is a computable metric space via <d-cite key="weihrauch_article"></d-cite>,
    we can begin an exploration.
Recall that $\hat{\mathbb{C}}$ is the metric space $(\Sigma, d)$ where $\Sigma$ is the sphere and $d$ describes those points in relation to each other on that sphere.
Given that the $\mathbb{R} \subset \mathbb{C} \implies \mathbb{R} \subset \hat{\mathbb{C}}$,
    such that if $\hat{\mathbb{C}}$ is a metric space with metric $d$ then there must exist $(\mathbb{R}, d) \subset \hat{\mathbb{C}}$.
In particular we know that there exist regions of $\hat{\mathbb{C}}$ which are completely contained inside $(\mathbb{R}, d)$.
Let us assume that such a sub-region of that metric space is dense in $(\mathbb{R}, d)$.
Further lets assume that it was $\mathbb{Q}$,
    this implies there exists an exact natural projection $\lambda : \mathbb{N} \rightarrow \mathbb{Q}$.
Thus that subregion could be assumed computable, via <d-cite key="weihrauch_article"></d-cite> and TTE.
This concludes my rather shallow exploration into computable regions of $\hat{\mathbb{C}}$.

# Thoughts and future work
As somewhat of a limitation my understanding of the theory of computability seems to be lacking almost as much analysis.
Thus it is now a goal of mine to examine this again after expanding my understanding of the modern research in computability theory.
This work is incredibly interesting,
    due to the nature of computability.
Upon starting my research on mathematics in the continuous space (analysis) I believed computability to be impossible.
It was my understanding that computable algorithms were limited to discrete space strictly.
While it seems to be required to find natural projections to the domain,
    the rules seem to be less strict than I originally thought.
I think I will continue to investigate computability while working through <d-cite key="conway"></d-cite>, <d-cite key="needham"></d-cite>, and Lang's book (not cited here).
