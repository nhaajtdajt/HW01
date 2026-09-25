# R3 — Ba edge case AI không tìm ra, và vì sao nó bỏ sót

> **Bản nháp do Claude soạn theo yêu cầu của sinh viên.** Viết lại bằng lời của bạn trước khi nộp — buổi vấn đáp sẽ hỏi *"vì sao bạn chọn input X mà không phải Y"*, và phần này chính là câu trả lời.
> Nếu giữ nguyên câu chữ ở đây thì phải khai trong `[AI-02]` và trong Mandatory Disclosure.

## Bằng chứng bắt buộc

Đề yêu cầu **cả hai**:
- **(a)** Ảnh chat Gemini cho thấy nó **không** sinh ra 3 test case này → chụp **toàn bộ** danh sách 8 test case Gemini đã đưa, lưu `evidence/gemini_testcases_1.png`, `_2.png`…
- **(b)** Giải thích bằng chữ vì sao nó bỏ sót → phần dưới

---

## Gemini đã sinh ra những gì

8 test case: TC01 ba cấp gió · TC02 đảo gió · TC03 khớp gập cổ · TC04 nhấn đồng thời 2 phím · TC05 chặn hành trình quét · TC06 kẹt cứng cánh quạt · TC07 mất điện đột ngột · TC08 đặt nghiêng 10 độ.

Nhìn kỹ thì cả 8 đều xuất phát từ **một nguồn duy nhất: danh sách chức năng của cái quạt**. Có phím tốc độ thì test phím tốc độ. Có tuốc năng thì test tuốc năng. Có khớp gập thì test khớp gập. Bốn case gọi là "edge case" (TC04–TC08) thực ra vẫn là chức năng đó nhưng đẩy đến cực trị: chặn nó lại, ngắt điện nó, đặt nghiêng nó.

Ba test case dưới đây không sinh ra được bằng cách đó.

---

## Edge case 1 — TC13: Khe hở nan lồng bảo vệ

**Vì sao Gemini bỏ sót:** case này không đến từ chức năng nào của quạt cả. Thổi gió không liên quan gì đến khoảng cách giữa hai nan lồng. Nó đến từ **tiêu chuẩn an toàn TCVN 5699-2-80**, quy định vật thăm dò tiêu chuẩn không được chạm tới cánh đang quay.

Muốn nghĩ ra case này thì phải biết là có một bộ tiêu chuẩn quốc gia dành riêng cho quạt điện, và phải đi tra nó. Prompt của mình chỉ mô tả cái quạt và các chức năng của nó, không nhắc gì tới tiêu chuẩn, nên Gemini không có lý do gì để đi theo hướng đó.

**Chi tiết mình ghi rõ trong Excel:** mình dùng ngón út để **xấp xỉ** que thử tiêu chuẩn (test probe B, khớp nối, đường kính 12mm). Đây không phải phép thử hợp chuẩn, và mình ghi đúng như vậy chứ không nói là đã kiểm tra hợp chuẩn.

---

## Edge case 2 — TC14: Tháo lồng bảo vệ bằng tay không

**Vì sao Gemini bỏ sót:** cùng lý do với TC13, nhưng còn một tầng nữa. Đây là test một yêu cầu **phủ định**: lồng bảo vệ **không được** tháo ra nếu không có dụng cụ.

Gemini sinh test case theo kiểu "chức năng này phải làm được gì". Không có chức năng nào tên là "không tháo được lồng". Nó là một ràng buộc an toàn, và ràng buộc thì không nằm trong danh sách chức năng.

**Đây cũng là defect nặng nhất mình tìm được (DEF-02):** lồng bật ra bằng tay không, mà lồng là rào chắn duy nhất giữa người dùng và cánh quạt đang quay.

---

## Edge case 3 — TC10: Bấm chuyển cấp gió cách nhau dưới 0,5 giây

**Vì sao Gemini bỏ sót:** so sánh với TC01 và TC04 của chính nó thì thấy rõ.

- TC01 của Gemini: bấm 1, **chờ 5 giây**, bấm 2, **chờ 5 giây**, bấm 3. Đây là test trạng thái tĩnh, mỗi trạng thái được ổn định trước khi chuyển.
- TC04 của Gemini: bấm 1 và 3 **đồng thời**. Đây là test hai đầu vào cùng lúc.
- TC10 của mình: bấm 1 rồi bấm 2 **cách nhau dưới 0,5 giây**. Đây là test **chuyển trạng thái có ràng buộc thời gian**.

