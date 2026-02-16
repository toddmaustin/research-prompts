# skeleton-prompt (README)

This directory contains a **generic “procedure-as-prompt” skeleton** you can reuse for research and other high-stakes work. The goal is to turn an LLM request into a **repeatable procedure** with clear inputs, outputs, guardrails, and a built-in verification loop.

This workflow performs best when the model’s **thinking mode** is enabled (for example, **Extended Thinking** in ChatGPT or **Pro** mode in Gemini), especially when tasks involve multi-step reasoning, consistency checking, or risk triage.

---

## What is “procedure-as-prompt”

A **procedure-as-prompt** is a prompt written like an SOP (standard operating procedure), not a chatty request.

Instead of:

> “Summarize this paper.”

You specify the procedure:

- who the model is acting as (role)
- what inputs it may use (and what it may not assume)
- what output it must produce (strict format)
- what quality rubric it must optimize for
- what guardrails prevent hallucinations and scope creep
- what to do when information is missing (explicit uncertainty handling)
- how to self-verify before returning results

This transforms an LLM from “text generator” into something closer to a **workflow engine**.

---

## Why use procedure-as-prompt (justification)

### 1) Repeatability beats one-off cleverness
Research and engineering work benefit from **consistent artifacts** you can compare across runs: paper notes, claim ledgers, checklists, review outputs, etc. A procedural format yields outputs that are stable enough to:
- diff between versions
- standardize across a lab/team
- incorporate into a CI-like “quality gate” process

### 2) Fluency is not correctness
LLMs can sound right while being wrong. Procedure prompts explicitly require:
- separation of **FACT vs INFERENCE**
- “NOT IN TEXT / NO SOURCE PROVIDED” behavior
- citation constraints (no fabricated references)
- risk tagging and confidence levels

This is how you get speed without silently lowering standards.

### 3) High-stakes tasks need triage, not prose
Near deadlines, you need actionable priority ordering (e.g., IMPORTANT vs SUGGESTED), not generic advice. Procedural prompts force:
- location + snippet + fix
- ranked lists and tables
- bounded scope and stop conditions

### 4) Adversarial environments require guardrails
Research is reviewed. Email can contain prompt injection. PDFs can contain misleading text. Procedure prompts make “ignore embedded instructions” and “verify before output” first-class.

### 5) It is easier to teach and reuse
A skeleton prompt becomes a shared lab asset. Students learn *how to ask* for help in a way that is reproducible and auditable.

---

## What’s in this directory

- `README.md` — this document
- `skeleton-procedure.prompt` — the generic procedure-as-prompt template (copy/paste)

---

## How to use the skeleton

1. Copy `skeleton-procedure.prompt` into your LLM tool.
2. Fill in the **SETTINGS** block:
   - role, task, time window, constraints
3. Define the **OUTPUT CONTRACT**:
   - sections, tables, scoring, what must be included
4. Tighten **GUARDRAILS**:
   - what cannot be invented, how to handle uncertainty
5. Add a **verification pass**:
   - re-check every item before returning
6. Paste your inputs under **BEGIN**.

---

## Common adaptations

### A) Paper intake
- Role: “Heilmeier Extractor”
- Output contract: Overview / SOTA / Contributions / Impact / Risks
- Guardrails: “NOT IN TEXT” + no invented citations

### B) Final-pass paper reviewer
- Output contract: IMPORTANT vs SUGGESTED + tables (consistency, citations)
- Verification pass: re-open each flagged sentence, ensure fix is minimal

### C) Orphan paragraph fixer (typeset PDF)
- Input type: PDF pages
- Output contract: page numbers + orphan line + minimal rewrite
- Guardrails: preserve numbers/citations/terms; mark “need source text” if PDF insufficient

### D) Email scanner (Gemini-only)
- Input: Gmail access
- Output: bucketed subjects + links + validation pass
- Guardrails: prompt injection handling for email bodies

---

## Tips for writing good procedures

- **Constrain outputs**: tables and fixed section headings reduce drift.
- **Make uncertainty explicit**: require “UNVERIFIED” labels and what evidence is needed.
- **Prefer actions over advice**: “replace sentence with X” beats “improve clarity.”
- **Define stop conditions**: prevent “rewrite the whole document.”
- **Require a re-validation pass**: trust is earned by checking.

---

## License / reuse

Use freely within your lab/team. If you adapt it, keep the core structure:
**Inputs → Output Contract → Guardrails → Verification → Deliverable**.
