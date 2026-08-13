# Emergent Robotics

Professional research-program website for Trevor Smith, Ph.D. Built with Astro and designed to transition cleanly into a future faculty-lab website.

## Local development

Requirements: Node.js 18 or newer.

```bash
npm install
npm run dev
```

Open the local address Astro prints, normally `http://localhost:4321`.

```bash
npm run build
npm run preview
```

The production site is generated in `dist/`.

On Windows PowerShell, use `npm.cmd` instead of `npm` if your execution policy blocks `npm.ps1`:

```powershell
npm.cmd install
npm.cmd run dev
```

## Editing content

Most content can be updated without touching components:

- Identity, affiliation, biography, contact, and social links: `src/data/profile.ts`
- Research thrusts: `src/data/research.ts`
- Projects and paper/project links: `src/data/projects.ts`
- Publications: `src/data/publications.ts`
- Videos: `src/data/videos.ts`

To add a project, add one object to `projects.ts`. Astro automatically creates its card and `/projects/[slug]` detail page.

To add a publication, add one object to `publications.ts`. Year, project, and type filters are populated from the data automatically.

To add a video, add its verified YouTube URL and image to `videos.ts`. Videos are embedded only after visitors select them.

## Replacing images and the CV

Public files live in `public/` and retain their URL paths during the build.

- Research images: `public/images/research/`
- Portrait: `public/images/trevor-smith.jpg`
- Social preview: `public/images/og-image.jpg`
- CV: `public/cv/Trevor_Smith_CV.pdf`
- Favicon: `public/favicon.svg`

Keep the existing filenames to replace an asset without updating code. Use optimized JPG/WebP images around 1600–2400 pixels wide where possible.

## Changing affiliation or transitioning to a faculty lab

Edit `src/data/profile.ts`. The current value is:

```ts
siteMode: 'research-program'
```

After accepting a faculty position, change it to `faculty-lab`, change `brand` to `Emergent Robotics Lab`, and update the institution, department, and role fields. Empty lab-member, openings, facilities, alumni, and teaching pages are intentionally not exposed. Add those routes only when real content exists.

## Deployment

### GitHub Pages

1. Push the repository to GitHub.
2. In repository settings, open **Pages** and choose **GitHub Actions** as the source.
3. Add an Astro GitHub Pages workflow following the official Astro deployment guide.
4. For a project-site URL rather than a custom domain, add the repository path as `base` in `astro.config.mjs`.

The custom domain avoids a `base` path and is already represented by the `site` setting.

### Cloudflare Pages

1. Connect the GitHub repository in Cloudflare Pages.
2. Choose the **Astro** framework preset.
3. Use build command `npm run build`.
4. Use output directory `dist`.
5. Add `emergentroboticslab.com` under **Custom domains** and follow Cloudflare's DNS prompts.

### Custom domain

The canonical production domain is configured in `astro.config.mjs`. If the domain changes, update that file plus `public/robots.txt` and `public/sitemap.xml`.

## Repository map

```text
src/
  components/    Shared header, footer, and content cards
  data/          Editable research and profile content
  layouts/       SEO and page shell
  pages/         File-based routes
  styles/        Global visual system
public/          Images, CV, favicon, robots.txt, and sitemap
```

Do not add unverified publications, awards, accounts, or institutional claims. Blank social links in `profile.ts` remain hidden until verified URLs are supplied.
