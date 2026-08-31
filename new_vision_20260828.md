# New Vision


## Ben's Cello App
* Overarching goal: Re-establish fundamentals I was missing when I played cello 10+ years ago. Notably, INTONATION
* Retain tuner, but:
  * Add an ability to allow for me to hear an A/D/G/C to instead try to tune by sound instead of strictly tuner
  * Then, I will check against the tuner
* Scale scores
  * This is what I'm most bullish in. I want to input a scale and octave, perhaps "D major 2 octave", start recording and play. Then, I want to get a score strictly on my intonation of each note. I want to visualize where/when I start getting out of tune, and if I lean sharp/high. I want to aim for 100%, of course.
* Metronome
  * Hoping for web metronome, instead of using an app
* More to come!

## Scale Scores — Next Up
1. Allow for 2 and 3 octave scales
2. Allow for actual recordings that can be played back (review your run audibly, not just the scorecard)
3. History — track progress over time per scale (see improvement across sessions)
4. Partial scores — if I press stop before finishing the scale, show results for the notes I did play
5. Checkbox option for up AND down (ascending + descending in one run)
6. Full piece scoring — input actual sheet music (e.g. a Suzuki Book 1 piece) and score intonation across the entire piece
   * Best input format: MusicXML (widely available for Suzuki repertoire, parseable into a note sequence)
   * Also possible: MIDI import or manual text entry
   * Key challenges vs. scales: rhythm/duration awareness, repeated note detection (onset detection needed for two D's in a row), slurs/ties/dynamics affecting pitch detection
   * Realistic v1: MusicXML import → extract note sequence → "follow along" mode that tracks where you are by what it hears → per-note intonation scoring with scrolling visualization
   * Suzuki Book 1 pieces are slow and simple enough to be a good starting point