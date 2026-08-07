# Puzzle Hunt Site (Home -> Step 2 -> Base Case)

Plain static HTML/CSS/JS, ready to deploy on Vercel as-is.

## Pages
- `/` -> redirects to `/step1`
- `/step1` -> Home screen. Clue: **ADVANCE**
- `/step2` -> Clue: **RECURSION**. The answer is the site's own domain/URL
  (checked dynamically against `window.location`, so it works on
  whatever domain Vercel gives you, or a custom domain, with no
  hardcoding needed). Wrong answers show "that's not recursive enough".
  Correct answers show "sometimes you have to dig deeper" and log a
  styled hint to the browser console pointing to `/pictures`.
- `/pictures` -> Shows "// base case". This is where this build ends;
  everything past this (QR code, physical pictures, Google Form, etc.)
  is out of scope for this site.

`vercel.json` has `"cleanUrls": true`, which is what makes `/step1`
serve `step1.html`, `/step2` serve `step2.html`, etc.

## Deploy on Vercel

**Option A - Vercel CLI**
```bash
npm i -g vercel
cd puzzle-site
vercel
```
Follow the prompts (accept defaults - no build step needed).

**Option B - GitHub + Vercel dashboard**
1. Push this folder to a GitHub repo.
2. Go to vercel.com -> New Project -> Import your repo.
3. Framework preset: "Other" (no build command needed).
4. Deploy.

## Testing locally
Any static server works, e.g.:
```bash
npx serve puzzle-site
```
Note: the recursion-check on `/step2` compares against whatever
domain you're viewing it on, so it'll work locally too (e.g. typing
`localhost:3000` while testing on localhost).
