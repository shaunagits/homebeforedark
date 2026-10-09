# Home Before Dark

A pixel-art browser game: a boy rides his bike home at night down one road through the woods and dodges creatures that leap from the side when streetlights flicker. Read `README.md` for how a ride works and where the tuning knobs are, and `_docs/PROJECT_STATUS.md` for decisions and their reasons.

- Everything is in `index.html` (canvas + plain JavaScript, no build step), plus `icon.png` and `preview.png`.
- Repository `shaunagits/homebeforedark` (private), Vercel project `homebeforedark`, team `shaunagits-projects`. Every push to `main` deploys to production.
- Players reach it at https://games.shauna.digital/homebeforedark/ through a rewrite in the `shaunagits/games` repo. Keep every asset path relative.
- No test suite. Verify changes with an automated playtest (Playwright plus the `window.__nr` hooks); see `_docs/findings/2026-10-08-playtesting-with-bots.md`.
- Sound effects are off on purpose (music only). Shauna wants them added back one layer at a time and kept light against the music.
- The creature design is Shauna's call; do not redraw it without asking (see the decisions table).
- No em dashes in any text. No AI or assistant credit in code, commits, or docs.
- Shauna creates new GitHub repositories herself. A session cannot.
