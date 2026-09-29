# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| Vùng mid (r/R 0.35–0.60, frame adasind_001320, 014670, 034080) | 10 ca MISSING, 7 ca SPURIOUS | Vùng tập trung đa số đối tượng di chuyển phức tạp và bắt đầu chịu méo góc; tỷ lệ xung đột giữa model và người cao nhất. | Bảng đối chiếu r3_diag/model_compare.html, zone_table.md và các finding round r3_diag. |
| Vùng edge (r/R ≥ 0.60, frame adasind_001320, 014670) | 3 ca MISSING, 1 ca SPURIOUS, 1 ca BOX_GEOMETRY | Độ méo cực đại làm biến dạng đối tượng, dễ vi phạm cắt biên vòng kính (truncated) và tiếp giáp ego_body. | Tọa độ tâm/bán kính frames.csv, thuộc tính truncated/edge_zone và ảnh chụp screenshots. |

Giới hạn của kết luận từ ba frame ADASIND: Bộ dữ liệu chỉ gồm 3 frame trên một camera trước duy nhất tại một khung cảnh giao thông Ấn Độ ban ngày; không đại diện cho các điều kiện ban đêm, thời tiết xấu, thiếu góc nhìn 3 camera còn lại và không thể kiểm chứng hiện tượng trùng vật ở vùng seam nối ảnh.

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv` (kể cả tránh đếm nhiều frame liền nhau trong cùng cảnh như nhiều ca độc lập), và vì sao kế hoạch đó chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi: Cần áp dụng lấy mẫu phân tầng kết hợp khoảng cách thời gian (strided sampling tối thiểu cách nhau 30–60 frame) để tránh hiện tượng correlation giữa các frame liên tiếp. Kế hoạch này nhắm vào các ca khó (hard cases) để phát hiện lỗ hổng góc khuất và ranh giới quy chuẩn, không phải lấy mẫu ngẫu nhiên đồng nhất (IID), do đó chỉ dùng để khoanh vùng ca cần audit chứ không đo lường tỷ lệ lỗi tổng thể trên 50.000 frame.
