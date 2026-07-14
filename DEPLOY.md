# drtech.online — Deploy notes

Static landing for DFR Tech Solutions, served by GitHub Pages from `main` branch root of `Maximmxxii/drtech-online`.

## How to update the site

1. Edit `index.html` (or add assets under `assets/`).
2. Commit and push:

```bash
git add -A
git commit -m "Describe the change"
git push origin main
```

GitHub Pages rebuilds automatically on push (usually live within 1-2 minutes).

Do NOT delete or edit the `CNAME` file — it binds the custom domain `drtech.online`.

## DNS records expected at GoDaddy

| Type  | Host | Value                 |
|-------|------|-----------------------|
| A     | @    | 185.199.108.153       |
| A     | @    | 185.199.109.153       |
| A     | @    | 185.199.110.153       |
| A     | @    | 185.199.111.153       |
| CNAME | www  | maximmxxii.github.io  |

## Pending follow-up

- Once DNS propagates and GitHub issues the TLS certificate (can take up to 24h),
  enforce HTTPS:

```bash
gh api -X PUT repos/Maximmxxii/drtech-online/pages \
  -F cname=drtech.online -F https_enforced=true \
  -f 'source[branch]=main' -f 'source[path]=/'
```

  Or toggle "Enforce HTTPS" in repo Settings → Pages.
