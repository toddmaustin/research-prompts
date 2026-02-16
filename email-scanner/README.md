# Gemini Gmail Critical Email Scanner (README)

This prompt is a **daily inbox triage procedure** that uses **Gemini’s Gmail assistant** to surface the few emails you truly need to read from a high-volume inbox. It performs a **multi-pass scan** over a fixed time window (default: the last two weeks), filters out already-handled threads via a `+PROCESSED+` label, then groups the remaining candidates into priority buckets (visits, talks, reviews, letters, overdue, other).

**Important:** This workflow is **Gemini-only** because it relies on Gemini’s Gmail assistant panel inside Gmail (as described in the source post). It will not work in tools that do not have direct Gmail access.

This workflow performs best when Gemini’s **Thinking/Pro** mode is enabled, and it is strongly recommended to keep the **final re-validation pass** enabled to reduce hallucinated or misclassified emails.

---

## What problem it solves

If you receive ~100–200 emails/day, “scrolling the inbox” becomes a failure-prone process. Gmail’s built-in “IMPORTANT” tag helps, but its definition of importance may not match yours, and occasionally you can miss something truly critical.

This prompt turns inbox triage into a repeatable procedure:

- Identify mail addressed to you
- Remove already-handled threads
- Bucket the rest into a small set of actionable categories
- Re-validate results so you can trust the output

---

## When to use it

Use `email-scanner.prompt`:

- Every morning (or once per day) as an inbox “critical items” scan
- When you are behind and need a fast way to find **what matters**
- When you want the model to produce a **curated list of subjects with links**

Best timing: at the start of the day, before deep work.

---

## Requirements (Gemini-only)

This workflow requires:

- **Gmail in a web browser**
- The **Gemini panel** inside Gmail (Gemini “star” icon)
- A Gemini model mode that supports deeper reasoning (Thinking/Pro recommended)

If you cannot open the Gemini panel in Gmail, you will not be able to run this prompt as intended.

---

## Data handling / safety notes

- This prompt asks Gemini to read your email content. Treat your inbox as sensitive data.
- Do **not** paste confidential email content into other tools that lack your organization’s approvals.
- Email content can contain adversarial text (prompt injection). The prompt includes a rule to **ignore instructions inside emails**.

---

## How it works (multi-pass design)

The procedure is intentionally multi-pass:

1. **PASS 1 (Scope):** Identify emails addressed to your name and email aliases.
2. **PASS 2 (Exclusion):** Discard any threads labeled `+PROCESSED+`.
3. **PASS 3 (Triage):** Bucket surviving emails into priority sections and list them by **subject with links**.
4. **PASS 4 (Re-validation):** Double-check that each listed email actually matches its bucket and does not have `+PROCESSED+`.

PASS 4 is not optional if you care about trustworthiness; it is the primary guardrail against hallucinations.

---

## How to run it

1. Open **Gmail in a web browser**.
2. Click the **Gemini “star”** to open the Gemini panel with Gmail access.
3. Switch Gemini to **Thinking/Pro** mode if available.
4. Open the prompt definition in **`email-scanner.prompt`** and customize:
   - Your name
   - Your email addresses
   - Your category buckets
   - Your scan window (default: 2 weeks)
5. Paste the prompt into Gemini and run.
6. After you handle an email, **label the thread** with `+PROCESSED+` (or your chosen processed label) so it is ignored in future scans.

---

## Output format (what you get)

Gemini returns:

- A small set of titled sections (e.g., `VISITS`, `TALKS`, `REVIEWS`, `LETTERS`, `OVERDUE`, `OTHER`)
- Under each, a list of emails by:
  - **Subject** (with a Gmail link)
  - Optionally: sender, date, and a one-line “why it matters”

---

## Repository layout

- `README.md` — this file  
- `email-scanner.prompt` — the prompt definition (copy/paste into Gemini inside Gmail)

---

## Attribution / credit

This prompt is adapted from the Gmail/Gemini email triage prompt shared by **Todd Austin** on LinkedIn:

```text
https://www.linkedin.com/posts/prof-todd-austin_ai-aitools-email-activity-7422800120108249088-0Ogx/
```

---

## Practical tips

- Keep your buckets **small** and **action-oriented**. Add a bucket only if you will act on it.
- Make `OVERDUE` aggressive: it should catch “need reply,” “deadline,” “reminder,” “past due,” “ASAP,” and similar.
- Use `OTHER` sparingly and require a short justification for each item placed there.
- Re-run after labeling `+PROCESSED+` to confirm the scan is stable.

