# Discrete space - Wikipedia

In topology, a discrete space is a particularly simple example of a topological space (or similar structure), one in which the points are isolated from each other. The discrete topology is the finest topology that can be given on a set: every subset is open (and hence also closed); in particular every singleton is open.

### Definitions

* The discrete topology on a set X is the topology in which every subset of X is open (and hence closed). A set X equipped with this topology is a discrete topological space.
* The discrete uniformity on X is the uniformity where every superset of the diagonal {(x,x): x ∈ X} in X × X is an entourage. X with this uniformity is a discrete uniform space.
*   The discrete metric ρ on X is defined by

    $$
    \rho(x,y)=\begin{cases}0 & \text{if } x=y,\\ 1 & \text{if } x\ne y.\end{cases}
    $$

    The metric space (X, ρ) is a discrete metric space (a space of isolated points).
* A discrete subspace of a topological space (Y, τ) is a subset S ⊆ Y endowed with the subspace topology that is the discrete topology.
  * Example: S = {1/2, 1/3, 1/4, …} is a discrete subspace of R (with the Euclidean topology), while S ∪ {0} is not.
* In a metric space (X, d), a set S ⊆ X is discrete if every x ∈ S has δ > 0 such that d(x,y) > δ for all y ∈ S \ {x}. Such a set consists of isolated points.
* S is uniformly discrete in (X, d) if there exists ε > 0 such that for any distinct x, y ∈ S, d(x,y) > ε.
* A metric space (E, d) is uniformly discrete if there exists r > 0 such that for any x ≠ y in E, d(x,y) > r.

Note: the underlying topology of a metric space can be discrete without the metric being uniformly discrete (see proof below and examples).

<details>

<summary>Proof that a discrete space need not be uniformly discrete</summary>

Let X = {2⁻ⁿ : n ∈ N₀} = {1, 1/2, 1/4, 1/8, …} with the usual metric inherited from R. For each xₙ = 2⁻ⁿ ∈ X, choose ε = 1/2 (xₙ − xₙ₊₁) = 2^{−(n+2)}. Then (xₙ − ε, xₙ + ε) ∩ X = {xₙ}, so each singleton {xₙ} is open in the subspace topology, and X is discrete topologically.

However X is not uniformly discrete: if there were r > 0 with d(x,y) > r for all distinct x,y ∈ X, pick n large enough so that 2^{−(n+1)} < r (possible since n can be arbitrarily large). Then adjacent points xₙ and xₙ₊₁ are at distance 2^{−(n+1)} < r, a contradiction. Thus no such r exists and X is not uniformly discrete.

</details>

### Properties

* The underlying uniformity on a discrete metric space is the discrete uniformity; the underlying topology of a discrete uniform space is the discrete topology. The notions are compatible.
* The topology underlying a non-discrete uniform or metric space can still be discrete (e.g., X = {n⁻¹ : n ∈ N} with the usual metric is topologically discrete but not metrically the discrete metric and is not complete as a uniform space).
* Topological dimension of a discrete space is 0.
* A space is discrete iff all singletons are open (equivalently it contains no accumulation points).
* Singletons form a basis for the discrete topology.
* A uniform space X is discrete iff the diagonal {(x,x): x ∈ X} is an entourage.
* Every discrete topological space satisfies all separation axioms (in particular it is Hausdorff).
* A discrete space is compact iff it is finite.
* Every discrete uniform or metric space is complete.
* Every discrete uniform or metric space is totally bounded iff it is finite.
* Every discrete metric space is bounded.
* Every discrete space is first-countable; it is second-countable iff it is countable.
* Every discrete space is totally disconnected.
* Every non-empty discrete space is of second category.
* Any two discrete spaces with the same cardinality are homeomorphic.
* Every discrete space is metrizable (by the discrete metric). A finite space is metrizable only if it is discrete.
* If X is a topological space and Y carries the discrete topology, then X is evenly covered by X × Y (projection is a covering).
* The subspace topology on the integers (as a subset of R) is the discrete topology.
* A discrete space is separable iff it is countable.
* Any topological subspace of R that is discrete is necessarily countable. \[Wilansky 2008, p. 35]

Additional functional and categorical facts:

* Any function from a discrete topological space to another topological space is continuous. Any function from a discrete uniform space to another uniform space is uniformly continuous. Thus the discrete space X is free on the set X in the category of topological spaces (and continuous maps) and in the category of uniform spaces (and uniformly continuous maps).
* For metric categories, freeness depends on the morphisms chosen. The discrete metric space is free when morphisms are uniformly continuous or continuous, and also free in the category of bounded metric spaces with Lipschitz maps (or metric spaces bounded by 1 with short maps).
* Conversely, a function f: Y → X from a topological space Y to a discrete space X is continuous iff it is locally constant (each point of Y has a neighborhood on which f is constant).

Ultrafilter-related topology:

* Given an ultrafilter U on a non-empty set X, the topology τ = U ∪ {∅} has the property that every non-empty proper subset S of X is either open or closed, but never both. In contrast, in the discrete topology every subset is both open and closed.

### Examples and uses

* Discrete structures often serve as the default or extreme example on a set without other natural topology, uniformity, or metric. Any group can be given the discrete topology to become a topological group; algebraic groups considered without topology are often called discrete groups.
* A 0-dimensional (differentiable or analytic) manifold is a discrete countable topological space. Therefore countable discrete groups can be viewed as 0-dimensional Lie groups.
* The product of countably many copies of the discrete space N (natural numbers) is homeomorphic to the space of irrational numbers via continued fraction expansion.
* The product of countably many copies of the discrete space {0,1} is homeomorphic to the Cantor set (uniformly homeomorphic if endowed with the product uniformity), via ternary notation (see Cantor space).
* Every fiber of a locally injective function is a discrete subspace of its domain.
* In foundations of mathematics, compactness properties of products of {0,1} are central to topological approaches to the ultrafilter lemma (Boolean prime ideal theorem), a weak form of the axiom of choice.

### Indiscrete spaces

The opposite of the discrete topology is the trivial (indiscrete) topology, which has the fewest open sets (only ∅ and the whole space). Where the discrete topology is initial/free, the indiscrete topology is final/cofree: every function from a topological space to an indiscrete space is continuous.

### See also

* Cylinder set
* List of topologies
* Taxicab geometry

### References

1. Pleasants, Peter A.B. (2000). "Designer quasicrystals: Cut-and-project sets with pre-assigned properties". In Baake, Michael (ed.). Directions in mathematical quasicrystals. CRM Monograph Series. Vol. 13. Providence, RI: American Mathematical Society. pp. 95–141. ISBN 0-8218-2629-8. Zbl 0982.52018.
2. Wilansky, Albert (17 October 2008) \[1970]. Topology for Analysis. Mineola, New York: Dover Publications, Inc. ISBN 978-0-486-46903-4. (Wilansky 2008, p. 35)

Further reading:

* Steen, Lynn Arthur; Seebach, J. Arthur Jr. (1978). Counterexamples in Topology (2nd ed.). Springer-Verlag. ISBN 3-540-90312-7.

Retrieved from https://en.wikipedia.org/w/index.php?title=Discrete\_space\&oldid=1331155264
