# Marp Slides

This directory contains [Marp](https://marp.app/) slide decks written in Markdown.

## Previewing in VS Code

1. Install the **Marp for VS Code** extension (`marp-team.marp-vscode`).
2. Open any `.md` file in this directory.
3. Click the preview icon (or `Cmd+Shift+V`) to see the rendered slides.

## Exporting locally with Marp CLI

Install the CLI:

```bash
npm install -g @marp-team/marp-cli
```

Export to HTML:

```bash
marp bootcamp-agenda.md --html -o bootcamp-agenda.html
```

Export to PDF:

```bash
marp bootcamp-agenda.md --html --pdf -o bootcamp-agenda.pdf
```

Export to PowerPoint:

```bash
marp bootcamp-agenda.md --html --pptx -o bootcamp-agenda.pptx
```

Export all slides in the directory:

```bash
marp . --html
```

> PDF/PPTX export requires Chrome/Chromium. If not found automatically, set `CHROME_PATH`.
