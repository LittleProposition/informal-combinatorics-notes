# Counting Edge-Disjoint Random Cliques

[Read the manuscript (PDF)](./counting-edge-disjoint-random-cliques.pdf)

## Overview

Choose $t$ copies of $K_k$ independently and uniformly from the complete
graph $K_n$. Let

$$
\zeta(n,k,t)
$$

denote the probability that these $t$ random cliques are pairwise
edge-disjoint.

Two cliques may share a vertex, but they are not allowed to share an edge.
Equivalently, no two of the corresponding $k$-subsets of $[n]$ may have
intersection of size at least two.

Acan and Kahn asked how small this probability can be. When

$$
1\ll k\ll \sqrt n,
$$

two independent random $k$-cliques share an edge with probability

$$
(1+o(1))\frac{k^4}{2n^2}.
$$

If collisions between different pairs of cliques behaved independently,
one would therefore expect

$$
\log \zeta(n,k,t)
\sim
-\frac{t^2k^4}{4n^2}.
$$

Acan and Kahn proved the corresponding upper bound in the subcritical range

$$
1\ll t\ll \frac{n^2}{k^3}.
$$

This manuscript determines the sharp exponential rate in the next,
critical range

$$
t=\Theta\left(\frac{n^2}{k^3}\right).
$$

## Main result

Fix constants $0<c\le D<\infty$. As $k\to\infty$ and

$$
\frac{k^2}{n}\to 0,
$$

uniformly for

$$
c\frac{n^2}{k^3}
\le t\le
D\frac{n^2}{k^3},
$$

we prove

$$
\log \zeta(n,k,t)
=
-\left(\frac14+o(1)\right)
\frac{t^2k^4}{n^2}.
$$

Thus the independent-collision heuristic gives the correct exponential
constant throughout the critical range.

The argument also yields a uniform upper bound extending down to all

$$
1\le t\le D\frac{n^2}{k^3}.
$$

More precisely, for every fixed $D>0$ there is
$\varepsilon_D(n,k)\to 0$ such that

$$
\zeta(n,k,t)
\le
\exp\left(
-\left(\frac14-\varepsilon_D(n,k)\right)
\frac{t(t-1)k^4}{n^2}
\right).
$$

The factor $t(t-1)$ is necessary for a statement valid also for bounded
$t$, since $\zeta(n,k,1)=1$.

## Relation to previous work

The problem originates in work of Acan and Kahn on clique packings.

Their results established the predicted upper bound when

$$
1\ll t\ll \frac{n^2}{k^3},
$$

but left open what happens when the number of cliques reaches the critical
scale

$$
t=\Theta\left(\frac{n^2}{k^3}\right).
$$

This range is also relevant to the study of near-maximum clique packings in
random graphs, as discussed by Griffiths and Mattos.

The case

$$
k=\Theta(\log n)
$$

is already of particular interest in this connection.

The proof here treats the upper and lower bounds by two rather different
encodings of the same packing problem.

## The auxiliary intersection graph

For the upper bound, expose the vertices of $K_n$ one at a time.

At any stage, form a graph on the $t$ clique labels, joining two labels once
their cliques have already met at an exposed vertex. If the next vertex is
assigned simultaneously to several clique labels, those labels must form an
independent set in this auxiliary graph; otherwise two cliques would acquire
a second common vertex and hence share an edge.

This converts the counting problem into the estimation of a weighted sum

$$
Z_G(z)
=
\sum_{I\text{ independent in }G} z^{|I|}.
$$

A maximum-degree ordering gives a weighted version of the
Kleitman--Winston argument. The resulting estimate is strong enough to
control the normalization factors in a sequential random construction of
edge-disjoint clique families.

Averaging the construction over a uniformly random ordering of the
vertices of $K_n$ then gives the required upper bound

$$
\log \zeta(n,k,t)
\le
-\left(\frac14-o(1)\right)
\frac{t^2k^4}{n^2}.
$$

## The $C_4$-free bipartite representation

For the lower bound, represent a family of cliques by a bipartite graph.

The left side consists of the $t$ clique labels and the right side consists
of the $n$ vertices of $K_n$. A clique label is joined to the vertices
contained in that clique.

