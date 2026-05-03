# Convolution Visualizer

An interactive, step-by-step visualizer for **1D Discrete Convolution** — built to teach the *flip, shift, multiply, and add* process visually.

> **Live demo →** `https://YOUR-USERNAME.github.io/convolution-visualizer/`

---

## What it does

Discrete convolution is defined as:

$$y[n] = \sum_{k=-\infty}^{\infty} x[k] \cdot h[n-k]$$

This tool animates every step of that formula so you can *see* what is happening at each index:

| Phase | What you see |
|-------|-------------|
| **Flip** | h[k] is reversed across the y-axis to become h[−k] |
| **Shift** | h[−k] slides to the starting position before overlap |
| **Compute** | For each n, overlapping samples light up in amber; the multiplication and sum are shown live |
| **Done** | The full output y[n] is displayed on the bottom graph |

---

## Features

- **Three live stem-plot graphs** — x[k] (blue), h[n−k] (red), y[n] (green)
- **Color-coded multiply pairs** — active samples glow amber during each compute step
- **Live equation panel** — shows the exact arithmetic for the current step
- **Playback controls** — Play, Pause, Next, Previous, Reset
- **Speed slider** — animate slowly for teaching or fast for a quick overview
- **5 built-in presets** — moving average, impulse response demo, mixed polarity, and more
- **Custom signal input** — enter any comma-separated values in both fields
- **Zero dependencies** — pure HTML, CSS, and vanilla JavaScript; one file, opens in any browser

---

## Getting started

### Option A — just open the file
Download `index.html` and open it directly in any modern browser. No server or install needed.

### Option B — clone and serve locally
```bash
git clone https://github.com/YOUR-USERNAME/convolution-visualizer.git
cd convolution-visualizer
# open index.html in your browser, or serve with:
npx serve .
```

### Option C — deploy to GitHub Pages
1. Fork or clone this repo
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)` folder
4. Your app will be live at `https://YOUR-USERNAME.github.io/convolution-visualizer/`

---

## Usage

1. Enter your signal **x[n]** and impulse response **h[n]** as comma-separated numbers
   - Example: `x = 1, 2, 3, 1` and `h = 1, -1, 2`
2. Click **▶ Start Visualization**
3. Use the controls at the bottom to step through or auto-play the animation
4. Watch the equation panel on the left for the live math at each step

### Preset signals

| Preset | x[n] | h[n] | Demonstrates |
|--------|------|------|-------------|
| Default | `1, 2, 3, 1` | `1, -1, 2` | General convolution |
| Moving average | `1, 0, 1, 0, 1` | `1, 1, 1` | Box / smoothing filter |
| Simple accumulate | `1, 2, 3` | `1, 1` | Running sum |
| Impulse response | `1, 0, 0, 0, 0` | `1, 2, 3, 4` | System identification |
| Mixed polarity | `3, -1, 2, 0, 1` | `1, 2, -1` | Negative coefficients |

---

## Project structure

```
convolution-visualizer/
└── index.html      # entire app — HTML, CSS, and JS in one file
└── README.md
```

---

## How the math works

For two finite signals x[n] (length N) and h[n] (length M), the output y[n] has length **N + M − 1**.

Each output sample y[n] is computed by:
1. **Flipping** h[k] → h[−k]
2. **Shifting** h[−k] by n positions → h[n−k]
3. **Multiplying** x[k] · h[n−k] at every overlapping index k
4. **Summing** all products

The visualizer steps through each value of n from `0` to `N + M − 2`, highlighting the overlapping samples and showing the running total as it accumulates into y[n].

---

## Browser support

Works in all modern browsers — Chrome, Firefox, Safari, Edge. No frameworks, no build step.

---

## License

MIT — free to use, modify, and share.
