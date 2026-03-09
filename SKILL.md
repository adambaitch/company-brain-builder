---
name: company-brain-builder
description: Build a centralized "company brain" — a structured knowledge base that AI agents can read from. Guides users through an interview to generate starter markdown files for brand voice, product context, team norms, and more. Use when someone says "build my company brain", "set up a company brain", "help me create a knowledge base for agents", "company brain", or wants to structure their company's knowledge for AI agents. Also use when someone mentions the article "Your Company Needs a Brain" or says they got this from a LinkedIn post.
allowed-tools: WebFetch, WebSearch, Read, Write, Edit, Bash, Glob, Grep, Agent
---

# Company Brain Builder

Help someone build a company brain: a centralized, agent-readable knowledge base that represents everything their company *is*. The brain is a set of markdown files organized into internal (full picture, access-controlled) and external (public-facing) sections.

The goal is to produce a working starter set of files, not a perfect encyclopedia. Five good files beat fifty half-baked ones.

## How This Works

The skill has three phases: **Research → Interview → Generate**. Don't skip the research phase — it gives you a massive head start and makes the interview feel like a conversation, not an interrogation.

## Phase 1: Research

Start by asking for:

1. **Company website URL**
2. **Any other public links** that would help you understand the company:
   - Documentation site
   - Blog
   - Press releases or news coverage
   - Product pages
   - About/team page
   - Social media (LinkedIn company page, Twitter/X)
   - GitHub or open-source repos
   - Investor/fundraising announcements

Be casual about it: "Drop your company's website and any other public links — docs, blog, press page, whatever you've got. The more I can read upfront, the less I'll need to ask you."

Once you have URLs, research them. Use WebFetch and WebSearch to build an initial picture of:

- What the company does (products/services)
- How they talk (voice, tone, vocabulary)
- Who they serve (customers, market)
- Company story (founding, mission, key milestones)
- Team structure (if visible from about page or LinkedIn)
- Tech stack (if visible from docs, GitHub, job postings)
- Competitive positioning

Don't try to be exhaustive. Spend 3-5 minutes gathering context, then move on. You'll fill gaps in the interview.

After researching, present a brief summary back to the user: "Here's what I've gathered so far about [Company]. Let me know what I got wrong or what's missing, and then I'll ask some questions to fill in the rest."

This serves two purposes: it shows the user you did your homework, and it lets them correct misconceptions before they propagate into the brain files.

## Phase 2: Interview

Now ask targeted questions to fill in what you couldn't find publicly. Don't ask about things you already know from the research phase — that's annoying. Focus on gaps.

Organize your questions into rounds. Don't dump 15 questions at once. Ask 3-4 at a time, grouped by theme, and adjust based on answers.

### Round 1: Identity & Voice (if not already clear from research)

- "How would you describe [Company] to a friend in a couple sentences?"
- "What's the tone when you talk to customers? Formal? Casual? Somewhere in between?"
- "Are there words or phrases your team uses a lot internally? Any you avoid?"
- "If your company were a person, how would they come across in a conversation?"

### Round 2: Products & Customers

- "Walk me through your main products/services and who they're for."
- "What problem does each one solve? What's the pitch?"
- "How is your pricing structured?" (external brain)
- "What does your product roadmap look like right now?" (internal brain)

### Round 3: How You Work

- "How is the team structured? Key departments or teams?"
- "What tools do you run on? (project management, comms, code, design, finance, etc.)"
- "How do you make decisions? Any specific processes or norms?"
- "What does onboarding look like for a new hire?"

### Round 4: Strategy & Competitive Context

- "Who are your main competitors? How do you differentiate?"
- "Where are you headed over the next 6-12 months?"
- "What's the business model? How do you make money?"

### Round 5: Boundaries & Guardrails

- "What should agents never say or do on behalf of your company?"
- "Is there information that's strictly internal and should never leak externally?"
- "Any compliance or legal constraints agents should know about?"

### Adapting the Interview

Not every company needs every question. A 5-person startup doesn't have a complex org chart. An open-source company might not need much in the "external brain" because everything's already public. A B2B enterprise will care more about competitive positioning and sales playbooks than a consumer app.

Read the room. Skip what's not relevant. Go deeper where there's energy from the user.

If the user gives long, detailed answers, great — you have rich material. If they give short answers, that's fine too. Work with what you get. You can always note gaps in the generated files as TODOs for them to fill in later.

