# Houssam Moallem Website — Setup & Workflow Guide

> **Team:** Houssam (owner) + Hermes Agent (AI coding assistant)  
> **Workflow:** You ask for changes → I edit files → live immediately  
> **Last Updated:** July 7, 2026

---

## 1. How We Work

```
┌────────────────────┐         ┌──────────────────┐         ┌───────────────┐
│  Houssam           │         │  GitHub           │         │  Server       │
│  (Telegram)        │◀───────▶│  hsmoallem/       │◀───────▶│  nginx        │
│                    │         │  houssammoallem-com│        │  /var/www/... │
│  "update my site"  │         │  (source code)    │         │  (live site)  │
└────────────────────┘         └──────────────────┘         └───────────────┘
```

1. You message me on Telegram with changes
2. I edit files in two places:
   - **Server:** `/var/www/houssammoallem/` → live instantly
   - **Git repo:** `~/houssammoallem-com/` → committed + pushed to GitHub
3. Changes appear at [houssammoallem.com](https://houssammoallem.com)

---

## 2. Where Everything Lives

| What | Path |
|------|------|
| **Live site files** | `/var/www/houssammoallem/` |
| **Git local repo** | `~/houssammoallem-com/` |
| **Git remote** | `github.com/hsmoallem/houssammoallem-com` |
| **nginx config** | `/etc/nginx/sites-available/houssammoallem.com` |
| **SSL certs** | `/etc/nginx/ssl/houssammoallem.com.{pem,key}` |
| **Documentation** | `~/houssammoallem-com/docs/` |

---

## 3. Editing the Website

Just tell me what to change:
- *"Change the hero headline"* → I edit `index.html`
- *"Add a new case study"* → I create HTML in `projects/`
- *"Update About page"* → I edit `about.html`
- *"Change styling"* → I edit `styles.css`

---

## 4. Deploying After GitHub Edits

If code is edited on GitHub directly:

```bash
cd ~/houssammoallem-com
GIT_SSH_COMMAND="ssh -i ~/.ssh/id_ed25519_vocab -o IdentitiesOnly=yes" git pull
sudo cp -r * /var/www/houssammoallem/
```

Or just ask me: *"Pull from GitHub and deploy"*

---

## 5. Common Commands

| Task | Command |
|------|---------|
| Check site status | `curl -s -o /dev/null -w "%{http_code}" https://houssammoallem.com/` |
| View nginx logs | `sudo tail -f /var/log/nginx/access.log` |
| Reload nginx | `sudo systemctl reload nginx` |
| Test nginx config | `sudo nginx -t` |
| Check SSL expiry | `openssl s_client -connect houssammoallem.com:443 -servername houssammoallem.com </dev/null 2>/dev/null \| openssl x509 -noout -enddate` |
| Push to GitHub | From `~/houssammoallem-com/`: SSH push command |

---

## 6. Troubleshooting

| Problem | Check |
|---------|-------|
| Site down / 530 | Verify nginx running: `systemctl status nginx`, check DNS A record = `13.140.134.57` |
| 403 Forbidden | File permissions: files must be `644`, readable by `www-data` |
| Changes not showing | Clear browser cache, Cloudflare "Purge Cache" |
| Mobile not updating | Toggle airplane mode (flushes DNS) |
| GitHub push fails | `ssh -i ~/.ssh/id_ed25519_vocab -T git@github.com` |
| SSL cert error | Check cert not expired: `openssl ... -enddate` |
