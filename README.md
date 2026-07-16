# Miraggio — Shopify Theme

A custom Shopify storefront for **Miraggio**, a women's vegan-leather bag brand (handbags, slings, and clutches) designed in India. Built on Shopify's [Dawn](https://github.com/Shopify/dawn) theme and extended with a set of bespoke, editorial "aurora" sections.

## Overview

- **Base:** Shopify Dawn (Online Store 2.0, JSON templates + Liquid sections).
- **Brand:** Miraggio — editorial luxury look; warm palette (burgundy espresso, cream, gold/clay, olive), bold uppercase display headings, real hosted photography.
- **Customizations:** Six custom homepage/footer sections prefixed `aurora-`, plus a scaled-up global type size.

## Custom sections

All live in [`sections/`](sections/), are theme-editor friendly (schema settings + presets), and follow the same conventions: `#Prefix-{{ section.id }}` scoped CSS, brand palette CSS variables, real Unsplash bag imagery via `image_url` text settings, subtle entrance animations (gated behind `prefers-reduced-motion`), and mobile breakpoints.

| Section | File | Purpose |
|---|---|---|
| Hero | [aurora-hero.liquid](sections/aurora-hero.liquid) | Full-height hero with overlay, CTAs, and a signature "hangtag" motif. Ships the transparent-header overlay CSS. |
| Offer strip | [aurora-offer-strip.liquid](sections/aurora-offer-strip.liquid) | Slim promo band (free shipping / first-order discount / warranty). |
| Lookbook | [aurora-lookbook.liquid](sections/aurora-lookbook.liquid) | "Shop by style" grid of image cards (up to 4). |
| Promo banner | [aurora-promo.liquid](sections/aurora-promo.liquid) | Full-width image banner with overlay, heading, and CTA. |
| Feature | [aurora-feature.liquid](sections/aurora-feature.liquid) | Split image + text story panel (image left/right). |
| Tiles | [aurora-tiles.liquid](sections/aurora-tiles.liquid) | Two clickable image tiles linking to collections. |
| Footer | [aurora-footer.liquid](sections/aurora-footer.liquid) | Custom branded footer: brand block, newsletter, link columns, socials, policies. Wired via [footer-group.json](sections/footer-group.json). |

## Homepage layout

Section order in [`templates/index.json`](templates/index.json):

1. Aurora hero
2. Aurora offer strip
3. Aurora lookbook
4. Aurora promo banner
5. Rich text
6. Multicolumn ("The Miraggio promise")
7. Aurora feature
8. Aurora tiles
9. Featured collection
10. Newsletter

## Typography

Global type scale is driven by Dawn's own mechanism in [`config/settings_data.json`](config/settings_data.json):

- `body_scale`: **115** — sets `html { font-size: calc(var(--font-body-scale) * 62.5%) }`, scaling all `rem`-based text.
- `heading_scale`: **129** — heading multiplier, kept proportional to `body_scale`.

Adjust these two values (or the **Typography** panel in the theme customizer) to resize text across the whole store.

## Local development

Requires the [Shopify CLI](https://shopify.dev/docs/themes/tools/cli).

```bash
shopify theme dev      # live preview with hot reload
shopify theme check    # lint Liquid + JSON
shopify theme push     # deploy to the connected store
shopify theme pull     # pull the live theme's settings/templates
```

## Notes

- Aurora sections use remote (Unsplash) image URLs by design; `theme check` reports these as `RemoteAsset` performance *warnings*, not errors.
- Product grid placeholders (default Shopify images) come from products without uploaded images — that's store data, fixed by adding product photos in the Shopify admin, not in the theme.
