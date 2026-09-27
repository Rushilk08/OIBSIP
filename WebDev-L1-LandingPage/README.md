# Runova — Shoe Brand Landing Page

Runova is a fictional running shoe brand. This project is a static, responsive landing page for it, built with plain HTML5 and CSS3 — no frameworks, no JavaScript. It covers a sticky navigation bar, a hero section, several content sections (technology, stats, product lineup, testimonials, FAQ), and a footer, all styled with a consistent dark editorial colour palette and full mobile responsiveness.

**Live site:** https://rushilk08.github.io/OIBSIP/WebDev-L1-LandingPage

## Features

- Sticky navigation bar with 5 links (Collection, Technology, Compare, Stories, FAQ)
- Hero section with headline, subheadline, CTA button, product photo, and a spec data row
- Five distinct content sections: Technology, Measured/Stats, Collection, Stories, FAQ
- Product lineup with real photography, pricing, and per-model specs
- FAQ accordion built with native HTML `<details>/<summary>` — zero JavaScript
- Fully responsive layout (CSS Grid + Flexbox) down to small mobile widths
- Consistent monochrome + lime-accent colour palette across every section
- CSS-only material texture swatches in the Technology section (no extra image requests)

## Tech stack

- **HTML5** — semantic markup throughout
- **CSS3** — Flexbox, Grid, custom properties for theming and per-image sizing
- **Fonts** — Archivo (headings), Inter (body), Space Mono (spec labels), via Google Fonts
- No JavaScript

## Screenshots

| Desktop | Mobile |
|---|---|
|![Desktop View](README%20Images/Desktop%20view.png)|![Mobile View](README%20Images/Mobile%20view.jpg)|

## Output files

```
runova/
├── index.html      → the page markup
├── style.css        → all styling
├── README.md         → this file
└── images/
    ├── pulse3-hero.jpg
    ├── pulse3-studio.jpg
    ├── drift-trail.jpg
    └── court-high.jpg
```