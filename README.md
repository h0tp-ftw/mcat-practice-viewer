# MCAT-Style Practice Viewer

A single-file, offline web viewer for reviewing multiple-choice practice
questions in a test-day-style interface — split passage/question panes,
highlighter, answer elimination, a question navigator, a section timer, a
built-in periodic table, and per-question explanations.

It's one static `index.html` with **nothing to install or download** — open it
locally, or deploy it to GitHub Pages and use it straight from the browser.

> ⚠️ **Unofficial & content-free.** This project is **not affiliated with,
> endorsed by, or sponsored by the Association of American Medical Colleges
> (AAMC).** "MCAT" and "AAMC" are trademarks of the AAMC. **This repository
> ships no exam questions of any kind** — only the viewer and a small,
> entirely made-up demo (`sample.json`). You supply your own content, and
> you are responsible for complying with the copyright and terms of service
> of anything you load.

---

## Features

- **Authentic layout** — split passage / question panes, blue-navy exam
  chrome, Verdana passage text, A–D answer choices.
- **Two modes**, toggled by the **Review Answer** switch:
  - **Exam mode** (off) — change answers freely; see results only after you
    end the section.
  - **Tutor mode** (on) — **Confirm** reveals the correct answer and
    explanation; the button then turns into **Next ▶**.
- **Annotation tools** — highlight passage/question text, an **eraser** to
  remove highlights, and click-the-**✕** to strike out (eliminate) a choice.
  Highlights persist as you navigate.
- **Question navigator** with answered / flagged / current status, a
  clickable progress bar, and a **Flag for Review**.
- **Section timer** — time on the current question and total time.
- **Confidence tracker** — Low / Medium / High, colour-coded red / yellow /
  green.
- **Built-in periodic table** — a full 118-element table rendered from data,
  so it works offline with no image or download.
- **Load your own set** via the button *or by dragging a `.json` onto the page*.
- **100% offline & dependency-free.** One `index.html`, no build step, no
  network calls, no trackers.

## Quick start

**Locally:** open `index.html` in any modern browser — or serve the folder
(`python3 -m http.server`) and visit it. The bundled `sample.json` demo loads
automatically; nothing to install.

**Live on the web (GitHub Pages):** this repo ships a Pages deploy workflow
(`.github/workflows/deploy-pages.yml`). Enable **Settings → Pages → Build and
deployment → Source: GitHub Actions**, then push to `main`. The site goes live
at `https://<user>.github.io/<repo>/` with the demo pre-loaded — visitors just
click the link and use it, no install or download.

## Loading your own questions

Three ways, in order of convenience:

1. **Auto-load** — save your set as **`content.json`** in the app folder.
   The viewer loads it on startup. `content.json` is **git-ignored**, so it
   is never committed or published.
2. **Drag & drop** — drop a `.json` file anywhere on the page.
3. **Load JSON button** (top-right) — open any `.json` file on demand.
4. Replace `sample.json` for a different bundled demo (keep it synthetic —
   it *is* published).

See **[docs/FORMAT.md](docs/FORMAT.md)** for the exact JSON schema.

## Keyboard shortcuts

| Key | Action | Key | Action |
| --- | --- | --- | --- |
| `A` `B` `C` `D` | Select a choice | `Alt`+`H` | Highlight selection |
| `Alt`+`N` / `Alt`+`P` | Next / Previous | `Alt`+`E` | Erase highlights |
| `Alt`+`V` | Open navigator | `Alt`+`F` | Flag for review |
| `Alt`+`T` | Periodic table | `Esc` | Close a modal |

Tip: click any existing highlight to remove just that one; use the eraser
with no selection to clear all highlights on the current screen.

## Periodic table

The periodic table is **built in** — a full 118-element table (atomic number,
symbol, and standard atomic weight) rendered from data, so it works offline
with no image or download. Open it with the ⚛ toolbar button or **Alt+T**.

## Project layout

```
index.html              The entire app (HTML + CSS + JS, no dependencies)
sample.json             Synthetic demo content (safe to publish)
docs/FORMAT.md          JSON question-format specification
.github/workflows/      GitHub Pages auto-deploy
LICENSE                 GNU GPL v3
```

## Contributing

Issues and PRs for the **viewer** (UI, accessibility, format support,
bug fixes) are welcome. Please **do not** submit copyrighted exam content,
scrapers, or downloaded assets.

## License

Licensed under the **GNU General Public License v3.0** — see
[`LICENSE`](LICENSE). Derivatives must remain open under the GPL.
