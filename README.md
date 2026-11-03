# 🌿 MindReset

A private, browser-based stress-relief game for study pressure, overthinking, anxiety, difficult emotions and bedtime stress. It runs on mobile and desktop, needs no account, and keeps everything on your own device.

> MindReset is for relaxation and self-reflection. It is **not** a replacement for professional mental-health care. You can skip any exercise that doesn't feel right. If you feel unsafe or in crisis, contact your local emergency number or a crisis line in your country.

---

## The five modes

| Mode | What you do | Visual style |
|---|---|---|
| 📚 **Study Escape** | Pick a 5, 10 or 15 minute break, tick off small resets (shoulders, look far away, water, one thing you already know), then return when you're ready. | Focus cards on a calm study screen |
| 🌱 **Thought Garden** | Write a worry in a few words and plant it. Water it up to five times until it blooms, or let it go to delete it. | Animated SVG plants in a layered garden scene |
| 🌬️ **Breathing World** | Follow an expanding and contracting orb. Patterns: Calm 4-6, Box 4-4-4-4, Sleep 4-7-8. | Smooth glowing orb |
| 🏝️ **Emotion Island** | Choose a feeling (Anxious, Sad, Angry, Tired, Overwhelmed), then tap one of four places (Shore, Forest, Lighthouse, Cabin) for a small activity. | Colourful interactive SVG island |
| 🌙 **Night Escape** | A full-screen night scene with a 10, 20 or 30 minute wind-down timer and optional soft sound that fades out at the end. | Canvas moon, twinkling stars and layered hills |

## Features

- **No account, no tracking, no network calls.** Settings and progress are stored in the browser's `localStorage` under the key `mindreset`.
- **Sound is off by default.** It is a soft brown-noise generated with the Web Audio API. No audio files are used.
- **Motion control.** A "Motion" toggle stills all animation. `prefers-reduced-motion` is also respected.
- **Light and dark themes** follow the device setting.
- **Accessible:** visible keyboard focus, labelled buttons, large tap targets, live-region updates.
- **Mobile friendly:** safe-area insets for notches, a full-height layout, quick taps, and the screen stays awake during Night Escape where supported.
- **Back arrow** (←) on every mode returns to the home screen.

## Add it to your home screen

- **iPhone / iPad (Safari):** open the link, tap **Share**, then **Add to Home Screen**.
- **Android (Chrome):** open the link, tap the **⋮** menu, then **Add to Home screen** or **Install app**.

Notes:

- The shortcut opens the hosted link, so it needs an internet connection.
- Progress is stored per browser. On iPhone, the home-screen shortcut keeps its own storage, separate from Safari.
- On Android, the shortcut may open in a browser tab instead of a standalone window.

## Run it yourself

MindReset is a single self-contained file: `mindreset.html`.

1. Download `mindreset.html`.
2. Open it in any modern browser, or host it anywhere that serves static files (GitHub Pages, Netlify, Cloudflare Pages, your own server).

Fonts (Fraunces and DM Sans) load from Google Fonts, with system-font fallbacks if they're unavailable. There are no build steps or dependencies.

To make it a fully installable, offline app on your own domain, add a `manifest.webmanifest` and a small service worker alongside the file.

## Project structure

```
mindreset.html   # markup, styles and scripts in one file
README.md        # this file
```

Inside `mindreset.html`:

- **CSS tokens** at `:root` control colours for light and dark themes.
- **`V`** is a map of views (`home`, `study`, `garden`, `breathe`, `island`, `night`). Each view renders into `#app`.
- **`route()`** reads the URL hash (`#study`, `#garden`, `#breathe`, `#island`, `#night`) and shows the matching view.
- **`S`** is the saved state: counters, garden plants, sound and motion settings, and last-used lengths.

## Customising

- **Island activities:** edit the `EM` object. Each feeling has four suggestions, in the order Shore, Forest, Lighthouse, Cabin.
- **Island places:** edit the `LOC` array (name, position, colour, emoji).
- **Study resets:** edit the `cards` array in `V.study`.
- **Breathing patterns:** edit the `P` object in `V.breathe`. Each entry is a list of `[label, seconds]` steps. Labels containing "in" expand the orb, and labels containing "out" shrink it.
- **Break and wind-down lengths:** change the `[5,10,15]` and `[10,20,30]` arrays.
- **Colours:** change the CSS variables at the top of the stylesheet.

## Privacy

Everything you type, including worries in the Thought Garden, stays in your browser's local storage on your device. Nothing is sent to a server. Clearing your browser data, or using "Let go" on a plant, removes it.

## Known limitations

- Visuals are 2D (SVG and canvas) with a 3D-inspired feel. There is no true 3D yet.
- The screen wake lock and vibration depend on browser support.
- Sound may need a tap first on some browsers before it can play.
- Progress doesn't sync between devices.

## Ideas for next versions

- More sounds (rain, waves, wind chimes) and a sound mixer
- A garden that grows across several days
- More activities per Island location
- A private mood check-in history
- True 3D orb and study room with three.js
- Offline support and a proper installable app
- A hosted copy with its own domain

---

Take a breath. You're allowed to pause. 🌙
