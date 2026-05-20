# Lecture 01: Problems

1. Verify by truth table: (p ⇒ q) ⇔ (¬q ⇒ ¬p) is a tautology.

   | p | q | ¬p | ¬q | p ⇒ q | ¬q ⇒ ¬p | (p ⇒ q) ⇔ (¬q ⇒ ¬p) |
   |---|---|----|----|-------|---------|----------------------|
   | F | F | T  | T  |  T    |   T     |        T             |
   | F | T | T  | F  |  T    |   T     |        T             |
   | T | F | F  | T  |  F    |   F     |        T             |
   | T | T | F  | F  |  T    |   T     |        T             |

2. Show that p ↑ (p ↑ p) is a tautology, where ↑ is the nand operator.

   | p | p ↑ p | p ↑ (p ↑ p) |
   |---|-------|-------------|
   | F |   T   |     T       |
   | T |   F   |     T       |

3. Let P(x, y) be "x + y = 0" over ℝ. Show that ∀x∃y P(x,y) is true but ∃y∀x P(x,y) is false.

   **∀x∃y: true.** For any x, choose y = −x. Then x + (−x) = 0. ✓

   **∃y∀x: false.** Suppose some y works for all x. Then x + y = 0 for every x, so x = −y for every x. But then every real number equals −y, which is absurd. Alternatively: if y + x₁ = 0 and y + x₂ = 0, then x₁ = −y = x₂, contradicting x₁ ≠ x₂. ✓

4. Given axioms a₁ ⇔ (P ⇒ Q) and a₂ ⇔ P, write a formal proof of Q using the three rules (A), (T), (M).

   | Step | Proposition | Justification |
   |------|-------------|---------------|
   | q₁ | P ⇒ Q | (A) axiom a₁ |
   | q₂ | P | (A) axiom a₂ |
   | q₃ | (P ⇒ Q) ∧ P ⇒ Q | (T) tautology — modus ponens as a logical form |
   | q₄ | Q | (M) q₁ and q₂ are in the proof, (q₁ ∧ q₂) ⇒ q₄ is true (q₃), so we add Q |

5. Prove that ∃!x : P(x) ⇔ (∃x : ∀y : P(y) ⇔ x = y).

   By definition, ∃!x : P(x) := (∃x : P(x)) ∧ ∀y,z : (P(y) ∧ P(z) ⇒ y = z).

   **(⇒)** Assume (∃x : P(x)) ∧ ∀y,z : (P(y) ∧ P(z) ⇒ y = z).

    - Let a be such that P(a). For any y:
    - If P(y), then P(y) ∧ P(a), so y = a (by uniqueness).
    - If y = a, then P(y) = P(a) = true.
    - So P(y) ⇔ y = a, i.e. ∃x : ∀y : P(y) ⇔ x = y. ✓

   **(⇐)** Assume ∃a : ∀y : P(y) ⇔ y = a.

    - Existence: Set y = a. Since a = a, P(a) is true. ✓
    - Uniqueness: If P(y), then y = a. If P(z), then z = a. So y = z. ✓

6. Why can't P ∧ ¬P be proven in propositional logic?

Because propositional logic has no axioms, so the only way to insert things into a proof is via (T) or (M) - combining tautologies, since tautologies are always true and modus ponens preserves truth, every proposition in the proof is true. A contradiction can thus never appear.
