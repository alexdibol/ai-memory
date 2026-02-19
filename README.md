# AI Long Memory — Long-Context Reasoning Under Governance (Retrieval · State · Time)

Governance-first · auditable · reproducible · human-accountable  
Built for **MBA / Master of Finance cohorts** and **professional finance / trading / research practitioners** who need mechanism clarity under constraint.

---

## What this repository is

This repository is the governed home of **AI Long Memory**: a Colab-first laboratory for building and reviewing **long-context systems** that claim to “remember” across long documents, long workflows, and repeated interactions—**without confusing recall with truth**.

The objective is not “bigger context windows.”  
The objective is **a reviewable memory controller**: a system that behaves like a contract—explicit state, explicit retrieval, explicit constraints, explicit termination, explicit artifacts—so an independent reviewer can answer:

- what the system *kept* vs what it *ignored* (and why)
- what was retrieved, from where, and with what ranking logic
- how memory updates occurred (what changed, what did not)
- which statements were supported vs assumed vs unresolved
- where the system stopped, and what required human escalation
- how errors propagate under long context (dilution, inversion, anchoring)

This repo is intentionally explicit about limits:

- it does **not** treat “it was in the context” as evidence
- it does **not** claim correctness of external facts by default
- it does **not** assume retrieval quality is stable under scale
- it does **not** promise performance, alpha, or deployability

**Core premise:**  
**Capability ↑ ⇒ Risk ↑ ⇒ Controls ↑**

---

## Repository structure (as in this repo)

