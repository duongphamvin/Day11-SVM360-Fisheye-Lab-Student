# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B1 | BOX_GEOMETRY | 1 |
| center | B1 | MISSING | 9 |
| center | B1 | SPURIOUS | 4 |
| center | C0 | SPURIOUS | 1 |
| edge | B1 | BOX_GEOMETRY | 1 |
| edge | B1 | MISSING | 3 |
| edge | B1 | SPURIOUS | 1 |
| mid | B1 | ATTRIBUTE | 1 |
| mid | B1 | MISSING | 10 |
| mid | B1 | SPURIOUS | 7 |

## Top defects
- MISSING: 22 (ví dụ frame adasind_001320.jpg)
- SPURIOUS: 13 (ví dụ frame adasind_019560.jpg)
- BOX_GEOMETRY: 2 (ví dụ frame adasind_001320.jpg)

## Phân tích của bạn

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: Lỗi nổi bật nhất là MISSING (22 ca) và SPURIOUS (13 ca). Với MISSING, nguyên nhân chính là E1_annotator_error do người gán nhãn bỏ sót các vật thể kích thước nhỏ ở trung tâm và hậu cảnh (ví dụ Truck R1 và Pedestrian R4 trên frame adasind_001320.jpg do nằm xen kẽ trong khu vực cửa hàng phức tạp). Bên cạnh đó có ca E0_reference_defect khi ground truth đánh nhãn vật quá mờ. Với SPURIOUS, phần lớn là E4_model_domain do mô hình YOLO COCO đóng băng sinh nhiều box ảo do biến dạng hình học fisheye và bóng đổ.
- Cách sửa và ai nhận việc (`owner`): Với ca annotator bỏ sót (owner: annotator), thực hiện rework bổ sung hộp bám sát đối tượng nhìn thấy H>=40px theo R01. Với ca model domain (owner: ai_team), cần bổ sung dữ liệu huấn luyện fisheye và radial distortion augmentation. Với ca nghi vấn guideline/reference (owner: data_ops), rà soát tiêu chí đánh nhãn vật bị che khuất sâu.
- Bằng chứng: Dòng findings adasind_001320.jpg R1+M2 và R4+M1 (round r3_diag) đã được đối chiếu, phân loại và sửa hoàn chỉnh trong đợt rework (thể hiện qua delta.md tăng từ 3 lên 4 matched ở center và edge). Ảnh minh chứng lưu tại submission/screenshots/c0_fisheye_detection_overlay.jpg và báo cáo local_quality.md.
