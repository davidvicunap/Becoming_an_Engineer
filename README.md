# Becoming_an_Engineer

# Zero to Builder 🛠️

A static, self-hosted learning site that takes you from *zero* to *"I can build
anything"* — first-principles thinking, engineering problem-solving, programming
fundamentals in JavaScript **and** Python, and a flagship track on building
**AI agents on any LLM** (cloud or local) with power/privacy/cost tradeoffs made
explicit.

**This is a single self-contained file.** All the HTML, CSS, and JavaScript are
inlined into `index.html` — there is nothing else to install, bundle, or serve.

- **No backend, no accounts, no build step.**
- **Progress, XP, levels, and achievements persist in `localStorage`** — they survive refreshes and live only on your device.
- **Interactive challenges are checked in the browser.** JavaScript runs on the browser's own engine; the one Python challenge runs via [Pyodide](https://pyodide.org) (lazy-loaded from a CDN only when you open it — everything else is fully offline-friendly).
- Dark/light mode, mobile-first responsive, keyboard navigable.

## Run it locally

Because everything is inlined, you can simply **double-click `index.html`** to
open it in your browser — no server required.

(If you prefer a server, e.g. so the URL looks like a real site:
`python -m http.server 8000`, then open <http://localhost:8000>.)

## Deploy to GitHub Pages (exact steps)

1. Put `index.html` (and this `README.md`) in your repository and push:

   ```bash
   git add index.html README.md
   git commit -m "Add Zero to Builder"
   git push
   ```

2. On GitHub, open the repo → **Settings** → **Pages** (left sidebar).
3. Under **Build and deployment**:
   - **Source:** `Deploy from a branch`
   - **Branch:** the branch you pushed to (e.g. `main`), folder `/ (root)` → **Save**
4. Wait ~1 minute for the deploy to finish (watch the **Actions** tab).
5. Your site is live at `https://<your-username>.github.io/<your-repo>/`.

Every future push redeploys automatically. There is no build step, so there is
nothing that can fail to build.

> **Tip:** If you also add an empty file named `.nojekyll` next to `index.html`,
> GitHub Pages serves everything as-is and never runs it through Jekyll. It isn't
> strictly required for a single HTML file, but it's good insurance.

## What's inside

- **8-module roadmap** with lock/unlock progression, a **Free Roam** toggle to
  skip ahead, per-module progress bars, an XP/level HUD, and an achievements
  shelf.
- **Fully seeded content:** Modules 1–3 (first principles, thinking like an
  engineer, programming fundamentals in JS + Python) and the first two lessons of
  the flagship **AI Agents** track (context-window budgeting, and building a real
  tool-using agent loop), each with a working in-browser challenge checked by
  hidden tests.
- **Project briefs** with persisted self-assessment checklists.
- Modules 4, 5, 6, and 8 are stubbed with planned lesson titles ("coming soon").

### How progress and rewards work

| Event                        | Reward                                  |
| ---------------------------- | --------------------------------------- |
| Finish a lesson              | +25 XP                                  |
| Pass a challenge (all tests) | +50 XP                                  |
| Complete a project checklist | +100 XP                                 |
| Level up                     | Every 150 XP, with escalating titles    |

- A module **unlocks** when all previous modules' lessons + challenges are done
  (stub modules never block you). **Free Roam** on the home page unlocks
  everything.
- **Achievements** map to real competencies: debugging scientifically, reading
  docs, building an agent loop, running a local LLM, shipping a deploy…

### Resetting progress

Open the browser devtools console on the site and run:

```js
localStorage.removeItem("ztb.state.v1")
```

Refresh, and you're a beginner again.

## Editing the content

Everything is inside the single `index.html`. Open it in any text editor:

- **Styling** lives in the `<style>` block near the top.
- **Curriculum content** lives in the `<script type="module">` block — search for
  `const module1 = {` to see the schema. Each module has `lessons` (with optional
  `challenge`) and an optional `project` with a `checklist`. Lessons marked
  `{ stub: true }` render as "coming soon". Add a lesson by copying the shape of
  an existing one; the roadmap, unlocking, progress, and XP all adapt
  automatically.
