---
layout: distill
title: Computable regions of the Riemann sphere
description: Exploring computability in the context of the Riemann sphere
tags: analysis logic computability math
giscus_comments: false
date: 2026-06-18
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
        name: butte college

bibliography: 2026-06-12-Computability_on_the_Riemann_sphere.bib

citation: true

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).
toc:
  - name: Introduction
  - name: Topology of Riemann sphere
  - name: Computability
  - name: Future work
  - name: References
  - name: Nomenclature
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
placeholder

# Topology of Riemann sphere
Here I will investigate the Riemann sphere $\widehat{\mathbb{C}}$.
To this end I will use the chordal metric $d_{ch}$ defined as $d$ in <d-cite key="drake"></d-cite>,
    and make great use of the complex plane $\mathbb{C}$.
I will use the definition of the sphere and stereographic projection from a previous work <d-cite key="drake"></d-cite>.

## Metric topology
The metric topology is that topology which makes use of a metric space in order to form a basis set.
For any metric space $(X,d)$ open and closed balls are defined by Eq. $\eqref{def:open-closed-balls}$ and Figure 1, respectively <d-cite key="conway"></d-cite>.

{%
    include theme-images.html
    light="/assets/img/tikz/computable_riemann_sphere/riemann_sphere_line_projection_light.svg"
    dark="/assets/img/tikz/computable_riemann_sphere/riemann_sphere_line_projection_dark.svg"
    alt="visualization of open ball on Riemann sphere"
    caption="Figure 1: Visualization of open set on Riemann sphere"
%}

$$
\begin{equation} \label{def:open-closed-balls}
\begin{split}
    B(x;r) &:= \{y \in X: d(x,y) < r\} \quad \text{open balls} \\
    \bar{B}(x;r) &:= \{y \in X: d(x,y) \le r\} \quad \text{closed balls}
\end{split}
\end{equation}
$$

The metric topology of a metric space is built atop the basis set of that metric space.
In particular, for any family of open sets $\mathcal{B}$ of metric space $(X,d)$,
    $\mathcal{B}$ is a basis set if every open subset of $(X,d)$ is a union of sets in $\mathcal{B}$ <d-cite key="g&g"></d-cite>.
A topology has three axioms which define both how to build them and how they behave, see Eq. $\eqref{axiom:topo-1}$,
    $\eqref{axiom:topo-2}$,
    $\eqref{axiom:topo-3}$,
    see <d-cite key="g&g"></d-cite>.

$$
\begin{equation} \label{axiom:topo-1}
    X, \emptyset \in \mathcal{T} \\
\end{equation}
$$

$$
\begin{equation} \label{axiom:topo-2}
    \mathcal{U} \subseteq \mathcal{T} \implies \bigcup \mathcal{U} \in T
\end{equation}
$$

$$
\begin{equation} \label{axiom:topo-3}
    \mathcal{U}_1,  \ldots, \mathcal{U}_n \in \mathcal{T} \implies \bigcap_{j=1}^n \mathcal{U}_j \in \mathcal{T}
\end{equation}
$$

<div class="prop-block" markdown="1">
**Proposition 1**.

There exists a topological basis $\mathcal{B}$ for metric topology $\mathcal{T}$ formed from the metric space $(\widehat{\mathbb{C}}, d_{ch})$
</div>

<div class="proof-block" markdown="1">
Recall that $(\widehat{\mathbb{C}}, d_{ch})$ is a metric space <d-cite key="drake"></d-cite>.
Define a set $\mathcal{B}$ by Eq. $\eqref{def:basis}, \eqref{def:basis-elem}$,
    that is a set of open balls such that all elements of the space are included.

$$
\begin{equation} \label{def:basis}
    \mathcal{B} := {B : B \subseteq (\widehat{\mathbb{C}}, d_{ch}), B \text{ is open}}
\end{equation}
$$

