---
name: ntdat-frontend-design
description: Design and build high-craft, production-ready frontend interfaces without generic AI styling. Combines Anthropic's Design Thinking & End-to-End Execution, Taste-Skill's Anti-AI Aesthetics & Copywriting, Emil Kowalski's Motion Engineering, and Vercel's Web Design & Accessibility Guidelines. Use when creating, styling, refactoring, or auditing web applications, dashboards, landing pages, or UI components.
---
# ntdat Frontend Design

This skill synthesizes the four strongest pillars of modern AI frontend engineering into a unified workflow while stripping away rigid template lock-in and recognizable "AI-generated" layout clichés:

1. **Design Thinking & Holistic Execution (from Anthropic `frontend-design`):** Intentional aesthetic direction, atmospheric depth, and complete, self-contained, production-grade code execution across any domain.
2. **Editorial Taste & Zero-Fluff Copywriting (from `taste-skill`):** Natural human visual rhythm, asymmetrical hierarchy, and direct, concrete microcopy without LLM marketing clichés.
3. **Physics-Based Motion Engineering (from `emil-design-eng`):** Interruptible, origin-aware micro-interactions driven by custom spring physics and snappy easing curves.
4. **Web Standards, Ergonomics & Accessibility (from Vercel `web-design-guidelines`):** Strict DOM semantics, keyboard-first operability, URL state synchronization, form ergonomics, and layout stability.

## When to Use

- Designing or coding new web applications, operational dashboards, landing pages, or interactive UI components from scratch
- Refactoring existing interfaces to feel more polished, responsive, and human-crafted
- Adding micro-interactions, state transitions, or animations that feel physically grounded
- Auditing frontend code against Vercel's web interface guidelines, accessibility standards, and modern DOM best practices

## Core Pillars

### 1. Design Thinking & Execution Completeness (Anthropic `frontend-design` Core)

Before writing a single line of code, commit to a clear, domain-specific conceptual direction rather than defaulting to generic utility layouts:

- **Intentional Aesthetic Direction:** Define the exact Purpose, Tone (e.g., *Utilitarian Industrial*, *Editorial Swiss Grid*, *High-Craft Dark UI*, *Warm Tactile Paper*), and a single Memorable Anchor element for the interface.
- **Atmospheric Depth & Surface Craft:** Create depth through subtle surface layering (`surface-0`, `surface-1`, `surface-2`), crisp `1px` inner/outer borders, subtle noise/grain textures where appropriate, and deliberate negative space.
- **Bespoke Typography & Color System:** Define cohesive CSS variables/tokens upfront. Avoid default browser or generic Tailwind blues/purples; establish a dominant neutral surface palette paired with a high-intent semantic accent.
- **Zero-Placeholder Execution:** Never leave `// TODO`, incomplete tabs, or stubbed interactions. Deliver complete, working state logic, realistic domain data, and responsive layouts from the first render.

### 2. Anti-AI Taste & Copywriting (`taste-skill` Core)

Eliminate default LLM visual and verbal tropes so the interface looks crafted by a senior product designer:

- **Ban AI Visual Clichés:** Strictly avoid neon purple/indigo/cyan glowing gradients on dark backgrounds, excessive glassmorphism, floating decorative blobs, and uniform 3-column bento/card grids with identical `icon + heading + 2-line paragraph` structures.
- **Asymmetry & Structural Variety:** Use varied grid spans (e.g., 8/4 or 7/5 splits), inline key-value strips, dense data tables, and crisp `1px` hairlines (`border-subtle`) instead of heavy drop shadows to separate content.
- **Editorial Typography:** Pair distinct font weights and tight tracking (`-0.02em` to `-0.04em` on display headings) with comfortable reading widths (`60ch-70ch`) for prose. Always apply `font-variant-numeric: tabular-nums` (`tabular-nums`) to numeric columns, counters, live telemetry, and timestamps.
- **Zero-Fluff Copywriting:** Ban generic AI marketing filler (*"Unleash"*, *"Revolutionize"*, *"Elevate"*, *"Seamless"*, *"Next-Gen"*, *"Empower"*, *"Supercharge"*). Write direct, concrete labels, button verbs, and microcopy that state exactly what the system does in as few words as possible.

### 3. Motion & Interaction Engineering (`emil-design-eng` Core)

Animations must reinforce spatial relationships and make the interface feel fast and responsive, never decorative or sluggish:

