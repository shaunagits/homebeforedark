# Project status

Last updated 2026-10-08 (two lanes). Live at https://games.shauna.digital/homebeforedark/ (deploys from `main`).

## Current state

- One road home, half a mile (`HOME_FT=2640`), about 68 seconds at speed. Countdown in the corner.
- Dusk to dark over the ride; streetlights die more often near home; dead lights sputter only when something is coming.
- Two lanes. The flicker side is the lane a creature lands in. Back-to-back pairs from both sides from about 15% of the ride. Late in the ride creatures jump later (`LATE_LEAP`).
- Difficulty is driven by distance, with two breathers (`BREATHERS`) and a quiet last 260 ft. First two creatures of each ride are scripted (one per side, no false alarms yet).
- Landing shadow, treeline and roadside trunks, porch light that grows, backpack marker at your closest finish.
- Crash: headline "N FT FROM HOME", restart from the beginning; quick retry after the first crash of a visit.
- Ending: dismount, bike tips over, he walks in, door shuts, eyes in the trees, streetlights, porch light and windows go out, screen goes dark, "THE END".
- Music only (built-in synth); it muffles slightly during a flicker. Sound effects off (`SFX_VOLUME=0`).
- Verified 2026-10-08 on the live site: full crash and full ending playthroughs with no page errors; phone layout checked at 390x844.

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
