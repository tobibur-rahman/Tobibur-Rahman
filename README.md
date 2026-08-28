# Tobibur Rahman — Research Portfolio

A static, dependency-free personal research website (plain HTML/CSS/JS —
no build step, no framework). Rebuilt from an earlier Webflow version,
using the real content from that site plus your research and teaching
background, so it's ready to publish straight from GitHub.

## Preview locally

No build step needed. Either:

- Double-click `index.html` to open it in a browser, or
- From this folder, run a tiny local server so relative paths behave
  exactly like they will on GitHub Pages:

  ```
  python3 -m http.server 8000
  ```

  then visit `http://localhost:8000`.

## Publish with GitHub Pages

1. Create a new GitHub repository and push everything in this folder
   to it (keep the folder structure as-is — `index.html` and
   `assets/` need to stay at the same level).
2. On GitHub: **Settings → Pages → Source**, choose the branch
   (usually `main`) and the `/ (root)` folder, then save.
3. GitHub gives you a URL like
   `https://YOUR-USERNAME.github.io/YOUR-REPO/`. It can take a minute
   or two to go live the first time.
4. Once you have that URL, update it in two places:
   - `robots.txt` (the `Sitemap:` line)
   - `sitemap.xml` (every `<loc>` line)

If you'd rather use a custom domain, GitHub's own guide covers adding
a `CNAME` file: <https://docs.github.com/en/pages>.

## Before you publish — checklist

The site is fully real where it can be (your name, tagline, the four
research plots, your thesis and flood-modelling work, your tutoring
experience, your social/academic profile links). A few things only
you can fill in — each is marked with a dashed **EDIT** note right on
the page, and listed here too:

- [ ] **`about.html`** — add your university, department, and year of
      study (the bio paragraph currently leaves this out on purpose).
- [ ] **`cv.html`** — add your education details, and drop your real
      CV file at `assets/cv/Tobibur-Rahman-CV.pdf` so the download
      button works (see `assets/cv/README.md`).
- [ ] **`publications.html`** — add a link or PDF for your full LULC
      thesis report when you're ready to share it; add real
      peer-reviewed publications as they come out (an empty state is
      shown until then, linking to Scholar/ORCID instead).
- [ ] **`conferences.html`** — currently an honest "nothing yet" empty
      state. A copy-paste HTML template for each new entry is left as
      a comment in the page source.
- [ ] **Contact form** (`index.html`) — GitHub Pages can't run a
      server, so the form has nowhere to submit to yet. The easiest
      fix is a free service like [Formspree](https://formspree.io/):
      create a form there and replace
      `https://formspree.io/f/your-form-id` in `index.html` with the
      real endpoint it gives you. Until then, the form shows a
      friendly message instead of pretending to send.
- [ ] **`robots.txt`** and **`sitemap.xml`** — swap in your real
      GitHub Pages URL (see step 4 above).

None of these block publishing — the site works and looks complete
without them. They're just the spots with placeholder content instead
of your specifics.

## Structure

```
index.html            Home
about.html             About
publications.html      Research projects, thesis, applied work
conferences.html       Talks / posters (empty state for now)
experience.html        Research + teaching experience timeline
network.html           Academic profiles
cv.html                 CV summary + PDF download
404.html                GitHub Pages custom 404
assets/
  css/style.css         All styling (one file, custom properties at the top)
  js/main.js            Mobile nav, scroll reveal, footer year, form guard
  img/                  Logo, favicon, and the four research plot images
  cv/                   Put your CV PDF here
robots.txt
sitemap.xml
```

## Notes on the design

- Type: **STIX Two Text** (headings — the serif used in a lot of
  scientific publishing), **IBM Plex Sans** (body), **IBM Plex Mono**
  (labels/eyebrows). Loaded from Google Fonts via the `<link>` tags in
  each page's `<head>`.
- The wavy line under the hero is a real sech² soliton profile
  (periodic soliton), not a decorative squiggle — generated to match
  your actual research subject.
- Colors and spacing are defined once as CSS custom properties at the
  top of `assets/css/style.css` — change a value there and it updates
  everywhere.
- Motion respects `prefers-reduced-motion`, and content stays fully
  visible even if JavaScript doesn't load (the fade-in effect is a
  progressive enhancement, not a requirement).

## Updating content later

There's no CMS or build step by design — each page is plain HTML, so
editing is just opening the file and changing the text. The header,
footer, and overall structure are duplicated across pages (normal for
a small static site); if you rename a nav item or add a page, update
the `<nav class="site-nav">` block in every HTML file to match.
