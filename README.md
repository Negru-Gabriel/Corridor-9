# Corridor 9 – GitHub Pages Deployment

## Exact file list to upload to GitHub

Upload **every file and folder** listed below, keeping the exact same names and structure:

```
.nojekyll                          ← required — upload this too (prevents Jekyll)
index.html                         ← main game page (served at your GitHub Pages URL)
assets/
    index-BMB0-n4m.js              ← game engine (Three.js + all game logic)
    index-CTsSNjUt.css             ← game styles
blood.png
ceilling.png
wall-image.png
pic1.png
pic2.jpg
pic3.jpg
pic4.jpg
Garblit.glb
secret lab assets/
    rustywall.glb
```

> ⚠️ **Upload ALL files including .nojekyll — do not skip any.**
> Missing even one asset will cause the game to fail silently.

---

## Step-by-step: GitHub Pages setup

### 1. Create a new GitHub repository

- Go to https://github.com/new
- Name it e.g. `corridor9` (keep it short, no spaces)
- Set it to **Public**
- Do **NOT** initialise with a README (you're uploading your own files)
- Click **Create repository**

### 2. Upload all files

**Option A — GitHub web interface (easiest):**
1. On your empty repo page, click **uploading an existing file**
2. Drag and drop ALL the files and folders from this folder at once
3. Make sure the `secret lab assets/` folder is included as a folder, not just its contents
4. Commit directly to `main`

**Option B — Git command line:**
```bash
cd path/to/single_html_game
git init
git remote add origin https://github.com/YOUR_USERNAME/corridor9.git
git checkout -b main
git add .
git commit -m "Corridor 9 game files"
git push -u origin main
```

### 3. Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages** (left sidebar)
2. Under **Source**, select:
   - Branch: `main`
   - Folder: `/ (root)`
3. Click **Save**
4. Wait 1–2 minutes, then your game is live at:
   `https://YOUR_USERNAME.github.io/corridor9/`

> GitHub Pages serves `index.html` automatically from root, so that URL
> opens the game directly — no need to type `/index.html`.

---

## Embed on your website with an iframe

Paste this HTML into any page on your blogspot or website:

```html
<iframe
  src="https://YOUR_USERNAME.github.io/corridor9/"
  width="100%"
  height="620"
  style="border: none; display: block; border-radius: 6px;"
  allowfullscreen
  allow="pointer-lock *; fullscreen">
</iframe>
```

Replace `YOUR_USERNAME` with your actual GitHub username.

> **Tip:** The `allow="pointer-lock *"` attribute is required for mouse
> look to work inside an iframe. Without it, clicking inside the game
> won't lock the cursor and players can't look around.

---

## Test locally before uploading

Never open `index.html` directly (file:// won't work — browsers block
WebGL modules from the file:// protocol). Run a local server instead:

```bash
# Python 3
python3 -m http.server 8080
# Open: http://localhost:8080

# OR Node.js
npx serve .
```

---

## Credits

Game by Negru Gabriel · https://web-gam-dev.blogspot.com
Engine: Three.js · Assets: Secret Lab
