# Sizr — Precision-Fit Fashion

> **We don't make clothes for mannequins. We engineer them for the bodies that actually exist.**

---

## The Origin Story

It started with a frustration so simple it felt absurd: **why does every brand guess at sizes?**

Two engineers — one mechanical, one computer vision — stood in a fitting room in Lahore, watching a perfectly good shirt pull tight across shoulders that didn't match the pattern. The fabric was beautiful. The stitching was clean. The size tag said *Medium*. The body inside said *this doesn't work*.

That moment became a question: *what if clothing fit the way furniture does when it's custom-built?*

Not "close enough." Not "size up for comfort." Precisely. Intentionally. Without compromise.

---

## The Founders

**Ali Raza** — Computer Vision & Systems  
*Built the scanning pipeline. Obsesses over sub-millimetre proportion mapping. Still measures his own sleeves before bed.*

**Hassan Mahmood** — Mechanical Engineering & Materials  
*Sourced the fabrics. Negotiated with the mills. Knows the GSM of every bolt in the atelier by touch.*

They met at LUMS, lost touch, found each other again over a shared hatred of ill-fitting collars. Sizr is the result.

---

## The Philosophy

### Fit, Not Sizing
S/M/L is a statistical approximation from the 1940s. We use computer vision to map your proportions — every curve, every ratio, every asymmetry. Your clothes fit because they're built around your actual shape, not a letter on a tag.

### Material Integrity
300–400 GSM heavyweight fabrics that drape, move, and last. We source from Pakistan's finest mills — the same ones supplying luxury houses in Milan, London, New York. The cloth is the contract.

### No Compromise
Premium construction at honest prices. We cut the middlemen, not the quality. Every stitch is intentional. Every seam is earned.

---

## The First Drop

**Spring 2027** — a capsule of precision-fit essentials.

Heavyweight tees. Engineered shirts. Trousers that understand your seat and thigh. Each garment cut to your scan, sewn in Lahore, shipped to your door.

Early supporters join the **founding-fit cohort** — priority access, direct line to the founders, and a fit profile that evolves with you.

---

## The Technology

### The Scan
A browser-based computer vision pipeline. No app download. No special hardware. Stand in front of your phone camera for 40 seconds. We extract 47 body landmarks, compute your unique proportion matrix, and generate a digital pattern.

### The Pattern
Traditional grading scales a base pattern up and down. We don't grade. We generate — each pattern is a one-off, derived from your scan, adjusted for fabric behaviour, ease preferences, and the garment's intended drape.

### The Atelier
Lahore, Pakistan. Third-generation tailors. Industrial machines calibrated daily. Quality control at every station. The same hands that stitch for global luxury houses now stitch for you.

---

## This Repository

A single-file, zero-dependency landing page — the digital front door for the waitlist.

### What's Inside

```
index.html          # Complete landing page (HTML + CSS + JS)
assets/
  └── svgviewer-output.svg   # Brand lockup (SZ mark + wordmark + tagline)
```

### Features

- **Hero** — Full-bleed editorial imagery with Ken Burns drift, staggered entrance animation
- **Marquee** — Slow, masked brand-keyword strip (decorative)
- **About** — Framed atelier photograph, founder narrative
- **Principles** — Three ruled "plates" with outline numerals, hairline separators
- **Specs** — Measured stat row with tabular numerals
- **Editorial Break** — Full-bleed quote moment
- **Pre-Launch** — Status pill + email capture (validated, accessible, backend-ready)
- **Footer** — Structured brand, social, meta columns

### Design System: *Technical Editorial Precision*

| Role | Font | Purpose |
|------|------|---------|
| Display | **Bodoni Moda** | Fashion-editorial headlines, quotes, big numerals |
| Body | **Manrope** | Clean grotesque for paragraphs, UI copy |
| Technical | **Space Grotesk** | Labels, nav, buttons, spec rails — the engineering voice |

| Token | Value | Use |
|-------|-------|-----|
| `--ink` | `#0A0C0C` | Ground — near-black with cool cast |
| `--ink-2` | `#101313` | Elevated surfaces |
| `--ink-3` | `#171B19` | Hover states |
| `--bone` | `#F2EDE3` | Primary text, primary buttons |
| `--slate` | `#ABB3AD` | Secondary text (≥ 4.5:1 on ink) |
| `--ember` | `#FF5A3D` | Single accent — markers, focus, hover |
| `--hairline` | `rgba(242,237,227,.10)` | Structural rules, borders |

### Motion (all respect `prefers-reduced-motion`)

- 18s Ken Burns drift on hero image
- 42s marquee loop
- 2.4s status-pill pulse
- 0.8s cubic-bezier scroll reveals with stagger

### Accessibility

- `:focus-visible` on every interactive element (ember outline, 3px offset)
- Skip-to-content link
- Labeled email input with `aria-live` status region
- Semantic landmarks (`nav`, `main`, `section`, `footer`)
- Colour contrast ≥ 4.5:1 everywhere
- No emoji icons — SVG only

### JavaScript (vanilla, ~180 lines, one IIFE)

- Canvas-crop logo variants from single SVG source
- Hero image fade-in + Ken Burns trigger
- Staggered hero entrance
- Navbar glass transition on scroll
- IntersectionObserver scroll reveals
- Email validation + submit handler (backend stub)
- Zero dependencies, zero build step

---

## Getting Started

```bash
# No install. No build. Just open.
open index.html
# or serve it
npx serve .
# or
python -m http.server 8000
```

### Customise

| What | Where |
|------|-------|
| Hero image | `.hero-bg img src` (line ~120) |
| About image | `.about-img src` (line ~220) |
| Editorial image | `.editorial-break img src` (line ~270) |
| Launch window | `.status-pill` text (line ~250) |
| Social links | Footer `<a href="">` (lines ~300–305) |
| Email backend | `EMAIL HANDLER` section in `<script>` (line ~420) |

### Logo

The source `assets/svgviewer-output.svg` is a single dark-navy lockup. The script crops two regions at load:

```js
var LOGO_CROPS = [
  { id: 'navLogo',    top: 0.05, left: 0.36, height: 0.40, width: 0.28 }, // SZ mark
  { id: 'footerLogo', top: 0.50, left: 0.14, height: 0.32, width: 0.69 }, // wordmark
];
```

Replace the SVG → adjust these four numbers per crop → done.

---

## The Waitlist

The form posts to a `fetch('/api/waitlist', …)` stub. Wire your backend:

```js
fetch('/api/waitlist', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ email: val })
})
```

Success/error messages render in the `aria-live` region below the button.

---

## Browser Support

Modern evergreen browsers (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+).  
No polyfills. `IntersectionObserver`, `fetch`, `canvas`, CSS custom properties, `clamp()`, `aspect-ratio` — all baseline 2023+.

---

## The Name

**Sizr** — *size* + *er* (the agent that does the thing).  
Pronounced *sizer*. The 'z' is the engineer's mark.

---

## Contact

- **Email:** hello@sizr.shop
- **Instagram:** [@getsizr](https://instagram.com/getsizr)
- **TikTok:** [@getsizr](https://tiktok.com/@getsizr)

---

## License

Proprietary. All rights reserved.  
© 2026 Sizr — EST. 2025, Lahore · London

---

*Built by two engineers who were tired of "close enough."  
The first drop is coming. [Join the waitlist.](https://sizr.shop/#signup)*