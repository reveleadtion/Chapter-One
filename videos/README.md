# Videos — motion clips for the landing page

The landing page (`preview/index.html`) follows the reference-page design: the
**hero stays a still photo, and the other main portraits become short, muted,
looping video/gif clips.** Each motion slot shows a **poster still**, so the
page looks finished even before a clip lands; drop a clip in and it moves.

## What's wired now

| Slot | State | Files |
|------|-------|-------|
| Ethos portrait ("The Experience") | **Live motion** ✅ | `videos/chapter-one-portrait.webm` + `.mp4`, poster `photos/chapter-one-portrait-still.webp` |
| Film band (below the marquee) | Poster still | `photos/reveal-night.webp` — add a **wide ≥1440px** `videos/reveal-night.webm`+`.mp4` to animate |
| Reveal Night hero | Click-to-play film (YouTube Short `4xmrcap65bI`) | — |
| Hero (top of page) | Still (stays a photo) | `photos/hero-portrait.webp` |

`videos/chapter-one-portrait.*` were transcoded from `videos/source/Chapter_One.gif`
(muted, looping, no audio track). The `.webm` (VP9, ~340 KB) is served first;
the `.mp4` (H.264, faststart) is the Safari/iOS fallback.

## Adding another clip

1. Drop the source (`.mov`/`.mp4`/`.gif`) in `videos/source/`.
2. Transcode to a muted, looping pair, e.g.:
   ```
   ffmpeg -i source.gif -c:v libvpx-vp9 -b:v 0 -crf 33 -an -pix_fmt yuv420p out.webm
   ffmpeg -i source.gif -c:v libx264 -pix_fmt yuv420p -movflags +faststart -an \
          -crf 23 -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" out.mp4
   ```
3. Export a poster still (first frame) to `photos/`.
4. Point the slot's `<video>` `poster` + `<source>` lines at the new files.

Targets: 6–12 s seamless loop, ~1080–1440px wide for full-bleed bands, target
< 2–3 MB per file, no audio.
