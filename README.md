# tiny-chess-4k

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/OhhRayy/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/OhhRayy/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A 4 KB chess engine in Python (LZMA-packed, 2,873 bytes): alpha-beta + quiescence search, Zobrist transposition table, 60,000 nodes/move. Practice Elo 1,545 — above the 1,154 final floor and the 1,365 house baseline.

## Design

- 0x88 board, alpha-beta + quiescence (captures, promotions, replies to check), Zobrist transposition table, MVV-LVA + killer move ordering, iterative deepening with a fixed 60,000-node budget per depth (deterministic, no wall clock).
- Evaluation: material + piece-square tables + bishop pair.

## Practice trials (local, kit house engines)

| Trial | Elo | Result |
|---|---|---|
| Dev engine, 60k nodes | 1,451 | 3W 2D 1L |
| Compressed main.py, 60k nodes | 1,545 | 4W 1D 1L |

## Run it

```sh
python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
