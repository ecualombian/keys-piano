# Keys — Roadmap

The idea parking lot. Anything worth doing gets written here first; work happens in
batches pulled from **Now**. Claude keeps this file updated; Carlos adds/reorders
freely (it's just text — edit, commit, push, or paste thoughts into chat and
Claude will file them).

## Now (next working session)
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
- [x] Spotify play-along — MERGED 2026-07-18 overnight. Carlos still to do the
      one-time setup (developer.spotify.com Client ID) and login test.
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

## How we collaborate (agreed 2026-07-17)
1. Carlos practices; friction goes in a note (here, or just told to Claude —
   even "measure 21 felt wrong" is enough).
2. Ideas accumulate here instead of interrupting practice.
3. Working sessions pull a batch from **Now**, ship it, verify on the live site,
   move checked items to the git history.
4. `main` = always-working live site; risky work happens on branches.
