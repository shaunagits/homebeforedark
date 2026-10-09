# Playtesting with bots

**Question:** does reading the streetlights actually matter, and where does the difficulty peak?

**How it was measured:** Playwright drives the game through `window.__nr` (state, lane, creatures with `si`, `z`, `leap`, `tl`, `fake`, `lz`, `ldz`). A "react" bot ignores the lights and only moves after a creature leaps, after a fixed delay. A "lights" bot moves away from the flickering side before the leap.

**Results:**
- Before the change (lane picked at the leap, 90% your current lane): react bots with a 250 to 400 ms delay won 8 of 8, so the lights did not matter.
- After tying the landing lane to the flicker side and adding `LATE_LEAP`: react bots at 300 to 400 ms still win, at 550 ms they get caught at 54 to 58 s (the peak near the end) instead of at 30 s.
- Lights-bot results were unreliable: the bot's two rules (avoid the flicker side, dodge a landed creature) fought each other and caused crashes a human would not. The game logic was confirmed from logs instead: right-side creatures only land right or middle, left-side only left or middle.

**Hooks:** `__nr.warp(ft)` skips ahead, `__nr.clear()` removes creatures, `__nr.remain(ft)` puts the rider that far from home (use 200 to watch the ending).

**Running it:** start a local server with `cd /path/to/homebeforedark && python3 -m http.server 8791`, then in a Node project with `playwright` installed, launch Chromium, press Space to start, and poll `window.__nr` every 25 ms. On the cloud container the headless browser is under `/opt/pw-browsers/chromium_headless_shell-*/`.

**Before redoing this:** fix the lights bot so it only avoids the flicker side when that lane is not already occupied and does not override the dodge rule mid-dodge.
