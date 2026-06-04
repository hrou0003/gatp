# Lecture 03: Classification of Sets (Review)

## Maps

A map φ: A → B is a relation between two sets where for each a ∈ A there is **exactly one** b ∈ B with φ(a, b). "Map" and "function" mean the same thing in this course.

The existence half ("for each x there is a y") is what makes it a function-like object; the uniqueness half ("exactly one y") is what rules out e.g. y² = x as a map ℝ → ℝ (since x = 4 would map to both 2 and -2).

Properties on top of being a map:

- **Injective:** distinct inputs go to distinct outputs. Equivalently, φ(a₁) = φ(a₂) ⇒ a₁ = a₂. Says something about the *reverse* direction: each y has **at most one** x mapping to it (some y's may have none). Example: eˣ: ℝ → ℝ is injective even though y = -1 has no preimage.
- **Surjective:** every y ∈ B has **at least one** x ∈ A mapping to it. Equivalently, im φ = B. Note: surjectivity depends on the codomain — eˣ is not surjective ℝ → ℝ but is surjective ℝ → (0, ∞).
- **Bijective:** both injective and surjective. Each y has *exactly one* preimage. Two consequences worth holding onto:
  1. **Invertibility:** bijective ⟺ φ has a two-sided inverse ψ with ψ ∘ φ = id_A, φ ∘ ψ = id_B (problem 5).
  2. **Sameness of sets:** A ≅_set B iff there exists a bijection A → B. Cardinality is the equivalence class under this relation. Bijection is the "structure-preserving" map for sets.

**Composition:** given φ: X → Y and ψ: Y → Z, the composition is (ψ ∘ φ)(x) := ψ(φ(x)) — apply φ first, then ψ. The codomain of φ must match the domain of ψ for this to make sense.

- Not commutative in general: ψ ∘ φ ≠ φ ∘ ψ. Often the types don't even line up to allow both directions. Example: f(x) = x², g(x) = x + 1 on ℝ — f(g(x)) = (x+1)² but g(f(x)) = x² + 1.
- Associative: h ∘ (g ∘ f) = (h ∘ g) ∘ f, since both unpack to h(g(f(x))). So we drop the parens and write h ∘ g ∘ f.

**Inverse:** φ⁻¹ exists iff φ is bijective.

**Preimage:** for a subset V ⊆ B, define `preim_φ(V) := {a ∈ A | φ(a) ∈ V}`. It's an operator on *subsets of the codomain*, not on individual elements, so it's defined for any map — no need for φ to be invertible or surjective. If V contains values φ never reaches, the preimage is just ∅.

Don't confuse with φ⁻¹ as an inverse map: that only exists when φ is bijective. `preim_φ(V)` is a separate notion that always makes sense.

The preimage operator preserves all the basic set operations:
- preim_φ(∅) = ∅
- preim_φ(V ∪ W) = preim_φ(V) ∪ preim_φ(W)
- preim_φ(V ∩ W) = preim_φ(V) ∩ preim_φ(W)
- preim_φ(B ∖ V) = A ∖ preim_φ(V)

All four follow by unpacking the definition and distributing the logical connective. Contrast with the forward image, which is *not* as well-behaved (e.g. im_φ(A ∩ B) can be strictly smaller than im_φ(A) ∩ im_φ(B); example: φ(x) = x², A = {2}, B = {-2}).

## Equivalence relations

A relation ∼ on M is an **equivalence relation** if it satisfies:
- **Reflexive:** x ∼ x
- **Symmetric:** x ∼ y ⇒ y ∼ x
- **Transitive:** x ∼ y and y ∼ z ⇒ x ∼ z (note: ⇒, not ⇔)

These three axioms abstract what makes equality work — the minimum needed to consistently declare "x and y are the same for our purposes". Examples: ordinary equality, modular congruence, "has the same parent".

**Equivalence class:** [m] := {n ∈ M | m ∼ n}.

The three properties exist to make classes partition M cleanly:
- Reflexive guarantees every x lives in *some* class (namely [x], since x ∼ x).
- Symmetric + transitive together rule out partial overlap: if [a] ∩ [b] ≠ ∅, sharing some y, then a ∼ y and b ∼ y gives a ∼ b (via symmetric + transitive), so [a] = [b].

**Partition theorem:** equivalence relations on M ↔ partitions of M. Given ∼, the classes partition M; given a partition, "same block" is an equivalence relation. Problem 6 of this lecture is the key half: `[m] = [n]` or `[m] ∩ [n] = ∅`.

**Quotient:** M/∼ := {[m] | m ∈ M}. The set of equivalence classes.

**Well-definedness on quotients.** A map on M/∼ is **well-defined** if its output doesn't depend on which representative you pick from each class. Since `[a]` is a set (not a single element), any formula like `f([a]) := [a²]` secretly involves choosing a representative `a`. If someone else picks `a' ∈ [a]`, they must land in the same output class: `f([a']) = f([a])`.

So you must verify:

> if `a ∼ a'`, then the output class is the same.

For binary operations like `[a] · [b] := [a · b]`, this becomes: if `a ∼ a'` and `b ∼ b'`, then `a · b ∼ a' · b'`.

Example: define `f: ℤ/∼ → ℤ/∼` by `f([a]) := [a²]`, with `m ∼ n :⇔ 3 | (m − n)`. Check: if `3 | (a − a')`, does `3 | (a² − (a')²)`? Factor via difference of squares: `a² − (a')² = (a − a')(a + a')`. Since `3 | (a − a')`, it divides the product. So `a² ∼ (a')²`, and `f` is well-defined.

Example (binary operation): is `[a] · [b] := [a · b]` well-defined on `ℤ/∼`? Assume `a ∼ a'` and `b ∼ b'`, i.e. `3 | (a − a')` and `3 | (b − b')`. Need to show `3 | (ab − a'b')`. Decompose: `ab − a'b' = b(a − a') + a'(b − b')`. Each term has a factor divisible by 3, so the sum is too. Hence `ab ∼ a'b'`.

Without this check, the "function" might give different outputs for the same input depending on which representative you picked — i.e. it wouldn't actually be a function.

## Classification by cardinality

- **Finite:** A ≅_set {1, …, N}, |A| = N
- **Countably infinite:** A ≅_set ℕ
- **Uncountably infinite:** infinite but not countable

## Building number systems

Each successive number system is built from the previous one by quotienting a bigger set by an equivalence relation that identifies "different representations of the same thing".

**ℕ** comes from the axiom of infinity directly:

> 0 := ∅, 1 := {∅}, 2 := {{∅}}, …

No quotient needed — the axiom hands you a set with the right structure.

**ℤ = (ℕ × ℕ)/∼** with `(a, b) ∼ (c, d) :⇔ a + d = b + c`.

Intuition: think of a pair `(a, b)` as encoding the integer `a − b`. We can't actually write `a − b` (subtraction doesn't exist in ℕ — there's no `−1`), so rearrange `a − b = c − d` as `a + d = b + c`, using only addition. Negative integers like `−5` show up as the class `[(0, 5)]`.

**ℚ = (ℤ × ℤ*)/∼** with `(p, q) ∼ (u, v) :⇔ p · v = q · u`. Here `ℤ* = ℤ ∖ {0}`.

Intuition: `(p, q)` encodes the rational `p/q`. Equal rationals satisfy `p/q = u/v`, i.e. `p · v = q · u` (cross-multiply). Exclude `q = 0` since division by zero isn't a rational. The same fraction has many representations: `(1, 2), (2, 4), (3, 6), …` all live in the same class.

**ℝ = (almost-homomorphisms)/∼.** A real number is an equivalence class of functions `f: ℤ → ℤ` that are "almost additive": the discrepancy `f(m + n) − f(m) − f(n)` stays bounded as `m, n` range over ℤ. Two such functions are equivalent if `f − g` is bounded. This is the Eudoxus/Arthan construction — less common than Cauchy sequences of rationals or Dedekind cuts, but the same general pattern: a bigger set of "encodings" quotiented by an equivalence that identifies redundancies.

Pattern across all three: each ∼ is exactly the relation needed to make the "encoding → number" map well-defined on classes.
