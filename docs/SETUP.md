# Houssam Moallem Website — Setup & Workflow Guide

> **Team:** Houssam (owner/editor) + Hermes Agent (AI coding assistant)  
> **Workflow:** You ask for changes → I edit files → you see them live  
> **Last Updated:** July 6, 2026

---

## 1. How We Work

```
┌────────────────────┐         ┌──────────────────┐         ┌───────────────┐
│  Houssam           │         │  GitHub           │         │  Server       │
│  (Telegram / any)  │◀───────▶│  hsmoallem/       │◀───────▶│  nginx        │
│                    │         │  houssammoallem-com│        │  /var/www/... │
│  "update my site"  │         │  (source code)    │         │  (live site)  │
└────────────────────┘         └──────────────────┘         └───────────────┘
                                                                      │
                                                              Visitors see changes
                                                              instantly (static HTML)
```

1. You message me on Telegram: *"add this to my website"*, *"change the title"*, etc.
2. I edit the files in two places:
   - **Server live copy:** `/var/www/houssammoallem/` → changes appear instantly
   - **Git repo:** `~/houssammoallem-com/` → committed and pushed to GitHub
3. You see your changes live immediately at [houssammoallem.com](https://houssammoallem.com)

---

## 2. Where Everything Lives

| What | Path |
|------|------|
| **Live site files** | `/var/www/houssammoallem/` |
| **Git local repo** | `~/houssammoallem-com/` |
| **Git remote** | `github.com/hsmoallem/houssammoallem-com` |
| **nginx config** | `/etc/nginx/sites-available/houssammoallem.com` |
| **Documentation** | `~/houssammoallem-com/docs/` |

---

## 3. Editing the Website (via Hermes)

### To edit the Coming Soon page

Just tell me what to change:
- *"Change the title to X"*
- *"Add a new badge"*
- *"Add a link to my Twitter"*

I edit `/var/www/houssammoallem/index.html` and `/home/houssam/houssammoallem-com/index.html`.

### To edit the Beta portfolio

- *"Add a new case study"* → I create a new HTML file in `beta/projects/`
- *"Update the About page"* → I edit `beta/about.html`
- *"Change the styling"* → I edit `beta/styles.css`

### To add a new page

1. Tell me what the page should contain
2. I create the HTML file in the right location
3. I update `sitemap.xml` to include it
4. I commit everything to GitHub

---

## 4. Deploying After GitHub Edits

If you (or another AI tool) edit the code on GitHub directly, the live site won't update until you deploy:

### From your server terminal

```bash
cd ~/houssammoallem-com
GIT_SSH_COMMAND="ssh -i ~/.ssh/id_ed25519_vocab -o IdentitiesOnly=yes" git pull
sudo cp -r * /var/www/houssammoallem/
```

### From Hermes (just ask)

*"Pull from GitHub and deploy my website"*

---

## 5. Common Tasks

| Task | Command / How |
|------|---------------|
| Check if site is up | `curl -s -o /dev/null -w "%{http_code}" https://houssammoallem.com/` |
| View nginx logs | `sudo tail -f /var/log/nginx/access.log` |
| Restart nginx | `sudo systemctl restart nginx` |
| Test nginx config | `sudo nginx -t` |
| Push to GitHub | From `~/houssammoallem-com/`: use SSH push command |
| Check GitHub status | `git log --oneline -5` from repo |

---

## 6. Git Commit Conventions

We use simple commit messages:

```
SEO: add OG tags, Twitter cards to all pages

- beta/index.html: Schema.org Person, OG+Twitter tags
- beta/about.html: Schema.org AboutPage, OG+Twitter tags
- All 5 project pages: improved titles, meta descriptions, canonicals
```

---

## 7. Adding a New Case Study

1. Create the HTML file: `beta/projects/new-project.html`
2. Add a card for it in `beta/index.html` (under the case studies section)
3. Add the URL to `sitemap.xml`
4. Deploy to server and push to GitHub

---

## 8. Troubleshooting

| Problem | Check |
|---------|-------|
| Site returns 530 | Cloudflare can't reach origin — verify DNS A record is `13.140.134.57`, nginx is running |
| Site returns 403 | File permissions — files must be readable by `www-data` (mode 644) |
| Changes not showing | Clear browser cache, check Cloudflare "Development Mode" |
| Mobile not updating | Toggle airplane mode (flushes DNS cache) |
| www subdomain broken | In Cloudflare DNS, `www` must be A record (not CNAME) |
| GitHub push fails | Check SSH key: `ssh -i ~/.ssh/id_ed25519_vocab -T git@github.com` |
