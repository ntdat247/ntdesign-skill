---
name: ntdat-frontend-design
description: Design and build high-craft, production-ready frontend interfaces without generic AI styling. Built on five pillars — Design Thinking & Execution Completeness, Anti-AI Taste & Copywriting, Motion & Interaction Engineering, Web Standards & Accessibility, and Token Architecture & Semantic Color Discipline. Includes a complete Operational dashboard preset (token sheet + component recipes) and two design modes — replicate an existing UI faithfully, or craft an original direction. Use when creating, styling, refactoring, or auditing web applications, dashboards, design-token systems, light/dark theming, or UI components, especially when the result must match an existing design.
---
# ntdat Frontend Design

This skill synthesizes the five strongest pillars of modern AI frontend engineering into a unified workflow while stripping away rigid template lock-in and recognizable "AI-generated" layout clichés:

1. **Design Thinking & Holistic Execution:** Intentional aesthetic direction, atmospheric depth, and complete, self-contained, production-grade code execution across any domain.
2. **Editorial Taste & Zero-Fluff Copywriting:** Natural human visual rhythm, asymmetrical hierarchy, and direct, concrete microcopy without LLM marketing clichés.
3. **Physics-Based Motion Engineering:** Interruptible, origin-aware micro-interactions driven by custom spring physics and snappy easing curves.
4. **Web Standards, Ergonomics & Accessibility:** Strict DOM semantics, keyboard-first operability, URL state synchronization, form ergonomics, and layout stability.
5. **Token Architecture & Semantic Color Discipline:** HSL token scaffolding with light/dark parity, a three-token status system, strict brand/status/focus color-role separation, operational dashboard density patterns, and a token-lint enforcement workflow.

## When to Use

- Designing or coding new web applications, operational dashboards, landing pages, or interactive UI components from scratch
- Refactoring existing interfaces to feel more polished, responsive, and human-crafted
- Adding micro-interactions, state transitions, or animations that feel physically grounded
- Building or migrating a design-token system, theming (light/dark), or data-dense operational UIs (KPI cards, status badges, data tables, app shells)
- Auditing frontend code against web interface guidelines, accessibility standards, and modern DOM best practices

## Design Modes — decide before anything else

The #1 failure mode of this skill is inventing a fresh aesthetic when the user actually wants an existing one matched. Detect the mode from the request:

1. **Reference Replication** — the request names an existing UI, design system, or screenshot as the style target ("like our portal", "match our operations dashboard", "same style as X", "giống trang Y"): do **not** invent a direction — Pillar 1's original-direction step is suspended. Read `references/tokens-template.css` **and** `references/ops-components.md` in full, swap the reference's brand hues and fonts into the token sheet, then follow the component recipes literally (AppShell topology, KpiCard, StatusBadge, DataTable, button/badge/radius/typography specs). Deviate only where the reference genuinely lacks a pattern. Success test: side-by-side, the new screen must read as a *sibling* of the reference — same accent role, same header anatomy, same table rhythm, same badge treatment — not a cousin with a different accent color.
2. **Original Direction** — fresh product, no style target: apply Pillars 1–2 to commit to a deliberate aesthetic direction, then execute on the token architecture and component recipes as the default layer for data-dense UIs.

When a request is ambiguous, ask which mode is wanted — replicating poorly is worse than asking.

## Core Pillars

### 1. Design Thinking & Execution Completeness

Before writing a single line of code, commit to a clear, domain-specific conceptual direction rather than defaulting to generic utility layouts:

- **Intentional Aesthetic Direction:** Define the exact Purpose, Tone (e.g., *Utilitarian Industrial*, *Editorial Swiss Grid*, *High-Craft Dark UI*, *Warm Tactile Paper*), and a single Memorable Anchor element for the interface.
- **Atmospheric Depth & Surface Craft:** Create depth through subtle surface layering (`surface-0`, `surface-1`, `surface-2`), crisp `1px` inner/outer borders, subtle noise/grain textures where appropriate, and deliberate negative space.
- **Bespoke Typography & Color System:** Define cohesive CSS variables/tokens upfront. Avoid default browser or generic Tailwind blues/purples; establish a dominant neutral surface palette paired with a high-intent semantic accent.
- **Zero-Placeholder Execution:** Never leave `// TODO`, incomplete tabs, or stubbed interactions. Deliver complete, working state logic, realistic domain data, and responsive layouts from the first render.

### 2. Anti-AI Taste & Copywriting

Eliminate default LLM visual and verbal tropes so the interface looks crafted by a senior product designer:

