# Cloud 8 Studio - AI Agent Instructions

## Architecture Overview
This is a minimal Node.js application serving a static single-page landing site for Cloud 8 Studio, a design agency. The app uses Express to serve files from the `/public` directory on port 8080 (or `process.env.PORT`).

- **Server**: `server.js` - Simple Express setup with `app.use(express.static("public"))`
- **Frontend**: `public/index.html` - Landing page with contact form
- **Assets**: `public/assets/` - Fonts (Wildborn), icons (SVG), logo
- **No backend logic**: Form submissions use `mailto:` to open email client

## Key Workflows
- **Local development**: Run `npm start` to start the server at http://localhost:8080
- **Deployment**: Use Dockerfile for containerized deployment (`FROM node:18-alpine`, exposes 8080)
- **No build step**: Static files served directly, no compilation or bundling

## Code Conventions
- **Modules**: Use ES modules (`import`/`export`), set `"type": "module"` in `package.json`
- **Styling**: Inline CSS in `<style>` tags within HTML, glassmorphism design with backdrop-filter
- **Fonts**: Custom Wildborn font loaded via `@font-face` from `assets/wildborn-*.otf`
- **Interactions**: Mouse-following backdrop animations using CSS custom properties and requestAnimationFrame
- **Form handling**: Client-side only, constructs `mailto:` URLs with encoded subject/body

## Patterns & Examples
- **Static serving**: All assets referenced relative to `/public` (e.g., `assets/logo.svg`)
- **Responsive design**: Uses `min(420px,92vw)` for card width, media queries for mobile
- **Color scheme**: CSS variables like `--ink`, `--glass`, gradients for ethereal look
- **Accessibility**: Proper alt texts, ARIA labels on social links

## Dependencies
- **Express**: Only runtime dependency for static file serving
- **No dev dependencies**: Minimal setup, no testing or linting tools

Focus on maintaining the clean, minimal architecture. Changes should preserve the glassmorphism aesthetic and static nature.