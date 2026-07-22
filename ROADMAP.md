# Keys — Roadmap

The idea parking lot. Anything worth doing gets written here first; work happens in
batches pulled from **Now**. Claude keeps this file updated; Carlos adds/reorders
freely (it's just text — edit, commit, push, or paste thoughts into chat and
Claude will file them).

## Now (next working session)
- [x] **Back / rewind (fine)** — SHIPPED 2026-07-19. "⏪ Back" button + ← key step the
      playhead back a few notes (3 steps/press) and re-arm them; the lane slides back.
      Manual only, works for any song, no section data needed. Verified: replays clean
      to the end, guards at the start, no-ops in free play.
- [ ] **Back to start of section** — the structural jump Carlos asked for ("flub in
      m7, drop to the top of the strain at m5"). NEEDS the song format to carry section
      boundaries, which it does not today — repeats are flattened into one list. Plan:
      author songs as `sections:{A,B...}` + `form:['A','A','B','A','B','A']`; buildSteps
      records where each section instance begins; the jump becomes a lookup. Same
      structure unlocks **section looping** and **difficulty levels** (both below).
      Open design Qs for Carlos: strain-level jump (whole A/B) vs measure-level?
      Add drag-the-lane-to-scrub as the free-rewind gesture too, or is the button enough?

- [x] **Hand selector [L | Both | R]** — SHIPPED 2026-07-17. v1: other hand hidden;
      Listen respects the selection (hear each hand alone). Fast follows still open:
      ghosted other hand, **duet mode** (app plays the other hand while you play yours).
- [x] **Ornament tolerance in the gate** — SHIPPED 2026-07-17 (verified: flourish over
      held LH note is neutral, real mistakes still count).
- [x] **Listen plays ornaments** — SHIPPED 2026-07-17 (real main–neighbor–main flourish).
- [x] **Mordent visuals** — SHIPPED 2026-07-17 (zigzag glyph above block, satellite
      chip on neighbor key's lane; lower mordents get the vertical stroke).
- [ ] **Difficulty levels per song** — one transcription, three views:
  - L1 "The Tune": melody-first, core signs only, no repeats/ornaments
  - L2 "The Hands": exact both hands + finger numbers shown atop falling bars
  - L3 "As Written": repeats + ornaments marked, exact octaves (today's Minuet)
  - Note: the hand selector absorbs part of L1's job (levels × hands mix freely)
- [ ] **Listen plays ornaments** at every level (mordents/trills as real fast notes —
      the fun part of the piece should be audible)
- [ ] **Ornament tolerance in the gate** — neighbor notes of an ornamented target are
      never counted wrong (before the main note or in a short grace window after), so
      actually performing a mordent — even over a held LH chord — is rewarded, not
      punished. Gate stays press-triggered (release-gating breaks legato feel; decided
      2026-07-17, Carlos's scenario, Claude's trigger analysis).
- [ ] **Mordent visuals**: real zigzag glyph on the block (not "~" text), plus small
      satellite chips on the neighbor key's lane at L3 showing the back-and-forth
      motion spatially.
- [ ] **Fingering data** for Minuet (from the printed sheet + Carlos's pencil marks)

## Next
- [x] Canon in D, both hands — SHIPPED 2026-07-17: ground bass + theme + repeated
      quarters + eighth-note runs + final D, built from public-domain sources
      (Mutopia violin line + Pachelbel's ostinato), structured to follow the book's
      sections. NOT a note-for-note copy of the Hal Leonard arrangement (that
      arrangement is copyrighted); Carlos to flag any spots that diverge from the
      book while practicing and we adjust from the PD material.
- [x] Musette — COMPLETE 2026-07-18. Carlos supplied a clean PDF of the Suzuki vol. 1
      page (no. 18, p.31), which unblocked the B section. Whole piece is now in:
      form ||: A :|| ||: B A :|| (24 measures), both hands, with the D-minor cadence
      (C#4/C#5) of mm. 5–8. Song no longer marked `flats` — no B-flat occurs in it,
      so the only accidental now spells as C# instead of Db.
      The PDF lives in `sheets/`, which is gitignored: the underlying work is public
      domain but that scan is a copyrighted modern edition and this repo is public.
- [x] **Musette A section was WRONG — fixed 2026-07-19.** Carlos hit wrong notes while
      practicing. The piece is in **D minor**, not F major (same one-flat signature).
      The original A section (read from a photo of a different book) had both hands a
      step low over F-A-C; melody now reads D D D F F | A G F | G A G F E | D, ending
      on the tonic, over D minor / G minor broken chords. Verified twice — systems 1
      and 3 of the scan are the same music and now agree.
      Lesson: beat-total and gate checks pass happily on wrong pitches. Verifying a
      song means checking the notes against the source, not just that it plays.
- [~] Spotify play-along — REMOVED 2026-07-19. Spotify's "Update on Developer Access
      and Platform Security" (posted 2026-02-06) reduced Development Mode in scope:
      **Development Mode now requires a Spotify Premium account**, one Client ID per
      developer, **max 5 authorized users per Client ID**, and a narrowed endpoint
      list. New Client IDs from 2026-02-11; existing integrations from 2026-03-09
      (the 03-09 update postponed only the *endpoint* changes — the Premium
      requirement and user cap took effect as planned).
      Two independent killers: Carlos isn't buying Premium, and the 5-user cap breaks
      the baked-in-shared-Client-ID design on a public Pages site the moment a sixth
      person opens it. Code is in git history if it's ever wanted back.
      Note for later: the *paste-a-link embed* in that panel needed no Client ID,
      no login and no developer app — only the "connect my playlists" half did.
      A free replacement is a paste-a-YouTube-link embed: full-length tracks, no
      account, no API key. That's the version worth building if play-along returns.
- [ ] KEXP live radio button with now-playing

## Later / ideas
- [ ] More songs from Alfred's (public-domain pieces only)
- [ ] Metronome + slow-practice tempo control
- [ ] Section looping (practice just measures 13–16, repeat)
- [ ] Use MIDI note-off (release) data — currently discarded. Not as the step trigger
      (press stays the trigger; release-gating breaks legato), but for: held-duration
      honesty on long notes, sustain visualization, held-chord detection for duet mode.
- [ ] Native iPad app (CoreMIDI, App Store) — needs Xcode + Apple Developer decisions

## Decisions on record
- Ornaments: shown as `~`, main note satisfies the gate; full ornament playing is
  L3-and-beyond territory. They always sound in Listen.
- MIDI = primary input (MIDIWeb Browser on iPad, FP-10 over Bluetooth MIDI);
  mic = fallback; on-screen touch always works.
- Song sources: public-domain works only; Carlos's own sheets are the preferred
  reference for octaves/fingerings.
- Canon stays as the simplified famous theme until the full book arrangement lands.

## Awaiting Carlos at the keyboard (not done until played)
- [ ] **Musette** — corrected A section (D minor) shipped 2026-07-19 but NOT yet
      played by Carlos. Claude's checks prove the app *runs*; only playing it proves
      the notes are *right*. This is the gate that the first Musette bug slipped past.

## How we collaborate (agreed 2026-07-17)
1. Carlos practices; friction goes in a note (here, or just told to Claude —
   even "measure 21 felt wrong" is enough).
2. Ideas accumulate here instead of interrupting practice.
3. Working sessions pull a batch from **Now**, ship it, verify on the live site,
   move checked items to the git history.
4. `main` = always-working live site; risky work happens on branches.
5. **Git (agreed 2026-07-19):** song changes commit straight to `main`, one commit
   per song — GitHub Pages only serves `main`, so a song on a branch can't be
   practised on the iPad, and a diff of MIDI integers isn't reviewable by eye.
   Branches/PRs are for engine work, where a bug means the app won't load at all.
6. **Before a song ships, Claude posts the melody in note names** (plus harmonic
   sanity checks: does it end on the tonic? do the LH chords match the key?), not a
   diff. That is the reviewable artifact; `[74,.5]` is not. A whole-piece misreading
   shows up instantly in note names and is invisible in a diff.
