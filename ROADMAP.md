# Keys — Roadmap

The idea parking lot. Anything worth doing gets written here first; work happens in
batches pulled from **Now**. Claude keeps this file updated; Carlos adds/reorders
freely (it's just text — edit, commit, push, or paste thoughts into chat and
Claude will file them).

## Now (next working session)
- [x] **Section model** — SHIPPED 2026-07-19. Songs can declare `sections:{A,B…}` +
      `form:[…]`; the engine expands the same timeline as before but records each
      strain's step range. Section bar (Learn mode, sectioned songs only): label
      follows the playhead, ◀/▶ jump to this/next section start, "Play section" hears
      one strain, "Loop it" drills it (wrap-on-finish). Delivers the original
      "back to start of the section" ask + section looping. The Musette is the first
      sectioned song; flat songs are untouched. Follow-ups:
  - [ ] Section the Minuet (binary ‖:A:‖‖:B:‖) and the built-in Canon (variations).
  - [ ] Sectioned **imports**: extend the #import= format + saveImported validation so
        the personal Canon can carry sections (currently flat). Then its "intro" etc.
        become navigable/loopable on the device.
  - [ ] Auto-derive section boundaries from repeat/double barlines during Audiveris
        conversion, so new songs arrive already sectioned.
  - Note: this is the foundation the Levels ladder builds on (see Difficulty levels).

- [x] **Back / rewind (fine)** — SHIPPED 2026-07-19. "⏪ Back" button + ← key step the
      playhead back a few notes (3 steps/press) and re-arm them; the lane slides back.
      Manual only, works for any song, no section data needed. Verified: replays clean
      to the end, guards at the start, no-ops in free play.
- [x] **Back to start of section** — SHIPPED 2026-07-19 by the section model above
      (the ◀ button in the Section bar). Measure-level Back also shipped separately.
- [ ] **Slow-practice tempo** — a tempo control (½-speed toggle and/or a slider) that
      scales playback + the falling-lane speed. The gate already waits indefinitely, so
      slowing is purely a display/timing scale, not a rule change. Pairs directly with
      the section loop we just shipped: **loop a hard strain at half speed** is the
      classic drill. Promoted to Now 2026-07-19 after the ArtMaster/Artie research
      (see Research below) — Artie makes "loop + slow down" its core practice motion,
      confirming this is the highest-value next batch. Keep the written tempo as the
      100% mark; the label should show the real BPM at the chosen speed.

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
  - **Guiding model — "local original as the marker" (agreed 2026-07-19):**
    Every scanned piece yields an **exact original** = the full-fidelity version of
    Carlos's own book, which is the practice *target* / North Star. Originals live
    **device-local** (the ★ "My songs" list, delivered via #import= links) regardless
    of copyright — so a copyrighted book arrangement is handled structurally: it
    simply never leaves the device, no per-piece copyright call needed. The Canon
    Carlos imported 2026-07-19 is the first instance.
    The **published** app holds the Levels ladder, **rebuilt from public-domain
    sources**, climbing toward that original. Copyright ceiling: for copyrighted
    pieces the underlying melody is PD, so **L1 "the tune" is publishable**, but an
    L2/L3 mirroring the book's specific voicing/accompaniment is not — so their
    published ladder stops where it stops being PD, and the full arrangement exists
    only as the local original. PD works have no ceiling (L3 = the whole piece, as
    the Minuet already is). Naming keeps the two distinct: local
    "Canon in D — book (my practice)" vs a future published "Canon in D — L1 Tune".
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
- [ ] Metronome (slow-practice tempo promoted to Now — see above)
- [x] Section looping — SHIPPED 2026-07-19 as part of the section model (below).
- [ ] Use MIDI note-off (release) data — currently discarded. Not as the step trigger
      (press stays the trigger; release-gating breaks legato), but for: held-duration
      honesty on long notes, sustain visualization, held-chord detection for duet mode.
- [ ] Native iPad app (CoreMIDI, App Store) — needs Xcode + Apple Developer decisions

## Research: ArtMaster / Artie (looked at 2026-07-19)
ArtMaster (artmaster.com) is a subscription music-course platform; its flagship is
**Artie** (artmaster.com/artie), an AI piano app by MWM (on the App Store). Artie is
essentially a funded commercial version of what Keys already is — useful mostly as
validation that the core design is right, plus a couple of ideas worth borrowing.

Where Keys already matches Artie (the hard, defining parts — all done):
- Listens via **mic or MIDI**; **"Wait Mode"** = waits for the right note (our gate).
- **Loop tricky parts** (section loop + measure-snap Back); **one/both hands** (L/B/R);
  **import your own MIDI/MusicXML** (our #import= + the Audiveris→MusicXML pipeline).

Where Artie goes further — transferable ideas, ranked by fit:
1. **Slow-practice tempo** — Artie's core drill is "loop + slow down". We have loop;
   tempo is the other half. Promoted to Now (above). Highest-value next batch.
2. **Three difficulty levels** — Artie has exactly three; validates our L1/L2/L3 plan,
   now sitting on the section model.
3. **Rhythm/timing feedback** — a real FORK, not an auto-adopt. Artie judges timing and
   talks back; our gate deliberately waits forever to stay calm and legato-friendly
   (decision 2026-07-17). If ever added, make it an *optional* mode, not the default.
4. **Spoken/AI coaching, adaptive exercises** — SKIP. Against Keys' minimalist,
   no-account, single-file character; those are Artie's commercial-product features.

Framing: Keys should NOT try to compete with a subscription app. Its distinct value
is being Carlos's own free instrument with *his* exact book transcriptions, octaves,
fingerings, and local (even copyrighted) originals — which no commercial app gives.
The research sharpens the roadmap (slow-tempo next, Levels validated); it does not
redirect the project. Minor tech note: Artie imports MIDI/MusicXML directly; we
convert to our leaner format via Audiveris — direct in-browser import is possible
later but not worth rushing.

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
