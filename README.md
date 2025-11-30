# Slide template

Setup creation of reveal.js slides with either Quarto or Hugo.

https://quarto.org/docs/presentations/revealjs/

https://quarto.org/docs/reference/formats/html.html

https://quarto.org/docs/reference/formats/presentations/revealjs.html

https://themes.gohugo.io/themes/reveal-hugo/

https://meghan.rbind.io/blog/2022-07-12-making-slides-in-quarto-with-revealjs/#custom-elements

https://github.com/meghall06/personal-website/blob/master/static/slides/NEAIR/custom.scss

https://stackoverflow.com/questions/74060565/adding-a-logo-at-top-left-corner-for-all-slides-in-quarto-presentation

https://github.com/quarto-dev/quarto-cli/issues/809

## Mermaid Diagram Configuration (Quarto)

To ensure Mermaid diagrams render correctly (especially to PNG for Beamer/PDF output) and avoid issues like the "bomb" icon, the following setup is used:

1.  **System Chromium Requirement:** Quarto relies on a headless Chromium browser to convert Mermaid diagrams into static image formats (PNG/SVG). It's recommended to use a system-wide installation of Chromium.
    -   **Installation (Arch Linux):** `sudo pacman -S chromium`
    -   **Quarto Configuration:** Tell Quarto to use this system Chromium by setting the `QUARTO_CHROMIUM` environment variable before rendering:
        `export QUARTO_CHROMIUM=/usr/bin/chromium`

2.  **Diagram Aspect Ratio:** For better fit on slides, especially in Beamer, Mermaid diagrams are often configured for a Left-Right (`graph LR`) flow direction.

3.  **Clean Builds:** If rendering issues (e.g., old "bomb" icons) persist, ensure a clean build by manually removing generated files before re-rendering:
    `rm -rf quarto/*.html quarto/*.pdf quarto/*.tex quarto/*.log quarto/*.aux quarto/*.vrb quarto/slide_files`

**Example Mermaid Chunk:**
```markdown
```{mermaid}
graph LR
  A[Start] --> B{Is it working?}
  B -- Yes --> C[Great!]
  B -- No --> D[Fix it]
  C --> E[End]
  D --> E
```

