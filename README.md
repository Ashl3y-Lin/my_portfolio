# Ashley Lin · Portfolio

Personal portfolio website, hosted on GitHub Pages, with a built-in editor protected by a 6-digit PIN.

## What's in this folder

| File / folder | What it is |
| --- | --- |
| `index.html` | The website and the editor |
| `data.json` | All your text, projects, sections and links |
| `images/` | Every image, GIF, logo and favicon |
| `files/` | PDFs (MAIRIN identity manuals, Reviste report) |
| `.nojekyll` | Tells GitHub Pages to publish the files as they are |

## 1. Put the site on GitHub

1. On GitHub, create a new **public** repository called `portfolio`.
2. Upload everything in this folder to it.
   - In the browser: **Add file → Upload files**. GitHub accepts up to 100 files at a time, and `images/` has 101, so upload in two rounds (for example `index.html`, `data.json`, `files/` and half of `images/` first, then the rest).
   - `.nojekyll` is a hidden file on Mac. If it doesn't upload, that's fine. The site works without it.
3. Go to **Settings → Pages**. Under **Build and deployment**, set **Source** to **Deploy from a branch**, then choose branch **main** and folder **/ (root)**. Click **Save**.
4. After 1–2 minutes your site is live at **https://ashl3y-lin.github.io/portfolio/**.

## 2. Create your GitHub key (once)

The editor needs a key that lets it write to this one repository.

1. Open **GitHub → Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**
   (direct link: https://github.com/settings/personal-access-tokens/new).
2. **Name:** `portfolio editor`. **Expiration:** up to 1 year.
3. **Repository access:** **Only select repositories** → `portfolio`.
4. **Permissions → Repository permissions → Contents:** **Read and write**.
5. Click **Generate token** and copy it. Don't share it or put it in any file.

## 3. Set up editing on your device (once per device)

1. Open your live site and click **✎ Edit** at the bottom of the page.
2. Check the repository name (`ashl3y-lin/portfolio`), paste your key, and choose a 6-digit PIN.
3. Click **Save and unlock**.

## Everyday editing

1. Click **✎ Edit** at the bottom of the site and enter your PIN.
2. Make changes. You can:
   - edit your profile, photo, logo and the browser tab title
   - add, edit, reorder and delete projects
   - upload images, GIFs and videos, and group them into stages
   - add links and upload PDFs
   - add, rename, reorder and delete sections and categories
3. Click **Save & publish**. Your site updates for everyone in about a minute.

## How the PIN keeps the site safe

- Your key is saved **only in your browser**, encrypted with your PIN. It is never part of the website, so visitors can't see it.
- Someone who clicks **Edit** on another device only sees the setup screen. Without your key, they can't change anything.
- After 5 wrong PINs, editing locks for 5 minutes. After 10, the saved key is erased from that device.
- Every save is a normal GitHub commit, so you can see and undo any change in the repository's history.
- **Lost a device or forgot your PIN?** Delete the key on GitHub (**Settings → Personal access tokens**) and create a new one. Then, on the site, choose **Forgot PIN?** and set it up again.
- **When the key expires,** saving will tell you. Create a new key and use **Forgot PIN?** to enter it.
