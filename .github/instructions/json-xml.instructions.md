---
applyTo: "**/*.razor,**/*.cs,**/*.js"
---

# JSON & XML Editor Features

NoteThings will eventually support editing and formatting JSON and XML content within tabs. **The current editor is a plain `<textarea>`** — rich syntax highlighting and language-aware formatting are deferred until a real JS bundler is added to the project (see `copilot-instructions.md`).

## Current State
- Editor is a plain `<textarea>` styled with Tailwind.
- No syntax highlighting, no language-aware formatting yet.

## Formatting (planned)
- For JSON, use `System.Text.Json` with `JsonSerializerOptions { WriteIndented = true }`.
- For XML, use `System.Xml.Linq.XDocument` with `SaveOptions.None`.
- Auto-detect whether tab content is JSON or XML based on the first non-whitespace character (`{`/`[` for JSON, `<` for XML).

## Clipboard
- The `<textarea>` handles cut, copy, and paste natively. No JS interop is required.
