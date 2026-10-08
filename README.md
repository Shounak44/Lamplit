# Lamplit

**Light a lamp. Open a book.**

Lamplit is a cozy reading room that runs in your browser. Your books stand on a wooden bookshelf, the room changes colour with the music you play, and every page you read earns you a little XP. It works on phones and laptops, needs no account and no install.

[![Live demo](https://img.shields.io/badge/live%20demo-open%20Lamplit-cfae6a?style=for-the-badge)](https://shounak44.github.io/Lamplit/)

**Try it now: https://shounak44.github.io/Lamplit/**

<!-- Add a screenshot or two here, for example:
![The bookshelf](docs/shelf.png)
![The reader](docs/reader.png)
-->

---

## Features

### A real bookshelf
- Every book you add becomes a **spine on a walnut bookcase**, with its own colour, gold bands and a vertical title.
- Thicker books get wider spines. Shelves fill row by row, so the case grows as your library does.
- Hover (or tap) a spine to open the book. Use **Edit shelf** to delete books.

### Read almost anything
- **PDF**: shown exactly as the original pages, with the same layout, images and tables. Pages are drawn only when you scroll near them, so large books stay smooth.
- **EPUB** (DRM-free): turned into clean, readable text with a drop cap and chapter headings.
- **TXT**: plain text files work too.
- Drag a file onto the shelf, or press **Add book**.

### Sounds and moods
- **Ambience** (rain, thunderstorm, fireplace, ocean waves, forest night, quiet library) and **music** (soft piano, dark ambient, lo-fi, acoustic guitar) can play **together**, each with its own volume.
- Tracks **crossfade into themselves**, so loops never click or go silent.
- **The whole room changes theme** with what is playing: ember orange for the fireplace, deep teal for the waves, plum and pink for lo-fi, and so on.
- **Add your own tracks** (MP3, WAV, OGG) as ambience or music. They stay on your device and get their own colour theme.

### Reading tools
- **Bookmarks** you can jump back to from the side panel.
- **Resume where you left off**, for every book.
- **Focus sprints**: 15 minute timer with an XP bonus.
- **Reading themes**: Night, Day and Sepia, plus adjustable text size (zoom for PDFs).
- **XP, levels, day streak and words read**, to make reading a little game.
- **Help tab** listing places to download free books.

### Private by design
Everything is stored **in your own browser**. There is no server, no account, no tracking and nothing is uploaded anywhere.

---

## How to use

1. Get a DRM-free EPUB, a PDF or a TXT file (the **Help** tab lists free sources).
2. Press **Add book**, or drop the file onto the shelf.
3. Click a spine to read. Press **Bookmark** to save your spot.
4. Open **Sounds** at the bottom, pick an ambience and a music track, and watch the room change.

---

## Project structure

```
Lamplit/
├── index.html      The whole app (HTML, CSS and JavaScript)
├── audio/          Starter ambience and music tracks (MP3)
│   ├── rain.mp3
│   ├── storm.mp3
│   ├── fire.mp3
│   ├── waves.mp3
│   ├── forest.mp3
│   ├── library.mp3
│   ├── piano.mp3
│   ├── dark.mp3
│   ├── lofi.mp3
│   └── acoustic.mp3
└── README.md
```

To change the starter tracks, replace the files in `audio/` (keep the same names), or edit the `tracks` list near the sound code in `index.html`.

---

## Built with

- Plain **HTML, CSS and JavaScript**, with no framework and no build tools
- [PDF.js](https://mozilla.github.io/pdf.js/) for showing PDF pages
- [JSZip](https://stuk.github.io/jszip/) for opening EPUB files
- **IndexedDB** for storing books and your own tracks, **localStorage** for progress and settings
- Google Fonts: Cormorant Garamond and Jost

---

## Good to know

- **Your library lives in one browser.** Clearing site data deletes it, and a different phone or laptop starts with an empty shelf.
- **You need an internet connection** the first time you open the site, because the fonts and the PDF and EPUB libraries load from CDNs.
- **EPUBs with DRM** (most books bought from stores) cannot be opened.
- **PDFs are shown as pages**, not reflowed text, so you cannot change the font. Use the zoom buttons instead.
- **iPhones** ignore volume changes from web pages, so the volume sliders and fades do not work there. Android and desktop browsers are fine.
- **Storage space** depends on the browser. Text books are small, but PDFs are stored as the original file.
- The colour fade between themes needs a recent browser. Older ones still change theme, just instantly.

---

## Roadmap

- [ ] Google sign-in and Drive sync, so your shelf follows you between devices
- [ ] Download books from inside the app
- [ ] Export and import your whole library as a backup
- [ ] Reading text out of scanned PDFs (OCR)
- [ ] Installable offline app (PWA)
- [ ] Highlights and notes

---

## Credits

- Starter ambience and music from [Pixabay](https://pixabay.com/), used under the [Pixabay Content License](https://pixabay.com/service/license-summary/). Please do not redistribute the audio files on their own.
  <!-- Optional: list track titles and artists here -->
- Made by Shounak ([@shounak44](https://github.com/shounak44)).
