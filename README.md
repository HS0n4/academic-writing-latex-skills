# academic-writing-latex

A [Claude](https://claude.com/claude-code) skill for drafting, revising, and polishing academic graduation thesis reports in English. It encodes the conventions a student needs to satisfy an academic committee — formal register, IMRaD-aligned structure, IEEE-style citations, LaTeX-compatible formatting, and strict no-hallucination technical writing.

Use it when you have rough notes, an outline, or an early draft and you want Claude to expand or rewrite the content as proper thesis prose rather than as a chat reply or a blog post.

## What this skill does

When the skill is active, Claude will:

- Write in formal academic English with consistent tense and voice.
- Produce fully developed paragraphs instead of bullet-point summaries.
- Use LaTeX-compatible quotation marks (`` ``...'' ``) so the text compiles cleanly with `pdflatex` / `xelatex`.
- Define every acronym on first use and keep terminology consistent.
- Calibrate certainty with appropriate hedging ("suggests", "indicates") rather than unsupported superlatives.
- Cite credible peer-reviewed sources in IEEE style by default.
- Refuse to invent technical mechanisms, numerical results, or API behaviors — when context is missing, it asks instead of fabricating.
- Follow IEEE conventions for figures, tables, and equations (captions, numbering, cross-references).

See [SKILL.md](SKILL.md) for the complete behavioral specification.

## Installation

### Claude Code (project-level)

Place the skill inside the project where you want it active:

```bash
mkdir -p .claude/skills/academic-writing-latex
cp SKILL.md .claude/skills/academic-writing-latex/SKILL.md
```

### Claude Code (user-level, available in every project)

```bash
mkdir -p ~/.claude/skills/academic-writing-latex
cp SKILL.md ~/.claude/skills/academic-writing-latex/SKILL.md
```

### Claude.ai / Claude Desktop

Upload `SKILL.md` through the Skills interface in your Claude account. Refer to the [official Skills documentation](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) for the current upload flow.

Once installed, Claude loads the skill automatically when a user message matches the triggers declared in the frontmatter (for example, "draft chapter 3", "polish this section", "expand these notes into thesis prose").

## Usage examples

**Expanding rough notes into thesis prose**

> Expand these notes into the Methodology section of my thesis:
> - we use FreeRTOS on Cortex-M4
> - chosen over Zephyr because Zephyr is heavier
> - kernel under 10 kB

Claude will produce structured academic paragraphs that justify the design choice, define acronyms, reference prior sections, and treat rejected alternatives with neutral language. A worked example is included in [SKILL.md §10](SKILL.md#10-worked-example).

**Polishing an existing draft**

> Polish this Introduction so it reads like a graduation thesis rather than a blog post: <paste draft>

**Reviewing for thesis standards**

> Review this Evaluation chapter against thesis standards. Flag bullet-point hell, vague quantifiers, missing citations, and undefined acronyms.

## Scope and tradeoffs

This skill prioritizes academic rigor and depth over brevity. Output will be longer and more deliberate than a typical chat reply. It is **not** appropriate for:

- Marketing copy, blog posts, or product documentation.
- Slide decks or executive summaries.
- Casual explanations or quick chat answers.

The default citation style is **IEEE**. Override it explicitly if your university template requires APA, ACM, or another format.

## Project layout

```
.
├── LICENSE       # MIT license
├── README.md     # this file
└── SKILL.md      # the skill itself, with YAML frontmatter
```

## Contributing

Issues and pull requests are welcome — particularly for additional worked examples, university-specific citation templates, and refinements to the common-pitfalls section.

## License

Released under the [MIT License](LICENSE).
