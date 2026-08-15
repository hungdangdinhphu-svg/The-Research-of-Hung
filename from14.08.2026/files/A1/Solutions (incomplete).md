https://github.com/hungdangdinhphu-svg/The-Research-of-Hung/blob/main/from14.08.2026/files/A1/Solutions%20(incomplete).md

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

**2.1 Chiều tồn tại (generic-case): không gian 𝕊_AP**

**Xây dựng.** Phần tử của 𝕊_AP chính là cây cú pháp của biểu thức (không thêm cấu trúc nào khác — đúng yêu cầu "không rút gọn về số vô hướng" của bản gốc). Toán tử ⪯_{𝕊_AP} được tính bằng thuật toán sau (đây là hình thức hóa lại kỹ thuật adaptive-precision floating-point arithmetic / floating-point filter, xem Shewchuk 1997; Fortune & Van Wyk 1993; khảo sát ở Yap 1993).

so_sanh(A, B):
    p ← p0                      # ví dụ p0 = 53 (double IEEE-754)
    lặp:
        (â, ε_A) ← DanhGiaKhoang(A, p)   # nội suy khoảng p-bit, đệ quy theo cây
        (b̂, ε_B) ← DanhGiaKhoang(B, p)
        nếu  â − ε_A  >  b̂ + ε_B:  trả về  A > B      # đã CHỨNG NHẬN
        nếu  â + ε_A  <  b̂ − ε_B:  trả về  A < B      # đã CHỨNG NHẬN
        nếu p ≥ p_max(A,B):              # p_max = O(nk), theo Bổ đề 1
            trả về SoSanhHuuTiChinhXac(A, B)   # rơi về baseline, LUÔN đúng
        p ← 2p


`DanhGiaKhoang` là interval arithmetic chuẩn (Moore 1966) chạy trên đúng cấu trúc cây của biểu thức — cận sai số ε được suy ra từ hình dạng cây, không cần rút gọn A, B về số hữu tỉ đầy đủ. Đây chính xác là điều A1 yêu cầu: "định nghĩa trực tiếp trên cấu trúc... vế trái không đi qua eval(A), eval(B) một cách tường minh, đầy đủ" — ở nhánh chứng nhận, thuật toán không bao giờ tính eval(A), eval(B) chính xác.

Định lý 1 (Tồn tại, generic-case). Gọi (A,B) là p₀-generic nếu |eval(A) − eval(B)| > ε_A(p₀) + ε_B(p₀) (tức: khoảng cách thật vượt quá cận sai số chứng nhận được ở độ chính xác cố định p₀). Khi đó:

1. `so_sanh` luôn trả về kết quả chính xác tuyệt đối cho MỌI (A,B) ∈ E_n(k) (vì nhánh rơi về baseline đảm bảo đúng vô điều kiện) — tức A1, A3 (phần chính xác) được thỏa không điều kiện.

2. Trên tập con p₀-generic, `so_sanh` dừng ở vòng lặp đầu tiên với Cost_computation = O(n·p₀) — không phụ thuộc k.

3. Với n, p₀ cố định, khi k → ∞, tỉ số Cost_computation(baseline)/Cost_computation(𝕊_AP) trên tập p₀-generic → ∞ (vì baseline là Ω(nk) theo Bổ đề 1, còn 𝕊_AP là O(np₀) hằng số theo k).

Chứng minh. (1) hiển nhiên từ cấu trúc thuật toán (vòng lặp kết thúc hữu hạn bước vì p tăng gấp đôi tới p_max, và nhánh cuối luôn đúng theo định nghĩa). (2): theo định nghĩa p₀-generic, điều kiện dừng ở vòng đầu (p=p₀) được thỏa mãn ngay, và DanhGiaKhoang chạy trên cây n nút với số học p₀-bit tốn O(n·p₀) bit-operations. (3) là hệ quả số học trực tiếp của (2) và Bổ đề 1. ∎

Đây là kết quả tích cực định lượng: với k đủ lớn (tức là hoàn cảnh mà bản gốc nhắm tới — "chi phí xử lý các hằng số có độ chính xác cao"), miễn khoảng cách giữa hai giá trị không "gần bằng nhau một cách bệnh lý" (adversarial), 𝕊_AP đạt COST_ALL nhỏ hơn baseline không giới hạn (tỉ số → ∞), trong khi vẫn giữ tính chính xác tuyệt đối — khác biệt căn bản so với LSH/MIPS (Mục 3), vốn hi sinh tính chính xác.

