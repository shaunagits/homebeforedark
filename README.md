# Home Before Dark

A small browser game. Ride home at night. When the streetlights flicker, something is coming. Swerve.

Play it at https://games.shauna.digital/homebeforedark/

## How it is set up

- Plain static files: `index.html`, `icon.png` (home screen icon) and `preview.png` (share image). No build step.
- Hosting: Vercel project `homebeforedark` (team `shaunagits-projects`), deployed automatically from the `main` branch.
- The games site (`shaunagits/games`) forwards `games.shauna.digital/homebeforedark/` to this project, so all paths inside the game must stay relative.

## How a ride works

- One road home: half a mile (`HOME_FT`). The corner shows how far is left.
- Mom's porch light glows at the end of the road from the start; the house comes into view near the end.
- The ride starts at dusk and gets darker the closer you get. Streetlights die more often near home (`DEAD_MIN`, `DEAD_MAX`); a dead light only sputters when something is coming.
- Some flickers are false alarms (`FAKE_CHANCE`). The last stretch to the house is quiet.
- Crash and you start over from the beginning. The game remembers your closest finish and, once you make it home, your best time.

## Things to know

- Music is a loop built into the code. To use an audio track instead, add a file named `music.mp3` next to `index.html`.
- Sound effects (bike wheel whir, streetlight hum, flicker crackle, lane swish, monster leap, crash) are currently switched off so only the music plays. `SFX_VOLUME` at the top of the sound section turns them back on.
- Best score and mute setting are saved in the browser per web address, so scores saved at the `vercel.app` address do not appear on games.shauna.digital.
- Tuning knobs (speed, spacing, spawn distances) are at the top of the script in `index.html`.
