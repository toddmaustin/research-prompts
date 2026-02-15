# Brutal Final-Pass Reviewer (README)

This prompt is a **near-submission quality gate** for research papers. It is designed for the last few hours (or last day) before a deadline, when you need **high-signal triage**: what must be fixed to avoid rejection or credibility loss, vs what can be polished if time remains.

This workflow performs best when the model’s **thinking mode** is enabled (for example, **Extended Thinking** in ChatGPT or **Pro** mode in Gemini), especially for logic, consistency, and citation-audit passes.

---

## What this is for

Use this prompt when you have a **near-final draft** and want a structured review that covers:

- Proofreading (grammar, clarity, awkward phrasing)
- Fact checking (as far as possible from the text you provide)
- Consistency checking (terminology, acronyms, figure numbers, references, notation)
- Logic checking (gaps, contradictions, unstated assumptions, overclaims)
- Citation audit (missing citations, suspicious citations, unsupported assertions)
- Style constraints (e.g., remove em dashes)
- Reviewer traps (what a skeptical PC member will attack)

This is not a substitute for author judgment. It compresses the time required for a thorough pass and reduces “silent” errors that are easy to miss when tired.

---

## Why it works (prompt-as-procedure)

This prompt is written as a **procedure**, not a casual request. That matters because research editing is:

- **High-stakes**: a single overclaim, inconsistent term, or wrong baseline can sink a paper
- **Adversarial**: reviewers look for gaps, missing comparisons, and unsupported claims
- **Audit-heavy**: you need issues tied to specific text, not vague suggestions

The procedure format forces:
- **Repeatability** (same structure every run)
- **Triage** (IMPORTANT vs SUGGESTED)
- **Traceability** (locations + quoted snippets)
- **Guardrails** (no invented citations, explicit “UNVERIFIED” labels)

---

## What you get (deliverables)

The output is intentionally shaped like a “submission war-room” checklist:

1. **IMPORTANT CHANGES**  
   Must-fix issues that affect correctness, credibility, or acceptance likelihood.

2. **SUGGESTED CHANGES**  
   Polish, clarity improvements, phrasing and organization enhancements.

3. **CONSISTENCY REPORT (table)**  
   Canonical terminology + where inconsistencies appear.

4. **CITATION AUDIT (table)**  
   Claim-by-claim flags for missing or suspicious citations.

5. **FINAL “LOGIC COP” SUMMARY**  
   Top overclaims, handwavy arguments, and narrative contradictions.

---

## When to use it

### Best time
- Final 2–24 hours before submission
- After major restructuring is done
- When you want to lock correctness and coherence

### Best inputs
- Full paper text (preferred), or sections if necessary
- Figures + captions (highly recommended)
- Reference list / BibTeX (recommended)
- Venue constraints (page limit, formatting expectations)
- Style constraints (for example, “no em dashes”)

---

## What it does not do

This workflow is designed to avoid two failure modes: “rewrite everything” and “invent content.”

It will not (and should not be used to):
- Rewrite the entire paper end-to-end
- Add new claims, new results, or new experiments
- Fabricate citations or numbers
- Guess missing context (it should label items **UNVERIFIED** if needed)

---

## How to run it

1. Open the prompt definition in **`brutal-review.prompt`**.
2. Paste your manuscript (or sections) into the prompt’s **BEGIN REVIEW** area.
3. If you have them, also paste:
   - figure captions (and any key figures/tables)
   - the references section or BibTeX entries
4. Apply fixes in this order:
   1) IMPORTANT (High confidence)  
   2) IMPORTANT (Medium/Low confidence; verify)  
   3) SUGGESTED as time allows

---

## Repository layout

- `README.md` — this file
- `brutal-review.prompt` — the prompt definition (copy/paste into your LLM tool)

---

## Practical tips (from repeated use)

- Run it twice: once on the full paper, once on **intro + conclusion + captions**.
- Always include captions: caption errors and mismatched figure references are common.
- Treat **UNVERIFIED** as a to-do list: either add evidence, qualify, or delete.
- Never accept invented citations: if it suggests a citation, you must supply/verify it.

---

## Recommended variations

- **Short pass (time-crunched):** run on abstract + intro + conclusion + captions.
- **Venue-specific:** add venue constraints (length, novelty emphasis, baseline expectations).
- **Lab policy:** add a rule limiting sensitive inputs (partner data, embargoed results).

---

## License / reuse

Use freely within your lab. If you adapt it, keep the **guardrails** and the **IMPORTANT vs SUGGESTED** triage structure, that’s where most of the value comes from.

