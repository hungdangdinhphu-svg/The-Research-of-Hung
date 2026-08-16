## Khởi tạo

Cho $E = \{e_1, e_2, \dots, e_N\}$ là một tập hợp gồm $N$ biểu thức. Tập $E$ phải thỏa mãn các điều kiện tiên quyết sau:

1. Giới hạn toán tử: Các biểu thức $e_i$ chỉ được cấu thành từ các hằng số và các phép toán đại số cơ bản $(+, -, \times, \div)$.

2. Tính khả quyết (Decidability): Nhằm tuân thủ Định lý Richardson và tránh bài toán không quyết định được (undecidable problem), tuyệt đối loại bỏ các hàm siêu việt (transcendental functions) như $\exp, \log, \sin, \cos,\dots$ khỏi tập toán tử.

3. Tính hữu hạn và Khả thi tính toán: Mỗi biểu thức $e_i \in E$ có độ dài chuỗi (chuỗi ký tự biểu diễn) hữu hạn và độ phức tạp thời gian định trị (evaluation time complexity) nằm trong giới hạn khả thi của hệ thống tính toán.

Chi phí để tính toán và xử lý toàn bộ tập $E$ được định nghĩa là $COST\_ALL$, với:

$$COST\_ALL = Cost_{computation} + Cost_{memory} + Cost_{etc}$$
































