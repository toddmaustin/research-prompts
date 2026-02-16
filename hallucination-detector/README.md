# Hallucination Detector (README)

This prompt is a **second-opinion “hallucination detector”** for AI-generated content. It scans a draft for five common failure modes and reports issues **in order of urgency**, with evidence and concrete fixes.

**Best practice:** run the hallucination detector on **another vendor’s AI** than the one that produced the draft (e.g., draft with ChatGPT, validate with Gemini; or draft with Gemini, validate with ChatGPT). The point is to reduce correlated errors by using a more independent second opinion.

This workflow also benefits from enabling **thinking mode** (for example, Extended Thinking in ChatGPT or Pro/Thinking in Gemini), but cross-vendor validation is the key reliability lever.

---

## What it checks (the five variants)

The detector looks for:

1. **Factual fabrication**  
   Claims, numbers, quotes, or citations that appear invented or unsupported.

2. **Faithfulness hallucinations (source drift)**  
   The draft misrepresents provided sources (e.g., the source says X, the draft claims Y).

3. **Logical and mathematical errors**  
   Invalid inferences, broken reasoning chains, arithmetic mistakes, inconsistent units.

4. **Internal contradictions**  
   The draft contradicts itself (definitions, assumptions, results, timelines, counts).

5. **Sycophancy and bias**  
   The draft agrees too readily, flatters, or leans into the user’s framing in a way that distorts truth/uncertainty.

---

## When to use it

Use `hallucination-detector.prompt` when:

- You used AI to draft **professional** content (papers, proposals, reviews, reports, emails)
- You need a fast “quality gate” before sending or submitting
- You have sources and want to ensure the draft is **faithful** to them
- You suspect a model may have “filled in gaps” with plausible fiction

---

## Why cross-vendor works best

Hallucinations are often “rare error modes” of a model. Using a **different vendor/model family** for validation lowers the chance that the second model repeats the *same* mistake, especially for vendor-specific quirks.

Important nuance:
- Cross-vendor checking is not a proof of correctness.
- Models can share training data and biases, so correlated mistakes still happen.
- That is why the prompt requires **evidence** (quotes/snippets, recomputation, and “UNVERIFIED” flags).

---

## What you need to provide

Minimum:
- The **AI-generated draft** to validate.

Recommended:
- Any **sources** the draft is based on (links, excerpts, PDFs, citations, notes).
- The **intended audience** and what “correct” means (e.g., strict citation policy, allowed assumptions).

---

## Output format (what you get)

The prompt returns a ranked issue list. Each issue includes:

- **Severity:** {CRITICAL, HIGH, MEDIUM, LOW}
- **Category:** one of the five variants above
- **Claim snippet:** quoted text from the draft
- **Evidence:** why it’s wrong/suspect (and where the source disagrees, if sources exist)
- **Fix:** exact replacement text or an action (add citation, delete, qualify, recompute)
- **Confidence:** {High, Medium, Low}

It also returns a short **clean draft patch list** (copy/paste replacements) when possible.

---

## How to run it (recommended protocol)

1) **Draft** with Model A (your primary writing model).  
2) **Validate** with Model B (**another vendor/model family**) using `hallucination-detector.prompt`.  
3) Apply fixes in your source document.  
4) Optionally, re-run the detector after edits.

If you are validating a long document, run it section-by-section (e.g., abstract + intro; then methods; then results).

---

## Repository layout

- `README.md` — this file  
- `hallucination-detector.prompt` — the prompt definition

---

## Attribution / credit

This prompt is adapted from the “Second Opinion Protocol / Hallucination Detector” shared by **Todd Austin** on LinkedIn:

```text
https://www.linkedin.com/posts/prof-todd-austin_ai-productivity-promptengineering-activity-7424873822614441984-t3ki
```

