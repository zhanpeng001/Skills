---
name: nuxt-frontend-design
description: Use when creating or substantially redesigning polished UI components, pages, layouts, landing pages, or application views in a Nuxt project using Vue, TypeScript, and Vite.
---

# Nuxt Frontend Design

## Purpose

Create distinctive production-ready interfaces whose design fits the product and whose implementation respects Nuxt conventions, SSR, accessibility, and performance.

## Workflow

### 1. Read the Project First

Inspect `package.json`, `nuxt.config.*`, application directories, `public/`, and styles before editing. Nuxt 4 defaults to `app/app.vue`, `app/pages/`, `app/layouts/`, `app/components/`, and `app/assets/`; Nuxt 3 or configured projects may use root-level equivalents. Follow the project.

Identify styling/tokens, reusable components, installed modules, themes/breakpoints, routing/layout conventions, and validation commands. Do not add UI, font, animation, or styling dependencies solely for convenience.

### 2. Choose a Direction

Translate audience and purpose into one coherent visual direction. For open-ended work, briefly state it before implementation. Select one memorable signature: typography, composition, material treatment, illustration, or focused motion.

Avoid generic dashboard grids, arbitrary gradients, invented copy, and decoration unrelated to context. Prefer configured or realistically loadable fonts and existing tokens; get spacing, hierarchy, and responsive composition right before effects.

### 3. Build for Nuxt

- Use Vue SFCs with `<script setup lang="ts">` where consistent with the repo.
- Type props, emits, models, data, and composable contracts.
- Put route/layout composition and reusable components in the project's detected Nuxt directories; honor auto-import and naming conventions.
- Use `NuxtLink` for internal navigation. Use `<NuxtImg>` or `<NuxtPicture>` only when the image module is installed or explicitly added for the task.
- Put files Vite should process in `assets/`; use `public/` for unchanged, stable-root-URL assets.
- Use `useSeoMeta` for page metadata when a page needs SEO/share presentation.
- Use `useFetch`/`useAsyncData` for initial SSR render data, `$fetch` for user-triggered requests, and `useState` for SSR-safe shared UI state.
- Keep SSR markup deterministic; isolate genuinely browser-only behavior.
- Put shared tokens or global effects in the existing style entrypoint; scope component-only styling locally.
- Prefer CSS for simple motion and respect `prefers-reduced-motion`.

### 4. Refine and Verify

Cover applicable loading, empty, error, active, disabled, hover, focus-visible, and dark-mode states. Check semantics, keyboard access, contrast, alt text, and narrow/wide layouts.

Run applicable lint, tests, build, and `nuxt typecheck` when supported; `nuxt build` does not type-check by default. Run `nuxt prepare` if generated types are missing. Check hydration warnings, asset paths, overflow, interactions, and bundle-heavy additions. Inspect substantial visual work in a browser or screenshot workflow.

## Common Mistakes

- Replacing an established design system instead of extending it coherently.
- Assuming root-level directories in a Nuxt 4 app, or moving a configured Nuxt 3 app to `app/` without a migration request.
- Assuming Tailwind, Nuxt UI, Pinia, Nuxt Image, or a font module exists without checking.
- Producing a static mockup that ignores Nuxt navigation, SEO, SSR data, hydration, component reuse, or typed data.
