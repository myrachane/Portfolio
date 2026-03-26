# emtypyie — Portfolio Data

This repo is the **CMS** for [emtypyie.in](https://emtypyie.in).  
Edit a JSON file → commit → push → the portfolio updates automatically. No deploy needed.

---

## 📁 Folder Structure

```
portfolio-data/
├── data/
│   ├── projects.json     ← Your projects
│   ├── blogs.json        ← Blog posts
│   ├── experience.json   ← Work history
│   └── skills.json       ← Skills & proficiency
├── images/
│   ├── visrodeck-cover.png   ← Project cover images
│   └── relay-cover.png
└── README.md
```

---

## ✏️ How to Update Content

### Add a new project
Open `data/projects.json` and add an object to the array:

```json
{
  "id": "3",
  "name": "YOUR PROJECT NAME",
  "role": "Your Role Here",
  "desc": "Short description of the project.",
  "url": "https://yourproject.com",
  "github": "https://github.com/you/repo",
  "cover": "https://raw.githubusercontent.com/emtypyie/portfolio-data/main/images/project-cover.png"
}
```

> **Cover image:** Upload the image to the `images/` folder, then use the raw GitHub URL as the `cover` value.  
> Leave `"cover": ""` to show a placeholder.

---

### Add a blog post
Open `data/blogs.json` and add to the top of the array (newest first):

```json
{
  "id": "3",
  "title": "Your Blog Post Title",
  "tag": "Design",
  "date": "2025-06-01",
  "excerpt": "One sentence that appears in the blog card.",
  "content": "Full post text here.\n\nUse \\n\\n for paragraph breaks.\n\nWrite as much as you want — it renders in a modal."
}
```

**Available tags:** Design · Tech · AI · Culture · Startup · Personal *(or any custom tag)*

---

### Update experience
Open `data/experience.json` — newest entry first:

```json
{
  "id": "3",
  "period": "2025 — PRESENT",
  "role": "Your New Role",
  "company": "Company Name",
  "desc": "What you did there."
}
```

---

### Update skills
Open `data/skills.json` — group by `cat` (category):

```json
{ "id": "10", "cat": "Design", "name": "3D / Blender", "pct": 70 }
```

`pct` = proficiency percentage (1–100). Controls the animated bar.

---

## ⚙️ Connecting to the Portfolio

In `index.html`, find these 3 lines near the top of the `<script>` tag:

```js
const GH_USER   = 'emtypyie';        // ← your GitHub username
const GH_REPO   = 'portfolio-data';  // ← this repo's name
const GH_BRANCH = 'main';            // ← branch name
```

Change them to match your actual GitHub username and repo name.  
The portfolio fetches:
```
https://raw.githubusercontent.com/GH_USER/GH_REPO/GH_BRANCH/data/projects.json
https://raw.githubusercontent.com/GH_USER/GH_REPO/GH_BRANCH/data/blogs.json
https://raw.githubusercontent.com/GH_USER/GH_REPO/GH_BRANCH/data/experience.json
https://raw.githubusercontent.com/GH_USER/GH_REPO/GH_BRANCH/data/skills.json
```

> **Make sure this repo is PUBLIC** so the raw URLs are accessible without authentication.

---

## 🔄 Workflow

```
1. Edit a JSON file on GitHub.com  (or clone → edit → push)
2. Commit the change
3. Visit your portfolio — it fetches fresh data on every load ✓
```

No rebuilds. No deploys. Just JSON.
