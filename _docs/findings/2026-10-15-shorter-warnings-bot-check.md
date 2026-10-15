# Shorter warnings: bot check

**Question:** after making the flicker start later closer to home, is the ride still possible, and does the warning actually shrink as intended?

**The change:** before, a light flickered from the moment a creature spawned (`SPAWN_Z`) until it landed, about 1.5 s at the start and 1.0 s near home (shorter only because speed rises). Now each creature stores `wz`, the road distance where its flicker starts, from `warnZ(ldz)`: landing point plus `WARN_START` easing to `WARN_END` seconds at base speed (not including pedaling harder, so pedaling harder still cuts it). Capped at `SPAWN_Z`, so the start of the ride is unchanged. Feints: the fake flickers for 2.2 road units from `wz`, then the real one takes over from the same point.

**How it was measured:** same approach as `2026-10-10-harder-ride-bot-check.md`, run in-page (a 16 ms loop dispatching arrow keys), 4 rides per run. A "lights" bot knows a creature once its side flickers; a "react" bot only once it leaps. Both see roots from the start and pedal harder while the chaser is more than halfway close. The bot also logged the warning time for each creature it learned about from the lights.

| Bot | Result |
|---|---|
| lights, 150 ms | 8 of 8 home, about 49 s, score 930 to 1,030 |
| lights, 250 ms | 4 of 4 home |
| react, 300 ms | 4 of 4 home, score 1,140 to 1,390 |

Measured warning: about 1.37 s in the first 20% of the ride, about 0.63 s in the last 15%. No page errors.

**Not measured:** slower lights bots (450 ms and up), where the change should bite hardest. Run those if Shauna wants numbers on how much harder it got.

**Gotchas:**
- Use the headless shell, `/opt/pw-browsers/chromium_headless_shell-1194/chrome-linux/headless_shell`. The full `chromium-1194/chrome-linux/chrome` binary fails to launch in Playwright's default headless mode.
- The bot script lived in the session scratchpad and is gone; rebuild it from this note and the 10/10 one.
