# Pitch Lab — CLAUDE.md

## What This Is

A custom ear training web app for rebuilding pitch intuition. Built for a user with functional tone deafness (not clinical amusia) who played cello. Goal: develop functional pitch literacy for musical enjoyment, not performance.

## Stack & Architecture

- **Single self-contained HTML file** (`ear-trainer.html`) — no frameworks, no build step, no dependencies
- Web Audio API for synthesis (oscillator-based, no samples)
- localStorage for persistence (`pitchlab-stats`)
- No backend, no accounts

## How to Run

Serve from localhost (not `file://`) so browser remembers mic permissions:
```
python3 -m http.server 8000
```
Then open `http://localhost:8000/ear-trainer.html`

## Key Conventions

- Single HTML file, but CDN dependencies are fine (no local build step)
- No heavy gamification — calm, clinical aesthetic with visible data
- Session philosophy: 5 minutes or less, daily micro-sessions
- Two modes: Drill (endless, immediate feedback) and Quiz (10-question scored rounds)

## Tier Roadmap

| Tier | Status | Description |
|------|--------|-------------|
| I — Pitch Discrimination | Built (v1) | Same/higher/lower judgment on note pairs |
| II — Interval Recognition | Not built | Named intervals (m2, M3, P5, octave, etc.) |
| III — Real-World Application | Not built | Key ID, major vs minor, scale literacy |
| iOS App | Future (v4) | Native port, likely Swift + AudioKit |

## Audio Engine Notes

- `playNote(midi, startTime, duration)` — oscillator synthesis per instrument
- `playPair(noteA, noteB, callback)` — melodic vs harmonic timing
- `autoCorrelate()` — YIN-style pitch detection for mic/hum-back feature
- Instrument modes: Piano (triangle/sine, percussive) and Cello (sawtooth + filter, bowed)
- Ranges: C2–A4 (cello), C3–E5 (piano)

## File Reference

| File | Purpose |
|------|---------|
| `ear-trainer.html` | Full Tier I app, self-contained |
| `transition.md` | Context doc for session handoffs |
| `_claude/CONTEXT.md` | Project state snapshot |
| `_claude/DECISIONS.md` | Architecture decision log |
