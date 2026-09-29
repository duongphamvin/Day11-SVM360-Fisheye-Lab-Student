# Guideline patch

- **Rule mới đề xuất:** R12 — Tiêu chuẩn che khuất sâu và phân định cụm xe sạp hàng ven đường: Phương tiện đỗ trong sạp/mái hiên ven đường bị che khuất trên 70% diện tích hoặc không nhìn thấy rõ đặc trưng bánh xe/khung vỏ chính thì không gán bounding box riêng lẻ mà gộp vào polygon `ignore_region` với lý do `crowd_or_group`. Chỉ gán box độc lập nếu nhìn thấy tối thiểu 30% cấu trúc đặc trưng và xác định được ranh giới rõ ràng.
- **Áp dụng cho:** Các class `ThreeWheeler`, `Bike`, `Truck`, `Car` và polygon `ignore_region` tại khu vực ven đường/chợ phức tạp.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** Luật hiện hành R06 chỉ định nghĩa định tính "cụm vật không tách được từng cái", khiến annotator và QA có sự bất đồng khi gặp các xe ba bánh đỗ sâu trong lán sạp ở frame adasind_001320.jpg, dẫn đến các ca lỗi MISSING hoặc SPURIOUS mang tính chủ quan.
- **`rules_version` mới:** v1.1.0
- **Hiệu lực từ:** Vòng nghiệm thu kế hoạch gold set và chuẩn bị dữ liệu thử nghiệm 4 camera tiếp theo.
