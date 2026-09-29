# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 7 | 4 | 0 | 2 | 4 | MISSING (4) |
| mid | 9 | 4 | 0 | 6 | 7 | MISSING (4) |
| edge | 4 | 1 | 0 | 1 | 1 | MISSING (1) |

## Nhận xét

- Zone người (L) và model (M) gãy nhiều nhất: Cả L và M đều ghi nhận nhiều lỗi nhất ở vùng mid (L missing 4, M missing 6 và M thừa 7). Vùng center cũng có 4 ca L missing và 4 ca M thừa. Vùng edge có ít vật thể tham chiếu hơn (n_ref=4) với 1 ca missing cho L và 1 missing, 1 thừa cho M.
- Giả thuyết nguyên nhân: Vùng mid và edge chịu ảnh hưởng của biến dạng quang học fisheye và nén phối cảnh khiến model YOLO chuẩn (huấn luyện trên ảnh pinhole COCO) bị giảm độ chính xác định vị hộp và nhận diện sai class (đặc biệt ThreeWheeler và Rider). Với L, các vật thể nhỏ ở hậu cảnh tiệm cận ngưỡng H=40 hoặc bị bóng râm/vật cản che khuất dễ bị bỏ sót. Giới hạn slice 3 frame chỉ cung cấp quan sát cục bộ, chưa đại diện cho toàn bộ điều kiện vận hành 4 camera SVM.
