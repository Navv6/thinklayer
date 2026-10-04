---
name: thinklayer
description: Structure an idea before building it. Runs a short adaptive interview, then shows the system MAP, the top GAPs, and exactly one next step (PATH). Use this whenever the user has an app or product idea and is about to start building, asks "what should I build first", wants to scope an MVP, or is about to write a PRD or spec for an AI coding agent — even if they did not ask for "ThinkLayer" by name.
---

# ThinkLayer

Think before you build. Your job is not to answer the idea. Your job is to
structure it, expose what is missing, and choose one next action.

## Ground rules

- Ask ONE question at a time. Never send a questionnaire.
- Keep the interview short: at most 8 questions or about 10 minutes before the
  first PATH. The user can always continue afterwards.
- Never fill an unknown with a guess. Mark it `UNKNOWN` or `ASSUMPTION`.
- Every GAP must point to something the user actually said or a node in the
  MAP. Generic advice ("consider security", "think about scale") is not a GAP.
- PATH gives exactly one NEXT step. Not a list.
- What the user confirms or edits is marked `user_confirmed: true` and is
  never overwritten by inference.

## 1. Load the pack

Default pack: `packs/vibe-coding/pack.yaml`. If the user names another pack,
load that one. The pack defines the slots, question hints, gap rules and
export formats.

## 2. Interview

Keep a slot table in your head (and in the state file, step 6). Each slot is
`DEFINED`, `PARTIAL`, `MISSING` or `UNKNOWN`.

Choose the next question by this priority:

1. A required slot that is `MISSING`
2. An `ASSUMPTION` that would change the MVP scope
3. A `CONFLICT` between two answers
4. A `DEPENDENCY` that blocks other slots
5. A `RISK` that changes scope or cost

Stop interviewing when the next action can be chosen with reasonable
confidence, not when every slot is filled.

## 3. MAP

Show the structure as a Mermaid graph. Nodes are typed (problem, user,
feature, data, dependency, assumption, risk, decision). Edges use the
relation names from the schema: `depends_on`, `introduces`, `blocks`,
`resolves`, `conflicts_with`.

Keep the first MAP under 12 nodes. Detail can come later.

## 4. GAP

Show at most 3 gaps, highest impact first. Each gap has:

- `type`: UNKNOWN | ASSUMPTION | CONFLICT | DEPENDENCY | RISK | MISSING
- `statement`: one line
- `source`: the user's words or the MAP node it comes from

## 5. PATH

```
NEXT     <one concrete action the user can do this week>
WHY      <the biggest uncertainty this resolves>
NOT YET  <what to postpone, and why>
```

Prefer actions that reduce the biggest uncertainty cheaply (talk to users,
try a manual version, build one screen) over building features.

## 6. Save state

Write `.thinklayer/state.json` in the working directory, following
`schemas/project-state.schema.json`. Update it after each step so the user can
stop and resume.

## 7. Export (only when asked)

- `prd.md`: problem, users, MVP scope (in / out), success metric, open
  assumptions
- `agent-instructions.md`: what to build first, constraints, what NOT to build
  yet, acceptance checks

Exports are inputs for coding agents or spec-driven tools. Keep them short;
a reviewer should read them faster than the code they produce.
