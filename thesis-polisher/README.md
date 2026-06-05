# Thesis Polisher (README)

This prompt is a **near-submission quality gate** for a PhD thesis. It is adapted from the `brutal-review` prompt, but tuned for the final days before sending a dissertation to a committee, when you need **high-signal triage** across correctness, consistency, thesis-level narrative, and committee readiness.

This workflow performs best when the model’s **thinking mode** is enabled (for example, **Extended Thinking** in ChatGPT or **Pro** mode in Gemini), especially for cross-chapter consistency, narrative flow, citation auditing, and logic checks.

---

## What this is for

Use this prompt when you have a **near-final thesis draft** and want a structured review that covers:

- Proofreading (grammar, clarity, awkward phrasing)
- Fact checking (as far as possible from the text you provide)
- Consistency checking (terminology, acronyms, chapter references, figure numbers, notation)
- Logic checking (gaps, contradictions, unstated assumptions, overclaims)
- Citation audit (missing citations, suspicious citations, unsupported assertions)
- Style constraints (e.g., remove em dashes)
- Committee-reader traps (what an advisor, committee member, or future reader will attack)
- Thesis-specific structure (abstract, thesis statement, cohesive narrative, conclusion, and future work)

This is not a substitute for author or advisor judgment. It is designed to compress the time required for a thorough final pass and reduce “silent” dissertation errors that are easy to miss when tired or too close to the material.

---

## Why it works (prompt-as-procedure)

This prompt is written as a **procedure**, not a casual request. That matters because thesis editing is:

- **High-stakes**: a single overclaim, inconsistent definition, wrong chapter reference, or missing caveat can undermine credibility
- **Long-form**: problems often appear across chapters, not just within one section
- **Narrative-heavy**: the document must communicate a coherent thesis, not merely collect papers
- **Audit-heavy**: you need issues tied to specific locations and snippets, not vague suggestions

The procedure format forces:

- **Repeatability** (same structure every run)
- **Triage** (IMPORTANT vs SUGGESTED)
- **Traceability** (locations + quoted snippets)
- **Guardrails** (no invented citations, explicit “UNVERIFIED” labels)
- **Thesis-level review** (abstract, thesis statement, chapter transitions, conclusion, and future work)

---

## What you get (deliverables)

The output is intentionally shaped like a dissertation “final defense readiness” checklist:

1. **IMPORTANT CHANGES**  
   Must-fix issues that affect correctness, credibility, or committee readiness.

2. **SUGGESTED CHANGES**  
   Polish, clarity improvements, phrasing and organization enhancements.

3. **CONSISTENCY REPORT (table)**  
   Canonical terminology + where inconsistencies appear.

4. **CITATION AUDIT (table)**  
   Claim-by-claim flags for missing or suspicious citations.

5. **FINAL “LOGIC COP” SUMMARY**  
   Top overclaims, handwavy arguments, and narrative contradictions.

6. **PhD thesis specific recommendations**  
   A thesis-level assessment of the abstract, thesis statement, background consolidation, chapter-to-chapter narrative, conclusion, future-work framing, and artifacts that make chapters read like pasted-in papers rather than an integrated dissertation.

---

## When to use it

### Best time

- Final few days before sending the thesis to your committee
- After major restructuring is done
- When the thesis has stable chapters, figures, citations, and front/back matter
- When you want to lock correctness, coherence, and committee-readiness

### Best inputs

- Full thesis text (preferred), or chapters if necessary
- Abstract, introduction, conclusion, and future-work sections (strongly recommended)
- Figures, tables, captions, and lists of figures/tables (highly recommended)
- Reference list / BibTeX (recommended)
- Any university, department, advisor, or committee constraints
- Style constraints (for example, “no em dashes” or “preserve my writing voice”)

---

## What it does not do

This workflow is designed to avoid two failure modes: “rewrite everything” and “invent content.”

It will not (and should not be used to):

- Rewrite the entire thesis end-to-end
- Add new claims, new results, new experiments, or new contributions
- Fabricate citations, numbers, or historical framing
- Guess missing context (it should label items **UNVERIFIED** if needed)
- Replace feedback from an advisor, committee member, or graduate school formatter

---

## How to run it

1. Open the prompt definition in **`thesis-polisher.prompt`**.
2. Upload or paste your thesis draft into the prompt’s **BEGIN REVIEW** area.
3. If you have them, also provide:
   - figure/table captions and references
   - the references section or BibTeX entries
   - university formatting or committee constraints
   - known style constraints
4. Apply fixes in this order:
   1. IMPORTANT (High confidence)
   2. IMPORTANT (Medium/Low confidence; verify)
   3. Thesis-specific recommendations that affect narrative coherence
   4. SUGGESTED changes as time allows

---

## Repository layout

- `README.md` — this file
- `thesis-polisher.prompt` — the prompt definition (copy/paste into your LLM tool)

---

## Practical tips (from repeated use)

- Run it once on the full thesis, then a second time on **abstract + introduction + chapter openings/endings + conclusion**.
- Always include captions: mismatched figure/table references and stale captions are common in long documents.
- Ask for special attention to paper-to-thesis conversion artifacts, such as “in this paper,” duplicated related-work sections, inconsistent “we/I” usage, or chapters that do not motivate one another.
- Treat **UNVERIFIED** as a to-do list: either add evidence, qualify, or delete.
- Never accept invented citations: if it suggests a citation, you must supply and verify it.

---

## Recommended variations

- **Short pass (time-crunched):** run on abstract + introduction + conclusion + future work + captions.
- **Narrative pass:** run on chapter introductions and conclusions only, asking whether each chapter motivates the next.
- **Committee pass:** add known committee-member concerns, advisor preferences, and department expectations.
- **Paper-conversion pass:** ask it to find artifacts from imported papers, including phrasing, duplicated background, inconsistent notation, and stale cross-references.
- **Lab policy:** add a rule limiting sensitive inputs (partner data, embargoed results, unpublished results, or confidential committee feedback).

---

## License / reuse

Use freely within your lab. If you adapt it, keep the **guardrails**, the **IMPORTANT vs SUGGESTED** triage structure, and the thesis-specific recommendation pass, that’s where most of the value comes from.
