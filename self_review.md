# Tự đánh giá — Hoàng Minh Hải · G09

## 1. Tự rà soát 4 cảnh

Đã rà 4 ảnh gồm 2 OMS và 2 DMS, có Codex hỗ trợ đối chiếu ảnh và file export của Nguyễn Thị Hồng Hạnh.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_ir | infant_seat.facing | guess | Bản trước gán rear; review theo xe và bản Hạnh xác định front. | Có, front trong v2 |
| S04_rgb | face | ok | Mặt người lớn nhìn thấy rõ, giữ box của mình dù peer thiếu. | Giữ nhãn đúng |
| D02 | hand trái | box | Hai box cũ cắt thiếu ngón hoặc cổ tay; sửa về 541,465–645,614. | Có, trong v2 |
| D06 | face.eye_left, face13 | flag | Khe mắt trái đọc được; theo peer sửa open và tắt outside ở 4 điểm mắt trái. | Có, trong v2 |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Dùng unknown/outside quá rộng ở vùng có thể đọc được sau phóng to; một số box tay chưa sát ngón và cổ tay.

Vì sao mình mắc: Lượt gán đầu chưa soi đủ chi tiết mặt/tay và có trường hợp giữ giá trị mặc định hướng nôi mà chưa kiểm theo xe.

Lần sau tránh bằng cách: Rà riêng từng mắt, mép mí và đầu ngón; chỉ đặt điểm khi đủ căn cứ. Xác định hướng ghế theo chiều xe, phân biệt kiểm tra schema với kiểm tra nội dung ảnh.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó: S01_ir, infant_seat.facing, bản Hạnh là front còn bản trước của mình là rear. Đã sửa front sau đối chiếu hướng theo xe, không suy hướng lắp từ tên loại ghế.

Đã rà 76 dòng, có 46 mine, 19 peer, 2 both_wrong và 9 ambiguous. Bản sau sửa export_final_v2.zip đủ 22 ảnh, checker 0 lỗi, 0 cảnh báo. Log A/B được chạy theo phạm vi trên export đầy đủ, sau lượt gán.
