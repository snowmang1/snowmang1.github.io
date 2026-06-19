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

authors:
    - name: evan drake
      url: "https://snowmang1.github.io/"
      affiliations:
        name: butte college

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
    subsections:
      - name: Complex plane
      - name: Spheres
      - name: Metric spaces
  - name: Intuition
  - name: Stereographic projection
  - name: Chordal metric
  - name: Topology
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
Beginning with the complex plane $\mathbb{C}$ I explore the necessary background information.
I then construct the Riemann sphere $\widehat{\mathbb{C}}$ via a geometric and analytic intuition.
In particular the introduction of the extended complex plane and stereographic projection via light proof work.
This will present that homeomorphic mapping from the extended complex plane to the Riemann sphere.
Finally I explore shallowly that topology of the Riemann sphere that will be used in later articles.

### Complex plane
The complex numbers are an extension of $\mathbb{R}$;
    any $z \in \mathbb{C}$ is composed of two terms one real and one imaginary.
That is for any such $z$ it is the case that $z = a + ib$ such that $a,b \in \mathbb{R}$ and $i$ is imaginary.
This gives a rather simple geometric intuition wherein we use the two terms to form our axis <d-cite key="lang"></d-cite>.
A depiction of this relation can be seen in figure 1, borrowed from <d-cite key="lang"></d-cite>.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/cart_plane_light.svg"
    dark="/assets/img/tikz/stereographic_proj/cart_plane_dark.svg"
    alt="a depiction of the complex plane"
    caption="Figure 1: Complex plane"
%}

### Spheres
A sphere as we can see from figure 4 is that shape containing no "edges" in the three-dimensional space.
Being in a three-dimensional space describing a single point of any sphere requires a three-tuple,
    some $(x,y,z)$.
That is a sphere contains those points lying not only on its surface but those contained inside the extrema as well.
Note that some point $(x,y,z)$ need not always be located on a surface.
In the context of the discussion that follows,
    note that a fundamental rule of three-dimensionality is that the sphere contains those points within itself.
In particular,
    if the sphere did not contain those points within or if those points where unreachable then that sphere could be thought of as two dimensional.
That is the sphere itself could be treated as a two-dimensional surface projected in three-dimensional space,
    commonly referred to as $S^2$.

### Metric spaces
A metric space describes that relation between some set and a function $(S, d)$.
Such that those elements $a,b \in S$ can be described in relation to each other via $d$.
That is $d(a,b)$ will represent some metric between $a$ and $b$ <d-cite key="conway"></d-cite> <d-cite key="munkres"></d-cite> <d-cite key="g&g"></d-cite>.
There exist four axioms of a metric space $(S, d)$,
    such that a space can only be treated as such if they are true.

1. $d(a,b) \ge 0, \forall a,b \in S$
2. $d(a,b) = 0 \iff a = b, \forall a,b \in S$
3. $d(a,b) = d(b,a), \forall a,b \in S$
4. $d(a,c) \le d(a,b) + d(b,c), \forall a,b,c \in S$

# Intuition
It is common in analysis and topology to consider transformations with respect to $\infty$.
Given the above section on $\mathbb{C}$,
    assume this is a problem given the asymptotic nature of $\infty$ in $\mathbb{C}$.
Thus we create the extended complex plane from <d-cite key="conway"></d-cite> $$\mathbb{C}_\infty := \mathbb{C} \cup \{ \infty \}$$.
The addition of $\infty$ as a point is only useful if we can place it in relation to other points,
    thus we require the creation of a metric space.
It is tempting to consider a simple euclidean distance metric,
    geometrically this does not work as the ends of the plane now tend towards a single point, $\infty$.
In particular it must be true that those sequences that diverge to $\infty$ can never reach it,
    thus preserving the nature of those sequences.
This implies a need for a metric that will both give that distance between points,
    while not allowing any point to be finitely close to $\infty$.
Thus we use _stereographic projection_ as the metric function on $$\mathbb{C}_\infty$$.

