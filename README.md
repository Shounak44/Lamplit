# Lamplit

**Light a lamp. Open a book.**

Lamplit is a cozy reading room that runs in your browser. Your books stand on a wooden bookshelf, the room changes colour with the music you play, and every page you read earns you a little XP. It works on phones and laptops, needs no account and no install.

[![Live demo](https://img.shields.io/badge/live%20demo-open%20Lamplit-cfae6a?style=for-the-badge)](https://lamplit-app.shounakhazra0.workers.dev/)

**Try it now: https://lamplit-app.shounakhazra0.workers.dev/**

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

### Find free books inside the app
- Press **Find books**, search by title or author, and tap **Add**. The book lands on your shelf, ready to read.
- Books come from legal public domain sources: **Project Gutenberg**, with the **Internet Archive** as a backup.
- You can still **upload your own** EPUB, PDF or TXT files exactly as before.

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

### YouTube mini player
- Press **YouTube**, search for any song or mix, and tap **Play**. It opens in a small floating player, so you never leave the app.
- Drag it anywhere, minimise it, and keep reading while it plays. It stays open on every screen.
- One-tap Lofi Girl quick picks are included. YouTube needs an internet connection.

### Reading tools
- **Bookmarks** you can jump back to from the side panel.
- **Resume where you left off**, for every book.
- **Focus sprints**: 15 minute timer with an XP bonus.
- **Reading themes**: Night, Day and Sepia, plus adjustable text size (zoom for PDFs).
- **XP, levels, day streak and words read**, to make reading a little game.
- **Help tab** listing places to download free books.

### Private by design
Your shelf, bookmarks, progress and your own tracks are stored **in your own browser**. There is no account and no tracking. A small helper service is used only to fetch free books and YouTube search results for you. Your library is never uploaded anywhere.

---

## How to use

1. Press **Find books** to search free public domain books, or press **Add book** to upload your own DRM-free EPUB, PDF or TXT file.
2. Click a spine to read. Press **Bookmark** to save your spot.
3. Open **Sounds** at the bottom, pick an ambience and a music track, and watch the room change.
4. Press **YouTube** to play any song in the mini player while you read.

---

## Project structure

```
Lamplit/
├── index.html      The whole app (HTML, CSS and JavaScript)
├── worker.js       Small Cloudflare Worker helper (book downloads and YouTube search)
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

### The helper (`worker.js`)

Browsers do not let a web page download books straight from other websites, so Lamplit uses a tiny free [Cloudflare Worker](https://developers.cloudflare.com/workers/). It does two things:

- `/get?url=...` fetches books and catalogue data, only from these sites: Gutendex, Project Gutenberg, the Internet Archive and Open Library.
- `/yt?q=...` searches YouTube. It works without a key. If you add a secret named `YT_KEY` (a YouTube Data API v3 key) in the Worker's settings, it uses the official API instead, which is more reliable.

To run your own copy, deploy `worker.js` as a Worker and put its address in the `PROXY` line near the top of the script in `index.html`.

---

## Built with

- Plain **HTML, CSS and JavaScript**, with no framework and no build tools
- [PDF.js](https://mozilla.github.io/pdf.js/) for showing PDF pages
- [JSZip](https://stuk.github.io/jszip/) for opening EPUB files
- **IndexedDB** for storing books and your own tracks, **localStorage** for progress and settings
- **Cloudflare Workers** for the small helper service
- [Gutendex](https://gutendex.com/), [Project Gutenberg](https://www.gutenberg.org/) and the [Internet Archive](https://archive.org/) for free books
- The YouTube embedded player for the mini player
- Google Fonts: Cormorant Garamond and Jost

---

## Good to know

- **Your library lives in one browser.** Clearing site data deletes it, and a different phone or laptop starts with an empty shelf.
- **You need an internet connection** the first time you open the site, because the fonts and the PDF and EPUB libraries load from CDNs. **Find books** and **YouTube** need internet every time. Your shelf, uploaded books and your own tracks work offline.
- **YouTube search is unofficial without a key** and may stop working if YouTube changes its pages. Some videos cannot be played in other websites and will show "Video unavailable". Just pick another result.
- **EPUBs with DRM** (most books bought from stores) cannot be opened.
- **PDFs are shown as pages**, not reflowed text, so you cannot change the font. Use the zoom buttons instead.
- **iPhones** ignore volume changes from web pages, so the volume sliders and fades do not work there. Android and desktop browsers are fine.
- **Storage space** depends on the browser. Text books are small, but PDFs are stored as the original file.
- The colour fade between themes needs a recent browser. Older ones still change theme, just instantly.

---

## Roadmap

- [x] Download books from inside the app
- [x] YouTube mini player with search
- [ ] Google sign-in and Drive sync, so your shelf follows you between devices
- [ ] Export and import your whole library as a backup
- [ ] Reading text out of scanned PDFs (OCR)
- [ ] Installable offline app (PWA)
- [ ] Highlights and notes

---

## Credits

- Starter ambience and music from [Pixabay](https://pixabay.com/), used under the [Pixabay Content License](https://pixabay.com/service/license-summary/). Please do not redistribute the audio files on their own.
  <!-- Optional: list track titles and artists here -->
- Free books from [Project Gutenberg](https://www.gutenberg.org/) and the [Internet Archive](https://archive.org/), searchable through [Gutendex](https://gutendex.com/).
- Made by Shounak ([@shounak44](https://github.com/shounak44)).
