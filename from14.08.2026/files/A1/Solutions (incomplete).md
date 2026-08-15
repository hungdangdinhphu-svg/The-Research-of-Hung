# Structural Space Problem — Tổng hợp và trình bày giải pháp (Chưa hoàn thiện)

Đáp lại Structural Space Problem — Phát biểu chặt chẽ.

Bài toán trung tâm, như phát biểu ở Mục 4 của tài liệu gốc, chứa một lượng từ (quantifier) chưa được cố định: "COST_ALL nhỏ hơn baseline" — nhỏ hơn với mọi cặp biểu thức (worst-case), hay nhỏ hơn trên phần lớn/điển hình các cặp (average-case/generic-case)?

Tác giả cố tình giữ ở trạng thái mở nên đã làm vậy.

Nhưng ở đây, tôi sẽ chỉ tập trung vào lúc mà khi lượng từ này được cố định tường minh, và câu trả lời là một nhị phân (dichotomy) chứng minh được.

Kết quả chính. Tồn tại 𝕊 thỏa A1–A3 với COST_ALL nhỏ hơn thực sự baseline theo nghĩa generic-case (Định lý 1, Định lý 3 — xây dựng, tồn tại). Không tồn tại 𝕊 nào (trong lớp thuật toán chuẩn chứng nhận-số học — certified numerical algorithms, xem phạm vi ở Mục 6) đạt COST_ALL nhỏ hơn baseline theo bậc tiệm cận trong nghĩa worst-case, cho cả Vấn đề lớn 1 lẫn Vấn đề lớn 2 (Định lý 2, Định lý 4 — bất khả thi, chứng minh bằng cấu trúc đối kháng liên phân số).

Nói cách khác: bài toán trung tâm được đóng lại (closed) — không còn "mở" — bằng cách chỉ ra rằng câu trả lời phụ thuộc tất định vào mô hình chi phí, và cả hai nhánh của sự phụ thuộc đó đều chứng minh được. Phần đóng góp "sáng tạo" của lời giải này nằm ở (a) việc xác định chính xác chỗ mơ hồ đó là gốc rễ của tính "mở", (b) một cấu trúc đối kháng bằng continuant liên phân số (continued-fraction continuants) — không có trong tài liệu gốc và không phải kỹ thuật chuẩn trong tài liệu computational-geometry được trích dẫn — để chứng minh chiều bất khả thi, và (c) một phân tích COST_ALL tường minh, có công thức, cho chiều tồn tại.










