# Stereographic projection
Stereographic projection describes a technique for relating a unit sphere to some plane <d-cite key="needham"></d-cite>.
Thus all $z \in \mathbb{C}_\infty$ have the relation $z \mapsto Z$ for some point $Z \in S^2$.
The mapping is made via the north pole $N \in S^2$
We can see a two dimensional representation of this in figure 2 and the three dimensional version in figure 2.5
    taken from<d-cite key="needham"></d-cite>.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/profile_light.svg"
    dark="/assets/img/tikz/stereographic_proj/profile_dark.svg"
    alt="Stereographic projection 2D view"
    caption="Figure 2: 2D stereographic projection"
%}
{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/single_z_light.svg"
    dark="/assets/img/tikz/stereographic_proj/single_z_dark.svg"
    alt="Stereographic projection 2D view"
    caption="Figure 2.5: 3D stereographic projection"
%}

That mapping $z \mapsto Z$ implies a "straight line" $(N, z)$,
    such that the intersection of $S^2$ is that point $Z$ as shown in figure (2.5).
In particular if we take any point on the plane and induce a line $(N, z)$ for some $$z \in \mathbb{C}_\infty$$,
    it is the case that all but one line will pass through the surface of the sphere at some point other than $N$ <d-cite key="conway"></d-cite>.
The line $(N, z) \mid z = \infty$ will create a tangent line on $N$.
Here I define stereographic projection as $f$ in Eq $\eqref{eq:stereo_mapping}$.

$$
\begin{equation} \label{eq:stereo_mapping}
f(z) = (\frac{z + \bar{z}}{|z|^2 + 1}, \frac{-i(z - \bar{z})}{|z|^2 + 1}, \frac{|z|^2 - 1}{|z|^2 + 1}) \in S^2
\end{equation}
$$

Notice that as $$z \rightarrow \infty$$ the value $f(z) \rightarrow N$ for any value $$z \in \mathbb{C}_\infty$$.
In particular according to the definition of $f$,
    as $z \rightarrow \infty$ those coordinate values of $f(z)$ tend to $(0, 0, 1)$ or $N$.
Thus providing evidence any line $(N, \infty)$ forma a tangent line on $N$.
It is the case here that since the sphere $S^2$ is formed via that transformation of all points in $\mathbb{C}_\infty$,
    it can be assumed to be bijective<d-footnote> that being the case proofs are simply fun to form </d-footnote>.

_Proposition_. $f$ is a bijection

_Proof_. To show that any function is bijective one must prove that the given function is both surjective and injective.
Assume $f$ is not surjective, then there must exist a $z$ such that $f(z) = DNE$ or $f(z_1) = f(z_2)$
The only way this could be true is if the denominator of some coordinate could be zero,
    $|z|^2$ can be neither zero nor negative.
Thus it is impossible for any denominator of the coordinate equations to be zero,
    The second case is proven through a proof that $f$ is injective.
Assume $f$ is not injective, then there must exist some $z_1, z_2 \in \mathbb{C}_\infty : (z_1 \ne z_2) \land (f(z_1) = f(z_2))$.
For those points the following must be true:

$$
\begin{equation} \label{eq:z1_z2}
\begin{split}
    \frac{|z_1|^2 - 1}{|z_1|^2 + 1} &= \frac{|z_2|^2 - 1}{|z_2|^2 + 1} \\
    (|z_1|^2 - 1)(|z_2|^2 + 1) &= (|z_2|^2 - 1)(|z_1|^2 + 1) \\
    (|z_1|^2 |z_2|^2 - |z_2|^2 + |z_1|^2) &= (|z_1|^2 |z_2|^2 - |z_1|^2 + |z_2|^2) \\
    (|z_1|^2 |z_2|^2 + 2|z_1|^2) &= (|z_1|^2 |z_2|^2 + 2|z_2|^2) \\
    |z_1|^2 &= |z_2|^2 \\
    z_1 &= z_2
\end{split}
\end{equation}
$$

