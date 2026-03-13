# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Bizkeremet (Бизкеремет) — a corporate website for an IT company based in Bishkek, Kyrgyzstan. Single-page site in Russian language (`lang="ru"`).

## Commands

- `npm run dev` — start dev server at localhost:4321
- `npm run build` — build static site to `./dist/`
- `npm run preview` — preview production build locally
- `docker compose up --build` — build and run via Docker (nginx on port 8086)

## Architecture

**Stack:** Astro 5 (static output) + React + Tailwind CSS v4 + Framer Motion

**Structure:**
- Single page (`src/pages/index.astro`) composed of section components
- `src/layouts/Layout.astro` — base HTML layout with Inter font, meta tags
- `src/components/*.astro` — page sections: Header, Hero, Services, Portfolio, Team, Contacts, Footer
- `src/components/ui/shape-landing-hero.tsx` — React component (client:load) for animated hero with Framer Motion geometric shapes
- `src/lib/utils.ts` — `cn()` utility (clsx + tailwind-merge)
- `src/styles/global.css` — Tailwind v4 config via `@theme` directive (custom colors, font)

**Key patterns:**
- Path alias: `@/*` maps to `./src/*`
- Tailwind v4 integrated via Vite plugin (`@tailwindcss/vite`), not PostCSS
- Custom theme tokens defined in `global.css` `@theme` block: `--color-primary`, `--color-secondary`, `--color-bg`, `--color-text`, etc.
- React islands used only where client interactivity is needed (hero animation); everything else is Astro components
- TypeScript strict mode (`astro/tsconfigs/strict`)

## Deployment

Multi-stage Docker build: Node 22 builds static files, nginx serves them. Container exposed on port 8086.
