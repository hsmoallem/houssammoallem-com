# Houssam Moallem Website — Technical Documentation

> **Server:** Contabo VPS (vmi3349165, Ubuntu 24.04)  
> **IP:** 13.140.134.57  
> **Domain:** houssammoallem.com  
> **Last Updated:** July 7, 2026

---

## 1. Architecture

```
┌──────────┐     HTTPS      ┌──────────────┐     HTTPS :443    ┌───────────────┐
│ Visitor  │ ──────────────▶ │  Cloudflare  │ ────────────────▶ │  Your Server  │
│ (Browser)│ ◀────────────── │  (CDN/DNS)   │ ◀──────────────── │  nginx        │
└──────────┘                 │ Full (strict)│                   │  TLS 1.2/1.3  │
                             └──────────────┘                   │  /var/www/... │
                                                                └───────────────┘
```

| Layer | What | Detail |
|-------|------|--------|
| **DNS** | Cloudflare | `houssammoallem.com` A → `13.140.134.57` (proxied) |
| **CDN / SSL** | Cloudflare | Full (strict) — end-to-end HTTPS |
| **Web Server** | nginx 1.24.0 | Port 80 → 301 redirect, Port 443 → TLS 1.2/1.3 |
| **Host** | Contabo VPS | Ubuntu 24.04, AMD EPYC 6-core, 11 GB RAM |

---

## 2. Domain & DNS (Cloudflare)

### DNS Records

| Type | Name | Content | Proxy | TTL |
|------|------|---------|-------|-----|
| A | `@` | `13.140.134.57` | Proxied (orange) | Auto |
| A | `www` | `13.140.134.57` | Proxied (orange) | Auto |

### SSL/TLS Settings

| Setting | Value |
|---------|-------|
| SSL/TLS mode | **Full (strict)** |
| Always Use HTTPS | ON |
| Minimum TLS Version | 1.2 |
| HSTS | Enabled (6 months, include subdomains) |
| Origin Certificate | Cloudflare Origin CA (RSA 2048, 15 years) |

### Page Rules

| URL | Action |
|-----|--------|
| `www.houssammoallem.com/*` | 301 → `https://houssammoallem.com/$1` |

---

## 3. nginx Configuration

**File:** `/etc/nginx/sites-available/houssammoallem.com`

```nginx
# HTTP → HTTPS redirect
server {
    listen 80 default_server;
    server_name houssammoallem.com www.houssammoallem.com;
    return 301 https://houssammoallem.com$request_uri;
}

# HTTPS
server {
    listen 443 ssl;
    server_name houssammoallem.com www.houssammoallem.com;

    ssl_certificate /etc/nginx/ssl/houssammoallem.com.pem;
    ssl_certificate_key /etc/nginx/ssl/houssammoallem.com.key;
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers HIGH:!aNULL:!MD5;

    root /var/www/houssammoallem;
    index index.html;
}
```

---

## 4. File Structure

```
/var/www/houssammoallem/
├── index.html          ← Portfolio home
├── about.html          ← About page
├── styles.css          ← Shared stylesheet
├── favicon.ico         ← Browser tab icon
├── robots.txt          ← Crawl directives
├── sitemap.xml         ← All pages for indexing
└── projects/           ← 5 case studies
```

---

## 5. Git Setup

| Key | Value |
|-----|-------|
| **Repository** | `github.com/hsmoallem/houssammoallem-com` |
| **SSH Key** | `~/.ssh/id_ed25519_vocab` |
| **Branch** | `master` |
| **Local Repo** | `~/houssammoallem-com/` |

---

## 6. Quick Reference

```bash
# Check website
curl -s -o /dev/null -w "%{http_code}" https://houssammoallem.com/

# Test nginx config
sudo nginx -t && sudo systemctl reload nginx

# Deploy from repo
cd ~/houssammoallem-com && git pull && sudo cp -r * /var/www/houssammoallem/

# Push to GitHub
cd ~/houssammoallem-com
GIT_SSH_COMMAND="ssh -i ~/.ssh/id_ed25519_vocab -o IdentitiesOnly=yes" git push

# Check SSL cert
openssl s_client -connect houssammoallem.com:443 -servername houssammoallem.com </dev/null 2>/dev/null | openssl x509 -noout -dates
```

---

## 7. Security

| Layer | Status |
|-------|--------|
| HTTPS edge (CF ↔ visitor) | ✅ Cloudflare |
| HTTPS origin (CF ↔ server) | ✅ Full (strict) |
| TLS version | ✅ 1.2/1.3 only |
| HSTS | ✅ Enabled |
| HTTP → HTTPS redirect | ✅ 301 |
| www → root redirect | ✅ 301 |
| UFW firewall | ✅ Active (ports: 22, 80, 443, 3001, 9000) |
| SSH | ✅ Key-only auth |
| fail2ban | ✅ Active |
| unattended-upgrades | ✅ Active |
