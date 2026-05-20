# Lecture 01: Propositional Logic

## Propositions

A **proposition** is a logical variable which can only have the value true (T) or false (F), and no others.

Example: P: "it is raining" is either true or false (given a location and time). Propositional logic doesn't examine *why* it's true or false — it just assumes it has one of those two values.

## Tautologies and contradictions

A **tautology** is a proposition whose truth table is all T — true regardless of the truth values of its components. A **contradiction** is all F.

Examples of tautologies: P ∨ ¬P, (P ⇒ Q) ⇔ (¬Q ⇒ ¬P), ((P ⇒ Q) ∧ P) ⇒ Q

Example of a contradiction: P ∧ ¬P

This is a **structural property** of the proposition's logical form, not of what the variables represent.

## Binary operators

There are 2⁴ = 16 possible binary operators (each of the 4 input combinations maps to T or F). The named ones:

| p | q | p ∧ q | p ∨ q | p ⊻ q | p ⇒ q | p ⇔ q |
|---|---|-------|-------|-------|-------|-------|
| F | F | F     | F     | F     | T     | T     |
| F | T | F     | T     | T     | T     | F     |
| T | F | F     | T     | T     | F     | F     |
| T | T | T     | T     | F     | T     | T     |

The remaining 11 have no standard names. One of them — **nand** (p ↑ q :⇔ ¬(p ∧ q)) — is special: every operator can be built from nand alone.

### Implication (⇒)

P ⇒ Q is false *only* when P is true and Q is false. It does **not** mean "if P then Q" causally. It means: "P and ¬Q cannot both hold."

**Contrapositive:** (P ⇒ Q) ⇔ (¬Q ⇒ ¬P) — equivalent.

**Converse:** Q ⇒ P — *not* equivalent to P ⇒ Q.

Example: "If it's raining, the ground is wet" (P ⇒ Q). Contrapositive: "If the ground isn't wet, it's not raining" (equivalent). Converse: "If the ground is wet, it's raining" (not equivalent — could be a hose).

When P is false, P ⇒ Q is **vacuously true** regardless of Q. ("Ex falso quodlibet" — from a false assumption, anything follows.)

Binding strength (decreasing): ¬, ∧, ∨, ⇒, ⇔. This is a notational convention for parsing expressions without parentheses — not a structural property of the operators.

## Predicate logic

**Predicates** — A predicate P(x) is a proposition-valued function of a formal variable x. At this stage in the course, x is just a symbol with no type or domain — we deliberately don't ask "what does x range over" because sets haven't been defined yet. The logical language comes first; sets are built from it.

A predicate of two variables, Q(x, y), is called a **relation**.

### Quantifiers

From a predicate P(x), we build new propositions:

- **Universal:** ∀x : P(x) — "P(x) is true independently of x"
- **Existential:** ∃x : P(x) :⇔ ¬(∀x : ¬P(x)) — "there exists at least one x such that P(x)"
- **Unique existential:** ∃!x : P(x) — "there exists exactly one x such that P(x)"

Negation rules: ¬(∀x : P(x)) ⇔ ∃x : ¬P(x), and ¬(∃x : P(x)) ⇔ ∀x : ¬P(x).

**Order of quantification matters.** ∀x∃y ≠ ∃y∀x in general. The reversed order is stronger — it claims a single y works for all x simultaneously.

Example (over ℝ): ∀x : ∃y : x + y = 0 is true (y = −x). But ∃y : ∀x : x + y = 0 is false (no single y works for all x).

## Axiomatic systems and proofs

An **axiomatic system** is a finite sequence of propositions a₁, …, a_N (the axioms).

A **proof** of p is a finite sequence q₁, …, q_M = p where each q_j satisfies one of:
- **(A)** q_j is an axiom
- **(T)** q_j is a tautology
- **(M)** ∃ m,n < j : (q_m ∧ q_n ⇒ q_j) is true (modus ponens)

If p is provable, we write a₁, …, a_N ⊢ p.

### The three rules

These aren't assumptions — they're the **definition** of what counts as a valid proof. They're the rules of the game:

- **(A)** lets you copy an axiom into your proof (start from assumptions)
- **(T)** lets you insert any tautology (pre-built logical tool, always available)
- **(M)** lets you combine two things already in your proof to derive a new thing (the "reasoning" step)

A tautology inserted by (T) can serve as a tool for (M). Example: ((P ⇒ Q) ∧ P) ⇒ Q is a tautology — you insert it by (T), then use it to derive Q from P ⇒ Q and P by (M).

### Consistency

An axiomatic system is **consistent** if there exists a proposition q that cannot be proven:
∃q : ¬(a₁, …, a_N ⊢ q)

A system with contradictory axioms (both P and ¬P) can prove *anything*, since P ∧ ¬P ⇒ q is a tautology for any q. So consistency means the system isn't this powerful.

**Theorem.** Propositional logic is consistent. (No axioms → only tautologies are provable → contradictions like P ∧ ¬P can't be proven.)

### Gödel's incompleteness theorem

Any axiomatic system powerful enough to encode elementary arithmetic is either inconsistent or contains an undecidable proposition (neither provable nor disprovable).

**Proof sketch (self-reference via Gödel numbering):**

1. Encode every formula as a number (Gödel numbering). "Formula n is provable" becomes an arithmetic statement — expressible within the system.
2. Define D(x) := ¬Prov(sub(x)), where sub(n) returns the Gödel number of D(n).
3. Let n = Gödel number of D(x). Construct G = D(n).
4. G = ¬Prov(Gödel number of G). So G says "I am not provable."
5. If G is provable → system proves something false → inconsistent.
6. If G is not provable → G is true but unprovable → incomplete.

∴ The system is either inconsistent or incomplete.
