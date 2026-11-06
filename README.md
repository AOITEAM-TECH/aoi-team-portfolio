# Bharat FIH — SPI & AOI Team Portfolio

An onboarding site for the SPI & AOI team inside Bharat FIH's SMT (Surface Mount
Technology) process. Built so a new team member can open one link and understand
the team, the process, and their station — no shift handover required.

## What's inside

```
bharatfih-portfolio/
├── index.html          → login page (select your name, sign in)
├── portfolio.html       → the main portfolio (team, process, training)
├── css/style.css        → all styling
├── js/members.js         → the team list + usernames/passwords (edit this to update anyone)
├── js/auth.js            → login logic
├── js/main.js             → portfolio page logic
├── ppt/                  → put your training PPT exports here (see below)
└── README.md
```

## Login credentials (edit anytime in `js/members.js`)

| Name          | Username      | Password     |
|---------------|---------------|--------------|
| Saravanan V   | saravanan.v   | SMTaoi@01    |
| Sarathkumar   | sarathkumar   | SMTaoi@02    |
| Kavimani      | kavimani      | SMTaoi@03    |
| Boopathy      | boopathy      | SMTaoi@04    |
| Saravanan S   | saravanan.s   | SMTaoi@05    |
| Prasanth      | prasanth      | SMTaoi@06    |
| Periya Sami   | periyasami    | SMTaoi@07    |

### ⚠️ Important — what this login actually does

This is a **simple, client-side login**, as requested. It's great for:
- giving each person their own "welcome back" personalization,
- a light gate that keeps casual visitors out.

It is **not real security**. Because this site is a static page (and will be hosted
on GitHub Pages), anyone who looks at `js/members.js` in the browser or the GitHub
repo can see every username and password in plain text. Don't put anything
genuinely confidential behind this login. If you ever need real access control
(e.g. this becomes customer-facing or holds sensitive data), that needs a backend
login service — happy to help set that up separately if it comes to that.

## Adding your team roles / bios

Open `js/members.js` — each person has a `role` and `blurb` field. I drafted
starter roles (Team Lead, SPI Operator, AOI Stage 1/2 Inspector) based on the
stations you described — edit these to match reality exactly.

## Adding your PPTs and images (Training gallery)

The new **Training page** (`training.html`) is a dedicated gallery, in this exact order:

1. LASER
2. SPP
3. SPI
4. NXT – Component Mounting
5. PRE AOI
6. POST AOI
7. VI MATERIAL
8. Holly AOI Training Guideline RGB
9. Reference Image 1
10. Reference Image 2

It's driven entirely by `js/training-data.js`. Each entry lists a `file` path —
the gallery checks that path automatically and flips the card from
**"Awaiting upload"** to a working link the moment the real file exists there.
No other code changes needed.

**To add a PPT:**
1. Export it as a PDF (PowerPoint → File → Export → Create PDF/XPS).
2. Rename it to match the `file` path in `js/training-data.js` — e.g. the
   LASER entry expects `ppt/laser.pdf`. Rename the export to `laser.pdf`.
3. Drop it into the `ppt/` folder and push to GitHub. The card updates itself.

**To add an image:**
1. Rename your two images to `gallery-1.jpg` and `gallery-2.jpg` (or edit the
   `file` paths in `js/training-data.js` to match your actual filenames).
2. Drop them into the `images/` folder and push.
3. Want real titles instead of "Reference Image 1/2"? Edit the `title` field
   for those two entries in `js/training-data.js`.

If a PPT has a different file type in mind (e.g. you'd rather keep native
`.pptx` files instead of exporting to PDF), just change the `file` path's
extension to match — GitHub Pages will serve any file type, though PDFs open
directly in the browser while `.pptx` will prompt a download.

## Internal FAQ chatbot

A small chat bubble (bottom-right, on the portfolio and training pages) answers
built-in questions about SMT, SPI, AOI, the team, and where to find things.
It's fully client-side — no API, no cost, works on GitHub Pages as-is.

To add or correct an answer, open `js/chatbot.js` and edit the `FAQS` array —
each entry is a list of trigger keywords plus the answer to give. It's a
keyword matcher, not real AI, so it only knows what's written there. If you
ever want genuinely open-ended AI answers, that requires a small backend to
hold an API key safely — let me know if you want to go that route later.

## Hosting on GitHub Pages

1. **Create a repo** — on GitHub, click **New repository**, name it something like
   `bharatfih-aoi-team`, keep it **Public** (GitHub Pages on a free plan needs a
   public repo unless you're on GitHub Team/Enterprise).
2. **Upload the files** — either:
   - drag-and-drop all files/folders in this project into the repo via the GitHub
     web UI ("Add file" → "Upload files"), or
   - use git from your machine:
     ```bash
     cd bharatfih-portfolio
     git init
     git add .
     git commit -m "Initial team portfolio"
     git branch -M main
     git remote add origin https://github.com/<your-username>/bharatfih-aoi-team.git
     git push -u origin main
     ```
3. **Turn on Pages** — in the repo, go to **Settings → Pages**. Under
   "Build and deployment", set **Source** to `Deploy from a branch`, branch
   `main`, folder `/ (root)`. Save.
4. **Get your link** — after a minute or two, GitHub shows your live URL, usually:
   `https://<your-username>.github.io/bharatfih-aoi-team/`
   That's the link the whole team can bookmark.
5. **Updating later** — any time you edit a file and push to `main`, the live
   site updates automatically within a minute or two.

## What's next

This is the first-level version per your brief. Once you're ready, send over:
- the PPT files,
- any corrections to member roles/bios,
- your actual logo/colors if you have brand guidelines beyond what I designed,
- anything else you want added (photos, shift schedules, defect galleries, etc.)

and I'll enhance it from here.
