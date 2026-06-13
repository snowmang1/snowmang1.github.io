---
layout: distill
title: Riemann Spheres and Computability
description: article 
tags: Math
giscus_comments: false
date: 2026-06-12
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
  - name: Background
    subsections:
      - name: Planes
      - name: Spheres
  - name: The Riemann sphere
  - name: Relations

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
Here I give an exposition of the Riemann sphere $$\widehat{\mathbb{C}}$$.
I begin with recalling that definition of the two-dimensional plane (namely $\mathbb{C}$),
    and the three-dimensional sphere.

# Background
## Planes
Recall the Cartesian coordinate system,
    that two axis system describing a two-dimensional plane.
Notice that representation of a Cartesian plane in figure 1.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/cart_plane_light.svg"
    dark="/assets/img/tikz/stereographic_proj/cart_plane_dark.svg"
    alt="Stereographic projection 3D fig"
    caption="Figure 1: Cartesian plane"
%}

I describe the complex field in this article as that plane created via the $$\mathbb{R}$$ and imaginary component ($$\mathbb{I}$$) of a complex number.
Notably the intuition is normally given as those perpendicular axis of a plane being represented as $$\mathbb{R}$$ and $$\mathbb{I}$$<d-cite key="lang"></d-cite>.
In particular,
    we can now take any complex number $z = a + bi$ and index that number within $$\mathbb{C}$$ using this technique.
This of course relying on that fact that for any plane we can index a single point of that plane using a two-tuple, some $(x,y)$.
Thus some $MxM$ plane includes all those points inside of that $MxM$ space.

## Spheres
A sphere as we can see from figure 4 is that shape containing no "edges" in the three-dimensional space.
Being in a three-dimensional space describing a single point of any sphere requires a three-tuple, some $(x,y,z)$.
That is a sphere contains those points lying not only on its surface but those contained inside the extrema as well.
Note that some point $(x,y,z)$ need not always be located on a surface.
In the context of the discussion that follows,
    note that a fundamental rule of three-dimensionality is that the sphere contains those points within itself.
In particular,
    if the sphere did not contain those points within or if those points where unreachable then that sphere could be thought of as two dimensional.
That is the sphere itself could be treated as a two-dimensional surface,
    commonly referred to as $S^2$.

<!-- TODO: write a short section that outlines how the complex plane is defined and why -->
## The complex plane

<!-- TODO: write a short section that outlines how we define a metric space -->
## Metric space

# Riemann rewrite

<!-- TODO: Review and change this section to match nomenclature and style. -->
# The Riemann Sphere
The Riemann sphere is that projection of the extended complex plane that allows for natural inverses of elements<d-cite key="needham"></d-cite>.
In particular the Riemann sphere ($\mathbb{S}^2$) is that sphere created when all points of $\mathbb{C}$ are mapped to the unit sphere via *stereographic projection*<d-cite key="needham"></d-cite>.
Stereographic projection describes the process of mapping a unit sphere (denoted $S$) to some plane.
Here we will assume the plane to be the extended complex plane $$\widehat{\mathbb{C}}$$ or $\mathbb{C} \cup \infty$.
The inclusion of infinity allows descriptions of limits in $\mathbb{C}$ while via stereographic projection we can describe $$\widehat{\mathbb{C}}$$ as a metric space<d-cite key="conway"></d-cite>.
In particular stereographic projection describes a sphere ($S$) at the origin of $$\widehat{\mathbb{C}}$$ such that the plane bisects $S$ on its equator, see figure 1.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/single_z.svg"
    dark="/assets/img/tikz/stereographic_proj/single_z_light.svg"
    alt="Stereographic projection 3D fig"
    caption="Figure 2: Stereographic projection, 3D view"
%}

Using the north pole of $S$ denoted $N$, we can create a geometric intuition for distance among points of $$\widehat{\mathbb{C}}$$.
Thus using stereographic projection we can describe a metric space on $$\widehat{\mathbb{C}}$$, see <d-cite key="conway"></d-cite>.
This metric space is created by forming a straight, infinite line between $N$ and all points $$z \in \widehat{\mathbb{C}}$$, see figure 2.
It is trivial to intuit that all but one of these lines will pass through the sphere again before reaching $$\widehat{\mathbb{C}}$$.
In particular we label the intersection $Z$ in figure 2,
    the only value that will not produce an intersection point $Z$ is $$\infty \in \widehat{\mathbb{C}}$$.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/profile.svg"
    dark="/assets/img/tikz/stereographic_proj/profile_light.svg"
    alt="Stereographic projection 2D fig"
    caption="Figure 3: Stereographic projection, 2D view"
%}

The metric space $(\widehat{\mathbb{C}}, d)$ is defined in three dimensional space by the coordinate functions in Eq $\eqref{sphere-intersection-equations}$.
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

In the last section we showed stereographic projection to produce the description of a metric space over $$\widehat{\mathbb{C}}$$.
Notice that we did this only through description of the sphere,
    not ignoring the plane but simply not needing to use it.
We call this particular sphere $S^2$ or the Riemann sphere,
    as it defined by that bijection between $$\widehat{\mathbb{C}}$$ and $S^2$ derived from stereographic projection.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/riemann_sphere.svg"
    dark="/assets/img/tikz/stereographic_proj/riemann_sphere_light.svg"
    alt="Riemann sphere 3D"
    caption="Figure 4: Riemann sphere"
%}

<!-- TODO: Write about the topology of S^2 with emphasis on open sets, neighborhoods, convergence to \infty, and the compactification of C. -->
# Relations
Here I will describe that topology of $$\widehat{\mathbb{C}}$$ in relation to that of $$\mathbb{C}$$.

# Nomenclature
- $$\mathbb{C}$$: symbol representing the complex field.
- $$\widehat{\mathbb{C}}$$: symbol representing the Riemann sphere.
- $$\mathbb{R}$$: symbol representing the real numbers.
