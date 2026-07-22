# Claude Code Prompt: Build "Zero to Builder" — a learn-to-engineer website

Copy everything below the line into Claude Code.

---

## Role & goal

You are a senior full-stack engineer and instructional designer. Build me a **static learning website** called **Zero to Builder** that takes a complete beginner from *zero* to *"I can build anything."* The site teaches modern software, cloud, and AI engineering — with a heavy emphasis on **thinking from first principles, solving problems like an engineer, building with AI tools, and shipping commercial-ready products.** A flagship track teaches me to **build AI agents on any LLM (cloud or open-source/local), optimizing for power, privacy, and low cost.**

This site is for one learner (me) and must be **hosted on GitHub Pages.**

## Hard constraints (do not violate)

1. **Static site only.** No backend, no server, no database, no build step that GitHub Pages can't run. Plain **HTML + CSS + vanilla JavaScript** (ES modules are fine). If you use a framework, it must compile to fully static files and deploy to GitHub Pages with `gh-pages` branch or `/docs` — but prefer vanilla to keep it simple and dependency-light.
2. **All progress, XP, and achievement state persists in `localStorage`.** No accounts, no external calls for core functionality.
3. **Interactive code challenges run entirely in the browser.** Use the browser JS engine for JS challenges; use **Pyodide** (loaded from CDN) for Python challenges if you include them. Never require a server to check answers.
4. **Fully responsive, mobile-first.** Must look good on phone, tablet, and desktop.
5. **Zero paid dependencies.** Anything the *learner* is later taught to use should also have a free/open-source/private path.
6. Provide a `README.md` with exact **GitHub Pages deploy steps** and how to run locally (e.g. `python -m http.server`).

## Design & UX

- Clean, modern, focused. Dark mode + light mode toggle (persisted).
- A clear visual **learning path / roadmap** on the home page showing modules as a connected sequence with lock/unlock and completion states.
- A persistent progress bar, current **XP / level**, and an **achievements shelf**.
- Accessible: semantic HTML, keyboard navigable, good contrast, `alt` text.
- Fast: no heavy frameworks unless justified; lazy-load Pyodide only on pages that need it.

## Curriculum (structure the content around these modules)

Each module = short lessons (first-principles explanations, not just syntax) + at least one **interactive challenge** + one **build project brief**. Order matters — it should feel like a real engineer's growth.

1. **How things actually work (first principles).** What a computer, program, memory, the internet, and an HTTP request *really* are. How to reason from fundamentals instead of memorizing.
2. **Thinking like an engineer.** Problem decomposition, breaking big problems into small ones, debugging as a scientific method, reading docs/source, asking good questions, tradeoffs.
3. **Programming fundamentals.** Core concepts through **Python and JavaScript**: variables, control flow, functions, data structures, iteration, error handling. Concept-first, language-second.
4. **Building with AI tools (the modern workflow).** How to pair-program with an AI: writing good prompts, giving context, reviewing/verifying AI output, knowing when *not* to trust it, using AI to learn faster. Emphasize that the engineer stays the decision-maker.
5. **Building real applications.** Frontend (DOM, state, components-thinking), backend concepts, APIs/REST, JSON, databases, and how a full app fits together.
6. **Cloud & deployment.** Hosting, DNS, CI/CD, containers (Docker basics), environments, and shipping. Keep examples on free tiers.
7. **AI Agents — flagship track.** Build agents on **any LLM**:
   - LLM fundamentals: tokens, context, temperature, system prompts, structured output.
   - Calling hosted APIs vs. running **open-source LLMs locally** (e.g. Ollama, llama.cpp) for privacy and cost.
   - The **agent loop**: reasoning → tool calls → observation → repeat. Tool use / function calling.
   - **RAG** (retrieval-augmented generation) with local embeddings.
   - Multi-step and multi-agent patterns; memory; guardrails.
   - **Power / privacy / cost tradeoffs** made explicit in every lesson (local vs cloud, small vs large models, when each wins).
8. **Commercial-ready products.** Auth, security basics, payments, monitoring/logging, testing, performance, and what separates a demo from a product people pay for.

## Achievements & gamification logic

- Achievements must map to **real engineering competencies**, not busywork. Examples: *"Read The Docs"* (completed a doc-reading challenge), *"Rubber Duck"* (debugged a broken snippet), *"Ship It"* (completed a deploy project), *"Local Brain"* (ran an open-source LLM), *"Agent Architect"* (built a working tool-using agent loop), *"Private by Design"* (built something with no third-party data leakage).
- XP awarded for finishing lessons, passing challenges, and submitting project self-checklists.
- Unlock later modules by completing earlier ones (with an override to skip ahead).

## Interactive challenge mechanics

- In-browser code editor (a lightweight one like CodeMirror via CDN is fine) with a **Run** and **Check** button.
- Challenges have hidden test assertions run client-side; show pass/fail + a hint on failure.
- Project briefs include a **self-assessment checklist** the learner ticks off (persisted) to earn the achievement.

## Deliverables

- Complete static site: `index.html`, module pages (or a single-page app with client routing — your call, but keep it GitHub Pages-friendly), CSS, JS modules, and challenge/lesson content as structured data (e.g. JSON or JS objects) so content is easy to extend.
- Seed **real content** for at least Modules 1, 2, 3, and the first two lessons of Module 7 (AI Agents) — including working challenges — so the site is usable immediately. Stub the rest with clear "coming soon" placeholders and a documented content schema so I can add more.
- `README.md` with local-run + GitHub Pages deploy instructions.
- Clean, commented code I can learn from by reading it.

## Acceptance criteria

- Deploys to GitHub Pages with no build errors and works offline for core features.
- Progress/achievements survive a page refresh.
- At least one JS challenge and one project checklist fully working end-to-end.
- Responsive on a 375px-wide phone and a desktop.
- Content teaches *why*, not just *how*.

Before you start, briefly outline your file structure and the content schema, then build.
