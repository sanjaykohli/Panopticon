# Panopticon

A browser-based privacy diagnostic tool that shows what data websites silently collect about you — IP, hardware, canvas fingerprint, WebRTC leaks, fonts, and more. All processing happens locally. No server. No tracking.

---

## Clone & Run

```bash
git clone https://github.com/sanjaykohli/panopticon.git
cd panopticon
open index.html
```

That's it. No `npm install`. No build step. Just open the file.

---

## What it does

When you click **"I Understand, Continue"**, it runs a series of browser API probes and shows you exactly what any website could collect about you passively:

- **Public IP + location** — queried from `ipapi.co` / `ip-api.com`
- **VPN detection** — compares your browser's timezone against the IP-inferred timezone
- **WebRTC IP leak** — checks if your local LAN IP is exposed via ICE candidates (bypasses VPNs)
- **Canvas fingerprint** — renders a hidden scene, hashes the GPU output with SHA-256
- **Audio fingerprint** — runs an oscillator through a compressor, hashes the output
- **GPU info** — renderer and vendor strings via `WEBGL_debug_renderer_info`
- **WebGL deep scan** — max texture size, shader precision, viewport dims, extension count
- **Font enumeration** — probes 34 fonts by measuring canvas text width differences
- **Hardware profile** — CPU cores, RAM bucket, screen resolution, pixel ratio, touch points, storage quota, battery
- **Browser signals** — user agent, languages, Do Not Track, Global Privacy Control, color scheme, reduced-motion, plugins
- **Behavioral tracking** — mouse heatmap (radial gradient density), click count, scroll depth, keystrokes, time on page
- **Latency monitor** — live RTT chart using same-origin image loads
- **Security report** — auto-generated findings with fix recommendations

---

## Features

- **Fingerprint stability demo** — stores a hash in `localStorage` on first visit, shows a re-identification banner on return visits without any cookies
- **Camouflage mode** — hides the UI for privacy in public; hover to reveal
- **Entropy score** — animated score showing how fingerprint-able your browser is (illustrative, not population-measured)
- **Copy JSON** — exports everything collected as a structured JSON report
- **System overview modal** — explains each technique with privacy impact details
- **CSP meta tag** — the tool has its own Content Security Policy
- **`prefers-reduced-motion` support** — all animations disabled if the OS setting is on

---

## Tech

Pure vanilla HTML + CSS + JavaScript. No frameworks. No backend. Single file.

External resources:
- [Chart.js](https://www.chartjs.org/) — for the latency graph
- [Syne + Space Mono](https://fonts.google.com/) — fonts via Google Fonts
- `ipapi.co` / `ip-api.com` — for IP geolocation only

---

## Built with AI assistance

This version was improved using **Claude Sonnet 4.6** — fixed several critical syntax bugs in the original codebase (tagged-template call errors that prevented the file from parsing), rewrote the VPN detection logic, and added the new fingerprinting signals, heatmap, stability demo, and modal focus trap.

---

## References

- [EFF Cover Your Tracks](https://coveryourtracks.eff.org)
- [AmIUnique](https://amiunique.org)
- [BrowserLeaks](https://browserleaks.com)

---

> Built to educate, not to track.