# Quan sát vạch ô đỗ

- Sáu `parking_line` đã vẽ nằm trên các đoạn sơn trắng nhìn rõ ở hàng ô tiền cảnh và hàng giữa; mỗi polyline đi theo tim phần sơn tạo ranh giới giữa hai ô riêng, gồm các vạch lớn ở giữa/phải tiền cảnh và các vạch xiên rõ gần giữa ảnh.
- Không vẽ các đoạn sơn rất nhỏ ở hàng xa quanh xe đỏ và mép trên của bãi: phối cảnh làm chúng ngắn/mờ, chưa đủ chắc chắn để phân biệt ranh ô với mép hoặc dấu chỉ dẫn khác.
- Polygon `free_space` bao dải lối xe chạy trống giữa đầu trong của hàng ô giữa và đầu trong của hàng ô tiền cảnh. Polygon dừng tại hai hàng vạch, không bao xe đỏ, không kéo qua hàng ô đỗ và không mang nghĩa vùng lái xe tự hành an toàn.
- Ca chưa chắc cần hỏi người soát: các đoạn sơn hàng xa bị giảm kích thước do phối cảnh; hiện giữ ngoài phạm vi thay vì đoán.
