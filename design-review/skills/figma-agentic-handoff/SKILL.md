---
name: figma-agentic-handoff
version: 1.0.0
description: Produce a written, agent-ready design handoff for a Figma section a designer has shared, drawing on both the Figma file and the current conversation. Reads the selected section, establishes the job-to-be-done (asking the designer when it isn't clear), and writes a structured block — brief, flow structure, and a live Looker metrics table — stamped with the date and the people who called it for ownership. Output goes to the chat AND into a new Figma section. Use when a designer says "hand this off", "summarise this section for engineering/product", "create a resume of this flow", "prep this for an agent", or invokes /figma-agentic-handoff.
argument-hint: "[optional: the section/JTBD, or a Figma node URL]"
---

Produce a design handoff block for the Figma section the designer has shared. The reader is **another agent** (product or engineering) who will pick up this design with no prior context — so the block must be self-contained, factual, and honest about what is unknown.

$ARGUMENTS

This skill is empirical and consent-driven: **do not invent, do not fill blanks, and do not publish anything the designer hasn't approved.** When you can't ground a statement in the Figma file or the current conversation, stop and ask.

## Standing routines — every session, every time

Apply these three non-negotiable routines before any handoff work begins, on every invocation:

1. **Version check** — this skill is `version: 1.0.0`. Check whether a newer version exists in the source repo (`uphold/ai-toolkit`, e.g. `gh api repos/uphold/ai-toolkit/contents/plugins/uphold-figma-agentic-handoff/skills/figma-agentic-handoff/SKILL.md` and compare the `version:` field). If a newer version exists, tell the designer and offer to update before continuing. If the repo isn't reachable, say so and proceed.
2. **Ask, don't assume** — whenever context, intent, or data is missing, ask a clarifying question. No silent guessing, ever.
3. **Always link sources** — every piece of information shared (Looker dashboards, Figma frames, benchmarks, articles, docs) carries an inline link or a concrete reference (frame/node name, Look/Explore URL). No bare claims.

## Prerequisites (check first, ask if missing)

- The **Figma MCP** must be connected to the designer's file with the target section selected (or a node URL supplied in `$ARGUMENTS`). If no selection/URL is resolvable, ask the designer to select the section or paste its link before continuing.
- Writing into Figma uses `use_figma` — you **must** invoke the `figma-use` skill before that call (see Step 6).
- The **Looker MCP** (Uphold) is needed for Step 5. It's provided by the `claude_ai_Looker` connector — surface its tools with `ToolSearch` (query `looker`). Key tools: `mcp__claude_ai_Looker__get_models`, `__get_explores`, `__get_dimensions`, `__get_measures`, `__query`, `__run_look`, `__run_dashboard`. Auth is handled by the connector (no manual credentials); if the designer isn't authenticated, the tool will prompt them — surface that rather than guessing. If it can't be reached, degrade gracefully per Step 5.

## Step 1 — Gather grounding (do not write anything yet)

1. Read the shared section from Figma: use `get_metadata` and `get_screenshot` for layout, and `get_design_context` for structure/components. Note the section name and node id.
2. Re-read the **entire current conversation** — the designer invoked this skill mid-discussion, and that discussion is primary context for intent.
3. Identify the owner: call the Figma MCP `whoami` for the current user. Then **ask** the designer to name any collaborators/co-owners. Stamp the date automatically (today).

## Step 2 — Establish the job-to-be-done (consent gate)

Draft, in your head only, what the section is and what it aims to achieve, from the file + conversation.

- If the JTBD is **clear and grounded**, state your one-paragraph read of it back to the designer and ask them to confirm or correct it. Do not proceed to write the briefing until they confirm.
- If the JTBD is **not derivable** from the file + conversation, **stop and ask** the designer for the job-to-be-done and as much context as possible. Never guess it.

> Hard rule: no briefing text is composed or published without the designer's explicit consent on the JTBD.

## Step 3 — Compose the handoff block

Follow `references/handoff-template.md` exactly for structure and headers. Fill these three sections:

1. **Brief** — what the section is and what you (as designers) aimed to achieve. Grounded in the confirmed JTBD. Plain language, no filler.
2. **Flow structure** — what the reader will see and where things are located in the file: screens/frames, order, key components, states, and how they connect. Reference frame/node names so an agent can find them.
3. **Looker metrics** — see Step 5.

## Step 4 — Ownership header

Every block opens with: section name, **date**, and **owners** (Figma current user + any collaborators the designer named). This establishes and proposes ownership of the output.

## Step 5 — Looker metrics table (live)

Uses the `claude_ai_Looker` connector. Surface its tools with `ToolSearch` (query `looker`) before calling them.

1. Propose the **5 most relevant data points** this design should move, given the JTBD, and confirm the shortlist with the designer.
2. Ground each metric in a real Looker field, don't invent field names:
   - `mcp__claude_ai_Looker__get_models` → pick the relevant model (ask the designer if ambiguous).
   - `mcp__claude_ai_Looker__get_explores` → find the explore; `__get_dimensions` / `__get_measures` → confirm the exact field for each metric.
3. Pull the current live value for **Before**: use `mcp__claude_ai_Looker__query` (model + explore + fields + filters) for ad-hoc figures, or `mcp__claude_ai_Looker__run_look` / `__run_dashboard` when an existing Look/dashboard already reports it. Cite the source (Look/Explore name or URL via `__query_url`).
4. Set **After** as the target/hypothesis and confirm it with the designer — do not fabricate targets.
5. Render as a 3-column table (short headers, full explanation in the content):

   | Before | After | Design impact & tracking |
   |--------|-------|--------------------------|

   The third column explains *how our design affects this number and how we should track it* — name the exact model/explore/field and the cadence, with a `query_url` link where possible (standing routine: always link sources).
6. If Looker can't be reached or the designer isn't authenticated: surface that, still list the 5 proposed metrics with the exact field each needs, and leave **Before** as `— (Looker unavailable)` so it can be filled later. Don't silently skip it, and don't guess the numbers.

## Step 6 — Publish (both destinations)

1. Present the full block as text **in the chat** for the designer to review.
2. After they approve, write it into the Figma file as a **new section**: invoke the `figma-use` skill, then use `use_figma` to create a new section/frame near the shared one containing the block as text. Confirm placement with the designer if ambiguous.

## Guardrails — apply throughout, they override convenience

- **Consent before briefing.** Never compose or publish the brief without the designer confirming the JTBD (Step 2).
- **Never assume, never fill blanks.** Anything not grounded in the file or the conversation is a question for the designer, not a guess.
- **Ask before publishing to Figma.** No `use_figma` write without approval of the text (Step 6).
- **Live data only.** Before-numbers come from Looker, not memory. No invented targets — confirm After with the designer.
- **Write for an agent with zero context.** Reference concrete frame/node names; state unknowns explicitly rather than papering over them.
- **Link every source.** Per the standing routines, no bare claims — Looker figures cite their Look/Explore, design references cite frame/node names, external facts carry inline links.
