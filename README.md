# 📸 Free Photo Portfolio — GitHub Pages

A completely free, self-hosted photography portfolio. No subscriptions, no backend, no database. Your photos live in your GitHub repository and the site runs on GitHub Pages.

---

## What it is

A single HTML file that turns a GitHub repository into a fully functional photography portfolio. Upload photos through the built-in admin panel, organize them into collections, add captions and descriptions, and share individual photos or entire collections — all without paying for hosting or a CMS.

**Cost: $0.** GitHub Pages is free. Storage is free up to 1GB (roughly 2,000 photos at the compressed size this tool uses). Your only potential cost is a custom domain if you want one (~$10–15/year).

---

## Features

- **Collections** — group photos into named collections with optional descriptions
- **Focused carousel** on the homepage — active photo scales up, neighbours dim
- **Detail view** — full vertical feed when you open a collection, with captions
- **Lightbox** — click any photo to view full screen, navigate with arrows or keyboard
- **Share buttons** — share collections or individual photos to Instagram, WhatsApp, X, Facebook, Email, or copy link
- **Cover photo picker** — choose which photo represents each collection
- **Drag to reorder** — reorder photos and collections in admin mode
- **Auto compression** — photos are resized to 2048px and compressed before upload
- **Lazy loading** — photos load as you scroll, page stays fast with large collections
- **Shareable URLs** — each collection gets a `?c=collection-name` link
- **Custom domain support** — works with any domain pointed at GitHub Pages
- **HTTPS enforced** — automatic redirect from http to https
- **Mobile friendly** — responsive layout, touch swipe on carousel
- **No tracking, no ads, no third-party services** except Google Fonts

---

## Setup (5 minutes)

### 1. Create a GitHub repository

Go to [github.com](https://github.com) and create a new repository. Make it **public**.

> If you name it `yourusername.github.io` it will be available at `https://yourusername.github.io` automatically.

### 2. Enable GitHub Pages

**Settings → Pages → Source → Deploy from branch → main → / (root) → Save**

### 3. Add the files

Upload these to the root of your repository:

```
index.html        ← the portfolio (this file)
settings.json     ← your configuration
.nojekyll         ← empty file, required so GitHub Pages serves _data.json
```

`_data.json` is created automatically the first time you save anything in the admin panel.

Create `settings.json`:

```json
{
  "user":   "your-github-username",
  "repo":   "your-repository-name",
  "branch": "main",
  "title":  "Your Name"
}
```

### 4. Create a GitHub Personal Access Token

1. **GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)**
2. Click **Generate new token (classic)**
3. Check the **repo** scope
4. Copy the token (starts with `ghp_`)

> The token is only stored in your browser's `sessionStorage` and cleared when you close the tab.

### 5. Log in and start uploading

Open your site, click **Login**, paste your token, click **Connect**. The admin panel opens. Create a collection, switch to Upload, drag your photos in.

---

## Custom domain

1. Buy a domain from any registrar
2. In DNS, add an `A` record pointing to `185.199.108.153` (or a `CNAME` to `yourusername.github.io`)
3. In your repo: **Settings → Pages → Custom domain** → enter your domain → Save
4. Check **Enforce HTTPS** once the certificate is issued (a few minutes)

---

## Storage limits

| Limit | Photos (at ~500KB each) |
|---|---|
| GitHub soft limit — 1GB | ~2,000 photos |
| GitHub hard limit — 5GB | ~10,000 photos |

Photos are automatically compressed to 2048px / 88% JPEG quality before upload.

---

## File structure

```
/
├── index.html                  ← the entire portfolio (one file)
├── settings.json               ← GitHub user/repo/branch/title
├── _data.json                  ← collections, photos, captions (auto-managed)
├── .nojekyll                   ← tells GitHub Pages to skip Jekyll
└── photos/
    └── collection-slug/
        ├── photo-id.jpg
        └── ...
```

---

## Admin reference

| Action | How |
|---|---|
| Login | Click **Login** in the header, paste your GitHub token |
| Create collection | Admin panel → Collections → type name → Create |
| Upload photos | Admin panel → Upload → select collection → drag & drop |
| Reorder photos | Open collection → drag the handle on any photo |
| Reorder collections | Admin panel → Collections → drag any row |
| Set cover photo | In carousel or detail view, click ★ on any photo |
| Add caption | Open collection → edit the caption field below any photo |
| Add description | Open collection → edit the description at the top |
| Delete photo | Open collection → Delete button on any photo |
| Delete collection | Admin panel → Collections → Delete on any row |
| Edit contact/footer | Scroll to footer in admin mode — fields appear inline |
| Sync from repo | Click **Sync** in the header to re-scan photo folders |
| Logout | Admin panel → Collections → Logout |

---

## Tech stack

| | |
|---|---|
| Hosting | GitHub Pages (free) |
| Storage | GitHub repository (free) |
| Frontend | Single HTML file — vanilla JS, no frameworks, no build step |
| Fonts | Inter + Instrument Serif via Google Fonts |
| Images | Served from `raw.githubusercontent.com` |
| Data | `_data.json` managed via GitHub Contents API |

---

## License

Free to use for personal and commercial portfolios. No attribution required.
