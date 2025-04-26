# Modular Arithmetic Equivalence Proofs

## Theorem 1: Basic Equivalence

**Given:**
$(x - y) \pmod{m} = k$

**Equivalent Form:**
$y \pmod{m} = (x - k) \pmod{m}$

**Proof:**

Start with the given equation in terms of congruence:
$x - y \equiv k \pmod{m}$

Rearrange the terms to isolate $-y$:
$-y \equiv k - x \pmod{m}$

Multiply both sides by $-1$. Note that multiplying by $-1$ is equivalent to adding $m$ (the modulus) to make it positive in modular arithmetic:
$y \equiv -(k - x) \pmod{m}$
$y \equiv x - k \pmod{m}$

Convert back to the modulo operation:
$y \pmod{m} = (x - k) \pmod{m}$

## Theorem 2: Programming-Robust Version

**Given:**
$(x - y) \pmod{m} = k$

**Equivalent Form (with +m):**
$y \pmod{m} = (x + m - k) \pmod{m}$

**Proof:**

From Theorem 1, we know:
$y \pmod{m} = (x - k) \pmod{m}$

Adding a multiple of the modulus ($m$ in this case) to a number does not change its value modulo $m$:
$(x + m - k) \pmod{m} = (x - k + m) \pmod{m} \equiv (x - k) \pmod{m}$

Therefore:
$y \pmod{m} = (x + m - k) \pmod{m}$

## Why the +m Version Matters in Programming

**Key Differences:**

| Context        | Modulo Behavior                                 | Example (-3 mod 4) |
| -------------- | ----------------------------------------------- | ------------------- |
| Mathematics    | Always non-negative (typically in $[0, m-1]$)   | 1                   |
| Python         | Mathematically correct (sign of divisor)        | 1                   |
| C++/Java       | Can be negative (sign of dividend)            | -3                  |

**Practical Implications:**

Without `+ m` (risky in some languages):
