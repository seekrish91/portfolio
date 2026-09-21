# Ram Krishnamoorthy — portfolio

A small, dependency-free static website. The canonical checkout is `/Users/seetharamankrishnamoorthy/projects/portfolio/website`.

## Run locally

```sh
python3 build.py
python3 -m http.server 8765 --directory dist
```

Open http://localhost:8765. Re-run the build after content or CSS changes. No npm install is needed.

## Content

- About page and general page copy: `build.py`.
- Education: `content/education.json` (institution, degree, dates, focus, activities).
- Career history: `content/experience.json` (company, title, dates, location, summary, achievements).
- Projects: `content/projects.json`. Each record has a unique lowercase slug, title, type, status, summary, tags, and sections (title/text). Optional `repository` links to real source code. A detail page is built automatically.
- Writing: `content/writing.json`. It contains two verified LinkedIn articles. Add entries with `slug`, `title`, `date` (YYYY-MM-DD), `platform`, `url` (HTTPS), `summary`, and optional `project` (an existing project slug). Entries are shown newest first.
- Styles: `assets/style.css`.
- Generated public files: `dist/`. Keep these tracked for Sites static deployment. Vercel serves only `dist/`, but this GitHub repository is public. Do not put private notes or secrets anywhere in this repository.

Writing entry shape (example only; not published content):

```json
{
  "slug": "your-post-slug",
  "title": "Your actual published title",
  "date": "2026-10-01",
  "platform": "LinkedIn",
  "url": "https://www.linkedin.com/posts/your-actual-post",
  "summary": "A short, factual summary.",
  "project": "concurrency-and-latency"
}
```

Only add real publication links and verified claims. Project briefs must remain marked Planned until work has actually started. No external social embeds, analytics, trackers, remote fonts, or client-side JavaScript are required. The JSON-LD script is descriptive metadata, not executable application code.

## Design and quality

The site uses semantic landmarks, a skip link, visible keyboard focus, current-page navigation, responsive layouts, reduced-motion support, print styles, page descriptions, canonical URLs, Open Graph metadata, a favicon, sitemap, and a dedicated 404 page. It has no tracking cookies. This is not a certification of WCAG compliance.

Reference patterns: [Chip Huyen](https://huyenchip.com/) for clear personal context and links to actual work; [Eugene Yan](https://eugeneyan.com/) for distinct writing/prototyping areas and [readable writing entries](https://eugeneyan.com/writing/). The site's design and copy are original.

## Hosting

Target: Vercel Hobby, with the custom domain `ram.opscure.co` and DNS managed in GoDaddy. The existing private Sites deployment remains available as a draft; `.openai/hosting.json` preserves its identity. Do not create a second Sites site or overwrite the existing Sites remote when adding a GitHub remote.

Vercel reads `vercel.json`: framework Other, build command `python3 build.py`, output `dist`, no install step. This is a static site with no database or runtime functions. Python is needed only during the build.

`SITE_URL` controls canonical, Open Graph, and sitemap URLs; its default is `https://ram.opscure.co`. For an update to the private Sites draft, rebuild with `SITE_URL=https://ram-krishnamoorthy.ksraman91.chatgpt.site python3 build.py`.

Deployment steps:
1. Create a dedicated GitHub repository and push this website directory only, excluding the sibling learning_plan directory.
2. Import the repository into the existing personal Vercel Hobby account. Avoid enabling paid add-ons or trials.
3. Deploy and verify the Vercel URL, all routes, and the 404 response.
4. Add ram.opscure.co to the project's Domains settings.
5. Copy the exact domain-specific CNAME target shown by Vercel into GoDaddy, for host `ram`. Do not guess the target, alter nameservers, or change Punditpit/email records.
6. Confirm DNS verification and HTTPS issuance, then check the public site and canonical URLs.

Current state (2026-09-21):
- Source: https://github.com/seekrish91/portfolio (public), branch `main`, local remote `github`.
- Vercel project: https://vercel.com/seekrish91s-projects/portfolio on the existing Hobby plan.
- Live deployment: https://portfolio-nu-khaki-59.vercel.app
- GitHub integration is connected; pushes to `main` trigger production deployments.
- Primary site: https://ram.opscure.co — DNS configured by the owner in GoDaddy; Vercel reports Valid Configuration and HTTPS is verified.
- Active GoDaddy record: type `CNAME`, name `ram`, value `8f826b5b35a49b9c.vercel-dns-017.com` (from Vercel domain settings).
- Verified custom domain: home, projects, writing, and sitemap return HTTP 200 over HTTPS; a missing route returns HTTP 404.
- Verified initial deployment: home, projects, writing, a project detail page, stylesheet, sitemap, and robots return HTTP 200; a missing route returns HTTP 404.

To publish an update, edit the source/content, run `python3 build.py`, review changes, commit, and run `git push github main`.

Historical projects and published articles are sourced in CONTENT-SOURCES.md. Planned experiments remain explicitly labeled; no benchmarks or endorsements are invented.
