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
| AI tool(s) used | Claude (Anthropic) — Claude Code CLI, model Opus 5<br>Gemini (Google) — Flash-Lite: R2 và mindmap<br>Gemini (Google) — Flash Mở rộng: test case R3 |
| Log started | 15:07 22/09/2026 (UTC+07:00) |

**Quy tắc:** mọi prompt gửi cho AI được ghi nguyên văn, kèm timestamp `HH:MM dd/mm/yyyy`. Không diễn đạt lại. Không xoá entry, kể cả prompt thất bại hoặc bị bỏ.

**Cách xác định timestamp — đọc trước khi đối chiếu.**
Các mốc giờ trong log này có ba mức độ tin cậy khác nhau, và ký hiệu phân biệt rõ:

| Ký hiệu | Nghĩa | Cách kiểm chứng |
|---|---|---|
| `HH:MM` (không dấu ~) | Giờ sinh viên xác nhận trực tiếp, hoặc đọc được trên đồng hồ trong ảnh chụp màn hình | Mở ảnh tương ứng, xem góc dưới bên phải |
| `~HH:MM` | Giờ suy ra, neo theo mốc gần nhất có ảnh chứng và sắp theo đúng thứ tự prompt trong phiên | Sai số khoảng ±20 phút; **thứ tự trước sau là chính xác** |

Giao diện Claude Code CLI không hiển thị đồng hồ trong transcript, nên toàn bộ mốc giờ của Session 03 thuộc loại suy ra. Log này ghi rõ điều đó thay vì trình bày chúng như giờ quan sát được.

**Vì sao đồng hồ trong ảnh chụp muộn hơn giờ gửi prompt.** Các ảnh chụp cuộc trò chuyện với Gemini được chụp lại **sau khi** đã nhận câu trả lời, trong lúc thu thập bằng chứng. Ví dụ `R2_B1_ai_1.png` có đồng hồ 12:24 ngày 24/09 nhưng prompt G01 được gửi tối 22/09 — ảnh là ảnh chụp lại cuộc trò chuyện cũ, không phải ảnh chụp tại thời điểm gửi. Cuộc trò chuyện Gemini giữ nguyên URL nên chụp lại được bất cứ lúc nào.

---

## Session 01 — 22/09/2026 · Tool: Claude (Claude Code CLI, Opus 5)

> Mốc giờ của #01 và #02 suy ra từ thời gian sửa file trên ổ đĩa, vì log chỉ được lập lúc 15:07 cùng ngày.

### Prompt #01 — ~14:28 22/09/2026
**Tool:** Claude (Claude Code CLI, Opus 5)
**Prompt (verbatim, VI):**
```
tôi đang có lớp học về testing bạn hãy đọc đề trong bài phân tích và nói cho tôi nó yêu cầu gì đi
```
**Purpose:** Understand the HW01 brief.
**AI output summary:** AI tóm tắt các yêu cầu R1/R2/R3 và nội quy.
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
**AI output summary:** AI trích xuất nội dung từ các template và tạo worksheet R1.
**Artifact produced:** R1 worksheet (a container I fill in myself, not graded content).
**Audit entry:** Not required yet — no graded content generated. An entry becomes required the moment AI drafts any AI Impact Analysis text.
**Student verification:** Cross-checked the extracted category definition against `[AI-01] AI Agreement §4` → HW#00–HW#08 = Category 4. Confirmed.

---

---

## Session 02 — Gemini (R2: giải thích 20 sự cố · G9.1: mindmap · R3: test case quạt)

G01–G09 và G10 dùng **Gemini Flash-Lite**; G11 dùng **Gemini Flash Mở rộng** — model hiển thị ở góc dưới khung chat trong `R3_device/evidence/gemini_testcases_1.png`. Mục đích: lấy câu trả lời của AI để đối chiếu với tài liệu gốc và xác định một instance hallucination hoặc bias cho mỗi sự cố.

### G01 — ~21:30 22/09/2026
> Giờ suy ra từ một ràng buộc cứng: câu trả lời của G01 đã được dán sang Claude ở prompt #06, nên G01 phải xảy ra trước #06.
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


