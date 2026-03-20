# AI Development Office Hours - Episode 003

## Meeting Metadata

- **Series:** AI Development Office Hours
- **Episode:** 003
- **Cadence:** Bi-weekly
- **Participants:** Afonso Ferrer, Pedro Guimaraes, Carlos Eduardo Perez, Donovan Hiland, noelara, Marjorie, Ronald Rios, Ale Vidales, Jose Gomes-RAVN, Richie-RAVN, Juan Escobar

## TL;DR

Pedro broadens the audience beyond engineers, presenting AI fluency as a skill everyone at Ravn should develop -- regardless of role. He introduces the **4D framework** (Delegation, Description, Discernment, Diligence) as a practical model for working with AI effectively and responsibly. The session covers prompt specificity, the critical importance of verifying AI output, and includes role-specific examples for engineers, PMs, designers, and QA.

Pedro also debuts the **Meeting Intelligence** plugin -- the first Cowork plugin deployed org-wide by the AI platform team -- which generates structured meeting notes from any transcript.

## Key Topics

- **AI fluency for everyone** -- What it means to communicate with AI effectively, ethically, and safely
- **How LLMs actually work** -- Pattern matching and role-playing, not real intelligence
- **Three modes of AI work** -- Automation, augmentation, and agents
- **The 4D framework** -- Delegation, Description, Discernment, Diligence
- **Prompt specificity** -- From vague to precise, with examples
- **Discernment is paramount** -- AI generates confident nonsense; you must catch it
- **Role-specific applications** -- Engineers, PMs, designers, QA, and client-facing roles
- **Meeting Intelligence plugin** -- First org-wide Cowork plugin from the AI platform team

### AI Fluency for Everyone

AI fluency is the ability to talk to AI agents in an effective, efficient, ethical, and safe way. Regardless of whether output was AI-generated, the person delivering it is responsible for its quality. This applies to every role, not just engineers.

### How LLMs Actually Work

For non-technical attendees, Pedro demystifies LLMs: they are pattern recognition machines that are very good at pretending to be experts. They are not intelligent -- they role-play expertise convincingly. This means they can be powerful collaborators and thinking partners, but they cannot replace human judgment.

### Three Modes of AI Work

- **Automation** -- Specific tasks or workflows you want done automatically every time
- **Augmentation** -- AI-assisted work (what engineers do with Claude Code); also useful for research and brainstorming
- **Agents** -- Long-lived automations that take decisions, monitor things, and report back

### The 4D Framework

From Anthropic, adapted for Ravn:

- **Delegation** -- Decide what you do yourself vs. what you delegate to AI. Good to delegate: first drafts, brainstorming, research. Keep human: final decisions, sign-offs, human conversations, novel work, confidential data.
- **Description** -- Clear communication. Set your role, goals, requirements, constraints, and tone. Provide examples of good output. Assign roles, but keep them generic (don't fabricate impossible personas).
- **Discernment** -- The most important D. Use your expertise to evaluate output. AI generates wrong answers with extreme confidence. Always ask: Is this bullshit? Is this accurate, complete, and appropriate?
- **Diligence** -- Be responsible. Disclose AI usage when needed. Review output before delivering to clients or stakeholders. Never share confidential information. Follow organizational policies.

### Prompt Specificity

Pedro walks through progressive examples:

- **Vague:** "Write an email to the client with a status update"
- **Better:** Explain the two-week delay, mention the causes
- **Best:** Specify the audience (VP of Product), the tone (confident, reassuring), the length (concise), and what to cover (delay, causes, mitigation plan)

Same applies to engineering -- "review this pull request" vs. asking for security audit, reusability analysis, edge case detection, and readability assessment.

### Discernment Is Paramount

Pedro demonstrates with a deliberately absurd HR question about "per-token semantic load of interviews" -- ChatGPT confidently generates a framework with formulas for a concept that doesn't exist. The lesson: AI will give you wrong answers with extreme confidence. Always evaluate output through your domain expertise.

### Role-Specific Applications

- **Engineers:** Be extremely rigorous with linters, automated tests, and TDD. These safeguards compound over time.
- **Product Managers:** Use AI to brainstorm features and surface blind spots in specs.
- **Designers:** Close the gap between design knowledge and engineering edge cases. AI can surface failure modes the designer may not have considered.
- **QA:** Generate test matrices -- happy paths, edge cases, platform-specific differences (iOS vs. Android).
- **Client-facing roles:** Translate technical content into business impact. No jargon -- focus on cost, timeline, and product outcomes.

### Meeting Intelligence Plugin

The first Cowork plugin from the AI platform team, deployed org-wide. It generates structured meeting notes from any transcript source (Grain, Granola, etc.) with templates for standups, all-hands, client conversations, one-on-ones, and more. Available to everyone via the Claude desktop app or Claude AI web interface -- log in with your Ravn account and access it through the Cowork tab.

## Action Items

- **Everyone:** Download the Claude desktop app and try the Meeting Intelligence plugin with your next meeting transcript
- **Everyone:** Practice the 4D framework -- start with Description (write more specific prompts) and Discernment (critically evaluate output)
- **Everyone:** If you have ideas for useful org-wide plugins or tools, reach out to Pedro or Donovan
- **Pedro:** Post instructions for using the Meeting Intelligence plugin in the AI channel
- **Donovan & Pedro:** Post meeting recording, notes, and slides
- **AI platform team:** Continue developing Cowork plugins for both engineers and non-engineers

## Quotes

> "No matter if it was generated by AI or not, you are the one delivering it. Your name is in it. So you gotta be responsible for what you deliver." -- Pedro Guimaraes

> "They are very good at pretending to be an expert on something. They are not an expert on something. They're not a real intelligence thing. They are just a pattern matching machine." -- Pedro Guimaraes

> "I hate TDD as a human but I'll gladly make Claude do TDD every single time." -- Pedro Guimaraes

> "It is basically a bullshit generator. So sometimes... always look at the outputs with the lens of: is this bullshit? Is this machine lying to me?" -- Pedro Guimaraes