$$
\begin{equation} \label{def:basis-elem}
    x \in \widehat{\mathbb{C}} \implies (\exists B \in \mathcal{B}) \land (x \in B)
\end{equation}
$$

Notably $\widehat{\mathbb{C}}$ is a complete space <d-cite key="conway"></d-cite>,
    meaning there exist no gaps in $\widehat{\mathbb{C}}$.

<div class="prop-block" markdown="1">
**Lemma 1**

$\mathcal{B}$ is a topological basis in the metric space $(\widehat{\mathbb{C}}, d_{ch})$
</div>
<div class="proof-block" markdown="1">
Since $(\widehat{\mathbb{C}}, d_{ch})$ is a metric space we have access to the triangle inequality.
A basis is defined by the intersection theorem shown in Figure 2.
This theorem has two main parts explained by Eq. $\eqref{def:basis-1}, \eqref{def:basis-2}$ <d-cite key="g&g"></d-cite> <d-cite key="munkres"></d-cite>.

$$
\begin{equation} \label{def:basis-1}
    \forall x \in X \implies (\exists V) \land (x \in V \in \mathcal{B})
\end{equation}
$$

$$
\begin{equation} \label{def:basis-2}
    (U,V \in \mathcal{B}) \land (x \in U \cap V) \implies (\exists W \in \mathcal{B}) \land (x \in W \subset U \in V)
\end{equation}
$$

{%
    include theme-images.html
    light="/assets/img/tikz/computable_riemann_sphere/intersecting_open_ball_light.svg"
    dark="/assets/img/tikz/computable_riemann_sphere/intersecting_open_ball_dark.svg"
    alt="visualization of proof"
    caption="Figure 2: Intersection property of topological basis sets"
%}

The way I have defined our set $\mathcal{B}$ satisfies Eq. $\eqref{def:basis-1}$.
To satisfy Eq. $\eqref{def:basis-2}$ one needs only apply the triangle inequality
    <d-footnote> which seems to always by the answer in topology for some reason? </d-footnote>.
That is if there exists two open balls $U$ and $V$ with radii $\epsilon$ and $\gamma$ respectively,
    such that the outer ring of $U$ is within distance $\gamma$ or $V$, etc.
It is appropriate to assume that there exists some point $x$ that is within $\gamma$ of $V$ and $\epsilon$ of $U$,
    $x \in V \cap U$.
Lets assume that the distance from the center of $V$ ($V_c$) to the nearest point of $U$ is $\gamma_1$ at distance $\gamma - \epsilon$ from $V_c$,
    let us call the equivalent point on for $U$ $\epsilon_1$.
It is now possible to approximate the distance $d_{ch}(\gamma_1, \epsilon_1) > 0$ as that radius of $V \cap U$.
Therefore there must exist a point $x \in V \cap U$ such that $d_{ch}(\gamma_1, \epsilon_1) \le d_{ch}(\gamma_1, x) + d_{ch}(x, \epsilon_1)$.
We call this point $x$ the center of the open set $W$ with radius $min(d_{ch}(\gamma_1, x), d_{ch}(x, \epsilon_1))$,
    Satisfying Eq. $\eqref{def:basis-2}$.
</div>

Using Lemma 1 we know that $\mathcal{B}$ forms a basis on the metric space $(\widehat{\mathbb{C}}, d_{ch})$.
Thus the topology $\mathcal{T}$ exists as the arbitrary union of basis sets <d-cite key="g&g"></d-cite>.
Topology $\mathcal{T}$ can be defined as Eq. $\eqref{def:T}$ using basis $\mathcal{B}$.

$$
\begin{equation} \label{def:T}
    \mathcal{U} \subseteq \mathcal{B} \implies \bigcup \mathcal{U} \in \mathcal{T}
\end{equation}
$$
</div>

