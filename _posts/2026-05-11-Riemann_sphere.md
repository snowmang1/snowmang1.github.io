---
layout: distill
title: Computable regions of a Riemann sphere
description:
tags: math computability
giscus_comments: false
date: 2026-05-11
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

<!-- ## Computable analysis -->
