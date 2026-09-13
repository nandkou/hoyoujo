# Repository Guidelines

## Project Structure & Module Organization

This is a dependency-free, single-page web application. The complete UI, styles, facility master data, and browser-side logic live in `index.html`.

- `index.html` contains the Japanese price-board interface and calls the Rakuten Travel APIs directly from the browser.
- `.env` and `env.js` are optional local configuration inputs; both are ignored by Git. Never commit API credentials.
- There is currently no `src/`, package manifest, test suite, or build output directory. Keep related HTML, CSS, and JavaScript changes close to their existing sections in `index.html`.

## Build, Test, and Development Commands

No install, build, or automated-test commands are configured. Serve the repository through a local HTTP server so the optional `.env` loader works:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000`. Test with a valid Rakuten Web Service application ID and access key, using a small search before running the full facility list. Opening the file directly (`file://`) does not load `.env`.

## Coding Style & Naming Conventions

Match the existing four-space indentation and semicolon-terminated JavaScript. Use `camelCase` for functions and runtime variables (`fetchVacancy`, `hotelNoCache`), `UPPER_SNAKE_CASE` for static datasets (`FACILITIES`), and kebab-case for CSS classes (`grid-form`). Keep Japanese user-facing text natural and consistent with existing labels. Prefer CSS custom properties for repeated colors and preserve responsive behavior at the existing `640px` breakpoint.

## Testing Guidelines

Manually verify changes in a current desktop and narrow mobile viewport. Confirm date validation, filtering, table sorting, API error states, and a successful availability lookup. When changing facility records, verify the displayed name, prefecture, area, and Rakuten search keyword; use a known `hotelNo` when automatic matching is unreliable.

## Commit & Pull Request Guidelines

Recent history uses short, imperative messages, often Conventional Commit-style, such as `feat: add index.html` and `add .gitignore`. Follow that pattern; keep each commit focused. Pull requests should explain the user-visible change, list manual verification performed, link relevant issues, and include screenshots for layout or interaction changes. Do not include credentials, `.env`, or generated `env.js` files.
