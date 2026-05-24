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

  We need to define a functional relation R(x, y) on m. 
  For each x:
  

6. Prove that the empty set is unique (using only Axioms 1 and 2).

   Suppose x and x' are both empty.

   | y ∈ x | y ∈ x' | y ∈ x ⇒ y ∈ x' |
   |-------|--------|-----------------|
   | F     | F      | T               |

   Since x is empty, y ∈ x is false for all y. So (y ∈ x ⇒ y ∈ x') is vacuously true for all y, giving x ⊆ x'. Same argument gives x' ⊆ x. By definition of =, x = x'.
