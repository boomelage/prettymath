# Pretty Math LaTeX

`prettymath.sty` is a lightweight LaTeX package that wraps common theorem-like statements in colourful, page-friendly boxes. It is meant for lecture notes, homework solutions, or handouts where you want the logical structure of mathematical arguments to stand out without manual box styling.

## Purpose
- Provide consistent visual styling for theorem-family environments such as definitions, theorems, lemmas, propositions, corollaries, claims, examples, exercises, solutions, and proofs.
- Offer turnkey hyperref settings and numbered boxes so authors can focus on content rather than formatting.
- Keep dependencies minimal by building on standard AMS packages and `tcolorbox`.

## Features
- **Boxed theorem environments** powered by `tcolorbox`, each with tailored colours and bold headings to distinguish content types at a glance.
- **Shared numbering** for theorem-like statements: theorems, lemmas, propositions, corollaries, and claims all share the same counter (per section) for coherent references.
- **Definition/example linkage**: examples reset within each definition and gain alphabetic suffixes (`Definition X.Y` hosts `Example X.Ya`, `X.Yb`, …) to emphasize the attachment.
- **Unnumbered proofs and solutions**: `proofbox` and `solution` frame arguments without imposing counters, ideal for inline reasoning.
- **Exercise tracking**: dedicated exercise counter per section to keep problem sets organized.
- **Exercise-solution cross links**: the convenience `exercisesolution` wrapper titles each solution with a clickable reference back to its exercise, forcing the link text to render white so it stays legible inside the purple header even if you globally prefer dark hyperlink colours.
- **Opinionated hyperlink defaults** via `hyperref`, enabling coloured links and borderless PDF outlines out of the box.

## Provided Environments
| Environment | Counter Behaviour                | Default Colours (background / frame) | Typical Usage                        |
|-------------|----------------------------------|---------------------------------------|--------------------------------------|
| `definition`| Numbered within sections         | `green!5` / `green!35!black`          | Formal definitions                   |
| `example`   | Numbered within the current definition (letters) | `blue!5` / `blue!35!black`     | Illustrations tied to a definition   |
| `theorem`   | Numbered within sections         | `orange!5` / `orange!70!black`        | Main results                         |
| `lemma`     | Shares theorem counter           | `orange!5` / `orange!70!black`        | Supporting results                   |
| `proposition`| Shares theorem counter          | `orange!5` / `orange!70!black`        | Mid-tier statements                  |
| `corollary` | Shares theorem counter           | `orange!5` / `orange!70!black`        | Immediate consequences               |
| `claim`     | Shares theorem counter           | `orange!5` / `orange!70!black`        | Sub-claims in proofs                 |
| `exercise`  | Numbered within sections         | `purple!5` / `purple!60!black`        | Practice problems                    |
| `solution`  | Unnumbered                       | `purple!5` / `purple!60!black`        | Worked solutions                     |
| `proofbox`  | Unnumbered                       | `red!5` / `red!35!black`              | Structured proofs                    |
| `remark`    | Unnumbered (via `amsthm`)        | Uses standard amsthm remark styling   | Side observations                    |

## Requirements
- LaTeX2e
- `amsmath`, `amssymb`, `amsthm`
- `tcolorbox` (with `theorems` library)
- `graphicx`, `hyperref`

These packages are loaded automatically by `prettymath.sty`; you only need to ensure they are installed in your TeX distribution.

## Usage
```latex
\documentclass{article}
\usepackage{prettymath}

\begin{document}

\begin{definition}{}{even}
An integer is even if it equals twice another integer.
\end{definition}

\begin{example}{}{even-number}
The number 6 is even because it equals 2 times 3.
\end{example}

\begin{lemma}{}{even-square}
If an integer is even, then its square is even.
\end{lemma}

\begin{proofbox}{}{}
Write the integer as 2k and expand the square to show it is still a multiple of 2.
\end{proofbox}

\end{document}
```

Each `tcbtheorem` environment accepts an optional title parameter and an identifier label, matching the pattern `\begin{theorem}{Optional Title}{label}`. The `remark` environment behaves like the standard `amsthm` remark and does not take the extra arguments.

## Customization Tips
- Override colours by redefining environments with `\tcbset` or editing the `colback`/`colframe` values in `prettymath.sty`.
- Adjust numbering by changing `number within=section` or `use counter from=...` to fit your document structure.
- Update `\hypersetup{...}` in your main document after loading the package if you prefer different link colours.

## Contributing
Feel free to open issues or submit pull requests capturing bugs, colour suggestions, or additional environment styles that could benefit common classroom workflows.
