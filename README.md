# Home Before Dark

A small browser game. Ride home at night. When the streetlights flicker, something is coming. Swerve.

Play it at https://games.shauna.digital/homebeforedark/

## How it is set up

- Plain static files: `index.html`, `icon.png` (home screen icon) and `preview.png` (share image). No build step.
- Hosting: Vercel project `homebeforedark` (team `shaunagits-projects`), deployed automatically from the `main` branch.
- The games site (`shaunagits/games`) forwards `games.shauna.digital/homebeforedark/` to this project, so all paths inside the game must stay relative.

## How a ride works

- One road home through the woods: half a mile (`HOME_FT`). The corner shows how far is left.
- Mom's porch light glows at the end of the road from the start and grows as you get closer; the house comes into view near the end.
- The ride starts at dusk and gets darker the closer you get. Streetlights die more often near home (`DEAD_MIN`, `DEAD_MAX`); a dead light only sputters when something is coming.
- The flicker tells you where: a creature from the left lands in the left or middle lane, one from the right in the right or middle lane. Near the end creatures jump later (`LATE_LEAP`), so reading the lights matters more than reacting.
- Difficulty follows distance, not dodges: speed (`START_SPEED`, `MAX_SPEED`) and spacing ramp up, with quiet stretches (`BREATHERS`) and a quiet last stretch to the house. The first two creatures of every ride come one from each side, and false alarms (`FAKE_CHANCE`) start after that.
- A shadow on the road shows where a leaping creature will land.
- Crash and you start over from the beginning. After the first crash of a visit, a tap can skip ahead after `T_QUICK` seconds. Your dropped backpack marks your closest finish on later rides.
- Reaching home plays the ending: he hops off, the bike tips over, he goes inside, the streetlights and porch light go out with eyes in the trees, and the screen goes dark (timings `E_OFF` to `E_AGAIN`).
- Controls: left and right arrows or A and D; on touch, tap the left or right half (steers on touch down). P or Esc pauses, M mutes.

## Things to know

- Music is a loop built into the code. To use an audio track instead, add a file named `music.mp3` next to `index.html`.
- The music is muffled a little while a streetlight flickers.
- Sound effects (bike wheel whir, streetlight hum, flicker crackle, lane swish, monster leap, crash) are currently switched off so only the music plays. `SFX_VOLUME` at the top of the sound section turns them back on.
- Best score and mute setting are saved in the browser per web address, so scores saved at the `vercel.app` address do not appear on games.shauna.digital.
- Tuning knobs (speed, spacing, spawn distances) are at the top of the script in `index.html`.
