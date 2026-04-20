<div align="center">

# Feeling Music · **Resonance**

**Mood → sound → canvas in the browser**

One static page: procedural audio, a dark visualization window, optional mic/file, and song suggestions from public APIs.

[![Stack](https://img.shields.io/badge/stack-HTML_·_CSS_·_JS-0d4a3a?style=for-the-badge&labelColor=1a1811)](https://github.com/wnorton26-sketch/Feeling-music-)
[![Repo](https://img.shields.io/badge/GitHub-Feeling--music--181717?style=for-the-badge&logo=github)](https://github.com/wnorton26-sketch/Feeling-music-)

<br />

</div>

---

## What you get

| | |
|:---|:---|
| **Interface** | Light paper-style layout: **narrow mood rail** + **stage** (canvas + controls). Typography: **Space Grotesk** + **Source Serif 4** — no framework. |
| **Sound** | Per-mood loops (arps, chords, noise) through a **mood EQ** (`BiquadFilterNode`) and **dynamics compressor**. |
| **Visuals** | **FFT** (mirrored spectrum), **waveform**, particles, rings, vignette, **VU-style meter** — all fed by one `AnalyserNode`. |
| **External audio** | **Mic** or **audio file** into the same graph; the picture follows the signal. |
| **Real tracks** | **Deezer** search first, then **iTunes**; offline **curated picks** + **YouTube** links if APIs fail. |

---

## Moods

| Mood | Canvas / vibe | Audio (approx.) |
|:---:|:---|:---|
| Chill | Cool drift | ~72 BPM · ambient arp · pad layer |
| Happy | Warm, busy | ~118 BPM · chords · accents |
| Angry | Sharp, intense | ~140 BPM · noise + saw / square |
| Melancholy | Soft, minor | ~80 BPM · minor pads |

Changing mood **retunes the synth filter** and **lerps** background + canvas colors.

---

## Run it

**No install, no build.** Open `index.html` in a modern browser, or serve the folder locally (helps if APIs block `file://`):

```bash
python3 -m http.server 8080
# http://localhost:8080
```

> You must click **Play** once — browsers require a user gesture before audio.

---

## Controls (as in the UI)

| Area | What it does |
|:---|:---|
| **Pick** | Chill / Happy / Angry / Melancholy — new pattern + EQ + (optional) song fetch. |
| **Play** | Starts or stops generated audio; level follows **Vol**. |
| **Mic** / **Stop** | Live input into the same chain (permission required). |
| **Vol** | Master gain. |
| **Motion** | Visual intensity (30%–130%). |
| **File** | Loop a local file through Web Audio. |
| **Find a track** / **Shuffle** | Pull another track for the current mood; **Auto when mood changes** toggles debounced fetch. |

---

## Tech

- **Web Audio API** — oscillators, noise, biquad mood filter, compressor, analyser (FFT + time domain).
- **Canvas 2D** — layered passes, blend modes, animation via `requestAnimationFrame`.
- **Fetch** — Deezer & iTunes search JSON (CORS permitting); curated fallback.
- **Dependencies** — none. Host on **GitHub Pages** or any static server.

---

## Repo layout

```
Feeling-music-/
├── index.html    # Markup, styles, script (single file)
├── README.md
└── .gitignore
```

---

## Repository

**[github.com/wnorton26-sketch/Feeling-music-](https://github.com/wnorton26-sketch/Feeling-music-)**

---

<div align="center">

Mood, signal, and motion — in one HTML file.

</div>
