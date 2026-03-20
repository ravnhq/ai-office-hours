# AI Development Office Hours - Episode 002

## Meeting Metadata

- **Series:** AI Development Office Hours
- **Episode:** 002
- **Cadence:** Bi-weekly
- **Participants:** Pedro Guimaraes, Donovan Hiland, jorgehurtado, josegomes, Lucas Branco

## TL;DR

Pedro walks through the CLAUDE.md file -- what it is, how to structure it, where to put it, and how to keep it useful over time. The core message: keep it short, keep it specific, and treat it as a living document. Donovan adds a warning about contradictions creeping in from skills and plugins, and together they demo `/context` and `/insights` as tools for auditing your setup.

## Key Topics

- **CLAUDE.md fundamentals** -- Purpose, scope types, and placement within projects
- **Conciseness is critical** -- Why bloated CLAUDE.md files hurt more than they help
- **What to include vs. exclude** -- Actionable rules in, vague platitudes out
- **Contradictions and conflicts** -- How skills and plugins silently break your rules
- **Memory vs. CLAUDE.md** -- When to use each and the difference between them
- **Continuous improvement** -- Treating CLAUDE.md as a living, team-shared document

### CLAUDE.md Fundamentals

Pedro explains that CLAUDE.md (also called Agents MD or Gemini MD depending on the tool) is a set of behavioral and technical rules that prevent the AI from re-discovering your patterns every session. There are multiple scope levels:

- **Global (user-level)** -- Applied to every project; put non-project-specific standards here (functional patterns, commit style, TDD preferences)
- **Project-level** -- Shared with the team, committed to the repo, treated as living documentation
- **Subdirectory-level** -- Loaded when Claude navigates that directory (e.g., a `components/` CLAUDE.md for component conventions)
- **Local (gitignored)** -- Project-specific but personal; not shared with the team

### Conciseness Is Critical

Research shows LLMs cannot follow too many instructions at once. A bloated CLAUDE.md causes:

- **Context pollution** -- Too many rules loaded every session
- **Priority confusion** -- The model can't distinguish important rules from less important ones
- **Staleness** -- Larger files are harder to maintain and go stale faster
- Claude's system prompt allows it to ignore CLAUDE.md content it deems irrelevant, and this happens more often with bloated files

Pedro recommends keeping it under 100 lines, ideally around 60.

### What to Include vs. Exclude

**Include:** Specific, actionable rules with clear do/don't framing -- commands for running tests/builds/staging, disallowed patterns, dependency approval requirements, explicit conventions.

**Exclude:** Explanations of technologies (already in training data), vague directives like "write clean readable code" or "be helpful," code snippets (reference your own codebase instead).

### Contradictions and Conflicts

Donovan shares a real experience where a Vercel skill contradicted his CLAUDE.md, and Claude kept choosing the wrong rule. Solutions:

- If Claude repeatedly makes the same mistake, ask it to analyze which rules are unclear or contradictory
- When you have contradictions, make them explicit: "Always use functional components, except for error boundaries where we use class components"
- Be intentional about what you bring into the project -- skills, plugins, and external configs all add rules

### Memory vs. CLAUDE.md

Pedro demos the memory file (`~/.claude/` in the home folder). Key differences:

- Memory is auto-managed by Claude, not committed to the project
- Best for solo workflows; CLAUDE.md is better for team-shared conventions
- Memory can be disabled if you want to keep things simple
- Periodically check memory for things worth promoting to CLAUDE.md

### Continuous Improvement

- Ask Claude to add rules to CLAUDE.md when you spot repeated mistakes
- Ask Claude to help with wording for maximum effectiveness
- Periodically audit: Is the rule still true? Still helping? Can it be rephrased?
- Remove stale rules -- no rules is better than bad rules
- Share CLAUDE.md improvements in pull requests, code reviews, standups, and team channels

## Action Items

- **Everyone:** Create a CLAUDE.md in your project if you don't have one (use `/init` to generate a starting point)
- **Everyone:** If you already have one, trim it to under 100 lines and remove stale or vague rules
- **Everyone:** Run `/context` to audit what's consuming your context window
- **Everyone:** Run `/insights` to get personalized workflow suggestions
- **Everyone:** Share CLAUDE.md improvements in code reviews and team channels
- **Donovan & Pedro:** Post meeting recording and slides; gather feedback on format

## Quotes

> "Do not let it go stale. If something is not working, remove it from there. It's pretty much a living document." -- Pedro Guimaraes

> "If you feel like it continually messes something up, you can also ask it to analyze what of the rules that it has are unclear or contradictory." -- Donovan Hiland

> "It's better to not have anything than having stale rules or alternative rules." -- Pedro Guimaraes

> "LLMs, they're programmed to be super helpful all the time... they love scope creep, so you gotta try to tame it down a little bit." -- Pedro Guimaraes
