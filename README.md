<h1 align="center">feed-theme</h1>

<p align="center">An Instagram-inspired Shopify storefront built on the <strong>Skeleton</strong> base with <strong>Tailwind CSS v4</strong> and <strong>Alpine.js</strong>.</p>

<p align="center">
  <a href="./LICENSE.md"><img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License"></a>
</p>

It recreates familiar social-media patterns — a stories carousel, a square product feed, swipeable product galleries, a like/comment/share action bar, a slide-in cart drawer and a mobile bottom tab bar — on top of Shopify's lightweight Skeleton theme. It mirrors the design of its Dawn-based sibling, [`ig_theme`](https://github.com/buzkall/shopify_ig_theme), while keeping the leaner Skeleton foundation.

## Features

- **Stories carousel** with gradient rings (`feed-stories`)
- **Instagram feed** (`feed`): single-column "posts" on the home page, and the same post card shown in a **3-column grid** on the collection and search pages
- **Post cards** (`feed-post-card`) with a swipeable image carousel, double-tap-to-like, and a like / comment / share / save action bar
- **Slide-in cart drawer** and **mobile bottom navigation**
- **IG-style reviews**, saved page, and social gallery
- **Light/dark mode** (applied before first paint to avoid a flash)
- Storefront pages (cart, search, list-collections, 404, blog, article, page) styled to match the feed aesthetic
- Configurable **accent color** and primary **font** via theme settings

## Tech stack

- **Shopify Liquid** on the [Skeleton](https://github.com/Shopify/skeleton-theme) base
- **Tailwind CSS v4** — compiled from `assets/tailwind.css` → `assets/tailwind-output.css`
- **Alpine.js** — self-hosted at `assets/alpinejs.js`, loaded globally and deferred
- **`critical.css`** — per-page essential CSS; its reset is wrapped in `@layer base` so Tailwind's `components`/`utilities` always win the cascade

## Local development

You need a Shopify store (a free [development store](https://partners.shopify.com) works) and the [Shopify CLI](https://shopify.dev/docs/api/shopify-cli).

```bash
npm install
npm run dev          # Shopify theme dev + Tailwind watcher (via concurrently)
```

`npm run dev` runs the Shopify dev server (store set in the `theme:dev` script) alongside the Tailwind watcher and serves the storefront at <http://127.0.0.1:9292>.

### Scripts

| Command             | Description                                                        |
| ------------------- | ------------------------------------------------------------------ |
| `npm run dev`       | Shopify theme dev server + Tailwind watcher (`concurrently`)       |
| `npm run theme:dev` | Shopify theme dev server only                                      |
| `npm run build:css` | Compile `assets/tailwind.css` → `assets/tailwind-output.css`       |
| `npm run watch:css` | Recompile Tailwind on change                                       |

> Run `npm run build:css` before committing whenever you change Tailwind classes, since `assets/tailwind-output.css` is the checked-in build artifact. Validate with `shopify theme check`.

## Theme architecture

```bash
.
├── assets          # Static assets (compiled CSS, JS, images) + critical.css, tailwind.css, alpinejs.js
├── blocks          # Reusable, nestable theme blocks
├── config          # Global theme settings (settings_schema.json / settings_data.json)
├── layout          # Top-level page wrappers (theme.liquid)
├── locales         # Translation files (en.default.json)
├── sections        # Page sections — feed, feed-stories, feed-header, feed-footer, cart, search, …
├── snippets        # Reusable fragments — feed-post-card, feed-product-card, feed-cart-drawer, …
└── templates       # JSON templates wiring sections together per page type
```

The Instagram-specific components are prefixed `feed-*`. To learn more about theme structure, see the [theme architecture documentation](https://shopify.dev/docs/storefronts/themes/architecture).

## License

Open-sourced under the [MIT](./LICENSE.md) License.
