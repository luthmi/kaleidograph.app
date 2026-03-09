# Harmonic Kaleidograph Website — Setup Guide

## What You Have

- A domain through GoDaddy
- A ready-to-deploy website (the files in this folder)

## What You'll Set Up

1. A GitHub account and repository
2. GitHub Pages hosting (free)
3. Your GoDaddy domain pointing to the site

---

## Part 1: Create a GitHub Account

1. Go to **github.com** and click **Sign Up**
2. Use your email, create a username and password
3. Verify your email

---

## Part 2: Create a Repository and Upload Your Site

### 2A: Create the Repository

1. Click the **+** icon in the top-right corner of GitHub
2. Click **New repository**
3. Repository name: `kaleidograph.app` (or whatever your domain is)
4. Set it to **Public**
5. **Don't** check any of the initialization boxes (no README, no .gitignore, no license)
6. Click **Create repository**

### 2B: Upload Your Files

1. On the empty repo page, you'll see a link that says **"uploading an existing file"** — click it
2. Unzip the site folder I gave you on your computer
3. Before uploading, **edit the CNAME file** in a text editor:
   - Open `CNAME`
   - Replace `kaleidograph.app` with your actual domain (e.g., `kaleidograph.app`)
   - Save it
4. Drag ALL the files and folders from inside the site folder onto the upload area:
   - `index.html`
   - `CNAME`
   - `README.md`
   - `images/` folder (contains both logo images)
   - `screenshots/` folder
5. Under "Commit changes," type a message like `Initial site upload`
6. Make sure **"Commit directly to the main branch"** is selected
7. Click **Commit changes**

**Note:** If the `images/` folder doesn't upload via drag-and-drop (GitHub can be finicky with folders), do this instead:
1. First upload `index.html`, `CNAME`, and `README.md` and commit
2. Then click **Add file → Create new file**
3. Type `images/.gitkeep` as the filename (typing the slash creates the folder)
4. Commit it
5. Navigate into the `images/` folder on GitHub
6. Click **Add file → Upload files**
7. Upload `harmonic_kaleidograph.gif` and `hk-icon.jpg` and commit

---

## Part 3: Enable GitHub Pages

1. Go to your repository on github.com
2. Click **Settings** (tab near the top)
3. In the left sidebar, click **Pages**
4. Under **Source**, select **Deploy from a branch**
5. Under **Branch**, select **main** and **/ (root)**
6. Click **Save**

Within a couple minutes, your site will be live at:
`https://YOURUSERNAME.github.io/kaleidograph.app/`

Visit that URL and make sure everything looks right before connecting your domain.

---

## Part 4: Connect Your GoDaddy Domain

### 4A: Tell GitHub About Your Domain

1. In your repo, go to **Settings → Pages**
2. Under **Custom domain**, type your domain (e.g., `kaleidograph.app`)
3. Click **Save**
4. Check **Enforce HTTPS** (may be grayed out until DNS propagates — that's OK)

### 4B: Configure GoDaddy DNS

1. Log in to **godaddy.com**
2. Go to **My Products** → find your domain → click **DNS** (or Manage DNS)
3. You need to add/edit these records:

**For the root domain (yourdomain.com) — add these 4 A records:**

| Type | Name | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

If there are existing A records pointing to something else (like GoDaddy parking), **delete those first**, then add the four above.

**For the www subdomain — add this CNAME record:**

| Type | Name | Value |
|------|------|-------|
| CNAME | www | YOURUSERNAME.github.io |

Replace `YOURUSERNAME` with your actual GitHub username.

4. Save all changes

### 4C: Wait for DNS Propagation

- DNS changes can take **10 minutes to 48 hours** (usually under an hour)
- Check progress at **dnschecker.org** — type in your domain
- Once propagated, visit your domain — you should see your site!
- Go back to GitHub Settings → Pages and check **Enforce HTTPS** if it wasn't available before

---

## Part 5: Filling In the Placeholders

Once the site is live, fill in the remaining pieces one at a time. For each change, you'll edit files directly on GitHub (click any file → pencil icon → edit → commit).

### Add Screenshots to the Gallery

1. Take 6 screenshots of the Kaleidograph with different effects/settings
2. Navigate to the `screenshots/` folder in your repo on GitHub
3. Click **Add file → Upload files** and upload your screenshots (name them `1.jpg` through `6.jpg` or whatever you like)
4. Go back to `index.html`, click the pencil icon to edit
5. Find each `<div class="gallery-item reveal">screenshot</div>` and replace with:

```html
<div class="gallery-item reveal"><img src="screenshots/1.jpg" alt="Kaleidograph visualization"></div>
```

Do this for all 6, changing the filename each time. Commit the change.

### Add Your YouTube Demo Video

1. Upload your demo video to YouTube
2. Get the video ID from the URL (the part after `v=`, e.g., if the URL is `youtube.com/watch?v=abc123` the ID is `abc123`)
3. Edit `index.html` on GitHub
4. Find this block:

```html
<div class="video-placeholder">
  <div class="play-icon">▶</div>
  <span>Demo video coming soon</span>
</div>
```

5. Replace it with:

```html
<iframe src="https://www.youtube.com/embed/YOUR_VIDEO_ID" allowfullscreen style="border:none;"></iframe>
```

6. Commit the change

### Set Up Gumroad

1. Go to **gumroad.com** and create an account
2. Click **New Product**
3. Choose **Digital Product**
4. Upload your packaged Kaleidograph app (as a zip file)
5. Set the price to **$39**
6. Add a title, description, and cover image (use a screenshot or the logo)
7. Publish the product
8. Copy the product URL (looks like `https://yourname.gumroad.com/l/kaleidograph`)
9. Edit `index.html` on GitHub
10. Find every `href="#"` on purchase/download buttons and replace `#` with your Gumroad URL
11. Commit

### Link the Web Demo

When your limited web demo is ready:

1. Create a `demo/` folder in your repo (Add file → Create new file → type `demo/index.html`)
2. Paste in the limited version of the Kaleidograph
3. Update the "try the free web demo" links in `index.html` to point to `demo/index.html`

### Update Footer Links

Edit `index.html` and replace the `#` in the footer links with your actual YouTube channel and Reddit profile URLs.

---

## Making Future Updates

To change anything on your site:

1. Go to your repo on github.com
2. Click the file you want to edit
3. Click the **pencil icon** (edit)
4. Make your changes
5. Scroll down, type a commit message (e.g., "Updated pricing")
6. Click **Commit changes**

Changes go live within a minute or two.

To upload new files (like screenshots or images):

1. Navigate to the folder where you want them
2. Click **Add file → Upload files**
3. Drag files in and commit

---

## Troubleshooting

**Site shows 404:**
- Make sure GitHub Pages is enabled (Settings → Pages → source is set to main branch)
- Make sure `index.html` is in the root of the repo, not inside a subfolder

**Domain not working:**
- Double-check DNS records at **dnschecker.org**
- Make sure you deleted any old A records that GoDaddy had by default
- DNS can take up to 48 hours (usually much faster)

**HTTPS not working / "Enforce HTTPS" is grayed out:**
- GitHub needs to generate an SSL certificate after DNS propagates
- This can take up to 24 hours — just check back later

**Images not showing:**
- File paths are case-sensitive on GitHub — `Images/` is different from `images/`
- Make sure the filenames in your HTML match exactly what's in the repo

**Site looks different than expected:**
- Hard-refresh your browser: Ctrl+Shift+R (clears cached version)
