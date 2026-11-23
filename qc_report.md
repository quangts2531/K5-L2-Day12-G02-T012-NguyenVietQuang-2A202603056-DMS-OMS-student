# Báo cáo QC — DMS/OMS

## Phạm vi

Kiểm tự động `export_final.zip` bằng `scripts/cabin_check.py`, giới hạn vào 22 ảnh cốt lõi (`S01`–`S08`, `D01`–`D06`), và tổng hợp kết quả `cabin_check diff` đã cung cấp. Báo cáo này không đánh giá trực quan ảnh cabin.

## Kết quả kiểm tự động

- Đủ 22 ảnh cốt lõi; cả 22 ảnh có `frame_meta`.
- `cabin_check`: **0 lỗi, 0 cảnh báo**.
- Bản export/diff có thêm `S09` và `S10` (4 ảnh mở rộng); chúng không thuộc phạm vi 22 ảnh cốt lõi.

## Review chéo

- Lần diff mới nhất có 30 dòng; 4 dòng `S09/S10` là ảnh mở rộng ngoài phạm vi, còn 26 sai khác thuộc 22 ảnh chính.
- Các sai khác box `person` ở D01–D06 đã biến mất khỏi diff mới nhất.
- CSV đã được điền verdict, guideline và action cho 9 dòng `child_seat.occupied`.
- Ở 9 dòng đó, `mine=no` phù hợp GUIDE §4.8; `occupied=yes` không phải giá trị hợp lệ.
- 17 sai khác chính còn lại cần review trực tiếp trong CVAT: `frame_meta.light` ở D01–D06; `gaze_zone` và cờ `face13` ở D01; cờ `face13` ở D04; `person.seatbelt` ở D06; cùng `seat` của `person` và `infant_seat` ở S01_rgb.
- 4 dòng chỉ có `S09/S10` là khác phạm vi ảnh mở rộng, không tính là bất đồng nhãn trong 22 ảnh cốt lõi.

## Tình trạng hồ sơ nộp

Trong thư mục dự án hiện có `export_final.zip`, `check_final.txt` và `disagreement_log.csv`. Các file `check_cpA.txt`, `check_cpB.txt`, `ir_log.csv`, `class_list_v0.md`, `self_review.md`, `exit_ticket.md`, `TEAM.md` và `prompts.md` chưa thấy ở thư mục chính; hiện chỉ có các template tương ứng.

## Kết luận

Kiểm tự động trên 22 ảnh cốt lõi đạt yêu cầu. QC review chéo và hồ sơ nộp **chưa hoàn tất**: cần phân xử các sai khác còn lại bằng cách xem ảnh trong CVAT và hoàn thiện các file bằng chứng còn thiếu. Nếu chỉnh nhãn, sửa trong CVAT, export lại rồi chạy kiểm cuối lần nữa.
