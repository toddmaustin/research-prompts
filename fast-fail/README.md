# fail-fast (README)

This prompt is a **fail-fast ideation workflow** for research and engineering: generate **novel** candidate ideas, then aggressively design the **cheapest decisive tests** that let you know (with high confidence) whether an idea will (or will not) deliver its hypothesized value.

It is designed for “Stage 1” of the research workflow (idea generation + early shaping), but it explicitly treats **novelty as a first-class requirement**: an idea is not just “likely to work,” it must also be meaningfully new relative to plausible baselines and prior work.

This workflow performs best when the model’s **thinking mode** is enabled (for example, **Extended Thinking** in ChatGPT or **Pro/Thinking** mode in Gemini), especially for enumerating failure modes and designing minimal tests.

---

## What problem it solves

Early-stage ideation often fails in predictable ways:

- The idea is novel but **not falsifiable** (no crisp test).
- The idea is plausible but **not novel enough** to matter at the target venue.
- It has hidden assumptions that are **untrue in the target setting**.
- The “killer experiment” is expensive, so you postpone it and drift.
- The value proposition is correct, but the **validation path** is unclear.

This prompt forces each idea into an **Idea Card** with:
- a crisp hypothesis,
- an explicit novelty claim (relative to baselines),
- a measurable success criterion,
- a cheapest decisive test,
- explicit stop/pivot rules.

---

## Fail-fast patterns (common in computer engineering)

The prompt explicitly encourages standard “fail fast” moves used in computer engineering:

- **Hand-code micro-tests** instead of building a full compiler toolchain.
- Use **intrinsics** (C/C++) that map onto new ISA/ASM extensions to prototype instruction ideas quickly.
- Prototype on an **FPGA** in a clever/minimal way to measure circuit-level characteristics (timing, area proxy, throughput).
- Build a **minimal simulation model** that captures only the critical aspects needed to validate the hypothesis (avoid full-system modeling unless required).

These tactics reduce the time/effort to get to a decisive signal.

---

## When to use it

Use `fail-fast.prompt` when you want to:

- Brainstorm 3–10 **novel** candidate research directions quickly
- Stress-test an idea before investing serious time
- Convert a fuzzy thought into a crisp experiment plan
- Teach students how to think like a reviewer and an engineer (novelty + validation path)

Best timing: the first day/week of a new direction, or whenever you feel “we’re wandering.”

---

## Inputs you provide

Minimum:
- A short problem area and constraints (domain, venue, time, resources)

Helpful:
- Target audience/venue (ISCA, DAC, MICRO, NSF, etc.)
- What you *can* and *cannot* build/measure (hardware access, datasets, simulation tools)
- A baseline you must beat (or at least compare to)
- What you consider “value” (throughput, energy, area, QoR, latency, security, etc.)

---

## Outputs (what you get)

The prompt returns:

- A ranked list of **Idea Cards** (3–10), each with:
  - One-sentence hypothesis and “why it matters”
  - **Novelty claim** and differentiator vs baselines
  - Key assumptions
  - Likely failure modes (“how this dies”)
  - **Cheapest decisive test** (killer experiment), ideally using a fail-fast pattern above
  - Stop / pivot criteria (explicit)
  - Week-one plan (concrete tasks)
- A short **Go / No-Go** summary of which ideas are worth exploring next week

---

## How to run it

1. Open `fail-fast.prompt` and fill in **SETTINGS** (scope, constraints, number of ideas).
2. Paste your rough idea(s) or problem statement.
3. Run once to generate Idea Cards.
4. Pick the top 1–2 and re-run with:
   - tighter novelty bars (explicit baselines/prior work),
   - tighter success metrics,
   - a stricter “killer test” budget (hours/days).

---

## Repository layout

- `README.md` — this file
- `fail-fast.prompt` — the prompt definition (copy/paste into your LLM tool)

---

## Attribution / credit

This prompt is adapted from Todd Austin’s “fail fast ideation” workflow shared here:

```text
https://chatgpt.com/share/69934cd0-689c-8005-9f27-1748ed2e7680
```

(If you adapt this prompt further, please keep the fail-fast structure: **novel hypothesis → assumptions → killer test → stop/pivot**.)

