---
layout: distill
title: The Riemann sphere
description: description of the Riemann sphere with emphasis on how it is derived from the complex plane.
tags: Math
giscus_comments: false
date: 2026-06-13
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

authors: Evan Drake
url: "https://snowmang1.github.io/"
affiliations:
  name: Butte College

bibliography: 2026-06-13-The_Riemann_Sphere.bib

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
      - name: The complex plane
      - name: Metric spaces
  - name: The Riemann sphere
    subsections:
      - name: Intuition
      - name: Stereographic projection
  - name: Relations
  - name: Nomenclature
  - name: References

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
Notably the intuition is normally given as those perpendicular axis of a plane being represented as $$\mathbb{R}$$ and $$\mathbb{I}$$ <d-cite key="lang"></d-cite>.
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
## Metric spaces

# The Riemann sphere
## Intuition
It is common in analysis and further,
    topology to consider transformations with respect to $\infty$.
Given the above section on $\mathbb{C}$ we can safely assume this is a problem given the finiteness of $\mathbb{C}$.
Thus we create the extended complex plane from <d-cite key="conway"></d-cite> $$\mathbb{C}_\infty := \mathbb{C} \cup \{ \infty \}$$.
The addition of $\infty$ is only useful given we can place it in relation to other values,
    thus we require the creation of a metric space.
It is tempting to consider a simple euclidean distance metric,
    geometrically this does not work as the ends of the plane now tend towards a single point, $\infty$.
In particular it must be true that though the ends of the plane tend to $\infty$,
    they can never reach it.
This implies a need for a metric that will both give that distance between points,
    while not allowing any point to be finitely close to the singularity $\infty$.
Thus we use _stereographic projection_ as the metric function on $$\mathbb{C}_\infty$$.

## Stereographic projection
Stereographic projection describes a technique for relating a unit sphere to some plane,
    such that each point of the plane is related to a fixed point on the sphere.
Let the spheres orientation be fixed such that a north most point $N$ can be fixed as the north pole at location $(0,0,1)$.
We can see a two dimensional representation of this in figure 2.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/profile_light.svg"
    dark="/assets/img/tikz/stereographic_proj/profile_dark.svg"
    alt="Stereographic projection 2D view"
    caption="Figure 2: 2D stereographic projection"
%}

Mapping those points of the plane $$\mathbb{C}_\infty$$ to some points on the sphere $S^2$,
    requires we use out reference point and a straight line.
In particular if we take any point on the plane and induce a line through the fixed point $N$,
    it is the case the almost all the lines will pass through the surface of the sphere at some point other than $N$.
This is untrue of $\infty$ for reasons we will explore later.
That is if we consider stereographic projection to be some function $f: \mathbb{C}_\infty \rightarrow S^2$.
In particular we can define $f$ by Eq $eqref{eq:stereo_mapping}$.

$$
\begin{equation} \label{eq:stereo_mapping}
f(z) = (\frac{z + \bar{z}}{|z|^2 + 1}, \frac{-i(z - \bar{z})}{|z|^2 + 1}, \frac{|z|^2 - 1}{|z|^2 + 1})
\end{equation}
$$

Notice that as $z \in \mathbb{C}_\infty$ approaches $\infty$ the value $f(z)$ will tend toward $N$.
In particular paying attention to the order of each coordinates fraction as $z$ approaches $\infty$ the coordinates tend to $(0, 0, 1)$ or $N$.
A line from $\infty$ would be infinitely far from the sphere and thus form a tangent line on $N$.
Note $f$ is a bijection here.

_Proof_. To show that any function is bijective one must prove that the given function is both surjective and injective.
Assume $f$ is not surjective, then there must exist a $z$ such that $f(z) = DNE$.
The only way this could be true is if the denominator of some coordinate could be zero,
    $|z|^2$ can be neither zero nor negative.
Thus it is impossible for any denominator of the coordinate equations to be zero so $f$ is surjective.
Assume $f$ is not injective, then there must exist some $z_1, z_2 \in \mathbb{C}_\infty : (z_1 \ne z_2) \land (f(z_1) = f(z_2))$.
For those points the following must be true:

$$
\begin{equation} \label{eq:z1_z2}
\begin{split}
    \frac{|z_1|^2 - 1}{|z_1|^2 + 1} &= \frac{|z_2|^2 - 1}{|z_2|^2 + 1} \\
    (|z_1|^2 - 1)(|z_2|^2 + 1) &= (|z_2|^2 - 1)(|z_1|^2 + 1) \\
    (|z_1|^2 |z_2|^2 - |z_2|^2 + |z_1|^2) &= (|z_1|^2 |z_2|^2 - |z_1|^2 + |z_2|^2) \\
    (|z_1|^2 |z_2|^2 + 2|z_1|^2) &= (|z_1|^2 |z_2|^2 + 2|z_2|^2)
