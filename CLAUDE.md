# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static web presentation for a Learning Management System (LMS) module for Ru.di SNC, built as part of the GiveMeHive platform by STIIP. The project showcases a comprehensive proposal for an integrated LMS platform specialized in HACCP and workplace safety training, with multi-user access management, digital document repository, and automated expiration tracking.

## Project Structure

- **index.html** - Main entry point with tab navigation (Overview, Roadmap Sviluppo, Demo)
- **views/** - Contains HTML content loaded dynamically for each tab:
  - `overview-content.html` - LMS project description, GiveMeHive integration, problem/solution analysis, workflow, course categories, ROI
  - `analysis-content.html` - Development roadmap with 5 weekly sprints detailed plan, deliverables, and marketing automation integration
  - `demo-content.html` - Comprehensive UI mockups: admin backoffice, client portal, mobile employee interface, video player, quizzes, certificates, document management
- **assets/** - Static resources:
  - `css/styles.css` - Custom styles including brand colors and component styles
  - `js/main.js` - Empty placeholder file
  - `js/tabs.js` - Tab switching functionality
  - `image/` - Contains favicon
- **env.json** - Configuration for analysis expiration date

## Key Architecture Decisions

### Tab-based Content Loading
The application uses a client-side dynamic content loading system:
1. On page load, `index.html` fetches `env.json` to check expiration
2. If expired, displays contact message
3. If valid, loads `views/overview-content.html` by default
4. Tab buttons (Overview, Roadmap Sviluppo, Demo) trigger fetches to load corresponding view files
5. Content focuses on LMS platform for HACCP and workplace safety training

### Expiration System
The `env.json` file controls content visibility:
- `analysisExpired`: boolean flag
- `expirationDate`: ISO date string
- When expired, entire main content is replaced with contact form

## Styling System

The design uses:
- **Tailwind CSS 2.2.19** (CDN) for utility classes
- **Custom brand color**: `#FCD415` (yellow) defined in CSS variables
- **Material Icons** for iconography
- Responsive design with mobile-first approach
- Fixed header (top) and footer (bottom)

## Development Workflow

### Local Development
Since this is a static site, simply open `index.html` in a browser or use a local server:
```bash
python -m http.server 8000
# or
npx serve
```

### Modifying Content
- **Change tab content**: Edit files in `views/` directory
- **Update expiration**: Modify `env.json`
- **Style changes**: Edit `assets/css/styles.css`
- **Tab behavior**: Modify `assets/js/tabs.js`

### Adding New Tabs
1. Add button in `index.html` navigation with `data-tab="new-tab-id"`
2. Create `views/new-tab-id-content.html`
3. Add corresponding `<div id="new-tab-id" class="tab-content hidden"></div>` in main content area
4. Tab switching is handled automatically by existing JS

## Important Notes

- No build process required - pure static HTML/CSS/JS
- All content is client-side rendered
- External dependencies loaded via CDN (Tailwind, Google Fonts)
- The project showcases a SaaS module proposal, not the actual implementation
- GiveMeHive platform integration references are conceptual (CRM, digital quotes, electronic signature, email/WhatsApp marketing)

## Content Theme

The presentation describes a comprehensive LMS platform for Ru.di SNC with:
- Multi-user hierarchical access system (Admin Ru.di → Client Company → Employees)
- Complete e-learning system with video courses, interactive quizzes, and automated certificates
- Digital document management (DVR, HACCP manuals, registers, checklists)
- Automated expiration tracking and multi-channel notifications (email/WhatsApp)
- Full integration with existing GiveMeHive features (CRM, digital quotes, electronic signature, email/WhatsApp marketing)
- Course categories: HACCP, Workplace Safety, Fire Prevention, First Aid
- 5-week sprint-based agile implementation approach
- PDF certificate generation compliant with EU regulations (Reg. 852/2004, D.Lgs. 81/2008)
- Marketing automation for course renewals and customer reactivation
