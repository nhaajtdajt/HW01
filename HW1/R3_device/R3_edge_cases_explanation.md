# R3 — Ba edge case AI không tìm ra, và vì sao nó bỏ sót

## Bằng chứng

- **(a)** Ảnh chụp toàn bộ danh sách Gemini đã sinh: `evidence/gemini_testcases_1..6.png` — 8 test case TC01–TC08, không có ba case dưới đây.
- **(b)** Giải thích bằng chữ: phần tiếp theo.

## Gemini đã sinh ra những gì

Tám test case: TC01 ba cấp gió · TC02 đảo gió · TC03 khớp gập cổ · TC04 nhấn đồng thời hai phím · TC05 chặn hành trình quét · TC06 kẹt cứng cánh quạt · TC07 mất điện đột ngột · TC08 đặt nghiêng 10 độ.

Cả tám đều xuất phát từ **danh sách chức năng của cái quạt**. Có phím tốc độ thì test phím tốc độ, có tuốc năng thì test tuốc năng, có khớp gập thì test khớp gập. Bốn case nó gọi là "edge case" thực ra vẫn là các chức năng đó đẩy tới cực trị: chặn nó lại, ngắt điện nó, đặt nghiêng nó.

Ba test case dưới đây không sinh ra được bằng cách đó, và mỗi cái chạm vào một kiểu điểm mù khác nhau.

---

## Edge case 1 — TC10: Bấm hai nút tốc độ cách nhau dưới 0,5 giây

**Điểm mù: thời gian giữa hai trạng thái.**

So với chính hai case của Gemini thì thấy rõ:

- **TC01 của Gemini:** bấm 1, **chờ 5 giây**, bấm 2, **chờ 5 giây**, bấm 3. Mỗi trạng thái được để ổn định trước khi chuyển.
- **TC04 của Gemini:** bấm 1 và 3 **đồng thời**. Hai đầu vào cùng một thời điểm.
- **TC10 của em:** bấm 1 rồi bấm 2 **cách nhau dưới 0,5 giây**. Đây là chuyển trạng thái có ràng buộc thời gian.

Gemini tư duy theo trạng thái đứng yên, không theo khoảng thời gian giữa hai trạng thái. Nó không hình dung được thao tác tay thật: người dùng bấm liên tiếp chứ không bấm rồi đếm 5 giây.

**Kết quả: Fail — DEF-01.** Quạt tắt hẳn thay vì chuyển cấp, tái hiện 3/3 lần.

---

## Edge case 2 — TC12: Đảo gió có chạy đúng ở cả ba cấp tốc độ không

**Điểm mù: tương tác giữa hai chức năng.**

Gemini test mỗi chức năng đúng một lần, ở một thiết lập duy nhất. TC02 của nó kiểm tuốc năng **chỉ ở số 2**. Nó không đặt câu hỏi: nếu đổi cấp gió thì cơ cấu đảo gió có còn quét đúng biên độ không?

Đây là tư duy tổ hợp: hai chức năng độc lập trên giấy tờ nhưng dùng chung một động cơ, nên mô-men thay đổi theo cấp gió hoàn toàn có thể ảnh hưởng tới hành trình quét. Gemini phân rã bài toán theo từng chức năng riêng lẻ nên không bao giờ chạm tới vùng giao nhau.

**Kết quả: Pass.** Quạt quét được ở cả ba cấp, biên độ ba lần đo như nhau. Case Pass nhưng vẫn là một vùng rủi ro thật mà bộ test của AI để trống.

---

## Edge case 3 — TC13: Khe hở nan lồng bảo vệ

**Điểm mù: biết tên tiêu chuẩn không có nghĩa là áp dụng được điều khoản.**

Đây là case duy nhất mà Gemini có chạm tới vùng đúng nhưng vẫn trượt. TC08 của nó có tiêu đề *"Độ ổn định chống trượt/lật trên bề mặt nghiêng (IEC 60335 Stability)"* — tức là nó **có** biết bộ tiêu chuẩn IEC 60335 tồn tại và có gắn tên tiêu chuẩn vào test case.

