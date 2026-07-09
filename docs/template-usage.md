# Template Usage

This project is a Vue shell site. The homepage works like a Jekyll include list: edit one section registry, and the page composition changes.

## Start A New Site

1. Open `src/content/siteText.ts`.
2. Update `site.name`, `site.description`, `site.url`, and `site.ogImage`.
3. Edit the section content blocks.
4. Reorder, add, or remove names in `sections`.
5. Tune colors and spacing in `src/assets/theme.css`.
6. Run `npm run build`.

## Reorder Sections

The homepage order is controlled by:

```ts
sections: [
  "contact-bar",
  "nav-bar",
  "hero",
  "about",
  "steps",
  "map",
  "team",
  "testimonials",
  "contact",
  "footer",
],
```

Remove a section name to remove that block from the homepage.

## Add A Section

1. Create a component in `src/components/sections`.
2. Add its content object to `siteText.ts`.
3. Add its name to the `sections` array.
4. Add it to `componentMap` in `src/views/HomeView.vue`.

## Light And Future Dark Mode

Light mode is the default. The theme already includes a dormant `.theme-dark` variable block in `src/assets/theme.css`.

When you want a dark toggle later:

1. Add or remove `theme-dark` on the document root.
2. Store the user's choice in local storage.
3. Keep all component colors on semantic variables like `--shell-color-canvas`, `--shell-color-surface`, and `--shell-color-ink`.

Do not hard-code dark colors inside components unless a section truly needs a unique treatment.

## Empty Content

Reusable sections should handle empty arrays or missing optional values gracefully:

- Empty `team.members` shows a template note.
- Empty `testimonials.items` shows a template note.
- Empty `map.embedUrl` shows a map placeholder.

For production sites, either fill the content or remove that section name from the registry.
