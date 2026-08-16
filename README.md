# Your Learning Log & Portfolio — Setup Guide

This is a Jekyll starter: a public blog + portfolio where each post is a
Markdown file, hosted for free on GitHub Pages, with comments powered by
giscus. Follow these steps in order.

---

## Step 1 — Create the GitHub repo

1. Go to [github.com/new](https://github.com/new).
2. Repository name **must** be exactly: `your-github-username.github.io`
   (replace `your-github-username` with your actual GitHub username, all
   lowercase). This exact naming is what tells GitHub "auto-host this as a
   website."
3. Set it to **Public**.
4. Do **not** initialize with a README (you already have one here).
5. Click **Create repository**.

---

## Step 2 — Push this starter to your new repo

Open a terminal in this folder (`jekyll-starter/`) and run:

```bash
git init
git add .
git commit -m "Initial commit: Jekyll starter"
git branch -M main
git remote add origin https://github.com/your-github-username/your-github-username.github.io.git
git push -u origin main
```

Replace `your-github-username` in the URL with your real username.

---

## Step 3 — Turn on GitHub Pages

1. On your repo page, go to **Settings → Pages**.
2. Under "Build and deployment," set **Source** to `Deploy from a branch`.
3. Set **Branch** to `main` and folder to `/ (root)`. Click **Save**.
4. Wait 1–2 minutes. Refresh the page — you'll see a green box with your live
   URL: `https://your-github-username.github.io`.

If you named the repo exactly `your-github-username.github.io`, this often
turns on automatically — but check Settings → Pages to confirm it's not
paused.

---

## Step 4 — Personalize `_config.yml`

Open `_config.yml` in this repo and edit:

- `title` — your site's name
- `description` — one-line tagline
- `author` — your name
- `github_username` — your GitHub username
- `email` — optional, shown on the About page

Commit and push the change:

```bash
git add _config.yml
git commit -m "Personalize site config"
git push
```

GitHub rebuilds automatically on every push — no manual deploy step.

---

## Step 5 — Turn on Discussions (needed for comments)

1. Go to **Settings → General** on your repo.
2. Scroll to **Features** and check the box for **Discussions**.
3. Go to the new **Discussions** tab on your repo and create a category
   called `General` (or use the default one) — this is where all your blog
   comments will actually live, as GitHub Discussion threads.

---

## Step 6 — Connect giscus (your comment system)

1. Go to **[giscus.app](https://giscus.app)**.
2. Under "Repository," type `your-github-username/your-github-username.github.io`
   and wait for the green checkmark (it confirms Discussions is enabled).
3. Under "Page ↔ Discussions Mapping," choose **pathname** (already matches
   this starter's config).
4. Under "Discussion Category," choose **General**.
5. Scroll down — giscus now shows a script snippet. You don't need the whole
   snippet; you just need two values from it:
   - `data-repo-id="R_xxxxxxx"`
   - `data-category-id="DIC_xxxxxxx"`
6. Open `_config.yml` in your repo and paste those two values into:
   ```yaml
   giscus:
     repo: "your-github-username/your-github-username.github.io"
     repo_id: "PASTE THE R_xxxxxxx VALUE HERE"
     category: "General"
     category_id: "PASTE THE DIC_xxxxxxx VALUE HERE"
   ```
7. Commit and push. Comments are now live on every post.

---

## Step 7 — Add a knowledge entry or a project

The site has two content types, each in its own folder. Neither needs a
special filename pattern — any `.md` file works.

### Adding a knowledge entry

Create a file in `_knowledge/`, e.g. `_knowledge/what-is-rag.md`:

```markdown
---
title: "What I Learned About RAG"
category: ai
tags: [llm, rag]
date: 2026-08-16
summary: "One line shown on the card preview."
---

## The idea
...your notes here, normal Markdown...
```

`category` must match a `key` defined in `knowledge_categories` in
`_config.yml` (currently `ai` or `payments`). It automatically shows up on
the homepage, on `/knowledge/`, and on its category page.

**To add a brand-new category** (e.g. "Design"), open `_config.yml` and add
a block under `knowledge_categories`:

```yaml
  - key: design
    name: "Design Knowledge"
    description: "Notes on UX, visual design, and product thinking"
```

Then create a matching listing page — copy `knowledge/ai.html`, rename it
`knowledge/design.html`, and change `permalink` and `category_key` at the
top to `/knowledge/design/` and `design`.

### Adding a project

Create a file in `_projects/`, e.g. `_projects/my-side-project.md`:

```markdown
---
title: "My Side Project"
summary: "One line shown on the card preview."
tech: [Python, FastAPI]
github: "https://github.com/Gemx2a/my-side-project"
date: 2026-08-16
status: "Active"
---

## What it is
...write-up here...
```

`status` is free text (`Active`, `Complete`, `Paused` — whatever you want).
`github` is optional; omit it if there's no public repo yet.

Commit and push — new entries appear automatically, newest first, no other
files need editing.

```bash
git add _knowledge/ _projects/
git commit -m "New knowledge entry + project update"
git push
```

---

## Step 8 (optional) — Preview locally before pushing

If you have Ruby installed:

```bash
bundle install
bundle exec jekyll serve
```

Then open `http://localhost:4000` to preview changes before pushing. Not
required — GitHub will build it either way — but useful if you're tweaking
layout/CSS and want fast feedback.

---

## Your regular workflow going forward

1. Learn something.
2. Create a new file in `_posts/` following the naming pattern.
3. `git add`, `git commit`, `git push`.
4. Live on your site within ~1 minute, comments open.

## File map (what lives where)

| File/Folder | Purpose |
|---|---|
| `_config.yml` | Site title, giscus keys, and the list of knowledge categories |
| `_knowledge/` | Every knowledge entry — one file per entry |
| `_projects/` | Every project — one file per project |
| `_layouts/default.html` | Header, nav, footer — wraps every page |
| `_layouts/knowledge-post.html` | Wraps each knowledge entry (tags, category stamp, comments) |
| `_layouts/project.html` | Wraps each project (tech tags, GitHub link, comments) |
| `index.html` | Homepage — recent knowledge + featured projects |
| `knowledge/index.html` | Knowledge hub — one card per category |
| `knowledge/ai.html`, `knowledge/payments.html` | Per-category listing pages |
| `projects/index.html` | Projects hub — all projects as cards |
| `about.md` | Your bio page |
| `assets/css/style.css` | All styling — edit freely |
