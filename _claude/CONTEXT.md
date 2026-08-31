# Project: Pitch Lab

**Repo:** https://github.com/benjaminboughton/intonation_web_app
**Deploy:** Not deployed (local file)
**Stack:** Vanilla JS — single self-contained HTML file, Web Audio API, localStorage

---

## What This Is

A custom ear training web app for rebuilding pitch intuition. Built for a user with functional tone deafness who played cello. Three-tier roadmap from basic pitch discrimination through interval recognition to real-world musical application.

---

## Current State

### Working
- [x] Pitch discrimination trainer (same/higher/lower on note pairs)
- [x] Instrument toggle (Piano / Cello synthesis)
- [x] Playback modes (Melodic sequential / Harmonic simultaneous)
- [x] Drill mode (endless, immediate feedback, note names revealed)
- [x] Quiz mode (10-question scored rounds with dot tracker)
- [x] Stats tab (cumulative per-pair accuracy, color-coded, localStorage)
- [x] Mic input (real-time pitch detection via autocorrelation)
- [x] Session timer (5-minute countdown)
- [x] Theory drawer (enharmonic equivalents, minor scale basics)

### In Progress
- [ ] Nothing active — Tier I is feature-complete

### Known Limitations
- [ ] Note pair generation is fully random — no adaptive difficulty
- [ ] Melodic/harmonic split is 50/50 random — not configurable
- [ ] Quiz is always 10 questions — not configurable
- [ ] No spaced repetition logic
- [ ] Mic pitch detection needs quiet environment (no noise filtering)
- [ ] No Tier II content yet

---

## File Map

| File | Purpose |
|------|---------|
| `ear-trainer.html` | Full Tier I app — audio engine, UI, stats, mic input, all self-contained |
| `transition.md` | Session handoff context document |

---

## Do Not Touch

- The single-file architecture — don't split into multiple files without explicit discussion
- localStorage key `pitchlab-stats` — changing it would wipe user progress

---

## Last Updated

2026-04-19 — Populated from transition.md, replacing template scaffolding
