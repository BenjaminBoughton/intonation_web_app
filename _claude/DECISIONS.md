# Architecture & Design Decisions

> This file records *why* choices were made — not what was built.
> Add an entry any time a non-obvious decision is made so it doesn't get re-litigated.

---

## Decision Log

### 2026-04-19 — Single self-contained HTML file

**Context:** How to structure the web app

**Options Considered:**
- Option A — Single HTML file with inline CSS/JS
- Option B — Multi-file with bundler (Vite, Webpack, etc.)
- Option C — Framework-based (React, Vue, etc.)

**Decision:** Single self-contained HTML file

**Reason:** No build step, no dependencies, maximum portability. The app is small enough that splitting would add complexity without benefit. Can be opened directly in a browser. Aligns with the "lightweight, no-friction" philosophy of 5-minute daily sessions.

---

### 2026-04-19 — Web Audio API oscillator synthesis (no samples)

**Context:** How to generate instrument sounds

**Options Considered:**
- Option A — Pre-recorded audio samples
- Option B — Web Audio API oscillator synthesis

**Decision:** Oscillator synthesis

**Reason:** Zero external assets, instant loading, no hosting concerns. Piano uses triangle/sine with percussive envelope; cello uses sawtooth + filter with bowed attack/release. Good enough for pitch training where timbral accuracy isn't the goal.

---

### 2026-04-19 — localStorage for persistence

**Context:** How to store user progress/stats

**Options Considered:**
- Option A — Backend database
- Option B — localStorage

**Decision:** localStorage

**Reason:** No accounts, no backend, no server costs. Single-user app. Tradeoff: stats are device-local and not backed up. Acceptable for current scope.

---

### 2026-04-19 — iOS app deferred to v4

**Context:** When to build a native mobile version

**Decision:** Finish and stabilize web through Tier II before starting iOS port

**Reason:** A polished web app with real training content is more impressive and useful than a skeleton iOS app. iOS audio (AVAudioEngine/AudioKit) is significantly harder than Web Audio API. Swift learning curve is non-trivial. Better to nail the training methodology first.
