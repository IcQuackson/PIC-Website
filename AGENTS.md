# Repository Guidelines

## Project Structure & Module Organization

This is a Hugo static site for the PIC project. Core site settings live in
`config/_default/`, while page content and blog posts live under
`content/english/` and `content/french/`. Section data is stored in
`data/en/` and `data/fr/` YAML files. Local template overrides are in
`layouts/`; theme templates and bundled plugins are in `themes/meghna-hugo/`.
Use `assets/` for Hugo pipeline assets such as CSS and images, and `static/`
for files copied directly into the published site. Generated output goes to
`public/` and should not be committed.

## Build, Test, and Development Commands

Install dependencies first:

```bash
npm install
```

Common commands:

```bash
npm run dev      # Start Hugo locally with fast render disabled.
npm run build    # Build the production site into public/.
npm run test     # Run Hugo in production/watch mode with template metrics.
```

After starting the server, verify the GitHub Pages subpath:

```bash
curl -I http://127.0.0.1:1313/PIC-Website/
```

Deployment is handled by `.github/workflows/main.yml` on pushes to `main`.
The workflow uses Hugo extended `0.147.2`, Go `1.24.3`, and Node `18.15.0`.

## Coding Style & Naming Conventions

Follow `.editorconfig`: UTF-8, LF line endings, final newline, trimmed trailing
whitespace, and 2-space indentation. Markdown files may keep intentional
trailing spaces. HTML templates are Hugo Go templates; `.prettierrc` configures
`prettier-plugin-go-template` for `*.html`. Keep content slugs lowercase and
date-prefixed for blog bundles, for example
`content/english/blog/2026-03-24-topic-name/index.md`.

## Testing Guidelines

There is no separate unit test suite. Validate changes by running
`npm run build` for a clean static build. For layout, navigation, or asset
changes, also run `npm run dev` and confirm the project subpath returns HTTP
`200`. Check both English and French content when editing shared templates,
menus, or data files.

## Commit & Pull Request Guidelines

Recent commits use short imperative subjects, often with prefixes such as
`enhance:` or `fix`. Keep subjects concise, for example
`fix: correct team member number` or `enhance: improve blog navigation`.
Pull requests should describe the change, list local validation commands, link
related issues or course tasks, and include screenshots for visible UI changes.

## Agent-Specific Instructions

When running shell commands as an agent in this repository, prefix commands with
`rtk`, for example `rtk npm run build`, to keep command output token-efficient.
