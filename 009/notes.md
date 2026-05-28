# AI Development Office Hours — 2026-05-22

- **Date:** 2026-05-22
- **Duration:** 36:04
- **Grain:** https://grain.com/share/recording/3a4548a7-7904-4baf-9f1c-a4a7e21e5b0b/wKB3MW4Ldi4hbmRjcgq7R4spkSVC71VuD7SbRsA0
- **Format:** Open Q&A + announcements
- **Missing artifacts:** `recording.mp4`

## TL;DR

Stickers for the ~50 people who completed all four foundational courses by April 30 are inbound. Form feedback on office hours is positive; Pedro wants ideas for 30-minute practical sessions and Afonso suggested TDD-with-AI. Claude Architect certificate is open to everyone (no more pilot group), Ravn reimburses via Clockify. Kevin demoed an HTML-output skill for interview prep, prompting a broader discussion of HTML vs. Markdown for AI-generated artifacts (HTML wins on shareability and interactivity, despite the token cost).

## Key Topics

### Announcements (Pedro)
- **Revencito stickers** going to ~50 people who completed all four courses before April 30. Stickers are in El Salvador. List shared later today.
- **Office hours feedback form** — useful suggestions came in. Anyone who hasn't filled it: link reshared in chat.
- **Practical sessions** — Pedro looking for 30-minute ideas. Afonso volunteered TDD-with-AI as a topic, since writing tests-first is hard when you're prompting instead of typing the implementation yourself. Pedro will plan one.

### Claude Architect certificate (Carlos / Afonso)
- Pilot group is **closed**; the certificate is now open to **everyone**. Brandon announced this in Slack the day before.
- Ravn reimburses the cost via **Clockify → reimbursement spot**.
- Goal: everyone gets it by year-end.
- Prerequisite courses: AI Fluence, Cloud 101, Cloud Coding Action, Intro through MCPs.
- Certificate valid 6 months. Fail the exam → 6-month cooldown before retake. Practice exam available; passing the practice ≈ passing the real thing.
- 4 people certified so far in pilot: Marcelo Melgar, Carlos E. Pérez, Jose Gomes, Mario.
- **Carlos's advice:** focus on **strong fundamentals**. Many exam options look right; only solid fundamentals let you discriminate. Ask Claude to explain things by analogy.
- Less complex than AWS Solutions Architect — days to a week of study in the cracks is usually enough.

### HTML vs. Markdown for AI-generated artifacts (Hunter / Pedro / Kevin)
- Pedro just used HTML for the sticker-eligibility list (table generated from a spreadsheet) and finds it **more presentable and easier to share** than Markdown — at the cost of more tokens.
- Markdown forces recipients to either open VS Code or read raw — awkward.
- **Kevin's interview prep skill:** Claude generates an interactive HTML page with the question list, a notes box below each question, scoring sections, and an "export to Markdown" button at the bottom. The HTML is a mini-app — no separate Node project needed.
- HTML's win: **interactivity**. Search/filter, buttons, exports — Claude writes these fast and well.
- Donovan: Markdown can't be interactive; HTML can. Worth the token tradeoff for shareable artifacts.

### Built-in review skill vs. custom review sub-agent (Hunter / Juan)
- Built-in Claude Code review skill exists (Juan confirmed).
- Juan compared both for a week: ran his custom reviewer sub-agent, then the built-in review skill, then asked Claude to compare. The **built-in skill produced noticeably fewer false positives**.
- Juan has stopped using his custom reviewer.
- Universal caveat: AI review tools will find "improvements" forever. Don't accept the first pass; iterate with human judgment, and stop when changes stop being substantive.

### Non-tech use of AI at Ravn (Hunter)
- **Garland (CSM team)** uses Claude for: customer analysis, meeting prep, tracking client relationships, surfacing recurring internal-dev topics worth raising with the customer.
- Pattern: dev channels mention a problem repeatedly → Garland surfaces it in customer conversations to either solve internally or escalate.

### GPT 5.5 vs. Opus 4.7
- Both excellent. Choice is "vibes-based."
- **Recommendation:** if you have a personal ChatGPT subscription, install Codex and use it as a second-opinion reviewer alongside your Claude session.

### Future session ideas (Donovan / Pedro)
- A practical session: build something complicated in ~20 minutes, leaving 10 minutes for troubleshooting and discussion.
- Donovan: AI YouTubers are abandoning the "5-minute demo" format and showing full workflows in longer videos. Maybe office hours should too.
- Risk: Claude's processing time is unpredictable; awkward silences during live demos.

## Action Items

- [ ] **Pedro:** Share list of people receiving Revencito stickers later today.
- [ ] **Pedro:** Share the office-hours feedback form again in chat.
- [ ] **Pedro:** Post learnings to the #ai-office-hours Slack channel.
- [ ] **Pedro:** Plan and schedule a TDD-with-AI practical session (propose a date).
- [ ] **Pedro:** Add Mario to the Cloud Architect group when he reaches out.
- [ ] **Carlos E. Pérez:** Submit certificate reimbursement via Clockify reimbursement spot.
- [ ] **Kevin Del Castillo:** Share the HTML-based interview/assessment workflow and examples.

## Quotes

> "HTML is a lot easier to share than Markdown. It uses more tokens, but it's more presentable and you can make it interactive."
> — Pedro Guimaraes

> "The secret is to get the fundamentals strong. You'll see many answers that look correct — only fundamentals let you tell them apart."
> — Carlos E. Pérez (on the Claude Architect exam)

> "The more you guys actually interact and engage here, the more effective these will be. Right now it's mostly Pedro talking — that can be better."
> — Donovan Hiland (closing remarks)
