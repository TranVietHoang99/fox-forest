# 🦊 Cáo Trong Rừng (The Fox in the Forest)

Game bài **đánh nước** cho 2 người, bản tiếng Việt, chơi ngay trên trình duyệt. Mỗi ván 13 nước. Điểm phụ thuộc vào **số nước bạn thắng**, và tham quá thì trắng tay!

## Chế độ chơi
- **Chơi với máy**: nhập tên, bấm *Chơi với máy*. Có 3 mức: Dễ (Sóc con), Vừa (Cú mèo), Khó (Cáo già).
- **Online 1 đấu 1**: bấm *Tạo phòng*, gửi mã hoặc link cho bạn bè; bạn bè nhập mã và bấm *Vào phòng*.
  Người tạo phòng phải **giữ tab mở**, vì máy chủ phòng giữ trạng thái ván chơi.
- Tùy chọn điểm thắng trận: 16 (ngắn), 21 (chuẩn), 35 (dài).

## Luật
- 33 lá, 3 chất: 🔔 Chuông, 🗝️ Chìa Khóa, 🌙 Trăng; mỗi chất từ 1 đến 11.
- Mỗi người 13 lá; 7 lá còn lại làm chồng bài, lật lá trên cùng thành **Sắc Lệnh**: chất của nó là **chủ bài**.
- Người không chia bài dẫn nước đầu. Phải ra cùng chất nếu có. Chủ bài lớn nhất thắng, không có chủ bài thì lá lớn nhất của chất được dẫn thắng.
- Năng lực lá lẻ:
  - **1 Thiên Nga**: đánh lá này mà thua nước thì vẫn được dẫn nước sau.
  - **3 Cáo**: được đổi lá Sắc Lệnh với 1 lá trên tay.
  - **5 Tiều Phu**: rút 1 lá, rồi đặt 1 lá trên tay xuống đáy chồng bài.
  - **7 Kho Báu**: người thắng nước được +1 điểm cho mỗi lá 7 trong nước.
  - **9 Phù Thủy**: nếu nước chỉ có một lá 9, lá đó được tính như chủ bài.
  - **11 Quân Vương**: khi được dẫn, đối thủ phải ra lá 1 hoặc lá lớn nhất cùng chất.
- Tính điểm cuối ván: 0–3 nước **6đ** (Khiêm Tốn) · 4/5/6 nước **1/2/3đ** (Thất Bại) · 7–9 nước **6đ** (Thắng Lợi) · 10–13 nước **0đ** (Tham Lam), cộng điểm Kho Báu.
- Ai đạt 21 điểm (khi hết ván) và nhiều điểm hơn sẽ thắng. Bằng điểm ở vạch đích thì đánh thêm một ván (luật nhà).

## Điều khiển
- Máy tính: bấm một lá để đánh; rê chuột lên lá để xem năng lực.
- Điện thoại: chạm 1 lần để chọn và xem năng lực, chạm lần nữa (hoặc nút *Đánh lá này*) để đánh.
- Bảng bên phải: điểm trận, thang bậc điểm của ván (vị trí 2 người theo số nước), bảng theo dõi các lá đã ra, nhật ký.

## Kỹ thuật
Một file `index.html` duy nhất. Toàn bộ 33 lá bài vẽ bằng SVG (Thiên Nga, Cáo, Tiều Phu, Kho Báu, Phù Thủy, Quân Vương, lá số với chấm tròn), khung cảnh rừng đêm với trăng, sao, đom đóm, gốc cây làm mặt bàn. Âm thanh và nhạc hộp nhạc tự tổng hợp bằng Web Audio.
Kết nối P2P bằng [PeerJS](https://peerjs.com/), cùng khung với các game khác trong thư mục. Máy chủ phòng chỉ gửi cho mỗi người bài trên tay của chính họ (lá rút từ Tiều Phu cũng chỉ người rút thấy).
Bot dùng lấy mẫu bài ẩn (PIMC): mô phỏng nhiều thế giới khả dĩ theo những gì nó được biết, chơi thử theo heuristic kỳ vọng điểm theo bậc, và tìm kiếm chính xác alpha-beta cho các nước cuối ván.
Chạy thử: `npx http-server fox-forest -p 5194`.
