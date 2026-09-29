# Escalation ticket

## Ticket 1

- **Frame:** adasind_001320.jpg
- **Ảnh chụp:** submission/screenshots/c0_fisheye_detection_overlay.jpg
- **Expected impact:** Sai lệch chỉ số đánh giá độ khớp (mAP, IoU) giữa mô hình/người gán nhãn với bộ dữ liệu tham chiếu; gây tranh cãi kéo dài trong các đợt soát chéo QA và làm giảm độ tin cậy của bộ dữ liệu chuẩn vàng (gold set) SVM 360.
- **Owner:** guideline
- **Recommendation:** Chuyên gia dữ liệu và đội ngũ xây dựng guideline cần tái thẩm định đối tượng R5 trên frame adasind_001320.jpg để xác định rõ đối tượng này có đủ điều kiện gán nhãn ThreeWheeler hay nên chuyển sang vùng bỏ qua ignore_region với lý do crowd_or_group / unreadable theo đề xuất quy chuẩn v1.1.0.
