# R3 — Kế hoạch quay 5 video

Yêu cầu của đề: **≥ 5 video**, mỗi video **≤ 60 giây**, **có giọng nói của chính bạn**, upload **YouTube Unlisted**.

⚠️ Video có giọng nói nằm trong danh sách **cấm dùng AI** của đề. Không dùng giọng AI, không dùng phụ đề thay lời nói. Bị phát hiện là **0 điểm toàn bài + hội đồng kỷ luật**.

---

## Chọn 5 video nào

Ưu tiên test case **có lỗi** — vì khi có lỗi thì bạn có cái để nói, và video chứng minh được defect.

| Video | Test case | Thời lượng | Vì sao chọn |
|---|---|---|---|
| **1** | TC01 — ba cấp gió + tắt | ~45s | Video mở đầu, giới thiệu thiết bị |
| **2** | TC02 — đảo gió bật/tắt | ~40s | Dễ quay, thấy rõ chuyển động |
| **3** | TC09 + TC17 — so sánh lưu lượng 3 cấp và độ rung | ~60s | Gộp 2 test, dễ lòi defect |
| **4** | TC10 + TC15 — **2 defect đã xác nhận** | ~60s | Quan trọng nhất, chứng minh DEF-01 và DEF-03 |
| **5** | TC14 — **tháo lồng bằng tay không** | ~35s | Defect nặng nhất, DEF-02 |

Nếu còn sức thì quay thêm **Video 6** cho TC13 (khe nan) hoặc TC16 (dây nguồn) để dự phòng.

---

## Bố cục mỗi video

Nói theo ý, đừng đọc thuộc lòng — TA nghe ra ngay.

```
[0-8s]   Mình là <họ tên>, MSSV <số>. Video này chạy test case <ID> trên quạt <hãng model>.
[8-15s]  Mục tiêu của test này là gì, kết quả mong đợi là gì.
[15-50s] Thao tác thật, vừa làm vừa nói mình đang làm gì và đang thấy gì.
[50-60s] Kết luận: Pass hay Fail. Nếu Fail thì nói rõ lệch so với mong đợi ở chỗ nào.
```

**Ví dụ cho Video 4 (test case có lỗi):**
- *"Test case TC10, kiểm tra chuyển cấp gió nhanh. Mong đợi là quạt phải chuyển sang cấp 2 chứ không được tắt."*
- *(bấm 1, rồi bấm 2 thật nhanh)* — *"Bấm 1, bấm 2 luôn… quạt tắt hẳn rồi, phím 2 không ăn."*
- *"Mình lặp lại lần nữa cho chắc."* *(bấm lại)*
- *"Verdict Fail. Đây là DEF-01."*

---

## Mẹo quay

- **Quay dọc hay ngang đều được**, nhưng ngang dễ thấy toàn cảnh quạt hơn.
- **Kiểm tra âm thanh trước**: quạt chạy số 3 rất ồn, bạn phải nói to hơn hoặc đứng gần mic. Quay thử 10 giây rồi nghe lại.
- **Cho thấy thao tác tay** trong khung hình — TA cần thấy bạn thật sự bấm nút, không phải dựng cảnh.
- **Đúng 60 giây là giới hạn cứng.** Quay xong kiểm tra thời lượng, dài quá thì cắt bớt đoạn im lặng.
- **Quay một lần liền mạch**, đừng cắt ghép nhiều đoạn — video liền mạch đáng tin hơn.

---

## Upload YouTube

1. youtube.com → Create → Upload video
2. Visibility chọn **Unlisted** (không phải Private — Private thì TA không mở được)
3. Tiêu đề: `HW01 - 23120231 - TC10, TC15 - Fan speed switching and oscillation recovery`
4. Copy link, dán vào cột Video của file Excel và vào bug report tương ứng

Chỉ dùng Google Drive hoặc OneDrive khi YouTube gỡ video vì bản quyền — và phải chứng minh đã thử upload YouTube trước.

---

## Trước khi quay: chụp ảnh thiết bị

Việc này làm được ngay, không cần chờ gì:

- **1 ảnh: quạt và thẻ sinh viên trong cùng một khung hình**, cả hai đều đọc được
- Chụp thêm ảnh **tem thông số** ở lưng hoặc đế quạt để lấy hãng, model, năm, serial
- Trong báo cáo, **che 4 ký tự giữa của serial** (ví dụ `AB12****7890`)
- Lưu: `R3_device/evidence/device_with_id.jpg` và `device_rating_plate.jpg`

Ảnh này cũng nằm trong danh sách cấm dùng AI.
