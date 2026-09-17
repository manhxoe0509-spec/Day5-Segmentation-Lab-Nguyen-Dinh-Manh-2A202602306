# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202602306
- Ngày / CVAT local: 17/09/2026
- Công cụ đã dùng: CVAT và notebook tự kiểm `day5-segmentation-tu-kiem.ipynb`; notebook không lưu lại chính xác tên công cụ vẽ đã dùng.

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | `easy_semantic.zip` | 3 / 3 |  |
| medium_instance | `medium_instance.zip` | 3 / 3 |  |
| hard_panoptic | `hard_panoptic.zip` | 2 / 2 |  |
| cp1_holes | `cp1_holes.zip` | 1 / 1 |  |
| cp2_slice | `cp2_slice.zip` | 1 / 1 |  |
| cp5_occlusion | `cp5_occlusion.zip` | 1 / 1 |  |
| cp3_thin | `cp3_thin.zip` | 1 / 1 |  |
| cp4_curb | `cp4_curb.zip` | 1 / 1 |  |
| cp6_coverage | `cp6_coverage.zip` | 1 / 1 |  |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: Notebook không ghi lại thông tin này nên tôi không thể xác minh ảnh/vị trí từ file export.
- Class và quy tắc tôi dùng để chọn biên: Tôi cần bổ sung thủ công theo ghi chú trong CVAT; không suy đoán từ JSON/ZIP.
- Nếu dùng gợi ý sau đó: Notebook không ghi nhận việc dùng gợi ý hay hành động với gợi ý.
- Nếu không dùng gợi ý: Chưa có ghi chú đủ cụ thể trong notebook để xác nhận.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `medium_instance`, toàn bộ export Medium.
- Lỗi thuộc loại: sai lớp.
- Bằng chứng tôi nhìn thấy: lần kiểm trước báo các category không thuộc task là `building`, `road`, `sidewalk`, `sky`, `vegetation`; task Medium chỉ cho phép `person`, `bicycle`, `car`, `motorcycle`, `bus`, `truck`.
- Quy tắc và hành động sửa: Mở lại task Medium trong CVAT, loại các nhãn semantic bị lẫn, Save và export lại đúng format COCO 1.0.
- Sau sửa đã Save và export lại chưa? Đã. Lần kiểm mới nhất báo `medium_instance: OK`, 72 annotation polygon.

 Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): đã tự chạy `scripts/inspect_submissions.py`; Medium chuyển từ `LỖI` sang `OK`, chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| `hard_panoptic`, vùng vật bị che | Chỉ gán phần nhìn thấy / suy đoán toàn bộ vật phía sau vùng che | Hướng dẫn notebook yêu cầu chỉ kiểm phần nhìn thấy và xem lại chồng lấn trong CVAT | Tôi chọn phần nhìn thấy; cần coach xác nhận các ranh bị che nếu còn mơ hồ. |
| `cp2_slice`, hai xe sát nhau | Một mask chung / hai instance riêng | Hai vật cùng lớp nhưng có khe hoặc đường biên riêng phải là hai instance | Tôi chọn tách thành hai instance; cần đối chiếu lại trên ảnh gốc nếu khe giữa hai xe không rõ. |
| `cp4_curb`, mép bó vỉa | Road / sidewalk | Phân lớp theo chức năng vùng, không chỉ theo màu ảnh; notebook không lưu quyết định chi tiết | Tôi chọn theo chức năng bề mặt quan sát được; cần coach xác nhận ranh tại vùng màu gần giống nhau. |
