# Harder ride: bot check

**Question:** after the harder start and the new set pieces, is the ride harder from the beginning, and is everything still possible to dodge?

**How it was measured:** the same Playwright approach as `2026-10-08-playtesting-with-bots.md`. The bot looks at the nearest threat it can know about and moves to the other lane after a fixed delay. A "lights" bot knows a creature once its side flickers (so it also dodges false alarms and feints); a "react" bot ignores the lights and only knows a creature once it leaps. Both see roots from the start. The bot pedals harder while the chaser is more than halfway close, unless noted. 4 to 10 rides per row.

| Bot | Before (two-lane version) | Now |
|---|---|---|
| lights, 150 ms | | 10 of 10 home, about 55 s; pedaling harder the whole way 8 of 8, about 43 s |
| lights, 250 ms | 4 of 4 | 4 of 4 |
| lights, 450 ms | | 0 of 6, caught at 46 to 50 s |
| lights, 550 ms | | 0 of 6, caught at 16 to 33 s |
| react, 300 ms | 4 of 4 | 4 of 4 |
| react, 400 ms | | 4 of 6, caught at 50 to 52 s |
| react, 450 ms | 1 of 4, caught at 38 to 58 s | 0 of 6, caught at 36 to 50 s |

**Results:**
- Nothing is impossible: fast bots always make it home, including while pedaling harder the whole way.
- Slow bots are now caught as early as 16 seconds in, where before the first half was safe.
- The farmhouse left, right, left was a wall at first (every slow bot caught at the same spot). It now uses pairs spaced 20% wider (`triple(0,1.2)`), and deaths spread out.
- New hooks: `__nr.riderX`, `v`, `boost`, `chase`, `flip`, `prog`, `warn`, `nearCount`, `farmT`, `playT`, and `sprint(on)`. Roots appear in `__nr.mons` with `root: true` and their lane in `tl`.