## Compactness of $$\widehat{\mathbb{C}}$$
A space is said to be compact if every open cover of that space has a finite subcover <d-cite key="g&g"></d-cite> <d-cite key="conway"></d-cite> <d-cite key="munkres"></d-cite>.
As this can be difficult to prove in its current phrasing,
    here I will use the _Heine-Borel_ theorem <d-cite key="conway"></d-cite>.
In topology equivalence between spaces is defined as those spaces connected via _homeomorphisms_ <d-cite key="g&g"></d-cite>.
That is if there exists a homeomorphism $f: X \rightarrow Y$ the spaces $X$ and $Y$ are said to be topologically equivalent.

<div class="prop-block" markdown="1">
** Proposition 2 **

$\widehat{\mathbb{C}}$ is a compactification of $\mathbb{C}$.
</div>
<div class="proof-block" markdown="1">

First let us prove that $\mathbb{C}$ is not compact.
<div class="prop-block" markdown="1">
** Lemma 1 **

$\mathbb{C}$ is not compact.
</div>
<div class="proof-block" markdown="1">
Any compact set must be closed and bounded <d-cite key="g&g"></d-cite>.
$\mathbb{C}$ is unbounded,
    therefore $\mathbb{C}$ is not compact.
</div>

<div class="prop-block" markdown="1">
** Lemma 2 **