- **/book/**  
  The book source. The book is the governing spec: definitions, mechanisms, failure modes, acceptance gates for long memory.

- **/notebooks/**  
  The governed laboratories that operationalize the book with deterministic setups, diagnostics, and mandatory artifacts.

---

## The book structure (3 chapters)

This repository is organized to match the book exactly.  
Each chapter has corresponding governed notebooks.

### Chapter 1 — Why Long Memory Fails Without Governance
Long context is not “more knowledge.” It is **more opportunity to be wrong with confidence**.

Chapter 1 formalizes:
- the difference between **context**, **retrieval**, and **memory**
- why “more tokens” can reduce accuracy (dilution, distraction, anchoring)
- why long memory amplifies professional risk (selective recall, plausible nonsense)
- evidence discipline: **facts vs assumptions vs open items** as first-class output
- baseline failure modes: context drift, retrieval hallucination, silent overwrite, false continuity

Deliverable expectation:
- a reviewer can reconstruct the system’s *information path* from artifacts, not persuasion

### Chapter 2 — Mechanisms: Memory as a Controller (State + Retrieval + Update)
A long-memory system worthy of professional use must be designed like a controller:
- explicit **state** (what is known, unknown, pending, and prohibited)
- explicit **retrieval** (query construction, ranking, inclusion thresholds)
- explicit **update rules** (what becomes memory, what is discarded, what requires confirmation)
- explicit **constraints** (scope, refusal rules, evidence minimums)
- explicit **termination** (stop is a feature, not a bug)
- explicit **escalation paths** (human review triggers)

Chapter 2 operationalizes:
- bounded retrieval (top-k, budgets, and “why this chunk” provenance)
- memory write policies (no silent promotion of guesses)
- conflict handling (contradictions become review items, not overwritten facts)
- deterministic normalization (seeded tests; controlled perturbations)
- structured outputs that preserve uncertainty rather than hiding it

Deliverable expectation:
- the system can explain *why it retrieved*, *why it updated*, *why it refused*, and *why it stopped*

### Chapter 3 — Evaluation & Acceptance: Reproducible Stage Gates for “Remembering”
This repo is not a leaderboard. It is an acceptance framework.

Chapter 3 defines:
- acceptance criteria based on **traceability**, not eloquence
- robustness across seeds and controlled context perturbations
- retrieval correctness under scale (stress tests, adversarial distractors)
- refusal correctness (knowing when not to answer)
- exportable “advance / do-not-advance” decisions

Deliverable expectation:
- promotion is earned via artifacts and gates, not vibes

---

## Notebooks (how they map to the 3 chapters)

The notebooks are not “examples.” They are the operational proof of the book.

- **Chapter 1 notebooks** focus on:
  - long-context failure demonstrations (dilution, inversion, anchoring)
  - disciplined separation of facts/assumptions/open items
  - deterministic setup and artifact hygiene
  - early termination and escalation posture

- **Chapter 2 notebooks** focus on:
  - explicit state machines and memory update rules
  - governed retrieval (budgets, thresholds, provenance)
  - contradiction handling and safe “I don’t know” behavior
  - structured synthesis that cannot silently invent continuity

- **Chapter 3 notebooks** focus on:
  - evaluation harnesses (repeat runs, perturbations, stress suites)
  - audit bundles for every run
  - stage-gate promotion decisions with traceable rationale

(Notebook names and exact numbering live in **/notebooks/** and are the lab companion to the corresponding book chapter.)

---

## What every notebook enforces (non-negotiable)

Every notebook must be **reviewable by artifact inspection**. At minimum, each run must produce:

- deterministic behavior under seed where applicable
- explicit **state** (TypedDict or equivalent)
- governed retrieval with:
  - query text (or query plan)
  - top-k results + scores
  - inclusion/exclusion reasons
  - retrieval budget usage
- bounded loops (no unbounded retries)
- explicit termination reasons (stop is a feature)
- explicit separation of:
  - **facts_provided** (supported by available inputs/retrieval)
  - **assumptions** (declared and justified)
  - **open_items / open_questions** (what must be verified by humans)
- mandatory exported artifacts, including at minimum:
  - `run_manifest.json` (seed, versions, config hash, environment fingerprint)
  - `retrieval_log.jsonl` (per-step retrieval provenance and ranking)
  - `memory_delta.json` (what was written/updated and why)
  - `final_state.json` (what the system believed at the end)
  - `decision.json` (advance / revise / reject + reasons)
  - `risk_log.json` (risks triggered + controls applied)
  - `artifacts/` directory for any generated deliverables (reports, tables, exhibits)

This is not extra process.  
This is what makes “memory” **auditable**.

---

## How to use this repository

Recommended posture:

1) Read the relevant **chapter** in **/book/** (mechanism + acceptance rules).  
2) Run the corresponding **notebook(s)** in **/notebooks/** as-is (no edits).  
3) Inspect artifacts: retrieval provenance, memory deltas, termination reason, open items.  
4) Stress structurally:
   - add distractor context
   - remove key evidence
   - introduce contradictions
   - tighten retrieval budgets and thresholds
   - increase context length and rerun
5) Record failures as artifacts (don’t hand-wave them away).  
6) Modify **one mechanism at a time**, then re-run and compare artifacts.

Operating rule:  
If the system “works” only when you ignore gates, constraints, termination logic, or evidence rules, then it does not work.

---

## Shared governance spine (applies across this repo)

- **Generation ≠ verification**  
  Outputs are **Not verified** until qualified humans validate them.

- **Facts vs assumptions discipline**  
  Facts provided, assumptions made, and open questions are separated explicitly.

- **Scope and boundary control**  
  Clear stop-if rules, escalation paths, and refusal posture where required.

- **Auditability by design**  
  Artifacts enable reconstruction, supervision, and review.

- **Human accountability**  
  Responsibility never leaves the human professional.

---

## IMPORTANT DISCLAIMERS (read before use)

### Educational / Non-Reliance
All materials are provided **for educational and research purposes only**.  
Nothing in this repository constitutes investment, trading, legal, tax, accounting, audit, or compliance advice.

### Not verified
Unless explicitly stated otherwise in a specific artifact, treat all outputs, claims, calculations, citations, and conclusions as **Not verified**.

### Confidentiality and data hygiene
Do not paste confidential, proprietary, regulated, or personally identifying information into external systems.  
Use anonymization/redaction and **minimum-necessary** inputs by default.

### No fabricated sources or claims
Zero tolerance for invented citations, performance claims, fees, terms, or consequences.  
When evidence is missing, the correct output is a **verification task list**, not persuasive narrative.

---

## License (MIT)

This project is released under the **MIT License**.

**Copyright (c) 2026 Alejandro Reynoso**

---

## Contact

Alejandro Reynoso  
Email: areynoso@yahoo.com  
GitHub: https://github.com/alexdibol
