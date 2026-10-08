# CBIM Lecture 9 – EEG practical book

Quarto book version of the pre-class and in-class worksheets for CBIM Lecture 9.

## Files

| File | What it is |
|---|---|
| `_quarto.yml` | Book settings: title, author, chapter order, theme |
| `index.qmd` | Welcome page |
| `preclass.qmd` | Pre-class EEG cleaning worksheet (video transcript) |
| `cleaning.qmd` | In class, part 1: removing ICs, interpolation, bad trials |
| `analysis.qmd` | In class, part 2: EEGLAB study and ERSP/TFR plots |
| `styles.css` | Styling for menu paths and screenshots |
| `images/` | Screenshots from the original Word documents |
| `_setup/publish.yml` | GitHub Action that publishes the book to GitHub Pages on every push (move it to `.github/workflows/` first) |

## Editing in Positron

1. **File › Open Folder…** and choose this folder.
2. Install the Quarto CLI if you have not already (<https://quarto.org/docs/get-started/>). Positron ships with the Quarto extension.
3. Open any `.qmd` file and click **Preview** (or run `quarto preview` in the terminal). The book opens in the Viewer and refreshes as you save.
4. To add a chapter, create a new `.qmd` file and list it under `chapters:` in `_quarto.yml`.

### Handy syntax

- Menu paths: `[File › Load Existing Dataset]{.menu}`
- Keyboard keys: `{{< kbd F9 >}}`
- Boxes: `::: {.callout-tip}` … `:::` (also `note`, `warning`, `important`)
- Screenshots: `![](images/in-class/name.png){fig-alt="Description for screen readers"}`. Put text inside the square brackets to add a caption.
- Video: `{{< video https://link-to-video >}}` (there is a placeholder in `preclass.qmd`)
- R code: add an `{r}` chunk as usual. Rendered results are frozen in `_freeze/` (commit that folder), so publishing does not re-run your code.

## Publishing online

### Option A: GitHub Pages (automatic)

1. Move `_setup/publish.yml` to `.github/workflows/publish.yml` (create both folders; the leading dot matters).
1. Create a new GitHub repository and push this folder to its `main` branch.
2. In the repository go to **Settings › Pages** and set **Source** to **GitHub Actions**.
3. Every push to `main` now re-renders and publishes the book at `https://YOUR-USERNAME.github.io/YOUR-REPO/`.

Optionally, uncomment `repo-url` and `repo-actions` in `_quarto.yml` to add "Edit this page" links.

### Option B: Quarto Pub (quickest)

In the Positron terminal run:

```
quarto publish quarto-pub
```

and follow the prompts to sign in. Quarto Pub pages are always public.

### Option C: one-off publish to GitHub Pages from your computer

```
quarto publish gh-pages
```

If you use this, do not set up the GitHub Action in `_setup/` so the two methods do not clash.
