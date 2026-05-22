---
layout: distill
title: Riemann Sphere's and Computability
description: article 
tags: math computability
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
Here I will strive to describe computable regions of a Riemann sphere.
In particular I will describe how we define computable in this context,
    and present what a Riemann sphere is in the context of complex analysis.
There is no small amount of contextual material to cover so I will begin by presenting background information in subsections.
In particular: what is a Riemann sphere; what do I mean by computable here; how do I describe a region of a Riemann sphere.

# Background
I assume knowledge of $\mathbb{C}$.
In particular,
    I assume that readers understand the representation of complex numbers and basic arithmetic in $\mathbb{C}$.
I also assume familiarity with $\epsilon - \delta$ proofs and real analysis.

## Riemann Sphere
The Riemann sphere is that projection of the extended complex plain that allows for natural inverses of elements<d-cite key="needham"></d-cite>.
In particular the Riemann sphere ($\mathbb{S}^2$) is that sphere created when all points of $\mathbb{C}$ are mapped to the unit sphere via *stereographic projection*<d-cite key="needham"></d-cite>.
Stereographic projection describes the process of mapping a unit sphere (denoted $S$) to some plane.
Here we will assume the plane to be the extended complex plane $$\mathbb{C}_\infty$$ or $\mathbb{C} \cup \infty$.
The inclusion of infinity allows descriptions of limits in $\mathbb{C}$ while via stereographic projection we can describe $$\mathbb{C}_\infty$$ as a metric space<d-cite key="conway"></d-cite>.
In particular stereographic projection describes a sphere ($S$) at the origin of $$\mathbb{C}_\infty$$ such that the plane bisects $S$ on its equator, see figure 1.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/single_z.svg"
    dark="/assets/img/tikz/stereographic_proj/single_z_light.svg"
    alt="Stereographic projection 3D fig"
    caption="Figure 1: Stereographic projection, 3D view"
%}

Using the north pole of $S$ denoted $N$, we can create a geometric intuition for distance among points of $$\mathbb{C}_\infty$$.
Thus using stereographic projection we can describe a metric space on $$\mathbb{C}_\infty$$, see <d-cite key="conway"></d-cite>.
This metric space is created by forming a straight, infinite line between $N$ and all points $$z \in \mathbb{C}_\infty$$, see figure 2.
It is trivial to intuit that all but one of these lines will pass through the sphere again before reaching $$\mathbb{C}_\infty$$.
In particular we label the intersection $Z$ in figure 2,
    the only value that will not produce an intersection point $Z$ is $$\infty \in \mathbb{C}_\infty$$.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/profile.svg"
    dark="/assets/img/tikz/stereographic_proj/profile_light.svg"
    alt="Stereographic projection 2D fig"
    caption="Figure 2: Stereographic projection, 2D view"
%}

The arc length distance between different intersections is what forms the metric space.
In particular,
    it is the difference between any point $Z_a$ and $Z_b$ that defines our metric space on $$\mathbb{C}_\infty$$ <d-cite key="conway"></d-cite>.
We can calculate the position of any $Z$ given the associated point $z$ with the following equations, noting $Z = (x_1, x_2, x_3)$.

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
In particular it should be the case that when $z = \infty$ we should see the equation approach $N$.
As $N$ is located at $(0,0,1)$ in this orientation we can continue by testing each equation for $z = \infty$.
In the case of $x_1$ note that for any complex number $a$, we have $|a|^2 >> a + \bar{a}$.
It is trivial then trivial that $x_2$ is approaches zero when $z = \infty$.
It is not so clear in the case of $x_3$,
    we have to show that $|a|^2 - 1 \rightarrow b$ and $|a|^2 + 1 \rightarrow b$.
This of course is trivial as when $a$ becomes large the difference and addition of $1$ will be negligible.

The stereographic projection defines a formal metric space.
A metric space as defined in <d-cite key="conway"></d-cite>,
    is that space fulfilling the following requirements for the metric function $d$ and any points of the space $x,y,z$.

1. $d(x,y) \ge 0$
2. $d(x,y) = 0 \iff x = y$
3. $d(x,y) = d(y,x)$
4. $d(x,z) \le d(x,y) + d(y,z)$

In stereographic projection that metric $d$ is the defined as the arc length between two points $Z_a$ and $Z_b$.
Distance can not be negative,
    distance in terms of subtractions thus $x - y = 0 \implies x = y$,
    and arc length between points on a sphere is commutative.
The triangular inequality is less simple to prove but as this is distance in euclidean space,
    In particular $S^2$ we can assume its truth without an elaborate proof.

In the last section we showed stereographic projection to produce the description of a metric space over $$\mathbb{C}_\infty$$.
Notice that we did this only through description of the sphere,
    not ignoring the plane but simply not needing to use it.
We call this particular sphere $S^2$ or the Riemann sphere,
    as it is that sphere containing all points of $$\mathbb{C}_\infty$$ derived from stereographic projection.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/riemann_sphere.svg"
    dark="/assets/img/tikz/stereographic_proj/riemann_sphere_light.svg"
    alt="Riemann sphere 3D"
    caption="Figure 3: Riemann sphere"
%}

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
Computability describes those processes which can be described via mechanistic logic.
Thus for any given Region of the Riemann sphere ($\hat{\mathbb{C}}$) to be considered computable it would have to be describable in some mechanistic logic.
In particular it is true that such a region would need to be describable to a Turing machine.
This would make that Region Turing computable.
It is the case that Turing machines exist only in discrete space,
    such that the infinite expansion (completeness) of continuous space is undefined within such a logic.
Thus to define such a region of $\hat{\mathbb{C}}$ to a Turing machine that region must be limited to a discrete subset of $\hat{\mathbb{C}}$.
The above was my original thoughts on the problem,
    thankfully it seems I was wrong.
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
Given the above four rules and the knowledge that $(\mathbb{R}, d, \mathbb{Q}, v_\mathbb{Q})$ is a computable metric space,
    we can begin an investigation.
Recall that $\hat{\mathbb{C}}$ is the metric space $(\Sigma, d)$ where $\Sigma$ is the sphere and $d$ describes those points in relation to each other on that sphere.
Given that the $\mathbb{R} \subset \mathbb{C} \implies \mathbb{R} \subset \hat{\mathbb{C}}$,
    such that if $\hat{\mathbb{C}}$ is a metric space with metric $d$ then there must exist $(\mathbb{R}, d) \subset \hat{\mathbb{C}}$.
In particular we know that there exist regions of $\hat{\mathbb{C}}$ which are completely contained inside $(\mathbb{R}, d)$.
Let us assume that such a sub-region of that metric space is dense in $(\mathbb{R}, d)$.
Further lets assume that it was $\mathbb{Q}$,
    this implies there exists an exact natural projection $\lambda : \mathbb{N} \rightarrow \mathbb{Q}$.
Thus that subregion is computable$^\blacksquare$.

# Thoughts and future work
