# Operational Preset — UI Component Recipes

A complete, ready-to-apply preset for data-dense operational interfaces (dashboards, monitoring, fleets, queues, admin CRUD). Pairs with `tokens-template.css` — every class below assumes the Tailwind token bridge from that file (`h-control`, `text-caption`, `bg-danger-surface`, `duration-fast`, …).

**How to treat this file:**
- **Reference Replication mode** (matching an existing ops UI): follow it **literally** — this anatomy, these component shapes, this typographic rhythm. Only the brand hues and fonts change (swapped via the token sheet). The result must read as a sibling of the reference screen.
- **Original Direction mode:** this is the default execution layer for any data-dense UI; deviate only with a reason you can state.

Non-negotiable regardless of mode: sticky uppercase table header, `font-mono tabular-nums` numerals, status = icon + label on tinted surface, neutral-by-default color, `h-control` controls, `rounded-sm` badges / `rounded-md` controls / `rounded-lg` cards.

## Principles

1. **Field-first readability:** designed to be read at arm's length, in glare, on tablets → min 12px text, 14px body, 44px touch targets on coarse pointers.
2. **Brand ≠ status ≠ focus:** brand accent only for the primary action, active nav, logo/ribbon. Errors use `danger` + icon + text. Focus ring is its own hue.
3. **One signal per state:** status = icon + label on a tinted surface. Never dot + icon + text triplets, never color alone.
4. **Color only on violation:** neutral by default. A dashboard at rest reads almost monochrome; the few colored elements are the trouble.
5. **Numbers are mono:** IDs, codes, counts, times → `font-mono tabular-nums`; right-align in tables; keep width-stable (zero CLS).
6. **Truth over promotion:** never show a count or metric the data can't back — counters come from the same source as the list they summarize.

## AppShell / Header (one shell across the product)

```
<header class="sticky top-0 z-40 border-b border-border bg-card/95 backdrop-blur">
  <div class="brand-ribbon h-[3px]" aria-hidden />          ← accent→secondary gradient strip (identity)
  <div class="flex h-header items-center gap-2 px-4 lg:px-6">
    [logo mark] [product name, font-bold text-primary-text]
    [app chip: rounded-sm bg-brand-50 px-1.5 text-caption font-semibold]
    [primary nav — flex-1 overflow-x-auto]
    [data-status badge] [sync badge] [UTC/local clock, font-mono text-caption]
    [refresh icon-btn] [lang toggle] [theme toggle] [identity chip]
  </div>
</header>
<main class="w-full min-w-0 flex-1 space-y-4 py-4 lg:py-6 …">
```

- Nav item: active `border-b-2 border-primary font-semibold text-primary-text`; inactive `border-transparent text-muted-foreground hover:text-foreground`; count chip `rounded-sm bg-muted px-1.5 font-mono text-caption`.
- Identity chip: avatar initials + full name + role. Show the person's *name*, not a staff ID.
- Layout prop: `content` (`mx-auto max-w-content px-4`) for forms, `wide` (`w-full px-4`) for data grids.
- Skip-link: `sr-only focus:not-sr-only focus:absolute focus:left-4 focus:top-4 focus:z-60 …` first element in the DOM.

## Button

| Variant | Classes |
|---|---|
| primary | `h-control px-4 rounded-md bg-primary text-primary-foreground hover:bg-primary-hover active:bg-primary-active text-body font-semibold` — the ONE main action per view |
| secondary | `h-control px-4 rounded-md border border-border bg-card text-foreground hover:bg-muted` |
| ghost | `h-control px-3 rounded-md text-muted-foreground hover:bg-muted hover:text-foreground` |
| danger | `h-control px-4 rounded-md bg-danger text-white font-semibold` — destructive only |
| icon | `h-control w-[var(--control-height)] rounded-md justify-center` + mandatory `aria-label` |

All: `focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:opacity-50 disabled:cursor-not-allowed transition-colors duration-fast`.

## StatusBadge — the single status component

```
<span class="inline-flex items-center gap-1 rounded-sm border px-1.5 py-0.5 text-caption font-medium
             bg-{s}-surface border-{s}-border text-{s}"> <Icon class="size-3.5"/> Label </span>
```

| status | icon (lucide) | use |
|---|---|---|
| success | CheckCircle2 | OK / resolved |
| warning | AlertTriangle | attention / degraded |
| danger | XCircle | failure / violation |
| info | Info | informational finding |
| planned | CalendarClock | scheduled / future |
| unknown | HelpCircle | not monitored — render **muted, no border**, or hide |

