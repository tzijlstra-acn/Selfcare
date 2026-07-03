# How to handle me — a self-care dashboard

A single-file, self-contained interactive dashboard (Thomas Zijlstra). Animated avatar with moods, a life timeline, a marathon replay, a globe of visited countries (with an offline fallback map), a live 138-BPM trance loop, football crests, an interactive "good to know" section, and a "how to handle me" quiz.

Everything lives in **`index.html`**. There is no build step and no framework to install.

---

## Open it locally (VS Code)

1. Open the folder in VS Code (`File → Open Folder…`).
2. Just double-click `index.html` to open it in a browser, **or**
3. Install the **Live Server** extension, right-click `index.html` → **Open with Live Server** (gives you auto-reload while editing).

The audio needs a click to start (browsers block autoplay) — press **Play a 138 BPM loop** in the "On repeat" section.

---

## Publish it on GitHub Pages (free public link)

1. Create a new repository on GitHub (e.g. `self-care`).
2. Add `index.html` (and this `README.md`) to the repo. Either:
   - drag them into the repo's web uploader, or
   - from the terminal:
     ```bash
     git init
     git add index.html README.md
     git commit -m "Add self-care dashboard"
     git branch -M main
     git remote add origin https://github.com/<your-username>/self-care.git
     git push -u origin main
     ```
3. On GitHub: **Settings → Pages → Build and deployment**. Set **Source: Deploy from a branch**, **Branch: `main` / `/ (root)`**, then **Save**.
4. Wait ~1 minute. Your link will be:
   `https://<your-username>.github.io/self-care/`

That's the link to share with colleagues at the end of the talk.

### Even faster (no account): Netlify Drop
Go to <https://app.netlify.com/drop> and drag `index.html` onto the page. You get a live URL in seconds.

---

## What needs internet

The page loads a few things from public CDNs, so a live connection is needed for the full experience (any venue Wi-Fi is fine):

- **Fonts** (Google Fonts) — falls back to system fonts if blocked.
- **Flags** (flag-icons stylesheet) — country flags.
- **Globe** (d3 + topojson libraries, and the world map data) — the spinning 3D globe.

If the globe's map data can't load, the dashboard automatically shows a **built-in offline fallback map** (rough continents with your visited countries as orange dots), so that section is never blank. The audio is generated in the browser and needs no connection.

**Tip:** test on the actual laptop and Wi-Fi you'll present with beforehand.

---

## Editing the content

Open `index.html` in VS Code and search for these markers:

- **Timeline** — the `STAGES` array (`age`, `i` icon, `t` title, `n` note).
- **Moods** — the `MOODS` array (battery, colour, animation, nudge) and the `FACES` object (facial expressions).
- **Countries** — the `PASSPORT` object (grouped lists) and `CODES` / `LATLON` (flags and globe positions).
- **Good to know** — the `#gtkGrid` cards in the HTML; each has a `data-cat` (`work`/`sport`/`food`/`life`) that drives the filter tabs.
- **Quiz** — the `QUESTIONS` and `RESULTS` objects.
- **Fun sections** — search the HTML for `On the terraces` (crests), `Out of office` (adventures), `On repeat` (audio), `What's next` (future).

Reduced-motion preferences are respected automatically (animations pause).

---

## Files

- `index.html` — the whole dashboard (this is the only file you need to deploy).
- `README.md` — this file.