### G10 — ~15:25 24/09/2026
> Giờ suy ra: file `mindmap/ISTQB_CTFL_Syllabus_v4.0.pdf` được tải về lúc 15:41 để đối chiếu câu trả lời, nên prompt phải gửi trước mốc đó. Đồng hồ trong ảnh `mindmap/evidence/mindmap_ai_1.png` đọc được 15:42 — ảnh chụp lại sau khi đã nhận câu trả lời.
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

### G11 — 14:18 25/09/2026
> Đồng hồ trong ảnh `R3_device/evidence/gemini_testcases_1.png` đọc được 14:18 ngày 25/09/2026.
**Tool:** Gemini **Flash Mở rộng** (kèm 2 ảnh chụp cái quạt làm đầu vào)
**Purpose:** R3 - de AI sinh test case cho quat, lam co so xac dinh 3 edge case AI bo sot
**Prompt (verbatim):**
```
tạo test case cho tôi với Objective, Input, Steps, Expected result.
Cover normal operation and edge cases
```
**Result:** 8 test case TC01-TC08. Luu tai `R3_device/mindmap_ai_original`-tuong duong: noi dung goc nam trong `R3_device/evidence/gemini_testcases_1..6.png`.
Ba test case TC10, TC12, TC13 KHONG co trong danh sach nay - day la bang chung cho yeu cau "3 edge case AI khong tim ra".
TC06 goc (Locked Rotor Test: chen cung canh quat, cap dien 30-60 phut) da bi loai vi khong an toan.
**Ghi chu:** Gemini nhin thay ca 2 anh cai quat nhung khong sinh ra test case nao dua tren tieu chuan in tren tem thiet bi.

---

## Session 03 — Claude (Claude Code CLI, Opus 5): đối chiếu nguồn và soạn nháp, 22–24/09/2026

Claude được dùng để đối chiếu từng câu trả lời của Gemini với tài liệu gốc và để soạn nháp phần chữ của báo cáo.
Toàn bộ mốc giờ dưới đây là **giờ suy ra** (xem bảng ký hiệu ở đầu log): neo theo các mốc Gemini có ảnh chứng, thứ tự trước sau là chính xác.
Câu trả lời đầy đủ của Claude không chép lại ở đây; các artifact mà chúng tạo ra được liệt kê trong `[AI-02]`.

