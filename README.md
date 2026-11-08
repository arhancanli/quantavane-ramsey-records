# Ramsey number lower bounds from Quantavane

The Ramsey number R(s,t) is the least n such that every red/blue colouring of the edges of the complete graph K_n
contains a red K_s or a blue K_t. A colouring of K_n with neither shows that R(s,t) > n.

| Bound | Colouring | Previous best |
|---|---|---|
| R(4,18) ≥ 210 | K_209 | 209, from a 208-vertex colouring in google-research/ramsey_number_bounds (2026); Radziszowski's survey *Small Ramsey Numbers*, revision 18, lists 205 |
| R(5,15) ≥ 283 | K_282, circulant | 279, from our K_278 colouring of 24 Oct 2026 (below); before it 275, from a recursive construction (Radziszowski's survey *Small Ramsey Numbers*, revision 18) |
| R(8,12) ≥ 523 | K_522 | 519, from our K_518 colouring of 3 Nov 2026 (below); before it 512 (our K_511 colouring of 25 Oct 2026) and 511, from a 510-vertex colouring in google-research/ramsey_number_bounds (2026) |

**R(4,18) ≥ 210.** `colourings/R4_18_K209.txt` adds one vertex, number 208, to the 208-vertex colouring
`R(4, 18) >= 209.txt` from
[google-research/ramsey_number_bounds](https://github.com/google-research/google-research/tree/master/ramsey_number_bounds)
(its 1s are the red edges here). An add-a-vertex-and-repair local search in the style of Fritz Cremer's
(arXiv:2610.12122) then recoloured edges until no red K_4 and no blue K_18 was left: among vertices 0 to 207, 152
edges changed from red to blue and 53 from blue to red (all 205 are listed in `records.json`), and every other edge
keeps its colour. There is no red K_4 and no blue K_18. It was found on 8 November 2026 and checked on all 209
vertices by three independently written programs: a search with greedy-colouring bounds, Bron-Kerbosch with Tomita's
pivot, and the branch and bound in `check.c` (largest red clique 3, largest blue clique 17).

**R(5,15) ≥ 283.** Number the vertices 0 to 281 and colour the edge {i, j} red when min(|i−j|, 282−|i−j|) is one
of 2, 6, 8, 9, 10, 13, 14, 21, 29, 30, 32, 33, 36, 39, 44, 45, 47, 52, 55, 61, 67, 69, 71, 72, 77, 83, 86, 89, 92,
95, 97, 99, 108, 112, 114, 115, 117, 118, 120, 121, 124, 128, 130, 131, 132, 135, 136, 139, 141, and blue otherwise
(`colourings/R5_15_K282.txt`). There is no red K_5 and no blue K_15. A second colouring, with distance 109 red as
well, also works (`colourings/R5_15_K282_b.txt`); no multiplier d ↦ kd maps one to the other. Both were found on
5 November 2026 by a tabu search over circulant colourings, started from the K_278 colouring below scaled to 282
vertices (distance d takes the colour of distance round(278d/282)) and perturbed at random, and checked by two
independently written programs (Bron-Kerbosch with Tomita's pivot, and the branch and bound in `check.c`).

**R(5,15) ≥ 279 (24 Oct 2026, now superseded).** Number the vertices 0 to 277 and colour the edge {i, j} red when min(|i−j|, 278−|i−j|) is one
of 1, 6, 8, 9, 10, 13, 41, 42, 43, 44, 45, 46, 48, 51, 54, 57, 60, 63, 66, 67, 68, 69, 70, 71, 94, 95, 96, 97, 98,
99, 104, 107, 110, 113, 116, 118, 119, 122, 125, 126, 128, 129, 130, 131, 133, 135, 137, 139, and blue otherwise.
There is no red K_5 and no blue K_15. It was found by a tabu search over circulant colourings. The line of searches
behind it started from E. Kuznetsov's cyclic (5,14)-colouring on 266 vertices (Table 2 of arXiv:1505.07186), its
distances scaled to 276 vertices; the colourings for 276, 278 and then 282 vertices grew from there.

**R(8,12) ≥ 523.** `colourings/R8_12_K522.txt` adds four vertices, numbers 518 to 521, to the K_518 colouring below,
one at a time. Each new vertex starts as a copy of an existing one (vertex 518 as a copy of vertex 64, joined to it in
red), and Fritz Cremer's local search (arXiv:2610.12122) then recolours edges until no red K_8 and no blue K_12 is
left. Among vertices 0 to 517, 39 edges changed colour: {50, 64}, {64, 512}, {64, 514} and {64, 517} from red to
blue, and 35 edges at vertex 356 and its copies 512 to 514 from blue to red (all 39 are listed in `records.json`).
Every other edge among them keeps its colour. There is no red K_8 and no blue K_12. It was found on 6 November 2026
and checked on all 522 vertices by two independently written programs: Bron-Kerbosch with Tomita's pivot, and the
branch and bound in `check.c` (largest red clique 7, largest blue clique 11).

**R(8,12) ≥ 519 (3 Nov 2026, now superseded).** `colourings/R8_12_K518.txt` enlarges the K_511 colouring below by copying three of its vertices.
Vertex 102 becomes the pair 102, 511, joined in red. Vertices 356 and 458 each become four vertices (356 and 512 to
514; 458 and 515 to 517), joined all in blue. Every other edge takes the colour of the edge between the original
vertices, so vertices 0 to 510 keep their colours. There is no red K_8 and no blue K_12. Vertex 511 came from the same
add-a-vertex local search as the K_511 colouring; the six blue copies came from a search for vertices whose copies
create neither.

**R(8,12) ≥ 512 (25 Oct 2026, now superseded).** `colourings/R8_12_K511.txt` extends the 510-vertex colouring
`R(8, 12) >= 511.txt` from
[google-research/ramsey_number_bounds](https://github.com/google-research/google-research/tree/master/ramsey_number_bounds)
by one vertex (number 510) and recolours the edge {131, 356} from red to blue. Every other edge keeps its colour.
There is no red K_8 and no blue K_12. It was found with the add-a-vertex-and-repair local search of Fritz Cremer
(arXiv:2610.12122).

## Paper

Arhan Canli, *New lower bounds for the Ramsey numbers R(5,15) and R(8,12)*, version 2 (3 November 2026),
[doi:10.5281/zenodo.23920916](https://doi.org/10.5281/zenodo.23920916). It gives both colourings and the proof of
R(8,12) ≥ 519 from the K_511 colouring.

## Check them yourself

```sh
cc -O2 -o check check.c
./check colourings/R4_18_K209.txt    # a few seconds
./check colourings/R5_15_K282.txt    # a few seconds
./check colourings/R5_15_K282_b.txt  # a few seconds
./check colourings/R5_15_K278.txt    # a few seconds
./check colourings/R8_12_K511.txt    # about two hours on a laptop
./check colourings/R8_12_K518.txt    # a few hours on a laptop
./check colourings/R8_12_K522.txt    # an hour or two on a laptop
```

`check.c` confirms that each matrix is symmetric with a zero diagonal, then finds the largest red clique (1s) and
the largest blue clique (0s) exactly, by branch and bound. For a circulant colouring it searches from vertex 0 only,
since rotations preserve both colours. Expected results: R4_18_K209, red 3 and blue 17; R5_15_K282, R5_15_K282_b and R5_15_K278, red 4 and blue 14; R8_12_K511, R8_12_K518 and
R8_12_K522, red 7 and blue 11. Each colouring was also checked by at least one other, independently written program before release.

## Files

- `colourings/*.txt`: n lines of n characters; 1 is a red edge, 0 a blue edge.
- `records.json`: the table above in machine-readable form.
- `check.c`: the checker.

## Licence

CC BY 4.0 (see `LICENSE`). `colourings/R4_18_K209.txt` is derived from a colouring released by Google Research under
the Apache License 2.0, as are `colourings/R8_12_K511.txt`, `colourings/R8_12_K518.txt` and
`colourings/R8_12_K522.txt` (from another of its colourings); that licence also applies to them. Please credit
"Arhan Canli, Quantavane" when you use these colourings.

Arhan Canli, Quantavane · quantavane.com
