# AthwinUI

> AthwinUI is a lightweight, framework-free CSS component library. One stylesheet, no JavaScript required, light and dark themes built in. All classes are prefixed `aw-`. Colors, radii, shadows and fonts are CSS custom properties (`--aw-*`).

- Docs site: https://atherix.org/athwinui
- Source: https://github.com/D-gger/athwinui
- License: GPL-3.0

## Table of contents

- [Install](#install)
- [LLMs](#llms)
- [Key notes for writing code](#key-notes-for-writing-code)
- [Layout](#layout)
- [Typography](#typography)
- [Buttons](#buttons)
- [Surfaces](#surfaces)
- [Forms](#forms)
- [Navigation and disclosure](#navigation-and-disclosure)
- [Data and feedback](#data-and-feedback)
- [Utilities](#utilities)
- [Design tokens](#design-tokens)
- [Optional](#optional)

## Install

Add this to the `<head>` of any HTML page, then use `aw-*` classes:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/D-gger/athwinui@main/athwin.css">
```

Via npm: `npm install athwinui`, then `import "athwinui/athwin.css"`.

Minimal page:

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/D-gger/athwinui@main/athwin.css">
</head>
<body>
  <main class="aw-container aw-section">
    <h1 class="aw-h1">Hello</h1>
    <button class="aw-btn aw-btn-primary">Click me</button>
  </main>
</body>
</html>
```

## LLMs

Reference https://atherix.org/llms.txt in your prompt
> **Example:** ```Use https://atherix.org/llms.txt for styling```

## Key notes for writing code

- Use only classes listed below.
- Variants are suffixes: `aw-btn aw-btn-primary`, `aw-badge aw-badge-success`. Always include the base class.
- Wrap page content in `aw-container aw-section`.
- Customize with CSS variables, not by editing the library: `:root { --aw-primary: #0ea5e9; }`.
- Dark mode follows the system by default. Force with `<html data-aw-theme="dark">` (or `"light"`), or scope with `class="aw-dark"`.
- Styles live in cascade layers, so any unlayered CSS you write overrides them.

## Layout

- `aw-container`: centered, max width `--aw-container` (1160px). `aw-section`: vertical padding.
- `aw-stack`: vertical flex column; spacing via `style="--aw-gap:.5rem"`.
- `aw-cluster`: wrapping horizontal row, vertically centered (button groups, badges).
- `aw-grid`: equal columns via `--aw-cols` (e.g. `style="--aw-cols:3"`); one column under 700px.
- `aw-grid-auto`: auto-fit columns, minimum width via `--aw-min` (default 220px).
- `aw-between`: flex, space-between. `aw-center`: center both axes. `aw-divider`: `<hr>` line.

## Typography

`aw-eyebrow` (small uppercase label), `aw-display`, `aw-h1`, `aw-h2`, `aw-h3`, `aw-lead`, `aw-muted`, `aw-subtle`, `aw-small`. Inline `<code>` and `<kbd>` are styled by default.

## Buttons

Base `aw-btn` on `<button>` or `<a>`. Variants: `aw-btn-primary`, `aw-btn-outline`, `aw-btn-ghost`, `aw-btn-soft`, `aw-btn-success`, `aw-btn-danger`. Modifiers: `aw-btn-sm`, `aw-btn-lg`, `aw-btn-pill`, `aw-btn-icon`, `aw-btn-block`.

```html
<button class="aw-btn aw-btn-primary aw-btn-lg">Save</button>
```

## Surfaces

```html
<article class="aw-card aw-card-hover">
  <div class="aw-card-header"><h3 class="aw-h3">Title</h3><span class="aw-badge aw-badge-success">Active</span></div>
  <p class="aw-muted">Body</p>
  <div class="aw-card-footer"><a href="#">View</a></div>
</article>
```

- `aw-panel`: subtle inset box. `aw-surface`: surface background.
- Badges: `aw-badge` + optional `-primary | -success | -warning | -danger | -info`.
- Avatars: `<span class="aw-avatar">JD</span>`; sizes `aw-avatar-sm`, `aw-avatar-lg`.

## Forms

Wrap each control in `aw-field` with `aw-label` and optional `aw-hint`.

```html
<label class="aw-field">
  <span class="aw-label">Email</span>
  <input class="aw-input" type="email" placeholder="jane@example.com">
  <span class="aw-hint">We'll never share your email.</span>
</label>
```

- `aw-input` (add `aw-input-error` for invalid), `aw-textarea`, `aw-select`, `aw-range` (on `<input type="range">`).
- `<label class="aw-check"><input type="checkbox"> Text</label>`; `<label class="aw-radio"><input type="radio" name="x"> Text</label>`.
- Switch: `<label class="aw-switch"><input type="checkbox"><span class="aw-switch-track"></span><span>Label</span></label>`.

## Navigation and disclosure

- `aw-nav`: row of links; current link gets `aria-current="page"`.
- `aw-tabs`: links or buttons; active one has `aria-selected="true"` or `.is-active`. Panel switching needs your own JS.
- `aw-breadcrumbs`: links, last item `<span aria-current="page">`.
- Dropdown (no JS): `<details class="aw-dropdown"><summary class="aw-btn aw-btn-outline">Menu</summary><div class="aw-dropdown-panel"><a href="#">Item</a></div></details>`.
- Tooltip: `<button class="aw-btn aw-tooltip" data-tip="Hint">Hover</button>`.
- `aw-kbd`: keyboard key chip.
- Accordion (no JS): `<div class="aw-accordion"><details><summary>Q</summary><p>A</p></details></div>`.

## Data and feedback

- Table: `<div class="aw-table-wrap"><table class="aw-table">…</table></div>`.
- List: `<ul class="aw-list"><li><span class="aw-dot"></span><span>Item</span></li></ul>`.
- Stat: `<div class="aw-stat"><span class="aw-muted aw-small">Label</span><strong class="aw-stat-value">24,892</strong></div>`.
- Alerts: `aw-alert` + `-success | -info | -warning | -danger`; markup `<div class="aw-alert aw-alert-success"><span>✓</span><div><strong>Title</strong>Message</div></div>`.
- Progress: `<div class="aw-progress"><div class="aw-progress-bar" style="--aw-progress:72%"></div></div>`; add `aw-progress-success` for green.
- Loading: `aw-spinner`, `aw-skeleton` (set width/height inline).
- Toast: `aw-toast`.
- Modal: `<div class="aw-modal-backdrop"><div class="aw-modal" role="dialog" aria-modal="true">…</div></div>`. Toggle visibility with your own JS or `aw-hidden`.

## Utilities

`aw-hidden`, `aw-block`, `aw-inline`, `aw-flex`, `aw-flex-wrap`, `aw-items-center`, `aw-justify-between`, `aw-gap-1|2|3`, `aw-mt-1|2|3`, `aw-mb-1|2`, `aw-p-0`, `aw-w-full`, `aw-w-100`, `aw-max-w`, `aw-mx-auto`, `aw-text-center`, `aw-text-right`, `aw-rounded`, `aw-shadow`, `aw-truncate`.

## Design tokens

`--aw-font`, `--aw-mono`, `--aw-bg`, `--aw-surface` (`-2`, `-3`), `--aw-text`, `--aw-muted`, `--aw-subtle`, `--aw-border`, `--aw-primary` (`-hover`, `-soft`), `--aw-on-primary`, `--aw-success|warning|danger|info` (each with `-soft`), `--aw-radius-*`, `--aw-pill`, `--aw-shadow-sm|shadow|shadow-lg`, `--aw-ring`, `--aw-container`, `--aw-transition`.

Override tokens for dark mode too: `[data-aw-theme="dark"] { --aw-primary: …; }`.

## Optional

- Full interactive docs with live previews: https://atherix.org/athwinui
- Stylesheet source: https://github.com/D-gger/athwinui/blob/main/athwin.css
