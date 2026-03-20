# AI Development Office Hours - Episode 004

## Meeting Metadata

- **Series:** AI Development Office Hours
- **Episode:** 004
- **Cadence:** Bi-weekly
- **Participants:** Pedro Guimaraes, Donovan Hiland, Dany Beltran, Afonso Ferrer, Alejandro Rodriguez, Rodrigo Pineda, Edson, Juan Escobar

## TL;DR

Alejandro Rodriguez and Rodrigo Pineda from Ravn Labs present the custom tools they built during the Mint project. Alejandro demos **BridgeOS**, which connects Design OS outputs to Agent OS workflows so design tokens, plans, and standards flow seamlessly into spec-driven development. Rodrigo demos **Forge**, an MCP-based tool that lets an AI agent spawn, monitor, and communicate with multiple parallel AI terminal sessions -- eliminating the manual work of managing worktrees and context across repos.

The session showcases a shift from using AI tools as-is to building custom tooling that solves real workflow friction -- a key theme Donovan highlights as a takeaway for everyone.

## Key Topics

- **BridgeOS** -- Connecting Design OS to Agent OS for a unified design-to-code workflow
- **Forge** -- AI-supervised parallel terminal management via MCP
- **Parallel development workflow** -- Using worktrees and multiple Claude sessions for feature parallelism
- **Recommended tools** -- RTK AI, Agency Agents, Promptfoo, Open Viking
- **Build your own tools** -- The barrier to solving workflow friction is lower than you think

### BridgeOS

Alejandro built BridgeOS to solve a disconnect: Design OS produces a design system (colors, typography, tokens, architecture) and Agent OS drives spec-driven development, but they live in separate folders with no shared source of truth. BridgeOS bridges them.

**Commands:**

- `bridge init` -- Installs dependencies for both Agent OS and Design OS
- `bridge design` -- Runs an interactive workflow to define the design system (colors, typography, architecture)
- `bridge sync` -- Syncs the Design OS plan into Agent OS folders so specs can reference the design source of truth
- `bridge build` -- Creates spec-driven features following the synced design plan
- `bridge evolve` -- Redesigns or adds new features without re-explaining the existing design context

**Problems it solves:**

- Design tokens not connected to development standards
- No single source of truth for design across the project
- Having to re-explain the design system every time you create a new spec
- Manual integration between Design OS and Agent OS outputs

### Forge

Rodrigo built Forge after realizing his manual parallel workflow -- spinning up worktrees, copy-pasting prompts across terminal tabs, babysitting each session -- could be automated. Forge is an MCP tool that lets any AI agent (Claude Code, Gemini, Codex) spawn, monitor, and communicate with other AI terminal sessions.

**Key features:**

- Persistent terminals that can be stopped, continued, and monitored
- MCP integration so AI agents can launch and manage terminals programmatically
- Web dashboard for visual monitoring of all active sessions
- Cross-CLI support -- Claude Code, Gemini, and Codex terminals can coexist and communicate
- Broadcasting messages to all terminals at once (e.g., "report your progress")

**Rodrigo's parallel workflow:**

1. Start a Claude session, ask it which features can be worked in parallel (checks roadmap, dependencies)
2. For each feature, create a worktree with an isolated branch
3. Launch separate Claude Code sessions in each worktree via Forge
4. Monitor progress through the dashboard or by asking the main session to broadcast status checks
5. When backend completes, ask that session to generate a summary prompt for a frontend session in the other repo

### Parallel Development Workflow

Rodrigo's workflow demonstrates feature-level parallelism using worktrees:

- Ask Claude to identify features with no dependencies that can be worked simultaneously
- Each feature gets its own worktree and branch to prevent file conflicts
- Separate Claude sessions per worktree give more control than spawning parallel agents within one session (especially for spec-driven development where architectural questions need answers)
- Backend-to-frontend handoff is smoother when the completing backend session generates a context summary for the frontend session

### Recommended Tools

- **RTK AI** -- Token compression proxy for AI agents; summarizes verbose command output (e.g., git diff) so the agent receives only the useful information, saving tokens
- **Agency Agents** -- Framework for spawning multiple AI agents with roles that can collaborate and delegate to each other
- **Promptfoo** -- Testing framework for AI prompts; includes red teaming, pen testing, and vulnerability assessment for LLM apps
- **Open Viking** -- Open source database for persisting AI agent context

### Build Your Own Tools

Donovan's key takeaway: Alejandro and Rodrigo didn't just use existing tools -- they identified friction in their workflows and built solutions. The barrier to trying things out is low right now. If your AI workflow has pain points, you can use AI itself to build tools that fix them.

## Action Items

- **Everyone:** Try git worktrees for parallel feature development
- **Everyone:** Check out the BridgeOS and Forge repos (shared by Alejandro and Rodrigo)
- **Everyone:** If you notice friction in your AI workflow, consider building a tool or abstraction to solve it
- **Donovan:** Shared git worktree documentation in the chat
- **Alejandro & Rodrigo:** Share repos for BridgeOS and Forge

## Quotes

> "We were thrown into the ocean for AI and learned how to swim. Along the way, we built the tools we wished we had." -- Alejandro Rodriguez

> "The barrier to trying things out is pretty low. So if you're noticing that something's not great with your AI workflow, you can build systems yourself that help you fix it." -- Donovan Hiland

> "You can make your own life better with the tools that are making your life hard right now." -- Donovan Hiland

> "You might want to walk before you run. And worktrees are kind of like running, but it's still cool once you get there." -- Donovan Hiland
