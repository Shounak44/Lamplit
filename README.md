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
- Books come from legal public domain sources: **Project Gutenberg**, with the **Internet Archive** as a backup, plus **Wikisource** for Bengali and Hindi texts.
- You can still **upload your own** EPUB, PDF or TXT files exactly as before.

### Read almost anything
- **PDF**: shown exactly as the original pages, with the same layout, images and tables. Pages are drawn only when you scroll near them, so large books stay smooth.
- **EPUB** (DRM-free): turned into clean, readable text with a drop cap and chapter headings.
- **TXT**: plain text files work too.
- Drag a file onto the shelf, or press **Add book**.

### Highlights, notes and define
- Select a word or passage in any **EPUB, TXT or PDF** book, and a small toolbar appears with **Define**, **Highlight** and **Note**.
- On PDFs, Lamplit puts an invisible text layer over each page, so you can select text and your highlights are drawn right on the page. Tap a highlight to read, edit or remove its note.
- Everything you save is collected in the **Notes** tab. Press **Go** to jump back to the exact spot, or **Copy all** to export your notes.
- Scanned PDFs are only pictures of pages, so their text cannot be selected.

### Dictionary
- The **Dictionary** tab lets you type any word and see its meaning, without needing to select text first.
- Lookups ask two dictionaries at the same time and use whichever answers first, with Wiktionary as a backup. This works for English, and Wiktionary covers many other languages.
- Words you have looked up are remembered, so they open instantly the next time, even offline. A **Recent words** list keeps the last 60.

### Side panel
- Everything lives in one side panel with a **vertical pillar of tabs**: Books, Find, Dictionary, Notes, Bookmarks, Goals, Music and Help.
- Tap a tab on the pillar and its page opens next to it. No sideways scrolling.

### Sounds and moods
- **Ambience** (rain, thunderstorm, fireplace, ocean waves, forest night, quiet library) and **music** (soft piano, dark ambient, lo-fi, acoustic guitar) can play **together**, each with its own volume.
- Tracks **crossfade into themselves**, so loops never click or go silent.
- **The whole room changes theme** with what is playing: ember orange for the fireplace, deep teal for the waves, plum and pink for lo-fi, and so on. Soft ambient effects (rain, embers, dust, stars) float over the room and can be switched off in Help.
- **Add your own tracks** (MP3, WAV, OGG) as ambience or music. They stay on your device and get their own colour theme.

### YouTube mini player
- Press **Music**, switch to the **YouTube** tab, search for any song or mix, and tap **Play**. It opens in a small floating player, so you never leave the app.
- Drag it anywhere, minimise it, and keep reading while it plays. It stays open on every screen.
- One-tap Lofi Girl quick picks are included. YouTube needs an internet connection.

### Reading tools
- **Bookmarks** you can jump back to from the side panel.
- **Resume where you left off**, for every book.
- **Focus sprints**: 15 minute timer with an XP bonus.
- **Reading themes**: Night, Day and Sepia, plus adjustable text size (zoom for PDFs).
- **Help tab** listing places to download free books.

### Reading as a game
- **XP, levels, day streak and words read**, with a daily word goal you can set.
- **Daily quests**, a **bounty board** with one-of-a-kind medals, and a wall of **badges** to unlock.

### Private by design
Your shelf, bookmarks, highlights, notes, progress and your own tracks are stored **in your own browser**. There is no account and no tracking. A small helper service is used only to fetch free books and YouTube search results for you, and dictionary services only receive the word you look up. Your library is never uploaded anywhere.

---

## How to use

1. Press **Find books** to search free public domain books, or press **Add book** to upload your own DRM-free EPUB, PDF or TXT file.
2. Click a spine to read. Press **Bookmark** to save your spot.
3. Select a word or passage to **Define**, **Highlight** or add a **Note**. Open the **Dictionary** tab to look up any word you type.
4. Open **Music** at the bottom, pick an ambience and a music track, and watch the room change.
5. In **Music**, switch to the **YouTube** tab to play any song in the mini player while you read.

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
- [PDF.js](https://mozilla.github.io/pdf.js/) for showing PDF pages and making their text selectable
- [JSZip](https://stuk.github.io/jszip/) for opening EPUB files
- **IndexedDB** for storing books and your own tracks, **localStorage** for progress, highlights, notes and settings
- **Cloudflare Workers** for the small helper service
- [Gutendex](https://gutendex.com/), [Project Gutenberg](https://www.gutenberg.org/), [Wikisource](https://wikisource.org/) and the [Internet Archive](https://archive.org/) for free books
- [Free Dictionary API](https://dictionaryapi.dev/), [Datamuse](https://www.datamuse.com/api/) and [Wiktionary](https://en.wiktionary.org/) for word meanings
- The YouTube embedded player for the mini player
- Google Fonts: Cormorant Garamond, Jost, Noto Serif Bengali and Noto Serif Devanagari

---

## Good to know

- **Your library lives in one browser.** Clearing site data deletes it, and a different phone or laptop starts with an empty shelf. Highlights and notes are stored there too.
- **You need an internet connection** the first time you open the site, because the fonts and the PDF and EPUB libraries load from CDNs. **Find books**, **YouTube** and looking up **new words** need internet. Your shelf, uploaded books, notes, your own tracks and words you have already looked up work offline.
- **YouTube search is unofficial without a key** and may stop working if YouTube changes its pages. Some videos cannot be played in other websites and will show "Video unavailable". Just pick another result.
- **EPUBs with DRM** (most books bought from stores) cannot be opened.
- **PDFs are shown as pages**, not reflowed text, so you cannot change the font. Use the zoom buttons instead. Highlight, Note and Define work only on PDFs that contain real text, not on scanned ones.
- **iPhones** ignore volume changes from web pages, so the volume sliders and fades do not work there. Android and desktop browsers are fine.
- **Storage space** depends on the browser. Text books are small, but PDFs are stored as the original file.
- The colour fade between themes needs a recent browser. Older ones still change theme, just instantly.

---

## Roadmap

- [x] Download books from inside the app
- [x] YouTube mini player with search
- [x] Highlights and notes (EPUB, TXT and PDF)
- [x] Built-in dictionary tab
- [ ] Installable offline app (PWA)

---

## Credits

- Starter ambience and music from [Pixabay](https://pixabay.com/), used under the [Pixabay Content License](https://pixabay.com/service/license-summary/). Please do not redistribute the audio files on their own.
  <!-- Optional: list track titles and artists here -->
- Free books from [Project Gutenberg](https://www.gutenberg.org/), [Wikisource](https://wikisource.org/) and the [Internet Archive](https://archive.org/), searchable through [Gutendex](https://gutendex.com/).
- Word meanings from the [Free Dictionary API](https://dictionaryapi.dev/), [Datamuse](https://www.datamuse.com/api/) and [Wiktionary](https://en.wiktionary.org/).
- Made by Shounak ([@shounak44](https://github.com/shounak44)).
