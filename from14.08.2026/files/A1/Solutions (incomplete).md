# Structural Space Problem — Tổng hợp và trình bày giải pháp (Chưa hoàn thiện)

Đáp lại Structural Space Problem — Phát biểu chặt chẽ.

Bài toán trung tâm, như phát biểu ở Mục 4 của tài liệu gốc, chứa một lượng từ (quantifier) chưa được cố định: "COST_ALL nhỏ hơn baseline" — nhỏ hơn với mọi cặp biểu thức (worst-case), hay nhỏ hơn trên phần lớn/điển hình các cặp (average-case/generic-case)?

Tác giả cố tình giữ ở trạng thái mở nên đã làm vậy.

Nhưng ở đây, tôi sẽ chỉ tập trung vào lúc mà khi lượng từ này được cố định tường minh, và câu trả lời là một nhị phân (dichotomy) chứng minh được.

Kết quả chính. Tồn tại 𝕊 thỏa A1–A3 với COST_ALL nhỏ hơn thực sự baseline theo nghĩa generic-case (Định lý 1, Định lý 3 — xây dựng, tồn tại). Không tồn tại 𝕊 nào (trong lớp thuật toán chuẩn chứng nhận-số học — certified numerical algorithms, xem phạm vi ở Mục 6) đạt COST_ALL nhỏ hơn baseline theo bậc tiệm cận trong nghĩa worst-case, cho cả Vấn đề lớn 1 lẫn Vấn đề lớn 2 (Định lý 2, Định lý 4 — bất khả thi, chứng minh bằng cấu trúc đối kháng liên phân số).

Nói cách khác: bài toán trung tâm được đóng lại (closed) — không còn "mở" — bằng cách chỉ ra rằng câu trả lời phụ thuộc tất định vào mô hình chi phí, và cả hai nhánh của sự phụ thuộc đó đều chứng minh được. Phần đóng góp "sáng tạo" của lời giải này nằm ở (a) việc xác định chính xác chỗ mơ hồ đó là gốc rễ của tính "mở", (b) một cấu trúc đối kháng bằng continuant liên phân số (continued-fraction continuants) — không có trong tài liệu gốc và không phải kỹ thuật chuẩn trong tài liệu computational-geometry được trích dẫn — để chứng minh chiều bất khả thi, và (c) một phân tích COST_ALL tường minh, có công thức, cho chiều tồn tại.

**1. Hình thức hóa mô hình chi phí (bước bắt buộc trước khi "giải")**

Tài liệu gốc định nghĩa COST_ALL một cách cố ý trừu tượng ("môi trường thực tế, thiết bị quy định"). Để bài toán quyết định được, ta phải chọn một mô hình cụ thể. Lựa chọn dưới đây không phải tùy tiện: nó là mô hình chuẩn được dùng chính trong hai dòng tài liệu mà bản gốc tự trích dẫn làm tiền lệ (Mục 4.1(ii) của bản gốc: exact/certified geometric predicate evaluation; error-free-transformation dot products).

**Mô hình.** Real-RAM với chi phí theo bit (bit-complexity RAM): một phép toán số học trên hai số có p bit tốn Θ(p) đến Θ(p log p) bit-operations (tùy thuật toán nhân dùng schoolbook hay FFT — kết luận bên dưới không phụ thuộc lựa chọn này). Một biểu thức A gồm n toán tử trên các lá k-bit (𝔽_k = tập số hữu tỉ biểu diễn được bằng phân số có tử/mẫu ≤ k bit) thuộc lớp E_n(k).

Cost_computation(ALG, A, B) = tổng số bit-operations mà thuật toán ALG thực hiện để trả lời ⪯_𝕊(A,B) (hoặc d_𝕊(A,B)), tính trên input cụ thể (A,B).

**"Baseline"** = thuật toán cổ điển: rút gọn A, B về số hữu tỉ chính xác (tử/mẫu dạng bignum, không rút gọn qua GCD — xem Bổ đề 1), rồi so sánh bằng cross-multiplication.


**Hai lượng từ khả dĩ cho "COST_ALL < baseline":**

(W) Worst-case: max trên toàn bộ E_n(k)×E_n(k) của Cost_computation(𝕊, A,B) < max trên toàn bộ E_n(k)×E_n(k) của Cost_computation(baseline, A,B), theo bậc tiệm cận (n,k → ∞).

(G) Generic-case: tồn tại một tập con "không suy biến" 𝒢 ⊆ E_n(k)×E_n(k), có thể mô tả tường minh và chiếm "hầu hết" các trường hợp thực tế (xem định nghĩa "p₀-generic" ở Định lý 1), sao cho với mọi (A,B) ∈ 𝒢, Cost_computation(𝕊,A,B) < Cost_computation(baseline,A,B), thường là một khoảng cách tiệm cận không giới hạn.

Phần còn lại của tài liệu chứng minh: (G) đúng (Định lý 1, 3) và (W) sai (Định lý 2, 4).

**Bổ đề 1 (độ dài bit của baseline).** Với phép cộng/trừ/nhân/chia hai số hữu tỉ không rút gọn qua GCD, nếu T(x) := (số bit tử) + (số bit mẫu) của x, thì T(x∘y) ≤ T(x) + T(y) + O(1) cho ∘ ∈ {+,−,×,÷}. Do đó, với cây biểu thức n toán tử, lá k-bit: T(eval(A)) = O(nk).

Chứng minh. Với nhân/chia: tử(x∘y) và mẫu(x∘y) là tích của tử/mẫu thành phần, nên độ dài bit cộng dồn. Với cộng/trừ: a/b + c/d = (ad±bc)/(bd); độ dài bit mẫu = L(b)+L(d); độ dài bit tử ≤ max(L(a)+L(d), L(b)+L(c)) + 1. Cộng lại, T(x+y) ≤ T(x)+T(y)+O(1). Quy nạp theo cấu trúc cây cho kết luận. ∎

**2. Vấn đề lớn 1 — biểu thức số học tổng quát {+,−,×,÷}**







































