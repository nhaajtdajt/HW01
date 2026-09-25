# R3 — Bug reports (dán vào GitHub Issues)

Đề yêu cầu **≥ 5 defect** từ thiết bị thật, log thành **Issues trong repo GitHub của chính bạn**, kèm ảnh trang Issues hiện username.

`[AI-01] §11` ghi rõ: *"Bug reports: 100% student-written; AI may not draft the description."* Nên bên dưới là **khung và dữ kiện bạn đã quan sát được**, phần mô tả bạn viết lại bằng lời mình.

**Trạng thái:** 3 defect đã xác nhận (DEF-01, 02, 03), còn **2 defect nữa** phải tìm — ứng viên ở cuối file.

---

## DEF-01 — Quạt tắt hẳn khi chuyển cấp gió quá nhanh

**Title:** `[DEF-01] Fan switches off instead of changing speed when buttons are pressed under 0.5s apart`

```
**Test case:** TC10
**Thiết bị:** SENKO quạt bàn, cánh 29cm, 220V/50Hz/40W, Lô SX 107, tháng SX 07-2022 (thiết bị không có số serial riêng)
**Môi trường:** 220V/50Hz, <địa điểm>, <ngày>

**Các bước tái hiện**
1. Cắm điện, quạt ở trạng thái 0
2. Bấm phím 1
3. Bấm phím 2 trong vòng dưới 0,5 giây sau đó

**Kết quả mong đợi**
Quạt chuyển sang cấp 2 và tiếp tục chạy.

**Kết quả thực tế**
Quạt tắt hẳn. Phím 1 nảy lên nhưng phím 2 không khoá được vị trí.

**Tần suất:** <?/5 lần thử>
**Severity:** Medium
**Priority:** Low
**Bằng chứng:** <link YouTube Video 4>
```

**Gợi ý phân tích nguyên nhân** (bạn tự viết): cơ cấu cam của cụm phím cơ cần thời gian để phím cũ nhả hết rồi phím mới mới khoá được. Bấm quá nhanh làm cả hai phím ở trạng thái trung gian và mạch hở.

---

## DEF-02 — Tháo được lồng bảo vệ bằng tay không

**Title:** `[DEF-02] Front guard can be removed by hand without any tool`

```
**Test case:** TC14
**Tiêu chuẩn liên quan:** TCVN 5699-2-80 (tương đương IEC 60335-2-80)

**Các bước tái hiện**
1. Rút phích điện, chờ cánh dừng hẳn
2. Bật các kẹp lồng bằng tay không
3. Tháo lồng trước ra

**Kết quả mong đợi**
Không tháo được lồng bảo vệ nếu không dùng dụng cụ.

**Kết quả thực tế**
Bật được kẹp và tháo rời lồng trước hoàn toàn bằng tay không.

**Severity:** High
**Priority:** High
**Lý do severity:** lồng bảo vệ là rào chắn duy nhất giữa người dùng và cánh quạt đang quay.
Trẻ nhỏ có thể tháo ra khi quạt đang chạy. Quạt thuộc cấp chống giật điện cấp 0, không có tiếp địa bảo vệ.
**Điểm mấu chốt:** tem thiết bị công bố "SP phù hợp: TCVN 5699-2-80:2007 (IEC 60335-2-80:2005)".
Đây là điểm KHÔNG PHÙ HỢP với chính tiêu chuẩn nhà sản xuất tự công bố, không chỉ là bất tiện khi dùng.
**Bằng chứng:** <link YouTube Video 5> + evidence/device_rating_plate_with_id.jpg
```

---

## DEF-03 — Biên độ quét không tự phục hồi sau khi bẻ quá hành trình

**Title:** `[DEF-03] Oscillation sweep range does not recover after the head is forced past its travel limit`

```
**Test case:** TC15

**Các bước tái hiện**
1. Bật số 2, ấn tuốc năng, đánh dấu 2 điểm cuối hành trình quét trên tường
2. Bẻ nhẹ đầu quạt vượt quá điểm cuối khoảng 15 độ rồi thả tay
3. Theo dõi 3 chu kỳ quét tiếp theo

**Kết quả mong đợi**
Quạt quét lại đúng biên độ ban đầu, trùng vạch đánh dấu.

**Kết quả thực tế**
Biên độ quét bị lệch so với vạch ban đầu, không tự phục hồi.

**Severity:** Medium
**Priority:** Medium
**Bằng chứng:** <link YouTube Video 4>
```

**Cần đo bổ sung:** lệch bao nhiêu độ? Lệch về một bên hay cả hai? Có phục hồi sau khi tắt bật lại không? Con số cụ thể làm bug report mạnh hơn nhiều.

---

## Còn thiếu DEF-04 và DEF-05

Chạy 4 test case sau, khả năng cao lòi ra lỗi trên quạt đã dùng lâu:

| Test case | Lỗi hay gặp | Severity dự kiến |
|---|---|---|
| **TC03** cổ quạt | Cổ tự gục xuống khi chạy số 3, khớp gập mòn hết ma sát | Medium |
| **TC09** ba cấp gió | Cấp 2 và cấp 3 cho lưu lượng gần như bằng nhau (tụ yếu) | Medium |
| **TC06** độ ồn | Tiếng lạch cạch theo nhịp từ hộp tuốc năng, hoặc ồn vọt ở cấp 3 | Low–Medium |
| **TC17** rung | Quạt tự dịch chuyển khỏi vạch đánh dấu sau 10 phút | Medium |

**TC03 và TC09 là hai cái đáng thử trước** — nhanh, an toàn, và là hai lỗi phổ biến nhất ở quạt cũ.

---

## Thang severity dùng cho R3

| Mức | Tiêu chí |
|---|---|
| **Critical** | Nguy cơ điện giật, cháy, hoặc chạm được vào cánh đang quay |
| **High** | Rào chắn an toàn mất tác dụng, hoặc thiết bị hỏng chức năng chính |
| **Medium** | Chức năng hoạt động sai hoặc suy giảm, người dùng vẫn dùng được |
| **Low** | Bất tiện, thẩm mỹ, hoặc lệch nhỏ so với thông số |

Thang này bám định nghĩa severity của ISTQB: *mức độ ảnh hưởng của defect lên vận hành của hệ thống*. Dùng đúng một thang cho cả 5 defect để phần Test Summary Report nhất quán.

---

## Checklist khi log lên GitHub

- [ ] Tạo repo (có thể để private, nhưng TA phải xem được — cân nhắc public repo không chứa ảnh có email của bạn)
- [ ] 5 Issue, mỗi issue một defect, title theo mẫu `[DEF-0x] ...`
- [ ] Mỗi issue có: test case ID, bước tái hiện, mong đợi, thực tế, severity, link video
- [ ] Gắn label: `bug`, và label severity
- [ ] Chụp ảnh trang Issues **thấy rõ username GitHub của bạn**
- [ ] Lưu ảnh vào `R3_device/evidence/github_issues.png`
