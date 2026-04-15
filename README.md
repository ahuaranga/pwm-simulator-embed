# PWM Simulator — Embeddable Demo

A self-contained, interactive visualization of **Pulse-Width Modulation (PWM)**. It shows how a sinusoidal reference (fundamental) compared against a triangular carrier produces a two-level switched PWM output, and how that output reconstructs the original sine on average.

Built as a single HTML file — no build step, no dependencies, no frameworks. Drop it anywhere.

**Live demo:** https://ahuaranga.github.io/pwm-simulator-embed/

## Features

- **Two-panel scope view**: top shows the fundamental (sine) against the carrier (triangle); bottom shows the resulting PWM output with the reconstructed sine overlay.
- **Direct control of all three signal parameters**: fundamental frequency, fundamental amplitude (modulation index), and carrier frequency.
- **Overmodulation region indicator**: the amplitude readout flags the `Linear` / `Overmod` regions so users can explore the edge of the linear PWM region and square-wave degeneracy (0–127%).
- **Scope-style time base**: fixed ms presets (5 / 20 / 40 / 100 ms), plus a **Lock 1 cycle** toggle that forces the window to exactly one fundamental period regardless of frequency.
- **Animate / Pause / Reset** controls.
- **Crossing guides**: dashed vertical lines mark every sine/carrier intersection, aligned across both panels — making the cause→effect of each PWM edge visually obvious.
- **HiDPI / Retina crisp** rendering via `devicePixelRatio` scaling, with 4× oversampling to prevent aliasing at high carrier frequencies.
- **Fully responsive**: reflows for phones, tablets, desktops, and narrow iframes. Touch-target sizes comply with iOS/Android guidelines.
- **Iframe-friendly**: transparent background and `ResizeObserver` handling for dynamic container resizes.

## Controls

| Control | Range | Description |
|---|---|---|
| Fundamental | 5–120 Hz | Frequency of the reference sine |
| Amplitude | 0–127 % | Sine peak as a percentage of the carrier peak (modulation index) |
| Carrier | 300–5000 Hz | Switching frequency of the triangle reference |

When amplitude exceeds 100%, the simulator enters the **overmodulation** region — the sine starts to clip against the carrier peaks and the PWM output degenerates toward a square wave.

## Usage

### Online
Open the live demo: https://ahuaranga.github.io/pwm-simulator-embed/

### Standalone
Clone the repo and open `index.html` directly in any modern browser.

### Embedded
```html
<iframe
  src="https://ahuaranga.github.io/pwm-simulator-embed/"
  width="100%"
  height="560"
  style="border:0"
  loading="lazy">
</iframe>
```

The simulator uses a transparent background, so the host page's styling shows through the outer margin.

## Tech

- Pure HTML + CSS + vanilla JavaScript (ES5-compatible, IIFE-scoped).
- Canvas 2D rendering with 4× oversampling.
- Zero dependencies. Zero build tooling. One file.

## Educational Context

This simulator is designed as a teaching aid for courses and documentation on:
- PWM generation via sine-triangle comparison
- Modulation index and the linear vs. overmodulation regions
- Variable Speed Drives (VSDs) and inverter fundamentals

## License

MIT
