# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Owl and Pillar is an AI-powered college matching service landing page built with Astro. This is a static site with no backend functionality, currently in beta stage.

## Commands

### Development
- `npm run dev` - Start development server (default: http://localhost:4321)
- `npm run build` - Build for production (outputs to `dist/`)
- `npm run preview` - Preview production build locally

### Deployment
The site is configured for GitHub Pages deployment with custom domain owlandpillar.com. To deploy:
1. Run `npm run build`
2. Deploy the `dist/` folder to GitHub Pages
3. CNAME file in `public/` ensures custom domain configuration

## Architecture

### Structure
- **Single Page Application**: All content is in `/src/pages/index.astro`
- **No Component Architecture**: Everything is inline in the index file
- **Static Only**: No JavaScript functionality, pure HTML/CSS
- **No Backend**: Email signup form has no action endpoint

### Styling
- **Inline CSS**: All styles are in the index.astro file
- **Color Scheme**:
  - Primary Blue: #003366
  - Primary Gold: #FFB81C  
  - Secondary Blue: #0051A5
- **Typography**:
  - Headings: Playfair Display (serif)
  - Body: Inter (sans-serif)
- **Responsive**: Mobile breakpoint at 768px using CSS Grid

### Key Sections in index.astro
1. **Meta/Head** (lines 1-50): SEO tags, fonts, favicon
2. **Global Styles** (lines 50-450): All CSS including animations
3. **Header** (lines 450-470): Logo and beta badge
4. **Hero Section** (lines 470-500): Main value prop and email signup
5. **Features Grid** (lines 500-550): Target/Reach/Safety schools
6. **Pricing Cards** (lines 550-650): Three pricing tiers
7. **Footer** (lines 650-end): Copyright and tagline

## Important Considerations

### Accessibility
The site implements WCAG AA compliance with:
- Semantic HTML structure
- ARIA labels on all form inputs
- Screen reader-only content (`.sr-only` class)
- Focus indicators for keyboard navigation
- Reduced motion support (`prefers-reduced-motion`)
- High contrast color ratios

### Current Limitations
- Email signup form is non-functional (no backend endpoint)
- No component reusability - all code is in one file
- No testing framework or tests
- No environment variables or configuration files needed

### When Making Changes
1. Maintain the existing color scheme and typography for brand consistency
2. Ensure any new features maintain WCAG AA accessibility standards
3. Test responsive design at mobile (< 768px) and desktop breakpoints
4. Keep the single-file architecture unless refactoring is explicitly requested