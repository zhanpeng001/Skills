---
name: nuxt-ui-review
description: Use when reviewing, critiquing, or improving an existing Nuxt interface for design quality, responsiveness, accessibility, SSR/hydration correctness, SEO presentation, or frontend performance.
---

# Nuxt UI Review

## Purpose

Audit an implemented Nuxt interface and turn concrete findings into targeted improvements, preserving product character and project conventions.

## Review Order

### 1. Establish Context

Inspect `package.json`, `nuxt.config.*`, the detected app directories, styling/tokens, modules, and validation commands. Identify the route, audience, user task, and intended visual tone before judging aesthetics.

### 2. Find Problems by Impact

Review in this order:

1. Broken behavior: navigation, form controls, interactive state, SSR/hydration mismatches, data/state misuse.
2. Accessibility: semantic structure, keyboard flow, visible focus, labels, contrast, alt text, reduced motion.
3. Responsive usability: overflow, layout collapse, touch targets, reading measure, persistent navigation.
4. Nuxt implementation: `NuxtLink`, routed layouts/components, asset placement, `useSeoMeta`, SSR-safe `useFetch`/`useAsyncData`/`useState`, correct module assumptions.
5. Visual quality: hierarchy, spacing rhythm, typography, palette, depth, motion, and whether the interface has a coherent point of view.
6. Performance: unnecessary client-only rendering, heavy dependencies/effects/assets, payload bloat, avoidable layout shift.

Lead with findings tied to files and rendered behavior. Separate confirmed defects from taste-based recommendations.

### 3. Improve Surgically

When implementation is requested or clearly implied, fix the highest-impact issues using existing components, tokens, and dependencies. Retain intentional brand decisions unless they cause a concrete usability or accessibility problem. Avoid converting an audit into an unrequested redesign or framework migration.

### 4. Verify

Exercise affected interaction states and responsive layouts. Inspect substantial visual changes in a browser or screenshot workflow. Run applicable lint, tests, build, and `nuxt typecheck` when supported; check hydration warnings and asset paths.

## Common Traps

- Criticizing distinct styling merely because it is unconventional.
- Recommending a new UI kit before understanding the existing system.
- Focusing on polish while missing broken keyboard behavior or SSR failures.
- Reporting generic design advice without file-specific or observable evidence.
