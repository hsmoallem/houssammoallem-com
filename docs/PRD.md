# Houssam Moallem Portfolio — Product Requirements Document

> **Version:** 1.0.0  
> **Date:** July 6, 2026  
> **Status:** Phase 1 Complete (MVP Live), Phase 2 Planned  
> **Domain:** [houssammoallem.com](https://houssammoallem.com)

---

## Project Identity

| Key | Value |
|-----|-------|
| **Product Name** | Houssam Moallem Portfolio |
| **Domain** | `houssammoallem.com` |
| **GitHub Repo** | `github.com/hsmoallem/houssammoallem-com` |
| **Tech Stack** | Static HTML + CSS, nginx, Cloudflare CDN |
| **Target Audience** | Recruiters, hiring managers, potential clients in Germany/EU |
| **Primary Goal** | Rank #1 on Google for "Houssam Moallem" |

---

## 1. Product Vision

A personal portfolio website that serves as the central hub for Houssam Moallem's professional identity online. The site presents his product management expertise through case studies, credentials, and a clear narrative — making it easy for recruiters and clients to understand his value and get in touch.

**Core Value Proposition:** One URL that tells the full story — who Houssam is, what he's built, and why you should hire him.

---

## 2. Pages

### 2.1 Coming Soon Landing Page (`/`)

**Status:** ✅ Live

A minimal dark-themed page with:
- Name and role
- Skill badges (Product Management, UI/UX Design, Flutter, MBA/PMP)
- Links to Portfolio (Framer), LinkedIn, GitHub
- "View Beta" button linking to the full portfolio
- SEO metadata and Schema.org Person structured data

### 2.2 Full Portfolio Home (`/beta/`)

**Status:** ✅ Live

The main portfolio page containing:
- Navigation bar (Case studies, Clients, About me, Get in touch)
- Hero section with status chip, headline, and intro paragraph
- Client/company grid (SevenSeas, Banxway, MCN, Pearson, Alef Education, Qatar MoE, Million Bridges)
- Case studies grid (5 projects)
- Credentials section (PMP, MBA, BA Graphic Design, Google UX Foundations)
- Contact section with email, LinkedIn, WhatsApp

### 2.3 About Page (`/beta/about.html`)

**Status:** ✅ Live

- Career narrative: graphic design → MBA → PMP → product management
- Quick facts sidebar (location, work authorization, roles, experience, certifications, languages, methodologies, tools)
- Inspirations and interests
- Contact section

### 2.4 Project Case Studies (`/beta/projects/`)

**Status:** ✅ Live (5 pages)

| # | Title | Client | Status |
|---|-------|--------|--------|
| CS-01 | CAAS Platform: Admin & Cardholder Portals | SevenSeas | Live |
| CS-02 | CAAS Cardholder Application (PWA) | SevenSeas | Live |
| CS-03 | Admod Optimization: Streamlining Workflows | MCN | Delivered |
| CS-04 | Billing & Revenue Automation | MCN | Delivered |
| CS-05 | Credit Limit Management System | Fintech | Live |

---

## 3. Design Decisions

| Decision | Rationale |
|----------|-----------|
| **Static HTML (no framework)** | Fastest load time, zero build step, easy to edit, no dependencies |
| **Dark theme** | Modern, professional, good contrast |
| **Google Fonts (Sora + IBM Plex)** | Clean typography, loads from CDN (fast) |
| **Cloudflare CDN + Flexible SSL** | Free HTTPS, global edge caching, DDoS protection |
| **"Coming Soon" as main page** | Professional impression while beta portfolio is refined |
| **Beta at `/beta/`** | Can iterate freely without affecting main page |
| **Separate HTML files per project** | Each case study has its own URL (good for SEO) |
| **No JavaScript framework** | Keeps the site fast and maintainable with zero JS overhead |

---

## 4. SEO Strategy

| Phase | Action | Status |
|-------|--------|--------|
| 1 | Meta titles and descriptions on all pages | ✅ Done |
| 1 | OG and Twitter card tags on all pages | ✅ Done |
| 1 | Schema.org structured data (Person, AboutPage) | ✅ Done |
| 1 | sitemap.xml (8 URLs) | ✅ Done |
| 1 | robots.txt | ✅ Done |
| 1 | Canonical URLs on all pages | ✅ Done |
| 2 | Submit to Google Search Console | 🔴 Pending |
| 2 | Add domain to LinkedIn profile | 🔴 Pending |
| 2 | Add domain to GitHub profile | 🔴 Pending |
| 2 | Link from houssam.framer.website | 🔴 Pending |
| 3 | Get indexed and rank for "Houssam Moallem" | ⏳ In progress |

---

## 5. Roadmap

### Phase 1: MVP ✅ Complete

- [x] Coming Soon landing page
- [x] Full portfolio (beta) with 5 case studies
- [x] About page
- [x] Cloudflare DNS + CDN + HTTPS
- [x] SEO metadata on all 8 pages
- [x] sitemap.xml, robots.txt
- [x] GitHub repository

### Phase 2: Launch & SEO 🔴 Planned

- [ ] Submit to Google Search Console
- [ ] Backlinks from LinkedIn, GitHub, Framer
- [ ] Monitor ranking for "Houssam Moallem"
- [ ] Replace Coming Soon with full portfolio as main page
- [ ] Add favicon

### Phase 3: Content Expansion 🔮 Future

- [ ] Blog/Articles section (product management thought leadership)
- [ ] PDF download of CV/Resume
- [ ] Testimonials section
- [ ] More case studies
- [ ] German language version

### Phase 4: Polish 🔮 Future

- [ ] Custom 404 page
- [ ] Dark/light mode toggle
- [ ] Analytics (privacy-friendly, no Google Analytics)
- [ ] Auto-deploy from GitHub (CI/CD)
- [ ] Performance optimization (image compression, font self-hosting)

---

## 6. Competitor Analysis

Current Google results for "Houssam Moallem" (July 2026):

| # | Result | Domain Authority |
|---|--------|-----------------|
| 1 | houssam.framer.website | Medium (Framer subdomain) |
| 2 | github.com/hsmoallem | High |
| 3 | xing.com profile | High |
| 4 | lightroom.adobe.com | High |
| 5 | linkedin.com | Very High |

**Goal:** `houssammoallem.com` to reach #1 within 4 weeks of Search Console submission.
