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
Here I explore the computability of the Riemann sphere $\widehat{\mathbb{C}}$.
The necessary foreground to the problem is laid out by an exploration of the topology of $\widehat{\mathbb{C}}$ and then computability on such spaces.
Theorem 1 is given to show that there exists a metric topology on $\widehat{\mathbb{C}}$.
Given the constraints of traditional recursion theory it is necessary to use type 2 computability to explore a structure in real space.
With a brief introduction to type 2 computability it becomes apparent that type two effectivity theory (TTE) is a useful tool for such a question.
Using that metric topology on $\widehat{\mathbb{C}}$ and a dense set there in,
    the claim of TTE computability can be made on the space of $\widehat{\mathbb{C}}$.

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
It is understood that $\mathcal{T}$ can be built from the basis $\mathcal{B}$ in the manner described by Eq. $\eqref{def:T-from-basis}$.

$$
\begin{equation} \label{def:T-from-basis}
    \mathcal{T} := \{ \bigcup \mathcal{U} : \mathcal{U} \subseteq \mathcal{B} \}
\end{equation}
$$

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
    \mathcal{U} \subseteq \mathcal{T} \implies \bigcup \mathcal{U} \in \mathcal{T}
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
**Proof of Proposition 1**

Recall that $(\widehat{\mathbb{C}}, d_{ch})$ is a metric space <d-cite key="drake"></d-cite>.
Define a set $\mathcal{B}$ by Eq. $\eqref{def:basis}, \eqref{def:basis-elem}$,
    that is a set of open balls such that all elements of the space are included.

$$
\begin{equation} \label{def:basis}
    \mathcal{B} := \{ B_{d_{ch}}(z ; r) : z \in \widehat{\mathbb{C}}, r > 0 \}
\end{equation}
$$

$$
\begin{equation} \label{def:basis-elem}
    z \in \widehat{\mathbb{C}} \implies (\exists B \in \mathcal{B}) \land (z \in B)
\end{equation}
$$

Open sets in a metric space have the form $B(x; \epsilon)$ <d-cite key="conway"></d-cite>,
    therefore it can be known that all sets in $\mathcal{B}$ are open in the metric space.
By the definition of $\mathcal{B}$ all elements of $(\widehat{\mathbb{C}}, d_{ch})$ belong to some set in $\mathcal{B}$.
In particular,
    the definition gives that for all elements of the space there exists an open ball of non-zero radius on that element.
Any basis set must also have the intersection property <d-cite key="g&g"></d-cite>.
The property that for any two intersecting open sets $U \cap V$ such that $U$ and $V$ are in the basis set,
    there exists another set $W$ in the basis set such that $W \subset (U \cap V)$ as seen in Figure 2.

{%
    include theme-images.html
    light="/assets/img/tikz/computable_riemann_sphere/intersecting_open_ball_light.svg"
    dark="/assets/img/tikz/computable_riemann_sphere/intersecting_open_ball_dark.svg"
    alt="visualization of proof"
    caption="Figure 2: Intersection property of topological basis sets"
%}

<div class="prop-block" markdown="1">
**Lemma 1**

The set $\mathcal{B}$ has the intersectional property.
</div>
<div class="proof-block" markdown="1">
**Proof of Lemma 1**

The open sets $U, V \in \mathcal{B}$ must be open balls,
    thus let us define them as Eq. $\eqref{def:u-v}$.
$$
\begin{equation} \label{def:u-v}
\begin{split}
    U := B(a ; r_U) \\
    V := B(b ; r_V)
\end{split}
\end{equation}
$$

Such that some point $z$ has the property $z \in B(a ; r_U) \cap B(b ; r_V)$.
Given that $U \cap V \ne \emptyset$ we can say that there exists $W \in U \cap V$.
In particular,
    we can describe $W$ as that open ball centered on the point $z$ with radius of the shortest distance to the bound of either intersecting set Eq. $\eqref{def:w1}$.

$$
\begin{equation} \label{def:w1}
\begin{split}
    W := B(z ; r_W) \\
    r_W = min[(r_U - d(z,a)),(r_V - d(z, b))]
\end{split}
\end{equation}
$$

This grantees the relationship $W \subseteq U \cap V$ which is not quite the desired $W \subset U \cap V$,
    the fix is observed by Eq. $\eqref{def:w2}$.