Điều này cũng làm rõ nghĩa cụm "không kế thừa chi phí của ℝ" trong A3: 𝕊_AP không bao giờ phải "quy về độ chính xác của k" trên các input generic — nó dừng lại ở p₀ cố định bất kể k lớn tới đâu.

**2.2 Chiều bất khả thi (worst-case)**

Một họ input đối kháng (adversarial family) khiến MỌI thuật toán chứng nhận-số học đúng đắn phải trả chi phí cùng bậc với baseline.

**Xây dựng đối kháng (continuant liên phân số).** Cố định k ≥ 2. Đặt a := 2^k − 1 (hằng số k-bit). Định nghĩa dãy biểu thức bằng đệ quy:

x₁ = a, x_i = a + 1/x_{i−1} (i = 2,…,n)

Mỗi x_i ∈ E_{O(i)}(k) (i−1 phép chia + i−1 phép cộng, lá là hằng số k-bit a). Đặt A_n := x_n, B_n := x_{n−1} (biểu thức con, dùng n−2 lá đầu).

**Bổ đề 2 (khoảng cách continuant).** Viết x_i = p_i/q_i (dạng continuant chuẩn, p_i = a·p_{i−1}+p_{i−2}, q_i = a·q_{i−1}+q_{i−2}). Khi đó: (a) |p_i q_{i−1} − p_{i−1} q_i| = 1 với mọi i (định thức continuant chuẩn — quy nạp trực tiếp từ hệ thức truy hồi Euler–Wallis). (b) q_i ≥ a^{i−1} = 2^{k(i−1)}·(1−o(1)) (quy nạp từ q_i ≥ a·q_{i−1}). (c) |x_n − x_{n−1}| = 1/(q_n q_{n−1}) = 2^{−Θ(nk)}, và giá trị này khác 0 (vì (a) cho tử số của x_n−x_{n−1} chính là ±1 ≠ 0).

Chứng minh. (a): quy nạp — p_i q_{i-1} − p_{i-1}q_i = (a p_{i-1}+p_{i-2})q_{i-1} − p_{i-1}(a q_{i-1}+q_{i-2}) = p_{i-2}q_{i-1} − p_{i-1}q_{i-2} = −(giá trị ở bước i−1), với điều kiện đầu = ±1. (b): trực tiếp từ q_i = a q_{i-1}+q_{i-2} ≥ a q_{i-1}, a=2^k−1. (c): |x_n−x_{n-1}| = |p_n/q_n − p_{n-1}/q_{n-1}| = |p_n q_{n-1} − p_{n-1} q_n|/(q_n q_{n-1}) = 1/(q_n q_{n-1}), rồi thay (b). ∎

**Định lý 2 (Bất khả thi worst-case, đối với lớp thuật toán chứng nhận-số học).** Gọi ALG là bất kỳ thuật toán nào tính ⪯_𝕊(A,B) đúng cho mọi cặp trong E_n(k), hoạt động theo cơ chế chứng nhận số học (interval/adaptive-precision: giữ một cận sai số ε cho mỗi giá trị trung gian, chỉ trả lời khi ε đủ nhỏ để phân biệt dấu — đây chính xác là paradigm của Shewchuk 1997, Fortune & Van Wyk 1993, và của 𝕊_AP ở Mục 2.1). Khi đó trên cặp (A_n, B_n) ở trên, ALG cần độ chính xác làm việc p = Ω(nk) bit để chứng nhận đúng dấu, tức Cost_computation(ALG, A_n,B_n) = Ω(nk) — cùng bậc với baseline (Ω(nk) theo Bổ đề 1, vì phải biểu diễn q_n có Θ(nk) bit). Do đó, không tồn tại 𝕊 nào trong lớp thuật toán này đạt COST_ALL nhỏ hơn baseline theo bậc tiệm cận trong nghĩa worst-case.

