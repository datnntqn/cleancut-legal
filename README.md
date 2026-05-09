# cleancut-legal

Static site for CleanCut: About + Privacy Policy + Terms of Use + Support. Hosted on GitHub Pages.

## Files

| File           | Purpose                                                                               |
| -------------- | ------------------------------------------------------------------------------------- |
| `index.html`   | About / landing page                                                                  |
| `privacy.html` | Privacy Policy (URL goes in App Store Connect → App Information → Privacy Policy URL) |
| `terms.html`   | Terms of Use                                                                          |
| `support.html` | Support page (URL goes in App Store Connect → App Information → Support URL)          |
| `style.css`    | Shared styles                                                                         |
| `.nojekyll`    | Tells GitHub Pages to serve files as-is, no Jekyll build                              |

## Publish to GitHub Pages

You'll do this once. After that, every `git push` updates the live site within ~1 minute.

### Step 1 — Initialize the local repo (one time)

```bash
cd /Users/datnnt/Desktop/DatNNT/App/cleancut-legal
git init
git add .
git commit -m "Initial commit: About, Privacy, Terms, Support"
git branch -M main
```

### Step 2 — Create the GitHub repo (pick ONE of the two paths below)

#### Path A — GitHub web UI (no CLI needed)

1. Go to <https://github.com/new>
2. **Repository name:** `cleancut-legal`
3. **Visibility:** Public (required for free GitHub Pages)
4. **Do NOT** check "Add a README" / `.gitignore` / license — your local repo already has files.
5. Click **Create repository**.
6. Copy the SSH URL it shows (looks like `git@github.com:<your-username>/cleancut-legal.git`).
7. Back in your terminal:
   ```bash
   git remote add origin git@github.com:<your-username>/cleancut-legal.git
   git push -u origin main
   ```

#### Path B — GitHub CLI (`gh`)

```bash
# Install gh first if you don't have it:
brew install gh
gh auth login            # follow the browser prompt

# Then from inside cleancut-legal/:
gh repo create cleancut-legal --public --source=. --remote=origin --push
```

### Step 3 — Enable GitHub Pages

1. Go to <https://github.com/`<your-username>`/cleancut-legal/settings/pages>
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Under **Branch**, choose **main** and **/ (root)**, then click **Save**.
4. Wait ~30-60 seconds. The page will show a green box: `Your site is live at https://<your-username>.github.io/cleancut-legal/`.

### Step 4 — Verify the URLs work

Open these in an incognito window (proves they're truly public):

- `https://<your-username>.github.io/cleancut-legal/` ← About
- `https://<your-username>.github.io/cleancut-legal/privacy.html` ← Privacy Policy
- `https://<your-username>.github.io/cleancut-legal/terms.html` ← Terms of Use
- `https://<your-username>.github.io/cleancut-legal/support.html` ← Support

### Step 5 — Paste the URLs back into the submission plan

Open `/Users/datnnt/Desktop/DatNNT/App/SonicMerge/docs/superpowers/plans/2026-05-09-app-store-submission.md` and fill the Decision 1.2 block:

```
Privacy Policy URL: https://<your-username>.github.io/cleancut-legal/privacy.html
Terms of Use URL:   https://<your-username>.github.io/cleancut-legal/terms.html
Support URL:        https://<your-username>.github.io/cleancut-legal/support.html
```

These are the URLs you'll paste into App Store Connect in §4.2.

## Updating later

After launch, edit any `.html` file and:

```bash
git add .
git commit -m "Update <what>"
git push
```

GitHub Pages rebuilds within ~1 minute. Privacy/Terms changes don't require an app re-review (the URL stays the same).

## Local preview

```bash
cd /Users/datnnt/Desktop/DatNNT/App/cleancut-legal
python3 -m http.server 8000
# open http://localhost:8000
```

## Notes

- The "Get CleanCut on the App Store" button on `index.html` currently links to `#`. Update to your real App Store URL after launch.
- All three legal pages reference `datnnt.qn.it@gmail.com` as the support contact. Search-and-replace if this changes.
- The site uses no build step, no Jekyll, no JS. Pure HTML + one CSS file. Loads in <100ms on 4G.
