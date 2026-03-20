---
marp: true
theme: ravn
paginate: true
footer: "Ravn AI Development Office Hours"
---

<!-- _class: title -->
<!-- _paginate: false -->
<!-- _footer: '' -->

# CLAUDE.md

## The Most Important File in Your Codebase

<div class="divider"></div>

February 2026 · Ravn AI Development Office Hours

---

## The Problem: Groundhog Day

Every session, you start from zero.

<div class="columns">
<div class="card bad">

### Without CLAUDE.md

- Re-explain the stack on every prompt
- Inconsistent code style between sessions
- Claude makes the same mistakes repeatedly
- Copy-pasting context into every conversation
- New teammates get no AI context

</div>
<div class="card good">

### With CLAUDE.md

- Claude knows your project on session one
- Consistent patterns enforced automatically
- Rules persist — mistakes don't repeat
- Context loads silently, every time
- Onboarding AI context ships with the repo

</div>
</div>

---

## What is CLAUDE.md?

A Markdown file that Claude reads **automatically** at the start of every session — no prompt required.

<div class="columns three">
<div class="card accent">

### Persistent Context

Everything Claude needs to know about your project — written once, applied forever.

</div>
<div class="card accent">

### Behavioral Rules

Guard rails and conventions that survive across sessions and across teammates.

</div>
<div class="card accent">

### Team Knowledge

Encode what your team has learned. Every engineer gets the same AI baseline.

</div>
</div>

> **Platform note:** CLAUDE.md works in Claude Code (CLI). It does not apply to claude.ai chat sessions.

---

## Where Does CLAUDE.md Live?

Four scopes — each overrides the broader one below it.

<div class="columns">
<div class="scope-card">

### Global
<span class="path">~/.claude/CLAUDE.md</span>

</div>
<div class="scope-card">

### Project
<span class="path">./CLAUDE.md</span>

</div>
</div>

<div class="columns">
<div class="scope-card">

### Subdirectory
<span class="path">./src/components/CLAUDE.md</span>

</div>
<div class="scope-card">

### Local Override
<span class="path">./CLAUDE.local.md</span>

</div>
</div>

<p class="dim" style="font-size: 0.78em; margin-top: 12px;">
  <strong>+ Managed Policy:</strong> <code>/Library/Application Support/ClaudeCode/CLAUDE.md</code> — org-wide rules deployed by IT/DevOps, applies to all users.
</p>

---

## Where Does CLAUDE.md Live?

<div class="scope-card">

### Global
<span class="path">~/.claude/CLAUDE.md</span>

Applies to **all your projects** — every repo you open, every session you start.

Use it for personal tool preferences, universal coding habits, and default behaviors you want everywhere. Things like "always use bun" or "prefer functional style" if those apply across all your projects.

</div>

---

## Where Does CLAUDE.md Live?

<div class="scope-card">

### Project
<span class="path">./CLAUDE.md</span>

Applies to **this codebase**. Stack conventions, architecture rules, team-wide norms.

This is the most important scope. It lives at the root of your repo and ships with your code. **Commit this.** Every teammate and every Claude session gets the same baseline.

Also supports `.claude/rules/*.md` for modular, topic-specific rules (covered below).

</div>

---

## Where Does CLAUDE.md Live?

<div class="scope-card">

### Subdirectory
<span class="path">./src/components/CLAUDE.md</span>

Applies **only when working in** `src/components`. Module-specific patterns, domain rules, local conventions.

Use this when a specific area of the codebase has its own rules — design system patterns, component API conventions, or domain-specific logic that doesn't belong in the root CLAUDE.md.

</div>

---

## Where Does CLAUDE.md Live?

<div class="scope-card">

### Local Override
<span class="path">./CLAUDE.local.md</span>

**Gitignored.** Your personal preferences that shouldn't be imposed on the rest of the team.

Use it for editor preferences, personal workflow shortcuts, or debugging habits that are yours alone. Add `CLAUDE.local.md` to your `.gitignore` — this file stays on your machine only.

</div>

---

## The Golden Rule

<div class="center">
<h3 style="color: #B7986A; font-size: 1.4em; font-family: 'Calibri', 'Trebuchet MS', sans-serif;">
"Would Claude make a mistake without this line?"
</h3>
<p class="dim" style="font-size: 0.85em;">If no → delete it. If yes → keep it.</p>
</div>

