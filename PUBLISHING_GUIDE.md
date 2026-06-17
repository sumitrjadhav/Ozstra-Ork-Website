# Publishing the Ozstra Website on GitHub

This guide walks you through putting the website online for free using
**GitHub Pages**. No coding required beyond copy-pasting commands — total
time is about 10 minutes.

You'll end up with a live URL like:
`https://YOUR-USERNAME.github.io/ozstra-site/`

You can later point your own domain (e.g. `ozstra.io`) at this for free too —
see Step 6.

---

## What's in this folder

```
ozstra-site/
├── index.html                    ← the website itself
├── favicon.ico                   ← browser tab icon
├── apple-touch-icon.png          ← iOS home screen icon
├── android-chrome-192x192.png    ← Android icon
├── android-chrome-512x512.png    ← Android icon (large)
└── .nojekyll                     ← tells GitHub Pages not to process the site
```

`index.html` is the filename GitHub (and the web in general) automatically
loads when someone visits your site's root URL — don't rename it.

---

## Step 1 — Create a free GitHub account

Skip this if you already have one. Go to **github.com/signup** and follow
the prompts.

---

## Step 2 — Create a new repository

1. Once logged in, click the **+** icon top-right → **New repository**
2. Repository name: `ozstra-site` (or anything you like — this becomes part
   of your URL)
3. Set it to **Public** (required for free GitHub Pages hosting)
4. Don't check "Add a README" — leave everything else default
5. Click **Create repository**

GitHub will show you a page with setup instructions — keep that tab open,
you'll need the repository URL it shows (something like
`https://github.com/YOUR-USERNAME/ozstra-site.git`).

---

## Step 3 — Upload the files

You have two options. **Option A** is easiest if you've never used git
before.

### Option A — Upload through the browser (no terminal needed)

1. On your new repository's page, click **uploading an existing file**
   (it's a link in the quick-setup instructions)
2. Drag in every file from this `ozstra-site` folder, **including the
   hidden `.nojekyll` file** — if your file browser hides it, use Option B
   instead, or enable "show hidden files" first
3. Scroll down, click **Commit changes**

### Option B — Upload using git (handles hidden files automatically)

Open a terminal, `cd` into this `ozstra-site` folder, then run:

```bash
git init
git add -A
git commit -m "Initial Ozstra website"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/ozstra-site.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your actual GitHub username. You'll be
prompted to log in the first time — follow GitHub's instructions (it'll
likely ask you to authenticate via browser or a personal access token).

---

## Step 4 — Turn on GitHub Pages

1. In your repository, click **Settings** (top tab bar)
2. In the left sidebar, click **Pages**
3. Under "Build and deployment" → **Source**, select **Deploy from a branch**
4. Under **Branch**, choose **main** and folder **/ (root)**, then click **Save**

GitHub will take 30–60 seconds to build your site for the first time.

---

## Step 5 — Visit your live site

Refresh the **Pages** settings screen — a green banner will appear with
your live URL:

```
https://YOUR-USERNAME.github.io/ozstra-site/
```

Click it. Your Ozstra website is now live and publicly accessible.

Any time you push new changes to the `main` branch, GitHub automatically
rebuilds the live site within about a minute.

---

## Step 6 — (Optional) Connect a custom domain like ozstra.io

If you own a domain:

1. In **Settings → Pages**, under **Custom domain**, type your domain
   (e.g. `ozstra.io` or `www.ozstra.io`) and click **Save**
2. GitHub will show a **Save** confirmation and create a `CNAME` file in
   your repo automatically
3. Go to your domain registrar (GoDaddy, Namecheap, Google Domains, etc.)
   and add these DNS records:

   **For a root domain (ozstra.io):**
   | Type | Name | Value |
   |------|------|-------|
   | A | @ | 185.199.108.153 |
   | A | @ | 185.199.109.153 |
   | A | @ | 185.199.110.153 |
   | A | @ | 185.199.111.153 |

   **For a www subdomain (www.ozstra.io):**
   | Type | Name | Value |
   |------|------|-------|
   | CNAME | www | YOUR-USERNAME.github.io |

4. DNS changes can take anywhere from a few minutes to 24 hours to take effect
5. Back in **Settings → Pages**, once GitHub detects the DNS is correctly
   pointed, check **Enforce HTTPS** for a secure padlock

---

## Updating the site later

Any time you want to change something:

- **Browser method:** open the file in your repository on GitHub, click the
  pencil (✏️) icon to edit, then **Commit changes**
- **Git method:** edit `index.html` locally, then run:
  ```bash
  git add -A
  git commit -m "Update site copy"
  git push
  ```

Changes go live automatically within about a minute.

---

## Troubleshooting

**Site shows a 404 page** — double check the file is named exactly
`index.html` (lowercase) and sits in the repository root, not inside a
subfolder.

**Favicon/icons don't show up** — browsers cache favicons aggressively; try
a hard refresh (Ctrl+Shift+R / Cmd+Shift+R) or open in a private/incognito
window.

**Custom domain shows "not configured" error** — DNS propagation can take
up to 24 hours; re-check your DNS records match exactly, and that the
`CNAME` file GitHub created wasn't accidentally deleted.
