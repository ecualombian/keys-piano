# Keys — a piano practice room

A free, no-signup web app for getting back into piano. Falling-notes lessons that
wait for you to play the right note before moving on, an on-screen keyboard, and
(coming soon) live radio + play-along with your own music.

Runs in any browser, including Safari on an iPad. Add it to your Home Screen to
launch it full-screen like a real app.

## Run it locally
Open `index.html` in a browser. (Some features that talk to the internet — KEXP,
Spotify — only work once it's hosted online, not from a local file.)

## Roadmap
- [x] Falling-notes lessons + on-screen keyboard + mic listening
- [ ] **Stage 1 — put it online (GitHub Pages)** ← you are here
- [ ] Stage 2 — KEXP live radio button with now-playing
- [ ] Stage 3 — Spotify login: browse your playlists + embedded play-along
- [ ] Stage 4 — grow the song library from sheet-music photos & requests

## Adding songs
There's no magic auto-import — accurate note data for arbitrary songs doesn't
exist to grab. Instead: send Claude a song name, or a **photo of your sheet
music**, and it transcribes a simplified melody into the library format below.
Your own practice sheets are the best source.

Song format (right-hand melody), `[MIDI note, beats]`:
```js
ode: { name:"Ode to Joy", tempo:112, notes:[ [64,1],[64,1],[65,1],[67,1], ... ] }
```

---

## Git cheat-sheet (the mental model)

A **repo** is just this folder plus a hidden `.git/` that remembers every saved
version. Your work moves through three zones:

    working folder  --git add-->  staging area  --git commit-->  history (saved snapshots)
       (your edits)                (what's next)                  (permanent, with a message)

**GitHub** is a copy of the repo in the cloud. `push` sends your commits up;
`pull` brings new ones down; `clone` downloads a repo the first time.

### Everyday commands
```bash
git status                 # what's changed / what's staged — run this constantly
git add .                  # stage everything you changed
git add index.html         # ...or just one file
git commit -m "message"    # save a snapshot of the staged stuff
git log --oneline          # see your history
git push                   # send commits to GitHub
git pull                   # get commits from GitHub
```

### First-time setup for this repo (do these once)
```bash
cd ~/Desktop/keys-piano
git init                                   # start the repo
git add .                                  # stage everything
git commit -m "First version of Keys"      # first snapshot
# ...create the empty repo on github.com, then:
git remote add origin <the URL GitHub gives you>
git branch -M main                         # name the main line "main"
git push -u origin main                    # first push (sets the default)
```
After that, the daily rhythm is just: **edit → `git add .` → `git commit -m "..."` → `git push`.**
