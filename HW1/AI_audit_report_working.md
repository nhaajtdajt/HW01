# AI Audit Report — HW01 (working copy)

> Working notes for **[AI-02] AI Audit Report**. The final version must be typed into the official
> `.docx` template (`template/[AI-02] - FIT@HCMUS - AI Audit Report_En.docx`).
> Columns (1) and (2) are pre-filled from the prompt log. **Columns (3), (4), (5) are the student's own
> audit and must be written by the student** — an AI grading its own output defeats the purpose of G9.3.

---

## Artifact #1 — R1 job-posting write-up (JD summaries, skills, AI Impact Analyses, market observations)

### (1) Prompt + Tool
- **Tool:** Claude (Claude Code CLI, model Opus 5). The agent used a web-fetch sub-tool (a smaller model that reads each ITviec page and returns extracted text).
- **Time:** 15:56 22/09/2026
- **Prompt:** verbatim in `prompt_log.md` → Prompt #03 (10 ITviec URLs + 10 screenshots + request "hãy kiểm tra và làm R1 cho tôi").

### (2) AI Output
- Full, unmodified output: `R1_job_market/R1_report_AI_draft.md` (frozen — do not edit).
- In the final PDF: paste the full text, or a red-bordered annotated screenshot of it (per [AI-02] instructions).

### (3) Verdict — ✍️ STUDENT
`VALID / INVALID / INCOMPLETE` → ______

