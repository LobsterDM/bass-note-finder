# Bass Note Finder (and guitar)

A single-page ear-training app for bass guitar. It plays a random note or chord arpeggio. You find it on the fretboard, then reveal the answer on a fretboard diagram and a bass clef stave.

## Features

- **Single notes, chords or mixed.** Chords cover major, minor, augmented and diminished triads, played as an up, up-and-down or up-plus-block-chord arpeggio at three speeds.
- **Intervals mode.** Plays 2, 3 or 4 notes from a chosen key (major or natural minor, fixed or random key). Name each interval, then reveal the intervals (e.g. M3 ↑, P4 ↓), note names and scale degrees, with the notes numbered on the fretboard and shown on the stave with the key signature. Options for the biggest jump (4th, 5th or octave) and starting on the key note. Missed intervals come up more often.
- **Bass or guitar.** An instrument switch (Settings, or `#guitar` / `#bass` on the URL) swaps in an instrument profile: tuning (4/5-string bass or 6-string guitar), fret count, pitch-detection range (28–700 Hz bass, 60–1400 Hz guitar), notation (bass clef or treble clef, both written an octave above sounding pitch), default playback octave, practice riffs and riff register. Settings, scores, smart-repetition history and custom riffs are kept separately per instrument.
- **Follow the changes.** Plays a chord progression (15 common progressions in major and minor keys, including ii–V–I and blues, fixed or random key) and listens for the roots played back in order. Optional bass note in the playback for an easier start. Chord names and roots are spelled for the key.
- **Sight-reading drill.** Shows a single note or a 4-note phrase on the bass clef stave with no sound; play what you read. Hint shows the note names, and the sound plays on reveal.
- **Tuner.** Cents meter using the same YIN detector over a longer (170 ms) window, accepting only clean readings and smoothing over the last few; accurate to well under a cent on test tones. Reference tones for each open string.
- **7th chords.** maj7, m7, dominant 7 and m7♭5 arpeggios alongside the triads.
- **Riffs mode.** Plays the first 4–8 notes of a tune with its rhythm and listens for you to play it back. Built in: public-domain classical/traditional melodies (Ode to Joy, Hall of the Mountain King, Pachelbel's Canon bass, Greensleeves, Scarborough Fair, Amazing Grace and more) and original practice riffs. Players can add their own riffs in Settings as note names (`E1 A1:0.5 …`, stored in `localStorage`). Original key or random transposition, title shown before or only on reveal.
- **Listening (🎤).** Uses the microphone and a YIN pitch detector to hear what you play. Single notes are marked right as soon as you play them; for chords and intervals, play the notes in order. Matches on note name by default (phone mics barely capture a bass's fundamental), or exact octave as an option. Works on HTTPS (or localhost) only, and with listening on, hands-free mode scores automatically.
- **Manual or hands-free.** In hands-free mode the app plays, waits a set time (3–20 s), reveals the answer and moves on, so you can keep both hands on the bass.
- **Fretboard reveal.** In note mode, every position of the exact pitch is marked, with other octaves shown faintly. In chord mode the root and chord tones are marked with interval labels (R, ♭3, ♯5…).
- **Stave notation.** The note or chord is shown in bass clef, written an octave above sounding pitch (standard bass notation), with 8va for high notes and correct chord spelling. The stave can be off, hidden behind a 💡 Hint button (tap to see the note in notation before revealing the answer), or shown straight away for reading practice.
- **4- or 5-string**, 20–24 fret basses, adjustable practice range, natural notes only, sharp/flat/both naming.
- **Playback pitch.** Play at true bass pitch, or 1 or 2 octaves up for phone speakers. Notes that would sound above the top of your bass drop an octave so they are always playable.
- **Scoring and smart repetition.** Tracks score, streak and average tries per note, chord and interval. A simple spaced-repetition scheduler (Leitner-style boxes) uses the number of attempts each round took (wrong notes heard while listening, hints, extra replays, misses) to decide when an item returns: 4+ attempts or a miss replays the same item immediately (up to 3 times in a row), other struggled-with items come back within 3–4 rounds, first-time successes are spaced out progressively further (8 → 16 → 30 → 60 → 120 rounds). Everything is saved in `localStorage`.

## Files

| Path | Purpose |
| --- | --- |
| `index.html` | The whole app (HTML, CSS, JS) |
| `sw.js` | Service worker – caches the site so it works offline once installed |
| `manifest.webmanifest` | Makes it installable as a phone/desktop app |
| `icons/`, `favicon.ico` | App icons and favicons |
| `og-image.png` | Preview image for links shared on social media / messaging |
| `fonts/` | Self-hosted Space Grotesk and JetBrains Mono (SIL OFL, licences included) |
| `.htaccess` | Apache settings: HTTPS redirect, MIME types, caching, compression |
| `robots.txt` | Allows search engines to index the site |

## Deploying

No build step. Upload everything (including the hidden `.htaccess`) to your web root, or a subfolder, on any static host over HTTPS.

- **Shared hosting (Apache):** upload via FTP/file manager. `.htaccess` handles HTTPS and caching.
- **Netlify / Cloudflare Pages / GitHub Pages:** point it at this repo's root. `.htaccess` is ignored there and isn't needed.

**When you change anything:** bump `APP_VERSION` near the top of the script in `index.html`. That one number is shown next to the title, names the offline cache (`sw.js` is registered as `sw.js?v=<APP_VERSION>`), and lets open copies of the app show a "vN available" tag. If you add files, add them to the `FILES` list in `sw.js` too.

**Social previews:** some platforms need an absolute image URL. Once the domain is known, change `og:image` in `index.html` to `https://yourdomain/og-image.png` and add a `<link rel="canonical">`.

## Local testing

`python3 -m http.server` in this folder, then open http://localhost:8000. Offline caching only works over http(s), not when opening the file directly.
