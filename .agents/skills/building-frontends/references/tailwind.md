# Tailwind CSS v4 and tokens

Use the latest major. Configuration is CSS-first in `assets/css/main.css` through `@theme` / `@theme inline`. No `tailwind.config.js`.

## Tokens

Token rules: `SKILL.md`, Design tokens. This file holds the Tailwind setup.

- Colours are the Tailwind palette referenced as CSS variables. Define semantic role tokens in `@theme inline`, each mapped to a palette variable through an intermediate role variable, and override the role variables in `.dark`.
- Each role has its own token: `bg`, `surface`, `text`, `text-muted`, `border`, `primary`, `primary-hover`, `link`, `link-hover`, and the status roles `success`, `warning`, `error`, `info`. A link is `text-link`, not `text-blue-600`.
- Derived colours (hovers, tints) are tokens too, defined and flipped with the rest.
- Pick hues and shades from the Tailwind v4 colour docs when implementing.

```css
:root {
  --app-link: var(--color-<hue>-<shade>);
  --app-link-hover: var(--color-<hue>-<shade>);
}
.dark {
  --app-link: var(--color-<hue>-<shade>);
  --app-link-hover: var(--color-<hue>-<shade>);
}
@theme inline {
  --color-link: var(--app-link);
  --color-link-hover: var(--app-link-hover);
  --breakpoint-tablet: 768px; /* example names and values */
  --breakpoint-desktop: 1280px;
  --font-sans: "<body font>", sans-serif;
  --font-heading: "<heading font>", sans-serif;
}
```

## Base and component classes

- Style base elements (`body`, headings, `a`, form controls) in `@layer base` from role tokens.
- A recurring element (button, card, input, badge) gets one class in `@layer components` built from role tokens, instead of repeating utilities at call sites.

```css
@layer components {
  .btn {
    @apply inline-flex items-center rounded-md px-4 py-2 font-medium;
    @apply bg-primary text-surface hover:bg-primary-hover;
  }
}
```

In markup use role utilities (`bg-bg`, `text-text`, `text-link`) and component classes.

## Breakpoints and dark mode

- Define the project's breakpoints as tokens (the `tablet` and `desktop` above are examples) and use only those names.
- Dark mode is class-based: `.dark` on `<html>`, set by the framework's colour-mode module. The `.dark` block overrides role variables, so themed utilities flip with no `dark:` prefixes.
