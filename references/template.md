# Company Brain Template

This is the full target structure for a company brain. Not every company needs every file. Start with the basics (marked with ★) and grow from there.

```
company-brain/
├── AGENTS.md ★                      # Master index — who we are, how to navigate this brain
├── resources.md ★                   # Canonical URLs — website, docs, blog, socials, product pages
│
├── external/                        # Public-facing brain — what any agent can see
│   ├── identity/
│   │   ├── about.md ★              # Mission, vision, values, origin story
│   │   ├── brand-voice.md ★        # Tone, vocabulary, do's and don'ts
│   │   ├── style-guide.md          # Writing style, content formatting rules
│   │   └── design-system.md        # Visual language, colors, typography, components
│   ├── products/
│   │   ├── overview.md ★           # Product suite, how they fit together
│   │   ├── product-a/
│   │   │   ├── description.md
│   │   │   ├── features.md
│   │   │   ├── pricing.md
│   │   │   └── faq.md
│   │   └── product-b/
│   │       └── ...
│   ├── support/
│   │   └── playbook.md             # Public support scripts, common Q&A
│   └── company-story.md            # The narrative you want the world to know
│
└── internal/                        # Full picture — need-to-know access per team/role
    ├── identity/
    │   ├── internal-comms-voice.md  # How we talk internally (Slack, all-hands, postmortems)
    │   └── culture.md ★            # Values in practice, decision-making norms
    │
    ├── products/
    │   ├── roadmap.md              # → Points to Linear, Jira, Asana, or Notion
    │   ├── bets.md                 # Longer-term strategic bets
    │   ├── product-a/
    │   │   ├── architecture.md     # Technical design, system dependencies
    │   │   ├── metrics.md          # Internal KPIs, dashboards
    │   │   └── known-issues.md     # Bugs, tech debt, workarounds
    │   └── product-b/
    │       └── ...
    │
    ├── business/
    │   ├── model.md                # How we make money
    │   ├── strategy.md             # Where we're headed and why
    │   ├── competitors/            # One file per competitor
    │   │   ├── competitor-a.md
    │   │   └── competitor-b.md
    │   └── market.md               # Industry context, positioning
    │
    ├── operations/
    │   ├── departments/            # One file per department
    │   │   ├── engineering.md
    │   │   ├── marketing.md
    │   │   ├── sales.md
    │   │   └── support.md
    │   ├── processes/              # Key workflows and SOPs
    │   │   ├── onboarding.md
    │   │   ├── incident-response.md
    │   │   └── release-process.md
    │   └── policies/
    │       ├── security.md
    │       ├── data-handling.md
    │       └── compliance.md
    │
    ├── people/
    │   ├── org-chart.md            # → Points to Deel/Gusto/BambooHR
    │   ├── team/                   # Executives, leads, key people
    │   │   ├── ceo.md
    │   │   ├── head-of-product.md
    │   │   └── ...
    │   └── working-norms.md        # How we communicate, make decisions, meet
    │
    ├── engineering/
    │   ├── repos.md                # → Points to GitHub/GitLab
    │   ├── standards.md            # Coding standards, PR process, review expectations
    │   └── architecture.md         # System design, infrastructure overview
    │
    ├── knowledge/
    │   ├── documentation.md        # → Points to docs site, Confluence, Notion wiki
    │   ├── playbooks/              # Sales playbooks, support scripts, marketing guides
    │   └── glossary.md             # Internal terminology and acronyms
    │
    └── rules/
        ├── agent-instructions.md ★ # How agents should behave and interact
        ├── access-control.md       # What's public, internal, restricted
        └── guardrails.md ★         # What agents should never do or share
```

## Key Principles

When generating files from this template:

1. **Don't repeat yourself.** If knowledge lives in another system (docs site, Jira, GitHub), point to it. Don't copy it.
2. **MECE.** Every piece of knowledge has one home. No overlapping content across files. "Collectively exhaustive" means different things for internal vs external — the external brain covers what you'd want any outside agent to know, not everything.
3. **Start small.** Generate the ★ files first. Everything else is additive.
4. **Write for agents.** Be explicit, define terms, avoid ambiguity. Agents read literally.
5. **Mark gaps.** Use `<!-- TODO: ... -->` for sections you don't have enough info to fill.
6. **Use pointers.** `→ Points to [tool/URL]` for data that lives in other systems.
