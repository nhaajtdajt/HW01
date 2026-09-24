# Appendix A — Prompt Log (HW01)

| Field | Value |
|---|---|
| Course | CS423 / CSC13003 – Software Testing (AI-augmented · 2026) |
| Assignment | HW01 – QA/QC Jobs · 20 Defects · Test a Physical Product |
| AI Use Category | **Category 4 – AI-Assisted Production** |
| Bloom-AI level | G9.1 (Understand) · G9.3 (Analyse) |
| Student name | Trương Nhật Đạt |
| Student ID | 23120231 |
| Class / Cohort | CQ2023/31 |
| AI tool(s) used | Claude (Anthropic) — Claude Code CLI, model Opus 5 |
| Log started | 15:07 22/09/2026 (UTC+07:00) |

**Rule:** every prompt sent to any AI tool is logged here verbatim, with timestamp `HH:MM dd/mm/yyyy`.
Do **not** paraphrase prompts. Do **not** delete entries, even for failed or discarded attempts.

---

## Session 01 — 22/09/2026 · Tool: Claude (Claude Code CLI, Opus 5)

> ⚠️ Timestamps for #01 and #02 were reconstructed from file-system modification times
> because the log was started at 15:07. **Sinh viên cần xác nhận / sửa lại cho đúng.**

### Prompt #01 — ~14:28 22/09/2026
**Tool:** Claude (Claude Code CLI, Opus 5)
**Prompt (verbatim, VI):**
```
tôi đang có lớp học về testing bạn hãy đọc đề trong bài phân tích và nói cho tôi nó yêu cầu gì đi
```
**Purpose:** Understand the HW01 brief.
**AI action:** Read `2026.HW01.Jobs.Defects.PhysicalProduct_En.md`; produced a structured summary of R1/R2/R3, the AI Collaboration Protocol, anti-cheat list, and submission rules.
**Artifact produced:** Summary only — not submitted as an artifact.
**Audit entry:** Not required (comprehension aid, no artifact in the report).
**Student verification:** Re-read the original brief; confirmed the summary. AI additionally flagged two real inconsistencies I verified myself:
1. R3 is worth **40 pts** in the Description but **25 pts** in the rubric table (rubric sums to 100 → 25 is the operative figure). → Cần hỏi lại GV/TA.
2. The **QA/QC role mindmap (G9.1)** appears only in the CLO-mapping table and the submission file list, not as a numbered requirement — easy to miss but mandatory.

### Prompt #02 — ~15:02 22/09/2026
**Tool:** Claude (Claude Code CLI, Opus 5)
**Prompt (verbatim, VI):**
```
tôi vừa thêm các template được cung cấp vào rồi đó nếu có yêu cầu bài cần đến nó thì bạn hãy dùng nhé và bật prompt log lên đi. Tôi sẽ làm R1 trước bạn hãy hướng dẫn tôi làm đúng với yêu cầu đi tôi đã vào trang linked in và tìm được các job QA/QC đăng gần đây rồi
```
**Purpose:** Start the prompt log; get R1 guidance.
**AI action:** Extracted text from `[AI-01]`, `[AI-02]`, `[AI-03]`, `[AI-05]` templates; created this log + `R1_job_market/R1_worksheet.md`; gave R1 procedure guidance.
**Artifact produced:** This prompt-log scaffold + R1 worksheet (both are *containers I fill in myself*, not graded content).
**Audit entry:** Not required yet — no graded content generated. An entry becomes required the moment AI drafts any AI Impact Analysis text.
**Student verification:** Cross-checked the extracted category definition against `[AI-01] AI Agreement §4` → HW#00–HW#08 = Category 4. Confirmed.

---

---

## Session 02 - Gemini Flash-Lite (R2: explanations of the 20 defects)

Tool: **Gemini Flash-Lite** (gemini.google.com). Purpose: obtain AI explanations of the 20 defects so that one hallucination/bias instance per defect could be identified against primary sources. Times marked `~` are approximate (reconstructed from screenshot clocks); times without `~` were confirmed by the student.