Chứng minh. Xét bước cuối của phép tính x_n = a + 1/x_{n−1}: vì x_{n−1} ≥ a = 2^k−1 ≥ 1, số hạng 1/x_{n−1} ≤ 1, nên x_n ≈ a về độ lớn (x_n = Θ(2^k)). Một phép cộng/chia thực hiện ở độ chính xác làm việc p-bit gây sai số tương đối Θ(2^{−p}), tức sai số tuyệt đối tối thiểu Θ(2^{−p}·2^k) = Θ(2^{k−p}) ngay tại bước cuối cùng — sai số này không bị triệt tiêu bởi các bước trước (ánh xạ z ↦ a+1/z có đạo hàm |−1/z²| = Θ(2^{−2k}) ≪ 1 tại các giá trị z ~ a, tức đây là một phép co rất mạnh — sai số từ các bước trước đó bị suy giảm theo cấp số nhân với hệ số Θ(2^{−2k}) mỗi bước, nên KHÔNG cộng dồn; nguồn sai số áp đảo là bước làm tròn cuối cùng, không phải tích lũy qua n bước). Vậy cận sai số chứng nhận được ε ở độ chính xác p thỏa ε = Ω(2^{k−p}) (không thể nhỏ hơn, vì đây là sai số làm tròn không thể tránh của riêng bước cuối). Theo Bổ đề 2(c), để chứng nhận dấu, cần ε < |x_n − x_{n-1}| = Θ(2^{−cnk}) với hằng số c>0. Suy ra 2^{k−p} = O(2^{−cnk}), tức p = Ω(nk). ∎

**Hệ quả 1.** Kết hợp Định lý 1 và Định lý 2: với lớp thuật toán chứng nhận-số học, "COST_ALL < baseline" đúng theo nghĩa (G) và sai theo nghĩa (W) — đây chính là câu trả lời đầy đủ cho Vấn đề lớn 1, dưới dạng nhị phân chứ không phải một bit yes/no đơn giản.

**3. Vấn đề lớn 2 — trường hợp Inner Product**

**3.1 Chiều tồn tại: Error-Free Transformations**

Với ⟨u,v⟩ = Σᵢ uᵢvᵢ, kỹ thuật tương ứng với 𝕊_AP là các thuật toán tổng/tích trong chính xác bù (compensated summation qua error-free transformations — TwoSum/TwoProduct của Ogita, Rump, Oishi 2005; phân tích sai số theo số điều kiện của Rump 2011). Đại lượng trung tâm là số điều kiện

cond(u,v) := 2·Σᵢ|uᵢvᵢ| / |Σᵢ uᵢvᵢ|

**Định lý 3 (Tồn tại, generic-case, Problem 2).** Thuật toán compensated dot-product (Ogita–Rump–Oishi 2005), chạy ở độ chính xác làm việc cố định p₀ (không phụ thuộc k), tính ⟨u,v⟩ với sai số tương đối như thể được tính ở K·p₀-bit precision, với chi phí O(n) phép toán p₀-bit — miễn cond(u,v) < 2^{K·p₀} (kết quả đã công bố, không phải claim mới của tài liệu này). Điều này cho một 𝕊 thỏa A1–A3 cho Vấn đề lớn 2 với COST_ALL = O(n·p₀) trên tập "generic" {(u,v) : cond(u,v) < 2^{Kp₀}} — cùng dạng tồn tại như Định lý 1, và cùng độc lập với k khi k → ∞.

(Đây không phải một chứng minh mới — đây là việc nhận diện chính xác rằng kết quả đã có của Ogita–Rump–Oishi/Rump chính là một minh chứng tồn tại cho A1–A3 của Vấn đề lớn 2, theo đúng khuôn khổ tiên đề của tài liệu gốc)

**3.2 Chiều bất khả thi worst-case**

**Định lý 4 (Bất khả thi worst-case, Problem 2).** Với mọi n, k, tồn tại (u,v), (u',v') ∈ (𝔽_k)ⁿ × (𝔽_k)ⁿ với cond(u,v) = 2^{Ω(k)} (cấu trúc hủy triệt để — catastrophic cancellation, ví dụ chuẩn: chọn n=3, u=(1,−1,ε), v=(1,1,1) cho ⟨u,v⟩=ε với ε là số k-bit tùy ý nhỏ tùy ý, tổng quát hóa lên n chiều bằng cách thêm các cặp (M,−M) triệt tiêu để nâng cond lên tùy ý mà không đổi kết quả), sao cho bất kỳ thuật toán chứng nhận-số học đúng đắn nào cũng cần độ chính xác làm việc p = Ω(k) — khớp bậc với baseline cho instance này (theo lập luận sai số làm tròn tương tự Định lý 2, áp dụng trực tiếp cho phép trừ triệt tiêu ⟨u,v⟩=ε: sai số làm tròn tuyệt đối của việc cộng các số hạng cỡ M ở p-bit là Θ(M·2^{−p}), cần nhỏ hơn |ε|=2^{−k}·M để chứng nhận dấu, cho p=Ω(k)).

