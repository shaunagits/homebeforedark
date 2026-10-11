# Copying files back and pushing

**Question:** why did commit `94c1e64` ("Harder again and a score") deploy without the game changes?

**What happened:** the session edits `index.html` in its cloud workspace and copies it back to the project folder on Shauna's computer. In the second round the copy-back reported success but the computer kept the first-round file (57,336 bytes instead of 58,266). The working tree looked clean, so the commit took only the docs. Vercel deployed it and reported READY, which looked like success. It was caught the next day when a status check grepped the computer's file for `START_SPEED` and found the old value.

**Likely cause:** both rounds copied back from the same staged file name (`outputs/index.html`), and the second copy appears to have been served from the first. Copying from a new file name (`outputs/index-round2.html`) worked.

**Before trusting a copy-back:** compare checksums on both sides (`shasum -a 256 index.html` on the computer, `sha256sum` in the workspace), or grep a value that changed. Check `git diff --stat` shows `index.html` before committing.

**Pushing:** the shell on Shauna's computer has no GitHub login, so `git push` there fails ("could not read Username"). Either Shauna runs `cd ~/Desktop/claudecode/homebeforedark && git push origin main` in Terminal, or the session attaches `shaunagits/homebeforedark` with push access and pushes from a clone. To keep the same commit on both sides, make a bundle on the computer (`git bundle create hbd.bundle origin/main..main`), fetch it into the clone and push, then delete the bundle. Git commits from the session also need delete permission on the folder, or git leaves lock files behind.
