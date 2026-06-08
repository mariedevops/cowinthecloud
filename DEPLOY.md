# Cow in the Cloud — Deploy Guide

## Step 1 — Host on GitHub Pages (browser only, no terminal)

1. Go to **github.com** → sign in (or create a free account)
2. Click **+** → **New repository**
   - Name: `cowinthecloud`
   - Set to **Public**
   - Click **Create repository**
3. On the new repo page click **uploading an existing file**
4. Drag and drop ALL files from your `cowinthecloud` folder:
   - `cow_in_the_cloud.html`
   - `manifest.json`
   - `sw.js`
   - `icon-32.png`, `icon-180.png`, `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`
5. Click **Commit changes**
6. Go to **Settings** → **Pages** (left sidebar)
7. Under *Source* select **Deploy from a branch** → branch: **main** → folder: **/ (root)**
8. Click **Save** — wait ~60 seconds
9. Your game is live at: `https://YOUR-USERNAME.github.io/cowinthecloud/cow_in_the_cloud.html`

---

## Step 2 — Test on iPhone (no developer account needed)

1. Open Safari on your iPhone
2. Go to your GitHub Pages URL above
3. Tap the **Share** button (box with arrow) → **Add to Home Screen**
4. Name it "Cow Cloud" → **Add**
5. The game icon appears on your home screen — tap it to play fullscreen

> Rotate your phone to **landscape** before opening for best experience.

---

## Step 3 — Package for Google Play (browser only)

1. Go to **pwabuilder.com**
2. Paste your GitHub Pages URL → click **Start**
3. PWABuilder will analyse your PWA and show a score
4. Click **Package for stores** → choose **Google Play**
5. Fill in:
   - Package name: `com.yourname.cowinthecloud`
   - App version: `1`
   - Signing key: click **Generate** (save the `.keystore` file safely — you need it for all future updates)
6. Click **Download** — you get an `.aab` file (Android App Bundle)
7. Go to **play.google.com/console** → create a developer account ($25 one-time fee)
8. Create a new app → upload the `.aab` → fill in store listing → submit for review

---

## Step 4 — Package for App Store (requires a Mac with Xcode)

**Option A — Median.co (no Mac needed, paid service ~$29/mo)**
1. Go to **median.co**
2. Enter your GitHub Pages URL
3. Median builds the iOS `.ipa` for you
4. You still need an Apple Developer account ($99/year) to submit to App Store

**Option B — Build it yourself on a Mac**
1. On a Mac: install Node.js (nodejs.org) and Xcode (App Store, free)
2. Open Terminal and run:
   ```
   npm install -g @capacitor/cli
   npx create-capacitor-app cowinthecloud
   cp cow_in_the_cloud.html www/index.html
   cp manifest.json sw.js icon-*.png www/
   npx cap add ios
   npx cap open ios
   ```
3. In Xcode: sign with your Apple Developer account → **Product → Archive → Distribute**

---

## Store listing checklist (both stores)

Before submitting you will need:
- [ ] App name: *Cow in the Cloud*
- [ ] Short description (80 chars): *Help Berta the cow dodge birds, planes and balloons on her magic cloud!*
- [ ] Full description
- [ ] Screenshots: at least 2 landscape screenshots (take them from your browser)
- [ ] Privacy policy URL (required) — a simple one-page site is fine
- [ ] Content rating: Everyone / 4+
- [ ] Category: Games → Arcade
