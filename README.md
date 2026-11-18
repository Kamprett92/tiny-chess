# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Kamprett92/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Kamprett92/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A compact chess engine in 4 KB of Python for make.fun tiny-chess-01.

## Run it

```sh
python3 main.py
```

## Design

- **Board**: 0x88 representation (128 squares, off-board detection via `sq & 0x88`)
- **Search**: Alpha-beta with iterative deepening to 50,000 nodes
  - Transposition table (100k entries)
  - Move ordering: MVV-LVA captures first, promotions
  - Quiescence search (captures only)
  - Null move pruning (depth >= 3)
- **Evaluation**: Material + piece-square tables
  - Pawn 100, Knight 320, Bishop 330, Rook 500, Queen 900, King 20000
  - PSTs encoded as compact strings (value+50 per square)
- **Deterministic**: Fixed node budget, no clock, no randomness

## Size

- `main.py`: 3,307 bytes (lzma-compressed payload + unpacker)
- Total repo: under 8,192 bytes

## Files

- `main.py` - The engine (compressed)
- `README.md` - This file
- `LICENSE` - MIT license

---

<sub>Entered on [make.fun](https://make.fun/?ref=t1yg6scf&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
