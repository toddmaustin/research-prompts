# Orphan Finder (README)

This prompt helps you **trim a paper without deleting content** by finding and fixing *paragraph orphans* (paragraphs whose last line contains only a few words, wasting vertical space). It identifies candidate paragraphs and proposes **minimal, meaning-preserving rewrites** that “pull words up” to reclaim full lines and often recover **0.1–0.5 pages** near a submission deadline.

This workflow performs best when the model’s **thinking mode** is enabled (for example, **Extended Thinking** in ChatGPT or **Pro** mode in Gemini), especially when proposing low-risk rewrites across many paragraphs.

---

## What is a “paragraph orphan” (as used here)

A *paragraph orphan* is a paragraph where the **final rendered line** contains very few words (for example, **2–5 words**). These orphans often appear after late-stage edits and can cause page overflow (e.g., **10.2 pages** when you need **10.0**).

This prompt targets **micro-edits** that shorten earlier lines slightly so the last short line disappears.

---

## When to use it

Use `orphan-finder.prompt` when:

- You are **over the page limit** by a small amount (e.g., 0.1–0.3 pages).
- You want to avoid cutting methodology, results, or a figure.
- You want edits that are **surgical** and **meaning-preserving**.

Best timing: the final hour/day before submission, after major restructuring is complete.

---

## What you need to provide

This method depends on *how the text is actually wrapped into lines*.

Best inputs (choose one):

1. **Rendered text with hard line breaks** (preferred): paste the relevant page/section exactly as it appears in the PDF (including line breaks).
2. **A PDF excerpt with line numbers** (good): paste the text with line numbers if available.
3. **Plain paragraphs without line breaks** (fallback): the prompt can still propose micro-trims, but it cannot reliably guarantee that an orphan line will vanish.

If you want the most reliable results, run this on a **page-by-page** slice of your paper (or on the section that is pushing you over the limit).

---

## What you get (deliverables)

The prompt returns:

- A list of **candidate orphan paragraphs** (ranked by likely savings)
- The **exact orphan line** (or last-line word count) that triggered the flag
- One or more **minimal rewrites** per paragraph (with “before/after”)
- A short estimate of **risk** (chance of altering meaning) and **expected savings**
- A **page-by-page** summary if you provide paginated text

---

## Safety / guardrails (recommended expectations)

Good “orphan slaying” edits should:

- Preserve technical meaning and claims
- Avoid changing numbers, equations, citations, and terminology unless requested
- Prefer deletions of filler words (e.g., “very”, “quite”, “in order to”) and small restructures
- Never introduce new facts, citations, or claims

---

## Repository layout

- `README.md` — this file
- `orphan-finder.prompt` — the prompt definition (copy/paste into your LLM tool)

---

## Attribution / credit

This prompt is adapted from the “Orphan Slaying” prompt shared by **Karu Sankaralingam** on LinkedIn:
https://www.linkedin.com/posts/karusankaralingam_to-my-academic-colleagues-weve-all-been-activity-7420534273532882944-OXHq

---

## Practical tips

- Start with the **section that causes the overflow** (often Related Work or Evaluation).
- Fix the largest-impact orphans first (last line = 1–2 words).
- Re-render after each batch of edits; layout shifts can create or remove new orphans.
- Combine with a normal clarity pass (remove fluff) if you still need more space.