$$
\begin{equation} \label{def:w2}
\begin{split}
    W := B(z ; r_W) \\
    r_W = \frac{1}{2}min[(r_U - d(z,a)),(r_V - d(z, b))]
\end{split}
\end{equation}
$$

This guarantees the desired relation $z \in W \subset U \cap V$ required by the intersection property.
The remaining doubt is that all elements of $W$ belong to both $U$ and $V$.
This can easily be observed through the triangle inequality.
It is observed that for any point $w \in W$ that $d(a,w) \le d(a,z) + d(z,w) < d(z,a) + r_W < r_U$.
The same relation is observed for $V$,
    therefore all elements of $W$ belong to $U$ and $V$.
</div>

Given the above information on $\mathcal{B}$ and **Lemma 1** it proved a basis set.
Therefore the metric topology $\mathcal{T}$ exists and takes the form of Eq. $\eqref{def:T-from-basis}$.
</div>

## Compactness of $$\widehat{\mathbb{C}}$$
A space is said to be compact if every open cover of that space has a finite subcover <d-cite key="g&g"></d-cite> <d-cite key="conway"></d-cite> <d-cite key="munkres"></d-cite>.
As this can be difficult to prove in its current phrasing,
    here I will use the _Heine-Borel_ theorem <d-cite key="conway"></d-cite>.
In topology equivalence between spaces is defined as those spaces connected via _homeomorphisms_ <d-cite key="g&g"></d-cite>.
That is if there exists a homeomorphism $f: X \rightarrow Y$ the spaces $X$ and $Y$ are said to be topologically equivalent.

<div class="prop-block" markdown="1">
**Proposition 2**

$\widehat{\mathbb{C}}$ is a compactification of $\mathbb{C}$.
</div>
<div class="proof-block" markdown="1">
**Proof of Proposition 2**

First let us prove that $\mathbb{C}$ is not compact.
<div class="prop-block" markdown="1">
**Lemma 1**

$\mathbb{C}$ is not compact.
</div>
<div class="proof-block" markdown="1">
**Proof of Lemma 1**

Any compact set must be closed and bounded <d-cite key="g&g"></d-cite>.
$\mathbb{C}$ is unbounded,
    therefore $\mathbb{C}$ is not compact.
</div>

<div class="prop-block" markdown="1">
**Lemma 2**

There exists a homeomorphism $f: \widehat{\mathbb{C}} \rightarrow S^2$ such that $\widehat{\mathbb{C}}$ and $S^2$ are homeomorphic.
</div>
<div class="proof-block" markdown="1">
**Proof of Lemma 2**

