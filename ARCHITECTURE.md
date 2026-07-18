# Keys — how the engine works (handoff notes)

Single-file app: everything lives in `index.html`. Written 2026-07-18 as a handoff
so future work doesn't break the load-bearing parts.

## The step engine (the heart)
- A song is `notes:[[midi,beats,ornament?]...]` (right hand) + optional `lh:[...]`
  (left hand). `[null,beats]` = rest. `[m,0]` = chord member sharing the next
  note's start time. Ornament value = signed neighbor offset (+2 upper, -2 lower).
- `buildSteps(song)` merges both hands into a timeline of **steps**
  `{t, notes:[{m,hand,b,o,done}]}` grouped by start time (quantized ×96).
  The hand selector (`handFilter` L/B/R) filters at this level — rebuild steps
  (and reset `idx`, `curT`) after changing it, the song, or restarting.
- **Gate rule:** `press(m, fromMic, silent)` matches m against the current step's
  un-done notes — exact for touch/MIDI, pitch-class (%12) for mic. The step
  advances only when every note is done. Wrong notes count a miss EXCEPT
  ornament tolerance: within ±2 semitones of an ornamented note of the current
  step, or (within 700ms) the just-completed step, notes are silently ignored.
- MIDI note-ons call `press(note,false,true)` (silent: the real piano sounded).
  Note-offs are currently discarded (roadmap: duration honesty, duet mode).

## Rendering
- The lane is time-proportional: `curT` eases toward the current step's `t`;
  y = hitline − (t − curT)×PPB (55 px/beat). Block height = duration.
  RH teal (gold when current), LH violet. Ornaments: zigzag glyph above the
  block + a small satellite chip on the neighbor key's lane.
- The keyboard rebuilds per song (`windowForSong`: C-aligned window sized to the
  song's range, middle C dot on C4). **Black keys are positioned in pixels and
  MUST be re-aligned on any size change** — three triggers exist (ResizeObserver,
  resize event, 500ms width-poll in `draw()`); keep all three, environments differ.
- `midiName` spells flats when `song.flats` is true (set `useFlats` in loadSong).

## Audio input
- Mic: dedicated AudioContext created AFTER getUserMedia (sample-rate mismatch
  records silence on iOS) and the source node is kept referenced (Safari GC bug).
  Pitch detection = normalized autocorrelation, shortest-strong-lag pick (avoids
  octave-low errors), 2-consecutive-frames stability, gain slider (localStorage).
  A watchdog flags browsers that grant a silent mic (old WKWebView wrappers).
- Web MIDI works in desktop Chrome and iPad MIDI-browser apps (NOT iOS Safari).
  User's setup: Roland FP-10 → Bluetooth MIDI → MIDIWeb Browser app.

## Songs & sources
- Transcriptions: prefer text sources over vision — Mutopia LilyPond files are
  curl-able and authoritative (Minuet BWV Anh 115 and Canon came from there).
  `\relative` decoding: closest-note-within-a-fourth, then '/, shift octaves;
  after `<< >>` polyphony the reference is the LAST simple voice's first chord note.
- Photo transcription workflow: `sips -r 90` rotate → `--cropOffset y x -c h w`
  crops per system → read zoomed. Fingering numbers (1=thumb..5=pinky) reveal
  hand position and disambiguate note heights. PDF pages render via a small
  PDFKit Swift script (no poppler on this machine; recreate `pdfpage.swift` in
  the scratchpad when needed — see git history or ARCHITECTURE commit).
- Copyright rule of thumb: underlying public-domain works are fair game; do not
  copy a modern arrangement note-for-note — rebuild from PD sources matching the
  book's structure, and say so in the song comment.

## Deploy & practice loop
- `main` = live site (GitHub Pages, ~1-2 min after push). Verify before push:
  copy index.html to the session scratchpad, serve via .claude/launch.json
  ("keys-piano", port 8778; update the scratchpad path per session), drive with
  `window.__keysDebug` (midiNote, state, jump) — simulated MIDI tests everything.
  Browser-pane tabs must be VISIBLE for rAF/ResizeObserver to run — hidden tabs
  freeze rendering callbacks and fake test failures.
- One working folder shared with the user: check `git branch --show-current`
  before committing; their checkouts switch your branch too.
- The user's workflow prefs: bare command blocks (no comments — zsh executed
  them), literal numbered "Do this now" steps, batch work from ROADMAP.md.
