# Tự đánh giá — Nguyễn Viết Quang · G02

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S03_ir.png | child_seat / occupied | ok | Giữ `no`; `yes` không hợp lệ theo GUIDE §4.8 | Không cần sửa |
| S04_rgb.png | child_seat / occupied | ok | Giữ `no`; `yes` không hợp lệ theo GUIDE §4.8 | Không cần sửa |
| D02.png | person box | box | Ban đầu box sai khác/IoU thấp; sau chỉnh không còn trong diff mới | Có |
| D01.png | face/face13: eye_right, gaze_zone, điểm mắt phải | flag | Còn bất đồng; được giữ theo quyết định người nộp | Không, chấp nhận |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Box person ở các ảnh DMS ban đầu sai khác với peer.

Vì sao mình mắc: Chưa đối chiếu kỹ độ phủ box trên phần cơ thể nhìn thấy trước khi review chéo.

Lần sau tránh bằng cách: Soát từng ảnh D01–D06 trong CVAT, kiểm cả box và thuộc tính trước khi export.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó: D02 `person` box ban đầu sai khác/IoU thấp; sau review mình chỉnh lại để ôm phần cơ thể tài xế nhìn thấy.