### G01 - ~22:00 22/09/2026
**Tool:** Gemini Flash-Lite
**Purpose:** R2-B1 - defects D01-D05
**Prompt (verbatim):**
```
I am studying software testing. Answer from your own knowledge, without searching the web.
For EACH of the following software incidents, give:
(1) the exact date, (2) the organisation and system involved, (3) the technical root cause,
(4) the scale of impact with numbers, (5) the financial or legal consequences,
(6) who was responsible, (7) how it was fixed and what prevention was added,
(8) a severity rating (Critical / High / Medium / Low) with a one-line justification.

1. The Atlassian cloud outage (April 2022)
2. The Rogers Communications network outage in Canada (July 2022)
3. The Nomad bridge hack (August 2022)
4. The Ticketmaster failure during the Taylor Swift Eras Tour presale (November 2022)
5. The Southwest Airlines holiday meltdown (December 2022)
```
**Result:** Answer text: evidence/R2_B1_ai_answer_as_pasted.txt; screenshots: evidence/R2_B1_ai_1..5.png

### G02 - 09:30 24/09/2026
**Tool:** Gemini Flash-Lite
**Purpose:** Follow-up, D02 Rogers
**Prompt (verbatim):**
```
For the Rogers outage: exactly what configuration change was made, and on which type of routers?
```
**Result:** Answer was CORRECT (routing filter removed on distribution routers). Recorded as a VALID answer.

### G03 - 09:30 24/09/2026
**Tool:** Gemini Flash-Lite
**Purpose:** Follow-up, D04 Ticketmaster
**Prompt (verbatim):**
```
What is your source for 'outages lasting more than 14 hours' in the Ticketmaster case?
```
**Result:** Answer attributed the figure to Rolling Stone, Variety and CNN Business - none of which support it. Used as the D04 instance.

### G04 - 09:30 24/09/2026
**Tool:** Gemini Flash-Lite
**Purpose:** Follow-up, D03 Nomad
**Prompt (verbatim):**
```
Which firm audited Nomad, and was the buggy code part of the audited code?
```
**Result:** Answer said the code was introduced 'after the audit period had concluded' (sources say after the audit had BEGUN) and contradicted its own earlier answer.

### G05 - ~13:00 24/09/2026
**Tool:** Gemini Flash-Lite
**Purpose:** R2-B2 - defects D06-D10
**Prompt (verbatim):**
```
I am studying software testing. Answer from your own knowledge, without searching the web.
For EACH of the following software incidents, give:
(1) the exact date, (2) the organisation and system involved, (3) the technical root cause,
(4) the scale of impact with numbers, (5) the financial or legal consequences,
(6) who was responsible, (7) how it was fixed and what prevention was added,
(8) a severity rating (Critical / High / Medium / Low) with a one-line justification.

1. The FAA NOTAM system outage in the United States (January 2023)
2. The ChatGPT incident where users could see other users' data (March 2023)
3. The MOVEit Transfer vulnerability exploited by the CL0P gang (2023)
4. The Mata v. Avianca case where lawyers used ChatGPT (2023)
5. The UK NATS air traffic control failure (August 2023)
```
**Result:** Screenshots: evidence/R2_B2_ai_1..5.png

### G06 - ~13:50 24/09/2026
**Tool:** Gemini Flash-Lite
**Purpose:** R2-B3 - defects D11-D15
**Prompt (verbatim):**
```
I am studying software testing. Answer from your own knowledge, without searching the web.
For EACH of the following software incidents, give:
(1) the exact date, (2) the organisation and system involved, (3) the technical root cause,
(4) the scale of impact with numbers, (5) the financial or legal consequences,
(6) who was responsible, (7) how it was fixed and what prevention was added,
(8) a severity rating (Critical / High / Medium / Low) with a one-line justification.

1. The Chevrolet dealership chatbot that agreed to sell a car for $1 (2023)
2. The Air Canada chatbot bereavement fare case (2024)
3. The Google Gemini image generation controversy (February 2024)
4. The Google Cloud deletion of UniSuper's account (May 2024)
5. The Google AI Overviews "glue on pizza" answers (May 2024)
```
**Result:** Screenshots: evidence/R2_B3_ai_1..5.png

