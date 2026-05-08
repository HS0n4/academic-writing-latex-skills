---
name: academic-writing-latex-skills
description: Use when drafting, revising, or polishing an academic graduation thesis report in English (or expanding rough notes into thesis prose). Covers mathematics, robotics, motion planning, and optimal control domains. Enforces formal academic register, IMRaD-style structure, IEEE-style citations, LaTeX-compatible formatting, and zero-hallucination technical writing. Triggers on requests like "draft chapter", "polish this thesis section", "rewrite academically", "expand these notes into thesis prose", "write the introduction/methodology/evaluation".
license: MIT
---

# Academic Writing with LaTeX — Guidelines

Behavioral guidelines for producing academic writing that is formal, coherent, well-structured, and ready for a student to adapt into a final graduation thesis submission.

**Tradeoff.** These guidelines prioritize academic rigor, depth, and formal structure over quick summarization or casual explanation. Output will be longer and more deliberate than a typical chat reply, and structured specifically for thesis review by an academic committee.

**Scope.** Applies to undergraduate and master's-level graduation theses, conference and journal papers, and technical reports written in English. The primary domain is mathematics, robotics, motion planning, and optimal control. The default citation style is IEEE; switch only when the user specifies a different university template.

---

## 1. Academic Tone and Structure

Write in clear academic English with a formal and consistent register.