| # | Giờ | Prompt (nguyên văn, tiếng Việt) |
|---|---|---|
| #06 | ~21:39 22/09/2026 | "đây là câu trả lời bản check lại thử nó có trả lời đúng không nếu có thì tôi phải vào link bài báo để chụp chỗ trả lời sai đúng không nếu không tìm ra lỗi thì tôi sẽ thử với AI khác" *(kèm câu trả lời B1 của Gemini cho D01–D05)* |
| #07 | ~21:50 22/09/2026 | "cần xác thực lại với tôi trước khi làm" |
| #08 | ~09:40 24/09/2026 | "đây là câu trả lời của AI đó" *(kèm câu trả lời follow-up của Gemini cho D02, D03, D04 — tức G02, G03, G04 lúc 09:30 cùng ngày)* |
| #09 | ~09:50 24/09/2026 | "kiểm tra thật kĩ lại 5 lỗi đó có chính xác không cho tôi, tôi sợ bạn đọc nhớ context đề mà dựa theo đó mà đưa ra quyết định không chính xác hãy check kĩ lại rồi nói phần ảnh nguồn để xác thực lại thì phải chụp 5 ảnh với dòng xác thực lại ở 5 bài báo chứ đúng không" |
| #10 | ~10:00 24/09/2026 | "nhưng các trang bạn đưa cho tôi ở trên có phải là trang chính thống uy tín không vậy nếu nó cũng là 1 trang báo thì sao lại so sánh được" |
| #11 | ~10:15 24/09/2026 | "bạn kiểm tra lại có đúng không nếu đúng phân tích và nói bước tiếp theo tôi cần làm đi" *(kèm 5 ảnh nguồn)* |
| #12 | ~10:40 24/09/2026 | "các đường link bạn đưa ra tôi tìm không có từ khóa đó hãy tìm lại các bài và từ khóa của bài đó ( từ giờ hãy nói gọn cách làm lại thôi )" |
| #13 | ~11:00 24/09/2026 | "ảnh đây bạn thêm vào giúp tôi nhé" *(kèm ảnh nguồn)* |
| #14 | ~11:20 24/09/2026 | "bạn đừng kĩ lưỡng quá mỗi cái 1 ảnh mình chứng là đủ rồi nhé" |
| #15 | 12:20 24/09/2026 | "gemini flash-lite giờ gửi là 9:30 ngày hôm nay" *(sinh viên xác nhận giờ gửi G02–G04)* |
| #16 | ~12:25 24/09/2026 | "đây là ảnh trả lời của gemni nhé giờ tôi sẽ qua batch tiếp" *(kèm 5 ảnh chat)* |
| #17 | ~13:05 24/09/2026 | "đây là các lỗi từ gemini trả về … hãy kiểm tra lại giúp tôi đi" *(kèm câu trả lời B2)* |
| #18 | ~13:10 24/09/2026 | *(10 ảnh: 5 ảnh nguồn + 5 ảnh chat, batch B2)* |
| #19 | ~13:55 24/09/2026 | "đây bạn kiểm tra và thực hiện phần này cho tôi đi" *(kèm câu trả lời B3)* |
| #20 | ~14:00 24/09/2026 | *(10 ảnh: 4 ảnh nguồn + ảnh Gemini tự rút lại khẳng định D12 + 5 ảnh chat, batch B3)* |
| #21 | ~14:25 24/09/2026 | *(kèm câu trả lời B4)* |
| #22 | ~14:26 24/09/2026 | *(1 ảnh: câu trả lời follow-up D16/D17)* |
| #23 | ~14:30 24/09/2026 | "vậy tìm cho tôi 2 lỗi khác đi 2 câu này AI đã trả lời đúng rồi" |
| #24 | ~14:40 24/09/2026 | "vậy là xong bài 2 rồi đúng không" *(kèm 7 ảnh: CrowdStrike, NVD, 5 ảnh chat B4)* |
| #25 | ~14:50 24/09/2026 | "bạn làm cho mình 5 việc đó luôn đi" |

---

## Session 04 — Claude (Claude Code CLI, Opus 5): mindmap G9.1, 24/09/2026 chiều

Neo thời gian của phiên này: `mindmap/mindmap_task.md` tạo lúc 15:20, `ISTQB_CTFL_Syllabus_v4.0.pdf` tải lúc 15:41, 7 ảnh trong `mindmap/evidence/` lưu lúc 15:46 — đều đọc được bằng thuộc tính file.

| # | Giờ | Prompt (nguyên văn) |
|---|---|---|
| #26 | ~15:05 24/09/2026 | "nói lại cho tôi yêu cầu mindmap và R3 trong bài yêu cầu đi" |
| #27 | ~15:15 24/09/2026 | "vậy hãy làm mindmap cho tôi đi" |
| #28 | ~15:38 24/09/2026 | "đây bạn kiểm tra và thực hiện phần này cho tôi đi" *(kèm mindmap Gemini vừa sinh ở G10)* |
| #29 | ~15:43 24/09/2026 | "4 ảnh đó ở đâu vậy nói lại cho tôi link đi" |
| #30 | ~15:46 24/09/2026 | "ảnh đây bạn thêm vào giúp tôi nhé" *(kèm 4 ảnh trang syllabus)* |

**Kết quả phiên:** `mindmap/mindmap_3_mistakes.md` (3 lỗi dùng chính thức + 2 dự phòng, mỗi lỗi kèm trích dẫn nguyên văn và số trang) và `mindmap/qa_qc_mindmap_corrected.md`. Khai báo là Artifact #9, #11, #12 trong `[AI-02]`.

---

## Session 05 — Claude (Claude Code CLI, Opus 5): R3 và hoàn thiện bài, 25/09/2026

