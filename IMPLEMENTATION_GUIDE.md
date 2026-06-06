# 🚀 Johnthan's GitHub Profile — Complete Implementation Guide

> **Setup time: ~15 minutes** · Everything is copy-paste-ready.

---

## 📁 File Structure

After following this guide, your repository layout will look like this:

```
johnthan/                         ← Your special profile repo (username = repo name)
├── README.md                     ← Main profile page (the centerpiece)
├── metrics/                      ← Auto-generated SVG stats (created by Actions)
│   ├── core.svg
│   ├── calendar.svg
│   ├── achievements.svg
│   └── prs.svg
└── .github/
    └── workflows/
        ├── update-activity.yml   ← Recent activity feed (every 6 hours)
        ├── update-stats.yml      ← Metrics SVGs (daily)
        ├── update-pins.yml       ← Featured project rotation (weekly)
        └── update-prs.yml        ← PR tracker (every 4 hours)
```

---

## STEP 1 — Create the Special Profile Repository

GitHub renders a `README.md` from a repo named **exactly your username** as your public profile.

1. Go to **https://github.com/new**
2. Set **Repository name** to: `johnthan` (must match your GitHub username exactly)
3. Set visibility to **Public**
4. Do **not** initialize with a README (you'll add your own)
5. Click **Create repository**

---

## STEP 2 — Copy the Files

### Option A — Git CLI (fastest)

```bash
# Clone your new empty profile repo
git clone https://github.com/johnthan/johnthan.git
cd johnthan

# Copy all provided files into this directory
# (README.md + .github/workflows/*.yml + metrics/ placeholder)

# Create the metrics directory (Actions will populate it)
mkdir -p metrics
touch metrics/.gitkeep

# Commit everything
git add .
git commit -m "🎉 Initial profile setup"
git push origin main
```

### Option B — GitHub Web UI

1. In your new repo, click **"uploading an existing file"**
2. Drag and drop `README.md` → commit
3. Navigate to `.github/workflows/` using the **"Create new file"** button and type the path: `.github/workflows/update-activity.yml`
4. Paste each workflow file's content → commit
5. Repeat for all 4 workflow files

---

## STEP 3 — Create a Personal Access Token (PAT)

The `METRICS_TOKEN` is needed by the `update-stats.yml` workflow (lowlighter/metrics).
The built-in `GITHUB_TOKEN` handles the other 3 workflows automatically.

### Create the token:

1. Go to **GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)**
   Direct link: https://github.com/settings/tokens/new
