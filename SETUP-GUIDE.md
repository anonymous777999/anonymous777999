# 🚀 RedVortex GitHub Profile — Complete Setup Guide

> ⏱ **Estimated time:** ~45 minutes  
> 📋 **Follow these steps in order.** Test after each phase before moving to the next.

---

## Phase 0 — Create Profile Repo

- [ ] Go to [github.com/new](https://github.com/new)
- [ ] **Repository name:** `anonymous777999` (exactly your username)
- [ ] Set to **Public**
- [ ] Tick **Add a README file**
- [ ] Click **Create repository**

### Upload Banner SVGs
- [ ] Run the **Master Prompt** Python pipeline with your photo to generate `dark.svg` and `light.svg`
- [ ] Upload both files to your repo root: **Add file → Upload files**
- [ ] Commit to `main`

---

## Phase 1 — Banner in README

- [ ] Copy the `<picture>` block from the README.md I generated (already there!)
- [ ] Or manually add it — replace `USERNAME` with `anonymous777999`
- [ ] **Test:** Switch your GitHub theme (avatar → Settings → Appearance → Dark/Light) and reload your profile. Both banner versions should appear.

---

## Phase 2 — Self-Host Stats Cards

### Step 1: Create GitHub Token
- [ ] Go to [github.com/settings/tokens](https://github.com/settings/tokens)
- [ ] Click **Tokens (classic)** → **Generate new token (classic)**
- [ ] **Note:** `readme-stats`
- [ ] **Expiration:** No expiration
- [ ] **Scopes:** Tick `repo` (entire group)
- [ ] **Generate → COPY THE TOKEN NOW** (GitHub shows it once)
- [ ] ⚠️ Never paste this token in chats, public repos, or anywhere except Vercel

### Step 2: Fork & Deploy
- [ ] Fork [github.com/anuraghazra/github-readme-stats](https://github.com/anuraghazra/github-readme-stats)
- [ ] Go to [vercel.com](https://vercel.com) → Sign up with GitHub → **Hobby** (free) plan
- [ ] **Add New → Project → Import your fork**
- [ ] Leave all build settings as-is
- [ ] **Environment Variables:** Add `PAT_1` = your copied token
- [ ] **Deploy** → Wait ~2 minutes for confetti 🎉

### Step 3: Verify & Update README
- [ ] Copy your URL: `https://your-instance.vercel.app`
- [ ] Verify: Open `https://your-instance.vercel.app/api?username=anonymous777999&show_icons=true` — a card should render
- [ ] Open `README.md` and replace all `YOUR-INSTANCE` with your actual Vercel URL
- [ ] Commit the change

---

## Phase 3 — Contribution Snake

### Step 1: Enable Actions Permissions
- [ ] Go to your **repo** → **Settings** (repo tab, NOT account)
- [ ] Sidebar → **Actions → General**
- [ ] Scroll to **Workflow permissions**
- [ ] Select **Read and write permissions**
- [ ] Click **Save**
- [ ] URL should be: `github.com/anonymous777999/anonymous777999/settings/actions`

### Step 2: Create Workflow
- [ ] The file `.github/workflows/snake.yml` is already created in this repo!
- [ ] Copy it to your profile repo at the exact same path: `.github/workflows/snake.yml`
- [ ] Commit to `main`
- [ ] Go to **Actions** tab — the run should go green in ~1 minute
- [ ] An `output` branch will be created automatically

> ⚠️ **The colour rule that matters:** The first colour in `color_dots` is the empty cell. For the dark snake it must be a visible slate like `#2d3343` — against GitHub's `#0d1117` a near-black empty cell disappears. I've already set this correctly above.

### Step 3: Display It
- [ ] The snake `<picture>` block is already in your README.md
- [ ] **Only verify it after** the Action runs green — the `output` branch doesn't exist before then

---

## Phase 4 — Social Badges

- [ ] Badges are already in your README.md — LinkedIn, Instagram, Facebook, Medium, and Email
- [ ] Verify all URLs point to your actual profiles

> ⚠️ **LinkedIn trap:** Shields.io has a documented bug — the LinkedIn logo only renders on brand blue `#0A66C2`. On any custom colour the glyph silently vanishes. That's why LinkedIn is the only badge NOT themed to your palette. Accept brand blue or embed the logo as a base64 data-URI to theme it.

---

## ✅ Final Checklist

- [ ] Banner SVGs uploaded to repo root
- [ ] Banner renders in both dark & light mode
- [ ] Stats cards deployed on Vercel (self-hosted)
- [ ] `YOUR-INSTANCE` replaced with your Vercel URL
- [ ] Snake workflow committed & Action ran green
- [ ] Snake renders on profile
- [ ] All social badge links work
- [ ] Profile looks good at ~900px width (GitHub's README width)

---

## 🔧 Troubleshooting

| Symptom | Cause |
|---------|-------|
| Card shows "API rate limit exceeded" | Using public instance — self-host on Vercel |
| Snake image is broken | `output` branch doesn't exist yet — run the Action |
| Snake grid invisible in dark mode | Empty-cell colour too close to `#0d1117` |
| LinkedIn badge has no logo | Shields.io bug — needs `#0A66C2` or base64 |
| "I changed it but nothing happened" | CDN cache — open `?v=999` URL, Ctrl+U, search hex |
| Dark assets not showing | You're in light mode — check theme |
| Action fails, "maxDuration" | Vercel free-tier limit — set to 10 in `vercel.json` |

---

## 📌 Good to Know

- **Scheduled Actions pause** after ~60 days of repo inactivity. The snake freezes until you push or click "Enable workflow".
- **Stats totals** won't match GitHub's exactly. Different date windows + cache lag = normal gap.
- **Top-languages** reflects code volume, not skill. A template's CSS can dominate. Exclude repos if needed.
- **Banner SVGs** can't contain working links — GitHub strips them. Clickable links must be badges in the README.
