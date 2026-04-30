# Cloudflare Astro Blog

A static-first Astro + MDX blog configured for Cloudflare Workers Static Assets.

## Tooling

This project expects Node.js 22 or newer. A portable Node runtime was downloaded to `.tools/` for bootstrapping because the system Node install was too old and the Chocolatey upgrade needed admin access.

In a fresh terminal with modern Node on your `PATH`, use normal npm commands:

```sh
npm install
npm run dev
npm run build
npm run deploy
```

From this workspace right now, the portable runtime works too:

```powershell
.\.tools\node-v24.15.0-win-x64\npm.cmd run dev
```

## Content

Add posts as `.md` or `.mdx` files in `src/content/blog/`.

```md
---
title: "Post title"
description: "Short summary for listings and metadata."
pubDate: 2026-04-30
tags: ["example"]
---

Your post content.
```

## Cloudflare

`wrangler.jsonc` deploys the built `dist/` directory as Workers Static Assets. For token-based deploys, set these environment variables instead of committing secrets:

```powershell
$env:CLOUDFLARE_API_TOKEN = "..."
$env:CLOUDFLARE_ACCOUNT_ID = "..."
```

Then run:

```powershell
npm run deploy
```
