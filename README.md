# RightsDesk

**RightsDesk** is a lightweight collection of browser‑based civics tools built for students, teachers and engaged citizens.  Each tool is a self‑contained HTML + JavaScript file that runs entirely in your browser—no backend needed.

## 🚀 Quick Start

1. Clone the repository:

   ```bash
   git clone https://github.com/YOUR_USERNAME/rightsdesk-site.git
   cd rightsdesk-site
   ```

2. You can simply open `index.html` in your browser to browse the tools locally, or serve the folder with any static HTTP server (e.g. `python -m http.server`).

3. Deploy to Vercel by installing the [Vercel CLI](https://vercel.com/docs/cli) and running:

   ```bash
   vercel --prod
   ```

   Make sure you set `VERCEL_TOKEN` in your environment or in GitHub secrets.

## 🗂 Directory Structure

```
/index.html                  # Home page listing all tools
/apps/<slug>/index.html      # Individual tools (pure HTML + JS + Tailwind)
/assets/logo.svg             # Brand logo
/sitemap.xml                 # Sitemap used by search engines
/robots.txt                  # Robots rules referencing sitemap
/vercel.json                 # Static hosting rewrites for Vercel
/.github/workflows/deploy.yml# CI workflow to deploy on push to main
```

## 🛠 Adding a New Tool

To manually add a tool:

1. Create a folder under `apps/` with a URL‑friendly slug.
2. Add an `index.html` file inside that folder.  Follow the pattern in `apps/bill-of-rights-keyword-finder/index.html` for meta tags, accessibility and monetization placeholders.
3. Update `/index.html` by adding a new card to the tools grid with the tool’s title, description and link.
4. Append a new `<url>` entry to `/sitemap.xml` with the new tool path and the current date.
5. Commit your changes and push.  The GitHub workflow will deploy automatically.

## ⚙️ Automation

A pre‑configured Zapier/Make automation (see `AUTOMATION_SPEC` below) can generate a new tool every Friday at 10:00 AM America/Chicago:

- It triggers this GPT agent with a queued tool idea.
- It writes the new `/apps/<slug>/index.html`, updates `index.html` and `sitemap.xml`, and commits the changes via the GitHub API.
- It triggers a Vercel deploy and posts announcements to X and Pinterest.

## 🔐 Secrets

For deployments and automation you’ll need to set the following secrets in your GitHub repository:

- `VERCEL_TOKEN` – your personal Vercel token for CLI deployments.
- `ADSENSE_CLIENT_ID` – your Google AdSense publisher ID (optional; otherwise placeholders remain).
- `AMAZON_ASSOC_TAG` – your Amazon Associates affiliate tag (optional).
- `GH_TOKEN` and `GH_USERNAME` – used by the automation to authenticate GitHub API calls.

## 🗓 License

All site content (including the Bill of Rights text【470169887546908†L183-L249】) is in the public domain.  Code in this repository is MIT licensed.
