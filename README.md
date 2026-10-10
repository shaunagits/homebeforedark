# Home Before Dark

A small browser game. Ride home at night. When the streetlights flicker, something is coming. Swerve.

Play it at https://games.shauna.digital/homebeforedark/

## How it is set up

- Plain static files: `index.html`, `icon.png` (home screen icon) and `preview.png` (share image). No build step.
- Hosting: Vercel project `homebeforedark` (team `shaunagits-projects`), deployed automatically from the `main` branch.
- The games site (`shaunagits/games`) forwards `games.shauna.digital/homebeforedark/` to this project, so all paths inside the game must stay relative.

## How a ride works

- One road home through the woods: half a mile (`HOME_FT`), about 55 seconds without pedaling harder. The corner shows how far is left.
- Mom's porch light glows at the end of the road from the start and grows as you get closer; the house comes into view near the end.
- The ride starts at dusk and gets darker the closer you get. Streetlights die more often near home (`DEAD_MIN`, `DEAD_MAX`); a dead light only sputters when something is coming.
- Two lanes, one on each side of the center line (`LANE`). The flicker tells you where: a creature from the left lands in the left lane, one from the right in the right lane.
- Difficulty follows distance and starts from the first second: speed ramps steadily (`START_SPEED`, `MAX_SPEED`), the first creature comes about a second in (`FIRST_IN`) and spacing tightens (`GAP_START`, `GAP_END`, `GAP_RAND`). The first two creatures come one from each side.
- Pairs from both sides start almost right away (`PAIR_FROM`, `PAIR_MAX`, `PAIR_GAP`): dodge the first into the second's lane and switch back in time. In the last third a pair can become left, right, left (`TRIPLE_FROM`, `TRIPLE_CHANCE`).
- False alarms (`FAKE_CHANCE`), and feints (`SWITCH_FROM`, `SWITCH_CHANCE`): one side flickers briefly, then the other, and only the second is real.
- Roots (`ROOT_FROM`, `ROOT_CHANCE`): purple-glowing cracks show in one lane, then roots come up through the road. No flicker; you read the road.
- The ride in order: a quiet stretch (`BREATHERS`), then a farmhouse on the left (`FARM_AT`) whose holiday lights go dark and spell R, U, N one bulb at a time (also shown big at the top), then a scripted left, right, left. Then the flip side (`FLIP_FROM`, `FLIP_TO`): the picture inverts for a moment, the road turns cold blue, the sky goes red with lightning, spores drift up, the music drops and creatures come closer together (`FLIP_GAP`). A clock chimes going in and coming out. After another quiet stretch the clock chimes three times and creatures start jumping later (`LATE_FROM`, `LATE_LEAP`). From `CHASE_FROM` something follows behind; then a quiet last stretch to the house (still chased).
- Pedal harder: hold Up (or W), or swipe up and keep the finger down on a phone. You go `SPRINT` times faster: a better time, less time to react.
- Something behind you: eyes low in the dark behind the bike creep closer while you coast and drop back while you pedal harder. The closer it is, the dimmer your headlight. It cannot catch you.
- Close calls: a creature or root passing very close (`NEAR_X`), or one in the lane you left a moment ago (`NEAR_T`), gives a moment of slow motion, a jolt and "CLOSE ONE".
- A shadow on the road shows where a leaping creature will land.
- Crash and you start over from the beginning. After the first crash of a visit, a tap can skip ahead after `T_QUICK` seconds. Your dropped backpack marks your closest finish on later rides.
- Reaching home plays the ending: he hops off, the bike tips over, he goes inside, the streetlights and porch light go out with eyes in the trees, and the screen goes dark (timings `E_OFF` to `E_AGAIN`).
- Controls: left and right arrows or A and D, Up or W to pedal harder; on touch, tap the left or right half to move to that lane (steers on touch down) and swipe up to pedal harder. P or Esc pauses, M mutes. "< GAMES" (top left on the title, crash and ending screens), Esc on those screens, or ALL GAMES in the pause menu goes back to games.shauna.digital. It is hidden while riding so a steering tap cannot leave the game.

## Things to know

- Music is a loop built into the code. To use an audio track instead, add a file named `music.mp3` next to `index.html`.
- The music is muffled a little while a streetlight flickers.
- Sound effects (bike wheel whir, streetlight hum, flicker crackle, lane swish, monster leap, crash) are currently switched off so only the music plays. `SFX_VOLUME` at the top of the sound section turns them back on. The clock chime is the one exception: it plays on its own quiet channel (`chime()`), not through the effects.
- Closest finish (`homebeforedark-closest`), best time (`homebeforedark-time`) and the mute setting (`homebeforedark-muted`) are saved in the browser per web address, so anything saved at the `vercel.app` address does not appear on games.shauna.digital.
- Tuning knobs (distance, speed, spacing, pairs, triples, feints, roots, the farmhouse, the flip side, the chaser, close calls, ending timings) are at the top of the script in `index.html`.
- Project status, decisions and next steps: `_docs/PROJECT_STATUS.md` and `_docs/TODO.md`.
