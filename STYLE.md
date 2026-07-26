# STYLE.md

House style for the revision note. Apply to every section so the finished document is uniform. The note is written to be memorised and delivered orally, so brevity beats completeness and the physical picture beats the derivation.

---

## 1. General

Avoid repetition. If something is defined or explained in one place and needed in another, give it a `\label{}` and point at it with `\cref{}` (sections, equations, tables, figures, postulates). Where two places would want the same definition on equal terms, put it in whichever section comes first. Pointing forwards to a later section is also fine when that is where the material really belongs.

An answer may reference another answer instead of repeating it, and should. Only content a listener genuinely cannot follow without is worth restating.

Never introduce a technical term without either a plain-language definition at first use or a cross-reference to where it is defined. Basic school-level material is exempt.

---

## 2. Emphasis

| Use | For |
| --- | --- |
| `\emph{}` | first use of a defined term, and emphasis in prose |
| `\textbf{}` | label at the head of an `itemize` or `description` item, and header cells in tables. Nothing else |
| `\textit{}` | a law, principle or theorem quoted as a self-contained statement (Newton's first law, the Clausius statement, the Nernst heat theorem). Nowhere else |

Bold never appears inside a sentence. If a term is important enough to stand out, `\emph` does it.

---

## 3. Maths

- **Inline fractions**: `\nicefrac{a}{b}`, differential operators included — `\nicefrac{\partial f}{\partial x}`, `\nicefrac{d}{dt}`. Never a bare `a/b`, never `\frac` or `\tfrac` inline. The one exception is inside a superscript, where `e^{hf/\kB T}` stays as it is.
- **Display fractions**: `\frac`, or `\tfrac` where a stacked fraction would be too tall.
- **Differentials** are a plain italic `d`: `dt`, `dV`, `\frac{d}{dt}`. Not `\mathrm{d}`. Inexact differentials are `\delta Q`, `\delta W`.
- **Vectors and matrices**: `bmatrix`, square brackets. Never `pmatrix`.
- **Inline matrices**: `\left[\begin{smallmatrix}...\end{smallmatrix}\right]`.
- **Operators carry hats**: `\hat{Q}`, `\hat{H}`, `\hat{H}'`, `\hat{p}`, `\hat{x}`.
- **Vector-valued operators** carry both a hat and an arrow: `\hat{\vec{L}}`, `\hat{\vec{S}}`, `\hat{\vec{J}}`, `\hat{\vec{\mu}}`. A single component is `\hat{L}_{z}`, hat only, and so is a squared magnitude, `\hat{L}^{2}`. Classical vectors are `\vec{L}`, no hat.
- **Equations to be memorised** are boxed:
  ```latex
  \begin{empheq}[box=\fbox]{equation}\label{eq:...}
      ...
  \end{empheq}
  ```
  Three or four per section at most, or the emphasis stops meaning anything.
- A displayed equation is part of the sentence around it, so it carries whatever comma or full stop the sentence needs.

---

## 4. Symbols reserved across the note

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
| `\simeq` | approximate value |
| `\varepsilon_{0}` | vacuum permittivity. Never `\epsilon_{0}` |
| `\varphi` | electric scalar potential — `\Phi` is reserved for a wave function |
| `\rho_{\text{f}}`, `\rho_{\text{b}}` | free and bound charge, likewise `\vec{J}_{\text{f}}`, `\vec{J}_{\text{b}}`. Subscripts in `\text{}`, never italic |
| `f` | frequency, never `\nu`. `\nu` is a neutrino, or a four-index |
| `M` | magnetisation, magnetic moment per unit volume, in every section |
| `\chi`, `\chi_{m}` | electric and magnetic susceptibility, both dimensionless |

---

## 5. Quantum-mechanics notation

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

---

## 6. Structure

- Section headings reproduce the exam question from `misc/Pytania_egzaminacyjne.md` **verbatim**, semicolons included. The only permitted departures are typo fixes, articles (*the*, *a*), punctuation and British spelling. Where the official English is a mistranslation of the Polish, the English still wins, and the discrepancy goes in a green `\todoai` note rather than into the heading.
- Every `\section` carries a `\label{sec:...}`, whether or not anything points at it yet.
- Subsection titles are short and plain, and use the correct physics term even where the question does not. Where a question has several parts, the subsections map onto those parts one for one, so it is visible which paragraphs answer which part.
- Postulates go in the `postulate` environment. Roman numerals, counter runs document-wide, so numbering must stay consistent if sections are reordered. `\label{post:...}` inside, referenced with `\cref{post:...}`.
- Labels must be unique across `content_1`–`content_3`, since all three are `\input` into one document. Prefixes: `sec:`, `eq:`, `tab:`, `fig:`, `post:`. Labels are spelled correctly, because they are read as often as the prose is.
- Cross-reference with `\cref`, never with "see above" or "as mentioned earlier".
- Footnotes carry the side material that would break the spoken flow: matrix mechanics, tensor products, partial versus total derivatives, and similar.
- Joint names take an en-dash: `Euler--Lagrange`, `Amp\`ere--Maxwell`, `Hamilton--Jacobi`, `Einstein--Hilbert`, `Bose--Einstein`, `Klein--Gordon`.
- `Schrödinger` is written with a literal `ö` (UTF-8 input is on), never `Schr\"odinger`.

---

## 7. Prose

- British spelling: normalised, quantisation, polarisation, behaviour.
- **No semicolons.** Split the sentence or use a dash. The exception is a section heading, which copies the question as written.
- Em-dash as `---`, **no surrounding spaces**. Three exceptions, all of which keep the spaces:
  1. a symbol gloss after a display — `where $\chi$ --- electric susceptibility of a material`;
  2. a label gloss at the head of a list item — `\item \textbf{Covalent} --- neighbouring atoms share...`;
  3. section and subsection titles.
- `\enquote{}` for quotation marks, never `` `` '' ``.
- No verbose or literary sentences, and no textbook throat-clearing ("Let us begin by...", "It is worth noting that..."). This is a note, not a book.
- Historical asides earn their place only if they carry physics.

---

## 8. `\todo` colours

| Colour | Macro | Meaning |
| --- | --- | --- |
| default (orange) | `\todo` | outstanding question or gap, not yet resolved |
| green | `\todoai` | rewritten and checked, comment from AI |
| red | `\todoper` | persistent note for my own check later |

---

## 9. Tables

- Three horizontal rules only: above the header, below the header, below the last row. No vertical rules, no full grid.
- `\renewcommand{\arraystretch}{1.25}` inside the float, and `\rule{0pt}{2.6ex}` on the first data row to lift it off the header rule.
- Header cells in `\textbf{}`.
- `[H]` placement (`float` package) so the table sits where it is written.
- Every table gets a `\caption` and a `\label{tab:...}`, referenced with `\cref{tab:...}`.
- Caveats about the numbers (order-of-magnitude only, source disagreement, conditions of comparison) go in the caption, not in the body text.

---

## 10. Figures

- `[H]` placement, `\centering`, `width=0.6\linewidth` unless there is a reason to differ.
- Every figure gets a `\caption` and a `\label{fig:...}`, and the body text points at it with `\cref{fig:...}`. A figure nothing refers to is either deleted or cited.
- The numbers quoted in the text must agree with what the figure actually shows.

---

## 11. Numerical values

- Quote values rounded to what is worth saying aloud. Uncertainties only where the uncertainty is itself the point.
- Units in text mode with a thin space: `$80$~GeV`, `$10^{-15}$\,m`. Never a bare space.
- Particle masses and physical constants follow PDG. Name the year in the file's top comment block when a value could drift.
- Where a range matters for the exam, give it in both the units the note uses and the ones the examiner may use — the visible band, for instance, is stated in nm *and* in Hz.

---

## 12. LaTeX source formatting

- One paragraph per source line. No hard wrapping inside a paragraph.
- Exactly one blank line between paragraphs, never two.
- Indentation follows the structure:

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

- Every content file starts with `% !TeX root = main.tex`.
- A comment block at the top of a file records the provenance of anything that might drift (PDG year, lecture number).