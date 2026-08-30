# Videos — motion clips for the landing page

The landing page (`preview/index.html`) follows the reference-page design: the
**hero stays a still photo, and the other main portraits become short, muted,
looping video/gif clips**. Each motion slot already shows a **poster still**, so
the page looks finished today — drop a clip in and it starts moving. Nothing
breaks while clips are still being made.

## Motion slots (what goes where)

| Slot | Type | Poster still | Clip files to add | Status |
|------|------|--------------|-------------------|--------|
| Hero (top of page) | **Still — stays a photo** | `photos/hero-portrait.webp` | — | done |
| Film band (below recognition) | Motion | `photos/reveal-night.webp` | `videos/chapter-one.webm` + `.mp4` | waiting on clip |
| Ethos portrait ("The Experience") | Motion | `photos/ethos-portrait.webp` | `videos/ethos.webm` + `.mp4` | waiting on clip |
| Reveal Night hero | **Click-to-play film** (YouTube) | thumbnail | already wired (Short `4xmrcap65bI`) | done |
| Wall-art trio (gallery) | **Stills — framed prints** | `photos/wall-art-1/2/3.webp` | — | done |

## How to hand me a clip

Easiest: **commit the source file to the repo** (a `.mp4`, `.mov`, or `.gif`),
the same way the photos were added — e.g. `videos/source/sequin-portrait.mov`.
Pasting an image/gif into chat only reaches me as a single still frame, not the
moving file, so it must be in git for me to use it.

I'll then transcode it to a web-optimized **muted, looping** pair and wire it in:
- `<name>.webm` (VP9/AV1 — smaller, loads first)
- `<name>.mp4`  (H.264, `-movflags +faststart` — Safari/iOS)

## Encoding targets (if you export them yourself)

- **Length:** 6–12 s, seamless loop
- **Size:** ~1080–1440px wide, target **< 2–3 MB** per file
- **No audio track** (slots autoplay muted)
- Provide both `.webm` and `.mp4`

## Wiring (I handle this)

Each motion slot has a commented `<video>` block right next to it in
`preview/index.html`. Once the files exist I uncomment it and point the
`<source>` lines at them. `prefers-reduced-motion` viewers automatically fall
back to the poster still.
