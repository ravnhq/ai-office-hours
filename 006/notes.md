# AI Development Office Hours — 2026-04-24

- **Date:** 2026-04-24
- **Duration:** 38:22
- **Grain:** https://grain.com/share/recording/e091d9ac-e241-4a2c-b875-a5ddd36b0ab6/uZDwrEUKpsqYbudpJtz6MjxsqlE8iwMnmjbqnyIK
- **Format:** Open Q&A (no presentation)
- **Missing artifacts:** `recording.mp4`

## TL;DR

Open Q&A session. Themes: how to bootstrap codebases (greenfield and brownfield) so AI can read them; whether worktrees are worth the setup cost; and how to introduce AI features (skills/hooks/rules) into existing projects without being overwhelmed by options. Recurring advice: start small, find a problem first, then reach for a tool — not the other way around.

## Key Topics

### Setting up a codebase for AI to understand (Obed)
- Greenfield: same approach as writing it yourself — define an architecture, enforce it with linter rules **in code**, not in agent prompts.
- Assume the agent will mess up. If it *can* work around a rule, it will.
- Some people add a short comment at the top of every file explaining its purpose. Pedro hasn't tried this but it tracks with the fact that LLMs have a strong bias toward the top and bottom of files.
- Always pair deterministic enforcement (linter, tests, mutation tests, LSP) with the agent rules.
- LSP is underused: when Claude changes a function signature, the LSP throws warnings immediately — another deterministic signal the agent can read.

### Brownfield projects (Afonso)
- Afonso's prior company: 8-9 repos of legacy spaghetti, AI made constant wrong assumptions.
- Workflow: every time Claude got confused, document the gotcha in memory + CLAUDE.md. Especially around bad variable names and DB column names.
- Pedro's incentive analogue: greenfield mobile app cloning an existing web dashboard with complex financial rules. The bootstrap was a short diagram + rules sheet from Oksana. From there, Claude + Codex queried a local copy of the dashboard to map endpoints and DB structure. Lots of trial and error; complex rules always confirmed with a human.

### Worktrees (Juan)
- Pedro: limited personal use. Hard to keep multiple parallel tasks in his head. Prefers sequential work as fast as possible.
- Pain points:
  - Annoying setup (copy `.env`, run `pnpm install`) — Conductor lets you script this per-worktree.
  - Agent gets lost — doesn't realize it's on a different branch.
  - Reviewing 3-4 concurrent worktrees can negate the time savings.
- Donovan: worktrees pay off when verification is automated and high-confidence. If you still have to manually review everything, you're just queueing work for yourself.
- Good worktree use cases:
  - Backlog of small bugs with clear repro + verification steps.
  - Trying multiple implementation approaches for the same feature in parallel.
- Investing in tests/formatters/linters is what makes worktrees safe — otherwise "code smells" pile up.

### Workflow questions (Raul)
- Pedro: still mostly Claude + plan mode. Combines related tickets into one session when they touch the same area.
- Tip: ask the planner to make work testable as early as possible, so course-correction is cheap.
- Bake `git add && git commit` into every plan checkpoint — if step 70 breaks, you can rewind to step 60 instead of starting over.

### Where to start adding AI features (Hiago)
- The space is overwhelming on purpose. Don't try to learn everything before starting.
- **Pedro:** progressive disclosure for CLAUDE files.
  - Root `CLAUDE.md` = index. "Look here for X, look there for Y."
  - Sub-directory `CLAUDE.md` files for module-specific rules (test/, ui/, etc.).
  - Coverage rules can vary by module (100% on core, integration-first elsewhere).
- **Donovan:** start with plan mode and nothing else. When you hit a real problem, look for the tool that solves *that* problem. Don't shop for tools first.
- Make every rule **actionable**. "Don't use bun" → "Don't use bun, use pnpm instead." Same as giving advice to a person: tell them what to do, not just what not to do.
- Donovan's analogy: same as parenting kids — "stop doing X" doesn't work nearly as well as "do Y instead."

## Action Items

- [ ] **Obed:** Send Pedro the Pinterest link/video about setting up codebases for AI.
- [ ] **Donovan:** Compile outstanding questions and move some to the next meeting.
- [ ] **Donovan:** Set up a question-queue system and run weekly office hours sessions.
- [ ] **All:** Collect and write down AI questions during the week for the next session.

## Quotes

> "Always work with the assumption that the agent will mess up. And if the agent can work around anything, it will also do that."
> — Pedro Guimaraes

> "It's better to give some actionable advice instead of just saying 'don't do that.' Same as with people — if they don't know what to do, they're just going to hide it or work around what you said."
> — Pedro Guimaraes

> "Don't worry about all the stuff before you start. Get into plan mode. As you find problems, find solutions to those problems."
> — Donovan Hiland

> "Claude is like your child — and you need to treat it that way."
> — Donovan Hiland
