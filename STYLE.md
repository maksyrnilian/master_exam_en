# STYLE.md

House style for the revision note. Apply to every section so the finished document is uniform.

## General

Notes should avoid repetition. If something is explained and defined somehwere and is relevant somewhere else it should be assigned a label by `\label{}` referenced by `\cref{}` (sections, equations, etc.). Generally, if two places warrant a certain definition in a comparable way, it should be given in the section that appears earlier but referenceing stuff that appears later is also acceptable if this stuff is more needed there. 

## Emphasis

| Use | For |
| --- | --- |
| `\emph{}` | first use of a defined term, and emphasis in prose |
| `\textbf{}` | label at the head of an `itemize` or `description` item, nothing else |
| `\textit{}` | a law, principle or theorem quoted as a self-contained statement (Newton's first law, the Clausius statement, the statement of Noether's theorem). Nowhere else |

Bold never appears inside a sentence. If a term is important enough to stand out, `\emph` does it.

## Maths

- **Inline fractions**: `\nicefrac{a}{b}`. Never a bare `a/b`, never `\frac` inline.
- **Display fractions**: `\frac`, or `\tfrac` where a stacked fraction would be too tall.
- **Vectors and matrices**: `bmatrix`, square brackets. Never `pmatrix`.
- **Vector-valued operators** carry both a hat and an arrow: `\hat{\vec{L}}`, `\hat{\vec{S}}`, `\hat{\vec{J}}`. A single component is `\hat{L}_{z}`, hat only. Classical vectors are `\vec{L}` with no hat.
- **Inline matrices**: `\left[\begin{smallmatrix}...\end{smallmatrix}\right]`.
- **Operators carry hats**: `\hat{Q}`, `\hat{H}`, `\hat{p}`, `\hat{x}`.
- **Equations to be memorised** are boxed:
  ```latex
  \begin{empheq}[box=\fbox]{equation}\label{eq:...}
      ...
  \end{empheq}
  ```
  Three or four per section at most, or the emphasis stops meaning anything.

## Symbols reserved across the note (macros in preamble)

| Macro / symbol | Meaning |
| --- | --- |
| `\Hilb` = `\mathscr{H}` | Hilbert space |
| `\Ham` = `\mathcal{H}` | classical Hamiltonian, a function on phase space |
| `\hat{H}` | quantum Hamiltonian, an operator |
| `\Lagr` = `\mathcal{L}` | Lagrangian |
| `\ev{}` | expectation value |
| `\comm{}{}`, `\acomm{}{}` | commutator, anticommutator |
| `\kB`, `\muB`, `\const` | Boltzmann constant, Bohr magneton, constant |
| `\equiv` | definitional equality |
| `\simeq` | for approximate values |
| `\varepsilon_{0}` | vacuum permittivity. Never `\epsilon_{0}` |
| `\varphi` | electric scalar potential --- `\Phi` is reserved for a wave function |
| `\rho_{\text{f}}`, `\rho_{\text{b}}` | free and bound charge, likewise `\vec{J}_{\text{f}}`, `\vec{J}_{\text{b}}`. Subscripts in `\text{}`, never italic |
| `f` | denotes frequency, not nu |

## Quantum-mechanics notation

Follows the notation table in Lecture 4, p. 18, so the note and the lecture PDFs can be read side by side.

| Symbol | Meaning |
| --- | --- |
| `\hat{Q}` | generic observable |
| `q_n` | its eigenvalues |
| `\psi_n` | its eigenfunctions, also the basis vectors |
| `\Psi` | total wave function |
| `c_n` | expansion coefficients, `\Psi = \sum_n c_n \psi_n` |
| index `n` | throughout, not `k` or `i` |

Capital `\Psi`, `\Phi` is the full time-dependent wave function. Lower-case `\psi`, `\phi` is the time-independent part alone.

## Structure

- Postulates go in the `postulate` environment. Roman numerals, counter runs document-wide, so numbering must stay consistent if sections are reordered.
- `\label{post:...}` inside a postulate, referenced with `\cref{post:...}`.
- Section headings are the exam questions verbatim, semicolons included.
- Subsection titles are short and plain. Where a question has several parts, the subsections map onto those parts one for one, so it is visible which paragraphs answer which part.
- Every `\section` carries a `\label{sec:...}`, whether or not anything points at it yet.
- Labels must be unique across `content_1`--`content_3`, since all three are `\input` into one document. Prefixes: `sec:`, `eq:`, `tab:`, `fig:`, `post:`.
- Cross-reference with `\cref`, never with "see above" or "as mentioned earlier". An answer may point at another answer instead of repeating it, and should.
- Joint names take an en-dash: `Euler--Lagrange`, `Amp\`ere--Maxwell`, `Hamilton--Jacobi`, `Einstein--Hilbert`.
- `Schrödinger` is written with a literal `ö` (UTF-8 input is on), never `Schr\"odinger`.

## Prose

- British spelling: normalised, quantisation, behaviour.
- **No semicolons.** Split the sentence or use a dash.
- Em-dash as `---`, no surrounding spaces. Two exceptions: the symbol-gloss pattern after a display, `where $\chi$ --- electric susceptibility of a material`, and section titles, which reproduce the exam question as written.
- `\enquote{}` for quotation marks, never `` `` '' ``.
- No verbose or literary sentences. This is a note, not a book.
- Never introduce a technical term without defining it at first use or cross-referencing where it is defined.
- Footnotes carry the side material that would break the spoken flow: matrix mechanics, tensor products, and similar.

## `\todo` colours

| Colour | Meaning |
| --- | --- |
| default (orange) | outstanding question or gap |
| green | rewritten and checked (comment from AI)|
| red (`\todoper`) | persistent note for my own check later |

## Tables

- Three horizontal rules only: above the header, below the header, below the last row. No vertical rules, no full grid.
- `\renewcommand{\arraystretch}{1.25}` inside the float, and `\rule{0pt}{2.6ex}` on the first data row to lift it off the header rule.
- Header cells in `\textbf{}`. This is the one place besides a list label where bold is allowed.
- `[H]` placement (`float` package) so the table sits where it is written.
- Every table gets a `\caption` and a `\label{tab:...}`, referenced with `\cref{tab:...}`.
- Caveats about the numbers (order-of-magnitude only, source disagreement, conditions of comparison) go in the caption, not in the body text.

## Numerical values

- Quote values rounded to what is worth saying aloud. Uncertainties only where the uncertainty is itself the point.
- Units in text mode with a thin space: `$80$~GeV`, `$10^{-15}$\,m`. Never a bare space.
- Particle masses and physical constants follow PDG. Name the year in the file's top comment block when a value could drift.

## LaTeX source formatting

- One paragraph per line. No hard wrapping inside a paragraph.
- Blank line between paragraphs.
- hierarchical indentetaions in environments: 
```latex
\section{}
  text
  \subsection{}
    text
    \begin{}
      text
    \end{}
\section{}
```