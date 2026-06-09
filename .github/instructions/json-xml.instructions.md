---
applyTo: "**/*.razor,**/*.cs"
---

# JSON & XML Editor Features

NoteThings supports editing and formatting JSON and XML content within tabs.

## Formatting
- Provide a format/pretty-print action for JSON using `System.Text.Json` with `JsonSerializerOptions { WriteIndented = true }`.
- Provide a format/pretty-print action for XML using `System.Xml.Linq.XDocument` with `SaveOptions.None`.
- Auto-detect whether tab content is JSON or XML based on the first non-whitespace character (`{`/`[` for JSON, `<` for XML).

## Syntax Highlighting
- Use a Blazor-compatible syntax highlighting library (e.g. a Monaco Editor or Prism.js integration via `wwwroot`) to colour-code JSON and XML tokens.
- Highlighting should update live as the user types.

## Clipboard
- Support cut, copy, and paste using the browser Clipboard API via JS interop (`navigator.clipboard`).
