# AI Development Office Hours — 2026-04-17

- **Date:** 2026-04-17
- **Duration:** 52:21
- **Grain:** https://grain.com/share/recording/57d5d3b8-c1e6-4d30-8fe9-ad31b8881402/BTjwnNdmAI51MLmC9MrrzW85GC7eUmpiERymqngU
- **Topic:** Harness Engineering (Pedro presentation) + Q&A
- **Missing artifacts:** `recording.mp4`, `presentation.*` (not pulled from Grain)

## TL;DR

Pedro introduced "harness engineering": everything you build around a non-deterministic model so it behaves reliably — system prompts, CLAUDE.md/agents.md, MCPs, sub-agents, hooks, skills, memory. The deterministic levers (hooks, programmatic back-pressure) always win; everything else is a suggestion the agent can ignore. Donovan announced a Slack reorg into AI Random / AI Curated / AI Help to scale knowledge sharing.

## Key Topics

### What is a harness?
- The model is non-deterministic by design — that's what makes it useful, but also unpredictable.
- The harness = system prompt + user prompt + CLAUDE.md/AGENTS.md + tools (bash, MCPs, CLIs) + sub-agents + hooks + skills + memory.
- Quote (Mitchell Hashimoto): "Everything you add to context might help, but it also might make the agent dumber." Late-session noise can wreck output.

### Six levers, ranked by determinism
1. **Hooks + programmatic back-pressure** — deterministic, always wins. Hooks trigger on lifecycle events (PostToolUse, Stop, etc.) and can run any script; output goes back to the session.
2. **CLAUDE.md / rules folder / AGENTS.md** — suggestion only. Human-written rules beat LLM-generated ones (the study Pedro cited shows LLM-generated rules degrade performance and burn tokens).
3. **MCPs and skills** — tool definitions live in context permanently. Disable unused MCPs; prefer CLI alternatives (GitHub CLI vs. GitHub MCP). Treat MCP/skill install like adding a package — they run arbitrary code with your agent's permissions.
4. **Sub-agents** — best context-saver. Parent only sees the sub-agent's final report, not all the intermediate tool calls.
   - Wrong way: model by persona (frontend agent, backend agent).
   - Right way: model by scope — file paths + read/write permissions. A reviewer agent without write tools literally cannot mutate code.
5. **Skills / memory** — suggestion only.
6. **Tool output hygiene** — when a tool succeeds, emit one line. Dumping 4,000 lines of passing tests caused another team's LLM to hallucinate.

### Architecture pattern that works well with LLMs: functional core, imperative shell
- Core module: pure functions, no I/O, business logic only.
- Outer shell: services that touch the outside world (API, analytics, logging).
- Linter rule enforced as **error** (not warning): inner layer never imports from outer layer.
- All strings localized from day one.
- Test rules enforced by linter: no `jest.mock` inside core tests; match elements by `testId`, never by text.

### Pedro's incentive project setup
- 2,000+ test cases, tablets supported, full localization, shipped in a month.
- Stop hook checks the transcript for evidence the linter, type-checker, and tests ran. If not, it blocks and tells Claude to run them.
- 7 project-scoped sub-agents: core / service / context / UI component / API-integration / explorer / verifier.
- Global sub-agents: researcher (with web search + Context7), implementer, verifier, reviewer — chained in a loop.
- A `tmux` script auto-attaches Claude to a session with Expo server + iOS logs + Android logs on separate panes. Claude can read logs and even send keystrokes on demand.

### Q&A highlights
- **Carlos:** When is something a hook vs. a CLAUDE.md rule? → CLAUDE.md = short do/don't list, actionable ("don't use X, use Y instead"). Anything you can verify deterministically → hook.
- **Donovan:** How do you tell the agent to prefer CLI over MCP? → Mention the CLI by name in CLAUDE.md ("use `gh` for GitHub", "use `brun` for Bruno requests"). Familiar CLIs (`curl`, `git`, `gh`) don't need explanation; obscure ones get a small doc with the most common invocations.
- **Chat Q:** Do hooks increase token usage? → Negligible. Only the final block message ("you didn't run the linter, run it") leaks back into context.

## Slack reorg (Donovan)
- **#ai-random** (renamed from #ai) — unfiltered chatter, memes, anything goes.
- **#ai-curated** — high-signal only, moderated by the AI team. Discussions go in threads to keep the top level clean. "Raven-blessed" suggestions and news.
- **#ai-help** — questions about skills, hooks, setup. Moderated lightly, anyone can ask.

## Action Items

- [ ] **Pedro:** Share the linter-enforcement Stop hook and help teams fix linter rules.
- [ ] **Donovan:** Schedule recurring weekly Q&A sessions.
- [ ] **Donovan:** Post AI Curated / AI Help channel links in #ai-random and #general.

## Quotes

> "You cannot only trust the models to get better. The models are by design non-deterministic — that's what allows them to do all the kinds of crazy things, but it also means they might just decide to do something else."
> — Pedro Guimaraes

> "Everything you add to your context might be helpful, but it also might make the agent dumber."
> — Mitchell Hashimoto (quoted by Pedro)

> "If the agent can work around the rules, it will. So enforce them with code, not text."
> — Pedro Guimaraes

> "Review your agent configuration. Add the basic hook. Fix your linter rules — don't let them accumulate. Treat the linter as an enforcer."
> — Pedro Guimaraes (closing takeaway)
