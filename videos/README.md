# Videos — cinematic film bands

Drop short, **muted, looping** clips here for the full-bleed film band(s) on the
landing page (`preview/index.html`, the `.filmband` sections).

## Recommended encoding (keep it light for paid mobile traffic)
- **Length:** 6–12 s, seamless loop
- **Formats:** provide both, WebM first (smaller) then MP4 (Safari/iOS):
  - `chapter-one.webm` (VP9/AV1)
  - `chapter-one.mp4`  (H.264, `-movflags +faststart`)
- **Size:** aim for ~1080–1440px wide, target < 2–3 MB per file
- **No audio track** (bands autoplay muted)
- Also export a **poster still** to `photos/film-poster.webp` (first frame)

## Wire it up
In `preview/index.html`, inside the `.filmband` `<video>`, uncomment the
`<source>` lines and point them here. Until then the poster image shows on its
own and nothing breaks.

Example:
```html
<video class="filmband__video" autoplay muted loop playsinline preload="none"
       poster="/photos/film-poster.webp">
  <source src="/videos/chapter-one.webm" type="video/webm">
  <source src="/videos/chapter-one.mp4"  type="video/mp4">
</video>
```
