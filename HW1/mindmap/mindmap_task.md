# G9.1 — QA/QC + ISTQB mindmap: ask an AI, then find 3 mistakes

The brief mentions this task in three places and never numbers it as a requirement:

| Where | Wording |
|---|---|
| Outcomes | *"Understand: ask an AI Tool for an **ISTQB-process mindmap** and find **3 mistakes**"* |
| CLO mapping, row G9.1 | *"AI Tool draws a **QA/QC role mindmap**; you find **3 mistakes**"* |
| Required submission files | *"**QA/QC role mindmap** (PNG / Markdown)"* |

The two descriptions disagree (process vs roles), so the prompt below asks for both in one mindmap.

---

## Step 1 — Prompt to send (use Gemini Flash-Lite, same tool as R2)

Send it in a **new chat**. Note the time for the prompt log.

```
Draw a mindmap of software QA/QC based on the ISTQB Foundation Level syllabus.
Use a Markdown outline (nested bullets) so it can be rendered as a mindmap.
Cover these branches:
1. QA vs QC vs Testing — how they differ
2. The ISTQB test activities (the test process)
3. Roles in testing according to ISTQB
4. Test levels
5. Test types
6. The ISTQB testing principles
7. Static testing vs dynamic testing
For each branch, list the items exactly as the ISTQB syllabus names them.
```

Then screenshot the answer (`evidence/mindmap_ai_1.png`, `_2.png` …) and paste the Markdown to me.

---

## Step 2 — Ground truth to check it against

ISTQB CTFL **v4.0**. *Verify the clause numbers against the syllabus edition used in your class — v3.1 and the 2011 edition differ, and that difference is itself the most common AI mistake.*

| Branch | What v4.0 actually says | Count |
|---|---|---|
| **Test activities** (§1.4.1) | test planning · test monitoring and control · test analysis · test design · test implementation · test execution · test completion | **7** |
| **Roles in testing** (§1.4.5) | Only **two** principal roles: the **test management role** and the **testing role** | **2** |
| **Test levels** (§2.2.1) | component (unit) testing · component integration testing · system testing · system integration testing · acceptance testing | **5** |
| **Test types** (§2.2.2) | functional · non-functional · black-box · white-box | **4** |
| **Change-related testing** (§2.3) | confirmation testing · regression testing — these are **not** test types and **not** test levels | 2 |
| **Testing principles** (§1.3) | testing shows the presence, not the absence, of defects · exhaustive testing is impossible · early testing saves time and money · defects cluster together · tests wear out · testing is context dependent · absence-of-errors is a fallacy | **7** |
| **Static vs dynamic** (§3) | Static testing = reviews and static analysis, no code executed. Dynamic testing executes the software | — |
| **QA vs QC** (§1.2) | QA is **process**-oriented (does the process produce quality?); QC is **product**-oriented; **testing is a form of quality control** | — |

---

## Step 3 — Where AI mindmaps usually go wrong (check these first)

Do **not** assume these are present. Check each one, then keep the 3 you can actually prove.

| # | Likely mistake | How to prove it |
|---|---|---|
| 1 | **4 test levels instead of 5** — "unit, integration, system, acceptance". v4.0 splits integration into *component integration* and *system integration* | Count the branch; compare with §2.2.1 |
| 2 | **Invented role hierarchy** — "QA Manager, Test Lead, Test Engineer, SDET, Automation Tester" presented as ISTQB roles. ISTQB v4.0 names only two | Compare with §1.4.5 |
| 3 | **Regression / retesting listed as test types** — they belong to change-related testing | Compare with §2.2.2 vs §2.3 |
| 4 | **Old process model** — "planning & control, analysis & design, implementation & execution, evaluating exit criteria, test closure" is the 2011 syllabus, not v4.0 | Compare the 7 activity names |
| 5 | **Wrong principle count or renamed principles** — 6, 8, or invented wording | Count them; check "absence-of-errors is a fallacy" is present |
| 6 | **QA described as "testing"** or QC described as process improvement — the two are swapped | Compare with §1.2 |
| 7 | **Verification/validation swapped** — verification = building it right; validation = building the right thing | Standard definition |

---

## Step 4 — What to write up

For each of the 3 mistakes:

```
### Mistake N
- **AI said:** (quote the branch from the mindmap)
- **ISTQB says:** (quote or cite the syllabus clause)
- **Why it matters:** one sentence
- **Corrected version:** (the fixed branch)
- **Evidence:** evidence/mindmap_ai_N.png
```

## Step 5 — What to submit

| File | Content |
|---|---|
| `mindmap_ai_original.md` (+ screenshots) | The AI's mindmap, unedited — this is the artifact being audited |
| `qa_qc_mindmap_corrected.md` or `.png` | The corrected mindmap — this is the file the brief asks for |
| 3 mistakes write-up | In the main report |
| Prompt log entry | Tool, time, verbatim prompt |
| `[AI-02]` row | One more artifact |

To turn the Markdown into a PNG: paste it into **markmap.js.org/repl**, then export. Or draw it in XMind / draw.io.
