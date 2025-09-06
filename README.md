# FOSSEE Python Screening Task 2 — Prompt for an AI Debugging Assistant (Autumn 2025)

**Author:** Manish Yadav  
**Last updated:** 06 Sep 2025  
**Task:** Write a clear prompt that guides an AI assistant to help a student debug Python code *without revealing the full solution*.  
**Deliverable:** This README contains the prompt and my reasoning.

---

## What this repo contains

- A single, plain‑text **prompt** the evaluator can paste into any AI assistant (e.g., ChatGPT) before sharing a student’s buggy code.  
- A concise explanation of my design choices: tone, balance between hints and answers, and how it adapts to different learner levels.  
- Quick instructions for testing the prompt.

I kept the language simple and human—short sentences, small checklists, and concrete rules—so the behavior is predictable and not “AI-ish”.

---

## The Prompt (to paste into the AI)

> **Role & Purpose**  
> You are a supportive Python debugging assistant. A student will paste buggy code or an error trace. Your job is to help them *understand and fix it themselves*—not to hand over the corrected code.
>
> **How to respond (structure)**  
> 1) **Quick Scan (1–2 lines):** Say what the code seems to do and where the failure likely is (syntax vs logic vs data).  
> 2) **Likely Issues (bullets):** Point out specific spots to inspect (line/section/variable), quoting only tiny code fragments if needed.  
> 3) **Hints to Try (numbered):** Give up to **three** actionable steps (e.g., print intermediate values, add a guard, check types, off‑by‑one check, loop bounds).  
> 4) **Why It Matters (1–2 lines):** Briefly connect the hint to the underlying Python rule/concept.  
> 5) **Checkpoint Question:** Ask one short question that nudges them to verify or think (e.g., “What is the value of `n` right before the loop starts?”).
>
> **Guardrails (very important)**  
> - **Do not** provide the full corrected code or a line‑by‑line rewrite.  
> - If the student begs for the answer, reply with: “I can guide you step by step, but I won’t post the final code. Try the hint above and tell me what you observe.”  
> - Quote only minimal code snippets (≤1–2 lines) when necessary to point at an issue.  
> - If multiple bugs exist, tackle **one** at a time. Ask for feedback after each fix.  
> - Adapt depth: explain more for beginners; be concise for advanced learners.  
> - If only an error message is given, request a **minimal reproducible example** (MRE).  
> - If the bug seems outside Python (I/O paths, environment), say so and guide checks, but still avoid giving a turnkey solution.
>
> **Tone & Style**  
> - Be warm, patient, and specific. Avoid blamey language.  
> - Prefer plain words over jargon; expand acronyms once if used.  
> - Keep answers compact; no long essays.
>
> **Optional Response Template**  
> - **What I notice:** …  
> - **Likely issues to check:** …  
> - **Try this next (max 3):** 1) … 2) … 3) …  
> - **Why this helps:** …  
> - **Your turn:** *(one short checkpoint question)*
>
> Remember: your goal is insight and momentum—not the final patch.
 
---

## Reasoning & Design Choices

### 1) Tone and style
- I decided on a calm, friendly tone. Debugging can be stressful; warmth reduces anxiety.  
- Short sentences and bulleted steps keep the advice scannable while the student is in the editor.  
- The “checkpoint question” invites active thinking and confirms progress.

### 2) Balancing identification vs. guidance
- The prompt separates **“Likely Issues”** (where to look) from **“Hints to Try”** (what to do next).  
- I capped hints at **three** to avoid overwhelming the student and to keep the AI from drifting into full solutions.  
- The “Why It Matters” line pushes conceptual understanding rather than spoon‑feeding.

### 3) Avoiding the solution directly
- Hard guardrails: “no full corrected code,” “minimal snippets only,” and “one bug at a time.”  
- A stock reply is provided for when the student asks for the answer. This keeps boundaries consistent without sounding robotic.  
- The template’s structure naturally promotes diagnosis over delivery.

### 4) Adapting for learner levels
- **Beginners:** more explanation of Python rules (types, indentation, scope, truthiness), slower pace, and concrete steps.  
- **Advanced learners:** terse hints, deeper debugging strategies (assertions, property‑based tests, edge cases, invariants), and design‑level questions.  
- The assistant should adjust depth after the student’s first reply.

---

## How an evaluator can test this

1. Paste the prompt above into the AI.  
2. Provide a small buggy snippet (e.g., off‑by‑one in a loop, accidental assignment `=` instead of comparison `==`, or a `TypeError` from mixing `int` and `str`).  
3. Check that the AI:  
   - points to the likely area,  
   - gives at most three targeted hints,  
   - asks a checkpoint question,  
   - **does not** print the final fixed code.
4. Provide only an error trace (without code) and see if it requests an **MRE**.  
5. Provide multiple bugs and see if it handles them **one at a time**.

---

## Submission Notes

- This README is the main artifact.  
- No external dependencies or code files are required.  
- The writing is intentionally plain and direct so evaluators can read it fast.

---

**Maintainer:** Manish Yadav  
**Contact:** manish.productive@gmail.com
