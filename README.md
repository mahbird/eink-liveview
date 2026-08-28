# GxEPD2 e-ink Liveview Editor

A **standalone browser-based live preview editor** for the [GxEPD2](https://github.com/ZinggJM/GxEPD2) Arduino library (e-paper / e-ink displays).

Write drawing commands, see them rendered instantly on a canvas, drag objects, get warnings for common mistakes, and copy clean code into your sketch — no install, no build step. Open the single HTML file in any modern browser.

**Live use:** download [`GxEPD2_liveview.html`](./GxEPD2_liveview.html) and open it locally, or host it (e.g. GitHub Pages).

---

## Features

- Live canvas preview for **BW**, **3-colour**, **4-colour**, **6-colour (Spectra)** and **7-colour (ACeP)** e-ink displays
- Supports most GxEPD2 / Adafruit_GFX drawing primitives, text, simple variables, and basic `for` / `while` loops (experimental)
- Because GxEPD2 builds on Adafruit_GFX, much of this tool is also useful for LCD sketches that use Adafruit_GFX (adjust colours as needed)
- Drag objects on the canvas or edit them in the properties panel
- **Resize** shapes with handles (corners/edges for rects, vertices for triangles, endpoints for lines, radius for circles)
- Insert shapes, text, and helpers from the toolbar
- Warnings for out-of-bounds geometry, unsupported colours, missing `setCursor` / `setTextColor` / `setTextSize`, and more
- Export PNG of the preview
- Copy clean code (comments stripped) for pasting into your Arduino sketch
- Undo / redo, **Clear canvas** (with confirmation), zoom, grid overlay, resizable panels

---

## Quick start

1. Download or clone this repository, or direclty use the <a href="https://mahbird.github.io/eink_liveview/">HTML hosted on github</a> in your browser.
2. Edit the C++ drawing code on the left (or use **Insert Tool**).
3. Watch the live preview and parser output update.
4. Click **Copy Clean Code** and paste into your `do { ... } while (display.nextPage());` loop.

A short **Beginner's Guide** (hardware SPI, pins, `setFullWindow` / `setPartialWindow`, full sketch skeleton) is built into the editor.

---

## Example workflow

```cpp
display.fillScreen(GxEPD_WHITE);
display.setTextColor(GxEPD_BLACK);
display.setTextSize(1);
display.setCursor(10, 20);
display.print("Hello World!");
```

Set the toolbar **Width / Height** to match your panel (or the size after `setRotation`), choose the colour class that matches your display, and refine layout visually before uploading to the MCU.

---

## Known limitations

- Text uses approximate Adafruit GFX 5×7 metrics; real panel glyphs and spacing will look slightly different. `display.getTextBounds` is not simulated.
- Bitmaps are shown as labelled placeholders (no pixel data in the preview).
- Rotation, custom fonts, and full hardware init are not simulated — set toolbar W/H to the rotated size and see the in-app Guide for setup.
- Custom / user-defined functions are not supported (only built-in GxEPD2 / GFX drawing commands, simple variables, and basic loops).
- Dragging or resizing an object that uses variables or expressions (e.g. `margin`, `display.height()`) will replace those expressions with plain numbers. Clicking alone does not change the code.

---

## Hardware & Arduino setup

This editor only previews **drawing** commands. To run on real hardware you still need:

- Correct GxEPD2 (or GxEPD2_4G) driver class and colour header
- Hardware SPI pins (MOSI / SCK) plus CS, DC, RST, BUSY
- `setFullWindow()` or `setPartialWindow(...)` **before** `firstPage()`
- The usual `firstPage()` / `nextPage()` paged loop and `powerOff()` when done

See the in-app **Beginner's Guide** for a full sketch skeleton and pin notes.

Official library: [ZinggJM/GxEPD2](https://github.com/ZinggJM/GxEPD2)

---

## License

This project is distributed under the <a href="https://www.gnu.org/licenses/gpl-3.0.html">**GNU General Public License v3.0 (GPLv3)** </a>. 
Derivatives must remain open-source under the same license

---

## Credits

- Built for use with **[GxEPD2](https://github.com/ZinggJM/GxEPD2)** by Jean-Marc Zingg and the underlying **[Adafruit_GFX](https://github.com/adafruit/Adafruit-GFX-Library)** library.
- Editor built by [mahbird](https://github.com/mahbird) with Grok 4.5 / xAI assistance.