2. Name: `METRICS_TOKEN`
3. Expiration: **No expiration** (or 1 year — you'll get an email reminder)
4. Select these scopes:
   - ✅ `repo` (full control of private repositories)
   - ✅ `read:user`
   - ✅ `read:org`
5. Click **Generate token**
6. **Copy the token immediately** — you won't see it again

### Add it as a repository secret:

1. Go to your profile repo: `https://github.com/johnthan/johnthan`
2. Click **Settings → Secrets and variables → Actions**
3. Click **New repository secret**
4. Name: `METRICS_TOKEN`
5. Value: *paste your token*
6. Click **Add secret**

> **Note:** `GITHUB_TOKEN` is automatic — GitHub injects it into every workflow.
> You do NOT need to create it manually.

---

## STEP 4 — Personalize the README

Open `README.md` and update these sections:

### 🔧 Replace placeholder values

| Find | Replace with |
|------|-------------|
| `johnthan` (username in URLs) | Your actual GitHub username |
| `johnthan@example.com` | Your real email |
| `johnthan.dev` | Your portfolio URL |
| `johnthan` (LinkedIn/Twitter) | Your actual handles |
| `your-top-repo-1` | An actual repo name you want featured |
| `your-top-repo-2` | Another actual repo name |

### 🎨 Change the color accent

The profile uses purple `#7C3AED` throughout. To change it, find-replace `7C3AED` with any hex color:

```
7C3AED → 0EA5E9  (sky blue)
7C3AED → F97316  (orange)
7C3AED → 10B981  (emerald green)
7C3AED → EC4899  (pink)
```

### 🧑‍💻 Update the `about` code block

Edit the TypeScript object in the "About Me" section to reflect your actual:
- Role/title
- Location
- Current focus areas
- Tech stack preferences
- Contact/links

### 📌 Add the PR Tracker Section (optional)

The `update-prs.yml` workflow looks for these HTML comment markers in `README.md`.
Add this block wherever you want the PR table to appear:

```markdown
## 🔀 Open Pull Requests

<!--PR_TRACKER:start-->
> 🔄 PR tracker auto-updates every 4 hours via GitHub Actions.
<!--PR_TRACKER:end-->
```

---

## STEP 5 — Run the Workflows Manually (First-Time Test)

After pushing all files:

1. Go to **Actions** tab in your repo: `https://github.com/johnthan/johnthan/actions`
2. You'll see all 4 workflows listed. Run each one manually to verify:
   - Click the workflow name
   - Click **"Run workflow"** → **"Run workflow"** (green button)
3. Watch the logs — green checkmarks = working correctly ✅

**Expected first-run behaviour:**
- `update-activity.yml` → Populates the Recent Activity section
- `update-stats.yml` → Creates `metrics/core.svg`, `calendar.svg`, etc. in your repo
- `update-pins.yml` → Replaces the placeholder repo cards with your actual top repos
- `update-prs.yml` → Fills the PR table (if you added the markers)

---

## STEP 6 — Add Metrics to the README (After First Run)

After `update-stats.yml` runs for the first time and commits the SVG files, add them
to your README by inserting this block in the **GitHub Analytics** section:

```markdown
<!-- Generated by update-stats.yml — auto-refreshes daily -->
<div align="center">
  <img src="metrics/core.svg" alt="Core Metrics"/>
  <img src="metrics/calendar.svg" alt="Contribution Calendar"/>
  <img src="metrics/achievements.svg" alt="Achievements"/>
</div>
```

> The stats cards from `github-readme-stats.vercel.app` work immediately (no setup needed).
> The `metrics/*.svg` files are the richer, self-hosted alternative.

---

## Automation Schedule Summary

| Workflow | Trigger | What updates |
|----------|---------|-------------|
| `update-activity.yml` | Every 6 hours + every push | Recent activity feed (last 5 events) |
| `update-stats.yml` | Daily at midnight UTC | Metrics SVGs (languages, habits, achievements) |
| `update-pins.yml` | Every Monday noon UTC | Featured projects rotation |
| `update-prs.yml` | Every 4 hours | PR status table |

---

## Troubleshooting

### ❌ Workflow fails with "Permission denied"
→ Go to repo **Settings → Actions → General → Workflow permissions**
→ Select **"Read and write permissions"** → Save

### ❌ `update-stats.yml` fails with "token invalid"
→ Your `METRICS_TOKEN` may have expired or have wrong scopes
→ Regenerate it (Step 3) and update the secret

### ❌ Stats cards show "Card not available"
→ `github-readme-stats` is a free third-party service that may be rate-limited
→ Fallback: self-host it (see https://github.com/anuraghazra/github-readme-stats#deploy-on-your-own)
→ Or use the `metrics/*.svg` approach instead (fully self-contained)

### ❌ Activity feed not updating
→ Make sure the `<!--RECENT_ACTIVITY:start-->` and `<!--RECENT_ACTIVITY:end-->` comment markers
  are present in your README.md — the action looks for these exact strings

### ❌ Featured repos not rotating
→ Repos need a **description** set — edit each repo and add one
→ Forks and archived repos are excluded by design

### 💡 Rate limit issues with GitHub API
→ The workflows use `${{ secrets.GITHUB_TOKEN }}` which has 5,000 requests/hour
→ All 4 workflows combined use fewer than 50 requests per run — no risk of hitting limits

---

## Optional Enhancements

### 🎵 Add a Spotify Now Playing card
```markdown
[![Spotify](https://novatorem.vercel.app/api/spotify)](https://open.spotify.com/user/YOUR_SPOTIFY_ID)
```
Follow setup at: https://github.com/novatorem/novatorem

### 📝 Add latest blog posts (RSS feed)
Add a `<!--BLOG_POSTS:start--><!--BLOG_POSTS:end-->` block and use:
```yaml
- uses: gautamkrishnar/blog-post-workflow@master
  with:
    feed_list: "https://dev.to/feed/johnthan"
```

### 🌐 Add a visitor map
```markdown
![Visitor Map](https://profile-counter.glitch.me/johnthan/count.svg)
```

### 🐍 Add the contribution snake animation

Add to `update-stats.yml`:
```yaml
- uses: Platane/snk@v3
  with:
    github_user_name: J0HNTHAN
    outputs: |
      metrics/snake.gif
      metrics/snake-dark.gif?palette=github-dark
```
Then embed in README: `![Snake](metrics/snake-dark.gif)`

---

## Services Used (All Free)

| Service | Purpose | Limits |
|---------|---------|--------|
| [github-readme-stats](https://github.com/anuraghazra/github-readme-stats) | Stats cards | Free, shared instance |
| [readme-typing-svg](https://github.com/DenverCoder1/readme-typing-svg) | Typing animation | Free, unlimited |
| [github-readme-streak-stats](https://github.com/DenverCoder1/github-readme-streak-stats) | Streak counter | Free |
| [capsule-render](https://github.com/kyechan99/capsule-render) | Header/footer banners | Free |
| [github-readme-activity-graph](https://github.com/Ashutosh00710/github-readme-activity-graph) | Contribution graph | Free |
| [github-profile-trophy](https://github.com/ryo-ma/github-profile-trophy) | Achievement trophies | Free |
| [lowlighter/metrics](https://github.com/lowlighter/metrics) | Rich SVG metrics | Self-hosted via Actions |
| [komarev/ghpvc](https://komarev.com/ghpvc/) | Profile view counter | Free |

---

*Generated for Johnthan · Setup time ~15 min · Zero ongoing maintenance required*
