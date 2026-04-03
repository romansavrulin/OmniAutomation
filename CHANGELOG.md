# Changelog

## [Unreleased]

### Added
- **YFM Renderer Library** (`yfm-renderer-library.omnijs`) — New library that parses Yandex Flavored Markdown and renders it as rich text in OmniFocus task notes using the OmniFocus 4 `Text` API. Supports headings, bold, italic, links, inline/fenced code, lists, blockquotes, tables, horizontal rules, and YFM-specific `{% cut %}` / `{% note %}` blocks.
- **Rich text descriptions** in task notes — When resolving StarTrek issues, the issue description is now rendered with formatting (bold headings, clickable links, indented lists, monospace code) instead of raw YFM markup.
- `descriptionFormat` field in the resolver chain — Resolvers can now specify the format of their description (e.g., `"yfm"`) so the action knows how to render it.

### Changed
- `URL-to-TaskName.omnijs` (v0.2 → v0.3) — Uses `task.noteText` (OmniFocus 4 rich Text API) to render descriptions with formatting. Adds a bold `── Description ──` separator. Cleans up legacy `<!--resolver:description-->` comment blocks.
- `resolver-startrek.omnijs` — Returns `descriptionFormat: "yfm"` alongside the description.
- `url-resolver-library.omnijs` — `normalizeResult()` now passes through the `descriptionFormat` field from resolvers.
- `README.md` — Added documentation for the YFM Renderer Library.