We find the Eq $\eqref{eq:z1_z2}$ describes a contradiction as the only way for $f(z_1) = f(z_2)$ is that $z_1 = z_2$,
    therefore $f$ is injective and surjective thus bijective$^\blacksquare$.

# Chordal metric
Here I will describe that metric that allows formulation of the distance function between two points of $S^2$.
I accomplish this using that metric space $\widehat{\mathbb{C}} := (S^2, d)$ where the function $d$ is the _chordal distance_.
That is the euclidean distance between two points $Z_1, Z_2 \in S^2$ <d-cite key="conway"></d-cite>.
Here I will use those points of $\mathbb{C}_\infty$ assuming stereographic projection of those points.
That is those $z, z'$ points of this metric function $d$ will be defined as points of the complex plane,
    rather than those direct mappings of $S^2$.
This is legal due to stereographic projection being a homeomorphism,
    which I describe later in detail.
Notably Eq $\eqref{eq:chordal_dist}$ is taken from <d-cite key="conway"></d-cite>,
    however starting from the euclidean distance on $S^2 \subset \mathbb{R}^3$ and adjusting for Eq $\eqref{eq:stereo_mapping}$ one can derive it themselves simply.
It is necessary to prove that any metric $d$ follows those axioms of a metric space for some set,
    in this case $S^2$.
