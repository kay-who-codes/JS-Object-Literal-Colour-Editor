# JS Object Literal Colour Editor

> A real-time visual editor for colour values inside JavaScript object literals.

---

## Overview

JS Object Literal Colour Editor is a lightweight, zero-dependency static web app that lets you visually edit colour values stored in JavaScript object literals. Paste your JS object, click any colour swatch to open the native colour picker, tweak hex values inline, then copy the updated code back into your project — all without leaving the browser.

It was built for developers who maintain colour configuration objects (themes, category maps, design tokens, etc.) and want a faster, more visual workflow than manually editing hex codes in a text editor.

---

## Features

- **Real-time parsing** — paste any JS object containing colour values and entries are extracted instantly, no button clicks required
- **Flexible format support** — handles `const`, `let`, `var`, named exports, any indentation style, and colour values in `#rrggbb`, `#rgb`, `rgb()`, and `hsl()` formats
- **Native colour picker** — click any swatch to open the browser's built-in colour picker; changes propagate immediately
- **Inline hex editing** — type directly into the hex field for precise control; the swatch updates in real time
- **Live syntax-highlighted output** — the reconstructed JS object renders with syntax highlighting as you edit, preserving your original variable declaration and formatting
- **Palette preview row** — all colours displayed as a row of chips with hover tooltips showing the key and value
- **Add & remove entries** — add new key/colour pairs with the `+` row; remove any entry with `×`
- **Reset** — revert all colours back to the values originally pasted
- **One-click copy** — copies the full, reconstructed JS object to the clipboard
- **Fully responsive** — fluid layout works on all screen sizes from 320px upwards, with touch-friendly tap targets

---

## Getting Started

JS Object Literal Colour Editor is a single static HTML file with no build step and no external dependencies.

### Option 1 — Open directly in a browser

```bash
git clone https://github.com/yourusername/JS Object Literal Colour Editor-color-editor.git
cd JS Object Literal Colour Editor-color-editor
open color-editor.html   # macOS
# or
start color-editor.html  # Windows
# or
xdg-open color-editor.html  # Linux
```

### Option 2 — Serve locally

Any static file server works:

```bash
# Python
python -m http.server 8080

# Node (npx)
npx serve .

# VS Code
# Use the Live Server extension and click "Go Live"
```

Then open `http://localhost:8080/color-editor.html` in your browser.

### Option 3 — Host on GitHub Pages

1. Fork or push the repo to GitHub
2. Go to **Settings → Pages**
3. Set the source to the `main` branch, root directory
4. Your app will be live at `https://yourusername.github.io/JS Object Literal Colour Editor-color-editor/color-editor.html`

---

## Usage

### Basic workflow

1. **Paste** your JS colour object into the left panel
2. **Edit** colours using the swatches (colour picker) or hex fields (keyboard)
3. **Copy** the updated object from the output panel
4. **Paste** it back into your source file

### Supported input formats

JS Object Literal Colour Editor will correctly parse any of the following patterns:

```js
// Named const with string keys
const categoryColors = {
    "Entertainment": "#3dd6f5",
    "Danger": "#f85d5d"
};

// let / var
let theme = {
    primary: "#e8d8a1",
    secondary: "#b8edff"
};

// Unquoted keys
var palette = {
    background: "rgb(19, 19, 19)",
    highlight: "hsl(45, 70%, 75%)"
};

// Exported object
export const colors = {
    brand: "#FF69B4",
    accent: "#FFD700"
};
```

JS Object Literal Colour Editor extracts only the entries whose values are recognised colour strings. Non-colour keys (strings, numbers, booleans) are ignored and preserved in the output unchanged.

### Supported colour value formats

| Format | Example |
|---|---|
| 6-digit hex | `#3dd6f5` |
| 3-digit hex | `#fff` |
| Hex without `#` | `ffffff` |
| `rgb()` | `rgb(61, 214, 245)` |
| `rgba()` | `rgba(61, 214, 245, 0.8)` |
| `hsl()` | `hsl(192, 88%, 60%)` |

> **Note:** `rgba()` and `hsl()` values are displayed as-is in the output. The native colour picker operates on the `#rrggbb` equivalent internally.

### Adding a new entry

Use the row at the bottom of the **Edit Colours** panel:

1. Type a key name into the text field
2. Click the colour swatch to choose a colour (defaults to `#b8edff`)
3. Press **Enter** or click **+**

### Keyboard shortcuts

| Action | Shortcut |
|---|---|
| Add new entry | `Enter` (while focused on the new key field) |

---

## Project Structure

```
JS Object Literal Colour Editor-color-editor/
└── color-editor.html    # The entire app — HTML, CSS, and JS in one file
```

The app is intentionally self-contained in a single file for maximum portability. There are no build tools, no package manager, and no external network requests.

---

## Design

JS Object Literal Colour Editor uses a dark theme built around two accent colours:

- **Primary accent:** `#e8d8a1` (warm gold) — used for headings, focus states, and the copy button
- **Secondary:** `#b8edff` (cool blue) — used for keyword highlighting and status indicators

Typography is set in **Syne** (display/UI) and **Space Mono** (code and labels), loaded from Google Fonts. A subtle noise texture overlay adds depth to the background without distracting from the colour work.

---

## Browser Compatibility

JS Object Literal Colour Editor relies on standard browser APIs available in all modern browsers:

| Browser | Support |
|---|---|
| Chrome / Edge 88+ | ✅ Full |
| Firefox 90+ | ✅ Full |
| Safari 14+ | ✅ Full |
| Mobile Chrome / Safari | ✅ Full |

The `<input type="color">` element (native colour picker) behaviour varies slightly between browsers but is functional across all of the above.

---

## Contributing

Contributions are welcome. To suggest a feature or report a bug, please open an issue. For pull requests:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Make your changes to `color-editor.html`
4. Open a pull request with a clear description of what changed and why

Please keep the single-file constraint — no build tooling, no external dependencies.

---

## License

MIT License. See [LICENSE](LICENSE) for details.

---

## Acknowledgements

- [Syne](https://fonts.google.com/specimen/Syne) and [Space Mono](https://fonts.google.com/specimen/Space+Mono) typefaces via Google Fonts
- Native browser `<input type="color">` API for the colour picker
