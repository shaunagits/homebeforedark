# TODO

In priority order. Build only what Shauna asks for or approves.

1. **Shauna to play the shorter warnings** (live since `bc4853e`) and say if the timing feels right. Knobs: `WARN_START`, `WARN_END` near the top of `index.html`.
2. **Arcade-style scoring: Shauna to decide, then build.** Ideas and the recommended first round are in `_docs/findings/2026-10-11-arcade-scoring-ideas.md`. Open questions: which ideas; high score table per browser or shared online (needs a small database, Supabase is connected); a spare bike at a score threshold (leaning no, it breaks restart-on-crash); quiet tally blips on the end screen only, or silent.
3. **More difficulty ideas, proposed 2026-10-15, none approved.** Shauna to pick, or drop:
   - The chaser can catch you (parked since 10/10, the biggest lever left).
   - The flip side reverses the lights: a left flicker lands on the right while the world is inverted.
   - A threat across the center line that only pedaling harder gets you past (already listed as a lane idea on 10/10).
   - Creatures that land, then scuttle into the other lane.
   - Roots in one lane timed with a creature flickering into the other.
   - No landing shadow in the last stretch.
   - A pitch-black stretch where the only tell is eyes glinting on one side.
   - A harder mode unlocked after the first finish (faster tuning, no shadow, a chaser that catches).
4. **Add sound effects back, one layer at a time, light against the music.** Suggested order: tyre hum, a streetlight buzz only during a warning, then a heartbeat when something is close. The old effects are still in the code behind `SFX_VOLUME`.
5. Refresh `preview.png` (the share image); the flip side or the farmhouse would make a stronger image than the plain road.
6. Optional, not yet built: thin the music out in the last stretch; pause on tab switch during the crash sequence.
