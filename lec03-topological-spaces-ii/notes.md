# Lecture 03: Classification of Sets (Review)

## Maps

φ: A → B is a relation where each a ∈ A has exactly one b ∈ B with φ(a, b).

- **Injective:** φ(a₁) = φ(a₂) ⇒ a₁ = a₂
- **Surjective:** im φ = B
- **Bijective:** both. Structure-preserving maps for sets: A ≅_set B iff ∃ bijection.

**Composition:** ψ ∘ φ, associative. **Inverse:** φ⁻¹ exists iff φ is bijective.

**preim_φ(V)** := {a ∈ A | φ(a) ∈ V}. Preserves ∅, complements, unions, intersections.

## Equivalence relations

∼ on M: reflexive, symmetric, transitive. **Equivalence class:** [m] := {n | m ∼ n}.

Key: a ∈ [m] ⇒ [a] = [m]; classes are either equal or disjoint.

**Quotient:** M/∼ := {[m]}. Maps on quotients defined via representatives must be checked for well-definedness.

## Classification by cardinality

- **Finite:** A ≅_set {1, …, N}, |A| = N
- **Countably infinite:** A ≅_set ℕ
- **Uncountably infinite:** infinite but not countable

## Building number systems

- ℕ from axiom of infinity (0 := ∅, 1 := {∅}, 2 := {{∅}}, …)
- ℤ = (ℕ × ℕ)/∼, ℚ = (ℤ × ℤ*)/∼, ℝ = (set of almost-homomorphisms)/∼
