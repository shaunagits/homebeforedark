# Project status

Last updated 2026-10-10 (harder start, set pieces, pedal harder). Live at https://games.shauna.digital/homebefored## Current state

- One road home, half a mile (`HOME_FT=2640`), about 55 seconds without pedaling harder (43 if you pedal harder the whole way). Countdown in the corner.
- Harder from the first second: faster start, steady ramp, first creature about a second in, tighter spacing, pairs from 5% of the ride, triples in the last third, feints that switch sides.
- Set pieces in order: breather, farmhouse lights spelling R U N, scripted left/right/left, the flip side (52% to 65%), breather, three chimes and late leaps (70%), chaser from 72% to the house.
- New hazards and mechanics: roots in one lane (cracks first), pedal harder (Up / W / swipe up), something behind you that dims the headlight while you coast, close-call slow motion.
- Dusk to dark over the ride; streetlights die more often near home; dead lights sputter only when something is coming.
- Landing shadow, treeline and roadside trunks, porch light that grows, backpack marker at your closest finish.
- Crash: headline "N FT FROM HOME", restart from the beginning; quick retry after the first crash of a visit.
- Ending: dismount, bike tips over, he walks in, door shuts, eyes in the trees, streetlights, porch light and windows go out, screen goes dark, "THE END".
- Music only (built-in synth); it muffles slightly during a flicker and drops on the flip side. Clock chime on its own quiet channel. Other sound effects off (`SFX_VOLUME=0`).
- Verified 2026-10-10 locally with bots (see `_docs/findings/2026-10-10-harder-ride-bot-check.md`), screenshots at desktop and 390x844, a root crash and a full ending with no page errors. Not yet pushed or checked on the live site.

 layout checked at 390x844.

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

