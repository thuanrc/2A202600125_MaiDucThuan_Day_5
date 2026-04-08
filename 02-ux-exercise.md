# Bài tập UX: phân tích sản phẩm AI thật
**Họ và tên:** Mai Đức Thuận

**Mã học viên:** 2A202600125

## Chọn sản phẩm
| Sản phẩm | AI feature | Truy cập |
| --- | --- | --- |
| Vietnam Airlines — Chatbot NEO | Chatbot hỗ trợ khách hàng, tra cứu chuyến bay, xử lý yêu cầu cơ bản | vietnamairlines.com hoặc Zalo VNA |

## Phần 1 — Khám phá (15 phút)
**Trước khi dùng:** 
- **Marketing hứa:** "Trợ lý ảo thông minh NEO hỗ trợ 24/7", "Tra cứu nhanh - chính xác", "Xử lý đổi vé, hoàn vé tự động bằng ngôn ngữ tự nhiên".
- **Kỳ vọng:** AI hiểu được câu hỏi phức tạp, không cần bấm chọn menu cứng.

**Dùng thử thực tế:**
- **Phản hồi AI:** Xử lý tốt câu hỏi đơn (giờ bay, hành lý). Gặp khó khăn với câu hỏi nhiều ý định như "đổi vé + mua hành lý".
- **UI:** Hiện danh sách FAQ dạng nút bấm khi không hiểu. Không có indicator rõ ràng khi AI đang suy nghĩ hay xử lý ngữ cảnh.
- **Không có fallback trực tiếp:** không có nút chuyển cho người trực tiếp, chỉ có tự động chuyển cho nhân viên khi bot chưa xử lý được yêu cầu đặc biệt trong khi chat.

## Phần 2 — Phân tích 4 paths (10 phút)
| Path | Câu hỏi | Phân tích Chatbot NEO |
| --- | --- | --- |
| 1. Khi AI đúng | User thấy gì? Hệ thống confirm thế nào? | User thấy thông tin chuyến bay hiển thị dạng card rõ ràng, có icon check xanh. Hệ thống confirm bằng dữ liệu thực (giờ, sân bay, trạng thái). UX mượt, đúng như marketing. |
| 2. Khi AI không chắc | Hệ thống xử lý thế nào? Im lặng? Hỏi lại? Show alternatives? | Bot hỏi lại "Bạn vui lòng cung cấp mã đặt chỗ". Không im lặng, có show 3-4 nút gợi ý (FAQ). Nhược điểm: Gợi ý đôi khi không khớp ngữ cảnh, bắt user phải chọn lại thủ công. |
| 3. Khi AI sai | User biết bằng cách nào? Sửa bằng cách nào? Bao nhiêu bước? | User biết khi bot trả lời lệch chủ đề hoặc lặp câu cũ. Không có nút "Sửa câu hỏi" hay "Gõ lại". User phải tự thoát ra và restart conversation → mất 3-4 bước để quay lại. |
| 4. Khi user mất tin | Có exit không? Có fallback (con người, manual)? Dễ tìm không? | Fallback tồn tại nhưng rất khó tìm. Nút "Gặp tổng đài viên" ẩn trong menu cài đặt/phụ. Không có trigger tự động chuyển sang người khi AI fail 2 lần → User dễ bỏ cuộc. |

**Tự phân tích:**
- **Path xử lý tốt nhất:** Path 1 (Khi AI đúng). Lý do: Câu hỏi đơn, dữ liệu có sẵn, AI phản hồi nhanh, UI hiển thị rõ ràng.
- **Path yếu nhất:** Path 4 (Khi user mất tin). Lý do: Thiếu cơ chế fallback mượt mà, exit path bị ẩn, làm gãy trải nghiệm và giảm niềm tin vào sản phẩm.
- **Gap marketing vs thực tế:** Marketing hứa "xử lý mọi yêu cầu bằng ngôn ngữ tự nhiên", nhưng thực tế chỉ ổn với intent đơn. Gap lớn nhất nằm ở **khả năng xử lý multi-intent** và **thiếu human hand-off thông minh** khi AI gặp giới hạn.

## Phần 3 — Sketch "làm tốt hơn" (10 phút)
**Path chọn để cải thiện:** Path 4 — Khi user mất tin / AI sai liên tục

- **Cột trái (AS-IS):** User hỏi câu phức → Bot trả lời FAQ sai lệch → User scroll tìm nút hỗ trợ ẩn trong menu → Gạch chéo đoạn này đánh dấu "Gãy UX".
- **Cột phải (TO-BE):** User hỏi câu phức → Bot hiện popup nhỏ: "Tôi thấy bạn có 2 yêu cầu. Bạn muốn xử lý việc nào trước?" + Nút nổi bật bên dưới: "Chưa ổn? Nói chuyện với nhân viên ngay".

**Ghi chú thay đổi:**
| Thêm | Bớt | Đổi |
| --- | --- | --- |
| + Nút CTA "Gặp nhân viên" nổi bật sau 2 lần bot fail | - Bớt danh sách FAQ dài, không liên quan | - Đổi logic: Từ "bắt user chọn lại" → "AI xác nhận intent trước khi xử lý" |
| + Toast message: "Tôi chưa hiểu rõ, thử cách khác hoặc gặp người nhé!" | - Bớt bước user phải tự thoát app/web để tìm hotline | - Đổi vị trí nút hỗ trợ: Từ menu ẩn → sticky bar cuối khung chat |

