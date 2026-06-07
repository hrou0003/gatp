# Lecture 05: Topological Invariants

Properties preserved by homeomorphisms — tools for distinguishing topological spaces.

## 5.1 Separation properties

**T1:** For distinct p, q ∈ M, ∃ open U(p) with q ∉ U.

**T2 (Hausdorff):** For distinct p, q ∈ M, ∃ disjoint open neighbourhoods U(p), V(q).

Examples:
- (ℝᵈ, 𝒪_std) is T2 (hence T1)
- Zariski topology: T1 but not T2
- Chaotic topology {∅, M}: neither T1 nor T2

## 5.2 Compactness and paracompactness

**Cover:** C ⊆ 𝒫(M) with ⋃ C = M. **Open cover** if C ⊆ 𝒪.

**Subcover:** C̃ ⊆ C still a cover.

**Compact:** every open cover has a finite subcover.

### Heine-Borel theorem

In (ℝᵈ, 𝒪_std): compact ⟺ closed and bounded.

Proof sketch: (⟹) bounded: cover with balls of radius 1, finite subcover gives bounded. Closed: if p ∉ M, each point of M has an open neighbourhood not containing p (Hausdorff), finite subcover gives a neighbourhood of p disjoint from M. (⟸) bisection: enclose in a box, split in half. One half has no finite subcover. Repeat — nested boxes shrink to a point. That point is in M (closed), so covered by some open set in the cover, which covers a whole neighbourhood — contradiction.

Examples:
- [0, 1] is compact
- ℝ is not compact (cover {(n, n+1) | n ∈ ℤ} has no finite subcover)
- (0, 1) is not compact

Product of compact spaces is compact. By induction, any finite product of compact spaces is compact (finite case of Tychonoff's theorem; the full theorem for arbitrary products requires the axiom of choice).

### Paracompactness

A refinement R of cover C: ∀U ∈ R : ∃V ∈ C : U ⊆ V. **Locally finite:** for every p ∈ M, there exists an open neighbourhood U of p such that U ∩ Ũ ≠ ∅ for only finitely many Ũ ∈ C̃. Around every point, only finitely many sets in the cover "touch" that neighbourhood.

**Paracompact:** every open cover has an open locally finite refinement. Compact ⟹ paracompact. Every metrisable space is paracompact (Stone's theorem).

Any subcover is a refinement (each set is contained in itself), but not vice versa — a refinement can introduce new sets not in the original cover, as long as each fits inside some original set. So paracompactness is strictly weaker than compactness.

### Partitions of unity

Set F of continuous maps f: M → [0, 1] with Σ f(p) = 1 (locally finite). Subordinate to cover C if each f is supported in some U ∈ C.

**Theorem.** Hausdorff space is paracompact ⟺ every open cover admits a subordinate partition of unity.

## 5.3 Connectedness and path-connectedness

**Connected:** ¬∃ open, non-empty, disjoint A, B with M = A ∪ B. Equivalently: only ∅ and M are both open and closed.

**Path-connected:** ∀p, q ∈ M, ∃ continuous γ: [0,1] → M with γ(0) = p, γ(1) = q.

**Theorem.** Path-connected ⟹ connected. Converse false (topologist's sine curve).

Example: ℝ \ {0} is not connected.

## 5.4 Homotopy and the fundamental group

### Homotopic curves

γ, δ: [0,1] → M with same endpoints are **homotopic** if ∃ continuous h: [0,1]² → M deforming γ to δ. This is an equivalence relation.

### Loop space and fundamental group

L_p := {γ: [0,1] → M | continuous, γ(0) = γ(1) = p}

Concatenation: (γ ∗ δ)(λ) = γ(2λ) for λ ∈ [0, 1/2], δ(2λ−1) for λ ∈ [1/2, 1].

**Fundamental group:** π₁(p) := L_p / ∼ with [γ] • [δ] := [γ ∗ δ].

- Identity: constant curve γ_e(λ) = p
- Inverse: −γ(λ) = γ(1 − λ)

Group-valued invariant (not just boolean).

### Examples

| Space | π₁ |
|-------|-----|
| S² (sphere) | trivial {1} |
| S¹ × ℝ (cylinder) | ℤ |
| T² (torus) | ℤ × ℤ |

No complete classification of topological spaces by known invariants exists.
