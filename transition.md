# Pitch Lab — Claude Code Transition Doc

## Who This Is For

This doc exists to give a new Claude Code session full context on the Pitch Lab project — a custom ear training web app built for a specific user with functional (not clinical) tone deafness who played cello and wants to rebuild their pitch intuition as an adult.

---

## User Context & Goals

### The Problem
The user has functional tone deafness — not clinically confirmed amusia, but severe enough to have undermined their cello playing. Specific deficits identified:

- Cannot reliably tell if two notes are the same, higher, or lower
- Cannot find or reproduce a pitch themselves (e.g. could never self-tune a cello from a reference pitch)
- Cannot identify intervals (major 3rd, perfect 4th, etc.)
- Loses tonal context in real music

Cello is retired. The goal is not to return to performance — it's to develop **functional pitch intuition** for musical literacy and enjoyment.

### End Goals (Three Tiers)

**Tier I — Pitch Discrimination** *(built, v1)*
Pure same/higher/lower judgment on two notes. The absolute foundation. Must be solid before moving on.

**Tier II — Interval Recognition** *(not yet built)*
Identifying named intervals: minor 2nd, major 3rd, perfect 5th, octave, etc. Also: understanding minor scale variations (natural, harmonic, melodic minor — yes, confusingly the same words as melodic/harmonic intervals).

**Tier III — Real-World Application** *(not yet built)*
- Identifying the key of a piece of music by ear (target: casual listening like The Strokes)
- Understanding what distinguishes minor from major in practice
- Explaining music theory concepts like enharmonic equivalents (E# = F, etc.)
- Scale literacy: being able to name and explain the difference between minor scale types

### Session Philosophy
- **5 minutes or less** — daily micro-sessions, not marathon practice
- No heavy gamification, but quiz mode and cumulative accuracy stats are desired
- Mix of drill (open-ended practice) and quiz (scored 10-question rounds)
- Calm, clinical aesthetic — not game-like, but data-visible

---

## Current Build — Tier I (`ear-trainer.html`)

Single self-contained HTML file. No dependencies, no framework, no build step.

### Features
- **Instrument toggle**: Piano (triangle/sine oscillators, percussive decay) or Cello (sawtooth + filter, bowed attack/release)
- **Playback modes**: Melodic (notes play sequentially) and Harmonic (notes play simultaneously) — randomly mixed
- **Answer interface**: Lower / Same / Higher buttons, locked until notes have been played
- **Drill mode**: Endless pairs with immediate feedback, note names revealed on answer
- **Quiz mode**: 10-question rounds, scored, with per-question color-coded dot tracker
- **Stats tab**: Cumulative accuracy per note pair (e.g. C→F#), color-coded green/amber/red, persisted to localStorage
- **Mic input**: Real-time pitch detection via autocorrelation (Web Audio API + getUserMedia), shows detected note name and amplitude meter — lets user hum/sing back to check internal pitch
- **Session bar**: 5-minute countdown timer
- **Theory drawer**: Collapsible explanation of E#/F enharmonic equivalents and minor scale basics

### Audio Engine
Built on Web Audio API (no libraries).

- `playNote(midi, startTime, duration)` — generates oscillator-based synthesis per instrument
- `playPair(noteA, noteB, callback)` — handles melodic vs harmonic timing, fires callback on completion
- Note range: C2–A4 for cello mode, C3–E5 for piano mode (roughly idiomatic ranges)
- `autoCorrelate()` — YIN-style pitch detection from mic buffer for hum-back feature

### State & Persistence
- Stats stored in `localStorage` under key `pitchlab-stats`
- Format: `{ "C→F#": { correct: N, total: N }, ... }`
- No backend, no accounts — intentionally lightweight

### Known Limitations / Next Steps for v2
- Note pair generation is fully random — no adaptive difficulty yet (prioritize struggling pairs)
- Melodic/harmonic split is 50/50 random — could become a user setting
- Quiz is always 10 questions — could be configurable
- No spaced repetition logic
- Mic pitch detection works best in quiet environments; no noise filtering
- No Tier II content exists yet

---

## iOS App — Scope Assessment

This is a longer-term goal (user called it "v4"). The intent is both convenience and portfolio value. Here's an honest assessment.

### Realistic Path: React Native or Swift

**Option A: React Native (recommended starting point)**
- The web app logic (audio, state, UI) could be partially ported
- Web Audio API does NOT exist in React Native — audio synthesis would need to be replaced with `expo-av` or a native audio library
- Pitch detection (autocorrelation) would need reimplementation, likely via a native module or `react-native-pitch-detector`
- UI components translate reasonably well
- Shorter path to App Store than full native Swift
- Good portfolio piece if you can demo it working on-device

**Option B: Swift / SwiftUI (harder, better portfolio signal)**
- Full native: AVAudioEngine for synthesis, AudioKit library is a strong option
- SwiftUI makes UI relatively approachable
- Steeper learning curve if Swift is new
- Stronger signal for iOS-specific roles

### Honest Difficulty Assessment

| Concern | Reality |
|---|---|
| Audio synthesis on iOS | Harder than web — Web Audio API doesn't exist; AVAudioEngine or AudioKit required |
| Pitch detection | Doable, but mic permissions + buffer processing need native handling |
| App Store submission | Requires Apple Developer account ($99/yr), provisioning, review process |
| If Swift is new | Expect 2–4 weeks just on language + SwiftUI basics before touching audio |
| If React Native | Faster start, but audio layer still requires native knowledge |

### What Makes It a Good Portfolio Piece
- Demonstrates real-world audio processing (not just a CRUD app)
- Has a personal story behind it (which interviewers love)
- Shows product thinking — you defined the problem, designed the UX, built iteratively
- Mic input + real-time pitch detection is technically impressive on mobile

### Suggested Path
1. Finish and stabilize the web version through Tier II
2. Learn Swift basics + SwiftUI (Apple's own tutorials are genuinely good)
3. Port as a native Swift app using AudioKit for synthesis
4. Submit to App Store once stable

Don't rush to iOS until the core training content (Tier II at minimum) is solid — a polished v1 with real content is more impressive than a skeleton iOS app.

---

## File Reference

| File | Description |
|---|---|
| `ear-trainer.html` | Full Tier I app, self-contained |
| `transition.md` | This document |

---

## Suggested Prompt for New Claude Code Session

> "I'm continuing work on Pitch Lab, a custom ear training web app. Read transition.md for full context. The current build is ear-trainer.html — a self-contained Tier I pitch discrimination trainer. I want to start on [X]."

Replace `[X]` with whatever's next: adaptive difficulty, Tier II interval training, iOS scoping, etc.