Map every domain state onto this set once (a table in the domain lib), e.g. priority 1/2/3 → danger/warning/success; use the same mapping everywhere — never improvise per screen. Text-only status color (a violating number without a badge): `text-{s}`.

## KpiCard

- `rounded-lg border bg-card p-4 text-left shadow-xs` — **neutral border always**; selected state `border-foreground ring-1 ring-foreground`, never a status-colored border.
- Label: `text-caption font-medium uppercase tracking-wide text-muted-foreground`.
- Value: `font-mono text-display` — colored (`text-danger`…) **only when it violates**; otherwise `text-foreground`. Include the threshold in the hint (`≤ 2.0 mm`) so the color is self-explanatory.
- Icon chip 32px `grid size-8 place-items-center rounded-md bg-muted text-muted-foreground` — takes the status surface/text pair only when the KPI is in alert.
- As a filter it is a toggle button: `aria-pressed={active}`.

## Alert / announcement bar

`rounded-lg border px-4 py-3 bg-{s}-surface border-{s}-border` + icon + title `text-body font-semibold` + body `text-body-sm` + secondary action + dismiss icon button. Prefer one dismissible bar over a rotating hero.

## Tabs / Segmented filter

`role="tablist"` + `role="tab"` + `aria-selected`. Trigger `h-8 px-3 rounded-sm text-body-sm`; active `bg-foreground text-background font-semibold` (**neutral**, not brand); count `font-mono text-caption`.

## FilterChip (multi-select toggle)

`aria-pressed` + `h-8 rounded-sm border px-2 text-caption font-medium`; active `border-border-strong bg-card text-foreground`; inactive `border-dashed border-border text-muted-foreground`.

## Input / search

`h-control rounded-md border border-input bg-card px-3 text-body placeholder:text-subtle-foreground focus:ring-2 focus:ring-ring`. One global ⌘K command palette; page filters reuse the same field component. Every input has a `<label>`.

## DataTable

- Header cell: `sticky top-0 z-10 bg-muted px-3 py-2 text-left text-caption font-semibold uppercase text-muted-foreground` — the only ALL-CAPS text in the product.
- Body cell: `px-3 py-2 text-body-sm` (13px is allowed **only** here); numbers `font-mono tabular-nums text-right`.
- Selectable row: `tabIndex={0} aria-selected` + Enter/Space activation + `hover:bg-muted focus-visible:ring-2 focus-visible:ring-inset focus-visible:ring-ring`, selected `bg-accent`.
- Category chips in cells: `rounded-sm px-1 text-caption font-semibold` using surface+text of a palette — never saturated fills with white text.
- Emphasized column (e.g. "today"): `bg-accent` + `border-x border-primary/40`. Violations: `bg-danger-surface` + icon.

## Card / Section

- Card: `overflow-hidden rounded-lg border border-border bg-card shadow-xs` (no heavy shadows; borders separate content).
- Section header: `flex items-center gap-x-3 border-b border-border px-4 py-3` + `text-title text-foreground` (sentence case, not ALL CAPS) + count `text-caption text-muted-foreground` + right-aligned actions.

## Charts

- Structural strokes/fills from tokens (`hsl(var(--border))`, `--info`, `--muted-foreground`) → follow dark mode automatically.
- Categorical series palette = constants beside the chart code (SVG-only), validated for light + dark — kept out of the status tokens on purpose.

## New-component checklist

States: default · hover · focus-visible · active · disabled · loading · empty · error — each in **light + dark**, at **390 / 820 / 1440px**, operable by **keyboard only**, with a screen-reader label, and **i18n-complete** strings.

## Enforcement workflow (refactor or new build)

1. Wire the token sheet + Tailwind bridge first; grep baseline: `#[0-9a-fA-F]{3,8}\b`, `rgb(`, `hsl(`, and raw Tailwind palette classes (`text-slate-`, `bg-emerald-`, …) in components. Target: **0** (tokens + chart constants exempt).
2. Map the screen to the recipes above; list gaps; migrate per component in small commits.
3. Screenshot matrix mobile/tablet/desktop × light/dark; verify: nothing under 12px, no horizontal scroll, targets ≥ 44px on touch.
4. Dark-mode parity: flip tokens, not per-component `dark:` overrides.
