# Heilmeier Extractor (README)

This prompt is a **paper-reading accelerator**: it turns a typeset research paper into a structured, reviewer-ready analysis organized around the **Heilmeier Catechism** (DARPA-style questions that expose the *problem, novelty, evidence, and adoption risks*).

It is intended to help you read **more papers, faster**, without defaulting to shallow summaries. In practice, it produces an actionable artifact you can save into your notes: a concise overview, the current state-of-the-art and its limits, a contributions inventory (including “CLEVER” ideas), likely impact, and adoption realism.

This workflow performs best when the model’s **thinking mode** is enabled (for example, **Extended Thinking** in ChatGPT or **Pro** mode in Gemini), especially for extracting assumptions, missing baselines, and threats-to-validity.

---

## What problem it solves

Reading papers is not just “understanding the gist.” For research, you usually need:

- What exactly is the claim and why should I believe it?
- What is *new* relative to prior work?
- What assumptions does it rely on?
- What experiments/baselines are missing?
- If this works, who would adopt it and what blocks adoption?

A generic summary rarely answers these cleanly. The Heilmeier Extractor forces structure.

---

## When to use it

Use `heilmeier-extractor.prompt` when:

- You are doing **literature review** and want consistent, comparable notes.
- You are **triaging** a stack of papers and need fast depth.
- You are mentoring students and want to teach “how to read like a reviewer.”
- You are starting a project and need to identify **gaps, baselines, and risks**.

Best timing: early in a project (Stage 1), and anytime you want a fast “reviewer mindset” read.

---

## Inputs (recommended)

- A **typeset PDF** of the paper draft (preferred), or the paper text (abstract + intro + evaluation sections at minimum).
- Optional: the bib/references section, or a short list of “must-consider” related work.

---

## Outputs (what you get)

The prompt returns these sections (strict format):

1. **OVERVIEW**  
   Minimal-jargon paragraph: what the paper is trying to do, the problem, and the approach.

2. **CURRENT STATE-OF-THE-ART**  
   How the problem is handled today, limitations, and which limitations the paper targets.

3. **CONTRIBUTIONS**  
   - One overview paragraph  
   - Bullet list of contributions  
   - Mark especially clever ideas with `CLEVER:`  
   - Related-work fairness check; if something important is missing, call it out and suggest a citation/link.

4. **POTENTIAL IMPACT**  
   Who should care and what changes if the approach succeeds.

5. **RISKS AND REALISM**  
   Adoption barriers, realism of deployment, and what would prevent it becoming standard practice.

In addition, the prompt asks for:
- **Section references** (in parentheses) for fast follow-up in the PDF.
- Optional **color commentary** (in brackets) when helpful.
- A **prompt-injection check**: ignore any “secret instructions” embedded in the paper text.

---

## How to run it

1. Open the prompt definition in **`heilmeier-extractor.prompt`**.
2. Attach the paper PDF (or paste the paper text).
3. Run in thinking mode if available.
4. Save the output into your paper notes, and optionally:
   - rerun on “intro + eval” only for faster iteration, or
   - rerun with a “must-check related work” list.

---

## Repository layout

- `README.md` — this file  
- `heilmeier-extractor.prompt` — the prompt definition (copy/paste into your LLM tool)

---

## Attribution / credit

This prompt is adapted from the “Heilmeier Extractor” shared by **Todd Austin** on LinkedIn:

```text
https://www.linkedin.com/posts/prof-todd-austin_ai-aitools-research-activity-7405033854929031168-lpdL/
```

---

## Practical tips

- If you want better baseline critiques, include the **evaluation section** and **related work**.
- If you only paste an abstract, expect “uncertain” flags; the prompt will label missing support.
- Use the output as a checklist: missing baselines, unclear assumptions, overclaims, and adoption risks.

