# AI Development Office Hours — 2026-05-08

- **Date:** 2026-05-08
- **Duration:** 34:28
- **Grain:** https://grain.com/share/recording/423462b0-f246-45d9-828a-a6ba9161fb77/uW0iida5ehloWKgkNm7IgmKYjl2JqG4mELxNFjFF
- **Format:** Open Q&A
- **Missing artifacts:** `recording.mp4`

## TL;DR

Q&A on vendor lock-in (we're not locked in — Codex, Gemini, OpenCode + Chinese models are real alternatives), permission management with wildcards + deny lists, preserving context across sessions, LSP support in Claude Code vs. OpenCode, MCP vs. plain scripts, and Pedro's feature-planning workflow (talk to the requester first, brainstorm options with Claude, present with a recommendation).

## Key Topics

### Vendor lock-in with Claude (Kevin)
- Not currently planning to officially support other agents, but watching the space.
- Anthropic's recent moves on usage/subscriptions have shaken some of Pedro's trust.
- Local models will eventually become affordable; US companies (Fireworks, Cerebras) are increasingly serving Chinese models.
- If we ever had to migrate: Codex (with a Claude-config import), Gemini, OpenCode with any provider — most things (skills, sub-agents, MCPs, hooks) are now standardized across tools.

### Managing permissions to stop the prompt fatigue (Frank Paris)
- Use wildcards: `npm *` → blanket allow.
- Pair with a deny list to carve out destructive variants: deny `npm upgrade`, `npm remove`, `npm push`.
- Read-only commands like `rg` deserve a wildcard, no exceptions — never approve them again.
- Built-in command `/code` (or the slash command Pedro referenced) reviews recent sessions and offers to whitelist frequently-prompted commands.

### Preserving context across sessions (Kevin)
1. **Proactive `/compact`** — pass a prompt to bias what gets prioritized: `/compact we're about to do X, keep details about Y`.
2. **Export** the session contents to clipboard or file.
3. **TODO file inside the project** — Claude marks tasks done as it goes. New sessions read the file and resume cleanly.

### OpenCode vs. Claude Code (Kevin)
- Kevin likes OpenCode's UX and especially its **LSP integration** — diagnostics fire immediately on file write, so Claude self-corrects before a full build.
- Claude Code also supports LSP, but it's hidden behind config. Action item: Kevin + Pedro to write a guide.

### MCP protocol vs. plain scripts
- Individually: scripts are usually faster and more deterministic. If you can ask Claude to write a shell script that calls an API, do that.
- Org-wide: MCPs win for distribution — Claude AI org settings can push connectors to everyone, no install step.
- Same rule applies to skills: bundling into a plugin matters when you need versioning + distribution.

### Codex GPT 5.5 vs. Claude Code
- Both are very good. Experiment. If you already have a personal ChatGPT subscription, install Codex and ask it for a second opinion — it often catches things Claude missed.

### Build a "review super-agent" or use the built-in review skill? (Hua)
- Built-in review skill exists (confirmed by Juan during the call).
- Juan found the built-in skill produced **fewer false positives** than his custom reviewer sub-agent.
- Either way, don't accept review output at face value — there's a tendency for AI reviewers to keep finding "improvements" forever. Treat suggestions as starting points; a human breaks the loop.

### Pedro's feature-planning framework
1. Talk to the requester first. Understand the actual problem before touching code.
2. Brainstorm/research with Claude — list options with explicit pros/cons.
3. Present options to the team or stakeholder with a **recommendation** and your reasoning.
4. Double-check the decision with the team before committing.

### Skills vs. CLAUDE.md vs. rules — when to use which
- **CLAUDE.md**: general project-wide directives. Always loaded.
- **`.claude/rules/*.md`**: scoped to specific paths or modules (UI rules, test rules).
- **Skills**: reusable workflows you invoke on demand. Don't pollute context until needed.
- Lazy mode tip from Donovan: paste your prompt into Claude and ask it to convert it into a skill for you.

### Ravn Claude organization access (Donovan)
- We have an org. Whether you use it depends on the project — client tooling takes precedence.
- For Anthropic courses and the Claude Architect certificate (coming soon), use the Ravn account.
- Anyone with access questions → Donovan, your engineering manager, or your PM.

## Slack reorganization (Kevin)
- New channel: **#ai-office-hours** — Kevin will cross-post chat questions and resources here so nothing gets lost between meetings.
- Donovan to share an anonymous feedback link for the meeting itself.

## Action Items

- [ ] **Kevin:** Cross-post meeting questions and resources to the new #ai-office-hours Slack channel.
- [ ] **Kevin + Pedro:** Document how to set up LSPs in Claude Code.
- [ ] **Pedro:** Schedule presentations for Marvin and Edson over the next two weeks.
- [ ] **Pedro:** Share saved prompt and/or convert it into a reusable Claude skill.
- [ ] **Donovan:** Send anonymous feedback link to AI channels.

## Quotes

> "The only question we will refuse to answer is how to make Claude do your taxes."
> — Pedro Guimaraes

> "Codex has a way to import your Claude stuff. So there you go — we're not really locked in."
> — Donovan Hiland

> "Be as lazy as possible. Paste it into Claude and say 'can you make this a skill for me?'"
> — Donovan Hiland

> "Treat AI review suggestions as starting points. There's a tendency to find improvements forever — a human has to break the loop."
> — Pedro Guimaraes (paraphrased from discussion with Juan)
