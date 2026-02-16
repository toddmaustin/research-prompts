# writing-voice (README)

This package contains two prompts that help an LLM write in **your** recognizable writing voice:

1) **`voice-analyzer.prompt`** — analyzes multiple *non-AI* exemplar writings to build a reusable **VOICE CARD** (a compact “style model”).
2) **`write-in-voice.prompt`** — uses that VOICE CARD to turn rough notes into polished prose, then **self-checks** voice fidelity and regenerates if needed.

This workflow performs best when the model’s **thinking mode** is enabled (for example, **Extended Thinking** in ChatGPT or **Pro** mode in Gemini), especially for capturing cadence/structure and for the self-evaluation loop.

---

## What this is for

Use these prompts when you want AI assistance **without losing your voice**. Common uses:

- Drafting technical prose from bullets (papers, proposals, reviews)
- Writing emails and endorsements in a consistent institutional tone
- Producing LinkedIn posts that still sound like you
- Keeping multi-author drafts coherent (one voice, not five)

A side effect (not a guarantee) is that prose that matches a real person’s voice often looks less “generic LLM,” which may reduce false positives from AI-text detectors.

---

## Inputs you should provide

### For `voice-analyzer.prompt`
- **3–10 exemplar writings** that are *definitely your own* and *not AI-generated*
- Prefer exemplars from the **same genre** you want to generate (e.g., research writing vs emails)
- Include at least one piece you consider “peak you” (best example of your voice)

### For `write-in-voice.prompt`
- The **VOICE CARD** output from `voice-analyzer.prompt`
- Rough bullets / notes / constraints (and optionally a rough draft you want rewritten)
- Target document type (paper paragraph, email, review, LinkedIn post, etc.)

---

## How to run

1) Run **`voice-analyzer.prompt`** with your exemplar writings.
   - Save the resulting **VOICE CARD** (commit it to a private notes doc, or paste it into a “system prompt” for a custom bot).

2) Run **`write-in-voice.prompt`** with:
   - the VOICE CARD
   - your bullets/draft
   - the desired output format and constraints

3) If the output feels “off,” update the VOICE CARD:
   - add 1–2 more exemplars
   - tighten the “avoid” list
   - add a short phrase bank of your favorite transitions/verbs

---

## Data handling / safety notes

- Your exemplars may contain sensitive information. **Redact** names, private details, student information, and confidential partner content.
- Treat all model output as **draft**: you remain responsible for correctness, citations, and factual claims.
- Do not use this workflow to fabricate credentials, endorsements, or facts.

---

## Repository layout

- `README.md` — this file
- `voice-analyzer.prompt` — builds the VOICE CARD from exemplars
- `write-in-voice.prompt` — generates prose using the VOICE CARD + a self-check loop

---

## Attribution / credit

These prompts are adapted from the two-prompt “write in your voice” workflow shared by **Todd Austin** on LinkedIn:

```text
https://www.linkedin.com/posts/prof-todd-austin_ai-aitools-aiassistance-activity-7423795647046336514-GzT_/
```

