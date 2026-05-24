# Lecture 02: Problems

1. Show that {x | x ∉ x} cannot be a set (Russell's paradox).

Let u = { x | x ∉ x } and assume that it is a set.
Then by axiom 1, u being set implies that u ∈ u is a proposition.
Assuming that u ∈ u, then such an x being u is contradicted by x ∉ x.
Assuming that u ∉ u, then the condition is satisfied and in fact u ∈ u. But this is a contradiction.
Our assumptions are contradicted therefore u is not a set.

2. Prove that (x, y) := {x, {x, y}} satisfies (x, y) = (a, b) ⇒ x = a ∧ y = b.

Take (x, y) = (a, b), then by definition {x, {x, y}} = {a, {a, b}}.
Then x is in the right side, so x = a or x = {a, b}.
If x = a, then {a, {a, y}} = {a, {a, b}}, so {a, y} = {a, b}, so y = a or y = b.
If y = a, then {a, a} = {a, b} forces a = b.
If y = b, done.
If x = {a, b}, this leads to a ∈ a, violating foundation. Not possible.

3. Construct {a, b, c} explicitly from the ZFC axioms (pair set and union axioms only).

Assume a, b and c are sets.
Then {a, a} is a set and {b, c} is a set and {{a}, {b, c}} is a set by the pair axiom.
By the union axiom, {a, b, c} is also a set.

4. Compute 𝒫(𝒫(∅)).
∅ = {}
𝒫(∅)) = {{}}
𝒫(𝒫(∅)) = {{}, {{}}}

5. Derive the principle of restricted comprehension ({y ∈ m | P(y)} is a set) from the axiom of replacement.

  Conceptual trick: we want to use replacement to carve out the P-satisfying elements of m, but replacement needs a *functional* relation (∀x ∃!y R(x, y)) — every x must go somewhere. The naive "send non-P elements to a fixed c ∈ m with P(c)" fails when no such c exists. Instead, wrap each P-element as a singleton {x} and dump every non-P element into ∅. Replacement then gives a set whose elements are the {x}'s plus possibly ∅. Taking ⋃ recovers the x's (singletons flatten) and erases the ∅ (it contributes nothing to a union). The two transformations cancel for the wanted elements and annihilate the unwanted ones, with no edge case to handle separately.

  Define R(x, y) :⇔ (P(x) ∧ y = {x}) ∨ (¬P(x) ∧ y = ∅).

  R is a functional relation. For any x, axiom 1 gives exactly one of P(x), ¬P(x):
    - Existence: if P(x), take y = {x} (a set by the pair axiom, since {x} = {x, x}); if ¬P(x), take y = ∅ (a set by axiom 2).
    - Uniqueness: the two disjuncts have mutually exclusive hypotheses, so only one can fire, and within each disjunct y is pinned (to {x} or to ∅).

  Note that R is well-defined unconditionally — no element of m needs to be chosen.

  Applying replacement to R and m, the image

      im_R(m) := { y | ∃x ∈ m : R(x, y) }

  is a set. By the union axiom, ⋃ im_R(m) is also a set. We claim ⋃ im_R(m) = {y ∈ m | P(y)}.

  (⊆) Let z ∈ ⋃ im_R(m). Then there exists s ∈ im_R(m) with z ∈ s, and there exists x ∈ m with R(x, s). Either s = {x} (and P(x)), in which case z ∈ {x} forces z = x ∈ m with P(z); or s = ∅, in which case z ∈ ∅ is impossible. So z ∈ m and P(z).

  (⊇) Let z ∈ m with P(z). Then R(z, {z}) holds via the first disjunct, so {z} ∈ im_R(m). Since z ∈ {z}, we have z ∈ ⋃ im_R(m).

  Edge case is automatic: if no x ∈ m satisfies P, then im_R(m) = {∅}, and ⋃ {∅} = ∅ = {y ∈ m | P(y)}.


6. Prove that the empty set is unique (using only Axioms 1 and 2).

   Suppose x and x' are both empty.

   | y ∈ x | y ∈ x' | y ∈ x ⇒ y ∈ x' |
   |-------|--------|-----------------|
   | F     | F      | T               |

   Since x is empty, y ∈ x is false for all y. So (y ∈ x ⇒ y ∈ x') is vacuously true for all y, giving x ⊆ x'. Same argument gives x' ⊆ x. By definition of =, x = x'.
