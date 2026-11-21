# Danh sách lớp v0 — Hoàng Minh Hải · G09

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `eye_left`, `eye_right` | `open`, `closed`, `unknown` theo từng mắt | Ước lượng thời gian nhắm mắt qua nhiều khung hình để hỗ trợ cảnh báo buồn ngủ | Có khi phân biệt được hai mí. Phản xạ hoặc che khuất có thể khiến trạng thái là `unknown`. |
| 2 | `gaze_zone` | `road`, `mirror_l`, `mirror_r`, `mirror_c`, `cluster`, `center`, `lap`, `other` | Theo dõi vùng nhìn để phát hiện tài xế rời mắt khỏi đường kéo dài | Suy ra khi hướng mắt và đầu đủ rõ. Dùng `other` khi chưa chắc, kèm ghi chú. |
| 3 | `glasses` | `none`, `clear`, `sun`, `unknown` | Đánh giá độ tin cậy của tín hiệu mắt khi có kính hoặc phản xạ | Tùy khung hình. Kính râm có thể trông trong trên NIR. |
| 4 | `face13` | 13 điểm, có cờ `occluded` hoặc `outside` khi cần | Theo dõi hình học khuôn mặt để hỗ trợ ước lượng hướng đầu và trạng thái mí | Tùy độ rõ và che khuất. Chỉ gán khi mặt rộng từ 60 px. |
| 5 | `hand.on_wheel` | `yes`, `no`, `unknown` trên từng tay | Xác định tay có tiếp xúc vô lăng để đánh giá khả năng tiếp quản khi hệ thống yêu cầu | Có khi thấy vùng tiếp xúc tay–vô lăng. |
| 6 | `phone.state` | `held`, `mounted`, `lap` | Phân biệt điện thoại cầm tay với máy trên giá hoặc đặt ở đùi để hỗ trợ đánh giá xao nhãng | Có khi nhìn ra cạnh, góc hoặc màn hình điện thoại. |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person.seat` | `rear_left`, `rear_middle`, `rear_right` trong bài lab | Xác định ghế có hành khách để áp dụng nhắc dây theo ghế | Có khi phần người thấy được đủ để định vị theo ghế. |
| 2 | `person.seatbelt` | `not_worn`, `unknown` cho SVIRO | Hỗ trợ nhắc thắt dây theo từng ghế có người | Có khi nhìn rõ vùng thân và dây. Ghi `unknown` nếu bị che hoặc thiếu chi tiết. |
| 3 | `child_seat.occupied` | `no`, `unknown` | Phân biệt ghế trẻ em trống với ghế chưa xác minh được bên trong, phục vụ kiểm tra tình trạng ghế | Nhận dạng được theo hình dáng. Cần nhìn rõ lòng ghế để xác nhận `no`. |
| 4 | `infant_seat.facing` | `rear`, `front` | Xác định hướng lắp nôi theo chiều xe để hỗ trợ kiểm tra bố trí ghế | Có khi thấy được hình dáng và hướng lắp. |
| 5 | `object.type` | `bag`, `box`, `cup`, `other` | Phân biệt đồ vật đặt trên ghế với hành khách để tránh nhắc dây sai | Dựa chủ yếu vào hình dáng. Ghi `other` nếu chưa đủ căn cứ phân loại. |
| 6 | `frame_meta.camera_blocked` | `yes`, `no` | Phát hiện khi camera bị che để hệ thống đánh dấu kết quả theo dõi ghế là thiếu tin cậy | Có thể nhận ra khi có dấu hiệu che khuất rõ trong khung. |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. Câu hỏi: G09 có người nhỏ trong ghế/nôi, trong khi GUIDE mô tả không có ca này và schema Day12 thiếu occupied=yes. Coach xác nhận cách xử lý các ghế này thế nào?

   Khung ví dụ: S01_rgb, S02_ir, S05_rgb, S06_ir.
    Bạn tạm gán thế nào và vì sao: Giữ box ghế theo xe; child_seat S02 dùng occupied=unknown theo schema hiện tại. Nôi S01/S05/S06 dùng facing=front sau review. Gán person/face của người nhỏ chờ phạm vi Ngày 22 theo slide 50.
2. Câu hỏi: Khi bàn tay nằm sát vô lăng nhưng vùng tiếp xúc bị che, tiêu chí hoặc ví dụ mẫu nào quyết định on_wheel=yes hay unknown?

   Khung ví dụ: D03, tay trái ở tiền cảnh trên trái ảnh.  
   Tạm gán thế nào và vì sao: Giữ side=left, on_wheel=unknown do chưa thấy rõ tiếp xúc; ghi ambiguous để trao đổi với Hạnh hoặc coach.
