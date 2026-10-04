# ThinkLayer

**Think before you build.** The thinking layer before AI builds.

> Map your thinking. Find the gaps. Follow the path.

[한국어](README.md)

![ThinkLayer concept demo](docs/demo.gif)

*Concept demo. v0.1 is in progress; output is illustrative.*

---

## Why

AI coding agents made building fast. Deciding *what* to build did not get
faster. Ideas go straight to code, features pile up, and the rework starts.

Spec-driven tools help once you know what you are building. ThinkLayer sits
one step earlier: **should this be built, and what is the smallest version
worth building?**

```
Idea → ThinkLayer (MAP · GAP · PATH) → PRD / spec → your coding agent or spec tool
```

## How it works

| Step | What you get |
| --- | --- |
| **Interview** | One question at a time, chosen by what is missing. Short by design. |
| **MAP** | Your idea as a graph: features, data, dependencies, assumptions, risks. |
| **GAP** | At most 3 gaps, each tied to something you said. No generic advice. |
| **PATH** | Exactly one next step, why it matters, and what to postpone. |

Then, only if you ask: `prd.md` and `agent-instructions.md`.

## Principles

- **Structure before output.** No answers before the problem is clear.
- **Unknown is explicit.** Nothing is guessed. Unknowns and assumptions are labelled.
- **One next step.** Not a list of twenty recommendations.
- **Human editable.** What you confirm is never overwritten by the model.
- **Use the AI you already have.** No model is bundled. See [Credentials](#credentials).

## Quick start (v0.1)

ThinkLayer v0.1 is an **agent skill**: a set of instructions your coding
agent runs inside its own session.

1. Clone this repo.
2. Copy `skills/thinklayer/` into your agent's skills folder
   (see your tool's documentation for the location), or paste
   `skills/thinklayer/SKILL.md` as instructions if your tool has no skill support.
3. Start a session and say: *"I want to build ..."*.

State is saved to `.thinklayer/state.json` in your project so you can stop and
resume.

## Repository layout

```
skills/thinklayer/       the core skill (interview → MAP → GAP → PATH)
packs/vibe-coding/       slots, question hints, gap rules, exports
schemas/                 Project State JSON Schema
examples/workout-tracker sample state, map and PRD
docs/                    demo and design notes
```

## Packs

The core flow stays the same; a **pack** defines the slots, questions and
outputs for a purpose. v0.1 ships the Vibe Coding Pack. Planned: Idea,
Startup, Project, Decision. Community packs are the long-term goal.

## Credentials

ThinkLayer never asks for, reads, stores or forwards your AI account
credentials or session tokens. It runs inside tools you have signed into
yourself, or uses an API key or local model you configure. Each provider's
terms decide how your subscription may be used; check them before connecting
anything.

## Status and roadmap

| Phase | Goal |
| --- | --- |
| 0. Concept | Schema and Vibe Coding Pack documented ← **now** |
| 1. Prototype | One idea processed end to end |
| 2. MVP | Local state, exports, 10–20 user tests |
| 3. Validation | Measure gap usefulness and scope change |
| 4. Release | Pack authoring guide, external packs |

## Contributing

Early stage. Issues with real ideas you tried, gaps that were useless, or
next steps that were wrong are the most valuable contribution right now.

## License

To be decided before the first release (MIT or Apache-2.0).
