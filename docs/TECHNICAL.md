# Houssam Moallem Website — Technical Documentation

> **Server:** Contabo VPS (vmi3349165, Ubuntu 24.04)  
> **IP:** 13.140.134.57  
> **Domain:** houssammoallem.com  
> **Last Updated:** July 6, 2026

---

## 1. Architecture

```
┌──────────┐     HTTPS      ┌──────────────┐     HTTP :80     ┌───────────────┐
│ Visitor  │ ──────────────▶ │  Cloudflare  │ ───────────────▶ │  Your Server  │
│ (Browser)│ ◀────────────── │  (CDN/DNS)   │ ◀─────────────── │  nginx        │
└──────────┘                 └──────────────┘                  │  /var/www/... │
                                                               └───────────────┘
```

| Layer | What | Detail |
|-------|------|--------|
| **DNS** | Cloudflare | `houssammoallem.com` A → `13.140.134.57` (proxied) |
| **CDN / SSL** | Cloudflare | Flexible SSL (browser↔CF encrypted, CF↔origin plain HTTP) |
| **Web Server** | nginx 1.24.0 | Serves static files from `/var/www/houssammoallem/` |
| **Host** | Contabo VPS | Ubuntu 24.04, AMD EPYC 6-core, 11 GB RAM, 193 GB SSD |

---

## 2. Domain & DNS (Cloudflare)

### DNS Records

| Type | Name | Content | Proxy | TTL |
|------|------|---------|-------|-----|
| A | `@` (houssammoallem.com) | `13.140.134.57` | Proxied (orange) | Auto |
| A | `www` | `13.140.134.57` | Proxied (orange) | Auto |

### SSL/TLS

- **Mode:** Flexible (Cloudflare ↔ browser: HTTPS encrypted, Cloudflare ↔ origin: HTTP port 80)
- **Always Use HTTPS:** ON
- **HTTP Strict Transport Security (HSTS):** OFF (not needed with Flexible mode)

### Common Issues

| Error | Cause | Fix |
|-------|-------|-----|
| **530** | Cloudflare can't reach origin | Check A record points to correct IP; check nginx is running |
| **1016** | Origin DNS error (www subdomain) | Use A record for www instead of CNAME to root |
| **DNS cache on mobile** | Old record cached | Toggle airplane mode, clear browser cache |

---

## 3. nginx Configuration

**Config file:** `/etc/nginx/sites-available/houssammoallem.com`  
**Symlinked from:** `/etc/nginx/sites-enabled/houssammoallem.com`

```nginx
server {
    listen 80 default_server;
    server_name houssammoallem.com www.houssammoallem.com;
    root /var/www/houssammoallem;
    index index.html;
}
```

### Useful Commands

```bash
# Test config
sudo nginx -t

# Reload (no downtime)
sudo systemctl reload nginx

# Restart
sudo systemctl restart nginx

# Check status
systemctl status nginx

# View logs
sudo tail -f /var/log/nginx/access.log
sudo tail -f /var/log/nginx/error.log
```

---

## 4. File Structure on Server

```
/var/www/houssammoallem/
├── index.html          ← Coming Soon page (live root)
├── robots.txt          ← Crawl directives
├── sitemap.xml         ← All page URLs for search engines
└── beta/
    ├── index.html      ← Full portfolio homepage
    ├── about.html      ← About page
    ├── styles.css      ← Shared stylesheet
    └── projects/
        ├── sevenseas-caas-platform.html
        ├── sevenseas-cardholder-app.html
        ├── admod-mcn.html
        ├── billing-revenue-automation.html
        └── credit-limit-management.html
```

**Permissions:** All files owned by `root:root`, mode `644` (readable by nginx `www-data`).

---

## 5. Deployment Workflow

```
┌─────────────────┐      git push       ┌──────────┐      git pull       ┌───────────────┐
│  Local editing   │ ─────────────────▶ │  GitHub  │ ◀───────────────── │  Server repo  │
│  (any machine)   │                    │          │                    │  ~/houss...   │
└─────────────────┘                    └──────────┘                    └───────┬───────┘
                                                                              │
                                                                     sudo cp -r *
                                                                              │
                                                                              ▼
                                                                     /var/www/houssammoallem/
                                                                         (live site)
```

