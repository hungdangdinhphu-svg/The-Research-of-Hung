## Khởi tạo

Cho $E = \{e_1, e_2, \dots, e_N\}$ là một tập hợp gồm $N$ biểu thức. Tập $E$ phải thỏa mãn các điều kiện tiên quyết sau:

1. Giới hạn toán tử: Các biểu thức $e_i$ chỉ được cấu thành từ các hằng số và các phép toán đại số cơ bản $(+, -, \times, \div)$.

2. Tính khả quyết (Decidability): Nhằm tuân thủ Định lý Richardson và tránh bài toán không quyết định được (undecidable problem), tuyệt đối loại bỏ các hàm siêu việt (transcendental functions) như $\exp, \log, \sin, \cos,\dots$ khỏi tập toán tử.

3. Tính hữu hạn và Khả thi tính toán: Mỗi biểu thức $e_i \in E$ có độ dài chuỗi (chuỗi ký tự biểu diễn) hữu hạn và độ phức tạp thời gian định trị (evaluation time complexity) nằm trong giới hạn khả thi của hệ thống tính toán.

Chi phí để tính toán và xử lý toàn bộ tập $E$ được định nghĩa là $COST\_ALL$, với:

$$COST\_ALL = Cost_{computation} + Cost_{memory} + Cost_{etc}$$


Tôi gọi đây là **"quy trình truyền thống"** :

Thực thi phép ánh xạ định trị tập biểu thức $E$ thành một vector $V \in \mathbb{R}^N$ thông qua tính toán số học trực tiếp.

Đầu ra: Một tập hợp $V = \{v_1, v_2, \dots, v_N\}$ gồm $N$ vô hướng thuộc trường số thực $\mathbb{R}$, tương đương với tọa độ của $N$ điểm trên không gian thực.

Chi phí thực thi: Tiêu tốn toàn bộ chi phí $COST\_ALL$.

Bài toán là làm sao cho quy trình bên dưới khả thi :

Giả định tập $E$ đã được nội hàm hóa (embedded) trong một không gian trạng thái $S$.

Thao tác: Từ không gian $S$, ta có thể thực hiện phép ánh xạ/trích xuất trực tiếp để thu được tập thông tin $I$.

Tính chất: Tập thông tin $I$ bảo toàn cấu trúc và đẳng cấu thông tin (informationally isomorphic) với tập $V$ ở Quy trình 1, tức là $I \equiv V$ về mặt ngữ nghĩa tọa độ trên $\mathbb{R}^N$.

Chi phí thực thi: $COST_{S} \ll COST\_ALL$ (Chi phí trích xuất nhỏ hơn biên độ rất lớn so với việc tính toán từ đầu).

Hệ quả:

Tập thông tin $I$ trích xuất từ $S$ đạt mức tương đương chức năng (functional equivalence) hoàn toàn với tập vô hướng $V$. Do đó, trong mọi kiến trúc hệ thống, thuật toán hay ứng dụng kỹ thuật phần mềm thuần túy, $I$ đóng vai trò là một sự thay thế trực tiếp (drop-in replacement) hoàn hảo cho $V$ mà không làm thay đổi tính đúng đắn của bài toán.
























