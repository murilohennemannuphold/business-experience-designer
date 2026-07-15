# Business eXperience Designer — Claude Code Plugin

## TL;DR

This is a Claude Code plugin that gives you a senior **BX (Business Experience) designer** on demand. Point it at any design flow — screenshots, wireframes, or a step-by-step description — and it returns a structured review that connects UX observations directly to business outcomes. It's not a generic UX critique: it thinks in Uphold's context, speaks Uphold's UX language, and frames every finding in terms of what it does to your metrics.

**Install it. Run it before shipping. Catch what you'd otherwise miss.**

---

## What it does

The `design-review-bx` skill acts as a reviewer who sits at the intersection of user experience and business strategy. It understands that a confusing confirmation screen isn't just a UX problem — it's a drop-off problem. That a tedious flow isn't just friction — it's a retention risk. It reviews designs the way a senior BX designer would in a real crit: direct, specific, and always tied to outcomes.

Every review it produces follows the same structure, so findings are consistent and comparable across flows, features, and designers.

---

## What a review covers

### 1. Standing routines — every session, every time
Before any review begins, the skill applies three non-negotiable routines:
- **Version check** — it tells you if a newer version of the skill exists in this repo, so you can update before continuing.
- **Ask, don't assume** — it asks clarifying questions whenever context, intent, or data is missing. No silent guessing.
- **Always link sources** — every piece of information it shares (benchmarks, Figma frames, dashboards, articles, docs) comes with an inline link. No bare claims.

### 2. Intake — before it starts, it asks you four things
It won't jump straight into a review. First it asks:
- **Product line** — is this Wallet (consumer), Enterprise (B2B / white-label), or something else?
- **Design stage** — are you in early exploration, mid-fi, hi-fi, or reviewing something already shipped?
- **Focus area** — what specific part worries you most?
- **Feedback type** — are you after strategic direction, flow logic, copy review, visual consistency, or business risk?

This calibrates the depth and angle. A first-draft wireframe gets directional signal. A pre-launch hi-fi gets precise, actionable findings.

### 3. Problem statement — drafted and aligned before the review
Once intake is done, the skill drafts a problem statement using the [NN/g framework](https://www.nngroup.com/articles/problem-statements/) — background, affected user group, why it matters to them, and the organizational impact. It presents it to you and asks for alignment before going any further. If the framing is wrong, you correct it; a review built on the wrong problem isn't useful to anyone. No solutioneering, one problem only, root cause not symptom.

### 4. Fit with the Uphold experience
A consistency table across five dimensions: visual consistency, interaction patterns, tone & language, mental model alignment, and trust signals. Each rated 🟢/🟡/🔴. Would a current Uphold user feel at home, or disoriented?

### 5. Step-by-step user experience breakdown
Every step of the flow reviewed from the user's perspective — what they expect, what they experience, where they might hesitate or bail, and what that costs the business if left unaddressed.

### 6. UX Risk Register
The 3–5 biggest risks, each tagged with Uphold's internal UX pain point taxonomy:

| UX Pain point | What it flags |
|----------|--------------|
| **Comprehension** | Confusing content, jargon, missing labels |
| **Desirability** | Users understand but aren't motivated to proceed |
| **Findability** | Users can't find what they need |
| **Flow** | Too many steps, non-intuitive journey |
| **Usability** | Unexpected actions, missing confirmations, misread elements |
| **Accessibility** | Barriers for users with specific needs |
| **Trust & Security** | Privacy concerns, unclear tone, lack of transparency |
| **Performance** | Delays, crashes, platform gaps |
| **Feedback** | Missing loading states, no success/error confirmation |

Risks are ranked by severity and include the likely user behavior and the business metric at stake. If one category dominates, the skill calls it out — that's a systemic signal, not just a list of issues.

### 7. Business outcomes
Hypothesis-style predictions: if the experience works, what should improve? If the UX risk materializes, what could we lose? Grounded in fintech/crypto benchmarks when Uphold-specific data isn't available — and every data point is cited inline so you can verify the source without hunting for it.

### 8. Missed opportunities
Realistic additions that could move the business needle without blowing up scope.

### 9. Recommendations
Prioritized list of changes — user benefit and business case for each.

### 10. Invitation to go deeper
After the first round, it offers to dig further into: drop-off analysis, competitive scan, copy deep-dive, edge cases and error states, or a specific user segment lens.

---

## Data citation rules

Every data point, statistic, or benchmark in a review is cited inline, immediately after the claim — never grouped at the bottom. The skill uses a consistent format for each source type (Figma, Looker, industry benchmark, user research, support data, estimation), so you can verify any finding without hunting for the source. If a number is an estimate without a primary source, it's tagged as such and flagged for validation — never presented as fact.

---

## Companion skill: Figma Agentic Handoff

Alongside the BX review, this plugin now ships the **`figma-agentic-handoff`** skill — a way to turn a design section into a clean, self-contained handoff that both people and agents can pick up without prior context.

Design work usually gets passed downstream as a scattered mix of Figma frames, Slack threads, and half-remembered decisions. The next person — or the next agent — has to reconstruct the intent before they can act. This skill fixes that. Point it at a Figma section you've shared and it produces a structured handoff block that captures **what the section is, how the flow is put together, and the live metrics it's meant to move** — grounded in the actual Figma file and the conversation around it, never invented.

Why it matters:
- **Empowers the handoff.** It packages design intent into one honest, self-contained block, so the moment you finish a flow it's ready to travel — to product, to engineering, or to another agent.
- **Cleaner reading for people and agents alike.** A consistent structure (brief → flow structure → Looker metrics), stamped with the date and owners, means whoever picks it up reads it the same way every time — no archaeology required.
- **Keeps the design process honest.** It grounds every statement in the file or the conversation, links its sources, and asks rather than guesses when something is unclear — the same standing routines as the BX review.

The output goes to the chat for review **and** into the Figma file as a new section, so the handoff lives right next to the work it describes.

Run it by saying:

> "Hand this off"

or

> "Create a resume of this flow for engineering"

or invoke `/figma-agentic-handoff` directly.

---

## How to install

```bash
/plugin marketplace add murilohennemannuphold/business-experience-designer
/plugin install design-review@business-experience-designer
```

## How to run it

In any Claude Code session, just describe your flow or share your screens and say:

> "Run the BX review on this"

or

> "Review this from a designer perspective"

---

## Who this is for

Any designer on the team working on a flow that touches users — onboarding, transacting, verifying, managing assets, anything. It's most useful before a flow goes to dev, but it's also valuable for retroactive reviews of shipped experiences where drop-off data is pointing at a UX problem.

---

*Built and maintained by Murilo Hennemann — Uphold Design.*