<div class="columns three">
<div class="tier ideal">
<div class="tier-num">< 60</div>
<p class="dim">lines</p>
<h3>Ideal</h3>
<p>Every line earns its place. High signal, zero noise.</p>
</div>
<div class="tier ok">
<div class="tier-num">60–200</div>
<p class="dim">lines</p>
<h3>Acceptable</h3>
<p>Still manageable. Audit regularly for dead rules, it should be a living document.</p>
</div>
<div class="tier warn">
<div class="tier-num">300+</div>
<p class="dim">lines</p>
<h3>Danger Zone</h3>
<p>Context window filler. Important rules are mixed with noise and might be lost.</p>
</div>
</div>

---

## Why Shorter Is Better

<div class="card bad">

### Context Pollution

Every token in CLAUDE.md is a token **not** available for your actual work.

Long files fill Claude's context window before you've written a single prompt.

</div>

---

## Why Shorter Is Better

<div class="card bad">

### Signal Dilution

When everything is a rule, nothing is.

Claude (or other AI agents) can't distinguish between important and noise. Pack as much valuable information as possible, in a concise way.

</div>

---

## Why Shorter Is Better

<div class="card bad">

### Staleness

Long files drift. Having outdated information is worse than having no information at all.

</div>

> The best CLAUDE.md you can write is the one you barely needed to write at all.

---

## Less Is More

<div class="columns">
<div class="card bad">

### 500+ line CLAUDE.md <span class="tag bad">BAD</span>

