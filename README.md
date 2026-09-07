# wii-browser

Wii/GameCube emulation in the browser. Evaluation-and-extend workspace built on
[wasm-dolphin](https://github.com/dougchansan/wasm-dolphin) — upstream Dolphin
cross-compiled to WebAssembly with a PowerPC→WASM JIT, software rasterizer +
WebGPU presentation.

## Quick start

Requires Node 18+ and a Chromium browser (WebGPU + SharedArrayBuffer).

```bash
cd wasm-dolphin
npm run play        # serves http://127.0.0.1:8080 with COOP/COEP headers
```

Drag a disc image (`.iso`, `.rvz`, `.ciso`, …) onto the page to boot it.
Bring your own games — none are included or committed (see `.gitignore`).

Controls: `X/Z/S/A` = A/B/X/Y · `Enter` = Start · `Q/E/C` = L/R/Z · arrows = D-pad · `WASD` = stick · gamepads polled.

## Status

- [x] Toolchain (emsdk 6.0.9, cmake 3.30.5) + upstream Dolphin clone @ `~/dolphin`
- [x] wasm-dolphin cloned + running locally (evaluation)
- [ ] Add Wii Remote input (mouse IR, Gamepad API motion/nunchuk)
- [ ] Custom frontend around the core
- [ ] Wiimote-required titles playable

## Vendored code & license

`wasm-dolphin/` is a vendored copy of
[dougchansan/wasm-dolphin](https://github.com/dougchansan/wasm-dolphin) at commit
`6ef689cf3956c3208c0966b8123d91c21d1f5ca4` (its `.git` was removed to vendor it
flat). It is © its authors, licensed **GPLv2-or-later**, and builds on
[Dolphin](https://github.com/dolphin-emu/dolphin) © the Dolphin Emulator Project.

Any distribution of this repository or built cores must comply with GPLv2+,
including corresponding-source obligations for the committed
`wasm-dolphin/cores/dolphin/dolphin-core-upstream.wasm` (see
`wasm-dolphin/provenance/` and `npm run dist:source` in that directory).