### G07 - ~13:54 24/09/2026
**Tool:** Gemini Flash-Lite
**Purpose:** Follow-up, D12 Air Canada
**Prompt (verbatim):**
```
What is your source that Air Canada implemented RAG after the ruling?
```
**Result:** Gemini withdrew its own claim ('an incorrect technical extrapolation on my part'). Screenshot: evidence/R2_D12_ai_admission.png

### G08 - ~14:15 24/09/2026
**Tool:** Gemini Flash-Lite
**Purpose:** R2-B4 - defects D16-D20
**Prompt (verbatim):**
```
I am studying software testing. Answer from your own knowledge, without searching the web.
For EACH of the following software incidents, give:
(1) the exact date, (2) the organisation and system involved, (3) the technical root cause,
(4) the scale of impact with numbers, (5) the financial or legal consequences,
(6) who was responsible, (7) how it was fixed and what prevention was added,
(8) a severity rating (Critical / High / Medium / Low) with a one-line justification.

1. The CrowdStrike Falcon update that crashed Windows computers (July 2024)
2. The EchoLeak vulnerability in Microsoft 365 Copilot (2025)
3. The Replit AI agent that deleted a production database (2025)
4. The AWS us-east-1 outage (October 2025)
5. The Cloudflare global outage (November 2025)
```
**Result:** Screenshots: evidence/R2_B4_ai_1..5.png

### G09 - ~14:22 24/09/2026
**Tool:** Gemini Flash-Lite
**Purpose:** Follow-up, D16 CrowdStrike + D17 EchoLeak
**Prompt (verbatim):**
```
At what exact UTC time was the faulty channel file released, and when was it reverted?
What is the CVE ID and CVSS score of EchoLeak, and when was it published?
```
**Result:** Both answers were CORRECT (04:09 / 05:27 UTC; CVE-2025-32711, 9.3, June 2025). Screenshot: evidence/R2_D16_D17_ai_followup.png


### G10 - ~15:15 24/09/2026 *(confirm the exact time)*
**Tool:** Gemini Flash-Lite
**Purpose:** G9.1 - have an AI draw a QA/QC + ISTQB mindmap so that three mistakes can be found in it
**Prompt (verbatim):**
```
Draw a mindmap of software QA/QC based on the ISTQB Foundation Level syllabus.
Use a Markdown outline (nested bullets) so it can be rendered as a mindmap.
Cover these branches:
1. QA vs QC vs Testing - how they differ
2. The ISTQB test activities (the test process)
3. Roles in testing according to ISTQB
4. Test levels
5. Test types
6. The ISTQB testing principles
7. Static testing vs dynamic testing
For each branch, list the items exactly as the ISTQB syllabus names them.
```
**Result:** `mindmap/mindmap_ai_original.md`. Three mistakes identified against the official v4.0 syllabus PDF: four test levels instead of five, black-box testing missing from the test types (with change-related testing wrongly listed as a type), and testing principle 5 garbled into "Pesticide paradox is destructive". Write-up: `mindmap/mindmap_3_mistakes.md`.

---

## Session 03 - Claude (Claude Code CLI, Opus 5): verification and drafting, 22-24/09/2026

Claude was used to cross-check every Gemini answer against primary sources and to draft the report text. Timestamps marked `~` are approximate. Full answers from Claude are not reproduced here; the artifacts they produced are listed in the AI Audit Report.

