# AmaliticZ website

Static site for [amaliticz.com](https://www.amaliticz.com). Plain HTML and CSS. No build step.

## Pages

| Path | File | What it is |
| --- | --- | --- |
| `/` | `index.html` | Homepage |
| `/privacy/` | `privacy/index.html` | Privacy policy |
| `/terms/` | `terms/index.html` | Terms of use |
| `/support/` | `support/index.html` | Support form (FormSubmit) |
| `/reset-password/` | `reset-password/index.html` | Password reset (Supabase) |
| `/verified/` | `verified/index.html` | Email-verified landing page |

Shared styles live in `assets/site.css`. The homepage phone frame uses `assets/app-screenshot.png`, which is a labeled stand-in until a real app screenshot replaces it.

## Deploy

GitHub Pages, workflow `.github/workflows/deploy-reset-page.yml`.

It runs on `workflow_dispatch`, and on push to `main` when any of these paths change:

- `**/*.html` and `*.html` (every page, including `index.html`)
- `assets/**`
- `CNAME`
- `.github/workflows/deploy-reset-page.yml`

The job checks out the repo, injects Supabase config, and uploads the whole site. It replaces `__SUPABASE_URL__` and `__SUPABASE_ANON_KEY__` in both `index.html` and `reset-password/index.html` using the Actions secrets `SUPABASE_URL` and `SUPABASE_ANON_KEY`. The deploy fails if either placeholder is still present in those two files.

Leave the placeholders in git. Do not commit real Supabase keys.

## Store links

App Store (live):

`https://apps.apple.com/us/app/amaliticz-purchase-insights/id6749656484`

Android placeholder. The same URL is used everywhere an Android link appears (homepage Google Play badge and `verified/index.html` `AND_URL`):

`https://play.google.com/store/apps/details?id=com.amaliticz.app`

Change that string on each page when the Play Store listing is live.
