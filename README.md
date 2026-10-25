# Ramsey number lower bounds from Quantavane

The Ramsey number R(s,t) is the least n such that every red/blue colouring of the edges of the complete graph K_n
contains a red K_s or a blue K_t. A colouring of K_n with neither shows that R(s,t) > n.

| Bound | Colouring | Previous best |
|---|---|---|
| R(5,15) ≥ 279 | K_278, circulant | 275, from a recursive construction (Radziszowski's survey *Small Ramsey Numbers*, revision 18) |
| R(8,12) ≥ 512 | K_511 | 511, from a 510-vertex colouring in google-research/ramsey_number_bounds (2026) |

**R(5,15) ≥ 279.** Number the vertices 0 to 277 and colour the edge {i, j} red when min(|i−j|, 278−|i−j|) is one
of 1, 6, 8, 9, 10, 13, 41, 42, 43, 44, 45, 46, 48, 51, 54, 57, 60, 63, 66, 67, 68, 69, 70, 71, 94, 95, 96, 97, 98,
99, 104, 107, 110, 113, 116, 118, 119, 122, 125, 126, 128, 129, 130, 131, 133, 135, 137, 139, and blue otherwise.
There is no red K_5 and no blue K_15. It was found by a tabu search over circulant colourings.

**R(8,12) ≥ 512.** This colouring extends the 510-vertex colouring `R(8, 12) >= 511.txt` from
[google-research/ramsey_number_bounds](https://github.com/google-research/google-research/tree/master/ramsey_number_bounds)
by one vertex (number 510) and recolours the edge {131, 356} from red to blue. Every other edge keeps its colour.
There is no red K_8 and no blue K_12. It was found with the add-a-vertex-and-repair local search of Fritz Cremer
(arXiv:2610.12122).

## Check them yourself

```sh
cc -O2 -o check check.c
./check colourings/R5_15_K278.txt    # a few seconds
./check colourings/R8_12_K511.txt    # about two hours on a laptop
```

`check.c` confirms that each matrix is symmetric with a zero diagonal, then finds the largest red clique (1s) and
the largest blue clique (0s) exactly, by branch and bound. For a circulant colouring it searches from vertex 0 only,
since rotations preserve both colours. Expected results: R5_15_K278, red 4 and blue 14; R8_12_K511, red 7 and
blue 11. Each colouring was also checked by at least one other, independently written program before release.

## Files

- `colourings/*.txt`: n lines of n characters; 1 is a red edge, 0 a blue edge.
- `records.json`: the table above in machine-readable form.
- `check.c`: the checker.

## Licence

CC BY 4.0 (see `LICENSE`). `colourings/R8_12_K511.txt` is derived from a colouring released by Google Research
under the Apache License 2.0, which also applies to it. Please credit "Arhan Canli, Quantavane" when you use these
colourings.

Arhan Canli, Quantavane · quantavane.com
