# Bass Note Finder

A single-page ear-training app for bass guitar. It plays a random note or chord arpeggio. You find it on the fretboard, then reveal the answer on a fretboard diagram and a bass clef stave.

## Features

- **Single notes, chords or mixed.** Chords cover major, minor, augmented and diminished triads, played as an up, up-and-down or up-plus-block-chord arpeggio at three speeds.
- **Manual or hands-free.** In hands-free mode the app plays, waits a set time (3–20 s), reveals the answer and moves on, so you can keep both hands on the bass.
- **Fretboard reveal.** In note mode, every position of the exact pitch is marked, with other octaves shown faintly. In chord mode the root and chord tones are marked with interval labels (R, ♭3, ♯5…).
- **Stave notation.** The note or chord is shown in bass clef, written an octave above sounding pitch (standard bass notation), with 8va for high notes and correct chord spelling. The stave can be off, shown on reveal, or shown straight away for reading practice.
- **4- or 5-string**, adjustable fret range, natural notes only, sharp/flat/both naming.
- **Playback pitch.** Play at true bass pitch, or 1 or 2 octaves up for phone speakers.
- **Scoring.** Tracks score, streak and the notes/chords you miss most. Missed items can be weighted to come up more often. Score and settings are saved in `localStorage`.

## Running it

It's one self-contained `index.html` with no build step or dependencies. Fonts load from Google Fonts and fall back to system fonts offline.

- Open `index.html` in a browser, or
- Serve it from any static host (GitHub Pages, Netlify, shared hosting). HTTPS is needed for the screen wake lock in hands-free mode.

On a phone, use "Add to Home Screen" for an app-like icon.
