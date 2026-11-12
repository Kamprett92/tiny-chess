# Tiny Chess Engine

A compact chess engine in 4 KB of Python for make.fun tiny-chess-01.

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
- `engine.py` - Uncompressed source (for reference)
- `README.md` - This file
- `LICENSE` - MIT license