Nhưng nó dừng ở đó. IEC 60335-1 là phần chung cho mọi thiết bị gia dụng, và độ ổn định là mục dễ liên tưởng nhất khi nhìn một vật đặt trên bàn. Phần **IEC 60335-2-80 dành riêng cho quạt điện** — phần quy định vật thăm dò tiêu chuẩn không được chạm tới cánh đang quay — thì không xuất hiện ở bất kỳ test case nào trong tám case.

Điều này đáng chú ý vì tem thiết bị trong ảnh em gửi có in rõ dòng *"SP phù hợp: TCVN 5699-2-80:2007 (IEC 60335-2-80:2005)"*. Gemini đã nhìn thấy ảnh, đã nhắc tới IEC 60335, nhưng không đọc con số **-2-80** trên tem để lần ra bộ yêu cầu cụ thể áp dụng cho chính thiết bị này.

Nói cách khác: nó dùng tên tiêu chuẩn như một nhãn để test case nghe có vẻ chuyên nghiệp, chứ không dùng tiêu chuẩn như một **test oracle** để suy ra yêu cầu phải kiểm.

**Kết quả: Pass.** Không vị trí nào đưa ngón tay chạm được vào cánh.

**Ghi chú về tính chặt chẽ:** tiêu chuẩn dùng **que thử tiêu chuẩn** (test probe B, có khớp nối, đường kính 12 mm). Em dùng ngón út để **xấp xỉ** que thử đó. Đây không phải phép thử hợp chuẩn, và em ghi đúng như vậy trong Excel thay vì tuyên bố đã kiểm tra hợp chuẩn.

---

## Điểm chung của ba case

Gemini sinh test case từ **những gì thiết bị làm được**. Ba case trên đến từ ba nguồn khác, và không nguồn nào nằm trong danh sách chức năng:

| Edge case | Nguồn của ý tưởng | Kiểu điểm mù |
|---|---|---|
| TC10 | Cách người dùng thật sự thao tác | Thời gian giữa hai trạng thái |
| TC12 | Hai chức năng dùng chung một động cơ | Tương tác giữa các chức năng |
| TC13 | Điều khoản cụ thể của TCVN 5699-2-80 in trên tem | Biết tên tiêu chuẩn nhưng không tra điều khoản áp dụng |

Liên hệ với môn học: Gemini dừng lại ở **functional testing** dựa trên đặc tả chức năng. Ba case của em thuộc nhóm dựa trên **rủi ro** và **kinh nghiệm sử dụng** — loại test case mà người kiểm thử phải mang kiến thức bên ngoài đặc tả vào mới nghĩ ra.

Và một quan sát nữa: trong tám test case của Gemini, **chưa case nào tìm ra lỗi**. Hai defect tìm được đều nằm ở các case em tự thêm (TC10 và TC15).

---

## Một test case của AI bị loại vì không an toàn

Trong tám case Gemini đưa ra có **TC06 — Locked Rotor Test**: chèn cứng cánh quạt, cấp điện số 3, giữ **30 đến 60 phút** để xem cầu chì nhiệt có ngắt không.

Em đã **loại case này và không thực hiện**. Rotor bị kẹt làm dòng điện tăng vọt và dồn toàn bộ nhiệt vào cuộn dây. Quạt đã dùng hơn ba năm có thể không còn cầu chì nhiệt hiệu lực, và nếu nó không ngắt thì kết quả là cháy cuộn dây. Đây là thử nghiệm phá huỷ, chỉ thực hiện trong phòng thí nghiệm có thiết bị chống cháy và giám sát nhiệt độ.

Gemini viết nó ra như một bước bình thường, **không kèm bất kỳ cảnh báo an toàn nào**, và cũng không hỏi lại em có đang ở môi trường phòng lab hay không.
