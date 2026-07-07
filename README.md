# MCAT-Style Practice Viewer

A single-file, offline web viewer for reviewing multiple-choice practice
questions in a test-day-style interface — split passage/question panes,
highlighter, answer elimination, a question navigator, a section timer, and
per-question explanations.

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
- **Periodic table** modal (bring your own image — see below).
- **100% offline & dependency-free.** One `index.html`, no build step, no
  network calls, no trackers.

## Quick start

**Locally:** just open `index.html` in any modern browser (or serve the
folder, e.g. `python3 -m http.server`, and visit it). It loads the bundled
`sample.json` demo automatically.

**On the web (GitHub Pages):** enable **Settings → Pages → Deploy from
branch → main / root**. Because the app is `index.html`, your site goes live
at `https://<user>.github.io/<repo>/` with the demo pre-loaded.

## Loading your own questions

Three ways, in order of convenience:

1. **Auto-load** — save your set as **`content.json`** in the app folder.
   The viewer loads it on startup. `content.json` is **git-ignored**, so it
   is never committed or published.
2. **Load JSON button** (top-right) — open any `.json` file on demand.
3. Replace `sample.json` for a different bundled demo (keep it synthetic —
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

The periodic-table modal loads an image named `periodic_table.jpg` from the
app folder. No image is bundled (to avoid shipping third-party art); drop in
your own and it appears automatically. Without one, the modal shows a short
placeholder note.

## Project layout

```
index.html        The entire app (HTML + CSS + JS, no dependencies)
sample.json       Synthetic demo content (safe to publish)
docs/FORMAT.md    JSON question-format specification
LICENSE           GNU GPL v3
```

## Contributing

Issues and PRs for the **viewer** (UI, accessibility, format support,
bug fixes) are welcome. Please **do not** submit copyrighted exam content,
scrapers, or downloaded assets.

## License

Licensed under the **GNU General Public License v3.0** — see
[`LICENSE`](LICENSE). Derivatives must remain open under the GPL.
