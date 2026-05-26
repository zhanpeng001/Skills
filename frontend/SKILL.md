---
name: nuxt-frontend
description: Use when creating, redesigning, systematizing, reviewing, or improving frontend interfaces in a Nuxt project using Vue, TypeScript, and Vite.
---

# Nuxt Frontend

## Purpose

Create and improve distinctive production-ready Nuxt interfaces using a Bootstrap-inspired system philosophy: mobile-first layouts, semantic tokens, predictable components, practical utilities, and clear layering. Adopt the philosophy, not necessarily Bootstrap as a dependency or visual style.

## Start With Context

Inspect `package.json`, `nuxt.config.*`, application directories, styles, `public/`, installed modules, existing components/tokens, themes, breakpoints, and validation commands before editing. Nuxt 4 defaults to `app/app.vue`, `app/pages/`, `app/layouts/`, `app/components/`, and `app/assets/`; Nuxt 3 or configured projects may use root-level equivalents. Follow the project.

Do not add a UI kit, Bootstrap, Tailwind, Nuxt UI, animation package, font dependency, theme module, or styling system solely for convenience.

## Design Direction

Translate the product purpose and audience into one coherent visual direction. Choose a recognizable signature in typography, composition, materials, imagery, or focused motion, without falling back to generic grids, arbitrary gradients, or decoration unrelated to context.

Keep product character distinct from stock Bootstrap. Bootstrap inspiration means consistency, responsiveness, and extensibility, not default Bootstrap appearance.

## Bootstrap-Inspired System

- Start mobile-first; add `min-width` layout enhancements for larger screens.
- Centralize semantic color, typography, spacing, radius, focus, motion, and breakpoint decisions.
- Use base-plus-modifier component APIs, such as typed `variant` and `size` props.
- Provide only repeated, useful layout utilities such as container, stack, grid, gap, and display helpers.
- Prefer simple primitives and composition over all-purpose configurable components.
- Use prefixed CSS custom properties such as `--app-color-primary`, `--app-space-3`, and `--app-focus-ring`; use local component variables where safe customization is needed.

## Layered Architecture

Dependencies flow downward only: compositions use patterns; patterns use primitives; primitives consume layouts/utilities and foundations. Lower layers must not depend on feature or route-specific code.

| Layer | Responsibility | Typical Nuxt Location |
| --- | --- | --- |
| Foundations | base styles, tokens, typography, focus, theme variables | global stylesheet under `assets/` or `app/assets/` |
| Layout and utilities | container, grid, stack, gap, visibility/display helpers | global CSS or small layout components |
| Primitives | button, input, link, badge, card, modal shell | `components/ui/` or project equivalent |
| Patterns | form field, navigation, toolbar, hero, empty state | reusable component groups |
| Composition | app layouts, feature sections, routed screens | `layouts/`, `pages/`, feature components |

Extract shared layers only from repeated needs or an explicit system request. Do not generalize a one-off decorative component.

## Nuxt Implementation Rules

- Use Vue SFCs with `<script setup lang="ts">` where consistent with the repository.
- Type props, emits, models, component variants, fetched data, and composable contracts.
- Honor detected Nuxt directories, auto-import conventions, component names, and established tokens.
- Use `NuxtLink` for internal navigation; use `<NuxtImg>` or `<NuxtPicture>` only when the Nuxt Image module is available or intentionally adopted.
- Put assets Vite should process in `assets/`; use `public/` only for files served unchanged at stable root URLs.
- Use `useSeoMeta` when a page requires search or share presentation.
- Use `useFetch` or `useAsyncData` for initial SSR data, `$fetch` for user-triggered requests, and `useState` for SSR-safe shared UI state.
- Keep SSR markup deterministic and isolate genuinely browser-only behavior.
- Prefer CSS transitions/keyframes for simple motion and respect `prefers-reduced-motion`.

## Review and Refinement

When reviewing existing UI, report and fix issues by impact:

1. Broken behavior, SSR/hydration mismatches, and incorrect data/state use.
2. Accessibility: semantics, keyboard behavior, focus, labels, contrast, alt text, reduced motion.
3. Responsive usability: overflow, collapse, touch targets, navigation, reading width.
4. Nuxt correctness: routing, metadata, assets, SSR-safe composables, installed-module assumptions.
5. Visual coherence: hierarchy, spacing, typography, palette, motion, and identity.
6. Performance: excessive client rendering, dependencies, effects, payload, or layout shift.

Separate confirmed defects from taste-based suggestions. Preserve deliberate brand choices unless they produce a concrete problem.

## Verify

Check applicable interaction, loading, empty, error, disabled, focus-visible, theme, and responsive states. Inspect substantial visual changes in a browser or screenshot workflow.

Run applicable lint, tests, build, and `nuxt typecheck` when supported; `nuxt build` does not type-check by default. Run `nuxt prepare` if generated types are missing. Check hydration warnings, asset paths, overflow, and avoidable bundle cost.
