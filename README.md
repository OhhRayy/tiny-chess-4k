# tiny-chess-4k

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/OhhRayy/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/OhhRayy/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A 4 KB chess engine in Python (LZMA-packed): PeSTO tapered evaluation, alpha-beta + quiescence + null-move pruning, Zobrist transposition table, per-opponent node budgets (60k–90k/move). Practice Elo 1,618 (3-trial mean) — above the 1,154 final floor and the 1,365 house baseline.

## Design

- 0x88 board, iterative deepening with fixed per-opponent node budgets (deterministic, no wall clock): 60k vs depth-2/3, 80k vs depth-4/nodes-100k, 90k vs nodes-250k and stronger.
- Evaluation: authentic PeSTO tapered middlegame/endgame piece-square tables, maintained incrementally (O(1) eval), plus bishop pair.
- Search: alpha-beta + quiescence (captures, promotions, replies to check), null-move pruning (R=2, only when eval ≥ beta and not in an endgame), LMR + PVS + history/killer ordering, check extension, mate-distance-adjusted transposition table (cleared each move), pseudo-legal move loop.

## Practice trials (local, kit house engines)

| Trial | Elo | Result |
|---|---|---|
| v10 trial-0 | 1,654 | 4W 2D 0L |
| v10 trial-1 | 1,545 | 4W 1D 1L |
| v10 trial-2 | 1,654 | 4W 2D 0L |
| **v10 mean** | **1,618** | **12W 5D 1L** |
| Baseline entry (mean) | 1,396 | 9W 4D 5L |

## Run it

```sh
python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
