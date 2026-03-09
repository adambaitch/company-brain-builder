# Company Brain Builder

A Claude skill that helps you build a structured, agent-readable knowledge base for your company. Think of it as a centralized "brain" — a set of markdown files that represent everything your company *is*, organized so AI agents can actually use it.

You give it your website and some context. It researches, asks smart questions, and generates a starter set of files you can drop into any repo or workspace.

## Why

AI agents are only as good as the context they have. Most companies feed agents scattered docs, stale wikis, and tribal knowledge trapped in Slack threads. A company brain gives every agent — and every teammate — one place to look.

This skill does the tedious part for you: it builds the first draft.

## How to Install

### Option 1: Install with the skills CLI (recommended)

```bash
npx skills add adambaitch/company-brain-builder
```

Works with Claude Code, Cursor, Codex, and other agents that support [SKILL.md](https://github.com/anthropics/skills).

### Option 2: Manual install

Copy the `SKILL.md` and `references/` folder into your Claude skills directory (e.g., `.claude/skills/company-brain-builder/`).

## How to Use

Once installed, tell Claude:

> "Help me build a company brain"

The skill runs in three phases:

1. **Research** — You share your company's website and public links. It scrapes them to build an initial picture.
2. **Interview** — It asks targeted questions in rounds to fill gaps the research couldn't cover.
3. **Generate** — It produces a starter set of markdown files, split into `external/` (public-facing) and `internal/` (full picture).

After generating, it helps you think through hosting, permissions, and how to keep the brain alive.

## What It Produces

A `company-brain/` folder with starter files:

```
company-brain/
├── AGENTS.md              # Master index — who you are, how to navigate this
├── resources.md           # Canonical URLs
├── external/
│   ├── identity/
│   │   ├── about.md       # Mission, story, what you do
│   │   └── brand-voice.md # How you sound
│   └── products/
│       └── overview.md    # Products, who they're for
└── internal/
    ├── identity/
    │   └── culture.md     # How you work, decision-making norms
    └── rules/
        ├── agent-instructions.md  # How agents should behave
        └── guardrails.md          # What agents should never do
```

It generates more files if you give it enough context — per-product pages, competitive intel, glossaries, process docs. See `references/template.md` for the full target structure.

## The Article

This skill is the companion to [Your Company Needs a Brain. Here's How to Give It One](https://adambaitch.substack.com) — a walkthrough of why centralized, agent-readable knowledge bases matter and how to build one.

## License

MIT
