# AI Development Office Hours — 2026-05-01

- **Date:** 2026-05-01
- **Duration:** 38:25
- **Grain:** https://grain.com/share/recording/68b85375-69eb-496c-aaa3-4c7aa5d7c962/OlhP6lGqPs3JJ21fw9A5rSwueXBTetIMOQ0zPuuW
- **Format:** Open Q&A (no presentation)
- **Missing artifacts:** `recording.mp4`

## TL;DR

Q&A on model choice (Codex vs. Claude), foundational courses, discovery channels for skills/agents, why parallelization is usually a trap, and how Ravn plans to absorb AI costs (~$1,200/person/year × 230 people) by passing them through to clients. Self-hosting open-source models was estimated at ~$50k/month and ruled out for now.

## Key Topics

### Codex vs. Claude (Hua)
- Codex (GPT-5.x) is genuinely good for coding — sometimes better than Claude for debugging stuck problems and clearly better for UI screenshot reading (though Anthropic claims Opus 4.7 closed that gap).
- Caveat on the comparison: when Pedro tries Codex *after* Claude has already churned on a problem, Codex inherits more context about the bug.
- The $20 ChatGPT plan feels more like a tech demo than a daily driver subscription.

### Foundational courses (recommendation)
- **AI Fluence**
- **Agent Skills**
- **Claude API course** — the most in-depth; covers MCP, API, how LLMs work. Can replace the standalone Claude Code / MCP courses.
- Skip the standalone MCP and Claude Code courses if you've done the API one — too much overlap.
- Claude Co-work is worth knowing for scheduled tasks (better UI than CLI scheduling).

### "Why does Claude find different issues in different sessions?" (Francisco)
- Different session = fresh context window = "fresh pair of eyes." Same model, no memory of prior session.
- Same effect when you spin up a sub-agent or switch tools (Codex/Gemini) for review.
- **Don't switch models mid-session.** Invalidates the cache; you re-pay for the full conversation as fresh output tokens. Spawn a sub-agent instead.

### AI cost handling at Ravn (Hua, answered by Donovan)
- Current spend: ~$1,200 per person per year × 230 people. One of the company's biggest line items.
- Plan: treat AI cost like infra, GitHub, Jira — pass it to clients. Could be a rate increase, could be a line item; Brandon, Rick, and the partners are working on the contract details.
- Costs probably stable through this year: Google just put $40B into Anthropic, Amazon another $10-20B. A 10× hike next month would be catastrophic for everyone, not just Ravn.
- Chinese labs (DeepSeq especially) pushing prices down on the open-source side.

### Discovery channels for skills/agents (Matheus)
- **skillsmp** (Pedro showed it)
- **skills.sh** (more common, Matheus uses)
- **agents.* / agents.md** sites
- **GitHub direct search** — harder to filter, but you find interesting agents that aren't on the indexes.

### Compatibility across tools (Samuel)
- Skills, sub-agents, MCPs are standard — work across Claude Code, Cursor, Codex, Gemini.
- Hooks: Claude Code, Codex, Gemini all have them; Cursor confirmed yes during the meeting.

### Self-hosting open-source LLMs (Yurio)
- Donovan did the math after some open-source model beat Opus on a benchmark. A Mac Studio could *technically* run it, but the resource requirements to keep it from being painfully slow push the bill to roughly **$50k/month** to serve the whole company.
- Best current local option discussed: Qwen 3.6 (and similar), still needs a 3090-class GPU (24GB VRAM) plus a lot of system RAM. Single-user fine; 200-user scale untenable.
- Claude is currently both cheaper and better.

### Agent orchestration / parallelizing work (Isaque/Zach)
- Both Pedro and Donovan default to **sequential** work, optimized for speed.
- Parallelizing across *different projects* is more manageable than parallelizing within one project.
- The win is "while Claude is running, do something that doesn't require a context switch" — not "spin up 5 worktrees."

### Git tooling
- Pedro is a creature of habit — terminal Claude Code most of the time.
- For worktree workflows: **Conductor** (supports Codex/Claude/Gemini), **T3** (Codex/Claude), **superset.sh** (experimenting).

## Action Items

- [ ] Define how AI costs are included in client contracts (Brandon/Rick/partners).
- [ ] **Donovan:** Post the link for submitting questions for next week's session.
- [ ] **All:** Prepare and submit questions for next week's AI session.

## Quotes

> "Don't switch models mid-session. You invalidate the cache and pay the higher tax of fresh output tokens. Spawn a sub-agent instead."
> — Pedro Guimaraes

> "It might be a little slower at first. Start using it, see where it falls down. Find the problem, then find the tool — not the other way around."
> — Donovan Hiland

> "If prices went 10× next month it would be catastrophically bad for everyone. There's still venture capital money being burned — Google just put $40 billion into Anthropic."
> — Pedro Guimaraes