- Prefer fully developed paragraphs over bullet points. Use bullet lists only when the content is inherently list-shaped (contributions, requirements, evaluation criteria, enumerations).
- Avoid over-fragmented subsections. Keep the document hierarchy clean, readable, and proportional to the content — do not introduce a subsection for every paragraph.
- Use `-` for list items, never `*` or `---`.
- **Quotation marks (LaTeX-compatible).** Use LaTeX-style quotes: two backticks to open and two apostrophes to close (`` ``double quotes'' ``); single backtick and apostrophe for single quotes (`` `single' ``). Never use Unicode smart quotes (`" "`, `' '`) or straight ASCII quotes (`"`, `'`) — they render incorrectly when compiled with `pdflatex`/`xelatex`.
- From the second paragraph onward within the same section, indent the first line when the target format supports it (LaTeX does this automatically; in Markdown drafts, leave it to the renderer).
- Keep transitions smooth between paragraphs and sections so the report reads as a continuous academic argument, not a sequence of disconnected notes.
- Avoid casual wording, unsupported superlatives ("the best", "extremely powerful"), marketing language, and rhetorical questions.

### 1.1 Tense and Voice

- **Past tense** for completed work the author performed: methods used, experiments conducted, results obtained ("The model was trained on...", "We measured...").
- **Present tense** for established knowledge, definitions, and statements about the thesis itself ("The system dynamics are described by...", "This chapter presents...").
- **Future tense** sparingly, mostly in the introduction's roadmap ("Chapter 4 will analyze...") and in Future Work.
- Prefer the **third person** or the **authorial "we"** consistent with the chosen style guide; avoid "I" unless the program explicitly permits it.
- Passive voice is acceptable in Methods and Results to keep focus on the work; do not use it to obscure agency in the Discussion.

### 1.2 Hedging and Claims

- Calibrate certainty. Use hedges ("suggests", "indicates", "is consistent with") for inferential claims and reserve definitive language ("proves", "demonstrates") for results that are formally established.
- Never write "it is well known that X" without a citation. If you cannot cite it, rephrase it as an assumption or remove it.

---

## 2. Content Development Workflow

Expand rough ideas into academic prose; do not translate them literally.

- **Analyze context.** Before drafting, identify the report topic, scope, academic level (B.Sc., M.Sc.), target chapter (Introduction, Background, Methodology, Results, Discussion, Conclusion), and any rubric or template constraints the user has shared.
- **Expand with purpose.** Read rough notes carefully and expand each main idea into full academic prose with logical transitions and sufficient explanation to stand on its own. A reader from the same field but unfamiliar with this specific project must be able to follow without external context.
- **Logical hierarchy.** Organize content into a sensible hierarchy: chapter → section → subsection. Each section should advance a single argumentative purpose.
- **Refine and polish.** Revise for clarity, remove repetition, and keep wording neutral. Read the draft aloud (mentally) — if a sentence feels conversational, rewrite it.
- **Light assumptions.** If non-technical contextual information is missing, make the lightest reasonable assumption and flag it (e.g., "Assuming the planning horizon is fixed..."). Never invent unsupported facts.

### 2.1 Suggested Chapter Structure (IMRaD-aligned)

For most engineering and applied-mathematics theses, the following structure is a safe default. Adjust to match the user's university template.

1. **Introduction** — problem statement, motivation, scope, contributions, thesis outline.
2. **Background / Related Work** — theoretical foundations and a critical review of prior art (not a list of paper summaries).
3. **Methodology / Problem Formulation** — the proposed approach, mathematical formulation, design decisions, and rationale.
4. **Implementation** — concrete realization, tooling, and engineering details (only if substantial enough to warrant a chapter).
5. **Evaluation / Results** — experimental setup, metrics, and observed outcomes, reported objectively.
6. **Discussion** — interpretation, comparison with related work, threats to validity, limitations.
7. **Conclusion and Future Work** — summary of contributions and concrete directions for extension.
8. **References** — formatted according to the chosen citation style.
9. **Appendices** — supplementary material (proofs, derivations, parameter tables) that would interrupt the main narrative.

---

## 3. Technical Rigor and Presentation

Maintain strict technical accuracy and clean formatting for engineering and mathematical content.

- **Zero hallucination.** Do not invent technical mechanisms, algorithm details, mathematical properties, or numerical results. If a specific technical constraint is missing, explicitly state the limitation or ask the user for clarification — never fill the gap with plausible-sounding fabrication.
- **Algorithm and pseudocode formatting.** Present algorithms using the `algorithm2e` or `algorithmicx` package — never in plain verbatim blocks. Use consistent notation between pseudocode and the surrounding mathematical exposition.
- **Terminology.** Define every technical acronym on first use, e.g., "Optimal Control Problem (OCP)", and use the acronym consistently thereafter. Maintain a single canonical spelling for each technical term across the document.
- **Numbers and units.** Use SI units with a non-breaking space between the value and unit ("16~kHz", "0.5~s" in LaTeX). Be explicit about precision: state the number of significant figures and the measurement uncertainty when reporting empirical results.

### 3.1 Mathematical Claims and Proofs

- State theorems, lemmas, and propositions precisely: all hypotheses must appear in the formal statement, not only in surrounding prose.
- Follow a definition → theorem → proof → interpretation pattern. Do not bury a key assumption in a footnote or a parenthetical remark.
- When an optimization problem, dynamical system, or constraint set is introduced, define all symbols before the formula, not after.
- For results borrowed from the literature, cite the source and state whether you use the result directly or adapt it.

### 3.2 Figures, Tables, and Equations

High-level expectations only; full conventions live in §5.4 (LaTeX floats), §6 (math), and §7 (figures and tables).

- Every figure and table must be **numbered, captioned, and referenced by number** from the body text — never by position.
- Captions are full sentences that convey the take-away, not just describe contents.
- Equations are numbered only when referenced.
- Trajectory plots and convergence curves are first-class results: label axes with the physical quantity and unit, and include a legend identifying each curve.

---

## 4. Research and Referencing

Support claims with credible academic sources and proper citations.

- Search for related theses, journal articles, conference papers, and authoritative documentation when background material is needed. Prefer venues with peer review (IEEE, ACM, SIAM, Springer, Elsevier) and reputable preprint servers (arXiv) when accompanied by a venue.
- Prefer reliable sources: university repositories, indexed journals, official standards documents (ISO, IETF RFCs), and recognized research databases. Avoid blog posts, Wikipedia, and Stack Overflow as primary citations; if they are the only source, indicate so and seek a stronger replacement.
- **Verify every reference** before citing it: confirm the URL resolves, the DOI is valid, and the work actually supports the specific claim being made. Do not cite a paper for something it does not say.
- Connect each citation directly to the claim it supports — placement matters. A citation at the end of a paragraph attaches to the whole paragraph; place it immediately after the specific sentence when only one claim is supported.
- Format citations in **IEEE style** by default unless the user specifies a different template (ACM, APA, university-specific). A typical IEEE entry:

  ```
  [1] J. Smith and A. Doe, ``Title of the paper,'' in Proc. IEEE Int. Conf. Robotics and Automation (ICRA), 2024, pp. 123--130, doi: 10.1109/ICRA.2024.0001.
  ```

- Avoid citation padding (citing many papers for a trivial claim) and citation laundering (citing a survey instead of the original work).

---

## 5. LaTeX Conventions

When the output is intended for LaTeX compilation, follow these conventions strictly. They are the most common sources of compilation errors and ugly typesetting in student theses.

### 5.1 Quotes, Dashes, and Spacing

- **Quotation marks.** See §1 — use `` ``...'' `` and `` `...' ``, never Unicode or ASCII straight quotes.
- **Dashes.** Three lengths, three uses:
  - Hyphen `-` for compound words ("real-time", "state-space").
  - En-dash `--` for ranges ("pp.~123--130", "1990--1995").
  - Em-dash `---` for parenthetical breaks in prose — like this — with no surrounding spaces.
  - Limit the use of em-dashes in academic prose. Prefer commas, parentheses, semicolons, or sentence restructuring when the same meaning can be expressed more formally and clearly.
- **Non-breaking space `~`.** Use between a label and its number, and between a value and its unit, to prevent line breaks: `Figure~3.2`, `Section~4.1`, `0.5~s`, `Dr.~Smith`.
- **Sentence-ending periods after abbreviations.** After a lowercase abbreviation that is not the end of a sentence, use a backslash-space to suppress the inter-sentence stretch: `e.g.,\ a convex set`, `i.e.,\ the feasible region`. Or use the `\@` trick when an uppercase letter ends a sentence.
- **Ellipsis.** Use `\dots` (or `\ldots`), not three periods `...`.
- **Percent sign.** Always escape: `95\%`, never `95%` (which begins a comment).

### 5.2 Cross-References and Labels

- Use `\label{}` and `\ref{}` (or `\eqref{}` for equations, `\autoref{}` if `hyperref` is loaded). Never write section or figure numbers by hand — they will desynchronize.
- Use a label-prefix convention to keep namespaces clear:
  - `\label{ch:intro}`, `\label{sec:methodology}`, `\label{subsec:formulation}`
  - `\label{fig:trajectory}`, `\label{tab:results}`, `\label{eq:dynamics}`, `\label{alg:solver}`, `\label{thm:optimality}`
- Place `\label{}` immediately after `\caption{}` inside floats, not before — placing it before captures the wrong counter.
- Cross-reference with a non-breaking space: `Figure~\ref{fig:trajectory}`, `Equation~\eqref{eq:dynamics}`.

### 5.3 Math Mode

LaTeX-syntax essentials only; symbol conventions, equation numbering, punctuation around equations, and multi-line layouts are covered in §6.

- **Inline math** uses `$...$` or `\(...\)`. Do not use the deprecated `$$...$$` for display math; use `\[...\]` or the `equation` / `align` environments.
- Use `align` (from `amsmath`) for multi-line equations, not `eqnarray` (deprecated and badly spaced).

### 5.4 Floats: Figures, Tables, Algorithms, and Listings

LaTeX mechanics only; design and authoring guidelines are in §7.

- Wrap figures and tables in `figure` / `table` floats with placement specifier `[htbp]`. Avoid `[H]` (forced placement) except when truly necessary.
- Place `\label{}` immediately after `\caption{}` inside floats, never before.
- **Algorithms.** Use the `algorithm2e` package (preferred for robotics/control theses) or `algorithmicx` with `algpseudocode`. Wrap the environment in an `algorithm` float so it can be captioned and cross-referenced.

### 5.5 BibLaTeX / BibTeX

- Prefer **BibLaTeX with the `biber` backend** for new theses; it handles Unicode, modern citation styles, and IEEE-Trans variants correctly. Fall back to BibTeX only if the university template mandates it.
- Keep entries in a single `references.bib` file. One entry per work; do not duplicate.
- **Capitalize titles defensively.** BibTeX lowercases titles in many styles; protect proper nouns with braces: `title = {{Pontryagin}'s minimum principle for {Riemannian} manifolds}`.
- Always include a stable identifier: `doi`, `isbn`, or `url` + `urldate` for online sources.
- Use semantic citation keys: `lavalle2006planning`, not `ref1`.
- Cite with `\cite{}` (numeric IEEE) or `\textcite{}` / `\parencite{}` (BibLaTeX author-year). Use `\cite[p.~42]{key}` for page-specific citations.

### 5.6 Document Structure and Packages

Standard preamble for a mathematics/robotics/control engineering thesis:

```latex
\documentclass[12pt,a4paper,oneside]{report}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{lmodern}
\usepackage[english]{babel}
\usepackage{microtype}                    % subtle typographic improvements
\usepackage{amsmath,amssymb,amsthm}       % core math environments
\usepackage{mathtools}                    % extensions to amsmath (coloneqq, etc.)
\usepackage{bm}                           % bold math symbols (\bm{x})
\usepackage{graphicx}                     % figures
\usepackage{booktabs}                     % professional tables
\usepackage{siunitx}                      % SI units and number formatting
\usepackage{pgfplots}                     % data plots and trajectory visualizations
\pgfplotsset{compat=1.18}
\usepackage{tikz}                         % diagrams, block diagrams, graphs
\usetikzlibrary{arrows.meta,calc,positioning,shapes.geometric}
\usepackage[ruled,vlined]{algorithm2e}    % algorithm pseudocode
\usepackage{nomencl}                      % list of symbols (heavy-math theses)
\usepackage[hidelinks]{hyperref}          % load LAST, except for cleveref
\usepackage[capitalize]{cleveref}         % smart cross-references; load AFTER hyperref
```

- **Package load order matters.** `hyperref` should be loaded last among most packages; `cleveref` must come after `hyperref`. `biblatex` should be loaded before `csquotes` is used.
- **One sentence per line in the source.** Makes diffs and version control reviewable. LaTeX collapses single newlines into spaces, so this does not affect the output.
- **Comment with `%`** to leave notes for collaborators. Use `\todo{}` (from the `todonotes` package) for visible drafting reminders that you intend to remove before submission.
- **Compile pipeline.** Run `pdflatex` → `biber` (or `bibtex`) → `pdflatex` → `pdflatex` to resolve all references and bibliography. Use `latexmk -pdf` to automate this.

### 5.7 Common LaTeX Mistakes to Avoid

- Hardcoded numbers for figures, sections, or equations instead of `\ref{}`.
- Using `\\` to break paragraphs (it breaks lines without starting a new paragraph; leave a blank line instead).
- Forgetting `~` before `\ref` and `\cite`, producing line breaks before "Figure 3" or "[7]".
- Italicizing entire blocks of text with `{\it ...}` instead of `\emph{...}`.
- Using `\centerline` or `\center` instead of the `center` environment.
- Mixing `\bf`, `\it`, `\rm` (deprecated TeX commands) with `\textbf`, `\textit`, `\textrm` (modern LaTeX commands).
- Using raw `x`, `u`, `f` in math mode for multi-letter identifiers (e.g., writing `cost` instead of `\mathrm{cost}`).

---

## 6. Mathematical Notation and Equations

These conventions apply to academic math regardless of typesetting tool, but the LaTeX hints assume `amsmath` and `mathtools` are loaded.

### 6.1 General Symbol Conventions

- **Scalars and variables:** italic lowercase Latin or Greek (`x`, `\theta`, `\lambda`).
- **Vectors:** bold lowercase (`\mathbf{x}`) or `\bm{x}` (from the `bm` package, supports Greek). Pick one convention and use it consistently throughout the entire thesis.
- **Matrices:** bold uppercase (`\mathbf{A}`) or uppercase italic, following the field convention. State the convention once in the Notation section at the front matter.
- **Tensors of order ≥ 3:** calligraphic (`\mathcal{T}`) or sans-serif bold.
- **Sets and number systems:** blackboard bold for canonical sets — `\mathbb{R}`, `\mathbb{N}`, `\mathbb{Z}`, `\mathbb{C}`. Custom sets in calligraphic (`\mathcal{F}` for a feasible set, `\mathcal{X}` for a state space).
- **Functions and operators:** named operators are upright. Use `\sin`, `\cos`, `\log`, `\exp`, `\max`, `\min`, `\arg\max`, `\arg\min`. For custom operators, declare with `\DeclareMathOperator{\dist}{dist}` in the preamble.
- **Constants vs. variables:** the differential `d` is upright in IEEE/engineering style: `\mathrm{d}x`, `\mathrm{d}t`.
- **Multi-letter identifiers** must be wrapped in `\text{}` or `\mathrm{}` to avoid being typeset as a product: `\mathrm{cost}`, `\mathrm{OCP}` — never raw in math mode. This applies to subscripts: `x_{\text{ref}}`, not `x_{ref}`.

### 6.2 Domain-Specific Symbol Conventions

These conventions are standard in robotics, motion planning, and optimal control literature. Apply them consistently unless the user specifies a different notation system.

#### Dynamical Systems

- Denote the **state** at time $t$ as $\mathbf{x}(t) \in \mathcal{X} \subseteq \mathbb{R}^n$ and the **control input** as $\mathbf{u}(t) \in \mathcal{U} \subseteq \mathbb{R}^m$.
- Write **continuous-time dynamics** as $\dot{\mathbf{x}}(t) = f(\mathbf{x}(t), \mathbf{u}(t))$ and **discrete-time dynamics** as $\mathbf{x}_{k+1} = f(\mathbf{x}_k, \mathbf{u}_k)$.
- Use $T$ or $T_f$ for a fixed horizon and $[t_0, t_f]$ for the time interval. Reserve $t$ for the continuous time variable and $k$ for the discrete step index.
- Denote trajectories as $\mathbf{x}(\cdot)$ (the entire function) versus $\mathbf{x}(t)$ (the value at time $t$).

#### Optimization Problems

- Present optimization problems in standard form with labeled parts:

  ```latex
  \begin{equation}
      \begin{aligned}
          \minimize_{\mathbf{x}(\cdot),\,\mathbf{u}(\cdot)} \quad
              & J(\mathbf{x}(\cdot), \mathbf{u}(\cdot)) \\
          \subjectto \quad
              & \dot{\mathbf{x}}(t) = f(\mathbf{x}(t), \mathbf{u}(t)), \\
              & \mathbf{x}(t) \in \mathcal{X},\quad \mathbf{u}(t) \in \mathcal{U}, \\
              & \mathbf{x}(t_0) = \mathbf{x}_0,\quad \mathbf{x}(t_f) \in \mathcal{X}_f.
      \end{aligned}
      \label{eq:ocp}
  \end{equation}
  ```

  Declare `\DeclareMathOperator{\minimize}{minimize}` and `\DeclareMathOperator{\subjectto}{subject\ to}` in the preamble.
- Use $J$ or $\ell$ for cost/objective, $g$ for inequality constraints, $h$ for equality constraints. Define each symbol immediately after the problem statement.
- Distinguish **decision variables** (what is optimized) from **parameters** (fixed data): state this explicitly in the surrounding text.

#### Graph and Geometric Structures

- Denote a graph as $\mathcal{G} = (\mathcal{V}, \mathcal{E})$ with vertex set $\mathcal{V}$ and edge set $\mathcal{E}$.
- Use $\mathcal{P}$ or $\mathcal{R}$ for the robot's configuration space and $\mathcal{C}_{\mathrm{free}}$, $\mathcal{C}_{\mathrm{obs}}$ for the free and obstacle subspaces.
- Convex sets: use $\mathcal{S}$, $\mathcal{P}_i$, or $\mathcal{H}_i$ with calligraphic notation; do not reuse the same letter for different sets in the same chapter.

### 6.3 Equation Numbering

- **Number only equations that are referenced** from the body text. Unreferenced equations clutter the document.
- Use `equation` (or `align`) for numbered displays, and `equation*` / `align*` (or `\[...\]`) for unnumbered displays.
- Reference with `\eqref{eq:label}` (renders as "(3.1)") not `\ref{}`. With `cleveref`, `\cref{eq:label}` produces "Eq.~(3.1)" automatically.
- For derivations, suppress numbering on intermediate steps with `\nonumber` (in `align`) or use `align*` and number only the final result.
- Subordinate numbering with `subequations` for related equations: `(3.1a)`, `(3.1b)`, `(3.1c)`.

### 6.4 Punctuation and Grammar Around Equations

Treat equations as part of the sentence, not as separate blocks.

- **Punctuate as if reading aloud.** A display equation that ends a sentence ends with a period; one that continues a sentence ends with a comma or no punctuation at all. The mark goes **inside** the math environment.

  ```latex
  The cost functional is defined as
  \begin{equation}
      J(\mathbf{x}(\cdot), \mathbf{u}(\cdot))
          = \int_{t_0}^{t_f} \ell(\mathbf{x}(t), \mathbf{u}(t))\,\mathrm{d}t
            + V_f(\mathbf{x}(t_f)),
      \label{eq:cost}
  \end{equation}
  where $\ell \colon \mathcal{X} \times \mathcal{U} \to \mathbb{R}$ is the running cost
  and $V_f \colon \mathcal{X} \to \mathbb{R}$ is the terminal cost.
  ```

- **Capitalization after a display.** Continue with lowercase ("where $\ell$...") if the equation is part of the sentence. Start a new sentence (capital) only if the equation ended one.
- **Do not start a sentence with a symbol.** Rewrite: not "$\mathbf{x}$ denotes..." but "Let $\mathbf{x}$ denote..." or "The state vector $\mathbf{x}$ denotes...".

### 6.5 Defining Symbols

- **Introduce every symbol on first use.** "Let $\mathbf{x}(t) \in \mathbb{R}^n$ denote the system state at time $t$, where $n$ is the state dimension." Do not assume the reader can infer meaning from context.
- **Do not redefine symbols** within the same chapter. If two concepts require the same letter, rename one and note the convention.
- **Maintain a Nomenclature / List of Symbols** at the front matter for theses with heavy math. Use the `nomencl` package or `glossaries`. Group by category (sets, scalars, vectors, operators, indices).
- When borrowing notation from prior work, cite the source on first use: "Following the notation of Lavalle~\cite{lavalle2006planning}, we write $\mathcal{C}$ for the configuration space."

### 6.6 Display vs. Inline

- **Inline** (`$...$`) for short expressions that fit on a single line and do not disrupt line spacing: `$x^2 + 1$`, `$O(n \log n)$`, `$\mathbf{x} \in \mathcal{X}$`.
- **Display** (`\[...\]` or `equation`) for any expression with `\sum`, `\int`, `\prod`, large fractions, matrices, optimization problems, or that you intend to reference later.
- **Force display-style limits inline** when needed: `$\sum\limits_{k=0}^{N-1} \ell_k$` or wrap in `\displaystyle`.

### 6.7 Multi-line Equations and Cases

- Use `align` (from `amsmath`) for systems of equations or step-by-step derivations. Align on `&` at the relation (`=`, `\leq`, `\Rightarrow`).
- Use `cases` for piecewise definitions:

  ```latex
  \[
      \phi(x) = \begin{cases} 0 & \text{if } x \in \mathcal{X}_f, \\ +\infty & \text{otherwise.} \end{cases}
  \]
  ```

- Long single equations that must break: use `split` (single equation number) or `multline`.
- Never use `eqnarray` — its spacing is broken by design.

### 6.8 Operator Limits and Big Operators

- Place limits **above and below** for `\sum`, `\prod`, `\bigcup`, `\bigcap`, `\lim`, `\max`, `\min` in display mode (default).
- For integrals over time, use **side-set** limits: `\int_{t_0}^{t_f} f(t)\,\mathrm{d}t`. Use `\,` (thin space) before the differential.
- Use `\left( ... \right)` for delimiters that must scale to their content (fractions, matrices). Do not apply `\left( \right)` mechanically — fixed-size `(...)` is better when the content is small.

### 6.9 Theorems, Definitions, and Proofs

For thesis chapters with formal results, use `amsthm` environments:

```latex
\newtheorem{theorem}{Theorem}[chapter]
\newtheorem{lemma}[theorem]{Lemma}
\newtheorem{proposition}[theorem]{Proposition}
\newtheorem{corollary}[theorem]{Corollary}
\theoremstyle{definition}
\newtheorem{definition}[theorem]{Definition}
\newtheorem{assumption}[theorem]{Assumption}
\newtheorem{example}[theorem]{Example}
\newtheorem{problem}[theorem]{Problem}
\theoremstyle{remark}
\newtheorem{remark}[theorem]{Remark}
```

- Use a single shared counter (`[theorem]`) so theorems, lemmas, and definitions share sequential numbering.
- End proofs with `\begin{proof} ... \end{proof}` (auto-inserts the QED tombstone).
- State theorems precisely: include all hypotheses in the statement. Use the `assumption` environment to collect standing assumptions at the start of a chapter and refer to them by number in theorem statements.

### 6.10 Common Math-Writing Pitfalls

- **Unbalanced delimiters.** `\left(` must pair with `\right)`.
- **Mixing notation.** Do not switch between `\mathbf{x}` and `\bm{x}` for the same vector.
- **Reusing letters.** Do not let $n$ mean both "state dimension" and "number of samples" in the same chapter.
- **Walls of math without prose.** Every non-trivial equation deserves a sentence of prose explaining what it captures, what is novel, or how it relates to the previous equation.
- **Overusing display equations.** Three short formulas in a row as displays — consider merging into an `align` block.
- **Assuming the reader knows your notation.** If in doubt, define it.
- **Writing constraints in prose instead of math.** State constraints formally with their mathematical domain; prose paraphrases are supplements, not substitutes.

---

## 7. Figures and Tables

Figures and tables are first-class content, not decoration.

### 7.1 When to Use a Figure vs. a Table vs. Prose

- **Prose** — for one or two values that fit naturally in a sentence ("the solver converged in 12 iterations").
- **Table** — for precise numeric comparison, especially when the reader needs exact values, statistical significance, or many metrics at once.
- **Figure (plot)** — for trajectories, convergence curves, phase portraits, and qualitative behavior where the shape matters more than exact values.
- **Figure (diagram/schematic)** — for system block diagrams, graph structures, geometric constructions, and algorithmic flow.
- Never duplicate the same data in both a table and a figure. Choose the form that best supports the argument and reference it once.

### 7.2 Figure Design

- **File format.** Use vector formats — PDF, EPS, SVG — for plots, diagrams, and schematics. Use raster (PNG) only for photographs or screenshots that genuinely contain pixel data. Never embed JPG for line art.
- **Resolution.** Raster figures should be at least 300~dpi at the printed size.
- **Source files.** Keep the script or source that generated each figure (`*.py`, `*.m`, `*.tex` with PGFPlots/TikZ) inside a `figures/src/` directory.
- **Sizing.** Use `\includegraphics[width=0.8\linewidth]{...}` (relative to text width).
- **Typography in figures.** Match the body text font and size where possible. Axis labels and legends must be readable at the printed size.
- **Color.** Use a colorblind-safe palette (Viridis, Cividis, ColorBrewer). Verify legibility in grayscale. Distinguish series by **both** color and line style or marker shape.
- **Axes.** Always label both axes with quantity and unit ("Time (s)", "Position (m)"). Start the y-axis at zero unless the data warrants otherwise — if not, indicate the truncation explicitly.
- **Error bars / confidence intervals.** Show them whenever results are aggregated over multiple runs. The caption must specify what they represent (standard deviation, 95\% CI, interquartile range).

### 7.3 Table Design

- **Use `booktabs`.** Three rules — `\toprule`, `\midrule`, `\bottomrule` — and nothing else. Never `\hline`, never vertical bars, never double rules.
- **Alignment.** Left-align text columns, right-align integer columns, decimal-align numeric columns with `siunitx`'s `S` column type.
- **Units in the header**, not in every cell.
- **Significant figures.** Be consistent within a column.
- **Highlight the winner.** Bold the best value in each metric column. State the convention in the caption.
- **Footnotes in tables.** Use `\tnote{}` from `threeparttable`, not `\footnote{}`.

### 7.4 Captions

- **Position.** Figure captions go **below** the figure; table captions go **above** the table.
- **Content.** A caption is a self-contained sentence that lets a reader who only skims figures understand what they are looking at without reading the surrounding text.
- **Take-aways belong in the caption** for results figures: "Figure~5.1: Planned trajectory for a representative scenario. The path avoids the obstacle region (shaded) while satisfying the terminal constraint."
- **No empty captions.** Every figure and every table must have a caption.

### 7.5 Cross-References

- Reference every figure and table from the body text by **number**, not by position.
- Use `~` (non-breaking space): `Figure~\ref{fig:trajectory}`, `Table~\ref{tab:results}`.
- Prefer `cleveref`'s `\cref{}` / `\Cref{}`.
- Every figure and table must be **referenced at least once** from the prose.

### 7.6 Sub-figures and Sub-tables

- Use `subcaption` (preferred over `subfig`).
- Number with letters: `(a)`, `(b)`. Reference as `Figure~3.2(a)` or `\cref{fig:traj:open}`.
- Each sub-figure deserves its own short caption; the parent caption explains the overall figure.

### 7.7 Reused or Adapted Figures

- A figure copied from another source must include `Source:~\cite{key}` in the caption.
- A figure adapted: `Adapted from~\cite{key}`.
- Do not paste figures from other papers without attribution.

### 7.8 Common Figure and Table Pitfalls

- **Screenshots of tables** instead of typeset tables.
- **Inconsistent figure styles** across chapters.
- **Trajectory plots with unlabeled axes** or missing units.
- **Tiny labels** illegible at printed size.
- **Legend overlapping data.**
- **Tables with vertical rules and double horizontal rules.**
- **Captions that just repeat the section text.**

---

## 8. Quality Verification

Before declaring a section finished, run through this checklist.

- **Language.** Formal, grammatical, free of contractions ("do not", not "don't"), appropriate for an academic committee.
- **Structure.** Paragraphs are fully developed (typically 3–6 sentences). No bullets standing in for prose. Each paragraph has a topic sentence and a clear function in the argument.
- **Consistency.** Acronyms are defined on first use; terminology is uniform; tense and voice are consistent within each section; mathematical notation is consistent across the entire chapter.
- **Citations.** Every non-trivial claim is supported. Every reference in the bibliography is cited at least once, and every in-text citation appears in the bibliography.
- **Technical correctness.** No hallucinated mechanisms, algorithm properties, or numerical results. Limitations and assumptions are stated explicitly.
- **Mathematical hygiene.** Every symbol is defined before use. Optimization problems are stated in standard form. Theorem statements contain all hypotheses.
- **The ultimate test.** Does the output read like a real graduation thesis draft — not a blog post, slide deck, marketing copy, or product documentation?

---

## 9. Common Pitfalls to Avoid

- **Bullet-point hell.** Long sequences of bullets are a sign that prose has not been written yet. Convert them to paragraphs unless the content is genuinely enumerative.
- **First-person narration of the thesis process.** "I struggled to choose an approach, but eventually decided..." belongs in a blog post, not a thesis.
- **Vague quantifiers.** "Significantly faster", "much better", "a lot of iterations" — replace with measured values or remove.
- **Forward references without grounding.** Do not say "as we will see" if the corresponding section does not yet exist or has not been outlined.
- **Marketing tone.** "This thesis presents a novel, powerful, and revolutionary framework..." — drop the adjectives; let the results make the case.
- **Translated idioms.** Phrases natural in the author's first language often translate to redundant or awkward English ("it can be said that", "with the aim of", "in order to be able to"). Rewrite the meaning, not the words.
- **Prose-only problem statements.** An optimization problem or planning problem described only in prose is ambiguous. Always provide a formal mathematical statement in addition to the prose description.
- **Conflating problem formulation with solution method.** The problem formulation section defines what is to be solved; the methodology section explains how. Keep these separate and cross-reference explicitly.

---

## 10. Worked Example

**Rough note (input):**

> sec 2 — explain why we model the robot as a dynamical system. state = position + velocity, control = force/torque. continuous time, need to discretize to simulate. constraints on state and control because of physical limits.

**Polished thesis prose (output):**

> The robot is modeled as a continuous-time dynamical system in which the state $\mathbf{x}(t) \in \mathbb{R}^n$ encodes the configuration and its time derivative, and the control input $\mathbf{u}(t) \in \mathbb{R}^m$ represents the generalized forces or torques applied by the actuators. The evolution of the state is governed by the ordinary differential equation
>
> $$\dot{\mathbf{x}}(t) = f\bigl(\mathbf{x}(t),\,\mathbf{u}(t)\bigr), \quad t \in [t_0, t_f],$$
>
> where $f \colon \mathbb{R}^n \times \mathbb{R}^m \to \mathbb{R}^n$ is assumed to be continuously differentiable. The state and control are subject to the constraints $\mathbf{x}(t) \in \mathcal{X}$ and $\mathbf{u}(t) \in \mathcal{U}$, where $\mathcal{X} \subset \mathbb{R}^n$ and $\mathcal{U} \subset \mathbb{R}^m$ are compact sets that encode the physical limits of the platform — joint angle limits, velocity bounds, and actuator saturation, respectively.
>
> For numerical simulation and trajectory optimization, the continuous-time dynamics are discretized over a uniform time grid $\{t_k\}_{k=0}^{N}$ with step size $h = (t_f - t_0)/N$. The resulting discrete-time system $\mathbf{x}_{k+1} = f_d(\mathbf{x}_k, \mathbf{u}_k)$ serves as an equality constraint in the finite-dimensional problem formulated in Section~3.2.

Notice how the polished version: defines every symbol before or immediately after it appears, presents the dynamical equation in standard display form with correct punctuation, separates the continuous model from the discrete approximation, cross-references the next section, and keeps the physical interpretation anchored to the mathematics without naming any specific discretization technique.
