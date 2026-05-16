# Shopify Theme Boilerplate

Minimal, production-ready Shopify theme with semantic Liquid templates, Theme Editor support, and CI via GitHub Actions.

## Structure

```
assets/          # CSS, JS, images (theme.css, theme.js)
config/
  settings_schema.json   # Theme settings definition
  settings_data.json     # Default setting values
layout/
  theme.liquid   # Root layout wrapping all pages
locales/
  en.default.json        # Translation strings
sections/        # Customizable sections (header, footer, hero, product, etc.)
snippets/        # Reusable Liquid partials
templates/       # Page templates (index, product, collection, page, cart)
```

## Getting Started

### 1. Use this template

```bash
gh repo create my-theme --template stevetoews/boilerplate-shopify-theme --private
cd my-theme
```

### 2. Install Shopify CLI

```bash
npm install -g @shopify/cli @shopify/theme
```

### 3. Connect to a store

```bash
shopify theme dev --store=your-store.myshopify.com
```

This opens a live preview at `http://127.0.0.1:9292`.

### 4. Push to a theme slot

```bash
# Push to an existing theme (get ID from Shopify admin)
shopify theme push --theme=123456789

# Push as a new theme
shopify theme push --unpublished --theme="My Theme Name"
```

## CI/CD

GitHub Actions runs `theme-check` on every push and PR to `main`, failing on any errors.

## Customizing

- Add sections in `sections/` — each gets a `{% schema %}` block for Theme Editor fields
- Add snippets in `snippets/` — render with `{% render 'snippet-name' %}`
- Extend settings in `config/settings_schema.json`
- Add translations in `locales/en.default.json`

## Deploying

Use [Shopify GitHub integration](https://shopify.dev/docs/storefronts/themes/tools/github) for automatic deploys, or deploy manually:

```bash
shopify theme push --store=your-store.myshopify.com
```