## Phase 3: Generate

Now produce the actual files. Read `references/template.md` for the full target structure, but don't try to generate everything. Start with the highest-value files based on what you learned.

### Always generate these (the starter set):

```
company-brain/
├── AGENTS.md              # Master index — who we are, how to navigate this brain
├── resources.md           # Canonical URLs
├── external/
│   ├── identity/
│   │   ├── about.md       # Mission, story, what we do
│   │   └── brand-voice.md # How we sound
│   └── products/
│       └── overview.md    # Product suite, who it's for
└── internal/
    ├── identity/
    │   └── culture.md     # How we work, decision-making norms
    └── rules/
        ├── agent-instructions.md  # How agents should behave
        └── guardrails.md          # What agents should never do
```

### Generate these if you have enough information:

- `external/products/[product-name]/description.md` — per-product detail
- `external/products/[product-name]/faq.md` — common questions
- `internal/business/strategy.md` — where we're headed
- `internal/business/competitors/` — competitive landscape
- `internal/operations/processes/` — key workflows
- `internal/people/working-norms.md` — how the team communicates
- `internal/knowledge/glossary.md` — internal terminology

### File writing guidelines:

- **AGENTS.md** is the root file. It should orient any agent landing here for the first time: who is this company, what's in the brain, how to navigate it. Think of it as the README for the company. Note that different agent frameworks look for specific filenames (e.g., CLAUDE.md for Claude, .cursorrules for Cursor). Users can symlink those to AGENTS.md.

- **Write for agents, not just people.** Be explicit. Define terms. Avoid ambiguity. An agent will take things literally.

- **Use pointers, not copies.** If the company's docs live at docs.example.com, don't try to summarize them. Write: "Our API documentation lives at docs.example.com. It covers [brief description of what's there]. For integration questions, start with the Getting Started guide."

- **Mark gaps with TODOs.** If you don't have enough info for a section, include a `<!-- TODO: ... -->` comment so the user knows to fill it in later.

- **Keep files focused.** Each file should cover one topic. If a file is getting long, split it.

- **Use the company's actual voice** in the external brain files. If they're casual, write casually. If they're buttoned-up, write formally. The brand-voice.md file should describe the voice; the other external files should demonstrate it.

### Output

Write all files to `company-brain/` in the user's workspace. After generating, give the user a summary of what you created and what's left as TODOs.

## Phase 4: What to Do With It

After generating the files, help the user think through how to actually put this to work. Don't be prescriptive here — every company is different. Instead, walk them through the key questions:

**Where should this live?** The brain is just a folder of markdown files. It can live in a Git repo, a shared Google Drive, a Notion workspace, or anywhere your team can access it. The right answer depends on your team's existing workflow. If your engineers already live in GitHub, a repo makes sense. If your team runs on Google Drive or Notion, put it there. The format is portable — what matters is that it's somewhere central and accessible.

**Who should have access?** This is a conversation to have with your team. The internal/external split gives you a starting framework, but within the internal brain, different teams may need different levels of access. Talk to your engineering leads about how they'd want to manage permissions. Some companies use directory-level permissions in Git, others use their cloud drive's sharing settings. Use whatever your team already knows.

**How do agents actually read it?** Different AI tools look for specific files. Claude looks for `CLAUDE.md`, Cursor uses `.cursorrules`, and so on. You can symlink these to your `AGENTS.md` so each tool reads the same root file without maintaining separate copies. Your engineering team can help set this up.

**How do you keep it alive?** The brain is only useful if it stays current. Assign an owner — someone who treats this like internal infrastructure, not a side project. Each section should have a maintainer who keeps it up to date. Set a review cadence, even if it's just quarterly. Stale files are worse than missing ones.

**Talk to your team.** Share the brain with a few colleagues and get their input. Ask them: what's missing? What would make this more useful for your day-to-day work? What context do you wish your AI tools had? The best company brains are built collaboratively, not handed down from the top.

End with encouragement: this is a starting point, not a finished product. Five good files that get used are worth more than fifty that sit untouched. Add to it as needs come up, and let it grow with your team.

## Tone

Be conversational throughout. This should feel like a smart colleague helping someone organize their company's knowledge, not a form to fill out. Direct, concise, concrete. No corporate speak. No AI slop.