### Deploy from server repo to live site

```bash
cd ~/houssammoallem-com && git pull && sudo cp -r * /var/www/houssammoallem/
```

### Deploy a single file

```bash
sudo cp ~/houssammoallem-com/index.html /var/www/houssammoallem/
```

**Note:** No build step — the site is static HTML/CSS. Changes are instant after copy.

---

## 6. Git Setup

| Key | Value |
|-----|-------|
| **Repository** | `github.com/hsmoallem/houssammoallem-com` |
| **SSH Key** | `~/.ssh/id_ed25519_vocab` (Ed25519) |
| **Auth** | SSH to `git@github.com` |
| **Branch** | `master` |
| **Local Repo** | `~/houssammoallem-com/` |

### Git commands (from `~/houssammoallem-com/`)

```bash
# Push with the correct SSH key
GIT_SSH_COMMAND="ssh -i ~/.ssh/id_ed25519_vocab -o IdentitiesOnly=yes" git push

# Pull latest
GIT_SSH_COMMAND="ssh -i ~/.ssh/id_ed25519_vocab -o IdentitiesOnly=yes" git pull

# Check status
git status
git log --oneline -5
```

---

## 7. SEO Technical Details

### Meta Tags (on every page)

```html
<!-- canonical URL -->
<link rel="canonical" href="https://houssammoallem.com/...">

<!-- Open Graph (Facebook, LinkedIn, etc.) -->
<meta property="og:title" content="...">
<meta property="og:description" content="...">
<meta property="og:url" content="...">
<meta property="og:type" content="website">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="...">
<meta name="twitter:description" content="...">
```

### Structured Data

**Landing page** (`index.html`):
```json
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Houssam Moallem",
  "jobTitle": "Product Manager & Product Owner",
  "url": "https://houssammoallem.com/",
  "address": {"addressLocality": "Dessau-Roßlau", "addressCountry": "DE"},
  "sameAs": ["https://linkedin.com/in/moallem", "https://github.com/hsmoallem"]
}
```

**Beta portfolio** (`beta/index.html`): Same Person schema.  
**About page** (`beta/about.html`): `@type: AboutPage`.

### robots.txt

```
User-agent: *
Allow: /
Sitemap: https://houssammoallem.com/sitemap.xml
```

### sitemap.xml

Lists all 8 pages with `lastmod`, `changefreq`, and `priority`. Generated manually — update when pages are added or removed.

---

## 8. Security

| Layer | Status |
|-------|--------|
| HTTPS | ✅ Cloudflare edge (Flexible SSL) |
| DDoS protection | ✅ Cloudflare (proxied DNS) |
| Server firewall | ⚠️ UFW inactive (only nginx port 80 exposed) |
| SSH | ✅ Key-only authentication |
| File permissions | ✅ `644` for web files, root-owned |
| fail2ban | ✅ Active |

---

## 9. Fonts

Loaded from Google Fonts CDN in `<head>`:

```html
<link href="https://fonts.googleapis.com/css2?
  family=Sora:wght@400;600;700&
  family=IBM+Plex+Sans:wght@400;500;600&
  family=IBM+Plex+Mono:wght@400;500&
  display=swap" rel="stylesheet">
```

| Font | Usage |
|------|-------|
| **Sora** (400, 600, 700) | Headings, brand name |
| **IBM Plex Sans** (400, 500, 600) | Body text, descriptions |
| **IBM Plex Mono** (400, 500) | Code, tags, metadata |

<style>
  .key-point { background: #ff6347; padding: 2px 6px; border-radius: 3px; color: white; }
</style>

---

## 10. Quick Reference Commands

```bash
# Check if website is up
curl -s -o /dev/null -w "%{http_code}" https://houssammoallem.com/

# Check nginx status
systemctl status nginx

# View nginx access log (Cloudflare IPs will show)
sudo tail -f /var/log/nginx/access.log

# Deploy after git changes
cd ~/houssammoallem-com && git pull && sudo cp -r * /var/www/houssammoallem/

# Check DNS from different resolvers
dig +short houssammoallem.com @1.1.1.1
dig +short houssammoallem.com @8.8.8.8
```
