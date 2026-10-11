# Arcade-style scoring: ideas

**Question:** how could the score feel like an 80s arcade game? Shauna asked for ideas only; nothing is built.

**Recommended first round:**
- Cabinet look: zero-padded score at top center (`000000`) with `HI 024500` beside it; multiply all points by 10 (100 per dodge, 500 per close call). The HI number flashes gold when you pass it mid-ride.
- Points pop up where they happen: a small number floats up from the dodged creature, gold for close calls. Replaces the "+10" under the distance.
- Chains: dodges close together build a multiplier (x2 up to x5, "CHAIN x3" by the score). A breather or long gap resets it. Pedal harder x2 stacks on top.
- Named bonuses: "RUN BONUS 5000" for clearing the farmhouse left/right/left; "FLIP SIDE CLEAR 3000"; a "SLIPPED AWAY" bonus for keeping the chaser back to the porch.
- End-of-ride tally that counts up line by line after "THE END": dodges x 100, close calls x 500, best chain x 1000, home 10000, total.
- Initials: 3 letters (left, right, up) for a top 5 table on the title, which can cycle with "PRESS START" like an attract screen.

**Open decisions (Shauna):**
1. Table per browser (simple, you only see your own) or shared online (needs a small database; Supabase is connected; raises moderation of initials).
2. Spare bike at a score threshold (classic extra life). Leaning no: it breaks restart-on-crash, which was chosen for tension.
3. Tally sound: quiet counting blips and a jingle on the end screen only would be the first sound effect back; or keep it silent.

**Where it touches the code:** `addPts()`, `saveScore()`, the HUD block in `render()`, the crash and ending text, and the `homebeforedark-score` key. A top 5 would replace that key with a list.
