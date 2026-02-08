# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Promotional single-page website for **ПолиграфФ** (Poligraff), a Russian printing company specializing in self-adhesive label production via flexographic printing. The site showcases services, capabilities, and provides contact information for sales manager Мария Истомина.

**Language:** Russian (lang="ru"). All user-facing text is in Russian.

## Architecture

This is a **zero-dependency, single-file static site**:

- `index.html` — The entire site (CSS, HTML, JS) in one file (~593 lines)
  - **Lines ~10–371:** Embedded `<style>` block with all CSS
  - **Lines ~374–540:** HTML markup (hero, stats, services, capabilities, CTA, contact card, footer)
  - **Lines ~542–591:** `<script>` block with `saveContact()` vCard generator
- `qr/` — QR code PNG images (site link, vCard)

## Running Locally

No build step. Serve static files with any HTTP server:

```bash
python3 -m http.server
# or: npx serve
```

Then open `http://localhost:8000` (or whichever port).

## Design System

CSS variables defined in `:root`:
- `--primary: #1a237e` (dark blue), `--accent: #ff6f00` (orange)
- Font: Google Fonts "Inter" (400, 500, 600, 700, 800)
- Mobile-first responsive layout (max-width container ~480px)
- Inline SVG icons throughout (no icon library)

## Key Functionality

- **vCard download:** `saveContact()` generates and downloads `PoligraffF_Istomina.vcf` with contact details
- **Contact methods:** Phone (+79652974401), email (istomina@poligraff.ru), WhatsApp link
- **Animations:** CSS `fadeUp` keyframe for scroll-in effects

## Working With This Codebase

- All changes happen in `index.html` — there are no separate CSS/JS files to update
- When modifying styles, use existing CSS variables rather than hardcoded colors
- Inline SVGs are used for all icons; keep them inline (no external icon files)
- The site targets mobile-first visitors; test responsive behavior at narrow widths