- **Ban AI Visual Clichés:** Strictly avoid neon purple/indigo/cyan glowing gradients on dark backgrounds, excessive glassmorphism, floating decorative blobs, and uniform 3-column bento/card grids with identical `icon + heading + 2-line paragraph` structures.
- **Asymmetry & Structural Variety:** Use varied grid spans (e.g., 8/4 or 7/5 splits), inline key-value strips, dense data tables, and crisp `1px` hairlines (`border-subtle`) instead of heavy drop shadows to separate content.
- **Editorial Typography:** Pair distinct font weights and tight tracking (`-0.02em` to `-0.04em` on display headings) with comfortable reading widths (`60ch-70ch`) for prose. Always apply `font-variant-numeric: tabular-nums` (`tabular-nums`) to numeric columns, counters, live telemetry, and timestamps.
- **Zero-Fluff Copywriting:** Ban generic AI marketing filler (*"Unleash"*, *"Revolutionize"*, *"Elevate"*, *"Seamless"*, *"Next-Gen"*, *"Empower"*, *"Supercharge"*). Write direct, concrete labels, button verbs, and microcopy that state exactly what the system does in as few words as possible.

### 3. Motion & Interaction Engineering

Animations must reinforce spatial relationships and make the interface feel fast and responsive, never decorative or sluggish:

- **Custom Easing & Spring Physics:** Never use `linear` or default `ease-in-out` for UI state changes. Use snappy custom ease-out curves (`cubic-bezier(0.22, 1, 0.36, 1)` or `cubic-bezier(0.16, 1, 0.3, 1)`) for drawers, modals, and entrances, and subtle spring physics for interactive drags or toggles.
- **Fast & Interruptible:** Keep micro-interactions between `120ms` and `240ms`. Animations must be interruptible mid-flight and only animate compositor-friendly properties (`transform`, `opacity`, `clip-path`).
- **Origin-Aware & Tactile Feedback:** Apply subtle scale-down feedback (`active:scale-[0.98]`) on interactive buttons. Ensure popovers, tooltips, dropdowns, and menus scale from their trigger origin (`transform-origin`) rather than the center of the viewport.
- **Reduced Motion Compliance:** Always respect `@media (prefers-reduced-motion: reduce)` by disabling spatial movement/scaling and falling back to instant or simple opacity transitions.

### 4. Web Standards, Accessibility & Ergonomics

Ensure every component behaves like a resilient, production-grade native web application:

- **Semantic HTML & Keyboard-First Navigation:** Use native elements (`<button>`, `<dialog>`, `<nav>`, `<main>`, `<table>`) before custom `<div>` wrappers. Every interactive control must have a crisp `:focus-visible` ring and full keyboard operability (`Tab`, `Shift+Tab`, `Enter`, `Space`, `Escape`, and arrow keys for menus/tabs). Icon-only buttons require explicit `aria-label`.
- **Hit Targets & Layout Stability (Zero CLS):** Keep interactive touch targets at least `44x44px` on mobile/touch devices. Prevent Cumulative Layout Shift (CLS) by reserving explicit dimensions, `aspect-ratio`, or skeleton placeholders for images and async data, and keep dynamic numeric readouts width-stable.
- **Defensive CSS & Complete UI States:** Explicitly design and handle `empty`, `loading` (skeletons/spinners), `error` (with recovery action), `disabled`, and `overflow` states. Prevent broken flex/grid layouts from long user strings using `min-w-0`, `truncate` (`text-overflow: ellipsis`), and `break-words`.
- **Form, Input & URL Ergonomics:** Every input requires an associated `<label>`, appropriate `type` / `inputmode`, `autocomplete`, and inline error feedback that does not shift layout. Sync meaningful view states (active tabs, filters, search queries, sort order) with URL query parameters or deterministic state. Use proper typographic characters (`…` for loading/truncation, curly quotes, non-breaking spaces for units like `10 MB` or `24 ms`).

### 5. Token Architecture & Semantic Color Discipline

Make the color system an engineered, auditable layer instead of per-component styling. Reference scaffolding ready to copy: `references/tokens-template.css` (token sheet) and `references/ops-components.md` (dashboard component recipes).

