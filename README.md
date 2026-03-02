# PIC Website

Website for the project **Aerial-Ground Mesh Networking System for Wilderness Search and Rescue**.

## Stack
- Hugo (extended) `v0.147.2`
- Go `v1.24.3`
- Node.js (npm scripts for setup/build)

## Repository Layout
- `config/` Hugo configuration
- `content/` site pages/posts
- `layouts/` templates
- `assets/` pipeline assets
- `static/` static files copied as-is
- `themes/meghna-hugo/` theme
- `docs/README.md` original upstream theme README

## Local Development
1. Install Hugo extended, Go, and Node.js.
2. Install dependencies:
```bash
npm install
```
3. Start local server:
```bash
npm run dev
```
4. Verify site is up (must return 200):
```bash
curl -I http://127.0.0.1:1313/PIC-Website/
```

## Production Build
```bash
npm run build
```
Generated output goes to `public/`.

## GitHub Pages Deployment
Deployment is handled by GitHub Actions workflow:
- `.github/workflows/main.yml`

Trigger:
- Push to `main`

Required GitHub setting:
- Repository Settings -> Pages -> **Source: GitHub Actions**

Published URL:
- `https://icquackson.github.io/PIC-Website/`

## Team Conventions
- Keep source content committed (`content`, `layouts`, `assets`, `config`, `themes`).
- Do not commit generated output (`public/`, `resources/`, local tooling caches).
- Before pushing, verify local page returns HTTP 200 on the project subpath.
