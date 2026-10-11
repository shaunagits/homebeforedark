# TODO

In priority order.

1. **Commit and push the staged second round** (`index.html`: harder tuning and the score). Until then the live game is round one while the docs describe the score. Message: "Harder again and a score: game file". Then check the live site shows SCORE under the distance.
2. **Arcade-style scoring: Shauna to decide, then build.** Ideas and the recommended first round are in `_docs/findings/2026-10-11-arcade-scoring-ideas.md`. Open questions: which ideas; high score table per browser or shared online (needs a small database, Supabase is connected); a spare bike at a score threshold (leaning no, it breaks restart-on-crash); quiet tally blips on the end screen only, or silent.
3. **Shauna to playtest round two** once live and say if it is hard enough. Knobs: `START_SPEED`, `GAP_START`, `PAIR_FROM`, `TRIPLE_CHANCE`, `ROOT_CHANCE`, `SWITCH_CHANCE`, `FLIP_GAP`, `LATE_LEAP`, `SPRINT`. Parked lever: let the chaser catch you.
4. **Add sound effects back, one layer at a time, light against the music.** Suggested order: tyre hum, a streetlight buzz only during a warning, then a heartbeat when something is close. The old effects are still in the code behind `SFX_VOLUME`.
5. Refresh `preview.png` (the share image); the flip side or the farmhouse would make a stronger image than the plain road.
6. Optional, not yet built: thin the music out in the last stretch; pause on tab switch during the crash sequence.
