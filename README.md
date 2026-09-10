![License](https://img.shields.io/badge/license-Apache--2.0-blue)
![Live Demo](https://img.shields.io/badge/demo-live-00e5a0)
![Complexity](https://img.shields.io/badge/decomposition-O(1)-7b61ff)

# D³ · Deterministic Data Decomposition by A-C Coupling

### 🔗 [Try the live demo](https://a19dammer91.github.io/D3-by-A-C-Coupling-Demo/)

**D³** stands for the three D's at the core of the pattern:

- **D**eterministic: for any input N, the decomposition is fully determined. No randomness, no ambiguity, the result is always the same.
- **D**ata: the pattern operates on any integer-valued data (amounts, quantities, counts), not just currency.
- **D**ecomposition: N is broken down into a fixed set of structural layers via a greedy algorithm, reducing it to a single anchor value A₀ = dr(N).

Combined with **A-C Coupling** (the relationship between the anchor value A₀ and the coefficient set C = [19, 9, 3, 3, 1] governing how N splits across layers), this defines a deterministic, O(1) method for representing any amount as a structured combination of denominations.

This demo validates the pattern on the Euro currency system.

---

## How it works

The system splits any amount N into five structural layers, each governed by its own coefficient:

![Layer structure](./assets/layer-structure.svg)

For any N, repeatedly summing digits reduces it to a single anchor value, computable directly in O(1) as A₀ = N mod 9:

![Reduction chain](./assets/reduction-chain.svg)

## What the demo computes

For any amount N, the demo calculates:

- Control value A₀ = N mod 9 = dr(N)
- Optimal greedy decomposition across the 5 structural layers, C = [19, 9, 3, 3, 1]
- Total number of payment ways
- Full reduction chain from N to dr(N)

## Examples

**€18,00** (1800 cents)

| Layer | Coefficient | Result |
|---|---|---|
| A | 19 | none |
| B | 9 | 1 × €10 |
| C | 3 | 1 × €5, 1 × €2, 1 × €1 |
| D | 3 | none |
| E | 1 | none |

A₀ = N mod 9, computed directly without iterating the greedy breakdown.

**€0,07** (7 cents)

| Layer | Coefficient | Result |
|---|---|---|
| A | 19 | none |
| B | 9 | none |
| C | 3 | none |
| D | 3 | none |
| E | 1 | 1 × €0,05, 1 × €0,02 |

A small amount still resolves through the same five layers. Most stay empty; only the innermost layer is used.

**€271,34** (27134 cents)

| Layer | Coefficient | Result |
|---|---|---|
| A | 19 | 1 × €200 |
| B | 9 | 1 × €50, 1 × €20 |
| C | 3 | 1 × €1 |
| D | 3 | 1 × €0,20, 1 × €0,10 |
| E | 1 | 2 × €0,02 |

A larger, uneven amount uses all five layers at once, each resolved independently.

**€1.000.000,00** (100 000 000 cents)

| Layer | Coefficient | Result |
|---|---|---|
| A | 19 | 2 000 × €500 |
| B | 9 | none |
| C | 3 | none |
| D | 3 | none |
| E | 1 | none |

Even at large scale, the decomposition stays deterministic and resolves in constant time. Above €100.000 the total payment ways figure switches from an exact count to an asymptotic estimate. The decomposition itself stays exact regardless of size.

## How to use

Open [the live demo](https://a19dammer91.github.io/D3-by-A-C-Coupling-Demo/), or run it locally:

```bash
git clone https://github.com/A19dammer91/D3-by-A-C-Coupling-Demo.git
cd D3-by-A-C-Coupling-Demo
open index.html   # or just double-click it
```

No server, no dependencies, no installation.

## Reference

The D³ Pattern: Deterministic Data Decomposition by A-C Coupling (2026)
Zenodo: https://doi.org/10.5281/zenodo.20819940
Academia: https://www.academia.edu/resource/work/169064537

### Cite this work

```bibtex
@misc{d3pattern2026,
  title  = {The D3 Pattern: Deterministic Data Decomposition by A-C Coupling},
  author = {El Issaoui, Bilal},
  year   = {2026},
  doi    = {10.5281/zenodo.20819940},
  url    = {https://doi.org/10.5281/zenodo.20819940}
}
```

## License

Apache License 2.0 · © 2026 Bilal el Issaoui
