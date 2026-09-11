# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

A single static HTML page (`index.html`) that renders a wedding menu ("Cardápio de Casamento") for Marcely & Natália. There is no build step, package manager, or JavaScript framework — everything (CSS, layout, and the small nav-highlighting script) lives inline in `index.html`. Two decorative images live in `assets/`.

## Development

There are no build/lint/test commands — this is plain HTML/CSS/JS. To preview changes, open `index.html` directly in a browser or serve the folder locally, e.g.:

```bash
python3 -m http.server 8000
```

## Structure

- `index.html` — the entire site: `<style>` block defines all CSS (custom properties for the color palette are declared in `:root`), the `<body>` contains a hero header, a sticky horizontal nav (`#navbar`), and one `<section class="menu-block">` per menu category (Entradas, Saladas, Petiscos, Risotos, Massas, Kids, Executivos, Partilhar, Sobremesas, Bebidas). A trailing `<script>` highlights the active nav link on scroll and auto-scrolls the nav bar to keep it in view.
- Each menu item follows a consistent markup pattern: `.item > .item-row` (name + dotted leader + price) optionally followed by `.desc` (description) or `.sizes` (for items sold by weight, e.g. the "Para Partilhar" section). Bebidas subcategories use an extra `.section > h3` label (e.g. "Águas", "Vinhos Tintos") since that section has no per-item description in most rows.
- `assets/corner-top.png` and `assets/corner-bottom.png` — decorative corner flourishes positioned absolutely in the hero header.

When adding or editing menu items, follow the existing `.item` markup pattern exactly so spacing/typography (dotted leaders, price alignment, uppercase names) stays consistent.
