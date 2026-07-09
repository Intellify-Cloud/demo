# Visual Design Reference

This file is a visual guide for the reusable Vue shell. It is inspired by the inspected Intercom-style layout, but it is not a brand specification and should not be copied literally.

Use this guide to shape spacing, surfaces, rhythm, and restraint. Replace all brand-specific copy, product assumptions, and imagery with the needs of each future site.

## What To Borrow

- Warm off-white page canvas instead of pure white.
- White content surfaces lifted from the canvas with subtle borders.
- Charcoal text as the primary visual anchor.
- One restrained accent color.
- Clean sans-serif typography.
- Large, calm sections with clear hierarchy.
- Minimal decorative effects.
- Components that feel reusable rather than bespoke.

## What Not To Copy

- Intercom wording, product names, navigation, or page structure.
- Fin AI-specific orange usage.
- Intercom's proprietary fonts.
- The assumption that every section must contain product screenshots.
- Pricing/helpdesk/customer-support components unless a future site needs them.
- Heavy brand mimicry.

## Color Tokens

Recommended defaults:

| Token | Value | Use |
|---|---|---|
| `--color-canvas` | `#f5f1ec` | Page background |
| `--color-surface` | `#ffffff` | Cards, forms, panels |
| `--color-ink` | `#111111` | Headings, body, primary buttons |
| `--color-muted` | `#626260` | Secondary text |
| `--color-subtle` | `#7b7b78` | Captions and helper text |
| `--color-hairline` | `#d3cec6` | Borders and dividers |
| `--color-accent` | `#ff5600` | Sparse accent and special CTAs |

Guidelines:

- Keep the canvas warm and quiet.
- Use white surfaces for hierarchy.
- Use accent color sparingly.
- Avoid one-note palettes dominated by a single hue.
- Avoid drop shadows by default; use surface contrast and borders first.

## Typography

Recommended default:

```css
--font-sans: Inter, ui-sans-serif, system-ui, sans-serif;
```

Suggested scale:

| Token | Size | Weight | Line Height | Use |
|---|---:|---:|---:|---|
| `--text-display` | `clamp(2.5rem, 5vw, 4.5rem)` | 500 | 1.05 | Hero heading |
| `--text-heading` | `clamp(2rem, 3vw, 3.5rem)` | 500 | 1.1 | Section headings |
| `--text-title` | `1.375rem` | 500 | 1.25 | Card titles |
| `--text-lead` | `1.125rem` | 400 | 1.5 | Lead copy |
| `--text-body` | `1rem` | 400 | 1.5 | Body copy |
| `--text-small` | `0.875rem` | 400 | 1.45 | Meta, footer, labels |

Guidelines:

- Use one sans-serif family for the whole shell.
- Keep body letter spacing at `0`.
- Use negative letter spacing only if it improves large headings.
- Avoid all-caps tracked eyebrows unless the future brand calls for it.
- Do not scale small UI text with viewport width.

## Layout

Recommended primitives:

- Base spacing unit: `8px`.
- Max content width: around `1280px`.
- Section vertical spacing: `64px` to `96px`.
- Desktop grids: 3 columns where useful.
- Tablet grids: 2 columns.
- Mobile grids: 1 column.

Use full-width sections with constrained inner containers. Avoid putting page sections inside decorative outer cards.

## Section Rhythm

The shell starts with:

1. 20px contact bar.
2. 100px navigation.
3. 80vh hero.
4. Reorderable content sections.
5. Footer.

Every section should have:

- A stable block class.
- A clear semantic wrapper.
- A predictable inner container.
- Placeholder-safe empty states.
- Responsive layout behavior.

## Components

### Buttons

Primary button:

- Charcoal background.
- White text.
- 8px radius.
- Minimum 40px tap height.

Secondary button:

- White background.
- Charcoal text.
- Hairline border.
- 8px radius.

Accent button:

- Accent background.
- White or charcoal text depending on contrast.
- Use sparingly.

### Cards

Cards should use:

- White background.
- 1px warm hairline border.
- 8px to 12px radius.
- No shadow by default.
- Padding from `24px` to `32px`.

### Forms

Inputs should use:

- White background.
- Charcoal text.
- Visible label.
- 8px radius.
- Minimum 44px touch target.
- Clear focus state.
- Clear error state.

### Navigation

Navigation should:

- Stay visually quiet.
- Collapse cleanly below tablet width.
- Keep the logo and primary action easy to find.
- Avoid overcrowding the first viewport.

## Responsive Behavior

Suggested breakpoints:

| Name | Width | Behavior |
|---|---:|---|
| Desktop | `1280px` | Full layout |
| Tablet | `1024px` | Reduce columns |
| Mobile large | `768px` | Collapse nav, single-column sections |
| Mobile | `480px` | Tighten spacing and heading sizes |

Guidelines:

- Text must not overlap or overflow containers.
- Fixed-format UI elements need stable dimensions.
- Images and iframes need explicit aspect ratios.
- Touch targets should be at least 40px, preferably 44px for form controls.

## SEO And Accessibility

The visual system should support:

- One `h1` per page.
- Logical heading order.
- Semantic landmarks: `header`, `nav`, `main`, `section`, `footer`.
- Descriptive links and buttons.
- Visible keyboard focus.
- Good color contrast.
- Metadata and structured data supplied from centralized content.

## Practical Rules

- Use this file as inspiration, not as a strict clone target.
- Prefer reusable block components over one-off page sections.
- Keep all editable text in the centralized content source.
- Keep theme primitives in CSS custom properties.
- Keep layout choices boring, predictable, and easy to reuse.
- Add visual richness through spacing, hierarchy, and good content before adding effects.
