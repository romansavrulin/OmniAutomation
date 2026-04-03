# OmniFocus Plug-Ins

A collection of [OmniAutomation](https://omni-automation.com/omnifocus/) plug-ins for OmniFocus by Roman Savrulin.

## Plug-Ins

### URL to Comment (`URL-to-Comment.omnijs`)
Keeps only the first line of a task name and moves any URL found in it to the task note. Useful for cleaning up tasks pasted from messengers or browsers.

**Works in:** OmniFocus, OmniGraffle, OmniPlan, OmniOutliner  
**Select:** One or more tasks

---

### URL → Task Name (`URL-to-TaskName.omnijs`)
Fetches the URL found in the task note (or name) and renames the task using the web page title — like a link preview in a messenger. When a resolver returns a description (e.g. StarTrek issue descriptions in YFM format), it is rendered as **rich text** in the task note with bold headings, links, bullet lists, code blocks, and more.

**Works in:** OmniFocus
**Select:** One or more tasks

---

### Copy As URL (`copyAsURL.omnijs`)
Copies selected tasks as formatted hyperlinks (HTML + plain text). Reads the URL from the task note. Useful for pasting rich links into documents or emails.

**Works in:** OmniFocus, OmniGraffle, OmniPlan, OmniOutliner  
**Select:** One or more tasks with a URL in the Note field

---

### Randomize Review Date (`Randomize Review Date.omnijs`)
Randomizes the next review date for selected projects based on each project's existing review interval, spreading reviews out to avoid clustering.

**Works in:** OmniFocus  
**Select:** One or more projects

---

### YFM Renderer Library (`yfm-renderer-library.omnijs`)
Parses **Yandex Flavored Markdown (YFM)** and renders it as rich text using the OmniFocus `Text` API. Used by `URL-to-TaskName.omnijs` to render StarTrek issue descriptions with formatting.

**Supported constructs:**
- Headings (`# H1` through `###### H6`) — bold, sized fonts
- **Bold**, *italic*, ***bold-italic***, ~~strikethrough~~
- [Links](url) — clickable hyperlinks in the note
- Inline `code` and fenced code blocks — monospace font
- Unordered and ordered lists with indentation
- Blockquotes — italic with `┃` prefix
- Markdown tables — header row in bold
- Horizontal rules
- YFM `{% cut "title" %}...{% endcut %}` — collapsible sections rendered with ▶ prefix
- YFM `{% note info/tip/warning/alert %}...{% endnote %}` — callout blocks with emoji prefixes

**Type:** Library

---

### StarTrek API Library (`st-api-library.omnijs`)
Shared plug-in library for StarTrek Sync integrations. Used internally by other plug-ins via `PlugIn.library("StApiLibrary")`.

**Type:** Library

## Installation

These plug-ins live in the OmniFocus iCloud Plug-Ins folder and are loaded automatically by OmniFocus. To install manually, copy the `.omnijs` files into:

```
~/Library/Mobile Documents/iCloud~com~omnigroup~OmniFocus/Documents/Plug-Ins/
```

Or use **OmniFocus → Settings → Automation → Open Plug-Ins Folder**.

## Development

`.omnijs` files are plain JavaScript. The editor is configured to treat them as JavaScript for syntax highlighting and IntelliSense.

- OmniAutomation API reference: <https://omni-automation.com>
- OmniFocus-specific API: <https://omni-automation.com/omnifocus/>
- Network requests use `URL.FetchRequest` (not `fetch`)
- Credentials use the `Credentials` keychain API (never hardcode tokens)
