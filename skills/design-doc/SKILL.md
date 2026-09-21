---
name: design-doc
description: Helps decide whether a software design document is warranted, then draft one or review an existing one against a standard framework (objective, background, goals/non-goals, scenarios, diagrams, SLOs, security/privacy, alternatives considered, etc). Use this whenever the user wants to write a design doc, RFC, tech spec, or proposal for a non-trivial software change, asks "should I write a design doc for this?", or shares a draft design doc / RFC and wants feedback on completeness or structure. Based on Michael Lynch's design doc guide.
---

# Writing an Effective Design Document

Source: Michael Lynch, "[How to Write an Effective Software Design Document](https://refactoringenglish.com/excerpts/write-an-effective-design-doc/)" (drawing on experience at Google, Microsoft, and his own companies).

## Step 1: Decide if a doc is even warranted

Don't draft one reflexively. A design doc pays for itself when the project has at least one of:

- Multiple people need to coordinate work
- More than ~3 months of full-time development
- It's a production system that will run for years
- It spans teams
- Goals or requirements are ambiguous
- Getting it wrong is catastrophic (security, legal, irreversible data loss)

None of these apply → skip the doc, just build it. Say so plainly if the user's project doesn't clear the bar.

## Step 2: Filter every section through "what's the penalty for being wrong?"

This is the single rule that keeps a design doc from bloating into a spec of everything. For each candidate section or decision, ask whether getting it wrong is expensive or permanent to reverse (language choice, database choice, wire format, data model) or cheap to change later (pagination styling, button copy). Include the former, skip the latter. When drafting, cut any section where you can't articulate a real cost of being wrong — that's the biggest lever for keeping the doc short and something people will actually read.

## Step 3: Structure

Not every doc needs every section — pick based on the Step 2 filter. Use this as the checklist / skeleton:

```markdown
# [Short, distinctive title]
Author: ... | Created: ... | Status: draft/approved | URL: ...

## Objective
One sentence, plain language, no jargon.

## Background
Context, motivation, prior attempts and why they fell short.

## Goals
High-level outcomes (impact, not implementation).

## Non-Goals
Explicitly out of scope — as important as the goals.

## Scenarios
Concrete, real-world usage examples. Ground the abstract design in how someone will actually hit this code path.

## Design / Diagrams
Include a diagram if there's any shape to explain. Reviewers don't have
the mental picture in their heads yet — a picture gets them there faster
than prose. Use an editable tool (Excalidraw, draw.io) so reviewers can
comment on or fork it.

## Glossary
Define terms a reviewer outside the immediate team won't know.

## Constraints
Budget, infra, timeline, org, or dependency constraints shaping the design.

## Service Level Objectives
Measurable performance/availability targets, if relevant.

## Monitoring & Alerting
How you'll know it's working / broken in production.

## Timeline
Milestones with concrete deliverables, not just dates.

## Interfaces
APIs, UI surfaces, file formats — the contract other people build against.

## Dependencies & Infrastructure
What this relies on, and what relies on this.

## Security
Threats, attack surface, trust boundaries.

## Privacy
Sensitive data handled, retention, who can access it.

## Legal
Anything with compliance or contractual implications.

## Logging
What gets logged, at what volume/retention, for debugging vs. audit.

## Open Issues
Problems that aren't resolved yet — surfacing these is more useful than hiding them.

## Resolved Issues
Decisions made and the reasoning, so future readers don't relitigate them.

## Alternatives Considered
Options that were rejected, and why. This is often the most valuable
section for a future reader trying to understand "why didn't we just do X."
```

Security, Privacy, and Legal only need real content when the project's risk profile calls for it (see Step 1's "catastrophic risk" trigger) — don't pad them with boilerplate for a low-stakes internal tool.

## Step 4: How much to invest

There's no universal rule for how long to spend on this. Match effort to project complexity, team size, and how expensive a wrong turn would be — a two-person one-month project warrants a lighter doc than a cross-team multi-quarter migration. If the user's project is small, say so and suggest trimming the template rather than filling in every section for completeness's sake.

## Reviewing an existing doc

When asked to review a draft design doc, don't just check section presence. For each section, ask:

1. Does it pass the Step 2 filter, or is it padding?
2. Is Alternatives Considered actually present with real rejected options, not just the chosen path restated?
3. Are Goals stated as outcomes rather than a list of implementation tasks?
4. Is there a diagram if the design has any topology to it (components, data flow, sequencing)?
5. Are Non-Goals explicit, not just implied?

Report findings as a short list of what's missing or weak, not a rewrite — the author owns the content.
