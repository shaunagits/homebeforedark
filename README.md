# Home Before Dark

A small browser game. Ride home at night. When the streetlights flicker, something is coming. Swerve.

Play it at https://games.shauna.digital/homebeforedark/

## How it is set up

- Plain static files: `index.html`, `icon.png` (home screen icon) and `preview.png` (share image). No build step.
- Hosting: Vercel project `homebeforedark` (team `shaunagits-projects`), deployed automatically from the `main` branch.
- The games site (`shaunagits/games`) forwards `games.shauna.digital/homebeforedark/` to this project, so all paths inside the game must stay relative.

## Things to know

- Music is a loop built into the code. To use an audio track instead, add a file named `music.mp3` next to `index.html`.
- Best score and mute setting are saved in the browser per web address, so scores saved at the `vercel.app` address do not appear on games.shauna.digital.
- Tuning knobs (speed, spacing, spawn distances) are at the top of the script in `index.html`.
