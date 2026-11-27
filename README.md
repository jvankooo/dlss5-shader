# dlss5-reshade

DLSS5 Shader for Uncapped

## DLSS 5 (RenoDX DLSS5 v2.0.1)

ReShade 6.8, RenoDX DLSS5 v10.8 and the dlss5-feed 2.0 bridge, set up so DLSS 5 runs once per captured frame on Uncapped's own stage, before frame generation.

### Install

Either:

- In Uncapped, Settings → **Post-processing** → **Import...** and pick `Uncapped-DLSS5_v2.zip` from the [latest release](../../releases/latest), or drag the zip onto the window.
- Or copy the entire contents of the [`dlss5_files`](dlss5_files) folder into your Uncapped install folder (the same folder as `Uncapped.exe`), merging it in on top.

Then launch Uncapped and open Settings → **Post-processing**: **RenoDX DLSS5** should be listed there. Enable it.

Strength (0-100%) and style (Default / Natural / Cinematic) are set from Uncapped's own menu under **RenoDX DLSS5**. Press **Home** for ReShade's menu if you want everything else.

`dxgi.dll` and `ReShade.ini` have to sit beside `Uncapped.exe`; everything else lives in `shaders/dlss5/`. Upgrading from v0.1.3: delete its `shaders/dlss5` folder first. Its old `DLSS5_Feed.fx` would otherwise sit in the same shader search path as the new one.

## Effects pack

[`effects`](effects) holds 16 native Uncapped effects (`.cvfx`). They are separate from DLSS 5: no ReShade, and any GPU.

Install: in Uncapped, Settings → **Post-processing** → **Import...** and pick `uncapped_effects.zip` (or a single `.cvfx`), or drag it onto the window. Each effect gets a toggle and its own sliders.

| Effect | File | What it does |
|---|---|---|
| CRT Display | `crt-display` | Scanlines, phosphor mask, glow, curvature |
| Scanlines | `scanlines` | Plain lines, cheap |
| VHS Tape | `vhs` | Colour smear, wobble, noise, bottom tear |
| Handheld LCD | `handheld-lcd` | Pixel grid, subpixels, few-shade palettes |
| Pixel Art | `pixel-art` | Chunky pixels, limited palette, dithering |
| Cartoon | `cartoon` | Cel shading and ink outlines |
| Comic Halftone | `comic-halftone` | Four-colour printed dots |
| Oil Paint | `oil-paint` | Brush-dabbed painting |
| Pencil Sketch | `sketch` | Outlines and cross-hatching on paper |
| Film Halation | `film-halation` | Highlight glow, split toning, grain |
| Black & White | `black-and-white` | Channel mix, contrast, sepia toning |
| Lens | `lens` | Colour fringing, vignette, distortion |
| Clarity | `clarity` | Local contrast and shadow detail |
| Sharpen | `sharpen` | Adaptive sharpening without halos |
| Edge Smooth | `anti-alias` | Smooths jagged edges |
| Capture Cleanup | `capture-cleanup` | Fixes limited range, colour bleed, banding |

Effects run in filename order, once per presented frame, so with frame generation at 2x each one costs double. Oil Paint, Cartoon and Pencil Sketch are the heaviest. Film grain and VHS noise move with the picture and hold still on a still one, because effects are not given a clock.

## Requirements

- For DLSS 5: Windows, Uncapped 0.2 or newer, and an NVIDIA RTX GPU with driver 616.56 or newer (DLSS 5 neural rendering needs both).