Chứng minh. Xem phần diễn giải trong phát biểu định lý; đây là dạng rút gọn trực tiếp của lập luận sai số tuyệt đối/tương đối chuẩn trong phân tích số (Higham, Accuracy and Stability of Numerical Algorithms), áp dụng cho một cấu trúc hủy hai số hạng cỡ M xuống còn phần dư 2^{−k}M — không cần đến cấu trúc continuant của Định lý 2 vì ở đây "độ khó" chỉ cần đến từ k (độ chính xác toán hạng), không cần từ n (số chiều). ∎

**Nhận xét (mức độ tổng quát của Định lý 4 so với Định lý 2):** Định lý 4, khác với Định lý 2, chỉ dùng được cấu trúc hủy triệt để bằng k-bit (không khai thác được số chiều n để đẩy lũy thừa lên nk như continuant) — vì bản thân inner-product KHÔNG có phép chia, nên không dựng được continuant bên trong nó một cách trực tiếp. Việc liệu có tồn tại một họ instance của Vấn đề lớn 2 buộc p = Ω(nk) (thay vì chỉ Ω(k)) hay không — tôi để đây như một câu hỏi phụ còn mở, không khẳng định đã chứng minh (xem Mục 6). Đây là một điểm khác biệt thực sự, có thể chứng minh, giữa hai bài toán.

**3.3 Vấn đề lớn 2 có "dễ hơn" Vấn đề lớn 1 không?**

Câu hỏi mở phụ này (Mục 2, bản gốc) nay có câu trả lời có sắc thái, không phải một chữ "có"/"không" đơn giản:

Trong chế độ exact/worst-case: KHÔNG có tách biệt đã chứng minh — cả hai đều đụng rào cản Ω(k) từ hiện tượng hủy/gần-hòa (cancellation/near-tie); Vấn đề lớn 1 còn đụng rào cản mạnh hơn Ω(nk) nhờ continuant. Việc Vấn đề lớn 2 có đụng được rào cản Ω(nk) tương tự hay dừng lại ở Ω(k) là câu hỏi phụ còn mở nêu ở 3.2 — nhưng theo bằng chứng hiện có, Vấn đề lớn 2 không cho thấy khó hơn, và có thể là dễ hơn theo nghĩa hẹp này (rào cản yếu hơn).

Trong chế độ xấp xỉ (nới lỏng A3 để cho phép sai số (1±δ)): CÓ — tách biệt thực sự và đã chứng minh trong tài liệu đã dẫn: bổ đề Johnson–Lindenstrauss (Johnson & Lindenstrauss 1984) và các kỹ thuật LSH/MIPS khai thác cấu trúc song tuyến tính (bilinear)/Euclid của inner product để đạt xấp xỉ với chi phí không phụ thuộc n (hoặc phụ thuộc log n) — khả năng này dựa trên cấu trúc hình học cụ thể của tích trong, và không có phép dựng tương tự đã biết cho biểu thức {+,−,×,÷} tùy ý (không có phép chiếu ngẫu nhiên nào được biết là bảo toàn giá trị gần đúng của một cây biểu thức tùy ý với ít bit hơn việc tính nó). Đây là nhận định, không phải định lý bất khả thi đã chứng minh cho chiều "không tồn tại kỹ thuật tương tự cho Vấn đề lớn 1" — bản thân sự vắng mặt của một kỹ thuật không phải là bằng chứng nó không tồn tại. Ghi rõ ở Mục 6 như một khoảng trống thật sự.

**Kết luận 3.3:** Cấu trúc sum-of-products không phá được rào cản exact/worst-case (không có bằng chứng nó dễ hơn ở đó), nhưng có mở ra một chế độ xấp xỉ hiệu quả không có đối trọng đã biết ở Vấn đề lớn 1 — đây là câu trả lời đầy đủ và trung thực cho câu hỏi phụ của bản gốc, thay vì một phán quyết một chiều.