- **Token-First Theming:** Define every color as an HSL-triplet CSS variable (shadcn convention) so the same sheet works in Tailwind v3 (`hsl(var(--x) / <alpha>)`) and v4 (`@theme`). Ship a complete light + dark pair with identical names — components never write `dark:` color overrides; tokens switch automatically. Pick the neutral temperature deliberately — cool (~hue 210–222) for technical/ops/finance, low-saturation neutral for minimal/editorial, warm (~hue 25–35) for hospitality/content/consumer — and keep one consistent hue across every neutral token; three pre-tuned sets are in `references/tokens-template.css`.
- **Three-Token Status System:** Every semantic status exposes `--{status}` (text/icon), `--{status}-surface` (tinted background), and `--{status}-border`. Render status as icon + label on the tinted surface — never saturated fills with white text, and never color alone (WCAG 1.4.1).
- **Brand ≠ Status ≠ Focus:** Three strictly separated color roles. The brand accent is only for the primary action, active nav, and logo — never links, decoration, or focus. The focus ring uses its own distinct hue, never the brand accent and never the error color, so focus can't be confused with either. When the accent is used *as text*, define a separate `--primary-text` shade retuned for AA contrast — a fill shade and a text shade are different lightness, not the same variable.
- **Color Budget (Neutrals Dominate):** In data views, neutral surfaces/text should own the vast majority of the canvas (~95% of pixels); color is scarce and semantic. Keep ≤ 5 distinct hue families on screen (brand + focus + status), never show status color for a *normal* state (a green "OK" everywhere is decoration), and keep chart categorical palettes separate from status hues. Never fade content with `opacity-*` to mean "unavailable" — use a badge + helper text.
- **Color Only on Violation:** KPI values, borders, and icon chips stay neutral by default and take a status color only when the value crosses a threshold. A dashboard at rest should read almost monochrome; scanning for trouble should be trivial because the few colored elements *are* the trouble.
- **Density With a Floor:** Operational type scale with strict usage — 12px caption floor for labels/meta/badges, 13px body allowed only inside data tables, 14px default body, display size for KPI numerals. All numerals `font-mono` + `tabular-nums`, right-aligned in table columns.
- **Motion & Control Tokens:** Durations (`--duration-fast`, `--duration-base`) and easing (`--ease-standard`) live as tokens; `@media (prefers-reduced-motion: reduce)` collapses durations to `0ms` at the token layer. Controls use `--control-height`, which switches to a 44px touch target via `@media (pointer: coarse)`.
- **Token Lint Enforcement:** Components contain zero hard-coded hex/rgb/HSL values — grep the codebase for `#[0-9a-f]{3,8}`, `rgb(`, and arbitrary Tailwind color classes before delivery; every exception belongs in the token sheet or the chart-constants file.

## Workflow Steps

1. **Detect Design Mode & Formulate Plan:** If the request names a reference UI to match → Reference Replication mode (see Design Modes): the plan IS the reference's anatomy, and both reference files must be read before coding. Otherwise, define the domain tone, surface palette, typographic scale, and layout topology for an original direction.
2. **Scaffold the Token System:** Read `references/tokens-template.css` and `references/ops-components.md` in full; stand up the HSL token pair (light + dark), the three-token status set, brand/status/focus role separation, and layout/motion tokens before any component code. In Replication mode, swap the reference's brand hues and fonts into the template — keep every other value unless the reference differs.
3. **Build Semantic Structure & Concrete Copy:** Construct accessible semantic DOM using realistic domain data, concise microcopy, and defensive flex/grid truncation (`min-w-0`, `tabular-nums`).
4. **Engineer Fluid Interactions:** Layer origin-aware transitions, custom `cubic-bezier` easing curves, tactile press states (`scale(0.98)`), and keyboard shortcuts.
5. **Execute Quality, A11y & Token Audit:** Verify `:focus-visible` rings, `aria-label` on icon buttons, hit target sizes, `empty`/`loading`/`error` state coverage, `prefers-reduced-motion` fallbacks, zero hard-coded colors, and light/dark parity across 390/820/1440px.

## Pre-Delivery Audit Checklist

- [ ] **Holistic Craft:** Cohesive aesthetic direction, layered surface tokens, and 100% functional interactive states (no placeholders or `TODO`s).
- [ ] **Anti-AI Check:** Zero neon purple/indigo AI gradients, zero generic 3-column icon cards, and zero marketing filler words.
- [ ] **Motion Check:** Transitions use `cubic-bezier(0.22, 1, 0.36, 1)` (`120ms-240ms`), buttons use `active:scale-[0.98]`, and popovers use accurate `transform-origin`.
- [ ] **Web Guidelines Check:** All metrics use `tabular-nums`, flex children use `min-w-0`/`truncate`, icon buttons have `aria-label`, keyboard navigation (`Tab`/`Escape`/`:focus-visible`) is complete, and `empty`/`loading`/`error` states are built.
- [ ] **Token Discipline:** Zero hard-coded colors in components (all through tokens); every status uses the surface + border + text trio with icon + label; focus ring hue is distinct from brand and error colors; numerals are `font-mono tabular-nums`; light/dark parity holds with no `dark:` color overrides; neutral states carry no status color.
