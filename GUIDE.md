# Moonbeam Talent — Website Guide

## How to Run

```bash
npm run dev       # Start dev server at http://localhost:4321 (live reload)
npm run build     # Build for production (output in dist/)
npx serve dist    # Preview the built site locally
```

---

## Architecture Overview

This is an **Astro** static website. Astro takes `.astro` files (HTML + optional JS) and builds plain HTML/CSS/JS files ready for deployment.

```
src/
├── pages/          ← Each file = a page on the website
├── components/     ← Reusable pieces shared across pages
├── layouts/        ← The HTML wrapper (head, meta tags, etc.)
├── data/           ← Content data (testimonials, companies, contact info)
├── styles/         ← Global CSS (colors, fonts, spacing)
public/
├── img/            ← Images (logos, photos)
```

---

## Pages — `src/pages/`

Each `.astro` file here becomes a URL on the website. To edit a page, open the corresponding file and change the HTML content directly.

| File | URL | What it shows |
|------|-----|---------------|
| `index.astro` | `/` | Homepage (hero, services, about, testimonials, contact) |
| `about.astro` | `/about` | Nivedita's bio, story behind Moonbeam, why Moonbeam |
| `services/index.astro` | `/services` | Overview of all three services |
| `services/business.astro` | `/services/business` | End-to-End Talent Search and Talent RPO with pricing |
| `services/talent.astro` | `/services/talent` | Consulting Job Search Program (6 steps) |
| `openings.astro` | `/openings` | Job listings (Happlicant iframe embed) |
| `testimonials.astro` | `/testimonials` | All testimonials |
| `privacy-policy.astro` | `/privacy-policy` | Privacy policy (Usercentrics embed) |

**To add a new page:** Create a new `.astro` file in `src/pages/`. The file path becomes the URL automatically (e.g., `src/pages/blog.astro` → `/blog`).

---

## Components — `src/components/`

Reusable sections that appear across multiple pages. If you want to change the header, footer, or a section on the homepage, edit the component file.

| File | What it controls |
|------|-----------------|
| `Header.astro` | Navigation bar and menu links |
| `Footer.astro` | Footer (contact info, social links, copyright) |
| `Hero.astro` | Homepage hero section (title, subtitle, metrics) |
| `FeaturedServices.astro` | Homepage "For Businesses" and "For Professionals" cards |
| `AboutPreview.astro` | Homepage "Meet Nivedita" section with photo |
| `CompanyLogos.astro` | Homepage company logo row |
| `TestimonialsPreview.astro` | Homepage testimonials preview (shows first 4) |
| `ContactForm.astro` | Contact form and contact info cards |

---

## Data — `src/data/`

Content data separated from layout. Edit these to update testimonials, companies, or contact details without touching page files.

| File | What it contains |
|------|-----------------|
| `testimonials.ts` | All testimonials (name, role, company, text) |
| `companies.ts` | Company logos shown on homepage |
| `site.ts` | Phone, email, address, LinkedIn URL, Web3Forms API key |

---

## Styles — `src/styles/global.css`

All colors, fonts, spacing, and shared styles are defined here. The most important part is the CSS variables at the top:

```css
:root {
  --color-accent: #0891b2;     /* Main accent color (teal) */
  --color-primary: #0f172a;    /* Dark text/headings */
  --color-bg-soft: #f8fafc;    /* Light gray backgrounds */
  --font-sans: 'Inter', ...;   /* Main font */
}
```

Change these variables to update colors and fonts across the entire site.

---

## Layout — `src/layouts/Layout.astro`

The base HTML wrapper used by every page. Edit this to change:

- Page title format
- Meta tags and SEO description
- Fonts loaded from Google Fonts
- Favicon

---

## Images — `public/img/`

Static images copied as-is to the built site. Reference them in code as `/img/filename.jpg`.

| Folder | Contents |
|--------|----------|
| `public/img/logos/` | Company logos (Neurons, OYO, Curity, etc.) |
| `public/img/pic/` | Profile photos (Nivedita) |

To add a new image, drop it in `public/img/` and use `/img/yourfile.jpg` in any page or component.

---

## Quick Reference

| I want to... | Edit this file |
|--------------|----------------|
| Change page text | `src/pages/[page].astro` |
| Add/remove a testimonial | `src/data/testimonials.ts` |
| Change phone/email/address | `src/data/site.ts` |
| Change navigation links | `src/components/Header.astro` |
| Change footer links | `src/components/Footer.astro` |
| Change colors or fonts | `src/styles/global.css` |
| Add a new page | Create `src/pages/newpage.astro` |
| Add a new image | Drop in `public/img/` |
| Change meta tags or page title | `src/layouts/Layout.astro` |