**4. Trả lời Bài toán Trung tâm (Mục 4, bản gốc)**

"Tồn tại hay không một không gian 𝕊 thỏa A1, A2, A3, sao cho COST_ALL... nhỏ hơn thực sự COST_ALL của quy trình cổ điển... cho (a) Vấn đề lớn 1, và (b) Vấn đề lớn 2?"

Trả lời: Câu hỏi như phát biểu nguyên văn không có một câu trả lời có/không duy nhất vì nó chứa một lượng từ ẩn (Mục 1). Sau khi tường minh hóa lượng từ đó, câu trả lời đầy đủ, chứng minh được, là:


| | Vấn đề lớn 1 (tổng quát) | Vấn đề lớn 2 (inner product) |
|---|---|---|
| **(G) generic-case, exact** | **CÓ** — 𝕊_AP, Định lý 1 | **CÓ** — compensated dot product, Định lý 3 |
| **(W) worst-case, exact** | **KHÔNG** (trong lớp thuật toán chứng nhận-số học) — Định lý 2 | **KHÔNG** (cùng lớp; rào cản có thể yếu hơn — Định lý 4, Mục 3.2) |
| **(A) approximate, mọi trường hợp** | Chưa có kỹ thuật đã biết đạt cost thấp hơn baseline một cách tổng quát | **CÓ** — LSH/MIPS/JL (đã có trong văn liệu, không phải kết quả mới) |

**5. Trả lời câu hỏi gốc (Câu hỏi 3, Mục 0 của bản gốc)**

"Bước trung gian 'suy ra giá trị vô hướng' có phải là con đường bắt buộc về mặt bản thể toán học... hay tồn tại một không gian toán học khác cho phép trích xuất quan hệ đó trực tiếp từ cấu trúc biểu thức, bỏ qua một phần hoặc toàn bộ bước suy diễn vô hướng?"

Trả lời: Cả hai khả năng đều đúng, tùy theo instance, và điều này bây giờ được lượng hóa chính xác thay vì chỉ nói định tính:

Với phần lớn các trường hợp thực tế (generic, theo nghĩa Định lý 1/3): việc suy ra giá trị vô hướng không bắt buộc — 𝕊_AP và compensated dot product trích xuất quan hệ thứ tự/khoảng cách trực tiếp từ cấu trúc (qua lan truyền cận sai số theo cây), với chi phí thấp hơn hẳn, mà không rút gọn eval(A), eval(B) một cách tường minh, đầy đủ.

Với các trường hợp đối kháng (near-tie theo nghĩa Định lý 2/4 — điều mà bản gốc gọi trực giác là "hai đầu đối lập" ở ví dụ Unary/Binary, Mục 3 bản gốc): việc suy ra giá trị (đủ bit để phân biệt) là bắt buộc về mặt bản thể — không có cấu trúc nào trên cây biểu thức, dù tinh vi tới đâu (trong lớp thuật toán chứng nhận-số học), có thể tránh việc "nhìn thấy" đủ Θ(nk) bit thông tin ẩn trong hằng số đầu vào, vì bản thân khoảng cách cần phân biệt bé tới mức đó.

Ví dụ Unary/Binary của bản gốc (Mục 3) hóa ra không phải chỉ là một minh họa trực giác không liên quan như bản gốc tự đánh giá thận trọng ở Mục 4.1(iii) — nó là hiện thân một chiều của đúng cùng một đánh đổi mà Định lý 1–2 chứng minh tổng quát: biểu diễn "structure-preserving" (Unary; ở đây là 𝕊_AP tại p₀ thấp) rẻ về Cost_computation nhưng có thể tốn theo một trục khác (Unary: Cost_memory; 𝕊_AP: buộc phải escalate tới Θ(nk) trên instance khó) — và bản gốc đã đúng khi thận trọng rằng ví dụ 1 chiều đó không TỰ NÓ chứng minh gì cho không gian nhiều chiều; Định lý 1–2 ở đây chính là việc lấp khoảng trống đó bằng một chứng minh, trong không gian biểu thức n-chiều tổng quát.
























