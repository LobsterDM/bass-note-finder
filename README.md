# Bass Note Finder

A single-page ear-training app for bass guitar. It plays a random note or chord arpeggio. You find it on the fretboard, then reveal the answer on a fretboard diagram and a bass clef stave.

## Features

- **Single notes, chords or mixed.** Chords cover major, minor, augmented and diminished triads, played as an up, up-and-down or up-plus-block-chord arpeggio at three speeds.
- **Manual or hands-free.** In hands-free mode the app plays, waits a set time (3–20 s), reveals the answer and moves on, so you can keep both hands on the bass.
- **Fretboard reveal.** In note mode, every position of the exact pitch is marked, with other octaves shown faintly. In chord mode the root and chord tones are marked with interval labels (R, ♭3, ♯5…).
- **Stave notation.** The note or chord is shown in bass clef, written an octave above sounding pitch (standard bass notation), with 8va for high notes and correct chord spelling. The stave can be off, hidden behind a 💡 Hint button (tap to see the note in notation before revealing the answer), or shown straight away for reading practice.
- **4- or 5-string**, 20–24 fret basses, adjustable practice range, natural notes only, sharp/flat/both naming.
- **Playback pitch.** Play at true bass pitch, or 1 or 2 octaves up for phone speakers. Notes that would sound above the top of your bass drop an octave so they are always playable.
- **Scoring.** Tracks score, streak and the notes/chords you miss most. Missed items can be weighted to come up more often. Score and settings are saved in `localStorage`.

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

**When you change anything:** bump `VERSION` in `sw.js` (e.g. `bnf-v2`) so installed copies fetch the new files. If you add files, add them to the `FILES` list too.

**Social previews:** some platforms need an absolute image URL. Once the domain is known, change `og:image` in `index.html` to `https://yourdomain/og-image.png` and add a `<link rel="canonical">`.

## Local testing

`python3 -m http.server` in this folder, then open http://localhost:8000. Offline caching only works over http(s), not when opening the file directly.
