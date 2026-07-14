# Solari Board Console

A self-contained, browser-based Solari-style split-flap departure board.
Manage flight data, watch it flip in with authentic mechanical clack audio
(sampled from a real split-flap recording), and export the animation as a
downloadable video clip.

**[Live demo](#)** — replace with your GitHub Pages URL once published (e.g. `https://yourusername.github.io/solari-board/`)

## Features

- 8-row board with Flight / Destination / Gate / Depart columns
- Reorder rows with per-row move controls
- Two animation modes:
  - **Populate Board** — full cascading flip from blank to your data (the "establishing" clip)
  - **Apply Update** — only the fields that changed flip, everything else holds (the "board update" clip)
- Real mechanical clack audio, sampled from an actual split-flap display recording, embedded directly in the page
- One-click recording: captures the canvas + audio to a downloadable `.webm` video
- Fully customizable appearance:
  - Background color
  - Default text color, with independent overrides per row and per column
  - Board name and its font size
  - Column label font size

## Usage

Just open `index.html` in a browser — no build step, no server, no dependencies.
Everything (including the audio samples) is embedded in the single HTML file.

1. Fill in the 8 rows, or click **Load Sample Data**.
2. Click **Populate Board** to record the opening cascade.
3. Edit whatever fields changed, then click **Apply Update** to record the transition.
4. Download the resulting `.webm` clip(s) and chain them together in your video editor.

`.webm` is what browsers can record natively. If you need `.mp4` for your editing
pipeline: `ffmpeg -i clip.webm clip.mp4`

## Tech notes

Pure HTML/CSS/JS, no frameworks. Rendering is done on `<canvas>` frame-by-frame;
video export uses `canvas.captureStream()` + `MediaRecorder`, mixed with a
Web Audio graph (with a limiter to keep dense flap cascades from clipping).

## License

MIT — do whatever you'd like with it.
