# Quire

**A quire is a set of sheets folded and sewn into one signature. This does the same to your PDFs — right in your browser, nothing uploaded anywhere.**

Quire is a single-file, client-side PDF workbench. Drop in a file, do the work, get a file back. No server, no account, no upload — every merge, cut, rotation, stamp, and spreadsheet is built in your browser and never leaves your device.

---

## Features

| Tool | What it does |
|---|---|
| **Merge** | Combine multiple PDFs into one. Every page from every file lands in a single grid — drag to reorder across files, nudge a page earlier/later with ◀ ▶, rotate with ↺ ↻, or drop pages you don't want. |
| **Split** | Select pages by clicking thumbnails or typing a range (`1-3, 5, 8-10`), set them aside as a file, repeat, then export — as a single PDF or a ZIP if you made several. |
| **Arrange** | Reorder, rotate, and delete pages within a single PDF, then export the rebuilt file. |
| **Certify** | Stamp a seal onto one page, every page, or a page you pick. Upload your own signature/logo image, or let Quire generate a wax seal from your initials. Optionally append a full certificate page with signer, title, date, and statement. |
| **To Excel** | Extract text from a PDF into a real `.xlsx`. Reads each text item's on-page position, groups it into rows by vertical position and columns by horizontal gaps, and lets you preview the result before downloading. One sheet per page, or everything combined. |

## Getting started

There's nothing to install. Open `quire.html` in any modern browser.

```bash
git clone https://github.com/<your-username>/quire.git
cd quire
open quire.html   # or just double-click the file
```

An internet connection is required on load, since the PDF/Excel engines are pulled from a CDN (see below). Once loaded, all processing happens locally — no file content is ever sent anywhere.

## How it works

Quire is one HTML file: markup, styles, and logic together, with no build step and no backend. It leans on a small set of well-established libraries, loaded from cdnjs:

- **[pdf-lib](https://pdf-lib.js.org/)** — creating, merging, splitting, rotating, and stamping PDF pages
- **[PDF.js](https://mozilla.github.io/pdf.js/)** — rendering page thumbnails and reading text position for the Excel converter
- **[JSZip](https://stuk.github.io/jszip/)** — bundling multiple split outputs into one ZIP download
- **[SheetJS (xlsx)](https://sheetjs.com/)** — writing the `.xlsx` workbook for the Excel converter

Table extraction in **To Excel** is heuristic, not OCR: it clusters text by y-position into rows and by x-gaps into columns. It works well on genuinely digital PDFs with clean spacing (invoices, statements, simple reports) but won't extract anything from scanned/image-only PDFs, and can occasionally over-split irregularly spaced or justified text — use the preview button to check before downloading.

## Browser support

Any current version of Chrome, Firefox, Safari, or Edge. Drag-and-drop reordering also has explicit ◀ ▶ and ↺ ↻ button controls, so every tool is fully usable on touch devices too.

## Privacy

Quire has no backend. Files are read with the browser's File API, processed in memory, and offered back as a download — they're never transmitted over the network. The only network activity is the one-time load of the libraries listed above from their CDN.

## License

MIT — do whatever you like with it.
