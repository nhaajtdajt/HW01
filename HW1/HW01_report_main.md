# HW01 — QA/QC Jobs · 20 Defects · Testing a Physical Product

| Field | Value |
|---|---|
| **Student** | Trương Nhật Đạt |
| **Student ID** | 23120231 |
| **Class / Cohort** | CQ2023/31 |
| **Course** | CS423 / CSC13003 — Software Testing (AI-augmented · 2026) |
| **Assignment** | HW01 · Individual |
| **AI Use Category** | **Category 4 — AI-Assisted Production** (per `[AI-01]` §4, HW#00–HW#08) |
| **Bloom-AI level** | G9.1 (Understand) · G9.3 (Analyse) |
| **AI tools used** | Claude (Claude Code CLI, Opus 5) · Gemini Flash-Lite |
| **Self-assessed grade** | `___ / 100` (fill before submission) |
| **Submission file** | `23120231_HW01_AI_<grade>.zip` |

---

## How to assemble the PDF

Export in this order into one PDF:

| # | Section | Source file | Status |
|---|---|---|---|
| 1 | Requirement 1 — QA/QC Job Market 2026+ | `R1_job_market/R1_report.md` + `screenshots/` | ✅ Done |
| 2 | Requirement 2 — 20 Software Defects | `R2_defects/R2_report.md` + `evidence/` | ✅ Done |
| 3 | Requirement 3 — Physical product test design | *not started* | ⬜ |
| 4 | QA/QC role mindmap + 3 mistakes found (G9.1) | `mindmap/` | ✅ Done (chat screenshot pending) |
| 5 | AI Audit Report summary | §4 below + `[AI-02]` docx | 🟡 Verdicts drafted - review them |
| 6 | AI Critique (200–300 words) | §5 below | 🟡 Draft written - rewrite in your words |
| 7 | Mandatory Disclosure | §6 below | 🟡 Confirm wording |
| 8 | Self-assessment | §7 below | ⬜ |
| — | Appendix A: prompt log | `prompt_log.md` | ✅ Running |

---

## 4. AI Audit Report — summary

Full working notes: `AI_audit_report_working.md`. Transfer into `template/[AI-02] - FIT@HCMUS - AI Audit Report_En.docx` before submission.

| Artifact | What | Tool | Where the output is |
|---|---|---|---|
| #1 | R1 job-posting write-up (10 JDs + AI Impact Analyses) | Claude | `R1_job_market/R1_report_AI_draft.md` |
| #2 | R2 defect write-up (20 defects) | Claude | `R2_defects/R2_report_AI_draft.md` |
| #3–#6 | Explanations of the 20 defects (4 batch prompts) | Gemini Flash-Lite | `R2_defects/evidence/R2_B*_ai_*.png` |
| #7 | R2 comparison + the 20 hallucination write-ups | Claude | `R2_defects/R2_report.md` §2.3 |

**Accuracy summary (§4 of the template)** — fill after you write your verdicts:

| Metric | Count | % |
|---|---|---|
| Total AI-generated artifacts audited | 7 | 100% |
| VALID (accepted as-is) | ___ | ___% |
| INVALID (rejected) | ___ | ___% |
| INCOMPLETE (accepted after edits) | ___ | ___% |

> Note for the conclusion (§5 of the template): across 20 explanations, Gemini Flash-Lite was reliable on **headline facts** (dates, totals, CVE IDs) and unreliable on **specifics nobody memorises** — vendor names, law-firm names, system names, remediation lists, exact financial figures. All 20 instances fall in the second category.

---

## 5. AI Critique (200-300 words)

> **DRAFT written by Claude at the student's request.** Rewrite this in your own words before submitting - not to disguise its origin, but because a critique you did not write cannot be defended in the oral exam, where you will be asked to "point out 1 mistake the AI made that you corrected".
> If you keep any of this wording, the Mandatory Disclosure below must say the critique was AI-drafted and student-revised. Do not claim it was written entirely by you.

---

Trong HW01 em dùng hai công cụ AI với hai vai trò khác nhau: Claude để soạn bản nháp và đối chiếu nguồn, còn Gemini Flash-Lite để giải thích 20 sự cố rồi em đi tìm chỗ sai trong đó.

Cả 20 giải thích của Gemini đều có ít nhất một chỗ sai kiểm chứng được. Nhưng thứ đáng chú ý với em không phải số lượng, mà là kiểu sai. Những dữ kiện nổi tiếng thì nó nhớ đúng: ngày CrowdStrike gây sập máy, con số 8,5 triệu thiết bị, mã CVE của EchoLeak, mức CVSS 9.3. Chỗ nó bịa lại là các chi tiết không ai thuộc lòng: tên hãng luật "Lebovits" (thật ra là Levidow, Levidow & Oberman), tên nhà cung cấp chatbot "Radiance" (thật ra là Fullpath), tên hệ thống "NERC" (thật ra là FPRSA-R), hay biện pháp khắc phục "historical accuracy parameters" mà Google chưa bao giờ công bố.

Nặng nhất là lúc em hỏi nguồn cho con số "hơn 14 giờ". Nó dẫn tên Rolling Stone, Variety và CNN Business, trong khi Variety viết sự cố giảm dần sau khoảng ba tiếng, còn CNN dẫn lời Ticketmaster nói trang web không sập. Ngược lại, ở một chỗ khác chỉ cần hỏi "nguồn của bạn là gì" là nó tự rút lại: "đây là suy diễn kỹ thuật sai của tôi".

Em cũng thấy AI đi kiểm tra AI vẫn sai. Claude hai lần kết luận Gemini sai rồi phải rút lại, vì nó chỉ tìm bằng chứng ủng hộ kết luận có sẵn chứ không tìm bằng chứng ngược lại.

Thứ giải quyết mọi tranh cãi không phải AI nào cả, mà là tài liệu gốc: báo cáo hậu sự cố của chính công ty, báo cáo cơ quan quản lý, bản án của tòa, hồ sơ CVE. Nguyên tắc em rút ra, nói theo ngôn ngữ kiểm thử: câu trả lời của AI chỉ là giả thuyết, nguồn gốc mới là test oracle, và không được lấy chính hệ thống đang kiểm thử làm oracle cho nó.

*(khoảng 280 từ)*

---

## 6. Mandatory Disclosure — paste verbatim in the final report

> "The R1 job-market write-up, the R2 defect write-up, the comparison tables, **the audit verdicts and the first draft of the AI Critique** were initially generated by **Claude (Claude Code, Opus 5)**; the explanations that were audited for hallucination were generated by **Gemini Flash-Lite**. I reviewed and modified `[section X]`, added `[edge cases Y, Z]`, and rewrote the AI Critique in my own words; **all Requirement 3 artifacts** were produced entirely by me. The detailed AI Audit Report is attached as Appendix A. I confirm I did not use AI to generate any artifact listed in the prohibited category below."

> ⚠️ Keep this wording accurate. If you rewrite the critique completely, change the sentence to say so. If you submit the AI draft as it stands, it must still be declared here - an undeclared AI artifact is what the brief penalises with 0 and a disciplinary referral.

Prohibited-category artifacts in this submission, all produced by me without AI:
- Device photo with my student ID card in the same frame (R3)
- Execution videos with my own voice narration (R3)
- All 10 job-posting screenshots showing my logged-in account (R1)
- Every source screenshot in `R2_defects/evidence/` (R2)
- This prompt log with timestamps

---

## 7. Self-assessment

| No. | Criteria | Max | Self-assessed | Evidence |
|---|---|---|---|---|
| 1 | Job Market 2026+ (10 jobs × 3 pts + AI Impact) | 40 | ___ | `R1_job_market/` |
| 2 | Software Defects 2022–2026 (20 defects) | 20 | ___ | `R2_defects/` |
| 3 | Physical-product test design (15 TCs + 5 videos) | 25 | ___ | *not started* |
| AI-1 | `[AI-02]` AI Audit Report (5-section) attached | 8 | ___ | `AI_audit_report_working.md` |
| AI-2 | AI Critique 200–300 words + `[AI-03]` Disclosure | 4 | ___ | §5, §6 |
| AI-3 | `[AI-05]` Checklist signed + anti-cheat artifacts | 3 | ___ | templates + `evidence/` |
| | **Total** | **100** | ___ | |

> The brief states 40 pts for Requirement 3 in the Description but 25 pts in the rubric table; the rubric sums to 100, so 25 is used here. **Confirm with the TA.**

---

## Remaining work

**R2 — complete.** All 20 defects have a source screenshot and an AI-answer screenshot in `R2_defects/evidence/` (46 files).

**R3 — not started.** Needs the physical device in hand:
1. Choose one household device; note brand, model, year, serial number (mask the middle 4 characters).
2. Photo of the device **with your student ID card in the same frame**.
3. Design 15 test cases (Objective / Input / Steps / Expected / Actual / Verdict) in Excel.
4. Ask an AI for test cases first, then add **≥ 3 edge cases it missed** — keep the screenshot of the AI conversation **plus** a written explanation of why it missed them.
5. Execute **≥ 5** test cases on the real device, record videos **≤ 60s with your own voice**, upload as YouTube Unlisted.
6. Find **≥ 5 defects** and log them as Issues in your own GitHub repo; screenshot the Issues page showing your GitHub username.

**Mindmap (G9.1) — done.** `mindmap/mindmap_ai_original.md` (AI version), `mindmap/mindmap_3_mistakes.md` (the three mistakes against ISTQB v4.0), `mindmap/qa_qc_mindmap_corrected.md` (the corrected mindmap to submit as PNG or Markdown). Still to capture: a screenshot of the Gemini chat, and screenshots of the three syllabus passages.

**Templates to sign:** `[AI-02]`, `[AI-03]`, `[AI-05]` (and `[AI-06]` must already be signed from Week 1).
