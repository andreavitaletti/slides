# Blockchain Introduction — Marp Presentation

## Files
- `main.md` — Marp markdown presentation (use with [Marp CLI](https://github.com/marp-team/marp-cli) or [Marp for VS Code](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode))
- `img/` — Slide images extracted from the original PDF (slide_01.png … slide_60.png)

## Usage

### Render to PDF
```bash
marp main.md --pdf --theme beam
```

### Render to HTML
```bash
marp main.md --html --theme beam
```

### VS Code
Install the "Marp for VS Code" extension, open `main.md`, and use the preview panel.

## Theme
This presentation uses the **beam** theme from:
https://rnd195.github.io/marp-community-themes/theme/beam.html

To use it with Marp CLI, download the theme file and pass it:
```bash
marp main.md --pdf --theme-set beam.css
```

## Notes
The `img/` folder contains the original PDF slides as PNG images (150 DPI).
You may replace specific slide images with your own diagrams/figures if needed.

You can swap in your own diagrams by referencing them as ![bg right:40% fit](img/slide_XX.png) using the extracted PNGs

## Prompt Claude

```
Can you translate the slides in the pdf document into and md document, considering presentation.md as a template. Place the result in a zip file that I can download, containing the main.md and the figures in a folder named img. Clearly you are ree to adapt the content to match the template, what is important is to keep the meaning
```
