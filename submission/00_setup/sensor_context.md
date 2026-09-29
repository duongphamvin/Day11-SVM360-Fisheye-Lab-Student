# Sensor context

- Rig: dữ liệu ADASIND trong bài đến từ một camera fisheye hướng về phía trước, gắn trên phương tiện đang di chuyển. Ảnh chỉ cho phép nhận xét hướng nhìn và độ méo; không có tài liệu để suy ra độ cao, tiêu cự, ngoại chuẩn hoặc cấu hình SVM bốn camera.
- `ego_body`: trên ảnh quan sát, một phần phương tiện gắn camera xuất hiện ở đáy khung hình, rõ tại góc dưới và vùng bóng/thân xe gần mép dưới. Chỉ gán `ego_body` tại frame thật sự nhìn thấy phần xe; không suy thêm ở frame ngoại lệ.
- Vòng kính: vùng ảnh hữu dụng gần hình tròn/oval nằm giữa khung dọc; viền đen `lens_border` bao quanh ngoài vòng kính, rõ ở hai bên và phần trên/dưới. Vùng hữu dụng chiếm gần toàn bộ chiều rộng ở giữa nhưng không phủ hết bốn góc khung hình.
- Giới hạn: đây là dữ liệu một camera, không có timestamp đồng bộ, calibration, depth hay policy seam/cross-camera; không dùng vị trí `center/mid/edge` để suy khoảng cách hoặc rủi ro thực tế.
