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

## Step 7 — Write your first real post

Posts live in `_posts/` and must be named exactly:

```
YYYY-MM-DD-short-title.md
```

Example: `_posts/2026-08-16-what-i-learned-about-rag.md`

Each post starts with **front matter** (the `---` block) then Markdown:

```markdown
---
layout: post
title: "What I Learned About RAG"
date: 2026-08-16
tags: [llm, rag]
---

## The idea
...your notes here, normal Markdown...
```

Delete or edit the sample post at
`_posts/2026-08-15-agentic-payments.md` once you're comfortable with the
format.

Commit and push — your new post appears on the homepage automatically,
newest first.

```bash
git add _posts/
git commit -m "New post: what I learned about RAG"
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
| `_config.yml` | Site title, your info, giscus keys |
| `_posts/` | Every learning log entry — one file per post |
| `_layouts/default.html` | Header, nav, footer — wraps every page |
| `_layouts/post.html` | Adds title/date/tags + comments to each post |
| `index.html` | Homepage — auto-lists all posts |
| `about.md` | Your portfolio/bio page |
| `assets/css/style.css` | All styling — edit freely |
