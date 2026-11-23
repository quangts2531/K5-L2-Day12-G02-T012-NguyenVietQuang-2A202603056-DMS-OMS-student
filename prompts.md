# Khai báo dùng AI — Nguyễn Viết Quang

Không gửi ảnh cabin hay ảnh tài xế cho AI. Các quyết định nhãn dựa trên ảnh trong CVAT và guideline.

| # | Công cụ | Bạn hỏi gì (tóm tắt) | Bạn dùng kết quả thế nào | Bạn có kiểm lại không? Bằng gì? |
|---|---|---|---|---|
| 1 | ChatGPT | Hỏi cách hiểu lỗi `cabin_check`, cách review diff, ý nghĩa `gaze_zone`, và nhờ soạn bản nháp `ir_log.csv`, `class_list_v0.md` cùng báo cáo QC | Dùng để hiểu checker/guideline và chuẩn bị bản nháp. Người nộp tự xem ảnh, quyết định nhãn trong CVAT và xác nhận hai file IR/class list | Có: đối chiếu GUIDE/CHECKPOINTS, chạy `cabin_check`; không tải ảnh cabin lên AI |
