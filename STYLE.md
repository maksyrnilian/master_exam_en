# STYLE.md

House style for the revision note. Settled while rewriting `pos_qm.tex`. Apply to every section so the finished document is uniform.

## Emphasis

| Use | For |
| --- | --- |
| `\emph{}` | first use of a defined term, and emphasis in prose |
| `\textbf{}` | label at the head of an `itemize` or `description` item, nothing else |

Bold never appears inside a sentence. If a term is important enough to stand out, `\emph` does it.

## Maths

- **Inline fractions**: `\nicefrac{a}{b}`. Never a bare `a/b`, never `\frac` inline.
- **Display fractions**: `\frac`, or `\tfrac` where a stacked fraction would be too tall.
- **Vectors and matrices**: `bmatrix`, square brackets. Never `pmatrix`.
- **Inline matrices**: `\left[\begin{smallmatrix}...\end{smallmatrix}\right]`.
- **Operators carry hats**: `\hat{Q}`, `\hat{H}`, `\hat{p}`, `\hat{x}`.
- **Equations to be memorised** are boxed:
  ```latex
  \begin{empheq}[box=\fbox]{equation}\label{eq:...}
      ...
  \end{empheq}
  ```
  Three or four per section at most, or the emphasis stops meaning anything.

## Symbols reserved across the note

| Macro / symbol | Meaning |
| --- | --- |
| `\Hilb` = `\mathscr{H}` | Hilbert space |
| `\Ham` = `\mathcal{H}` | classical Hamiltonian, a function on phase space |
| `\hat{H}` | quantum Hamiltonian, an operator |
| `\Lagr` = `\mathcal{L}` | Lagrangian |
| `\ev{}` | expectation value |
| `\comm{}{}`, `\acomm{}{}` | commutator, anticommutator |
| `\kB`, `\muB`, `\const` | Boltzmann constant, Bohr magneton, constant |

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
- Subsection titles are short and plain.

## Prose

- British spelling: normalised, quantisation, behaviour.
- **No semicolons.** Split the sentence or use a dash.
- Em-dash as `---`, no surrounding spaces (unless it is next to math like: `$\Psi$ --- total wave function`).
- `\enquote{}` for quotation marks, never `` `` '' ``.
- No verbose or literary sentences. This is a note, not a book.
- Never introduce a technical term without defining it at first use or cross-referencing where it is defined.
- Footnotes carry the side material that would break the spoken flow: matrix mechanics, tensor products, and similar.

## `\todo` colours

| Colour | Meaning |
| --- | --- |
| default (orange) | outstanding question or gap |
| green | rewritten and checked |
| red | structural or correctness flag needing attention before the exam |

## LaTeX source formatting

- One paragraph per line. No hard wrapping inside a paragraph.
- Blank line between paragraphs.
- Comment block at the top of each file naming the lecture or source the section follows.