Assume $d$ here is equivalent to that metric function $d(Z, Z')$ for any points $Z, Z' \in S^2$.

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
Thus the outcome of the function $d$ must always be non-negative$^\blacksquare$.

_Proposition_. $d(z, z') = 0 \iff z = z'$.

_Proof_. Assume $$\exists z, z_0 \in \mathbb{C}_\infty$$ such that $(z \ne z_0) \land (d(z,z_0) = 0)$.
Given the denominator of a fraction can not be zero,
    and it is impossible for the denominator of $d$ to be zero.
For this to be true the numerator must result in zero.
Thus $2|z - z_0| = 0$,
    it is sufficient to show that $|z - z_0| = 0$.
As $$z, z_0 \in \mathbb{C}_\infty$$ the prior statement is impossible unless $z = z_0$.
Therefore It is a contradiction to assume $\exists z, z_0 \in \mathbb{C}_\infty$ such that $(z = z_0) \land (d(z, z_0) = 0)^\blacksquare$.

_Propostion_. $$d(z,z') = d(z',z), \forall z, z' \in \mathbb{C}_\infty$$

_Proof_. Given that multiplication is commutative the denominator again does not matter.
Thus it must be proven that $|z-z'| = |z'-z|$,
    as it happens subtraction inside of an absolute value is also commutative.
Therefore $d$ meets the axiom of symmetry$^\blacksquare$.

_Propostion_. $$d(z,z'') \le d(z,z') + d(z,z''), \forall z,z',z'' \in \mathbb{C}_\infty$$

_Proof_. The geometric representation of the function $d(a,b)$ is that straight line from $a$ to $b$ in $\mathbb{R}^3$.
It can then be assumed that three points would form a triangle,
    which can be represented on a plane by figure 3.
Thus any three points of $\widehat{\mathbb{C}}$ such that the function $d$ maps them all in the form of the proposition above will form a triangle.
Observe one such triangle depicted in figure 3.
In particular,
    it is impossible for such a shape to have a side length larger than the sum of the two others.
That is for any triangle with arbitrary side lengths ${a,b,c}$ it is an impossibility that $a > b+c$,
    thus it must be true that $a \le b+c$ as in the case of the current proposition$^\blacksquare$.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/euclidean_triangle_light.svg"
    dark="/assets/img/tikz/stereographic_proj/euclidean_triangle_dark.svg"
    alt="triangle created by the distance between z, z', and z''."
    caption="Figure 3: Triangle created from distance between three points of $\mathbb{R}^3$"
%}

Thus we prove that the chordal metric $d$ can be used to form the metric space $(\widehat{\mathbb{C}}, d) \equiv (S^2, d)$.
That metric space $$\widehat{\mathbb{C}}$$ is referred to as the Riemann sphere <d-cite key="needham"></d-cite>.
In particular it is that projection of $$\mathbb{C}_\infty$$ onto $S^2$ via stereographic projection depicted in figure 4.
Such that each point of the extended complex field is mapped so some point on $S^2$.

{%
    include theme-images.html
    light="/assets/img/tikz/stereographic_proj/riemann_sphere_light.svg"
    dark="/assets/img/tikz/stereographic_proj/riemann_sphere_dark.svg"
    alt="a depiction of the Riemann sphere"
    caption="Figure 4: A depiction of the Riemann sphere"
%}

# Topology
It is the case that $$\widehat{\mathbb{C}}$$ is a compactification of $\mathbb{C}$.
To understand this we must examine those aspects of $\mathbb{C}$ which make it non-compact.
In particular for $\mathbb{C}$ to be compact it must be complete,
    thus it must contains all the limit points of its convergent subsets<d-cite key="conway"></d-cite>.
Thus any such infinite convergent sequence in $\mathbb{C}$ must have a limit in $\mathbb{C}$.
The existence of a sequence $$(x_n) \in \mathbb{C}$$ such that $$(x_n) \rightarrow \infty$$,
    would prove the non-compactness of $\mathbb{C}$.
Recall it was the purpose of constructing $$\widehat{\mathbb{C}}$$ for such sequences $$(x_n) \in \mathbb{C}$$,
    thus proving its non-compactness.
Therefore if $$\widehat{\mathbb{C}}$$ is compact then it must contain those limit points for such infinite sets.
Recall that the subset of a convergent set is itself convergent as well.

_Proposition_. $$\widehat{\mathbb{C}}$$ is compact

_Lemma_ 1. A set is compact if all infinite subsets contain a limit point <d-cite key="conway"></d-cite>.

_Lemma_ 2. Weierstrass-Bolzano: If S is an infinite bounded set of real numbers, then S has a point of accumulation<d-cite key="lang"></d-cite>. Assume this works for complex numbers.

_Proof_. Consider all infinite $X \subset \widehat{\mathbb{C}}$.
The set $X$ may either be bounded or unbounded.

_Case bounded_. If $X$ is bounded then it contains a subsequence $(x_n) \subset X$ such that $(x_n)$ is convergent by Lemma 2.

_Case unbounded_. If $X$ is unbounded then there exists a sequence $(x_n) \subset X$ such that $(x_n) \rightarrow \infty$.
Recall that $\infty$ is treated as an ordinary point in $\widehat{\mathbb{C}}$.

Given that for all infinite sets $X \subset \widehat{\mathbb{C}}$ there exists some sequence $(x_n) \subset X$ by Lemma 1 $\widehat{\mathbb{C}}$ is compact$^\blacksquare$.

# Nomenclature
1. $$\mathbb{C}$$: symbol representing the complex numbers.
2. $$\widehat{\mathbb{C}}$$: symbol representing the Riemann sphere.
3. $$\mathbb{R}$$: symbol representing the real field.
4. $$x \in X$$: $x$ is an element of the set $X$.
5. $$P \implies Q$$: the truth of the proposition P implies the truth of the proposition Q.
6. $$P \iff Q$$, $P$ iff $Q$: P is the true if and only if Q is true.
7. $$\widehat{\mathbb{C}}$$: symbol for the Riemann sphere.
8. $$\forall x \in S$$: "forall", meaning $x$ represents all elements of $S$ recursively.
9. $$(x_n)$$: denotes a sequence of size $n$.
10. $$(x_n) \rightarrow x$$: the sequence $(x_n)$ converges to limit point $x$.
11. $$\exists x \in X$$: there exists some element $x$ contained in the set $X$.
12. Eq (x): is a reference so some equation labeled numerically "x" in the document.
13. $$ P \land Q $$: read "P and Q" logical and means the statement is only true when both proposition P and Q are true.
