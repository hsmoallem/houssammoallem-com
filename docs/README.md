# Houssam Moallem — Portfolio Website

> **Domain:** [houssammoallem.com](https://houssammoallem.com)  
> **Beta:** [houssammoallem.com/beta/](https://houssammoallem.com/beta/)  
> **GitHub:** [github.com/hsmoallem/houssammoallem-com](https://github.com/hsmoallem/houssammoallem-com)  
> **Status:** Live  
> **Last Updated:** July 6, 2026

---

## Overview

Personal portfolio website for Houssam Moallem — PMP and MBA certified Product Manager and Product Owner based in Germany. The site serves as the primary online presence for job hunting, personal branding, and showcasing product management case studies.

---

## Features

- 🏠 **Coming Soon Landing Page** — Minimal dark-themed page with name, role, badges, and links. Includes a "View Beta" button to the full portfolio.
- 📋 **Full Portfolio (Beta)** — Multi-page portfolio with case studies, client list, credentials, and contact section.
- 👤 **About Page** — Career journey, quick facts, certifications, methodologies, and contact.
- 📂 **5 Case Studies** — Detailed project breakdowns across fintech, enterprise, and EdTech.
- 🔍 **SEO Optimized** — Schema.org Person structured data, OG/Twitter meta tags, canonical URLs, sitemap.xml, robots.txt on every page.
- ⚡ **Cloudflare CDN** — Global edge caching, free HTTPS, DDoS protection.
- 📱 **Responsive** — Mobile-friendly design with Google Fonts (Sora, IBM Plex Sans, IBM Plex Mono).

---

## Project Info

| Key | Value |
|-----|-------|
| **Domain** | `houssammoallem.com` |
| **Hosting** | Contabo VPS (Ubuntu 24.04, 13.140.134.57) |
| **Web Server** | nginx 1.24.0 |
| **DNS / CDN** | Cloudflare (proxied, Flexible SSL) |
| **Tech Stack** | Static HTML + CSS (no frameworks, no JavaScript framework) |
| **Fonts** | Google Fonts: Sora, IBM Plex Sans, IBM Plex Mono |
| **GitHub Repo** | `hsmoallem/houssammoallem-com` |
| **Files Location** | `/var/www/houssammoallem/` on server |
| **Local Repo** | `~/houssammoallem-com/` on server |

---

## Page Structure

```
houssammoallem.com/
├── index.html              ← Coming Soon landing (live)
├── robots.txt              ← Search engine crawl rules
├── sitemap.xml             ← All 8 pages for indexing
└── beta/
    ├── index.html          ← Full portfolio (case studies, clients, credentials)
    ├── about.html          ← Career story, quick facts, certifications
    ├── styles.css          ← All styling (shared across pages)
    └── projects/
        ├── sevenseas-caas-platform.html
        ├── sevenseas-cardholder-app.html
        ├── admod-mcn.html
        ├── billing-revenue-automation.html
        └── credit-limit-management.html
```

---

## SEO Implementation

| Element | Landing | Beta | About | Projects |
|---------|:-------:|:----:|:-----:|:--------:|
| Meta title | ✅ | ✅ | ✅ | ✅ |
| Meta description | ✅ | ✅ | ✅ | ✅ |
| Canonical URL | ✅ | ✅ | ✅ | ✅ |
| OG tags | ✅ | ✅ | ✅ | ✅ |
| Twitter cards | ✅ | ✅ | ✅ | ✅ |
| Schema.org | ✅ Person | ✅ Person | ✅ AboutPage | — |

SEO checklist to complete:
- [ ] Submit to Google Search Console
- [ ] Add `houssammoallem.com` to LinkedIn profile
- [ ] Add `houssammoallem.com` to GitHub profile
- [ ] Add link from `houssam.framer.website` to this domain

---

## Links

| Platform | URL |
|----------|-----|
| Website | [houssammoallem.com](https://houssammoallem.com) |
| Beta Portfolio | [houssammoallem.com/beta/](https://houssammoallem.com/beta/) |
| GitHub Repo | [github.com/hsmoallem/houssammoallem-com](https://github.com/hsmoallem/houssammoallem-com) |
| LinkedIn | [linkedin.com/in/moallem](https://linkedin.com/in/moallem) |
| Old Portfolio | [houssam.framer.website](https://houssam.framer.website/) |
