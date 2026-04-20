<div align="center">

# Resonance — Mood-Driven Music Engine

**A single-page web app that generates audio, reacts visually in real time, and recommends context-aware songs with resilient API fallbacks.**

[![Live Demo](https://img.shields.io/badge/Live_Demo-GitHub_Pages-ea4aaa?style=for-the-badge&logo=github)](https://wnorton26-sketch.github.io/resonance-feeling-music/)
[![Repo](https://img.shields.io/badge/Repo-resonance--feeling--music-181717?style=for-the-badge&logo=github)](https://github.com/wnorton26-sketch/resonance-feeling-music)

</div>

---

## Why this project is interesting

This is not just a themed landing page. `Resonance` combines procedural synthesis, live signal analysis, dynamic visualization, and content discovery in one browser-based experience with no external framework.

Core idea: **emotion selection controls both the sound design and the rendering model**, while users can swap between generated audio, microphone input, or uploaded audio files without leaving the same interactive stage.

---

## Feature highlights

- **Mood-driven generative audio**  
  Four musical profiles (`chill`, `happy`, `angry`, `melancholy`) each run different scheduling logic, tempo, and timbre combinations.

- **Real-time audio-reactive graphics**  
  Canvas effects are derived from FFT/time-domain analysis and include mirrored spectrum bars, waveform overlay, particles, rings, bloom, and level meters.

- **Multi-input audio pipeline**  
  Supports procedural synth, microphone stream, and local file playback through a shared Web Audio graph so visuals stay synchronized to whichever source is active.

- **Resilient song recommendation system**  
  Search/fetch chain uses multiple providers and strategies (standard fetch + proxy + JSONP fallback + Openverse + offline curated picks) to degrade gracefully on CORS/network issues.

- **Progressive, dependency-free architecture**  
  Plain HTML/CSS/JS with no build step. Runs locally and deploys directly to static hosting (GitHub Pages).

---

## How it works (technical)

### 1) Audio engine

- Uses `AudioContext` with modular nodes:
  - synth bus (`OscillatorNode` / noise buffers)
  - mood filter (`BiquadFilterNode`)
  - dynamics compression (`DynamicsCompressorNode`)
  - analysis tap (`AnalyserNode`)
  - final output (`GainNode` + destination)
- Mood switches retune synthesis parameters and filter characteristics.
- Transport controls handle start/stop, gain ramps, and source transitions.

### 2) Visualization engine

- Per-frame render loop via `requestAnimationFrame`.
- Pulls:
  - `getByteFrequencyData()` for spectral energy
  - `getByteTimeDomainData()` for waveform shape
- Derives musical energy bands (bass/mid/treble) and maps them to:
  - gradients and color lerp
  - particle size/speed
  - ring spread and pulse
  - HUD meters

### 3) Track discovery + fallback strategy

Primary and fallback behavior is intentional:

1. iTunes search (direct/proxy)
2. iTunes JSONP backup
3. Deezer search
4. Openverse audio catalog
5. Curated offline suggestions + YouTube search links

This keeps the product useful even when one provider is blocked.

---

## User-facing capabilities

- Pick mood and hear immediate musical/visual changes
- Play/pause generated transport
- Stream mic input into the analyzer
- Upload local audio for looped playback
- Adjust master volume and visual motion intensity
- Fetch and preview suggested tracks
- Shuffle alternatives from the active result pool
- Auto-fetch suggestions when mood changes

---

## Run locally

No install required.

```bash
python3 -m http.server 8080
```

Then open [http://localhost:8080](http://localhost:8080).

> Note: browsers require a user gesture before audio starts, so click `Play` at least once.

---

## Deployment

- **Live site:** [wnorton26-sketch.github.io/resonance-feeling-music](https://wnorton26-sketch.github.io/resonance-feeling-music/)
- **Repository:** [github.com/wnorton26-sketch/resonance-feeling-music](https://github.com/wnorton26-sketch/resonance-feeling-music)
- Hosted with **GitHub Pages** from the `main` branch root.

---

## Project structure

```text
resonance-feeling-music/
├── index.html   # app UI, styles, audio engine, visuals, data fetch logic
├── README.md
└── .gitignore
```

---

<div align="center">
Built as a browser-native interactive audio system, not just a static web mockup.
</div>
