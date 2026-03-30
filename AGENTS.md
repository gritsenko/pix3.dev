# AGENTS.md - Pix3 Development Guide

## Project Overview

Pix3 is a landing page website for a WebGL 3D playable ads engine. The project consists of static HTML, CSS, and media assets. It uses Tailwind CSS via CDN and is deployed to GitHub Pages.

## Project Structure

```
pix3dev/
├── index.html          # Main landing page
├── styles.css          # Custom CSS styles
├── media/              # Images and assets
│   ├── splash-logo.png
│   ├── editor-interface.jpg
│   └── ...
└── .github/
    └── workflows/
        └── static.yml  # GitHub Pages deployment workflow
```

## Build / Development Commands

This is a **static site** - no build process required.

### Running Locally

Simply open `index.html` in a browser, or use a local server:

```bash
# Using Python
python -m http.server 8000

# Using npx (if available)
npx serve
```

### Deployment

The site automatically deploys to GitHub Pages on push to main branch via the workflow in `.github/workflows/static.yml`.

To manually trigger deployment:
1. Go to GitHub Actions tab
2. Select "Deploy static content to Pages"
3. Click "Run workflow"

### Testing

**No tests exist** for this static site. If tests are added in the future, run them with:

```bash
npm test              # Run all tests
npm test -- --grep "pattern"  # Run tests matching pattern
```

## Code Style Guidelines

### General Principles

- Keep changes minimal and focused
- Maintain the dark theme aesthetic (primary color: `#fbcc48` yellow, background: `#0e0e10`)
- Preserve semantic HTML structure
- Ensure responsive design works on mobile/desktop

### HTML Guidelines

1. **Doctype & Structure**: Use HTML5 doctype, maintain proper head/body structure
2. **Accessibility**: Include alt text for all images, use semantic elements (nav, section, footer)
3. **Tailwind Classes**: Use Tailwind utility classes from the CDN configuration in the `<script id="tailwind-config">` tag
4. **Custom Colors**: Use the custom color palette defined in tailwind.config (see lines 44-95 of index.html)
5. **Font Families**: Use `font-headline` (Space Grotesk) for headings, `font-body` (Inter) for body text

### CSS Guidelines

- Place custom styles in `styles.css`
- Avoid duplicating Tailwind utility classes
- Use CSS custom properties sparingly if needed
- Maintain the dark theme colors from the design system

### JavaScript Guidelines

- Inline JavaScript is acceptable for simple interactions
- Use vanilla JavaScript - no frameworks
- Keep scripts minimal and performant
- Place external scripts (analytics, etc.) in the head as deferred

### Image & Media Guidelines

- Optimize images before adding to media/ folder
- Use appropriate formats: JPG for photos, PNG for graphics with transparency
- Include descriptive alt text for accessibility
- Keep file sizes reasonable for fast loading

### Git & Commit Guidelines

- Create descriptive commit messages
- Keep commits focused and atomic
- Push to main branch triggers automatic deployment

### Error Handling

- Ensure all external CDN links are valid (fonts, Tailwind, analytics)
- Test locally before committing
- Verify all images load correctly

## External Dependencies

- **Tailwind CSS**: https://cdn.tailwindcss.com (loaded via CDN with forms and container-queries plugins)
- **Google Fonts**: Space Grotesk, Inter, Material Symbols Outlined
- **Yandex Metrika**: Analytics tracking (line 110-119 of index.html)

## Common Tasks

### Adding a New Section

1. Add HTML markup in `index.html` using appropriate semantic element (`<section>`, `<div>`, etc.)
2. Apply Tailwind classes for styling
3. Use custom colors from the theme (`bg-surface`, `text-primary`, etc.)
4. Test responsive behavior

### Updating Styles

1. For Tailwind-based styles: Add classes to HTML elements
2. For custom CSS: Edit `styles.css`
3. For new Tailwind utilities: Update the tailwind.config script in index.html

### Adding Images

1. Place optimized image in `media/` folder
2. Reference with relative path: `src="media/filename.ext"`
3. Always include descriptive alt text

## Notes for AI Agents

- This is a simple static site - avoid over-engineering solutions
- No TypeScript, no React, no build tools needed
- The tailwind.config is embedded in index.html (not a separate file)
- Changes to index.html or styles.css will be deployed automatically on push to main