Two clique labels have two common neighbours precisely when this bipartite
graph contains a $4$-cycle. Thus pairwise edge-disjoint clique families
correspond to $C_4$-free bipartite graphs whose left degrees are all equal
to $k$.

The problem is therefore reduced to obtaining sufficiently sharp lower
bounds on the number of sparse labelled bipartite graphs without
$4$-cycles.

## Random greedy counting

To count such bipartite graphs, start with the empty bipartite graph and
repeatedly add a uniformly chosen edge whose addition does not create a
$4$-cycle.

The local behaviour of this process is analysed using the locality theorem
of Krivelevich, Mészáros, Michaeli and Shikhelman for random greedy
algorithms.

Around a fixed edge, the relevant dependency structure converges locally
to a branching process described by asymptotically independent Poisson
numbers of squares. This determines the asymptotic proportion of available
edges during the greedy process.

From this one obtains a lower bound of the form

$$
\frac{(LR)^m}{m!}
\exp\left(
-\frac{m^4}{4L^2R^2}-o(m)
\right)
$$

for the number of labelled $C_4$-free bipartite graphs with parts of sizes
$L$ and $R$ and $m$ edges, while simultaneously ensuring that almost all
left vertices have close to the required degree.

The constant $1/4$ appearing here is exactly the constant needed for the
clique-packing probability.

## Proof outline

The proof has four main components.

### 1. Weighted independent-set estimate

A maximum-degree ordering is used to bound the weighted independent-set
partition function of a graph satisfying a suitable density condition.

This is the basic counting lemma used in the upper bound.

### 2. Sequential encoding of clique packings

The vertices of $K_n$ are exposed in random order.

At each step, the clique labels receiving the current vertex must form an
independent set in the current auxiliary intersection graph. A carefully
chosen weighting of these choices, together with the weighted
independent-set estimate, bounds the probability assigned to any particular
packing.

Averaging over the vertex order and summing these probabilities gives the
upper bound.

### 3. Random greedy $C_4$-free graphs

For the lower bound, clique packings are encoded as $C_4$-free bipartite
graphs.

The random greedy process that avoids creating a $4$-cycle is analysed
through its local limiting search. The locality theorem converts this local
description into asymptotic estimates for the number of accepted and
available edges.

This yields the required exponential count of $C_4$-free bipartite graphs.

### 4. Deleting a small surplus

The random greedy count naturally produces bipartite graphs in which most
left degrees are slightly larger than $k$.

One therefore starts with slightly more than $t$ left vertices and slightly
more than $tk$ edges, keeps $t$ suitable left vertices, retains $k$
neighbours at each, and deletes the surplus.

The entropy cost of this deletion is negligible at the relevant exponential
scale, giving

$$
\log \zeta(n,k,t)
\ge
-\left(\frac14+o(1)\right)
\frac{t^2k^4}{n^2}.
$$

Together with the upper bound, this proves the sharp critical-range
asymptotic.

For smaller $t$, the uniform upper bound is completed by combining the
critical-range argument with the earlier theorem of Acan and Kahn and a
direct inclusion--exclusion calculation when $t$ is bounded.

## External probabilistic input

The main external probabilistic ingredient is the locality theorem for
random greedy algorithms proved by Krivelevich, Mészáros, Michaeli and
Shikhelman.

In the present setting, the underlying elements are the edges of a complete
bipartite graph and the forbidden configurations are the four edges of a
$4$-cycle.

The manuscript verifies the required local convergence and growth
conditions in this specific setting and derives the counting consequence
needed for the lower bound.

## Keywords

Random cliques; clique packings; edge-disjoint cliques; random set systems;
packing probability; $C_4$-free bipartite graphs; random greedy algorithm;
local weak limits; weighted independent sets; Kleitman--Winston method;
probabilistic combinatorics.

## Status

This is a preliminary and unrefereed manuscript. It is posted here so that
researchers interested in random clique packings, packing probabilities,
and related questions of Acan and Kahn can find and examine the result.

The manuscript may be revised or developed further, and a later version may
eventually be submitted for publication.

Comments, corrections, and reports of possible errors are welcome through
GitHub Issues.

## AI assistance

The author selected the problem and guided the overall direction. AI tools
were used extensively in developing the proof. The author then revised,
checked, and independently verified the final argument.