There exists a homeomorphism $f: \widehat{\mathbb{C}} \rightarrow S^2$ such that $\widehat{\mathbb{C}}$ and $S^2$ are homeomorphic.
</div>
<div class="proof-block" markdown="1">
Recall that in <d-cite key="drake"></d-cite> _stereographic projection_ is defined as a function mapping $$\mathbb{C}_\infty$$ to $S^2$ using the chordal metric.
Here the symbolic representation of $\mathbb{C}_\infty$ (Conway's notation) has been changed to $\widehat{\mathbb{C}}$ (common notation) due to personal preference.
It is clear that by our definition of homeomorphic above that stereographic projection is some homeomorphism $f: \widehat{\mathbb{C}} \rightarrow S^2$.
</div>

It can now understood by Lemma 2 that if $S^2$ is shown to be compact then so is $\widehat{\mathbb{C}}$ via the laws of topology <d-cite key="g&g"></d-cite>.
Via the Hiene-Borel Eq. $\eqref{def:HB}$ it is possible to show that $S^2$ is a compact space.

$$
\begin{equation} \label{def:HB}
    K \subset \mathbb{R}^n, (n \ge 1) \text{ is compact } \iff K \text{ is closed and bounded }
\end{equation}
$$

It is trivial to see that $S^2$ is bounded from its construction, see Eq. $\eqref{def:S2}$

$$
\begin{equation} \label{def:S2}
    S^2 := \{ x : (x \in \mathbb{R}^3) \land (\|x\| = 1) \}
\end{equation}
$$

Though the closedness of $S^2$ is also somewhat obvious from its definition it is worth examining.
By definition the compliment of a closed set must be an open set <d-cite key="g&g"></d-cite>.
In particular,
    $S^2$ is closed if and only if $\mathbb{R}^3 \setminus S^2$ is open.
It becomes clearer from construction that the compliment Eq. $\eqref{eq:S2-comp}$ is union of open sets though it may be worth further examination.

$$
\begin{equation} \label{eq:S2-comp}
    \Omega = \mathbb{R}^3 \setminus S^2 := \{ x : (x \in \mathbb{R}^3) \land ((\|x\| > 1) \lor (\|x\| < 1)) \}
\end{equation}
$$

$$
\begin{equation} \label{eq:S2-comp2}
    \Omega = \{ x : x \in \mathbb{R}^3, \|x\| < 1 \} \cup \{ x : x \in \mathbb{R}^3, \|x\| > 1 \}
\end{equation}
$$

The left hand side of the union in Eq. $\eqref{eq:S2-comp2}$ is a trivial open set,
    however the right hand side is not so obvious.
Recall that $S^2$ is a bounded sphere,
    thus the right hand side of the union represents all points in $\mathbb{R}^3$ that are outside the sphere while the left hand side is all points inside.
In particular given that all those points in $S^2$ have exactly distance $1$ from the origin it is conceivable that an open ball centered distance $2$ from the origin could be formed with radius $1$.
By this approach one can create an infinite number of open balls such that the union of which will be the right hand side of our union from Eq. $\eqref{eq:S2-comp2}$.
Notably the union of two open sets is itself an open set <d-cite key="g&g"></d-cite>,
    therefore $S^2$ is shown to be a closed set.
Since $S^2$ adheres to those requirements of the Heine-Borel theorem,
    it is has been proved that $S^2$ is compact.
Since $S^2$ is compact then by Lemma 2 $\widehat{\mathbb{C}}$ is compact.
By Lemma 1 it is known that $\mathbb{C}$ is not compact,
    therefore it has been proved that $\widehat{\mathbb{C}}$ is a compactification of $\mathbb{C}$.
</div>

## Dense subsequence
It is worth exploring a specific dense subset of $(\widehat{\mathbb{C}}, d_{ch})$ as it will be of importance.
Let us define the set $\Omega$ as those points rational points of $\mathbb{C}$ that have been mapped to $S^2$ via stereographic projection.
In particular it can be seen by Eq. $\eqref{def:omega}$ that $\Omega \subset \widehat{\mathbb{C}}$,
    as the complex numbers are isomorphic to $\mathbb{R}^2$ not $\mathbb{Q}^2$.

$$
\begin{equation} \label{def:omega}
\begin{split}
    A := \{ z_1 + iz_2 :  z_1, z_2 \in \mathbb{Q} \} \cup \{ \infty \} \\
    \Omega := \{ Z : Z \in (A \mapsto S^2) \}
\end{split}
\end{equation}
$$

<div class="prop-block" markdown="1">
** Proposition 3 **

$\Omega$ is dense in $\widehat{\mathbb{C}}$.
</div>
<div class="proof-block" markdown="1">
A dense subset is defined as that subset $U$ of a space $X$ for which the closure of the subset $\bar{U}$ is the space Eq. $\eqref{def:dense-subset}$.

$$
\begin{equation} \label{def:dense-subset}
    U \text{ dense in } X \implies \bar{U} = X
\end{equation}
$$

The closure of the rational numbers is the real numbers $\bar{\mathbb{Q}} = \mathbb{R}$ implies that $\bar{\mathbb{Q} + i\mathbb{Q}} = \mathbb{R} + i\mathbb{R}$.
Therefore as $A \mapsto S^2$ is an homeomorphism via Lemma 2 of theorem 2,
    it has been shown that $\Omega$ is dense in $\widehat{\mathbb{C}}$.
</div>

<!-- TODO: State what “computable region” will mean next—for example, computably open subsets as effectively enumerable unions of rational chordal balls. -->
# Computability

## Classical approach

<!-- TODO: Put genuine extensions, such as effective compactness or hyperspace representations, in a short future-work paragraph. -->
# Future work

# Nomenclature
1. $\emptyset$: Symbol for the empty set $$\{\}$$.
2. $\subset$: Symbol for subset.
3. $\widehat{\mathbb{C}}$: Symbol for the Riemann sphere.
4. $x \in A$: $x$ is an element of the set $A$.
5. $$\{ x: (x \in A) \land (x > 0)\}$$: set builder notation,
    read: all elements $x$ such that $x \in A$ logical and $x > 0$.
6. $S^2$: The unit sphere projected in $\mathbb{R}^3$.
7. $\exists x$: There "exists" some value $x$
8. $v_\mathbb{Q}: \mathbb{N} \rightarrow \mathbb{Q}$: the standard numbering on $\mathbb{Q}$ inherited from <d-cite key="weihrauch_article"></d-cite>.
9. $\mathbb{B}$: Baire space notation inherited from <d-cite key="weihrauch_article"></d-cite>.
