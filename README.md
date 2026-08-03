# Multiplicative-Order Parametrized Digraphs

Computational verification code and manuscript source for the article
*Multiplicative-Order Parametrized Digraphs*, in preparation for submission to
the (PLACEHOLDER).

**Author:** William Kau&atilde; Soares da Silva (Universidade Federal Rural de Pernambuco)

## Overview

For a set $\mathcal{P} = \{p_1, \dots, p_n\}$ of distinct odd primes and a
positive integer $m$, the digraph $\Xi_m(\mathcal{P})$ has vertex set
$\mathcal{P}$ and an edge from $p_i$ to $p_j$ exactly when
$p_i^{m} \equiv 1 \pmod{p_j}$. Writing $r_{ij} = \operatorname{ord}_{p_j}(p_i)$,
an edge is present exactly when $r_{ij} \mid m$, so the family
$\Xi(\mathcal{P})$ swept out by $m$ is finite and is governed entirely by the
multiset of the $n(n-1)$ multiplicative orders.

The article studies three nested classes of prime sets defined by conditions on
these orders:

- **Realizing sets** ($\mathcal{R}_n$): every one of the $2^{n(n-1)}$ digraphs
  on $\mathcal{P}$ is realized by some exponent. Characterized by
  lcm-independence of the orders; infinitely many exist for every $n$
  (proved unconditionally via Kummer theory and the Chebotarev density theorem).
- **Pairwise coprime sets** ($\mathcal{R}_n^{\mathrm{c}}$): the orders are
  pairwise coprime. Characterized as the exact condition under which the
  realization densities form a product measure (edges become independent
  events).
- **Aligned sets** ($\mathcal{R}_n^{\mathrm{a}}$): the orders are prime and
  pairwise distinct. Characterized as the exact condition under which the map
  from divisors of the fundamental exponent to digraphs is a Boolean algebra
  isomorphism.

Aligned sets exist for $n = 2$ (e.g. $\{3, 11\}$); none of cardinality
$n \geq 3$ is known. The article proves unconditional constraints on such sets
(a divisibility constraint on each column, and a cyclotomic confinement theorem
reducing the search space to the prime divisors of explicit integers) and
conjectures that no aligned set of cardinality $n \geq 4$ exists. The case
$n = 3$ is left open.

## Repository contents

- `manuscript/` &mdash; LaTeX source of the article (E-JC house style).
- `code/` &mdash; Python scripts (sympy/numpy) implementing the computational
  searches reported in the article:
  - exhaustive triangle search over all odd primes below $3 \times 10^{5}$
    for aligned triples;
  - cyclotomic-confinement search: for each prime $p < 100$ and each prime
    $r \leq 23$, complete factorization of $\Phi_r(p)$ and inspection of all
    resulting candidate pairs, with no upper bound on the candidates;
  - independent recomputation routines used to cross-check every reported
    order.
- `data/` &mdash; append-only CSV database of computed orders with canonical
  key ordering, JSONL run logs with watermarking for crash recovery, and
  coverage tracking per search pool.

## Reproducibility

Every computational claim in the article is intended to be independently
reproducible from this repository. Each search script records its parameters,
its input range, and a run log; duplicate detection and canonical ordering of
keys guarantee that reported counts are stable across re-runs. Orders reported
by any search are recomputed by an independent routine before being cited in
the manuscript.

Requirements: Python 3.10+, `sympy`, `numpy`.

```bash
pip install sympy numpy
python code/triangle_search.py --bound 300000
```

(Adjust script names and options to the actual entry points.)

## Status

The manuscript is in preparation. Theorems on realizing sets, pairwise coprime
sets and aligned sets are complete with full proofs; the non-existence
statement for aligned sets of cardinality $n \geq 4$ is a conjecture, supported
by the computational evidence above and by a heuristic count, and is explicitly
distinguished from the proved results throughout.

## License

- Manuscript: &copy; The author.
- Code: MIT License (see `LICENSE`).

## Citation

Until the article is published, please cite this repository directly:

```
W. K. Soares da Silva. Multiplicative-Order Parametrized Digraphs:
computational verification code. GitHub repository, 2026.
```