| # | Time | Prompt (verbatim, Vietnamese without diacritics where transcribed) |
|---|---|---|
| #06 | ~21:39 22/09/2026 | day la cau tra loi ban check lai thu no co tra loi dung khong ... (pasted Gemini B1 answer for D01-D05) |
| #07 | ~21:50 22/09/2026 | can xac thuc lai voi toi truoc khi lam |
| #08 | ~09:00 23/09/2026 | day la cau tra loi cua AI do (pasted Gemini follow-up answers for D02, D03, D04) |
| #09 | ~09:20 23/09/2026 | kiem tra that ki lai 5 loi do co chinh xac khong cho toi ... hay check ki lai roi noi phan anh nguon |
| #10 | ~09:00 24/09/2026 | cac duong link ban dua ra toi tim khong co tu khoa do hay tim lai cac bai va tu khoa cua bai do |
| #11 | ~09:15 24/09/2026 | (5 source screenshots: Atlassian, CRTC, Zellic, Yahoo, Ticketmaster) |
| #12 | ~09:40 24/09/2026 | (4 source screenshots: CRTC measures, Variety, Southwest Q4, Southwest Q1) |
| #13 | ~09:41 24/09/2026 | (1 source screenshot: CNN Business) |
| #14 | ~11:00 24/09/2026 | ban dung ki luong qua moi cai 1 anh minh chung la du roi nhe |
| #15 | ~12:20 24/09/2026 | gemini flash-lite gio gui la 9:30 ngay hom nay |
| #16 | ~12:25 24/09/2026 | day la anh tra loi cua gemini nhe gio toi se qua batch tiep (5 chat screenshots) |
| #17 | ~13:05 24/09/2026 | day la cac loi tu gemini tra ve (pasted B2 answers) |
| #18 | ~13:10 24/09/2026 | (10 screenshots: 5 sources + 5 chat, batch B2) |
| #19 | ~13:55 24/09/2026 | (pasted B3 answers) |
| #20 | ~14:00 24/09/2026 | (10 screenshots: 4 sources + D12 admission + 5 chat, batch B3) |
| #21 | ~14:25 24/09/2026 | (pasted B4 answers) |
| #22 | ~14:26 24/09/2026 | (1 screenshot: D16/D17 follow-up answers) |
| #23 | ~14:30 24/09/2026 | vay tim cho toi 2 loi khac di 2 cau nay AI da tra loi dung roi |
| #24 | ~14:40 24/09/2026 | vay la xong bai 2 roi dung khong (7 screenshots: CrowdStrike, NVD, 5 chat B4) |
| #25 | ~14:50 24/09/2026 | ban lam cho minh 5 viec do luon di |

## Prompt template — copy this block for every new prompt

```
### Prompt #NN — HH:MM dd/mm/yyyy
**Tool:**
**Prompt (verbatim):**
​```
<paste exactly what you sent — no edits>
​```
**Purpose:**
**AI output summary:** (full output goes in the AI Audit Report, §3 col 2)
**Artifact produced:**
**Audit entry:** Artifact #N in [AI-02] / not required
**Student verification:**
```

### Prompt #03 — 15:56 22/09/2026
**Tool:** Claude (Claude Code CLI, Opus 5)
**Prompt (verbatim, VI) + 10 attached screenshots (1.png … 10.png):**
```
1. https://itviec.com/it-jobs/senior-automation-test-ai-qa-qc-api-floware-1219Job description



2 https://itviec.com/it-jobs/hanoi-fullstack-qa-engineer-lead-manual-auto-ai-money-forward-vietnam-co-ltd-4636


3 https://itviec.com/it-jobs/middle-qa-automation-engineer-playwright-selenium-fpt-digital-4422



4 https://itviec.com/it-jobs/qa-engineer-automation-mobile-app-pytest-moatable-0149


5. https://itviec.com/it-jobs/qa-engineer-tester-qa-qc-english-up-to-1500-saritasa-4856
6. https://itviec.com/it-jobs/manual-qc-engineer-middle-saigon-technology-5140
7.https://itviec.com/it-jobs/qa-engineer-manual-automation-tester-dxc-vietnam-1007
8.https://itviec.com/it-jobs/manual-tester-qa-qc-good-english-netcompany-2659
9.https://itviec.com/it-jobs/lead-qa-qc-engineer-test-design-iot-product-safetrust-4626
10.https://itviec.com/it-jobs/performance-qa-engineer-nakivo-2956
tôi tìm được 10 công ty và cung cấp ảnh cho bạn như vậy đó bạn hãy kiểm tra và làm R1 cho tôi đi nếu thiếu thông tin gì cần tôi bổ sung hãy hỏi tôi nhé
```
**Purpose:** Verify the 10 screenshots against R1 constraints; draft R1 content.
**Note:** Screenshots were captured by the student 15:47–15:54 22/09/2026 (taskbar clock). They are student-made evidence, NOT AI-generated; AI only copied/renamed them, no pixel edits.
**AI action:** Checked each screenshot for (a) account name, (b) posting date, (c) capture date, (d) salary. Fetched the 10 live ITviec pages via a web-fetch sub-tool (15:56-16:00) to extract JD text, skills and AI mentions. Copied the 10 screenshots unmodified into `R1_job_market/screenshots/` with descriptive names (md5 verified identical). Drafted the full R1 write-up.
**Artifact produced:** **Artifact #1** — `R1_job_market/R1_report.md` (JD summaries, required skills, 10 AI Impact Analyses, market observations). Frozen copy of the unmodified AI output: `R1_job_market/R1_report_AI_draft.md`.
**Audit entry:** **Artifact #1** in [AI-02] — working notes in `AI_audit_report_working.md`.
**Issues flagged by AI for the student:** screenshot #01 does not show the posting date (retake needed); 7/10 postings do not disclose salary.
**Student verification:** _(to be completed by the student — see checklist V1-V8 in AI_audit_report_working.md)_

