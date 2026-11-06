# Comfort Data Collector

A single-page web app for collecting thermal-comfort data in class, built for the
NYJC Computing machine-learning lesson module. Students log readings; the teacher
gets a clean dataset.

## Features

- **Log a reading** — temperature (°C), relative humidity (%), and comfort level
  (`too warm`, `slightly warm`, `comfortable`, `slightly cold`, `too cold`), with
  input validation.
- **Readings table** — newest first, capped height with sticky headers, per-row
  delete, clear all, and CSV export (ISO timestamps, oldest first).
- **Reminders** — configurable interval (hours/minutes, default 1 hr) with quiet
  hours (default 22:00–06:00, handles midnight crossover). Browser notifications
  when permitted, in-page banners otherwise. Reminders repeat until a reading is
  logged.
- **Visualise my data** — collapsible scatter plot (temperature vs humidity)
  colour-coded by comfort level on a red–pink–white–pale-blue–blue diverging
  scale.
- **PWA** — installable on phones (offline-capable via service worker); data
  persists in `localStorage` per device. A "Remove all data" action in Settings
  resets the app.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The entire app (markup, styles, logic) |
| `manifest.webmanifest` | PWA manifest |
| `sw.js` | Service worker (precache + stale-while-revalidate) |
| `icon-*.png` | App icons (192, 512, and maskable 512) |

## Running

Serve the directory over HTTP(S) (e.g. `python -m http.server`) and open it in a
browser. Opening `index.html` directly also works — only the PWA features
(install, offline) need a secure context. Data stays on the device; nothing is
sent to a server.
