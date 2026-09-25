# R3 — Bug reports (dán vào GitHub Issues)

**Thiết bị:** SENKO quạt bàn, cánh 29 cm · 220V/50Hz/40W · Lô SX 107 · tháng SX 07-2022 · cấp chống giật điện cấp 0
**Tiêu chuẩn nhà SX công bố trên tem:** TCVN 5699-2-80:2007 (IEC 60335-2-80:2005)
**Ảnh tem:** `evidence/device_rating_plate_with_id.jpg`

> `[AI-01] §11`: *"Bug reports: 100% student-written; AI may not draft the description."*
> Phần mô tả lỗi, các bước tái hiện, kết quả thực tế, nguyên nhân dự đoán và ảnh hưởng người dùng trong ba issue dưới đây **do sinh viên tự viết sau khi trực tiếp thực thi test case**. Claude không soạn nội dung mô tả; phần Claude làm là khung trình bày của mẫu Issue và các trường cố định lặp lại ở cả ba issue (thông số thiết bị, môi trường, thang severity) — đã khai trong `[AI-03]` mục 4.

**Trạng thái:** 2 defect đã xác nhận trên tổng số 15 test case đã thực thi. Cả hai đã được log thành GitHub Issue tại `github.com/nhaajtdajt/HW01/issues`.

---

## DEF-01 — Quạt tắt hẳn khi bấm hai nút tốc độ liên tiếp quá nhanh

**Title:**
`[DEF-01] Fan switches off completely when two speed buttons are pressed less than 0.5s apart`

**Labels:** `bug` · `severity: medium` · `component: speed-switch`

```markdown
**Test case:** TC10
**Thiết bị:** SENKO quạt bàn 29cm, 220V/50Hz/40W, Lô SX 107, tháng SX 07-2022
(thiết bị không có số serial riêng)
**Môi trường:** 220V/50Hz, Nhà riêng, TP.HCM, 25/09/2026

## Các bước tái hiện
1. Cắm điện, bấm phím số 1, xác nhận quạt đang chạy
2. Bấm ngay phím số 2 kế tiếp, khoảng cách giữa hai lần bấm dưới 0,5 giây

## Kết quả mong đợi
Quạt nhận phím bấm sau cùng và chuyển sang cấp tốc độ tương ứng.

## Kết quả thực tế
Quạt không nhận cấp tốc độ nào. Cả hai phím đều nảy lên vị trí ngắt, động cơ mất điện
và dừng hẳn. Phải bấm lại một lần nữa quạt mới chạy.

## Số lần lặp
3/3 lần đều tái hiện được.

## Ngưỡng quan sát được
Bấm cách nhau khoảng 0,5 giây trở lên thì chuyển cấp bình thường; bấm nhanh hơn thì quạt tắt.

## Nguyên nhân dự đoán
Cơ cấu cam khóa của cụm công tắc cần một khoảng thời gian để nhả phím cũ rồi mới khóa được
phím mới. Bấm quá nhanh khiến phím mới chưa kịp vào khớp khóa, toàn cụm trở về vị trí ngắt.

## Ảnh hưởng người dùng
Chuyển tốc độ là thao tác thường xuyên nhất trên quạt. Người dùng bấm nhanh sẽ bị tắt quạt
ngoài ý muốn, tưởng quạt hỏng.

## Severity
**Medium** — không mất an toàn, nhưng ảnh hưởng thao tác cơ bản nhất của sản phẩm.

## Bằng chứng
Video: https://youtube.com/shorts/HPpBDBBYLWI
```


---

## DEF-02 — Hành trình quét đảo gió lệch vĩnh viễn sau khi bị đẩy quá điểm cuối

**Title:**
`[DEF-02] Oscillation sweep range permanently shifts after the head is pushed past its travel limit`

**Labels:** `bug` · `severity: medium` · `component: oscillation-gearbox`

