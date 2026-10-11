# Project status

Last updated 2026-10-11 (session wrap-up). Live at https://games.shauna.digital/homebeforedark/ (deploys from `main`).

## Current state

- **Deploy state, read first:** the live site runs the first round of 2026-10-10 changes (commit `2e1624c`). The second round (harder tuning and the score) is in `index.html` in the working copy, staged but not committed or pushed. Commit `94c1e64` on `main` only carried its docs, because the game file never reached the computer during that session (see `_docs/findings/2026-10-11-copy-back-and-push.md`). Until the staged change is pushed, the live docs describe a score the live game does not have.
- One road home, half a mile (`HOME_FT=2640`), about 50 seconds without pedaling harder (40 if you pedal harder the whole way). Distance countdown and score in the top left.
- Harder from the first second: speed 4.8 rising to 8.0, first creature about a second in, tight spacing, pairs from 5% of the ride, triples from halfway, feints that switch sides, roots from 12%.
- Set pieces in order: breather, farmhouse lights spelling R U N, scripted left/right/left, the flip side (52% to 65%), breather, three chimes and late leaps (70%), chaser from 72% to the house.
- Mechanics: two lanes; pedal harder (Up / W / swipe up); something behind you that dims the headlight while you coast (it cannot catch you); close-call slow motion; roots in one lane (cracks first).
- Score: 10 per dodge, 50 per close call, both doubled while pedaling harder, 500 for making it home. Best score is saved per browser and shown on the title, crash and ending screens. It replaced the best time.
- Dusk to dark over the ride; streetlights die more often near home; dead lights sputter only when something is coming.
- Landing shadow, treeline and roadside trunks, porch light that grows, backpack marker at your closest finish (hidden once you have made it home).
- Crash: headline "N FT FROM HOME", score and closest finish, restart from the beginning; quick retry after the first crash of a visit.
- Ending: dismount, bike tips over, he walks in, door shuts, eyes in the trees, lights go out, "THE END", score.
- Music only (built-in synth); it muffles during a flicker and drops on the flip side. Clock chime on its own quiet channel. Other sound effects off (`SFX_VOLUME=0`).
- Verified 2026-10-11: bots on the exact staged file (fast lights bot 4 of 4 home, react bot at 0.4 s 0 of 4), and on 2026-10-10 screenshots at desktop and 390x844, a root crash and a full ending with no page errors. See `_docs/findings/2026-10-10-harder-ride-bot-check.md`. Shauna playtested round one and approved it.

## Decisions

| Decision | Resolution | Why | Date |
|---|---|---|---|
| Where the game lives | Own repo and Vercel project, mounted into games.shauna.digital by rewrite | Shauna wanted it separate, matching how 13 Beads is set up | 2026-10-08 |
| Address | `/homebeforedark` (not `/home-before-dark`) | Shauna's requested URL | 2026-10-08 |
| Progression model | One night, one road, fixed distance home | Shauna chose it over a 7-night week or endless nights; the long road through the woods is the point | 2026-10-08 |
| On crash | Back to the start of the road | Shauna chose arcade tension over checkpoints | 2026-10-08 |
| After reaching home | Simple ending, then ride again for a better time | Shauna chose it over an endless mode | 2026-10-08 |
| Scenery | No changing scenery; trees only make the existing woods visible | Shauna: the long road through the woods is the whole point | 2026-10-08 |
| Sound | Music only for now; effects to return one layer at a time, light against the music | Shauna found the background noise distracting | 2026-10-08 |
| Music | Built-in synth loop, no audio file | Shauna likes it; her original track is not in the repo | 2026-10-08 |
| Flicker meaning | Flicker side limits the landing lane to that side or the middle | A design review with bots showed the lights did not matter: bots ignoring them won 8 of 8 | 2026-10-08 |
| Creature design | Keep the existing petal-headed creature | Shauna's choice. Flagged: it closely resembles a well-known TV monster, which conflicts with the original-artwork rule. An original antlered design with cold white eyes was mocked up and is available | 2026-10-08 |
| Creature eye color | Keep cream, not red | Red is the boy's vest and the UI color; dark red vanishes at night (design review) | 2026-10-08 |
| Ending monsters | Shown only as pairs of eyes in the trees | Avoids drawing more of the creature; reads well in the dark | 2026-10-08 |
| Number of lanes | Two lanes instead of three; landing lane always matches the flicker side; staggered pairs from both sides add the challenge | Shauna found three lanes too easy. Bot check: react-only bots at 0.4 s now get caught near the end (they made it home with three lanes); bots that read the lights mostly make it. Supersedes the "its side lane or the middle" rule above | 2026-10-08 |
| Difficulty and pace | Faster start, steady ramp, pairs from 5%, triples late, feints; ride stays half a mile | Shauna found it too easy and slow at the start. Length kept because the faster pace already cuts the ride to about 55 seconds and the new set pieces need the room | 2026-10-10 |
| New mechanics | Pedal harder (Up / swipe up), close-call slow motion, something behind you, roots on the road | Shauna picked these from the ideas list. The chaser dims the headlight but cannot crash you | 2026-10-10 |
| Show-inspired nods | Farmhouse lights spelling R U N, the flip side, a clock that chimes at the flip side and when late leaps start | Shauna's picks. Kept generic: no show, town or character names, no brands, no quotes, no theme music | 2026-10-10 |
| Creature resemblance | Not an issue at this resolution | Shauna: barely visible, and all monsters look the same at this size. Supersedes the flag in the creature design row | 2026-10-10 |
| Difficulty, second pass | Faster (4.8 to 8.0), tighter spacing, more pairs, triples from halfway, more roots and feints earlier, later late leaps, shorter breathers | Shauna: still needs to be harder after playing the first round | 2026-10-10 |
| Best time | Replaced by a score | Shauna: the ride takes the same time for every player, so time did not show skill. Supersedes "ride again for a better time" in the ending row | 2026-10-10 |
| Lanes | Stay at two | Three lanes made the middle a near-safe spot (the reason two was chosen), and two lanes keep tap-a-side touch controls simple. Ideas if variety is wanted later: a temporary wide road on the flip side, or a threat that straddles the center line | 2026-10-10 |
| Farmhouse triple and flip side flash | Keep as built | Shauna playtested and approved ("it all looks great") | 2026-10-10 |
| Score balance | Keep favoring risk (close calls and pedaling harder can outscore a clean ride) | Shauna: yes for now | 2026-10-10 |
| Chaser can catch you | Not yet | Shauna: maybe later. It is the biggest difficulty lever left and changes how the ending plays | 2026-10-10 |
| Arcade-style scoring | Ideas proposed, nothing built | Shauna asked for ideas only; see `_docs/findings/2026-10-11-arcade-scoring-ideas.md` and TODO | 2026-10-11 |

