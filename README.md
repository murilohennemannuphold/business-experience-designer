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

### 1. Intake — before it starts, it asks you three things
It won't jump straight into a review. First it asks:
- **Design stage** — are you in early exploration, mid-fi, hi-fi, or reviewing something already shipped?
- **Focus area** — what specific part worries you most?
- **Feedback type** — are you after strategic direction, flow logic, copy review, visual consistency, or business risk?

This calibrates the depth and angle. A first-draft wireframe gets directional signal. A pre-launch hi-fi gets precise, actionable findings.

### 2. Fit with the Uphold experience
A consistency table across five dimensions: visual consistency, interaction patterns, tone & language, mental model alignment, and trust signals. Each rated 🟢/🟡/🔴. Would a current Uphold user feel at home, or disoriented?

### 3. Step-by-step user experience breakdown
Every step of the flow reviewed from the user's perspective — what they expect, what they experience, where they might hesitate or bail, and what that costs the business if left unaddressed.

### 4. UX Risk Register
The 3–5 biggest risks, each tagged with Uphold's internal UX pain point taxonomy:

| Category | What it flags |
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

### 5. Business outcomes
Hypothesis-style predictions: if the experience works, what should improve? If the UX risk materializes, what could we lose? Grounded in fintech/crypto benchmarks when Uphold-specific data isn't available.

### 6. Missed opportunities
Realistic additions that could move the business needle without blowing up scope.

### 7. Recommendations
Prioritized list of changes — user benefit and business case for each.

### 8. Invitation to go deeper
After the first round, it offers to dig further into: drop-off analysis, competitive scan, copy deep-dive, edge cases and error states, or a specific user segment lens.

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