```markdown
**Test case:** TC15
**Thiết bị:** SENKO quạt bàn 29cm

## Các bước tái hiện
1. Bật quạt số 1, ấn chốt tuốc năng cho quạt bắt đầu quét
2. Để quạt quét ổn định 2 chu kỳ, xác định 2 điểm cuối hành trình làm mốc
3. Khi đầu quạt đang quét, dùng tay đẩy mạnh đầu quạt sang phải vượt quá điểm cuối hành trình
4. Thả tay, để quạt quét tiếp 2 chu kỳ và so với 2 mốc ban đầu

## Kết quả mong đợi
Sau khi thả tay, quạt quay lại đúng hành trình quét ban đầu.

## Kết quả thực tế
Cánh vẫn quay bình thường, nhưng hành trình quét bị dịch hẳn sang một bên. Hai điểm cuối
không còn trùng với mốc ban đầu. Quạt không tự phục hồi về hành trình cũ dù chạy tiếp,
phải tắt và chỉnh lại bằng tay.

## Số lần lặp
2/2 lần đều tái hiện được.

## Nguyên nhân dự đoán
Bộ nhông truyền động tuốc năng bị trượt răng khi chịu lực ngang vượt ngưỡng, làm mất vị trí
tham chiếu của hành trình quét.

## Ảnh hưởng người dùng
Xảy ra dễ dàng trong sinh hoạt — chỉ cần vô ý đụng vào quạt khi đi ngang, hoặc chỉnh hướng
gió bằng tay mà quên kéo chốt lên. Hậu quả: quạt thổi lệch khỏi vùng mong muốn.

## Severity
**Medium** — không mất an toàn, nhưng xảy ra trong thao tác thường ngày và không tự khắc
phục được.

## Bằng chứng
Video: https://youtube.com/shorts/Dtg48KkCVdo
```

---

## Vì sao chỉ có 2 defect

Toàn bộ 15 test case đã được thực thi: 13 Pass, 2 Fail. Hai defect trên tổng số 15 test case là kết quả hợp lý với một thiết bị đang hoạt động tốt — quạt vận hành đúng các chức năng cơ bản, dây nguồn và nhãn còn nguyên vẹn, lồng bảo vệ giữ chặt khi chạy, khe nan lồng đạt yêu cầu chống chạm cánh.

Cả hai defect đều nằm ở cụm cơ khí chuyển động: cụm công tắc tốc độ và hộp nhông đảo gió. Điều này phù hợp với nguyên tắc ISTQB *"defects cluster together"*.

Một quan sát bị loại khỏi danh sách defect: lồng bảo vệ trước tháo được bằng tay khi đã rút điện. Expected Result ban đầu của TC14 viện dẫn TCVN 5699-2-80, nhưng không tra được nguyên văn điều khoản (tiêu chuẩn không công bố miễn phí) nên không có test oracle để phán quyết, và lồng trước tháo tay là kết cấu phổ biến ở quạt bàn để vệ sinh cánh. Quan sát vẫn được ghi trong cột Actual Result của TC14, nhưng không nâng thành defect.

Đề đặt mục tiêu ≥ 5 defect (*"aim to find"*). Kết quả thực tế là 2, và báo cáo ghi đúng con số đó thay vì hạ tiêu chí Pass để tăng số lượng.

## Thang severity dùng cho R3

| Mức | Tiêu chí |
|---|---|
| **Critical** | Nguy cơ điện giật, cháy, hoặc chạm được vào cánh đang quay |
| **High** | Rào chắn an toàn mất tác dụng, hoặc không phù hợp tiêu chuẩn nhà SX công bố |
| **Medium** | Chức năng hoạt động sai hoặc suy giảm, người dùng vẫn dùng được |
| **Low** | Bất tiện, thẩm mỹ, hoặc lệch nhỏ so với thông số |

Bám định nghĩa severity của ISTQB: *mức độ ảnh hưởng của defect lên vận hành của hệ thống*.

---

## Checklist khi log lên GitHub

- [x] Tạo repo: `github.com/nhaajtdajt/HW01`
- [x] 2 Issue, title theo mẫu `[DEF-0x] ...`
- [x] Gắn label: `bug` + label severity
- [x] Cả hai issue đều có link video YouTube
- [x] Chụp ảnh trang Issues **thấy rõ username GitHub**
- [x] Lưu `evidence/github_issues.png`
- [x] Dán link repo vào sheet Test Summary Report
