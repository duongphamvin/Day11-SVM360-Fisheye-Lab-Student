# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** chọn 200 frame từ tình huống giả lập 50.000 frame của bốn camera SVM. Repo không chứa tập 50.000 frame; kế hoạch này không tuyên bố teaching reference ADASIND là gold set bốn camera.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | vật nhỏ xa, ngược sáng, bus/truck bị méo gần rìa | kích thước gần ngưỡng 40 px và glare làm thiếu box/sai class | ảnh fisheye gốc, lens circle, timestamp và calibration version | hai annotator làm độc lập; adjudicator kiểm ảnh gốc, R01–R09 và ca bất đồng |
| rear | vật rất gần, bị cắt biên, người/xe xuất hiện khi lùi | hình học thay đổi nhanh và `truncated` dễ lẫn `occluded` | camera ID rear, intrinsics/extrinsics và crop nguyên bản | review riêng thuộc tính, ignore region và ca đi vào/ra khỏi trường nhìn |
| left | pedestrian/bike sát xe, vật tại seam front-left/rear-left | méo radial lớn; cùng vật có thể xuất hiện ở camera kề | timestamp đồng bộ và vùng overlap theo calibration | review độc lập từng camera trước, sau đó adjudicate seam bằng timestamp/calibration |
| right | rider, ThreeWheeler, curb-side clutter và seam | class đặc thù dễ nhầm; người lái dễ bị tách thành Pedestrian + Bike | ảnh gốc, rule version và mapping R03/R04 | bắt buộc reviewer kiểm rider, class và box trong vùng edge |

- Refresh gold set khi đổi camera/lens/crop, thay intrinsics hoặc extrinsics, đổi `rules_version`, thay phân bố vận hành đáng kể, hoặc audit định kỳ phát hiện drift theo camera/zone/class.
- Ca seam cần policy: một Bike xuất hiện đồng thời ở `front-edge` và `right-edge`. Giữ hai box theo ảnh gốc cho tới khi timestamp, calibration và output policy xác nhận đó là cùng vật; chỉ sau đó mới ghép identity hoặc quyết định duplicate ở tầng đánh giá.
- Peer agreement hoặc quality report một camera chưa chứng minh gold set bốn camera đúng vì hai người có thể cùng hiểu sai luật, reference có thể lỗi, và một camera không kiểm được seam, đồng bộ hay khác biệt calibration của ba camera còn lại.
- Mỗi frame chỉ được gọi là gold sau hai nhãn độc lập, adjudication có decision log, kiểm tra artifact/lock, và xác nhận phiên bản ảnh-calibration-rule có thể truy vết.
