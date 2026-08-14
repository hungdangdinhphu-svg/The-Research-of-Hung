---
 
## 1. Định nghĩa hình thức
 
### 1.1 Đối tượng
 
Cho tập hợp biểu thức số học $\mathcal{E}$, mỗi phần tử là một **DAG có hướng, không chu trình** với:
- Nút lá: hằng số thực có độ chính xác hữu hạn (finite-precision real), biểu diễn bằng $p$ bit.
- Nút trong: một trong bốn toán tử $\{+, -, \times, \div\}$, có đúng 2 con.
- Không cho phép hàm siêu việt (dựa trên Định lý Richardson 1968)

Với $A \in \mathcal{E}$, gọi $n(A)$ = số nút của DAG, $\|A\|$ = giá trị số thực mà $A$ biểu diễn khi đánh giá đầy đủ.

### 1.2 Chi phí đánh giá đầy đủ (baseline đã biết)

$$\text{EVAL}(A) = \Theta(n(A))$$

— chi phí để tính $\|A\|$ bằng cách duyệt DAG một lần theo thứ tự tô-pô (topological order), giả sử mỗi phép toán cơ bản tốn $O(1)$ (bỏ qua chi phí tăng độ chính xác — sẽ nói ở mục 4).

### 1.3 Đối tượng trung tâm: CHỨNG CHỈ THỨ TỰ (Order Certificate)

Cho hai biểu thức $A, B \in \mathcal{E}$. Một **chứng chỉ thứ tự** $\pi(A, B)$ là một chuỗi hữu hạn các phép toán cục bộ trên DAG của $A$ và $B$ (đọc một tập con nút, so sánh một tập con giá trị trung gian, áp dụng cận sai số/interval bound) sao cho:

- $\pi$ **quyết định** đúng một trong ba quan hệ $\{A<B,\ A=B,\ A>B\}$;

- $\pi$ **không cần** tính $\|A\|$ và $\|B\|$ đầy đủ — nó chỉ cần đọc/tính một tập con các nút trung gian, gọi là **witness set** $W(A,B) \subseteq \text{nodes}(A) \cup \text{nodes}(B)$;

- $\pi$ là **có thể kiểm chứng** (verifiable) trong thời gian tuyến tính theo $|W(A,B)|$ — tức giống khái niệm "certificate" trong lý thuyết độ phức tạp


Định nghĩa độ phức tạp chứng chỉ:

$$\text{CERT}(A, B) = \min_{\pi \text{ hợp lệ}} |W_\pi(A, B)|$$

— số nút tối thiểu cần đọc để phân định quan hệ thứ tự giữa $A$ và $B$.

### 1.4 Câu hỏi mở trung tâm

> **Với lớp biểu thức $\mathcal{E}$ đã định nghĩa ở 1.1, tồn tại hay không một tập con vô hạn, không tầm thường $\mathcal{E}' \subseteq \mathcal{E} \times \mathcal{E}$ (cặp biểu thức) sao cho**

> $$\text{CERT}(A,B) = o\big(\min(n(A), n(B))\big) \quad \text{với } (A,B) \in \mathcal{E}'\ ?$$

Nói cách khác: có tồn tại một họ biểu thức, ngày càng lớn, mà việc phân định thứ tự giữa hai biểu thức trong họ đó **luôn** rẻ hơn hẳn (về bậc tiệm cận) so với việc đánh giá đầy đủ dù chỉ một trong hai biểu thức — **và điều kiện để nhận diện một cặp thuộc họ đó có thể kiểm tra được trong thời gian không vượt quá $\text{CERT}$**?

"Không tầm thường" ở đây loại trừ các trường hợp hiển nhiên (ví dụ $A$ và $B$ khác dấu ngay từ hằng số ở nút gốc) — xem mục 3 để phân biệt rõ.

## Axioms

| Comparability | Với mọi $A,B \in \mathcal{E}$, luôn tồn tại **ít nhất một** $\pi$ hợp lệ (điều này tầm thường đúng — $\pi$ = đánh giá đầy đủ luôn là một chứng chỉ hợp lệ, dù không tối ưu). Phần khó là **CERT có nhỏ hơn EVAL hay không**, không phải là sự tồn tại. |

| "Distance"/"Gap" | Định nghĩa lại: $\text{dist}(A,B) := \text{CERT}(A,B)$ — không phải khoảng cách hình học trừu tượng, mà là **số bước rút gọn cây tối thiểu để phân định dấu của $A-B$**. Đại lượng này đo được, có đơn vị (số nút), và trùng khớp với trực giác "độ lệch cấu trúc" mà không cần một không gian $\mathbb{S}$ mới. |

| Total Order / Decidability | Vì $\mathcal{E}$ giới hạn ở $\{+,-,\times,\div\}$ và số hữu tỉ hữu hạn (không có hàm siêu việt), bài toán "$A - B$ so với 0" là **khả định** (decidable) — đây là lý do Richardson's theorem xuất hiện đúng chỗ trong cả hai bản gốc của bạn. Tính khả định là điều kiện *cần* để CERT được định nghĩa tốt, không phải một tiên đề độc lập cần chứng minh thêm. |












