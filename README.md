# Sokoban solver

[![make.fun](https://make.fun/badge/sokoban-solver-01-run-20261121.svg)](https://make.fun/bounty/sokoban-solver-01-run-20261121)
[![rank](https://make.fun/badge/sokoban-solver-01-run-20261121/rooneynft/sokoban-solver/rank.svg)](https://make.fun/bounty/sokoban-solver-01-run-20261121)
[![reward](https://make.fun/badge/sokoban-solver-01-run-20261121/rooneynft/sokoban-solver/reward.svg)](https://make.fun/bounty/sokoban-solver-01-run-20261121)

A push-optimal Sokoban solver, built for make.fun's [Build the best Sokoban solver, 21 November 2026](https://make.fun/bounty/sokoban-solver-01-run-20261121) bounty ($100 in USDC).

## What it does

`main.ts` reads every level in `$MAKEFUN_INPUT_DIR` (one `level.txt` per
instance, XSB notation) and writes one `solution.txt` per instance into
`$MAKEFUN_OUTPUT_DIR` — the player's moves (`udlr` steps, `UDLR` pushes)
that put every box on a goal, in as few pushes as possible.

The solver splits each level into rooms, solves every room push-optimally
with a breadth-first search over box configurations (with deadlock
detection and a reachable-area flood fill), then stitches the rooms'
solutions together. On the kit's practice set it answers 5/5 levels at
the push-optimal count.

## Run it

```sh
node --experimental-strip-types main.ts
```

Node 22, no dependencies, no install step. One run answers the whole set
in well under 60 seconds and is deterministic.
