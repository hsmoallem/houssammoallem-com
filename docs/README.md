# Houssam Moallem — Portfolio Website

> **Domain:** [houssammoallem.com](https://houssammoallem.com)  
> **GitHub:** [github.com/hsmoallem/houssammoallem-com](https://github.com/hsmoallem/houssammoallem-com)  
> **Status:** Live  
> **Last Updated:** July 7, 2026

---

## Overview

Personal portfolio website for Houssam Moallem — PMP and MBA certified Product Manager and Product Owner based in Germany. The site serves as the primary online presence for job hunting, personal branding, and showcasing product management case studies.

---

## Features

- 📋 **Portfolio Home** — Case studies grid, client list, credentials section, contact CTA
- 👤 **About Page** — Career journey, quick facts sidebar, certifications, methodologies
- 📂 **5 Case Studies** — Detailed project breakdowns across fintech, enterprise, and EdTech
- 🔍 **SEO Optimized** — Schema.org Person structured data, OG/Twitter meta tags, canonical URLs, sitemap.xml, robots.txt, favicon
- ⚡ **Cloudflare CDN** — Global edge caching, HTTPS via Cloudflare Origin Certificate (Full strict), DDoS protection
- 🔒 **End-to-End HTTPS** — Cloudflare Full (strict) mode, nginx with TLS 1.2/1.3, HSTS enabled
- 📱 **Responsive** — Mobile-friendly design with Google Fonts (Sora, IBM Plex Sans, IBM Plex Mono)

---

## Project Info

| Key | Value |
|-----|-------|
| **Domain** | `houssammoallem.com` |
| **Hosting** | Contabo VPS (Ubuntu 24.04, 13.140.134.57) |
| **Web Server** | nginx 1.24.0 (HTTP 80 → 301 HTTPS, TLS 1.2/1.3 on 443) |
| **DNS / CDN** | Cloudflare (proxied, Full strict SSL) |
| **Tech Stack** | Static HTML + CSS |
| **Fonts** | Google Fonts: Sora, IBM Plex Sans, IBM Plex Mono |
| **GitHub Repo** | `hsmoallem/houssammoallem-com` |
| **Server Path** | `/var/www/houssammoallem/` |
| **Local Repo** | `~/houssammoallem-com/` |

---

## Page Structure

```
houssammoallem.com/
├── index.html              ← Portfolio home (case studies, clients, credentials)
├── about.html              ← Career story, quick facts, certifications
├── styles.css              ← All styling
├── favicon.ico             ← Browser tab icon
├── robots.txt              ← Crawl directives
├── sitemap.xml             ← All 7 pages for indexing
└── projects/
    ├── sevenseas-caas-platform.html
    ├── sevenseas-cardholder-app.html
    ├── admod-mcn.html
    ├── billing-revenue-automation.html
    └── credit-limit-management.html
```

---

## SEO Implementation

| Element | Home | About | Projects |
|---------|:----:|:-----:|:--------:|
| Meta title + description | ✅ | ✅ | ✅ |
| Canonical URL | ✅ | ✅ | ✅ |
| OG + Twitter tags | ✅ | ✅ | ✅ |
| Schema.org | ✅ Person | ✅ AboutPage | — |

---

## Security

| Layer | Status |
|-------|--------|
| HTTPS (visitor ↔ Cloudflare) | ✅ Cloudflare edge |
| HTTPS (Cloudflare ↔ origin) | ✅ Full (strict) — Cloudflare Origin Certificate |
| TLS version | ✅ 1.2/1.3 only |
| HSTS | ✅ Enabled |
| HTTP → HTTPS redirect | ✅ 301 |
| www → root redirect | ✅ 301 |
| SPF | 🔴 Pending (if email not needed: `v=spf1 -all`) |
| DMARC | 🔴 Pending (`v=DMARC1; p=reject`) |

---

## Links

| Platform | URL |
|----------|-----|
| Website | [houssammoallem.com](https://houssammoallem.com) |
| GitHub Repo | [github.com/hsmoallem/houssammoallem-com](https://github.com/hsmoallem/houssammoallem-com) |
| LinkedIn | [linkedin.com/in/moallem](https://linkedin.com/in/moallem) |
| Old Portfolio | [houssam.framer.website](https://houssam.framer.website/) |