Gemini tư duy theo trạng thái đứng yên, không theo khoảng thời gian giữa hai trạng thái. Nó không hình dung được thao tác tay thật của một người đang chỉnh quạt — người ta bấm liên tiếp chứ không bấm rồi đếm 5 giây.

**Và đây là chỗ lòi ra defect DEF-01:** quạt tắt hẳn thay vì chuyển cấp.

---

## Điểm chung của ba case

Gemini sinh test case từ **những gì thiết bị làm được**. Ba case này đến từ hai nguồn khác:

1. **Tiêu chuẩn an toàn** (TC13, TC14) — cái mà chỉ người biết ngành mới nghĩ tới đi tra
2. **Cách người dùng thật sự thao tác** (TC10) — thời gian, nhịp tay, thói quen

Liên hệ với ISTQB: Gemini dừng ở **functional testing** dựa trên đặc tả chức năng. Ba case của mình thuộc nhóm dựa trên **rủi ro** và **trải nghiệm** — loại test case mà người kiểm thử phải mang kiến thức bên ngoài đặc tả vào mới nghĩ ra được.

Và đáng chú ý: **hai trong ba case này tìm ra lỗi thật**, còn cả 8 case của Gemini thì chưa case nào tìm ra lỗi.

---

---

## Phát hiện quan trọng từ tem thiết bị

Ảnh tem quạt (`evidence/device_rating_plate_with_id.jpg`) ghi rõ:

> **SP phù hợp: TCVN 5699-2-80:2007 (IEC 60335-2-80:2005)**
> **Lồng quạt 96 nan - 1 vòng giữa**
> **Cấp chống giật điện: cấp 0**

Ba dòng này làm thay đổi trọng lượng của hai edge case mình tự nghĩ ra:

1. **Chính nhà sản xuất công bố tuân thủ TCVN 5699-2-80** — đúng tiêu chuẩn mình dùng làm cơ sở cho TC13 và TC14. Nghĩa là hai test case đó không phải mình áp tiêu chuẩn ngoài vào, mà là **kiểm tra đúng tiêu chuẩn nhà sản xuất tự cam kết**.

2. **Vì vậy DEF-02 (tháo được lồng bảo vệ bằng tay không) là một điểm không phù hợp với chính công bố của nhà sản xuất**, chứ không chỉ là bất tiện. Mức severity High là có căn cứ.

3. **Quạt thuộc cấp chống giật điện cấp 0**, tức không có dây tiếp địa bảo vệ, chỉ dựa vào cách điện cơ bản. Điều này làm TC16 (kiểm tra dây nguồn và cách điện) quan trọng hơn hẳn: với thiết bị cấp 0, lớp cách điện của dây là hàng phòng thủ duy nhất.

Và đây là điểm đáng nói nhất: **Gemini đã nhìn thấy ảnh cái quạt này** (mình gửi kèm 2 ảnh trong prompt) nhưng vẫn không sinh ra test case nào dựa trên tiêu chuẩn. Nó sinh test từ hình dạng và chức năng nhìn thấy được, không từ thông tin in trên tem.

## Thêm một quan sát về AI (dùng cho AI Critique)

Trong 8 test case Gemini đưa ra có **TC06 — Locked Rotor Test**: chèn cứng cánh quạt, cấp điện số 3, giữ **30 đến 60 phút** để xem cầu chì nhiệt có ngắt không.

Mình đã **loại test case này và không thực hiện**. Rotor bị kẹt làm dòng điện tăng vọt và dồn toàn bộ nhiệt vào cuộn dây. Quạt gia dụng đã dùng nhiều năm có thể không còn cầu chì nhiệt hiệu lực, và nếu nó không ngắt thì kết quả là cháy cuộn dây. Đây là thử nghiệm phá huỷ, chỉ làm trong phòng thí nghiệm có thiết bị chống cháy và giám sát nhiệt độ.

Gemini viết ra nó như một bước bình thường, **không kèm bất kỳ cảnh báo an toàn nào**. Nó cũng không hỏi lại là mình có đang ở môi trường phòng lab hay không.
