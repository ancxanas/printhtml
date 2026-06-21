# HTML Print Studio

A single-page static web app where you paste HTML, see a live print-emulated preview, and print/save as PDF with one click.

## Features

- **Live Preview** — A4-sized print-emulated preview updates as you type, with proper page margins, typography, and print CSS
- **CodeMirror 6 Editor** — syntax-highlighted HTML editor with line numbers and real-time linting
- **Strict HTML Validation** — Lezer-based HTML parser rejects invalid syntax; blocks print until clean
- **Print / Save as PDF** — one-click printing via native browser print dialog (Save as PDF supported)
- **Print Settings** — toolbar to switch page size (A4, Letter, Legal), orientation (portrait/landscape), margins, and background graphics toggle
- **File Operations** — open local HTML files (drag-and-drop or file picker), fetch remote URLs, download the current HTML as a file
- **Auto-Detect** — handles both full HTML documents and HTML snippets
- **Dark/Light Theme** — toggle between Catppuccin Mocha dark and light mode
- **Zero Server** — single `index.html` file, all libraries loaded from CDN

## Usage

1. Open `index.html` in any modern browser (no server needed — works via `file://` or any static host)
2. Type or paste HTML in the editor pane
3. See the live print preview update in the right pane
4. Adjust print settings (page size, orientation, margins) in the bottom toolbar
5. Click **Print** to open the native print dialog or save as PDF

### Keyboard Shortcuts

- `Ctrl/Cmd + P` — Print

## How It Works

- **Editor** uses CodeMirror 6 with the HTML language package for syntax highlighting and Lezer-based parsing
- **Preview** injects user HTML into a sandboxed iframe (`srcdoc`) with DOMPurify sanitization for defense-in-depth
- **Print** creates an ephemeral unsandboxed iframe with the print-ready document and calls `window.print()`
- **Print CSS** uses `@page` rules for paper size and CSS `break-inside`/`break-after` for proper pagination

## Tech Stack

- [CodeMirror 6](https://codemirror.net/) — editor with HTML syntax highlighting and linting
- [DOMPurify](https://github.com/cure53/DOMPurify) — XSS sanitization
- All libraries loaded from CDN via esm.sh and jsDelivr
- No build tools, no frameworks, no server

## License

MIT