- Explaining what React hooks are (it has it in its training data and it's capable of reading documentation)
- "Write clean, readable code" (what does this mean? according to who?)
- "Be helpful and concise" (what would it do otherwise? prank you?)
- Outdated architecture diagrams in prose (boring!)
- Duplicating what the codebase itself shows (the best code snippets are the ones that already exist in your codebase)
- Generic best practices Claude already follows*

`*` sometimes it doesn't

</div>
<div class="card good">

### ~40 line CLAUDE.md <span class="tag good">GOOD</span>

- `Always use bun, never npm or yarn`
- Non-obvious naming: `snake_case` for DB, `camelCase` for API
- `Never use any in TypeScript`
- Run tests with: `bun test`
- What this project _does_ in two sentences
- Team-specific tools and their exact invocations

</div>
</div>

---

## Good Rules: Dos and Don'ts

<div class="columns">
<div>

### ✓ Specific and Actionable

<div class="card accent" style="margin-bottom: 10px;">
<p style="font-family: 'Consolas', monospace; font-size: 0.78em; color: #ADB5BD;">Always use <strong>bun</strong>, never npm or yarn</p>
</div>
<div class="card accent" style="margin-bottom: 10px;">
<p style="font-family: 'Consolas', monospace; font-size: 0.78em; color: #ADB5BD;">Never suppress lint errors — rewrite or <strong>ask</strong></p>
</div>
<div class="card accent" style="margin-bottom: 10px;">
<p style="font-family: 'Consolas', monospace; font-size: 0.78em; color: #ADB5BD;">New dependencies require <strong>explicit approval</strong></p>
</div>
<div class="card accent">
<p style="font-family: 'Consolas', monospace; font-size: 0.78em; color: #ADB5BD;">Return <strong>{ data, error }</strong> from all API routes</p>
</div>

</div>
<div>

### ✗ Vague or Obvious

<div class="card bad" style="margin-bottom: 10px;">
<p style="font-family: 'Consolas', monospace; font-size: 0.78em; color: #6B7280;">Write clean, maintainable code <span class="tag bad">Claude's default</span></p>
</div>
<div class="card bad" style="margin-bottom: 10px;">
<p style="font-family: 'Consolas', monospace; font-size: 0.78em; color: #6B7280;">Use good error handling <span class="tag bad">Too vague</span></p>
</div>
<div class="card bad" style="margin-bottom: 10px;">
<p style="font-family: 'Consolas', monospace; font-size: 0.78em; color: #6B7280;">Follow TypeScript best practices <span class="tag bad">Meaningless</span></p>
</div>
<div class="card bad">
<p style="font-family: 'Consolas', monospace; font-size: 0.78em; color: #6B7280;">Be mindful of performance <span class="tag bad">No action defined</span></p>
</div>

</div>
</div>

---

## Rules from Our CLAUDE.md

<div class="columns">
<div>

### Behavioral Constraints

<div class="card accent" style="margin-bottom: 16px;">
<p style="font-family: 'Consolas', monospace; font-size: 0.78em; color: #ADB5BD;">Don't "improve" adjacent code, comments, or formatting.</p>
</div>
<div class="card accent" style="margin-bottom: 16px;">
<p style="font-family: 'Consolas', monospace; font-size: 0.78em; color: #ADB5BD;">State your assumptions explicitly. If uncertain, ask.</p>
</div>
<div class="card accent">
<p style="font-family: 'Consolas', monospace; font-size: 0.78em; color: #ADB5BD;">No "flexibility" or "configurability" that wasn't requested.</p>
</div>

</div>
<div>

### Project & Safety

<div class="card accent" style="margin-bottom: 16px;">
<p style="font-family: 'Consolas', monospace; font-size: 0.78em; color: #ADB5BD;">Prefer JS-only libraries (no native modules) to maintain <strong>Expo Go</strong> compatibility.</p>
</div>
<div class="card accent">
<p style="font-family: 'Consolas', monospace; font-size: 0.78em; color: #ADB5BD;">Linter rules are immutable — never suppress (<code>eslint-disable</code>, <code>@ts-ignore</code>). Rewrite to satisfy. If impossible, ask.</p>
</div>

</div>
</div>

---

## Anatomy of a Good CLAUDE.md

<div class="columns" style="align-items: start;">
<div style="flex: 1.1;">

```markdown
# Project

Task management SaaS. Next.js frontend,
Express API, PostgreSQL.

## Commands

- Dev: pnpm dev
- Test: pnpm test --watch
- Lint: pnpm lint --fix

## Stack & Conventions

- Use pnpm — never npm or yarn
- TypeScript strict — no `any` ever
- snake_case for DB columns, camelCase for JS
- Return { data, error } from all API routes

## Do Not

- Never use console.log (use src/lib/logger)
- Never commit with --no-verify
- Never edit migrations — create new ones
```

</div>
<div style="display: flex; flex-direction: column; gap: 10px; padding-top: 4px;">

<div class="card accent" style="padding: 10px 14px;">
<p style="font-size: 0.76em; margin: 0;"><strong>1. Product context</strong><br><span class="dim">2 sentences max. What it is, what it does.</span></p>
</div>
<div class="card accent" style="padding: 10px 14px;">
<p style="font-size: 0.76em; margin: 0;"><strong>2. Exact commands</strong><br><span class="dim">Specific invocations, not "run tests."</span></p>
</div>
<div class="card accent" style="padding: 10px 14px;">
<p style="font-size: 0.76em; margin: 0;"><strong>3. Non-obvious conventions</strong><br><span class="dim">Things Claude can't infer from the code.</span></p>
</div>
<div class="card accent" style="padding: 10px 14px;">
<p style="font-size: 0.76em; margin: 0;"><strong>4. Hard constraints</strong><br><span class="dim">The "never do this" rules that protect your system.</span></p>
</div>

</div>
</div>

---

## Modular Rules with `.claude/rules/`

When CLAUDE.md starts getting long, split it — don't pad it.

<div class="columns" style="align-items: start;">
<div>

**Directory structure**

```
.claude/
  rules/
    testing.md          # TDD rules, coverage requirements
    api-conventions.md  # Return shapes, error formats
    security.md         # No suppressions, auth patterns
```

Each file is loaded automatically — same as CLAUDE.md. One topic per file, short and auditable.

</div>
<div>

**Path-specific rules** via YAML frontmatter:

```yaml
---
paths:
  - "src/api/**/*.ts"
---
Always return { data, error } from API routes.
Never throw — use the error field instead.
```

Applies only when Claude works in `src/api/`. Rules for other paths are ignored.

</div>
</div>

> Your root CLAUDE.md becomes an index. Domain rules live in focused files. Think of 60 lines as a soft target per file, not a hard cap.

---

## CLAUDE.md Imports

Reference existing docs — no duplication required.

```markdown
# Project

@README                       ← pulls in your existing README
@docs/architecture.md         ← team architecture doc
@.claude/rules/testing.md     ← a specific rules file
```

<div class="columns">
<div class="card accent">

### How it works

- Paths are relative to the importing file
- Recursive imports (up to 5 levels deep)
- Works in CLAUDE.md and rules files alike

</div>
<div class="card good">

### Why it matters

If your team already wrote `docs/git-workflow.md`, import it. Don't rewrite it in CLAUDE.md. Single source of truth.

</div>
</div>

---

## The Self-Improving Pattern

Your CLAUDE.md should evolve as you work — not stay frozen.

<div>
<div class="step">
<div class="badge">1</div>
<div class="step-content">
<strong>Work normally with Claude Code</strong>
<p>Claude hits an edge case or makes an assumption you need to correct.</p>
</div>
</div>
<div class="step">
<div class="badge">2</div>
<div class="step-content">
<strong>Notice the pattern</strong>
<p>Did you rephrase the same correction twice? That's a CLAUDE.md candidate.</p>
</div>
</div>
<div class="step">
<div class="badge">3</div>
<div class="step-content">
<strong>Ask Claude to remember it: <code>Add this to CLAUDE.md: Always follow red green TDD before implementing a new component</code></strong>
</div>
</div>
<div class="step">
<div class="badge">4</div>
<div class="step-content">
<strong>Audit the rule regularly</strong>
<p>Is it still true? Can it be rephrased? Remove stale rules aggressively.</p>
</div>
</div>
<div class="step">
<div class="badge">5</div>
<div class="step-content">
<strong>Commit it to the repo</strong>
<p>CLAUDE.md is team infrastructure. It ships with the code.</p>
</div>
</div>
</div>

---

## Common Mistakes

<div class="columns">
<div class="card bad">

### Explaining things Claude knows

> "React is a UI library for building component-based interfaces..."

**Fix:** Content like this is already part of Claude's training data. Only add what's specific to _your_ project.

</div>
<div class="card bad">

### Rules that contradict each other

> "Always use functional components" + "Use class components for error boundaries"

**Fix:** Be explicit about exceptions. Ambiguity leads to inconsistency.

</div>
</div>

<div class="columns">
<div class="card bad">

### No ownership = no updates

> A 300-line CLAUDE.md created once but never updated.

**Fix:** Establish a routine of maintaining it, suggest improvements in code reviews, share suggestions with your team

</div>
<div class="card bad">

### Mixing global and project rules

> Personal preferences in the project CLAUDE.md imposed on the whole team.

**Fix:** Personal preferences (project) → `CLAUDE.local.md`. Team rules → `CLAUDE.md`.

</div>
</div>

---

## Getting Started Is Easy

<div class="columns" style="align-items: start;">
<div>

### Three steps

<div class="step">
<div class="badge">1</div>
<div class="step-content">
<strong>Run <code>/init</code> in your project</strong>
<p>Claude scans the repo and auto-generates a starting CLAUDE.md.</p>
</div>
</div>
<div class="step">
<div class="badge">2</div>
<div class="step-content">
<strong>Trim the fat</strong>
<p>Remove anything obvious. Add your real conventions. Target under 100 lines and try to get more concise ove time.</p>
</div>
</div>
<div class="step">
<div class="badge">3</div>
<div class="step-content">
<strong>Commit it</strong>
<p>It's team infrastructure. Ship it with the code.</p>
</div>
</div>

</div>
<div>

### What <code>/init</code> produces

<div class="terminal">
<span class="prompt">$</span> claude<br>
<span class="prompt">></span> /init<br>
<br>
<span class="output">Scanning project structure...</span><br>
<span class="output">Detected: TypeScript, React Native, bun</span><br>
<span class="output">Found: package.json, tsconfig.json</span><br>
<br>
<span class="success">✓ Created CLAUDE.md (34 lines)</span><br>
<br>
<span class="output">Review and customize before committing.</span>
</div>

</div>
</div>

---

## CLAUDE.md vs Skills vs Rules

<br>

| | **CLAUDE.md** | **Rules** | **Skills** |
|---|---|---|---|
| **Purpose** | Persistent project context | Topic-specific rule files | Reusable prompt workflows |
| **When active** | Every session, automatically | Every session, automatically | When explicitly invoked |
| **Written in** | Markdown | Markdown + optional YAML frontmatter | Markdown (prompt templates) |
| **Lives in** | `./CLAUDE.md`, `~/.claude/CLAUDE.md` | `.claude/rules/*.md` | `~/.claude/` |
| **Best for** | Stack, conventions, commands | Keeping CLAUDE.md concise | Repeated multi-step tasks |
| **Committed?** | Yes — team infrastructure | Yes | Optional |

<br>

<p class="dim" style="font-size: 0.8em; text-align: center;">All three compose. CLAUDE.md is the foundation everything builds on.</p>

---

## 10 Best Practices

<div class="columns">
<div>

<div class="step">
<div class="badge">1</div>
<div class="step-content"><strong>Aim for around 60 lines</strong><p>Every line is more token usage. It's a guideline, not a hard cap — but make them count.</p></div>
</div>
<div class="step">
<div class="badge">2</div>
<div class="step-content"><strong>Only write what Claude can't infer</strong><p>Trust training. Add project-specifics only.</p></div>
</div>
<div class="step">
<div class="badge">3</div>
<div class="step-content"><strong>Use specific, actionable language</strong><p>"Use bun" not "use the right package manager."</p></div>
</div>
<div class="step">
<div class="badge">4</div>
<div class="step-content"><strong>Include exact commands</strong><p>Not "run tests" — the actual invocation.</p></div>
</div>
<div class="step">
<div class="badge">5</div>
<div class="step-content"><strong>Version control it</strong><p>It ships with the repo. Always.</p></div>
</div>

</div>
<div>

<div class="step">
<div class="badge">6</div>
<div class="step-content"><strong>Ask Claude to add rules as you work</strong><p>e.g. "Add this to CLAUDE.md: always use bun, never npm."</p></div>
</div>
<div class="step">
<div class="badge">7</div>
<div class="step-content"><strong>Audit periodically</strong><p>Delete stale rules ruthlessly.</p></div>
</div>
<div class="step">
<div class="badge">8</div>
<div class="step-content"><strong>Layer your scopes</strong><p>Global for personal, project for team.</p></div>
</div>
<div class="step">
<div class="badge">9</div>
<div class="step-content"><strong>Use <code>CLAUDE.local.md</code> for personal rules</strong><p>Don't impose your preferences on the team.</p></div>
</div>
<div class="step">
<div class="badge">10</div>
<div class="step-content"><strong>Treat it as living documentation</strong><p>If the codebase changed, update the file.</p></div>
</div>

</div>
</div>

---

## Your Action Plan

<div>
<div class="timeline-item">
<div class="timeline-week">Today</div>
<div class="timeline-content">
<strong>Run <code>/init</code> in your main project</strong>
<p>Let Claude generate a starting point. Takes 30 seconds.</p>
</div>
</div>
<div class="timeline-item">
<div class="timeline-week">Day 2–3</div>
<div class="timeline-content">
<strong>Trim and customize</strong>
<p>Delete what's obvious. Add your real conventions. Aim for around 60 lines — treat it as a signal, not a ceiling.</p>
</div>
</div>
<div class="timeline-item">
<div class="timeline-week">Week 1</div>
<div class="timeline-content">
<strong>Commit and share with your team</strong>
<p>Open a PR. Invite teammates to review and add their conventions.</p>
</div>
</div>
<div class="timeline-item">
<div class="timeline-week">Ongoing</div>
<div class="timeline-content">
<strong>Evolve it</strong>
<p>Every time you correct Claude twice, it's a CLAUDE.md candidate.</p>
</div>
</div>
<div class="timeline-item">
<div class="timeline-week">Quarterly</div>
<div class="timeline-content">
<strong>Audit and prune</strong>
<p>Delete stale rules. The goal is fewer lines, not more.</p>
</div>
</div>
</div>

---

## Two Types of Memory

CLAUDE.md is what **you** write for Claude. Auto memory is what **Claude** writes for itself.

<div class="columns">
<div class="card accent">

### CLAUDE.md (you write)

- Project context, team rules, commands
- Committed to the repo
- Applies to all teammates
- You control every line

</div>
<div class="card accent">

### Auto Memory (Claude writes)

- Learnings Claude picks up from your sessions
- Lives in `~/.claude/projects/<project>/memory/`
- Private — never committed to the repo
- Claude updates it automatically as you work

</div>
</div>

> Auto memory is Claude's notes to itself. CLAUDE.md is the team rulebook you set intentionally. You don't need to manage auto memory — just know it exists.

---

<!-- _class: closing -->
<!-- _paginate: false -->

# Start with one file.

<div class="divider"></div>

<p style="font-size: 1em; color: #ADB5BD; max-width: 600px; margin: 0 auto 28px;">
The best CLAUDE.md you can write today is a short one — 20 lines that capture exactly what Claude would get wrong without them.
</p>

<div style="display: flex; gap: 20px; justify-content: center; flex-wrap: wrap;">
<div class="card accent" style="padding: 12px 20px; text-align: center; min-width: 200px;">
<p style="margin: 0; font-size: 0.82em;"><strong>Run</strong> <code>/init</code> today</p>
</div>
<div class="card accent" style="padding: 12px 20px; text-align: center; min-width: 200px;">
<p style="margin: 0; font-size: 0.82em;"><strong>Target</strong> ~60 lines</p>
</div>
<div class="card accent" style="padding: 12px 20px; text-align: center; min-width: 200px;">
<p style="margin: 0; font-size: 0.82em;"><strong>Ship</strong> it with your code</p>
</div>
</div>

<br>

<p class="dim" style="font-size: 0.78em;">
Questions? Ask in <strong>#ai</strong> on Slack · <a href="https://docs.anthropic.com/claude/docs/claude-md">docs.anthropic.com/claude/docs/claude-md</a>
</p>