Neo thời gian: 6 ảnh `gemini_testcases_*.png` lưu lúc 14:22 · `device_full_with_id.jpg` lúc 19:13 · `github_issues.png` lúc 19:35 · thư mục `templates_filled/` lúc 19:55 · thư mục nộp bài dựng lúc 21:55.

| # | Giờ | Prompt (nguyên văn) |
|---|---|---|
| #31 | ~13:30 25/09/2026 | "tôi chọn cái quạt giờ hãy hướng dẫn tôi làm để đạt yêu cầu R3 đi" |
| #32 | ~14:22 25/09/2026 | "hãy kiểm tra lại giúp tôi đi" *(kèm 8 test case Gemini vừa sinh ở G11, và 7 test case TC09–TC15 do em tự viết)* |
| #33 | ~14:50 25/09/2026 | "vậy bạn hãy bổ sung 2 lỗi khác vào cho tôi cho đủ 15 lỗi đi" |
| #33b| ~14:55 25/09/2026 | "ý tôi là bạn hãy bổ sung 2 case khác vào đi" |
| #34 | ~15:00 25/09/2026 | "giờ tôi sẽ quay 5 video và nếu video nào tìm ra lỗi tôi sẽ nói bạn và bạn tạo log Github issues cho tôi nhé" |
| #35 | ~18:40 25/09/2026 | "bạn hãy làm cho tôi đi" *(kèm kết quả em tự ghi sau khi quay video: TC01, TC02, TC09 Pass; TC10, TC15 Fail)* |
| #36 | ~19:05 25/09/2026 | "Giữ nguyên, không tụt, Đọc rõ hết, không nhòe, không bong, Chỉ có tiếng gió, không lạch cạch, cấp 3 ồn nhất, Không thấy tia lửa, chạy lại ngay, Dây lành, phích chắc, không xê dịch, Đồng xu còn nguyên, không lệch" |
| #37 | ~19:13 25/09/2026 | "DEF-02 cái này tôi không quay yt không cần gắn link được không" *(kèm ảnh cái quạt và thẻ sinh viên cùng khung hình)* |
| #38 | ~19:25 25/09/2026 | "cho tôi đoạn 3 issue đó để tôi dán nó vào đi" *(kèm 5 link YouTube)* |
| #39 | ~19:28 25/09/2026 | "https://github.com/nhaajtdajt/HW01---Issue.git tôi vừa tạo repo xong bạn switch qua này rồi đẩy lên cho tôi đi" |
| #40 | ~19:33 25/09/2026 | "rồi tôi đã tạo 3 issue trên repo hiện tại này rồi giờ tôi cần làm gì tiếp theo" |
| #41 | ~19:35 25/09/2026 | "2 có yêu cầu làm không, 3 tôi đang viết, 4 tôi đang làm hãy làm phần 5 cho tôi đi" *(kèm ảnh trang GitHub Issues)* |
| #42 | ~19:45 25/09/2026 | "bạn coi lại thử còn chỗ này mình chưa làm không" |
| #43 | ~19:52 25/09/2026 | "prompt gemini là tạo test case cho tôi với Objective, Input, Steps, Expected result. Cover normal operation and edge cases — điền và ký [AI-02], [AI-03], [AI-05] cho tôi AI-06 không cần" |
| #44 | ~21:50 25/09/2026 | "tôi đã dán ảnh ký vào các file docx đó rồi đó tạo ra cấu trúc thu mục cho tôi để tôi nộp bài đi đừng zip lại" |
| #45 | ~22:00 25/09/2026 | "\"5. AI Critique\" bằng bản bạn viết lại là sao" |
| #45b| ~22:02 25/09/2026 | "bạn hãy viết đoạn văn 200-300 từ bạn tự viết, phê bình con AI nhận xét bản thân tốt và chưa tốt điểm nào cho tôi" |
| #46 | ~22:05 25/09/2026 | "vậy bạn xóa các dòng gây hiểu lầm đó đi" |
| #47 | ~22:10 25/09/2026 | "tôi phát hiện ra các case ai bỏ sót là 9 10 và 12 hãy ghi vào đi" |
| #48 | ~22:15 25/09/2026 | "vậy thay bằng TC13 đi" |
| #49 | ~22:20 25/09/2026 | "tôi bị nhận xét như này do 1 số cái tôi đã làm nhưng bạn lại bị ngộ nhận và còn để lại các dòng như AI đã làm hoặc là quên xóa hãy làm lại cho tôi." *(kèm bản nhận xét phản biện toàn bài)* |
| #50 | ~22:45 25/09/2026 | "giờ bỏ lỗi DEF-02 đi và tôi đã sủa 03 thành 02 rồi và các file dox trong template tôi có kí rồi mà phục hồi prompt log lại cho tôi prompt nào có dòng nhắc không đặt vào log thì khỏi cần bỏ vào" |