Recall that in <d-cite key="drake"></d-cite> _stereographic projection_ is defined as a function mapping $$\mathbb{C}_\infty$$ to $S^2$ using the chordal metric.
Here the symbolic representation of $\mathbb{C}_\infty$ (Conway's notation) has been changed to $\widehat{\mathbb{C}}$ (common notation) due to personal preference.
It is clear that by our definition of homeomorphic above that stereographic projection is some homeomorphism $f: \widehat{\mathbb{C}} \rightarrow S^2$.
</div>

It can now understood by **Lemma 2** that if $S^2$ is shown to be compact then so is $\widehat{\mathbb{C}}$ via the laws of topology <d-cite key="g&g"></d-cite>.

<div class="prop-block" markdown="1">
**Lemma 3**

$S^2$ is compact via the Hiene-Borel theorem Eq. $\eqref{def:HB}$.
</div>
<div class="proof-block" markdown="1">
**Proof of Lemma 3**

The set $S^2$ defined by Eq. $\eqref{def:S2}$ is obviously a bounded subset of $\mathbb{R}^3$.

$$
\begin{equation} \label{def:S2}
    S^2 := \{ x : (x \in \mathbb{R}^3) \land (\|x\| = 1) \}
\end{equation}
$$

There exists a continuous function $f$ defined by Eq. $\eqref{def:f}$ such that $f$ is continuous.

$$
\begin{equation} \label{def:f}
\begin{split}
    f &: \mathbb{R}^3 \rightarrow \mathbb{R} \\
    f(x) &= \| x \|
\end{split}
\end{equation}
$$

Notably the pre-image of a closed set is closed via a continuous function across two metric spaces <d-cite key="g&g"></d-cite>.
Recall the set $\{ 1 \}$ is closed in $\mathbb{R}$,
    and $S^2 = f^{-1}(\{ 1 \})$ by  Eq. $\eqref{def:S2}$.
Therefore since $\{ 1 \}$ is closed in $\mathbb{R}$,
    it must be true that $S^2$ is closed in $\mathbb{R}^3$.
Via the Hiene-Borel Eq. $\eqref{def:HB}$ it is possible to show that $S^2$ is a compact space.

$$
\begin{equation} \label{def:HB}
    K \subset \mathbb{R}^n, (n \ge 1) \text{ is compact } \iff K \text{ is closed and bounded }
\end{equation}
$$

It has been proven that $S^2$ is both bounded and closed in $\mathbb{R}^3$,
    proving by Eq. $\eqref{def:HB}$ that $S^2$ is compact.
</div>

Given **Lemma 1**, **Lemma 2** & **Lemma 3** it can be said that $\widehat{\mathbb{C}}$ is a compactification of $\mathbb{C}$.
</div>

## Dense subsequence
It is worth exploring a specific dense subset of $\widehat{\mathbb{C}}$ as it will be of importance.
Let us define the set $\Omega$ as those points rational points of $\widehat{\mathbb{C}}$ including the point $\infty$.
In particular it can be seen by Eq. $\eqref{def:omega}$ that $\Omega \subset \widehat{\mathbb{C}}$,
    as the complex numbers are isomorphic to $\mathbb{R}^2$ not $\mathbb{Q}^2$.

$$
\begin{equation} \label{def:omega}
\begin{split}
    \Omega := (\mathbb{Q} + i\mathbb{Q} \cup \{ \infty \}) \subset \widehat{\mathbb{C}}
\end{split}
\end{equation}
$$

<div class="prop-block" markdown="1">
**Proposition 3**

$\Omega$ is dense in $\widehat{\mathbb{C}}$.
</div>
<div class="proof-block" markdown="1">
**Proof of Proposition 3**

A dense subset is defined as that subset $U$ of a space $X$ for which the closure of the subset $\bar{U}$ is the space Eq. $\eqref{def:dense-subset}$.

$$
\begin{equation} \label{def:dense-subset}
    U \text{ dense in } X \implies \bar{U} = X
\end{equation}
$$

The closure of the rational numbers is the real numbers $\bar{\mathbb{Q}} = \mathbb{R}$ implies that $\overline{\mathbb{Q} + i\mathbb{Q}} = \mathbb{R} + i\mathbb{R}$.
Thus it must be true that $$\mathbb{Q} + i\mathbb{Q} \cup \{ \infty \}$$ is dense in $$\mathbb{R} + i\mathbb{R} \cup \{ \infty \}$$,
    proving that $\Omega$ is dense in $\widehat{\mathbb{C}}$.
</div>

# Computability
A computable process can be defined as that mechanical logic which accomplishes a decidable predicate in finitely many steps <d-cite key="cutland"></d-cite>.
In particular,
    the idea of computability is dependant on the logic in use.
Let the definition of decidability be adopted from <d-cite key="cutland"></d-cite>,
    as a full treatment is beyond the scope of this article.
Here I will use the idea of Turing-computability,
    though my understanding of such mechanical logic is more closely tied to the Lambda calculus.
In particular this means that here a computable function utilizes the Turing machine as a mechanical logic.
We first examine the use of classical computability applied to the problem,
    then examine some more modern methodology.
For the remainder of this article is important to have some concrete definition of a _region_,
    to this end see Eq. $\eqref{def:region}$ taken from <d-cite key="conway"></d-cite>.

$$
\begin{equation} \label{def:region}
    X \subset \mathbb{R}^2 \text{ is a region} \iff X \text{ is open and connected }
\end{equation}
$$

It is understood that $\mathbb{R}^2$ is isomorphic to $\mathbb{C}$ and $\widehat{\mathbb{C}}$ is isomorphic to $S^2$,
    therefore a region in our sense will be that open connected subset of $\widehat{\mathbb{C}}$.

## Classical approach
To examine the computability of any region of $\widehat{\mathbb{C}}$ it is imperative to understand what it means for a set to be _computable_ or _recursive_.
Formally we say that a set is recursive when its characteristic function is computable <d-cite key="cutland"></d-cite>.
Moving forward note that this article will use the term recursive when discussing sets,
    and computable when discussing functions.
A sets characteristic function is the ownership defining function corresponding to the predicate $x \in A$.
Formally for any set $A \subseteq \mathbb{N}$ the characteristic function $c_A: \mathbb{N} \rightarrow \{0,1\}$ is that function which computes predicate $x \in A$.
Notably $c_A$ shown in Eq. $\eqref{fxn:c_A}$ is computable iff $x \in A$ is a _decidable_ predicate.

$$
\begin{equation} \label{fxn:c_A}
c_A = \begin{cases}
    1, \quad &x \in A \\
    0, \quad &x \notin A
    \end{cases}
\end{equation}
$$

It is clear that a set is recursive only when its characteristic function is computable,
    thus possessing a decidable predicate $x \in A$.
Via <d-cite key="cutland"></d-cite> all characteristic functions (defining recursive sets) are defined with denumerable domains,
    as the recursive sets themselves must be denumerable.
Notably membership of arbitrary subsets of $\widehat{\mathbb{C}}$ is not a Type-1 predicate problem,
    a problem ill-suited to classical recursion theory tools.
Therefore one must rely on effective openness and closedness,
    which falls in the problem space of Type-2 recursion theory.
Classical recursion theory (Type-1) concerns discrete spaces.
To discuss a non-discrete space such as $\widehat{\mathbb{C}}$ one must specify a representation of its structure.
Type-2 computability provides such a representation through the use of _Baire_ space and effective approximation.

## Computable topologies
Having deduced that classical computability does not have the power to examine the computability of $\widehat{\mathbb{C}}$ presenting an opportunity to examine modern approaches.
The space of computability I investigate here is that of _metric spaces_ on $\mathbb{R}^n$ where $(n \ge 1)$.
There exists a literature for computability on metric spaces belonging to $\mathbb{R}^n$ <d-cite key="frauendiener_klein"></d-cite>
    <d-cite key="brattka_weihrauch"></d-cite> <d-cite key="brattka_presser"></d-cite> <d-cite key="brattka"></d-cite>
    <d-cite key="weihrauch_book"></d-cite> <d-cite key="weihrauch_article"></d-cite>
    <d-cite key="weihrauch_comp"></d-cite>.
The literature describes the "classical approach" above as _type one_ theory of computability.
As discussed the type one theory is ineffective on spaces on the order of $\mathbb{R}^n$ where $n \ge 1$.
The literature then converges on <d-cite key="weihrauch_comp"></d-cite> <d-cite key="weihrauch_book"></d-cite>
    which describes the _type two_ theory of effectivity (TTE) which works in spaces on the order of $\mathbb{R}^n$.
The TTE has only appeared so far in writings stemming from <d-cite key="weihrauch_book"></d-cite> in my readings.
There exist previous sources of computability on broader spaces than $\mathbb{N}$ though none as general as TTE.
Notably TTE claims power enough to prove $\mathbb{R}$ a computable space <d-cite key="weihrauch_article"></d-cite>.
For the scope of $\widehat{\mathbb{C}}$ TTE provides insight into computability of metric spaces.
Such that TTE describes a theory of computability tied to specific topologies known as _Baire spaces_ <d-cite key="weihrauch_book"></d-cite>.
TTE describes a computable metric space as the four tuple $\bar{M}$ described in Eq. $\eqref{eq:tte-m}$.
Dictating that the cardinality of $M$ be at most that of a _Baire space_, $card(M) \le card(\mathbb{B})$.

$$
\begin{equation} \label{eq:tte-m}
\bar{M} := (M, d, A, \alpha)
\end{equation}
$$

1. $(M,d)$ is a metric space
2. $A \subset M$ is dense in $M$
3. $\alpha : \mathbb{N} \rightarrow A$ is a total numbering of $A$
4. $$D_{<} := \{ \langle i, j, k \rangle \mid d(\alpha(i), \alpha(j)) < v_\mathbb{Q}(k) \}$$ is recursively enumerable

Therefore by TTE if one can satisfy and prove the validity of the four elements of the tuple $\bar{M}$ then one proves the effectivity of the space $(M, d)$.
In the article so far It is clear that the metric space under investigation is $(\widehat{\mathbb{C}}, d_{ch})$.
Notably it was proven that $\Omega$ from Eq. $\eqref{def:omega}$ is a dense subset of this metric space.
Thus if there exists functions $\alpha$ and $D_{<}$ then the existence of recursively enumerable regions or $(\widehat{\mathbb{C}}, d_{ch})$ can be proved to exist.

<div class="prop-block" markdown="1">
**Proposition 4**

There exists a tuple $\bar{M}$ of the form described by equation Eq. $\eqref{construct:bar-M}$ that satisfies _TTE_.

$$
\begin{equation} \label{construct:bar-M}
    \bar{M} := ((\widehat{\mathbb{C}}, d_{ch}), \Omega, \alpha, D_<)
\end{equation}
$$
</div>
<div class="proof-block" markdown="1">
**Proof of Proposition 4**

It is clear from _proposition_ 3 that $Omega$ is dense in $\widehat{\mathbb{C}}$ there for it suffices to show the existence and definition of both $\alpha$ and $D_<$.

<div class="prop-block" markdown="1">
**Lemma 1**

There exists a bijection $\alpha$ of the form $\mathbb{N} \mapsto \Omega$.
</div>
<div class="proof-block" markdown="1">
**Proof of Lemma 1**

It is clear that $\Omega$ is isomorphic to that of $\mathbb{Q}^2$,
    therefore it suffices to show that $\mathbb{Q}^2$ is denumerable.
In particular,
    It must be shown that a bijection $\alpha: \mathbb{N}^2 \rightarrow \mathbb{Q}^2$ exists.
It is a standard fact of analysis that $\mathbb{Q}$ is denumerable.
Notably the Cartesian product of any two denumerable sets is its denumerable <d-cite key="tao"></d-cite>,
    there $\mathbb{Q}^2$ is denumerable.
Therefore there exists a bijection alpha $\alpha: \mathbb{N} \rightarrow \Omega$ proving our proposition.
</div>

The function $v_\mathbb{Q}$ is that most natural mapping $\mathbb{N} \mapsto \mathbb{Q}$.
Therefore $D_<$ can be described as those the set of natural three tuples for which the $d_{ch}(\alpha(i), \alpha(j)) < v_\mathbb{Q}(k)$.
From **Lemma 1** it is clear that alpha will result in elements of $\Omega$,
    using the chordal metric $d_{ch}$ results in some distance $z \in \mathbb{C}$.
Therefore the set $D_<$ is all those natural three tuples which result in a complex distance on $\widehat{\mathbb{C}}$ which is less than some rational mapping $v_\mathbb{Q}(k)$.

<!-- TODO: The proof of D< is not complete yet -->
<div class="prop-block" markdown="1">
**Lemma 2**

The set $D_<$ is recursively enumerable.
</div>
<div class="proof-block" markdown="1">
**Proof of Lemma 2**

The set $D_<$ defined by Eq. $\eqref{def:D<}$ is that set composed of natural triples satisfying the condition $d_{ch}(\alpha(i), \alpha(j)) < v_\mathbb{Q}$.

$$
\begin{equation} \label{def:D<}
    D_< := \{\langle i, j ,k \rangle : d_{ch}(\alpha(i), \alpha(j)) < v_\mathbb{Q}(k) \}
\end{equation}
$$

To prove a set $A$ is recursively enumerable one must show there exists a partially decidable predicate $x \in A$.
In particular one must prove that some characteristic function $c_A$ exists defined as Eq. $\eqref{def:c_A}$ <d-cite key="cutland"></d-cite>.

$$
\begin{equation} \label{def:c_A}
    c_A(x) = \begin{cases}
        1, \quad &x \in A \\
        \text{undefined}, \quad &x \notin A
\end{cases}
\end{equation}
$$

Notably that predicate defining ownership to a set must be decidable while that predicate of non ownership is undecidable.
This means that **Lemma 2** sets out to prove $\langle i, j, k \rangle \in D_<$ is decidable.
To this end the condition described above must be further investigated.
The chordal metric $d_{ch}$ is defined as Eq. $\eqref{def:dch}$ via <d-cite key="conway"></d-cite>.

$$
\begin{equation} \label{def:dch}
\begin{split}
    d_{ch}(z_1, z_2) &= \frac{2|z_1 - z_2|}{\sqrt{(1 + |z_1|^2)(1 + |z_2|^2)}} \\
    d_{ch}(z, \infty) &= \frac{2}{\sqrt{(1 + |z|^2)}} \rightarrow 0 \\
    z_1,z_2,z &\in \mathbb{C}
\end{split}
\end{equation}
$$

It is clear that given $\alpha: \mathbb{N} \rightarrow \Omega$ we can track the result number ring of the image of $d_{ch}$.
It is trivial to see that $d_{ch}$ given points from $\Omega$ results in numbers from $\mathbb{R}$.
<!-- TODO: demonstrate the existance of this alg -->
The objective is then to show that there exists an algorithm which can show the real number resulting from $d_{ch}(\alpha(i), \alpha(j))$ is less that $v_\mathbb{Q}(\alpha(k))$.
Therefore the set $D_<$ has the characteristic function $c_{D_<}$ defined in Eq. $\eqref{def:c-D<}$.

$$
\begin{equation} \label{def:c-D<}
    c_{D_<} = \begin{cases}
        1,  \quad &\langle i, j, k \rangle \in D_< \\
        \text{undefined}, \quad &\langle i, j, k \rangle \notin D_<
    \end{cases}
\end{equation}
$$

The algorithm that proves the decidability of $\langle i, j, k \rangle \in D_<$ is defined by Eq. $\eqref{def:pred-D<}$ for both cases of $d_{ch}$ (non-infinite and infinite).

$$
\begin{equation} \label{def:pred-D<}
\begin{split}
    \langle i, j, k \rangle \in D_< &\iff d_{ch}(\alpha(i), \alpha(j)) < v_\mathbb{Q}(k) \\
    d_{ch}(\alpha(i), \alpha(j)) &:= \frac{2|\alpha(i) - \alpha(j)|}
        {\sqrt{(1 + |\alpha(i)|^2)(1 + |\alpha(j)|^2)}} \\
    d_{ch}(\alpha(i), \infty) &:= \frac{2}{\sqrt{1 + |\alpha(i)|^2}}
\end{split}
\end{equation}
$$

Concerning the predicate shown in Eq. $\eqref{def:pred-D<}$ it suffices to show that an algorithm exists that can construct the set $D_<$.
One such algorithm would be to iterate through all the natural numbers including infinity and include the resulting element in $D_<$ depending on the condition.

```
function cond(i, j, k) {
    if d_ch(alpha(i), alpha(j)) < v_Q(alpha(k))
        return (i, j, k)
    return None
}

function main() {
    for i, j, k \in (\N union \infty){
        if cond(i, j, k) != None
            D_<.append(cond(i,j,k))
    }
}
```
The code snippet above presents an algorithm constructing the potentially infinite set $D_<$.
Let `alpha` be the $\alpha$ function; let `\N` represent the natural numbers; finally let `\infty` represent infinity as a point $$\{ \infty \}$$.
Notably this construction is not optimal though it does prove to show that such a construction is describable using the standard mechanistic logic (C-style pseudocode).
Therefore the valid triples belonging to $D_<$ can be found via an $n^3$ algorithm searching all combinations of numbers and checking the condition of Eq. $\eqref{def:pred-D<}$.

By the above $D_<$ is proved to be recursively enumerable.
</div>

With the addition of **Lemma 2** it has been proven that there exists a tuple $\bar{M}$ satisfying TTE.
</div>

# Future work
This kind of investigation is quite rewarding though extensions of this work seem substantial comparatively.
One could postulate the construction of such a computable region using research in computable geometry.
There is a possibility that such an exercise could be useful in furthering understanding $\widehat{\mathbb{C}}$ topologically.
In particular in the sense that computational geometry could construct such a region of $\widehat{\mathbb{C}}$ without interpolation or approximation.
I would personally love to see such a construction.
The extensions of the use case for TTE are endless,
    moving forward it will be inevitable to halt curiosity in using the tool to examine such structures.

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
10. $x \notin A$: The element $x$ can not be found in the set $A$.
11. $\bar{U}$: denoting the closure of set $U \subseteq X$ in the space $X$.
