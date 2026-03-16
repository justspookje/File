# FileVault — GitHub Pages File Hosting

A single-file, zero-dependency file hosting site you can deploy to GitHub Pages in minutes.

## Setup (3 steps)

### 1. Create your repository structure

```
your-repo/
├── index.html       ← this file
├── files/           ← put your files here
│   ├── document.pdf
│   ├── image.png
│   └── archive.zip
└── README.md
```

### 2. Configure `index.html`

Open `index.html` and edit the `CONFIG` block near the bottom of the `<script>` tag:

```js
const CONFIG = {
  owner:    'your-github-username',   // ← your GitHub username
  repo:     'your-repo-name',         // ← your repository name
  branch:   'main',                   // branch to read from
  filesDir: 'files',                  // folder where your files live
  siteTitle: 'FileVault',             // browser tab title
};
```

> **Note:** If you deploy to `username.github.io/reponame/`, the `owner` and `repo`
> values are auto-detected from the URL — you may not need to edit CONFIG at all.

### 3. Enable GitHub Pages

1. Go to **Settings → Pages** in your repo
2. Set source to **Deploy from a branch**
3. Select your branch (`main`) and root `/`
4. Save — your site will be live at `https://username.github.io/repo-name/`

---

## Adding files

Just drop files into the `/files/` folder, commit, and push. They'll show up on the site automatically.

```bash
cp ~/Downloads/my-file.zip files/
git add files/my-file.zip
git commit -m "add my-file.zip"
git push
```

---

## Features

- 🔍 **Search** — live filter by filename
- ↕ **Sort** — by name, size, or file type
- ⊞ **Grid / list** toggle
- 📥 **Direct download** links (GitHub raw URLs)
- 📊 File count and total size in the header
- 🌐 Works with any public GitHub repo (no token required)
- Zero dependencies — single HTML file

---

## Notes

- Only works with **public** repositories (GitHub API for private repos requires authentication)
- GitHub API has a rate limit of 60 requests/hour for unauthenticated requests
- Maximum individual file size for GitHub is 100 MB; files over 50 MB show a warning in GitHub
