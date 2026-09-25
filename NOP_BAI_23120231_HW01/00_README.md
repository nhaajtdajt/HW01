# HW01 — Trương Nhật Đạt · 23120231 · CQ2023/31

Môn CS423 / CSC13003 — Software Testing (AI-augmented · 2026)
AI Use Category 4 — AI-Assisted Production · Bloom-AI G9.1, G9.3

## Cấu trúc thư mục

| Thư mục | Nội dung | Yêu cầu tương ứng của đề |
|---|---|---|
| `01_BaoCao_chinh` | Báo cáo chính | Main report PDF, gồm AI Audit summary, AI Critique, Mandatory Disclosure |
| `02_PhuLucA_PromptLog` | Prompt log kèm timestamp | Appendix A |
| `03_Excel` | Test Cases · Checklist · Test Summary Report | Excel bắt buộc của R3 |
| `04_Templates_AI_da_ky` | [AI-02], [AI-03], [AI-05] | 3 template bắt buộc |
| `05_Mindmap` | Mindmap AI vẽ, 3 lỗi tìm được, mindmap đã sửa | QA/QC role mindmap (G9.1) |
| `06_Anh_thiet_bi` | Ảnh quạt + thẻ sinh viên, ảnh tem thông số | Device photo + student ID |
| `07_GitHub_Issues` | Ảnh trang Issues hiện username | Bug screenshots |
| `08_Link_video` | 5 link YouTube Unlisted | ≥5 demo videos |
| `09_Evidence` | 73 ảnh bằng chứng, chia theo từng requirement | Bằng chứng cho R1, R2, R3, mindmap |
| `10_Ban_goc_do_AI_sinh` | Bản chưa sửa do AI sinh ra | Cột (2) của [AI-02] tham chiếu tới các file này |

## Quy đổi đường dẫn

Các đường dẫn trong báo cáo và trong `[AI-02]` viết theo cây thư mục làm việc. Quy đổi sang thư mục nộp bài:

| Đường dẫn trong văn bản | Nằm ở đây |
|---|---|
| `R1_job_market/screenshots/…` | `09_Evidence/R1_tin_tuyen_dung/` |
| `R2_defects/evidence/…` | `09_Evidence/R2_20_su_co/` |
| `R3_device/evidence/…` | `09_Evidence/R3_thiet_bi/` |
| `mindmap/evidence/…` | `09_Evidence/Mindmap/` |
| `prompt_log.md` | `02_PhuLucA_PromptLog/AppendixA_prompt_log.md` |
| `R3_TestCases_Checklist_Summary.xlsx` | `03_Excel/` |
| `R1_report_AI_draft.md`, `R2_report_AI_draft.md`, `mindmap_ai_original.md` | `10_Ban_goc_do_AI_sinh/` |

## Tóm tắt bài làm

- **R1** — 10 tin tuyển dụng QA/QC đăng trong 60 ngày, 5 tin yêu cầu kỹ năng AI, mỗi tin có ảnh chụp hiện tên tài khoản.
- **R2** — 20 sự cố phần mềm 2022–2025, 7 sự cố liên quan AI, và 20 trường hợp AI bịa hoặc thiên lệch khi giải thích chính các sự cố đó, mỗi trường hợp có 2 ảnh đối chứng.
- **R3** — 15 test case cho quạt bàn SENKO, thực thi đủ 15, 12 Pass 2 Fail 1 Inconclusive (TC14), 5 video có giọng nói, 2 defect log thành GitHub Issues. Ba edge case AI không tìm ra: TC10, TC12, TC13.
- **G9.1** — mindmap ISTQB do Gemini vẽ, tìm được 3 lỗi đối chiếu với bản PDF chính thức syllabus CTFL v4.0.

## Khai báo sử dụng AI

Công cụ: Claude (Claude Code CLI, Opus 5) · Gemini Flash-Lite · Gemini Flash Mở rộng.
15 artifact do AI sinh, tất cả đã khai báo trong `[AI-02]`: 0 VALID, 5 INVALID, 10 INCOMPLETE.
Mục 6 của báo cáo chính là phần Mandatory Disclosure đầy đủ.
