# Đối chiếu chất lượng cục bộ — rectangle

Teaching reference, không phải gold set đã phê duyệt; không có điểm đạt tự động.
Nguồn: export r1_craft đã khóa SHA256 `0503dac0deb4755886fee5865b913dd31cc1245c890bc0b6398bab71f8970408`; slice `B1-edge`.
Ghép hình học greedy một-một theo IoU ≥ 0.50, rồi so class; H ≥ 40 px.
Box trái nằm chủ yếu trong ignore_region reference không tính. Polygon, polyline, track không được chấm.
Đây là phép tính offline của lab, không phải báo cáo hay kết quả tương đương CVAT Premium.

Frame được tính: adasind_001320.jpg, adasind_014670.jpg, adasind_034080.jpg. Frame thiếu trong export: không.
TP=11; FP=0; FN=9; số lần đối chiếu=20; mean IoU của TP=0.951.

| Chỉ số | Micro | Macro | Nhãn thấp nhất |
|---|---:|---:|---:|
| accuracy | 0.550 | 0.910 | 0.850 |
| precision | 1.000 | 1.000 | 1.000 |
| recall | 0.550 | 0.537 | 0.333 |
| jaccard | 0.550 | 0.537 | 0.333 |
| dice | 0.710 | 0.688 | 0.500 |

| Nhãn | TP | FP | FN | Accuracy | Precision | Recall | Jaccard | Dice |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Bike | 1 | 0 | 2 | 0.900 | 1.000 | 0.333 | 0.333 | 0.500 |
| Car | 3 | 0 | 1 | 0.950 | 1.000 | 0.750 | 0.750 | 0.857 |
| Pedestrian | 3 | 0 | 2 | 0.900 | 1.000 | 0.600 | 0.600 | 0.750 |
| ThreeWheeler | 3 | 0 | 3 | 0.850 | 1.000 | 0.500 | 0.500 | 0.667 |
| Truck | 1 | 0 | 1 | 0.950 | 1.000 | 0.500 | 0.500 | 0.667 |

| Frame | TP | FP | FN | Accuracy | Precision | Recall |
|---|---:|---:|---:|---:|---:|---:|
| adasind_001320.jpg | 3 | 0 | 3 | 0.500 | 1.000 | 0.500 |
| adasind_014670.jpg | 3 | 0 | 2 | 0.600 | 1.000 | 0.600 |
| adasind_034080.jpg | 5 | 0 | 4 | 0.556 | 1.000 | 0.556 |

Confusion matrix: hàng = teaching reference; cột = export đã khóa.
`<missing>` là thiếu box; `<extra>` là box thừa. Xem `local_quality_confusion.csv`.

| Reference \ Export | Bike | Car | Pedestrian | ThreeWheeler | Truck | <missing> |
|---|---:|---:|---:|---:|---:|---:|
| Bike | 1 | 0 | 0 | 0 | 0 | 2 |
| Car | 0 | 3 | 0 | 0 | 0 | 1 |
| Pedestrian | 0 | 0 | 3 | 0 | 0 | 2 |
| ThreeWheeler | 0 | 0 | 0 | 3 | 0 | 3 |
| Truck | 0 | 0 | 0 | 0 | 1 | 1 |
| <extra> | 0 | 0 | 0 | 0 | 0 | 0 |

Chi tiết xung đột trong `local_quality_conflicts.csv`; dữ liệu máy đọc trong `local_quality.json`.
Mismatching label đóng góp một FP cho class vẽ và một FN cho class reference; attribute khác được báo riêng.
Micro accuracy đếm mỗi cặp ghép sai class là một lần đối chiếu; Jaccard đếm cả FP và FN.
Macro/worst bỏ nhãn không xuất hiện ở cả hai phía; chỉ số không có mẫu là N/A.
