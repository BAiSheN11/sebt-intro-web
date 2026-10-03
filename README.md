# SEBT.mfu — Professor Introduction Webapp

A single-page introduction website for **SEBT.mfu**, the browser-based Star Excursion
Balance Test (SEBT) clinical analysis system built at Mae Fah Luang University.
It explains the clinical background, how the system works, embeds your recorded
demo video, and links to the live app — ready to host on **Vercel for free**.
The site is bilingual: **English and Thai**, switchable from the navigation bar.

---

## Project structure

```
sebt-intro-web/
├── index.html          ← the whole website (single self-contained file)
├── assets/
│   ├── demo-recording.mp4   ← your final demo video (44 s, 1920×1080)
│   ├── demo-poster.jpg      ← video poster frame
│   └── hero-shot.jpg        ← screenshot used in the hero section
└── README.md
```

No build step, no dependencies. `index.html` is the entry point.

---

## Language switch (EN / ไทย)

- A **EN | ไทย** toggle sits in the top navigation bar. The choice is remembered
  (localStorage), and the page also auto-detects a Thai browser.
- You can force a language with a URL parameter, e.g. `?lang=th` or `?lang=en`.
- Thai text uses Noto Sans/Serif Thai with system fallbacks — no tofu, no extra files.

---

## Deploy on Vercel (free) — 3 ways

### Way 1 · Vercel CLI (fastest, no GitHub needed)

1. Install Node.js from https://nodejs.org (LTS version).
2. Open a terminal in this folder (`sebt-intro-web`):
   ```bash
   npm i -g vercel
   vercel
   ```
3. Follow the prompts (log in with GitHub/Google if asked). It auto-detects a
   static site — press Enter for the defaults.
4. When finished you get a URL like `https://sebt-intro-web-xxxx.vercel.app`.
5. To update later, run `vercel --prod` from the same folder.

### Way 2 · Drag and drop on vercel.com (no terminal)

1. Go to https://vercel.com and sign in (free account).
2. Click **Add New → Project**.
3. Instead of importing a repo, drag the whole `sebt-intro-web` folder into the
   import area, or use **Upload Project**.
4. Vercel detects "Other / static" — click **Deploy**. Done.

### Way 3 · GitHub + Vercel

1. Push this folder to a GitHub repository.
2. In Vercel: **Add New → Project → Import** the repo.
3. Framework preset: **Other** (static). Click **Deploy**.

> The live URL you send to the professor is whatever Vercel gives you
> (e.g. `https://your-project.vercel.app`).

---

## Using your own demo video

The page plays `assets/demo-recording.mp4`. To use a different recording:

1. Put your video file inside `assets/` (keep the same filename, or update the
   `<video src>` path in `index.html`).
2. Update the caption under the video if the length changes.
3. Re-deploy (`vercel --prod`).

The current video is ~5.8 MB (44 s, 1920×1080), well within Vercel's free limits.

---

## Technical notes

- **No tracking, no analytics, no backend** — the page is purely static.
- Fonts load from a self-hosted CDN mirror; the page degrades gracefully to
  system fonts if offline.
- Fully responsive: desktop, laptop and mobile.
- The demo video is referenced with a relative path, so everything works when
  the folder is deployed as-is.
