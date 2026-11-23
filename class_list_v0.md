# Danh sách lớp v0 — Nguyễn Viết Quang · G02

Danh sách lớp dựa trên GUIDE Cabin v1.0 và chức năng DMS/OMS.

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | eye_state | open / closed / unknown | Phát hiện dấu hiệu buồn ngủ qua trạng thái mắt; `closed` mô tả khung hiện tại | Thường thấy trên NIR; kính, phản xạ hoặc che khuất có thể làm phải chọn `unknown` |
| 2 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Phát hiện tài xế nhìn khỏi đường hoặc nhìn sang vùng khác | Có thể suy từ mắt và hướng đầu; không chắc thì `other` |
| 3 | face13 | 13 điểm mặt; occluded / outside | Xác định vị trí mắt, mũi, miệng để hỗ trợ ước lượng trạng thái và hướng đầu | Một số điểm có thể khó thấy do góc mặt, che khuất hoặc phản xạ NIR |
| 4 | glasses | none / clear / sun / unknown | Nhận biết kính để diễn giải mắt đúng và tránh nhầm phản xạ với trạng thái mắt | Có thể nhận ra gọng; kính râm trên NIR có thể trông khác, nên dùng `unknown` khi không rõ |
| 5 | hand | whose=driver/passenger; side=left/right; on_wheel=yes/no/unknown | Theo dõi tay tài xế và việc tay có chạm vô lăng không | Thấy nếu tay không bị che; vật tối hoặc vùng khuất có thể làm khó phân biệt |
| 6 | phone | held / mounted / lap | Phát hiện hành vi dùng điện thoại khi lái xe | Thấy khi còn nhận ra hình dạng điện thoại; tay hoặc vùng tối có thể che máy |
| 7 | person / seatbelt | seat=driver; worn_correct / worn_incorrect / not_worn / unknown | Xác định tài xế và trạng thái thắt dây an toàn | Người thường nhận ra được; dây có thể khó thấy nếu tối, bị che hoặc chìm vào quần áo |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person / seat | driver / front_passenger / rear_left / rear_middle / rear_right | Xác định ghế nào có người để quản lý tình trạng cabin | Thường thấy hình dáng người; trái/phải ghế phải quy chiếu theo xe |
| 2 | person / seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Kiểm tra người ngồi có thắt dây đúng cách không | Dây có thể không rõ trên quần áo tối hoặc khi bị che |
| 3 | child_seat / occupied | no / unknown | Nhận diện ghế trẻ em và xác định bên trong có nhìn rõ ghế trống không | Hình dáng ghế thường thấy; phần bên trong có thể bị che; guideline không dùng `yes` |
| 4 | infant_seat / facing | rear / front | Nhận biết ghế em bé và hướng lắp để kiểm tra cách đặt ghế | Thường nhận ra được hình dáng và hướng; xác nhận theo phần ghế nhìn thấy |
| 5 | object / type | bag / box / cup / other | Nhận biết đồ vật để quản lý vật dụng trong cabin | Hình dáng thường còn thấy; màu sắc và chất liệu có thể mất trên IR |
| 6 | frame_meta / camera_blocked | yes / no | Phát hiện camera bị che để cảnh báo ảnh không đủ dùng | Thường thấy nếu vật che nằm trong vùng ảnh; cần xét trực tiếp khung hình |
| 7 | frame_meta / light | day / night / unknown | Ghi điều kiện ánh sáng để model hoặc hệ thống diễn giải ảnh phù hợp | IR không giữ thông tin màu; chọn `unknown` nếu không xác định được ngày/đêm |

## 2 câu hỏi leo thang

1. Câu hỏi: Với mắt phải khó quan sát trên ảnh NIR như D01, cần dấu hiệu nào đủ để phân biệt `closed` với `unknown`, nhất là khi các điểm `face13` bị che hoặc nằm ngoài vùng nhìn thấy?
   Khung ví dụ: D01.png
   Bạn tạm gán thế nào và vì sao: `unknown` nếu không nhìn rõ khe/mí; chỉ chọn `closed` khi thấy rõ mí khép.

2. Câu hỏi: Với `child_seat`, ranh giới nào giữa `occupied=no` và `unknown` khi một phần bên trong ghế bị che?
   Khung ví dụ: S03_ir.png
   Bạn tạm gán thế nào và vì sao: `no` nếu nhìn rõ ghế trống; `unknown` nếu không quan sát rõ bên trong; không dùng `yes` theo guideline v1.0.
