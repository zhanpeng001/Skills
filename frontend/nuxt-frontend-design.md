---
name: nuxt-frontend-design
description: Use when creating or substantially redesigning polished UI components, pages, layouts, landing pages, or application views in a Nuxt project using Vue, TypeScript, and Vite.
---

# Nuxt Frontend Design

## Purpose

Create distinctive, production-ready Nuxt interfaces with an intentional aesthetic point of view. Deliver real working Vue and TypeScript code whose visual ambition remains compatible with Nuxt conventions, SSR, accessibility, and performance.

## Workflow

### 1. Read the Project First

Inspect `package.json`, `nuxt.config.*`, application directories, `public/`, and styles before editing. Nuxt 4 defaults to `app/app.vue`, `app/pages/`, `app/layouts/`, `app/components/`, and `app/assets/`; Nuxt 3 or configured projects may use root-level equivalents. Follow the project.

Identify styling/tokens, reusable components, installed modules, themes/breakpoints, routing/layout conventions, and validation commands. Do not add UI, font, animation, or styling dependencies solely for convenience.

### 2. Form a Design Brief

Before coding, define:

- **Purpose:** What job does the interface do, and for whom?
- **Tone:** Choose an explicit aesthetic direction appropriate to the product, such as restrained editorial, industrial/utilitarian, luxury/refined, playful, organic, geometric, retro-futurist, brutalist, or cinematic.
- **Constraints:** Identify framework, existing design system, content, responsive, accessibility, performance, SSR, and asset/font restrictions.
- **Signature:** Decide the one memorable visual idea: an unusual typographic contrast, spatial rhythm, framing device, texture, color accent, illustration treatment, or orchestrated motion moment.

Commit to one direction and execute it precisely. Minimalism may be bold through proportion and detail; an expressive design still needs discipline. When the brief is open-ended, state the chosen direction and signature briefly before implementing.

### 3. Apply Frontend Aesthetics

#### Typography

Create hierarchy through font personality, scale, weight, line-height, and measure. When the project permits it, pair a distinctive display treatment with a readable body treatment. Do not reflexively introduce generic defaults or trendy fonts; first reuse configured fonts, brand assets, or realistically loadable licensed fonts without harming performance.

#### Color and Theme

Choose a cohesive palette with a clear dominant surface/text relationship and purposeful accents. Use existing tokens or CSS variables consistently. Avoid timid evenly distributed colors and clichéd gradients unrelated to the product. Respect existing light/dark theme behavior where present.

#### Motion and Interaction

Use motion to clarify state or create one high-impact moment, such as a controlled entrance sequence or meaningful hover transition, rather than scattering animation everywhere. Prefer CSS transitions and keyframes unless the repository already supports an appropriate motion tool. Always support `prefers-reduced-motion`, keyboard interaction, and stable layout.

#### Composition and Space

Avoid predictable template layouts when the content invites stronger composition. Consider asymmetry, overlap, layered hierarchy, deliberate negative space, framed density, or a controlled break from the grid. Responsive behavior must remain usable and intentional at narrow widths.

#### Atmosphere and Detail

Use backgrounds, borders, texture, light, shadow, pattern, imagery, or layered transparency only when they reinforce the direction. Details should create context and depth, not become arbitrary decoration or obscure content.

Avoid generic generated-looking results: interchangeable hero sections, default card grids, unconsidered type choices, fashionable but irrelevant gradients, and repeated motifs with no connection to the purpose.

### 4. Build for Nuxt

- Use Vue SFCs with `<script setup lang="ts">` where consistent with the repo.
- Type props, emits, models, data, and composable contracts.
- Put route/layout composition and reusable components in the project's detected Nuxt directories; honor auto-import and naming conventions.
- Use `NuxtLink` for internal navigation. Use `<NuxtImg>` or `<NuxtPicture>` only when the image module is installed or explicitly added for the task.
- Put files Vite should process in `assets/`; use `public/` for unchanged, stable-root-URL assets.
- Use `useSeoMeta` for page metadata when a page needs SEO/share presentation.
- Use `useFetch`/`useAsyncData` for initial SSR render data, `$fetch` for user-triggered requests, and `useState` for SSR-safe shared UI state.
- Keep SSR markup deterministic; isolate genuinely browser-only behavior.
- Put shared tokens or global effects in the existing style entrypoint; scope component-only styling locally.

### 5. Match Complexity to Direction

Build only the complexity the aesthetic requires. Refined minimal work needs exact spacing, type, contrast, and subtle states; expressive work can justify richer layers and motion when performance and accessibility remain controlled. A memorable design is coherent, not merely elaborate.

### 6. Refine and Verify

Cover applicable loading, empty, error, active, disabled, hover, focus-visible, and dark-mode states. Check semantics, keyboard access, contrast, alt text, and narrow/wide layouts.

Run applicable lint, tests, build, and `nuxt typecheck` when supported; `nuxt build` does not type-check by default. Run `nuxt prepare` if generated types are missing. Check hydration warnings, asset paths, overflow, interactions, and bundle-heavy additions. Inspect substantial visual work in a browser or screenshot workflow.

## Common Mistakes

- Replacing an established design system instead of extending it coherently.
- Assuming root-level directories in a Nuxt 4 app, or moving a configured Nuxt 3 app to `app/` without a migration request.
- Assuming Tailwind, Nuxt UI, Pinia, Nuxt Image, or a font module exists without checking.
- Producing a static mockup that ignores Nuxt navigation, SEO, SSR data, hydration, component reuse, or typed data.
- Producing a visually competent but interchangeable page with no design brief or memorable signature.
