# research-prompts

A small collection of **procedure-as-prompt** templates I use to integrate AI tools into a computer engineering research workflow: reading papers faster, tightening drafts near deadlines, preserving writing voice, and reducing hallucinations via cross-checking.

Most prompts are written as **repeatable procedures** (clear inputs, strict outputs, guardrails, and a verification pass), so you can reuse them across projects and teach them to students. For best results, enable your model’s **thinking mode** (for example, Extended Thinking in ChatGPT or Pro/Thinking in Gemini) when available.

## What’s in this repo

- **`brutal-review/`** — This prompt is a **near-submission quality gate** for research papers. It is designed for the last few hours (or last day) before a deadline, when you need **high-signal triage**: what must be fixed to avoid rejection or credibility loss, vs what can be polished if time remains.
- **`chalk-talk/`** — This prompt generates a **chalkboard-style “chalk talk” slide** for teaching a concept: bubbles/circles connected by arrows, short handwritten-style text, and a visual flow that mirrors how an instructor would explain the idea at a board.
- **`email-scanner/`** — This prompt is a **daily inbox triage procedure** that uses **Gemini’s Gmail assistant** to surface the few emails you truly need to read from a high-volume inbox. It performs a **multi-pass scan** over a fixed time window (default: the last two weeks), filters out already-handled threads via a `+PROCESSED+` label, then groups the remaining candidates into priority buckets (visits, talks, reviews, letters, overdue, other). **Gemini-only** (runs in Gmail’s Gemini assistant panel).
- **`hallucination-detector/`** — This prompt is a **second-opinion “hallucination detector”** for AI-generated content. It scans a draft for five common failure modes and reports issues **in order of urgency**, with evidence and concrete fixes. Best run on a **different vendor/model** than the one that produced the draft.
- **`heilmeier-extractor/`** — This prompt is a **paper-reading accelerator**: it turns a typeset research paper into a structured, reviewer-ready analysis organized around the **Heilmeier Catechism** (DARPA-style questions that expose the *problem, novelty, evidence, and adoption risks*).
- **`orphan-finder/`** — This prompt helps you **trim a paper without deleting content** by finding and fixing *paragraph orphans* (paragraphs whose last line contains only a few words, wasting vertical space). It identifies candidate paragraphs and proposes **minimal, meaning-preserving rewrites** that “pull words up” to reclaim full lines and often recover **0.1–0.5 pages** near a submission deadline.
- **`skeleton-prompt/`** — This directory contains a **generic “procedure-as-prompt” skeleton** you can reuse for research and other high-stakes work. The goal is to turn an LLM request into a **repeatable procedure** with clear inputs, outputs, guardrails, and a built-in verification loop. Use this format for new contributions.
- **`writing-voice/`** — This package contains two prompts that help an LLM write in **your** recognizable writing voice: Includes `voice-analyzer.prompt` and `write-in-voice.prompt`.

## Getting started

1. Pick a directory above and open its `README.md`.
2. Copy the corresponding `.prompt` file into your LLM tool.
3. Fill in the **SETTINGS** block and run on your input (PDF, draft text, inbox, etc.).
4. Treat the output as **draft guidance**: you remain responsible for correctness, citations, and policy compliance.

## Contributions welcome

If you have a prompt that improves research productivity (paper intake, experiment planning, review writing, proposal editing, teaching diagrams, etc.), please open a PR.

A few requests:
- Please format new prompts using the **`skeleton-prompt/`** procedure template (inputs → output contract → guardrails → verification → deliverable).
- Include a short `README.md` in the new directory explaining *when to use it*, *inputs/outputs*, and any *vendor/tool requirements* (Gemini-only, PDF required, etc.).
- If you are adapting someone else’s idea, **attribute the source** in the README.

## License

Distributed under the Apache 2.0 license, please see [`LICENSE`](LICENSE) for details.

