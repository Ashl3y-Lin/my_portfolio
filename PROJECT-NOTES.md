# Project notes: Ashley Lin's portfolio website

> **For Ashley:** when you start a new chat with any Claude account (or another AI), attach this file, or paste its link from GitHub, and say:
> *"This is my portfolio website. Read PROJECT-NOTES.md first, then help me with: …"*
>
> **For the AI reading this:** this file explains how the site works and where we left off. The repository is the source of truth. Read `data.json` for the current content before suggesting changes.

Last updated: October 2026.

---

## 1. What this is

Ashley Lin's personal portfolio: all her creative and tech projects. Hosted free on **GitHub Pages** from this repository. It is a static site with no server and no build step. Ashley keeps a local copy in VS Code and pushes with git.

- **Sections:**
  - **Blender:** the biggest focus. Categories: 3D style, 2D visual, Low poly.
  - **3D Production:** Sculpting, 3D printing.
  - **Branding**
  - **Animation**
  - **Advertising**
  - **Projects:** MAIRIN, AquaMotriz, Vitalia, Reviste, ANS Robotics website.
- **Look:**
  - Her color palette: white background, blush `#F5F0F4`, mauve `#886C7B`, slate/navy `#2A3744`, blue-gray.
  - Sans-serif fonts: Archivo (titles), Figtree (text), Barlow Condensed (small labels), Noto Sans SC (Chinese).
  - The A.L.F logo is the site icon.
- **Languages:** English, Spanish and Simplified Chinese, with a switcher at the top right.

## 2. Files

| File | What it is |
| --- | --- |
| `index.html` | The whole website **and** the built-in editor (HTML, CSS and JavaScript in one file) |
| `data.json` | All content: profile, sections, projects, links, image lists, translations |
| `i18n.json` | Ready-made Spanish and Chinese translations, merged in once (see §5) |
| `images/` | Images, GIFs, logo, favicon |
| `files/` | PDFs (MAIRIN identity manuals in English and Spanish, Reviste report) |
| `README.md` | Step-by-step instructions for Ashley (setup, editing, PIN, languages) |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |

## 3. How editing works

1. On the live site, Ashley clicks **✎ Edit** (bottom of the page) and types her **6-digit PIN**.
2. The PIN unlocks a **GitHub fine-grained token** (Contents: read and write, this repository only). The token is stored **encrypted in her browser only** (AES-GCM; key derived from the PIN with PBKDF2, 600,000 iterations). It is never in the repository.
3. **Save & publish** makes one commit through the GitHub API with the updated `data.json` and any new uploads. The site updates in about a minute.
4. **Safety:**
   - 5 wrong PINs lock editing for 5 minutes. After 10, the stored token is erased.
   - **Forgot PIN or token expired:** create a new token on GitHub, then click **Forgot PIN?** on the site.
5. ⚠️ Because the site editor commits straight to GitHub, **always run `git pull` in VS Code before pushing**, so an older `data.json` doesn't overwrite her edits.

Never ask Ashley to paste her token or PIN into a chat or a file.

## 4. Content model (`data.json`)

```
profile:  name, role, bio, location, email, avatar, links[{label,url}]
site:     title, logo
sections: [{id, title, kicker, intro, stages[], feature?, groups?[{id, title, stages[]}]}]
projects: [{id, section, group, title, year, tag, summary, body, award,
            links[{label,url}], media[{id(path), kind, stage, time, caption}],
            process(bool: show images as a step-by-step player), coverId, coverPos}]
```

**Translations** sit on each object as `i18n.es` / `i18n.zh`, with the same field names. For example:
- `project.i18n.es.title`
- `project.i18n.zh.links[url] = label`
- `project.i18n.es.media[imagePath] = {caption, time}`
- `section.i18n.es.stages = [...]` (same order as the English list)

Any field without a translation shows the English text.

## 5. Languages

- Visitors pick **EN · ES · 中文**. The choice is remembered, first-time visitors get their browser's language, and links can use `?lang=es` or `?lang=zh`.
- **New text is not translated automatically.** Ashley adds it in EN, then switches to ES or 中文, clicks Edit, and types the translation. Or she pastes the English to an AI and copies the result back in.
- `i18n.json` was a one-time seed. It is merged on load until `data.json` has `i18nSeed: 1`. A seed translation is only used while the English text still matches the text it was translated from.

## 6. Facts to keep correct

- **MAIRIN** (women's health app): 🥈 2nd place, Kronox Hackathon 10th edition (Oct 2026).
- **AquaMotriz:** 🥇 1st place at the UAM campus and Nicaragua national stages of the Latin American Rally, then 🥈 2nd place at the Latin American stage. Keeps both Spanish and English text.
- **Vitalia:** 🥇 1st place, National Innovation Rally, Nicaragua Innova 2026 (Innovation category). Keeps both Spanish and English text.
- **Reviste:** 🥈 2nd place **only at the UAM DIEM campus stage**, not national.
- **WRO robotics:** 5th, then 4th, then 2nd place over 3 years. Now her school's robotics coach.
- Don't show "Managua, Nicaragua" on the site. Don't write "(Amateur category)".
- She prefers **GIFs over MP4 videos** on the site.
- Twin-Tail Fighter's cover crop must keep her head (cover crop "Top").

## 7. Where we left off / ideas

- [ ] The "About me" bio on the home page is still placeholder text. Write it in EN, ES and 中文.
- [ ] Idea: auto-resize uploaded images to about 2000 px to keep the site light.
- [ ] Idea: if the GitHub token has expired, keep unsaved changes instead of losing them.
- Limits to remember (GitHub Pages): about 1 GB site size, 100 GB/month bandwidth, about 10 publishes per hour.
