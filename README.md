# Personal Site

A deliberately small Astro site for publishing mobile engineering work through this loop:

**Problem → Solution → Demo / Tool → Article → Website**

The public navigation contains only **Home**, **Solutions**, **Projects**, and **About**. The first reserved topic is **Android 16KB Page Size Compatibility**.

## Tech stack

- Astro static site generator
- Markdown and MDX through the official `@astrojs/mdx` integration
- GitHub Actions deployment to GitHub Pages
- No CMS, database, comments, server, or user accounts

## Local development

Requirements: Node.js 22 or newer and npm.

```bash
npm install
npm run dev
```

Open the local URL printed in the terminal (normally `http://localhost:4321/personal-site/`).

## Production build

```bash
npm run build
npm run preview
```

The static output is generated in `dist/`.

## Add an article

Create a `.md` or `.mdx` file under `src/pages/solutions/`. Use `ArticleLayout` in its frontmatter:

```md
---
layout: ../../layouts/ArticleLayout.astro
title: Article title
description: One-sentence summary.
status: Draft
---

Article content starts here.
```

Then add a card linking to it from `src/pages/solutions/index.astro`. Use MDX when the article needs components or expressions; ordinary Markdown works for text-only content.

## GitHub Pages configuration

The repository is expected to be:

```text
https://github.com/WeidongHe/personal-site
```

The initial Pages URL will be:

```text
https://weidonghe.github.io/personal-site/
```

The matching values are already set in `astro.config.mjs`. If the GitHub username or repository name changes, update both `site` and `base` there.

### First deployment

1. Create a public GitHub repository named `personal-site` without adding starter files.
2. From this directory, run:

   ```bash
   git init
   git add .
   git commit -m "Create minimal Astro personal site"
   git branch -M main
   git remote add origin git@github.com:WeidongHe/personal-site.git
   git push -u origin main
   ```

3. On GitHub, open **Settings → Pages** and set **Source** to **GitHub Actions**.
4. Open the repository's **Actions** tab and wait for **Deploy to GitHub Pages** to finish.
5. Visit `https://weidonghe.github.io/personal-site/`.

Every later push to `main` triggers the deployment workflow in `.github/workflows/deploy.yml` automatically.

## Project structure

```text
src/
├── layouts/        Shared page and article layouts
├── pages/          Home, Solutions, Projects, About, and articles
└── styles/         One global stylesheet
.github/workflows/  GitHub Pages deployment
public/             Static assets
```

## Custom domain

Not configured yet. Start with the default GitHub Pages address; a custom domain can be added later without changing the content structure.