### Thay đổi sau phiên

Ở thời điểm prompt #38 và #40 em đang có **3 defect** và đã tạo 3 issue. Sau khi rà lại, defect "lồng bảo vệ tháo được bằng tay" (TC14) có Expected Result viện dẫn TCVN 5699-2-80 nhưng không tra được nguyên văn điều khoản, nên không có test oracle để phán quyết. Issue tương ứng trên Github (#2) bị xóa thay vì đóng, do đó số lượng issue nhảy từ #1 sang #3.

### Hai lần Claude từ chối trong phiên này

- **#43** — Em nhờ Claude ký thay vào ba template. Claude từ chối, chỉ điền nội dung và để trống ô Signature để em tự ký. Chữ ký là artifact thuộc nhóm cấm dùng AI theo `[AI-01] §11`.
- **#49** — Bản nhận xét chỉ ra các chỗ khai báo AI mâu thuẫn nhau. Claude sửa bằng cách khai **đủ hơn** (tăng từ 10 lên 15 artifact trong `[AI-02]`), không phải bằng cách khai bớt đi.

---

## Phạm vi của log này — khai báo trung thực

Log ghi **11 prompt gửi Gemini** (G01–G11) và **50 prompt gửi Claude** (#01–#50), từ 22/09/2026 đến 25/09/2026.


Toàn bộ 15 artifact do AI sinh ra đều có mặt trong `[AI-02]` kèm prompt nguyên văn ở cột (1), verdict và phần sinh viên sửa.

---

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
**AI output summary:** AI kiểm tra 10 ảnh chụp màn hình và viết bản nháp cho R1_report.md.
**Artifact produced:** **Artifact #1** — `R1_job_market/R1_report.md` (JD summaries, required skills, 10 AI Impact Analyses, market observations). Frozen copy of the unmodified AI output: `R1_job_market/R1_report_AI_draft.md`.
**Audit entry:** **Artifact #1** in [AI-02] — working notes in `AI_audit_report_working.md`.
**Issues flagged by AI for the student:** screenshot #01 does not show the posting date (retake needed); 7/10 postings do not disclose salary.
**Student verification:** Đã kiểm tra theo checklist V1-V8 trong AI_audit_report_working.md

### Prompt #04 — 16:10 22/09/2026
**Tool:** Claude (Claude Code CLI, Opus 5)
**Prompt (verbatim, VI) + 1 attached screenshot (11.png):**
```
đây là ảnh bổ sung, vẫn giữ các lương ẩn đó. Mình là Trương Nhật Đạt, MSSV 23120231 khóa Kiểm thử phần mềm - CQ2023/31
giờ mình qua R2 đúng không
```
**Purpose:** Provide the Job #01 retake; confirm salary decision; provide identity; start R2.
**Student decision (R1):** Keep the 7 undisclosed salaries as "Not disclosed" rather than replacing postings.
**AI output summary (R1):** AI cập nhật lại thông tin ngày tháng cho Job #01.
**AI finding (R1):** Screenshot B shows the posting date but NOT the account name (dropdown closed). Job #01 is now evidenced by a pair of screenshots (A + B).
**AI output summary (R2):** AI chọn ra 20 lỗi và viết bản nháp cho R2_report.md.
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