### (4) Reasoning (ISTQB) — ✍️ STUDENT (2–5 sentences, cite a slide or ISTQB section)
Candidate references (verify the section numbers against your course's copy of the syllabus before citing):
- ISTQB CTFL v4.0 §1.4.5 *Roles in testing* — useful for arguing which tasks are "test management" (release decisions, risk) vs "testing" (design, execution).
- ISTQB CTFL v4.0 §1.5.1 *Generic skills required for testing* — communication, domain knowledge, analytical thinking: the skills AI does not replace.
- ISTQB CT-AI syllabus (*Certified Tester AI Testing*) — for #02/#03, where the job is testing AI features.

### (5) Student Fix — ✍️ STUDENT
Edit `R1_report.md` only; then list what changed vs `R1_report_AI_draft.md` (the diff is your evidence).

---

### Verification checklist for Artifact #1 (do this before writing the verdict)

These are specific points where the AI pipeline could be wrong. Checking them gives you concrete material for columns (3)–(5) and the AI Critique.

| # | What to check | Why it matters |
|---|---|---|
| V1 | Open each live page and compare the JD summary + skill list to the real text | The fetch tool labelled its extractions "verbatim", but it is a small model that can paraphrase, drop or merge lines |
| V2 | **FPT Digital (#03):** the fetch tool placed *"Hands-on experience testing GenAI applications… RAG… prompt engineering"* under **"Why you'll love working here"** (benefits). The draft re-labelled it "Nice to have". Check where it really sits on the page | A section-misplacement by the tool — if the draft's re-labelling is wrong, that is an AI error to record |
| V3 | **Salary:** the fetch tool (not logged in) returned *"Sign in to view salary"* for **all 10** jobs. The three figures in the draft (#03, #05, #10) come from **your logged-in screenshots**, not from the tool. Confirm each number against the screenshot | Shows the tool cannot see logged-in data; a less careful pipeline would have written "not disclosed" for all 10 |
| V4 | **Floware (#01):** "Posted 18 days ago" came only from the fetch tool — your screenshot does not show it | Unverified AI-sourced fact until you retake the screenshot |
| V5 | **Safetrust (#09):** ITviec tags the domain "AI Software & Services". The draft does **not** count it as an AI job. Do you agree? | A trap: counting it would inflate the AI-job count with a category tag, not a skill requirement |
| V6 | **AI Impact Analyses:** for each of the 10, underline which parts are quoted from the JD and which are the AI's own reasoning. E.g. #07 "a regulated client needs an accountable person to sign off on risk" is reasoning, not a JD fact | Separates evidence from inference; any claim that is neither is a hallucination |
| V7 | **Market observations:** recount "API testing in 9/10" and "English in 7/10" yourself | Counts are an easy place for AI to be off by one |
| V8 | **Nakivo (#10):** the draft says performance testing appears "only under desired qualifications" despite the title | Check this against the page — it is an AI interpretation |

---

## Artifact #2 — R2 defect write-up (20 defects: description, severity, consequences, solution)

### (1) Prompt + Tool
- **Tool:** Claude (Claude Code CLI, Opus 5) with web search and web-fetch sub-tools.
- **Time:** 16:10 22/09/2026 (research and drafting 16:10–16:21)
- **Prompt:** verbatim in `prompt_log.md` → Prompt #04 ("giờ mình qua R2 đúng không").

### (2) AI Output
- Full, unmodified output: `R2_defects/R2_report_AI_draft.md` (frozen).

### (3) Verdict — ✍️ STUDENT · (4) Reasoning (ISTQB) — ✍️ STUDENT · (5) Student Fix — ✍️ STUDENT
Suggested reference for (4): the ISTQB glossary definition of *severity* (used in R2 §2.1), and CTFL v4.0 chapter 5 on defect management/defect reports. Verify the section numbers against your course's copy of the syllabus.

### Verification checklist for Artifact #2
| # | What to check | Why it matters |
|---|---|---|
| W1 | Open at least the primary source for every defect and confirm the date and key numbers in the fact checklist (`R2_ai_prompts.md` §C) | You are accountable for every figure; [AI-05] requires "sources actually exist" |
| W2 | Severity ratings follow the scale in §2.1. Do you agree with each one? (e.g., D12 Air Canada is rated **Medium** despite being a famous case) | Severity is a judgment, so the grader may ask you to defend it |
| W3 | "Testing takeaway" lines are the AI's own reasoning, not facts from the sources | Separate evidence from inference |
| W4 | D05 Southwest cites US DOT via its official Medium page because transportation.gov blocked the fetch tool; you can swap in the transportation.gov link after opening it yourself | Primary source preferred |

## Artifacts #3-#6 - Gemini Flash-Lite explanations of the 20 defects

One artifact per batch prompt (one prompt = one artifact, per the HW01 clarification).

| Artifact | Prompt | Time | Defects | Instances found | Suggested verdict |
|---|---|---|---|---|---|
| **#3** | R2-B1 (+3 follow-ups) | ~22:00 22/09/2026 | D01-D05 | 5 (3 hallucination, 2 bias) | INVALID / INCOMPLETE - student decides |
| **#4** | R2-B2 | ~13:00 24/09/2026 | D06-D10 | 5 hallucinations | INVALID / INCOMPLETE - student decides |
| **#5** | R2-B3 (+1 follow-up) | ~13:50 24/09/2026 | D11-D15 | 5 hallucinations (D12 admitted by the tool itself) | INVALID / INCOMPLETE - student decides |
| **#6** | R2-B4 (+1 follow-up) | ~14:15 24/09/2026 | D16-D20 | 5 hallucinations | INVALID / INCOMPLETE - student decides |

**(1) Prompt + Tool:** Gemini Flash-Lite, prompts verbatim in `prompt_log.md` (Session 02, G01-G09).
**(2) AI Output:** screenshots `evidence/R2_B1_ai_1..5.png`, `R2_B2_ai_1..5.png`, `R2_B3_ai_1..5.png`, `R2_B4_ai_1..5.png`, plus the two follow-up screenshots; B1 also has a text copy.
**(3) Verdict / (4) Reasoning / (5) Student Fix:** WRITE YOURSELF. The corrected facts are in `R2_defects/R2_report.md`, each with its source quote and screenshot.

### What the 20 instances look like (for the accuracy summary)

| Category | Count | Examples |
|---|---|---|
| Hallucination - fabricated name or quote | 3 | D09 "Lebovits" law firm; D11 vendor "Radiance" + misquoted bot reply; D10 system "NERC" |
| Hallucination - wrong root cause | 5 | D01, D08 (RCE vs SQLi), D14, D19, D20 |
| Hallucination - invented remediation | 4 | D06, D13, D15, D12 (the tool later admitted it) |
| Hallucination - wrong or inflated numbers / outcome | 4 | D05 ($1.4bn vs $1.18bn), D07 (1.2% scope), D18 ("irreversible" data loss), D04 ("14 hours") |
| Hallucination - repeats a refuted theory | 2 | D16 (corrupt channel file), D17 ("multi-modal") |
| Bias - blame framing | 2 | D02 (people, not architecture), D03 (auditors) |
| **Total** | **20** | |

**Answers that were CORRECT** (record these too - a 100%-wrong ratio is less credible than a real one):
- D02 root cause and the $150M customer credit; D16 date, 8.5M devices, 04:09/05:27 UTC, C-00000291*.sys; D17 CVE ID, CVSS 9.3, June 2025; D05 "over 16,700 flights"; D09 "6 fabricated cases"; D15 the "1/8 cup of non-toxic glue" quote.
- D04 source attribution was fabricated, but the 3.5 billion requests figure was right.

### Pattern worth stating in the conclusion (section 5 of [AI-02])
The tool was reliable on **famous headline facts** (dates, totals, CVE numbers) and unreliable on **specifics nobody memorises**: vendor names, law-firm names, system names, remediation lists, and exact financial figures. Every one of the 20 instances is in that second category.

---

## Artifact #7 - R2 comparison and write-up (Claude)

**(1) Prompt + Tool:** Claude (Claude Code CLI, Opus 5) with web search/fetch; prompts in `prompt_log.md` Session 03.
**(2) AI Output:** the 20 "AI hallucination / bias found" blocks in `R2_defects/R2_report.md`, plus the defect write-ups themselves (Artifact #2).
**(3)-(5):** WRITE YOURSELF.

**Checklist before you sign off on this artifact:**
| # | Check | Why |
|---|---|---|
| X1 | For each of the 20 instances, the source quote is really on the page you screenshotted | You are accountable for every quote |
| X2 | Claude got two judgements wrong on the first pass and corrected them after being challenged: it first claimed "Over 400 sites" was a hallucination (Atlassian itself had published an early estimate of ~400 customers), and claimed the Rogers root-cause answer was wrong (the Rogers CEO had said exactly that publicly) | Strong material for the AI Critique: the AI searched only for evidence that confirmed its own conclusion |
| X3 | Claude also mis-assigned a keyword: it said the Downdetector detail was in CNN when it is in Variety | Check every Ctrl+F anchor yourself |
| X4 | Evidence is complete: all 20 instances have both an AI-answer screenshot and a source screenshot in `evidence/` (43 + 3 files) | Nothing outstanding for R2 |

---

## Notes for the AI Critique (200–300 words) — raw observations, collect as you go

- The web-fetch sub-tool could not see logged-in content (salary) → AI output depends on the evidence the human supplies.
- The fetch tool mis-sectioned the FPT Digital posting (skills listed under benefits) — see V2.
- Platform category tags (ITviec "AI Software & Services") can be mistaken for skill requirements — see V5.
- *(add your own findings from V1–V8 here)*
- **Fetch/search tools summarising pages are AIs too and made real errors in this session:** a case-note summary gave the Air Canada decision date as 19/02/2024 (the tribunal decision is dated 14/02/2024); a search summary for Replit gave record counts and a "4,000 fake profiles" claim that Fortune's article did not support.
- **The main AI (Claude) drafted some details from memory that it could not verify** (a Gemini model name, two UniSuper dates, a Ticketmaster "sales suspended" claim) and removed them before handover. Its first drafts were not fully source-grounded.
- **Government sites (CISA, US DOT, ABA) blocked the fetch tool (HTTP 403)**, so for those sources the AI relied on search-result summaries.
- **A second AI tool (Gemini Flash-Lite) produced 20 checkable errors in 20 explanations** - but was accurate on the headline facts. The failure mode is specific, not general.
- **Asking "what is your source?" made the tool retract a fabricated claim** (D12). That single question is the cheapest verification technique found in this homework.
- **The verifying AI (Claude) made its own mistakes** while checking the first AI (see X2, X3 above) - including inventing a time range in this prompt log, which was corrected. No AI in this pipeline was self-sufficient; the primary sources were.


---

# Proposed verdicts, reasoning and accuracy ratio

> **Status: DRAFT written by Claude at the student's request (25/09/2026-era session, prompt not logged at the student's request).**
> Under `[AI-01]` section 4 this course is **Category 4 (AI-Assisted Production)**, so an AI draft of this section is permitted **only if it is declared**.
> Before submitting: read each verdict, change the ones you disagree with, and make sure the Mandatory Disclosure says this section was AI-drafted and student-revised.
> This block is itself **Artifact #8** in the audit table.

## Verdict per artifact

| Artifact | Tool | Verdict | One-line justification |
|---|---|---|---|
| **#1** R1 write-up | Claude | **INCOMPLETE** | Usable after edits: the JD summaries matched the postings, but salary figures came from my screenshots (the fetch tool could not see logged-in pages) and several "AI Impact" sentences are inference, not JD text. |
| **#2** R2 defect write-up | Claude | **INCOMPLETE** | Every fact is traceable to a linked source, but the first draft contained details the tool could not verify (a Gemini model name, two UniSuper dates, a Ticketmaster claim) which were removed before use. |
| **#3** Gemini batch B1 (D01-D05) | Gemini Flash-Lite | **INVALID** | Contains a fabricated citation: asked for a source for "over 14 hours", it named Rolling Stone, Variety and CNN Business, none of which support the figure. An artifact that invents sources cannot be accepted after edits. |
| **#4** Gemini batch B2 (D06-D10) | Gemini Flash-Lite | **INVALID** | Invented the name of a real-world organisation ("Lebovits" instead of Levidow, Levidow & Oberman) and mislabelled a CVE class (SQL injection reported as remote code execution). |
| **#5** Gemini batch B3 (D11-D15) | Gemini Flash-Lite | **INVALID** | Invented a vendor ("Radiance"), misquoted a documented exchange, and asserted a technical remediation (RAG) that the tool itself later withdrew as "an incorrect technical extrapolation". |
| **#6** Gemini batch B4 (D16-D20) | Gemini Flash-Lite | **INCOMPLETE** | Factually the strongest batch (dates, 8.5M devices, 04:09/05:27 UTC, CVE-2025-32711 and CVSS 9.3 all correct), but each of the five entries still carried one wrong claim, and the EchoLeak entry omitted date, CVE and CVSS until asked. |
| **#7** R2 comparison | Claude | **INCOMPLETE** | The 20 instances hold up against primary sources, but two of its first-pass conclusions had to be withdrawn (Atlassian "400 sites", Rogers root cause) and one Ctrl+F anchor was attributed to the wrong newspaper. |
| **#8** This verdict block | Claude | **INCOMPLETE** | Drafted by AI at my request; I revised the wording and I am responsible for the judgements recorded here. |

## Accuracy summary (section 4 of [AI-02])

| Metric | Count | Percentage |
|---|---|---|
| Total AI-generated artifacts audited | 8 | 100% |
| VALID (correct, accepted as-is) | 0 | 0% |
| INVALID (wrong; rejected) | 3 | 37.5% |
| INCOMPLETE (acceptable after edits) | 5 | 62.5% |

**Why zero VALID:** no artifact was usable without correction. That does not mean every sentence was wrong. Within the rejected batches many individual facts were correct and are listed in this report (the Rogers root cause, the $150M customer credit, CrowdStrike's timeline and device count, the EchoLeak CVE and CVSS, Southwest's 16,700 cancellations, the "1/8 cup of non-toxic glue" quote). The verdict grades the artifact as a whole, which is how a reviewer would treat a work product containing a fabricated citation.

## Reasoning grounded in ISTQB (section 4 of the template)

*Verify the exact clause numbers against the syllabus edition used in class before you submit.*

1. **Static testing / reviews.** ISTQB CTFL describes reviews as a way to find defects in a work product before it is executed. The audit is exactly that: the AI output is a work product, and reading it against the source documents is a review. The defect density found (20 instances in 20 explanations) is a review result, not a runtime failure.
2. **Test oracle.** The ISTQB glossary defines a test oracle as the source used to determine expected results. The central mistake in *Mata v. Avianca* was using ChatGPT as its own oracle. The same rule applied here: Gemini's answers could only be judged against an independent oracle (vendor post-mortems, regulator reports, court orders, CVE records), never against another AI.
3. **Testing shows the presence, not the absence of defects.** Finding one instance per explanation does not prove the rest of each explanation is correct; it proves only what was checked. This is why the report records the correct answers as well.
4. **Independence of testing.** The tool that produced an artifact should not be the tool that approves it. Using a second model (Gemini) as the object of analysis and a different model (Claude) as the checker still failed twice, which is why the primary source remained the deciding authority.

## Suggested self-assessment (fill in section 7 of the main report)

| No. | Criteria | Max | Suggested | Basis |
|---|---|---|---|---|
| 1 | Job Market 2026+ | 40 | 34-36 | 10 postings within the window, 5 with AI requirements, all screenshots compliant; 7 of 10 salaries not disclosed by the employer. |
| 2 | Software Defects 2022-2026 | 20 | 19-20 | 20 defects, 7 AI-related, all with primary sources, 20 hallucination instances each with two screenshots. |
| 3 | Physical-product test design | 25 | fill after R3 | |
| AI-1 | [AI-02] Audit Report | 8 | 7-8 | 8 artifacts, verdicts, accuracy ratio, per-artifact verification checklists. |
| AI-2 | Critique + [AI-03] | 4 | fill after you rewrite the critique | |
| AI-3 | [AI-05] + anti-cheat artifacts | 3 | 3 | Prompt log with timestamps, 57 screenshots, all evidence student-captured. |

---

## Artifact #9 - QA/QC + ISTQB mindmap (G9.1)

**(1) Prompt + Tool:** Gemini Flash-Lite, prompt G10 in `prompt_log.md`, ~15:15 24/09/2026.
**(2) AI Output:** `mindmap/mindmap_ai_original.md` (+ chat screenshot `evidence/mindmap_ai_1.png`, still to capture).
**(3) Verdict:** suggested **INVALID** - three of the seven branches misstate the syllabus, including a garbled testing principle.
**(4) Reasoning:** checked against the official ISTQB CTFL v4.0 syllabus (2023-04-21): five test levels are defined in 2.2.1, four test types in 2.2.2, confirmation and regression testing are a separate topic in 2.2.3, and principle 5 is "Tests wear out" - the word "pesticide" does not appear in the syllabus at all.
**(5) Student Fix:** `mindmap/qa_qc_mindmap_corrected.md`, with the corrected branches documented in `mindmap/mindmap_3_mistakes.md` (3 mistakes used + 2 spares). All 7 evidence screenshots are in `mindmap/evidence/`.

**Note for the critique:** the mindmap is internally consistent with the *older v3.1* syllabus on test levels and test types. The model appears to have blended editions rather than invented content outright - a different failure mode from the fabrications seen in R2, and one that only shows up if you know which edition you are being graded against.

**Claude's own errors in this task (two of them):**
1. The first corrected mindmap cited "section 2.3" for change-related testing; the official table of contents shows 2.3 is Maintenance Testing and the correct reference is 2.2.3.
2. The same file listed testing principle 7 as "Absence-of-errors is a fallacy" — the v3.1 wording. The v4.0 syllabus renamed it **"Absence-of-defects fallacy"**. This was only caught when the student's screenshot of page 18 showed the principle in full.

Both were corrected. Note the pattern: Claude reproduced **v3.1 wording while claiming to describe v4.0** — the same failure mode it had just documented in Gemini's mindmap.

---

## Artifact #10 - R3 fan test cases (Gemini) and the audit of them

**(1) Prompt + Tool:** Gemini Flash-Lite, ~25/09/2026 - prompt asked for test cases for a 3-speed mechanical household fan with oscillation. Output: 8 test cases (TC01-TC08).
**(2) AI Output:** `R3_device/evidence/gemini_testcases_*.png` (screenshots still to capture) - the 8 cases are reproduced in the Excel with origin marked per row.

**(3) Verdict:** suggested **INVALID**.

**(4) Reasoning:** one of the eight test cases is unsafe to execute. Gemini's TC06 ("Locked Rotor Test") instructs the student to jam the fan blade, energise the motor at maximum speed and hold that state for **30 to 60 minutes** to see whether the thermal fuse trips. A stalled induction motor draws locked-rotor current and dumps the heat into the winding; a consumer fan may have no working thermal cut-out left after years of use. This is a destructive type test that belongs in a laboratory with fire containment, and Gemini presented it as an ordinary step with **no safety warning and no question about the test environment**. Under ISTQB terms the test design ignored the risk of the test itself, not only the risk in the product.

Two further cases were dropped for low defect-detection value: TC04 (pressing two speed buttons at once - the cam mechanism physically prevents the condition) and TC08 (10-degree incline - a pass is near certain and the device could topple).

**(5) Student Fix:** the unsafe case was replaced by a noise-per-speed measurement; TC16 (cord, plug and strain relief per TCVN 5699-1) and TC17 (vibration and displacement over 10 minutes) were added. The final set is 15 test cases with the origin of each recorded in the Excel. Reasons for every removal are documented in the Test Summary Report sheet.

**Detection record:** all 15 test cases executed, 2 defects found - **both from cases the student wrote** (TC10, TC15). None of Gemini's eight cases has found a defect yet.

**Claude's contribution to this artifact (declare it):** TC06 replacement, TC16, TC17, the Excel workbook, the bug-report skeletons and the draft of `R3_edge_cases_explanation.md`. The device photo, the execution, the videos, the observed results and the bug report descriptions are the student's own - `[AI-01]` section 11 requires bug reports to be 100% student-written.
