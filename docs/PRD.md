# Houssam Moallem Portfolio — Product Requirements Document

> **Version:** 1.1.0  
> **Date:** July 7, 2026  
> **Status:** Phase 2 Complete (Live, Full HTTPS, SEO optimized)  
> **Domain:** [houssammoallem.com](https://houssammoallem.com)

---

## Project Identity

| Key | Value |
|-----|-------|
| **Product Name** | Houssam Moallem Portfolio |
| **Domain** | `houssammoallem.com` |
| **GitHub Repo** | `github.com/hsmoallem/houssammoallem-com` |
| **Tech Stack** | Static HTML + CSS, nginx, Cloudflare Full (strict) |
| **Target Audience** | Recruiters, hiring managers, potential clients in Germany/EU |
| **Primary Goal** | Rank #1 on Google for "Houssam Moallem" |

---

## 1. Product Vision

A personal portfolio website that serves as the central hub for Houssam Moallem's professional identity online. The site presents product management expertise through case studies, credentials, and a clear narrative — making it easy for recruiters and clients to understand his value and get in touch.

---

## 2. Pages

### 2.1 Portfolio Home (`/`)

**Status:** ✅ Live

- Navigation bar (Case studies, Clients, About me, Get in touch)
- Hero section with status chip and intro paragraph
- Client/company grid (SevenSeas, Banxway, MCN, Pearson, Alef Education, Qatar MoE, Million Bridges)
- Case studies grid (5 projects)
- Credentials section (PMP, MBA, BA, Google UX)
- Contact section (email, LinkedIn, WhatsApp)

### 2.2 About Page (`/about.html`)

**Status:** ✅ Live

- Career narrative: graphic design → MBA → PMP → PM
- Quick facts sidebar (location, roles, experience, certifications, languages, tools)
- Inspirations and interests
- Contact section

### 2.3 Project Case Studies (`/projects/`)

**Status:** ✅ Live (5 pages)

| # | Title | Client | Status |
|---|-------|--------|--------|
| CS-01 | CAAS Platform: Admin & Cardholder Portals | SevenSeas | Live |
| CS-02 | CAAS Cardholder Application (PWA) | SevenSeas | Live |
| CS-03 | Admod Optimization | MCN | Delivered |
| CS-04 | Billing & Revenue Automation | MCN | Delivered |
| CS-05 | Credit Limit Management System | Fintech | Live |

---

## 3. Design Decisions

| Decision | Rationale |
|----------|-----------|
| **Static HTML (no framework)** | Fastest load, zero build step, easy editing |
| **Dark theme** | Modern, professional |
| **Google Fonts (Sora + IBM Plex)** | Clean typography, CDN-loaded |
| **Cloudflare Full (strict)** | End-to-end HTTPS, zero plain-text hops |
| **Origin Certificate** | Free from Cloudflare, 15-year validity |

---

## 4. SEO Strategy

| Phase | Action | Status |
|-------|--------|--------|
| 1 | Meta titles/descriptions, OG/Twitter tags | ✅ Done |
| 1 | Schema.org structured data | ✅ Done |
| 1 | sitemap.xml, robots.txt, canonical URLs | ✅ Done |
| 1 | HTTP → HTTPS redirect, www → root redirect | ✅ Done |
| 1 | Favicon | ✅ Done |
| 1 | Full (strict) SSL, end-to-end HTTPS | ✅ Done |
| 2 | Google Search Console submission | 🔴 Pending |
| 2 | Add domain to LinkedIn, GitHub, Framer | 🔴 Pending |
| 2 | Email security (SPF, DMARC) | 🔴 Pending |
| 3 | Rank #1 for "Houssam Moallem" | ⏳ In progress |

---

## 5. Roadmap

### Phase 1: MVP ✅ Complete
- [x] Portfolio home with case studies, clients, credentials, contact
- [x] About page with career story and quick facts
- [x] 5 project case studies
- [x] Cloudflare DNS + CDN + HTTPS (Full strict)
- [x] SEO metadata + structured data + sitemap

### Phase 2: Security & SEO ✅ Complete
- [x] Full (strict) SSL with Cloudflare Origin Certificate
- [x] TLS 1.2/1.3, HSTS, Always Use HTTPS
- [x] www → root redirect
- [x] Favicon

### Phase 3: Launch 🔴 Planned
- [ ] Google Search Console + sitemap submission
- [ ] Backlinks from LinkedIn, GitHub, Framer
- [ ] Email security (SPF, DMARC) or email setup (Zoho)
- [ ] Monitor ranking

### Phase 4: Content 🔮 Future
- [ ] Blog/Articles section
- [ ] PDF CV download
- [ ] Testimonials
- [ ] German language version
- [ ] More case studies

### Phase 5: Polish 🔮 Future
- [ ] Custom 404 page
- [ ] Dark/light mode toggle
- [ ] Privacy-friendly analytics
- [ ] Auto-deploy from GitHub (CI/CD)
