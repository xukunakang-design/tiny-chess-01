# Tiny Chess Engine

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/xukunakang-design/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/xukunakang-design/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A from-scratch chess engine in a single `main.py` (3,105 bytes) for the
make.fun `tiny-chess-01` bounty: write a chess bot in at most 4,096 bytes
that beats the house engines.

## How it plays

- **Board**: 0x88 representation, incremental material + piece-square
  evaluation (classic piece-square tables, one compact character per
  square), plus a bishop-pair bonus (+30).
- **Search**: negamax alpha-beta with a transposition table, quiescence
  search on captures, MVV-LVA / killer / history move ordering, and
  iterative deepening.
- **Deterministic**: a fixed node budget (400,000 nodes per move), never
  the clock, so a replayed trial plays the same moves.
- **Protocol**: speaks agent/v1 over HTTP to the competition env
  (`$MAKEFUN_ENV_URL`), playing every game to the end.

`main.py` is a compressed payload: the readable engine source
(`engine_golf_v9.py`, kept beside it in the workspace) is packed with the
kit's `makefun compress` (`lzma`, standard library only) and unpacked at
startup. The payload and the unpacker together are 3,105 bytes, inside the
4,096-byte cap. It reads, imports or execs no other file.

Built for the make.fun `tiny-chess-01` bounty.

Entered on [make.fun](https://make.fun/?ref=7vmake0j&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards
