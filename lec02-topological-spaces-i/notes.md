# Lecture 02: Axioms of Set Theory

## The ∈-relation

Set theory is built on a single primitive relation ∈ (read "epsilon"). ∈ is not defined — it's axiomatised. We don't say what it *means*, we say when it's *meaningful*.

Derived relations:
- x ∉ y :⇔ ¬(x ∈ y)
- x ⊆ y :⇔ ∀a : (a ∈ x ⇒ a ∈ y)
- x = y :⇔ (x ⊆ y) ∧ (y ⊆ x)
- x ⊂ y :⇔ (x ⊆ y) ∧ ¬(x = y)

## Zermelo-Fraenkel axioms (ZFC) — 9 axioms

### Axiom 1: The ∈-relation

x ∈ y is a proposition if and only if both x and y are sets:
∀x : ∀y : (x ∈ y) ⊻ ¬(x ∈ y)

This tells us when something is *not* a set. Russell's paradox: {x | x ∉ x} is not a set, because u ∈ u would be neither true nor false.

### Axiom 2: Empty set

∃y : ∀x : x ∉ y.

There exists a set with no elements. Unique, denoted ∅.

### Axiom 3: Pair sets

∀x : ∀y : ∃m : ∀u : (u ∈ m ⇔ (u = x ∨ u = y))

Given sets x and y, there exists a set containing exactly x and y. Denoted {x, y}. Unordered: {x, y} = {y, x}.

Also gives singletons: {x} := {x, x}.

Ordered pair: (x, y) := {x, {x, y}}. Satisfies (x, y) = (a, b) ⇔ x = a ∧ y = b.

### Axiom 4: Union sets

∀x : ∃u : ∀y : (y ∈ u ⇔ ∃s : (y ∈ s ∧ s ∈ x))

Given a set x, there exists a set whose elements are the elements of the elements of x. Denoted ⋃x.

Example: ⋃{{a}, {b, c}} = {a, b, c}. This "flattens" one level of nesting.

This is what lets you build sets with more than 2 elements: {a, b, c} = ⋃{{a}, {b, c}}.

### Axiom 5: Replacement

Let R be a functional relation (∀x : ∃!y : R(x, y)) and m a set. Then the image of m under R is a set.

Example: if m = {1, 2, 3} and R(x, y) :⇔ y = x², then im_R(m) = {1, 4, 9} is a set.

This is not provable from the other axioms — they can combine existing sets but can't "transform" a set via a functional relation. Added by Fraenkel to Zermelo's original axioms.

### On axioms and consistency

Axioms are chosen because they're useful and consistent, not because they're obvious. An axiom is *independent* if it can't be proved or disproved from the other axioms.

Key points:
- Removing an axiom can never cause inconsistency — fewer axioms means fewer things provable, not more contradictions.
- Adding an axiom is safe if it's consistent with the existing ones (doesn't introduce contradictions).
- The axiom of replacement is independent — Zermelo set theory (without it) is consistent but weaker.

### Axiom 6: Power sets

∀x : ∃y : ∀a : (a ∈ y ⇔ a ⊆ x)

Given a set x, there exists a set whose elements are all the subsets of x. Denoted 𝒫(x).

Example: 𝒫({a, b}) = {∅, {a}, {b}, {a, b}}.

### Axiom 7: Infinity

∃x : ∅ ∈ x ∧ ∀y : (y ∈ x ⇒ {y} ∈ x)

Guarantees a set containing ∅ and, whenever it contains y, also contains {y}. This gives:
x = {∅, {∅}, {{∅}}, {{{∅}}}, ...}

This is how we construct the natural numbers: 0 := ∅, 1 := {∅}, 2 := {{∅}}, etc. Without this axiom, ℕ can't be proven to exist.

### Axiom 8: Choice

Given a set whose elements are non-empty and mutually disjoint, there exists a set containing exactly one element from each.

Non-constructive: it asserts a selection exists without specifying how to make it. This leads to counterintuitive results (Banach-Tarski paradox) but is consistent and standard.

A **paradox** is surprising but not logically contradictory. An **inconsistency** is a genuine contradiction (both P and ¬P provable). The Banach-Tarski paradox is paradoxical but not inconsistent.

### Axiom 9: Foundation

∀x : (∃a : a ∈ x) ⇒ ∃y ∈ x : ⋂{x, y} = ∅

Every non-empty set x contains an element y that shares nothing with x (y ∩ x = ∅).

**Consequence: no set contains itself.** Suppose x ∈ x. Consider {x}. By foundation, {x} must contain an element y with y ∩ {x} = ∅. The only candidate is y = x. But x ∈ x (assumption) and x ∈ {x} (definition), so x ∈ x ∩ {x}, meaning x ∩ {x} ≠ ∅. Contradiction. ∎

---

ZFC = all 9 axioms together (Zermelo-Fraenkel with Choice).
