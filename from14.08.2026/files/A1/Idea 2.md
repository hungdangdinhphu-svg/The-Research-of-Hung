https://github.com/hungdangdinhphu-svg/The-Research-of-Hung/blob/main/from14.08.2026/files/A1/Idea%202.md

(vietnamese & english)

Authors: Hung Dinh Phu Dang

Date (Completeness): ...

---

Đọc phần Appendix để xem các giải thích về một số cụm từ/từ trong bài.

---

# Handling procedures (Classical)

**Tôi gọi cái bên dưới là "Quy trình xử lý cổ điển" :**

$$\text{Expressions (Các biểu thức)} \xrightarrow{\text{Arithmetic Computation}} \text{Scalar Values (Giá trị Vô hướng)}$$




# **Primary Hypothesis :**

Có một lớp các bài toán ứng dụng đương đại mà ở đó, chúng ta phải xử lý $N$ biểu thức khổng lồ. Việc ép buộc toàn bộ $N$ biểu thức này phân rã thành các giá trị vô hướng chỉ để tìm ra quan hệ thứ tự và khoảng cách thực chất là sự lãng phí tài nguyên cục bộ.


Ý tưởng trung tâm là kiến tạo một không gian toán học hình thức $\mathbb{S}$ (Structural Space) - nơi các biểu thức giữ nguyên tính toàn vẹn cấu trúc ký hiệu (structural integrity). Thay vì triệt tiêu hoàn toàn sự tồn tại của số vô hướng, không gian này sử dụng cấu trúc tô-pô (topology) của biểu thức để bao tiêu (bound) các thuộc tính quan hệ. Bước "tính toán vô hướng" truyền thống sẽ bị giáng cấp từ "nhiệm vụ bắt buộc" thành "nhiệm vụ trì hoãn" (lazy evaluation), chỉ được kích hoạt tại các "biên giới quyết định" (decision boundaries) cực hẹp nơi sự tương đồng cấu trúc là quá lớn.


Để không gian này có giá trị thực tiễn, nó phải thỏa mãn các tiên đề sau:

1. Khả năng bao tiêu khoảng cách (Structural Bounding): Tồn tại một độ đo metric trực tiếp trên đồ thị biểu thức $d_{\mathbb{S}}(A, B)$ sao cho nó phản ánh tỷ lệ thuận với khoảng cách vô hướng $\vert{}A - B\vert{}$. Thay vì phải tính ra $A$ và $B$, hệ thống đo $d_{\mathbb{S}}$.


2. Tính phân rã cục bộ (Topological Ordering): Không gian $\mathbb{S}$ không cần đẳng cấu tuyệt đối với $\mathbb{R}$, mà cung cấp một Trật tự bộ phận nghiêm ngặt (Strict Partial Order). Nếu $d_{\mathbb{S}}(A, B) > \epsilon$ (với $\epsilon$ là ngưỡng cấu trúc), không gian khẳng định $A > B$ với độ tin cậy tuyệt đối mà không cần tính toán. Chỉ khi $d_{\mathbb{S}}(A, B) \le \epsilon$, hệ thống mới cấp phát tài nguyên vô hướng (Scalar/Binary fallback).



3. Tối ưu hóa COST_ALL trên hệ lớn (Amortized Cost Efficiency): Hình dáng không gian này phải đảm bảo rằng khi xét trên $N$ biểu thức (với $N \to \infty$), tổng chi phí COST_ALL để xếp hạng và xác định khoảng cách trên $\mathbb{S}$ nhỏ hơn nghiêm ngặt (strictly less than) tổng chi phí ALU theo chuẩn quy đổi Binary.

# Computational Trade-Offs

Cho phép: $N$ biểu thức chỉ được chứa các phép toán số học cơ bản $\{+, -, \times, \div\}$ và các số thực có độ chính xác hữu hạn (finite precision)

Loại trừ: Mọi hàm siêu việt đều không được phép. (Richardson's Theorem - 1968)
