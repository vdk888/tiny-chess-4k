# tiny-chess-01

A chess engine in under 4 KB of Python 3 (standard library only). It plays over the
makefun HTTP+JSON interface: `MAKEFUN_ENV_URL=... python3 -P -s main.py`.

- 10x12 mailbox board, always seen from the side to move (rotated after each move);
  pseudo-legal moves with king-capture legality; the root only plays moves from `legal_moves`.
- Negamax alpha-beta (PVS) with iterative deepening bounded by a fixed node count
  (deterministic, no clocks), transposition table, null move, late-move reductions,
  killer moves, MVV-LVA-like ordering, quiescence search, repetition detection from history.
- Evaluation: material + piece-square tables (incrementally updated), endgame king/pawn tables.

Credits: the rotating 120-char board and king-capture legality follow ideas from
Sunfish by Thomas Ahle (the code here is written from scratch); piece-square values follow
Tomasz Michniewski's "Simplified Evaluation Function" (Chess Programming Wiki).

MIT licence, see LICENSE.
