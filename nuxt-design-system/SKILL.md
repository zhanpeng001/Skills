---
name: nuxt-design-system
description: Use when establishing or restructuring Bootstrap-inspired reusable UI foundations, design tokens, responsive utilities, component primitives, or cross-page visual consistency in a Nuxt project using Vue and TypeScript.
---

# Nuxt Design System

## Purpose

Build a coherent, Bootstrap-inspired UI system for Nuxt: predictable foundations, mobile-first layout, reusable components with clear variants, and practical utilities. Adopt Bootstrap's philosophy, not necessarily its dependency or default visual appearance.

## Workflow

### 1. Audit Before Abstracting

Inspect project structure, styling setup, modules, existing primitives, repeated component variants, themes, and rendered screens. Follow the detected Nuxt 3 or Nuxt 4 directory arrangement and the existing CSS/tooling approach.

Extract a system only from real repeated needs or an explicit design-system request. Do not replace stable app code with abstractions whose only evidence is a single page.

### 2. Apply the Bootstrap Philosophy

- **Mobile first:** make the smallest viewport work with minimal base styles, then add `min-width` enhancements.
- **Stable system surface:** provide reusable containers, layout utilities, spacing conventions, semantic color roles, form states, and core components.
- **Base plus modifier:** keep shared behavior in a base primitive and expose restrained variants such as `variant="primary"` or `size="sm"`.
- **Configurable, not chaotic:** centralize choices as tokens or variant maps rather than allowing arbitrary per-screen styling.
- **Composable markup:** prefer simple components and utilities that combine predictably over one component with excessive props.
- **Progressive customization:** extend foundations without copying or modifying external library source.

Do not make every interface look like stock Bootstrap. Product typography, color, density, imagery, and composition should remain distinctive.

### 3. Use Layered UI Architecture

Organize responsibility in downward-only layers. Higher layers may consume lower layers; primitives and foundations must not depend on page-specific features.

| Layer | Responsibility | Typical Nuxt Location |
| --- | --- | --- |
| Foundations | reset/base rules, semantic tokens, typography, focus, theme variables | existing global stylesheet under `assets/` or `app/assets/` |
| Layout and utilities | container, grid, stack, gap, visibility/display helpers | global CSS utilities or small layout components |
| Primitives | button, input, link, badge, card, modal shell | `components/ui/` or the project's equivalent |
| Patterns | form field, navigation, table toolbar, hero, empty state | feature-neutral component groups |
| Composition | application layouts, feature sections, routed screens | `layouts/`, `pages/`, feature components |

Keep utilities selective: introduce repeated layout behaviors, not an unbounded utility-class framework. Pages compose patterns; patterns compose primitives; primitives consume tokens.

### 4. Define Foundations

Choose a small token surface that matches the product:

- Color roles, surface/elevation, text/border/focus states, and supported themes.
- Typography roles, spacing rhythm, radii, shadows, breakpoints, and motion rules.
- Component interaction contracts: focus-visible, disabled, busy, validation, keyboard behavior.

Prefer prefixed CSS custom properties in the existing global style layer for themeable tokens, for example `--app-color-primary`, `--app-space-3`, and `--app-focus-ring`. Add local component variables at a base primitive when consumers need safe customization. Keep semantic names; avoid binding primitives to one page's literals.

### 5. Build Typed Primitives

- Create reusable Vue SFC primitives only where they remove duplication or centralize important behavior.
- Use `<script setup lang="ts">`; type props, emits, variants, slots where practical, and public component contracts.
- Model base/modifier APIs with small typed variants and sizes; do not expose every CSS property as a prop.
- Favor composition, slots, and selective utilities over highly configurable monolithic components.
- Preserve native semantics: a button remains a button, a link remains navigation, and form controls retain labels/errors.
- Use Nuxt auto-import and component naming conventions already configured in the project.

### 6. Integrate Incrementally

Apply foundations to representative components or pages first, then broaden adoption after validation. Do not conduct an unrelated full-app visual rewrite unless requested. Document unusual tokens or component API decisions in code only when they are not self-evident.

### 7. Verify

Check representative variants, themes, focus/keyboard behavior, reduced motion, narrow/wide layouts, and SSR hydration. Run applicable lint, tests, build, and `nuxt typecheck` when supported; `nuxt build` does not type-check by default.

## Guardrails

- Do not install Bootstrap merely because its philosophy is requested; install it only when the application should consume Bootstrap itself.
- Do not introduce Tailwind, UnoCSS, Nuxt UI, Storybook, a font package, or a theme module unless the project already uses it or the request justifies adoption.
- Do not turn one-off decorative components into global primitives.
- Do not trade readable semantic markup for a styling abstraction.
