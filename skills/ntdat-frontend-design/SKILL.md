---
name: craft-frontend-design
description: Design and build high-craft, natural frontend interfaces without generic AI styling. Use when creating, styling, refactoring, or auditing web applications, dashboards, landing pages, or UI components where natural aesthetics, concise copywriting, physics-based motion, and modern web accessibility standards are required.
---
# ntdat Frontend Design

This skill combines editorial taste, fluid interaction engineering, and strict web accessibility standards into a unified frontend workflow. It avoids rigid templates that stifle creativity while deliberately steering clear of recognizable "AI-generated" layout clichés.

## When to Use

- Designing or coding new web pages, dashboards, landing pages, or interactive UI components
- Refactoring existing interfaces to feel more polished, responsive, and human-crafted
- Adding micro-interactions, transitions, or animations that feel physically grounded
- Auditing frontend code for accessibility, keyboard navigation, and modern DOM best practices

## Core Pillars

### 1. Aesthetic & Copywriting (Anti-AI Taste)

Avoid default LLM visual tropes so the interface looks intentionally designed by a human rather than generated from a standard prompt.

- **Eliminate AI visual clichés:** Avoid neon purple/indigo gradients on dark backgrounds, excessive glassmorphism, glowing orbs, and uniform 3-column bento/card grids with identical icon-title-paragraph structures.
- **Asymmetry and visual hierarchy:** Use intentional whitespace, varied grid spans, and crisp 1px borders (`border-subtle`) instead of heavy drop shadows to separate content.
- **High-contrast, editorial typography:** Pair distinct font weights and tight tracking (`-0.02em` to `-0.04em` on large headings) with comfortable reading widths (`60ch-70ch`) for body text. Use `tabular-nums` for all numeric data, tables, and metrics.
- **Zero-fluff copywriting:** Ban generic marketing filler ("Unleash", "Revolutionize", "Elevate", "Seamless", "Next-Gen", "Empower"). Write direct, concrete labels and microcopy that state exactly what the feature does in as few words as possible.

### 2. Motion & Interaction Engineering

Animations should reinforce spatial relationships and make the interface feel responsive, never slow down the user.

- **Physics and custom easing:** Never use linear or default `ease-in-out` for UI state changes. Use snappy ease-out curves (`cubic-bezier(0.22, 1, 0.36, 1)` or `cubic-bezier(0.16, 1, 0.3, 1)`) for entrances and subtle spring physics for interactive elements.
- **Speed and interruptibility:** Keep micro-interactions between `120ms` and `250ms`. Animations must be interruptible and only animate compositor-friendly properties (`transform`, `opacity`, `clip-path`).
- **Tactile feedback:** Apply subtle scale-down feedback (`scale(0.98)`) on active button presses. Ensure popovers, dropdowns, and modals scale from their trigger origin (`transform-origin`) rather than the center of the screen.
- **Respect user preferences:** Always wrap non-essential motion in `@media (prefers-reduced-motion: no-preference)` or provide instant state transitions when reduced motion is enabled.

### 3. Web Standards & Accessibility

Ensure every component behaves like a rock-solid native application under real-world usage.

- **Semantic HTML & Keyboard first:** Use native elements (`<button>`, `<dialog>`, `<nav>`, `<main>`) before reaching for custom `<div>` wrappers. Every interactive element must have a visible `:focus-visible` ring and full keyboard operability (`Tab`, `Enter`, `Space`, `Escape`).
- **Hit targets and layout stability:** Keep interactive hit areas at least `44x44px` on touch devices (using padding or pseudo-elements if the visual icon is smaller). Prevent Cumulative Layout Shift (CLS) by reserving explicit dimensions or aspect ratios for images, skeletons, and async data.
- **Complete UI states:** Never ship only the "happy path". Explicitly handle and style `empty`, `loading`, `error`, `disabled`, and `overflow` (long text truncation with `text-overflow: ellipsis` or `min-w-0` in flex/grid containers) states.
- **URL and form ergonomics:** Sync meaningful filter, tab, or modal states with URL search params where appropriate. Ensure form inputs have proper `label` associations, `autocomplete` attributes, and inline validation feedback.

## Workflow Steps

1. **Establish the Aesthetic Direction:** Before writing code, pick a cohesive color palette (neutral surface tones with a single deliberate accent color) and typographic scale suited to the domain (e.g., dense and utilitarian for dashboards/tools, spacious and editorial for product pages).
2. **Draft Structure & Copy:** Build the semantic DOM layout using realistic, concise copy and domain-accurate sample data instead of `Lorem ipsum` or repetitive placeholder cards.
3. **Layer Micro-Interactions:** Add hover, focus, active, and transition states using custom easing curves and origin-aware transforms.
4. **Run the Quality & A11y Pass:** Verify contrast ratios, keyboard focus rings, text overflow handling (`min-w-0`, `truncate`), `tabular-nums` on numbers, and reduced-motion fallbacks before finalizing the code.

## Pre-Delivery Audit Checklist

- [ ] No neon purple/indigo AI gradients or generic 3-column icon-card grids
- [ ] All numeric metrics, counters, and tables have `font-variant-numeric: tabular-nums`
- [ ] Interactive transitions use custom `cubic-bezier` or spring physics (`120ms-250ms`)
- [ ] Buttons include tactile press feedback (`active:scale-[0.98]`)
- [ ] Full keyboard navigation (`Tab`, `Escape`, `:focus-visible`) works across all controls
- [ ] `empty`, `loading`, `error`, and text-overflow (`min-w-0` / `truncate`) states are handled