# Babu Vignesh Kumar — Portfolio

Personal portfolio site of **Babu Vignesh Kumar**, a Unity game developer working on multiplayer
casino and hyper-casual games for Android and WebGL.

🔗 **Live site:** https://babuvigneshkumar.github.io/BabuVigneshKumar/

## About

A single-page static site built on the [Dimension](https://html5up.net/dimension) template by
HTML5 UP. Each section (About, Games, Drawings, 3D Art, Contact) is an `<article>` that opens as an
overlay panel, driven by the URL hash.

## Structure

```
index.html                 # the whole site — all sections live here
assets/
  css/main.css             # template styles + custom gallery/project rules
  css/noscript.css         # no-JavaScript fallback
  css/fontawesome-all.min.css
  js/main.js               # article show/hide logic (hash-driven)
  webfonts/                # Font Awesome 5 webfonts
images/
  Gif/*.webp               # animated gameplay clips
  Art/2d/                  # 2D drawings (+ thumb/ WebP thumbnails)
  Art/3d/                  # 3D renders (full/ web-sized JPGs, thumb/ WebP thumbnails)
  favicon.svg
```

## Running locally

No build step — it's plain HTML/CSS/JS. Serve the folder over HTTP:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Opening `index.html` directly via `file://` mostly works, but a local server is recommended so
relative paths and the hash routing behave exactly as they do in production.

## Adding a new project

1. Add the gameplay clip to `images/Gif/` as an **animated WebP** (see below).
2. Add a tile inside the `#work` article's `.gallery-grid`, pointing at `#your-project-id`.
3. Add a matching `<article id="your-project-id">` before the Contact section.

### Converting a GIF to animated WebP

Gameplay GIFs are huge. Convert them before committing:

```bash
convert input.gif -coalesce -resize '480x>' -quality 60 \
        -define webp:method=4 -loop 0 output.webp
```

This typically cuts file size by 70–85% with no visible quality loss at display size.

## Image guidelines

- Animated clips → **animated WebP**, max ~480px wide.
- Photos → JPEG, sized ~2× their display size, `-strip -quality 82`.
- Always set `width`, `height`, and `loading="lazy"` on images below the fold — this prevents
  layout shift and keeps the initial page load small.

## Credits

Template: [Dimension by HTML5 UP](https://html5up.net/dimension) (CCA 3.0).
Icons: [Font Awesome](https://fontawesome.com) 5 Free.