\end{split}
\end{equation}
$$

We find the Eq $\eqref{eq:z1_z2}$ describes a contradiction as the only way for $f(z_1) = f(z_2)$ is that $z_1 = z_2$,
    therefore $f$ is injective$^\blacksquare$.

## Chordal Metric on $$S^2$$
Here I will describe that metric that allows us to formulate the distance between two points of $S^2$.
I accomplish this using that metric space $\widehat{\mathbb{C}} := (S^2, d)$ where the function $d$ is the _chordal distance_.
That is the euclidean distance between two points on the surface of the sphere <d-cite key="conway"></d-cite>.
Here I will use those points of $\mathbb{C}_\infty$ assuming stereographic projection of those points.
That is those $z, z'$ points of this metric function $d$ will be defined as points of the complex plane,
    rather than those direct mappings of $S^2$.
This is legal due to stereographic projection being a homeomorphism,
    which I describe later in detail.
Notably Eq $\eqref{eq:chordal_dist}$ is taken from <d-cite key="conway"></d-cite>,
    however starting from the euclidean distance on $\mathbb{R}^3$ and adjusting for Eq $\eqref{eq:stereo_mapping}$ one can derive it themselves simply.
It is necessary to prove that any metric $d$ in fact follows those axioms of a metric space.

$$
\begin{equation} \label{eq:chordal_dist}
    d(z,z') = \frac{2|z - z'|}{\sqrt{(1 + |z|^2)(1 + |z'|^2)}}
\end{equation}
$$

_Proposition_. $$d(z,z') \ge 0, \forall z,z' \in \mathbb{C}_\infty$$<d-footnote>
    As the equation is derived from euclidean distance on $\mathbb{R}^3$ the contradiction is absurd.
    </d-footnote>.

_Proof_. The first requirement is $$d(z,z') \ge 0, \forall z,z' \in \mathbb{C}_\infty$$.
Assume $$\exists z, z_0 \in \mathbb{C}_\infty$$ such that $d(z,z_0) < 0$.
If such a $z_0$ did exist there is two cases that would result in $d(z,z_0) < 0$.
_Case one_: The numerator of the fraction becomes negative while the denominator remains positive,
    this is an impossibility.
_Case two_: The denominator of the fraction becomes negative while the numerator remains positive,
    this is an impossibility.
Thus the outcome of the function $d$ must always be positive or zero$^\blacksquare$.

_Proposition_. $d(z, z') = 0 \iff z = z'$.

_Proof_. Assume $$\exists z, z_0 \in \mathbb{C}_\infty$$ such that $(z \ne z_0) \land (d(z,z_0) = 0)$.
Given the denominator of a fraction can not be zero,
    and it is impossible for the denominator of $d$ to be zero.
For this to be true the numerator must result in zero.
Thus $2|z - z_0| = 0$,
    it is sufficient to show that $|z - z_0| = 0$.
As $$z, z_0 \in \mathbb{C}_\infty$$ the prior statement is impossible unless $z = z_0$.
Thus a contradiction is achieved$^\blacksquare$.

_Propostion_. $$d(z,z') = d(z',z), \forall z, z' \in \mathbb{C}_\infty$$

_Proof_. Given that multiplication is commutative the denominator again does not matter.
Thus it must be proven that $|z-z'| = |z'-z|$,
    as it happens subtraction inside of an absolute value is also commutative.
Therefore $d$ meets the axiom of symmetry$^\blacksquare$.

_Propostion_. $$d(z,z'') \le d(z,z') + d(z,z''), \forall z,z',z'' \in \mathbb{C}_\infty$$

_Proof_. 

$$
\begin{equation} \label{proof:triangular}
\end{equation}
$$


<!-- TODO: Write about the topology of S^2 with emphasis on open sets, neighborhoods, convergence to \infty, and the compactification of C. -->
# Relations
Here I will describe that topology of $$\widehat{\mathbb{C}}$$ in relation to that of $$\mathbb{C}$$.

# Nomenclature
1. $$\mathbb{C}$$: symbol representing the complex numbers.
2. $$\widehat{\mathbb{C}}$$: symbol representing the Riemann sphere.
3. $$\mathbb{R}$$: symbol representing the real field.
