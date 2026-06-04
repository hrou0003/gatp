# Lecture 03: Problems

1. Let φ: ℝ → ℝ, φ(x) = x². Compute preim_φ([0, 4]) and preim_φ({4}).

preim_phi([0, 4]) = { x \in R | phi(x) \in [0, 4]} = [-2, 2]
preim_pi({4}) = {-2, 2}

2. Let M = ℤ and m ∼ n :⇔ 3 | (m − n). Verify this is an equivalence relation and describe ℤ/∼.

  For ~ to be an equivalence relation we need it to satisfy:

  - Reflexivity: take m ~ m = 3 | (m - m) then trivially 3 | 0 which is true trivially.
  - Symmetry: take n ~ m = 3 | (n - m) = 3 | -1 * (m - n) which isn't affected by sign so it is true.
  - Transitivity: take m ~ n and n ~ v, then set v' := m - n and then (m - n) + (n - v) = m - v but both (m - n) and (n - v) have some factor of 3, so 3 * (m' - n') and (n' - v') => 3 | (m - v) 

  Z/~ looks like {[x] : 3 | (x - x')} = {[0], [1], [2]}
  
3. With the same relation, is [a] · [b] := [a · b] well-defined?

  Take a, a' and b, b' then ab - a'b' = (ab - a'b) + (a'b - a'b') then b(a - a') + a'(b - b') since both bracketed expressions are divisible by 3, then the whole expression itself is divisble by 3 and we get the same result, thus well defined.

4. Show that ℚ is countably infinite.

   ℚ = (ℤ × ℤ*)/∼ where ℤ* = ℤ \ {0}.

   - ℤ is countable (list as 0, 1, -1, 2, -2, ...)
   - ℕ × ℕ is countable via Cantor pairing: φ(a, b) = (a + b)(a + b + 1)/2 + a
   - ℤ × ℤ* is countable (product of countable sets)
   - The projection π: ℤ × ℤ* → ℚ is surjective, so |ℚ| ≤ |ℤ × ℤ*|
   - ℚ is infinite, so it's countably infinite.

   ℚ = (ℤ × ℤ*)/∼ where ℤ* = ℤ \ {0}.

   - ℤ is countable (list as 0, 1, -1, 2, -2, ...)
   - ℕ × ℕ is countable via Cantor pairing: φ(a, b) = (a + b)(a + b + 1)/2 + a
   - ℤ × ℤ* is countable (product of countable sets)
   - The projection π: ℤ × ℤ* → ℚ is surjective, so |ℚ| ≤ |ℤ × ℤ*|
   - ℚ is infinite, so it's countably infinite.

5. Prove: a map φ: A → B has an inverse (ψ ∘ φ = id_A, φ ∘ ψ = id_B) iff φ is bijective.

    =>: Given theta * phi = id_A, then bijective which is that it is both injective and surjective.
      - Injection - for every y in B there exists at most one x in A: say there is x != x' s.t. phi(x) = phi(x'), then theta(phi(x)) = theta(phi(x')) = id_A and theta(phi(x)) = id_A but we said x != x' so we have a contradiction.
      - Surjection - every y has at least one x mapping to it: Take a y in B, then take psi(y) \in A which is simply an element x \in A. Now applying phi to both sides, phi(psi(y)) = phi(x) which is y = phi(x) and we have an x which maps to y.
    <=: Given φ is bijective, construct ψ: B → A as follows.
      1. Let b ∈ B
      2. ∃ a ∈ A with φ(a) = b — surjectivity
      3. If φ(a) = φ(a') = b then a = a' — injectivity
      4. Define ψ(b) := a — well-defined by 2,3
      5. Let a ∈ A
      6. ψ(φ(a)) = the a' with φ(a') = φ(a) — definition of ψ
      7. a' = a — injectivity
      8. ψ(φ(a)) = a — from 6,7; so ψ∘φ = id_A
      9. Let b ∈ B
      10. φ(ψ(b)) = b — definition of ψ (ψ(b) was defined as the a with φ(a)=b); so φ∘ψ = id_B

6. Let ∼ be an equivalence relation on M. Prove: either [m] = [n] or [m] ∩ [n] = ∅.

Assume [m] \intersect [n] != \empty, then \exists x \in X := [m] \intersect [n] => x \in [m] and x \in [n] => m ~ x and n ~ x => x ~ n by symmetry => m ~ x and x ~ n => m ~ n by transitivity.

Then a \in [m] with m ~ n => a ~ m by symmetry and then by transitivity a ~ n for arbitrary a => a \in [n].

Similarly, take b \in [n] then b ~ n => n ~ b by symmetry, m ~ n => n ~ m by symmetry, then b ~ m by transitivity => b \in [m].

Thus [m] = [n], or the assumption [m] \intersect [n] is false and [m] ∩ [n] = ∅ holds.
