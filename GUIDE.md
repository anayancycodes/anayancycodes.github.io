# Your site — how it works, one step at a time

Hi Anayancy. This is your manual. It's written so you can do **one small block at a time** and stop whenever. Nothing here is urgent, and nothing breaks if you walk away mid-way.

There are three "levels" below. **You only need Level 1 to get your site live.** Levels 2 and 3 are for when you feel like it.

---

## What you have now

Your repo is now a real **Hugo** blog (Hugo = a tool that turns Markdown files into a website). Here's the map:

```
anayancycodes.github.io/
├── hugo.toml              ← settings (title, menu, your links)
├── content/
│   ├── about.md           ← your About page
│   ├── search.md          ← the search page (don't need to touch)
│   └── posts/             ← YOUR BLOG POSTS LIVE HERE
│       ├── welcome-learning-in-public.md
│       ├── r-bioinformatics-starter-kit.md
│       └── _TEMPLATE-new-post.md   ← copy this to start a new post
├── themes/PaperMod/       ← the design (don't touch)
├── static/images/         ← put images here
└── .github/workflows/     ← the robot that publishes your site
```

The only folders you'll ever really touch: **`content/posts/`** and once in a while **`hugo.toml`**.

---

## LEVEL 1 — Get it live (≈10 minutes, do once)

You don't even need Hugo installed for this. GitHub builds the site for you.

**Step 1 — Push these files to GitHub.** In a terminal, in this folder:

```bash
git add .
git commit -m "Set up Hugo blog with PaperMod"
git push
```

**Step 2 — Turn on GitHub Pages (one time only).**
Go to your repo on github.com → **Settings** → **Pages** → under "Build and deployment" set **Source = GitHub Actions**. That's it.

**Step 3 — Watch it build.**
Go to the **Actions** tab on your repo. You'll see a job running. When it turns green (1–2 min), your site is live at:

> **https://anayancycodes.github.io/**

✅ **That's the whole launch.** If you stop here, you have a working blog. Come back for the rest another day.

> If the Actions job is red instead of green: click it, read the red step. 9 times out of 10 it's a typo in `hugo.toml`. You can also just undo your last change and push again.

---

## LEVEL 2 — Make it yours (whenever)

Open **`hugo.toml`**. Every line you might want to change is marked `# EDIT`. The big ones:

- `title` — what shows in the browser tab and header
- `[params.homeInfoParams]` → `Title` and `Content` — the welcome blurb on your homepage
- `[[params.socialIcons]]` — your real links. There are commented-out blocks for LinkedIn and Bluesky; delete the `#` at the start of those lines to turn them on.

Then open **`content/about.md`** and rewrite it in your own words. It's currently a draft in roughly your voice — every `(EDIT: ...)` is a blank for you to fill.

To publish a change, it's always the same three commands:

```bash
git add .
git commit -m "describe what you changed"
git push
```

The site rebuilds itself ~1 minute after every push.

---

## How to write a new post

1. Go to `content/posts/`.
2. Copy `_TEMPLATE-new-post.md` and rename the copy. **The filename becomes the web address**, so use lowercase-with-dashes, e.g. `learning-deseq2.md`.
3. Edit the top section (between the `+++` lines):
   - `title` — the post title
   - `date` — today's date
   - `draft = true` → change to `draft = false` when you want it public
   - `tags` — a few keywords
   - `summary` — one sentence (shows on the homepage)
4. Write below the `+++`. It's plain Markdown. For R code:

````
```r
library(tidyverse)
mtcars |> filter(mpg > 25)
```
````

   That gives you colored syntax and a copy button automatically.
5. `git add . && git commit -m "new post: ..." && git push`. Done.

**Tip:** a post can sit at `draft = true` as long as you want. It won't appear on the live site until you flip it to `false`. Great for half-finished ideas.

---

## LEVEL 3 — Preview locally before publishing (optional)

Nice once you're posting regularly, totally skippable at first. This lets you see changes on your own computer instantly without pushing.

**Install Hugo (once):**

- **Mac:** `brew install hugo`
- **Windows:** `winget install Hugo.Hugo.Extended`

**Preview:** in this folder, run:

```bash
hugo server -D
```

Then open the link it prints (usually `http://localhost:1313/`). The `-D` shows drafts too. Edits appear live as you save. Press `Ctrl+C` to stop.

---

## A note for the days it's hard

You set this up to **learn in public**, and the bar for that is genuinely low. A 150-word post that says "here's one thing that confused me this week and how I worked it out" is a real, valuable post. You do not owe anyone a tutorial.

Consistency beats intensity, and *something small* beats *nothing perfect*. The template is right there. Future you will be glad past you wrote it down.

---

## Cheat sheet

| I want to… | Do this |
|---|---|
| Publish any change | `git add . && git commit -m "..." && git push` |
| Write a post | copy `_TEMPLATE-new-post.md`, edit, set `draft = false` |
| Change my title/links | edit `hugo.toml` (look for `# EDIT`) |
| Rewrite my About | edit `content/about.md` |
| Hide a post for now | set `draft = true` in its top section |
| Preview locally | `hugo server -D` |
| See if a push worked | repo → **Actions** tab (green = live) |