- **Custom Easing & Spring Physics:** Never use `linear` or default `ease-in-out` for UI state changes. Use snappy custom ease-out curves (`cubic-bezier(0.22, 1, 0.36, 1)` or `cubic-bezier(0.16, 1, 0.3, 1)`) for drawers, modals, and entrances, and subtle spring physics for interactive drags or toggles.
- **Fast & Interruptible:** Keep micro-interactions between `120ms` and `240ms`. Animations must be interruptible mid-flight and only animate compositor-friendly properties (`transform`, `opacity`, `clip-path`).
- **Origin-Aware & Tactile Feedback:** Apply subtle scale-down feedback (`active:scale-[0.98]`) on interactive buttons. Ensure popovers, tooltips, dropdowns, and menus scale from their trigger origin (`transform-origin`) rather than the center of the viewport.
- **Reduced Motion Compliance:** Always respect `@media (prefers-reduced-motion: reduce)` by disabling spatial movement/scaling and falling back to instant or simple opacity transitions.

### 4. Web Standards, Accessibility & Ergonomics (Vercel `web-design-guidelines` Core)

Ensure every component behaves like a resilient, production-grade native web application:

- **Semantic HTML & Keyboard-First Navigation:** Use native elements (`<button>`, `<dialog>`, `<nav>`, `<main>`, `<table>`) before custom `<div>` wrappers. Every interactive control must have a crisp `:focus-visible` ring and full keyboard operability (`Tab`, `Shift+Tab`, `Enter`, `Space`, `Escape`, and arrow keys for menus/tabs). Icon-only buttons require explicit `aria-label`.
- **Hit Targets & Layout Stability (Zero CLS):** Keep interactive touch targets at least `44x44px` on mobile/touch devices. Prevent Cumulative Layout Shift (CLS) by reserving explicit dimensions, `aspect-ratio`, or skeleton placeholders for images and async data, and keep dynamic numeric readouts width-stable.
- **Defensive CSS & Complete UI States:** Explicitly design and handle `empty`, `loading` (skeletons/spinners), `error` (with recovery action), `disabled`, and `overflow` states. Prevent broken flex/grid layouts from long user strings using `min-w-0`, `truncate` (`text-overflow: ellipsis`), and `break-words`.
- **Form, Input & URL Ergonomics:** Every input requires an associated `<label>`, appropriate `type` / `inputmode`, `autocomplete`, and inline error feedback that does not shift layout. Sync meaningful view states (active tabs, filters, search queries, sort order) with URL query parameters or deterministic state. Use proper typographic characters (`…` for loading/truncation, curly quotes, non-breaking spaces for units like `10 MB` or `24 ms`).

## Workflow Steps

1. **Formulate Aesthetic & Architecture Plan (Anthropic):** Define the domain tone, surface palette, typographic scale, and layout topology before coding.
2. **Build Semantic Structure & Concrete Copy (Taste + Vercel):** Construct accessible semantic DOM using realistic domain data, concise microcopy, and defensive flex/grid truncation (`min-w-0`, `tabular-nums`).
3. **Engineer Fluid Interactions (Emil):** Layer origin-aware transitions, custom `cubic-bezier` easing curves, tactile press states (`scale(0.98)`), and keyboard shortcuts.
4. **Execute Vercel Quality & A11y Audit:** Verify `:focus-visible` rings, `aria-label` on icon buttons, hit target sizes, `empty`/`loading`/`error` state coverage, and `prefers-reduced-motion` fallbacks.

## Pre-Delivery Audit Checklist

- [ ] **Anthropic Holistic Craft:** Cohesive aesthetic direction, layered surface tokens, and 100% functional interactive states (no placeholders or `TODO`s).
- [ ] **Taste Anti-AI Check:** Zero neon purple/indigo AI gradients, zero generic 3-column icon cards, and zero marketing filler words.
- [ ] **Emil Motion Check:** Transitions use `cubic-bezier(0.22, 1, 0.36, 1)` (`120ms-240ms`), buttons use `active:scale-[0.98]`, and popovers use accurate `transform-origin`.
- [ ] **Vercel Guidelines Check:** All metrics use `tabular-nums`, flex children use `min-w-0`/`truncate`, icon buttons have `aria-label`, keyboard navigation (`Tab`/`Escape`/`:focus-visible`) is complete, and `empty`/`loading`/`error` states are built.
