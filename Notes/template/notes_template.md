# LukeDoesMaths — LaTeX Notes Template Reference

Read this before writing or editing any Leaving Cert notes (Maths, Applied Maths, Physics) for LukeDoesMaths.

## Files

- `lukedoesmaths.sty` — the style package. Defines brand colours, fonts, title page, header/footer, and box environments. Don't duplicate this setup inline in a notes file — always `\usepackage{lukedoesmaths}`.
- `notes-template.tex` — worked example (Differentiation) showing every box type in use. Copy this as the starting point for a new topic.

## Compiling

Must use **XeLaTeX or LuaLaTeX** (not pdfLaTeX) — the package uses `fontspec` for the Petrona/Work Sans brand fonts.

```
xelatex notes-template.tex
```

If Petrona / Work Sans aren't installed as system fonts, the style falls back automatically to Georgia / Latin Modern Sans — output still compiles, just without the exact brand typeface.

## Starting a new topic doc

```latex
\documentclass[11pt]{article}
\usepackage{lukedoesmaths}

\subject{Mathematics}       % or Applied Mathematics / Physics
\level{Higher Level}        % or Ordinary Level
\topic{Differentiation}     % topic title shown on the title page

\begin{document}
\ldmtitlepage
\tableofcontents
\clearpage
% ... content ...
\end{document}
```

## Box environments (use these, not raw tcolorbox/manual formatting)

| Environment | Colour | Use for |
|---|---|---|
| `ldmdefinition` | teal | formal definitions, syllabus statements |
| `ldmexample` | terracotta | worked examples / solved problems |
| `ldmexamtip` | gold | exam technique, common pitfalls, marking-scheme notes |
| `ldmformula` | teal/cream, centred | standalone key-formula callouts (rules tables, results to memorise) |
| `ldmsummary` | teal, side-rule | end-of-topic "Key Points" bullet list |

All boxes take an optional title override, e.g. `\begin{ldmexample}[Worked Example -- Chain Rule]`.

## Conventions to keep consistent across topics

- One `ldmsummary` box at the end of every topic — bullet list, 3–6 points max.
- At least one `ldmexamtip` per topic where there's a genuine marking-scheme or common-mistake angle — don't force one if there's nothing worth saying.
- Cross-subject links (e.g. Differentiation → kinematics in Applied Maths, → rates of change in Physics) get their own `\subsection` and ideally an `ldmexample` or `ldmexamtip`, not just a passing mention — this cross-linking is a deliberate feature of the brand (one tutor across all three subjects).
- Use `physics` package macros (`\dv`, `\pdv`, etc.) for derivatives/vectors rather than manual `\frac{d}{dx}` — already loaded by the style.
- Use `siunitx` (`\unit{}`, `\qty{}`) for units in Physics/Applied Maths worked examples — already loaded.
- Body text stays in Work Sans (main font); only headings, the title page, and the logo mark use the Petrona display font — don't manually switch fonts mid-paragraph.
- Don't hardcode hex colours in a notes file — always use the named colours (`ldmTerracotta`, `ldmTeal`, `ldmGold`, `ldmInk`, `ldmMuted`, etc.) defined in the `.sty` so a future palette tweak only touches one file.

## Source of truth for brand

Colour/typography rationale lives in `DESIGN.md` (site design system) and `PRODUCT.md` (positioning/voice) in this same project folder — check there before introducing any new visual element to the notes template.