### Prompt #04 — 16:10 22/09/2026
**Tool:** Claude (Claude Code CLI, Opus 5)
**Prompt (verbatim, VI) + 1 attached screenshot (11.png):**
```
đây là ảnh bổ sung, vẫn giữ các lương ẩn đó. Mình là Trương Nhật Đạt, MSSV 23120231 khóa Kiểm thử phần mềm - CQ2023/31
giờ mình qua R2 đúng không
```
**Purpose:** Provide the Job #01 retake; confirm salary decision; provide identity; start R2.
**Student decision (R1):** Keep the 7 undisclosed salaries as "Not disclosed" rather than replacing postings.
**AI action (R1):** New screenshot saved unmodified as `R1_job01_Floware_22-09-2026_B_posted-date.png`; original renamed `..._A_account.png`. Job #01 date filled in both `R1_report.md` and the frozen draft (rev 2) — factual update from student evidence, not a student fix. Identity fields filled in this log and the audit working file.
**AI finding (R1):** Screenshot B shows the posting date but NOT the account name (dropdown closed). Job #01 is now evidenced by a pair of screenshots (A + B).
**AI action (R2):** Selected 20 widely reported defects (Apr 2022 – Nov 2025; 7 AI/LLM-related) and verified each against primary or reputable sources with web search/fetch (16:10–16:21). Drafted `R2_defects/R2_report.md` (description, severity, consequences, solution per defect) and `R2_defects/R2_ai_prompts.md` (4 batch prompts for a *different* AI tool + verified fact checklist). Removed details the AI could not verify in-session before handover (e.g., a model name for Gemini images, two UniSuper dates).
**Artifact produced:** **Artifact #2** — `R2_report.md`; frozen copy `R2_report_AI_draft.md`.
**Audit entry:** Artifact #2 in `AI_audit_report_working.md`.

### Prompt #05 — 16:21 22/09/2026
**Tool:** Claude (Claude Code CLI, Opus 5)
**Prompt (verbatim, VI):**
```
giờ bạn trước tiên hãy tìm 20 lỗi mà có nhiều bài báo nói về nó và viết hơi quá lố lên rồi tôi sẽ dùng 1 con AI khác để hỏi và so nó lại với bạn nhé.
```
**Purpose:** Student asked for 20 widely reported defects written in an exaggerated way, to compare against another AI.
**AI response:** The 20 defects already selected are widely reported, and the compare-with-another-AI procedure was already prepared. The AI declined to write deliberately exaggerated content *as a source of "AI hallucination" findings*: planted errors are not genuine AI hallucinations, and reporting them as such would be a false AI disclosure. Offered a transparent alternative (disclosed fault seeding to test the second AI's fact-checking).
