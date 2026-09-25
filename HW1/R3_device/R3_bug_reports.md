# R3 — Bug reports (dán vào GitHub Issues)

**Thiết bị:** SENKO quạt bàn, cánh 29 cm · 220V/50Hz/40W · Lô SX 107 · tháng SX 07-2022 · cấp chống giật điện cấp 0
**Tiêu chuẩn nhà SX công bố trên tem:** TCVN 5699-2-80:2007 (IEC 60335-2-80:2005)
**Ảnh tem:** `evidence/device_rating_plate_with_id.jpg`

> `[AI-01] §11`: *"Bug reports: 100% student-written; AI may not draft the description."*
> Phần mô tả, nguyên nhân dự đoán và ảnh hưởng người dùng trong ba issue dưới đây **do sinh viên tự viết**. Claude chỉ định dạng lại theo mẫu GitHub Issue và bổ sung các trường cố định (thiết bị, môi trường, thang severity).

**Trạng thái:** 3/5 defect đã xác nhận. Còn **DEF-04 và DEF-05** — ứng viên ở cuối file.

---

## DEF-01 — Quạt tắt hẳn khi bấm hai nút tốc độ liên tiếp quá nhanh

**Title:**
`[DEF-01] Fan switches off completely when two speed buttons are pressed less than 0.5s apart`

**Labels:** `bug` · `severity: medium` · `component: speed-switch`

```markdown
**Test case:** TC10
**Thiết bị:** SENKO quạt bàn 29cm, 220V/50Hz/40W, Lô SX 107, tháng SX 07-2022
(thiết bị không có số serial riêng)
**Môi trường:** 220V/50Hz, <địa điểm>, <ngày kiểm thử>

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

⚠️ Bạn để trống số phím và ngưỡng thời gian trong bản gửi mình. Mình điền theo lần chạy trước của bạn (**phím 1 → phím 2, dưới 0,5 giây**). Kiểm lại đúng chưa trước khi đăng.

---

## DEF-02 — Tháo được lồng bảo vệ bằng tay không

**Title:**
`[DEF-02] Front guard can be removed by hand without any tool — non-conformity with the manufacturer's declared standard`

**Labels:** `bug` · `severity: high` · `component: guard` · `safety`

```markdown
**Test case:** TC14
**Thiết bị:** SENKO quạt bàn 29cm, lồng 96 nan + 1 vòng giữa
**Tiêu chuẩn liên quan:** TCVN 5699-2-80:2007 (IEC 60335-2-80:2005)

## Các bước tái hiện
1. Rút phích điện, chờ cánh dừng hẳn
2. Thử bật các kẹp lồng bằng tay không, không dùng tua vít hay kìm
3. Tháo lồng trước ra

## Kết quả mong đợi
Không tháo được lồng bảo vệ nếu không dùng dụng cụ.

## Kết quả thực tế
Bật được kẹp và tháo rời lồng trước hoàn toàn bằng tay không.

## Vì sao đây là lỗi nghiêm trọng
Tem thiết bị ghi rõ "SP phù hợp: TCVN 5699-2-80:2007 (IEC 60335-2-80:2005)".
Đây là điểm không phù hợp với chính tiêu chuẩn nhà sản xuất tự công bố, không chỉ là
bất tiện khi sử dụng. Lồng bảo vệ là rào chắn duy nhất giữa người dùng và cánh quạt đang
quay, và quạt thuộc cấp chống giật điện cấp 0 nên không có tiếp địa bảo vệ.

## Severity
**High**

## Bằng chứng
Ảnh: evidence/def02_guard_removed_by_hand.jpg — lồng trước đã tháo rời, chỉ dùng tay không
Ảnh tem: evidence/device_rating_plate_with_id.jpg — dòng "SP phu hop: TCVN 5699-2-80:2007"
Test case TC14 trong R3_TestCases_Checklist_Summary.xlsx
```

> Defect nay khong co video: 5 video theo yeu cau cua de la TC01, TC02, TC09, TC10, TC15.
> De chi yeu cau >= 5 video tren tong so test case, khong yeu cau moi defect mot video.

---

## DEF-03 — Hành trình quét đảo gió lệch vĩnh viễn sau khi bị đẩy quá điểm cuối

**Title:**
`[DEF-03] Oscillation sweep range permanently shifts after the head is pushed past its travel limit`

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

## Còn thiếu DEF-04 và DEF-05

Bốn test case chưa chạy, xếp theo khả năng ra lỗi:

| Ưu tiên | Test case | Lỗi hay gặp ở quạt đã dùng 3 năm | Thời gian |
|---|---|---|---|
| **1** | **TC03** — khớp gập cổ quạt | Cổ tự gục xuống khi chạy số 3, khớp mòn hết ma sát | 3 phút |
| **2** | **TC06** — đo độ ồn từng cấp | Tiếng lạch cạch theo nhịp từ hộp tuốc năng, hoặc ồn vọt ở cấp 3 | 5 phút |
| **3** | **TC17** — rung và tự dịch chuyển | Quạt đi khỏi vạch đánh dấu sau 10 phút chạy số 3 | 12 phút |
| **4** | **TC16** — dây nguồn, phích, cơ cấu giữ dây | Vỏ dây chai/nứt, phích lỏng, dây tuột tại điểm vào thân | 3 phút |

**TC03 nên thử trước** — nhanh nhất, và là lỗi phổ biến nhất ở quạt bàn dùng lâu. Quạt của bạn sản xuất 07/2022, đã hơn 3 năm.

**TC16 đáng chú ý riêng:** quạt thuộc **cấp chống giật điện cấp 0**, không có dây tiếp địa. Với loại này, lớp cách điện của dây nguồn là hàng phòng thủ duy nhất. Nếu tìm thấy vết nứt hay chai cứng thì đó là defect **High**, không phải Medium.

---

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

- [ ] Tạo repo, ví dụ `23120231-HW01-fan-testing`
- [ ] 5 Issue, title theo mẫu `[DEF-0x] ...`
- [ ] Gắn label: `bug` + label severity
- [ ] Mỗi issue có link video YouTube tương ứng
- [ ] Chụp ảnh trang Issues **thấy rõ username GitHub**
- [ ] Lưu `evidence/github_issues.png`
- [ ] Dán link repo vào sheet Test Summary Report
