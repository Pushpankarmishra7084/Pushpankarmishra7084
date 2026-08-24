# Setup & Verification Notes

## 1. Things I found that need YOUR confirmation before this goes live

I inspected your live GitHub profile and repo before writing anything. A few things didn't
match cleanly, so I left them as placeholders instead of guessing:

- **Two different LinkedIn URLs are currently public on your account:**
  - In your profile bio: `linkedin.com/in/pushpankar-mishra-959583261`
  - In your old README: `linkedin.com/in/pushpankarmishra`
  These may point to the same account with different vanity/legacy slugs, or one may be
  outdated. The new README currently uses the second one — swap in whichever is correct
  everywhere you see a LinkedIn link.

- **`https://socialweb-cnfj.onrender.com`** is listed as a link on your profile bio, with no
  label. I didn't know if this is a personal portfolio site, a live demo of a project, or
  something still in progress — so I commented out a "Portfolio" badge for it in the README
  rather than assume. Uncomment it (and re-label if it's actually a project) once confirmed.

- **Your live bio currently reads:** *"Aspiring software engineer currently in my third year
  at Technocrats Institute of Technology, Bhopal. Skilled-Java, HTML, CSS, JavaScript."* This
  is what recruiters see at the top of your GitHub profile page (separate from the README).
  It doesn't mention React/Node/MERN at all. If MERN/Next.js is genuinely your current focus,
  consider updating that bio field too (Settings → Profile) so it's consistent with the README.

- **Featured Projects:** your account currently has 7 repositories. Only `Tic-Tac-Toe-Game` is
  an original project with enough of a description to feature credibly. `netgame`, `hello`,
  and `test` don't have descriptions that convey what they are, and `free-api.github.io` is a
  fork, not your own work. I did not invent project names, descriptions, or live demo links —
  I left a template comment in the README (`## 05 Featured Projects`) for you to fill in with
  1–2 more real projects. This is the single biggest thing worth spending time on: a recruiter
  reads this section closest.

- **No LeetCode/certifications/company names were used anywhere** — none were verifiable from
  your profile, so per your instructions I left them out entirely rather than fabricate them.

## 2. What's genuinely interactive vs. visual-only

GitHub READMEs cannot execute JavaScript, run React, or load a Three.js scene — so nothing
here is "3D" in the literal WebGL sense. Here's what's real vs. what's a static/animated image:

| Element | What it actually is |
|---|---|
| Hero banner (`assets/hero.svg`) | Static SVG with embedded CSS/SMIL animation (typing effect, glowing cursor, drifting glow orbs). Renders identically for every visitor — not interactive, but genuinely animated. |
| Engineering Pipeline diagram (`assets/constellation.svg`) | Same technique — animated SVG, a pulse travels down the pipeline on loop. Visual-only. |
| GitHub stats / top languages images | **Real, live-computed data**, refreshed by a third-party service (github-readme-stats) each time the image is requested — not static numbers I typed in, but also not hosted by you, so it depends on that service staying up. |
| 3D contribution graph | **Genuinely automated**, not faked: a GitHub Action (below) regenerates the SVG daily from your real contribution data using `yoshi389111/github-profile-3d-contrib`. |
| Shields.io tech badges | Static images, cosmetic only. |

If you want true interactive 3D, that has to live outside the README (e.g. a Three.js /
React Three Fiber site on GitHub Pages or Vercel), with the README linking to it. I didn't
build that since you don't have a confirmed portfolio URL yet — happy to build one once you
decide where it'd be hosted.

## 3. Folder structure

Place these files at the **root of your `Pushpankarmishra7084/Pushpankarmishra7084` repo**
(this is the special repo whose README becomes your profile page):

```
Pushpankarmishra7084/
├── README.md
├── NOTES.md                              (optional — for your own reference, not shown on profile)
├── assets/
│   ├── hero.svg
│   └── constellation.svg
└── .github/
    └── workflows/
        └── profile-3d-contrib.yml
```

## 4. Exact setup steps

1. In your repo, replace the existing `README.md` with the new one.
2. Create an `assets/` folder and add `hero.svg` and `constellation.svg`.
3. Create `.github/workflows/profile-3d-contrib.yml` with the workflow provided — this is
   what generates `profile-3d-contrib/profile-night-rainbow.svg`, which the README's
   Contributions section references. **The image won't exist until this workflow runs once**,
   so after committing it, go to the **Actions** tab → select the workflow → **Run workflow**
   manually the first time (it'll run automatically every day after that).
4. Fix the LinkedIn URL and the portfolio badge per section 1 above.
5. Fill in your 2–3 real projects in the `## 05 Featured Projects` section.
6. Commit and push to the `main` branch.

## 5. Test checklist before you consider it done

- [ ] View the README on github.com (not just in an editor preview) — SVG animation and stats
      widgets only render correctly there.
- [ ] Confirm the hero and pipeline SVGs load (not broken image icons) — if they're broken,
      check the `assets/` path matches exactly.
- [ ] Run the 3D contribution graph workflow manually once, confirm the SVG commits
      successfully, and confirm it renders in the README afterward.
- [ ] Click every link (GitHub, LinkedIn, email, project repo) and confirm it goes where it
      should.
- [ ] View the profile page on a phone-width browser or GitHub mobile app — confirm nothing
      overflows or gets cut off.
- [ ] Wait a minute and hard-refresh — github-readme-stats can take a moment to render on
      first load.
- [ ] Re-read the About/Currently Building sections and confirm every line is still true.
