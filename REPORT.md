# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202602193
- Ngày / CVAT local: 17/09/2026 / CVAT local
- Công cụ đã dùng: Polygon

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | `easy_semantic.zip` | 3 / 3 | 20 |
| medium_instance | `medium_instance.zip` | 3 / 3 | 32 |
| hard_panoptic | `hard_panoptic.zip` | 2 / 2 | 30 |
| cp1_holes | chưa có | 0 / 1 | 3 |
| cp2_slice | chưa có | 0 / 1 | 3 |
| cp5_occlusion | chưa có | 0 / 1 | 3 |
| cp3_thin | chưa có | 0 / 1 | 3 |
| cp4_curb | chưa có | 0 / 1 | 3 |
| cp6_coverage | chưa có | 0 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: `000000373353.jpg`, xe bus đỏ ở giữa ảnh.
- Class và quy tắc tôi dùng để chọn biên: `bus`; tôi dùng Polygon bám theo phần thân xe bus nhìn thấy. Các phần bị taxi và người đi bộ che khuất không được vẽ đoán thêm vào mask.
- Nếu dùng gợi ý sau đó: không dùng gợi ý tự động; tôi tự vẽ và kiểm lại biên bằng Polygon.
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `medium_instance` / `000000373353.jpg` / xe bus đỏ ở giữa ảnh, đoạn sát taxi vàng và người đi bộ phía trước.
- Lỗi thuộc loại: biên.
- Bằng chứng tôi nhìn thấy: khi kiểm lại ở vùng đáy xe bus, biên mask cần dừng tại phần thân xe còn nhìn thấy; taxi và người đi bộ phía trước không thuộc xe bus.
- Quy tắc và hành động sửa: tôi chỉnh lại các điểm Polygon ở vùng che khuất để mask chỉ bao phần xe bus nhìn thấy, không lấn sang taxi hoặc người đi bộ.
- Sau sửa đã Save và export lại chưa? Đã Save và export lại `medium_instance.zip`.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| `medium_instance` / `000000373353.jpg`, xe bus đỏ ở giữa ảnh | Vẽ cả hình xe bus hay chỉ phần còn thấy sau taxi và người đi bộ | Quy tắc chung là chỉ vẽ phần nhìn thấy, không đoán phần bị che khuất | Chỉ gán nhãn phần xe bus nhìn thấy; dừng biên ở chỗ bị taxi và người che |
| `easy_semantic` / `81ae7cbb-6bc63a4a.jpg`, mép đường bên phải ảnh | Vùng lát sát lề là `road` hay `sidewalk` | Ranh được xác định theo chức năng và mép bó vỉa, không chỉ theo màu bề mặt | Chọn `sidewalk` cho phần lề đi bộ nằm sau bó vỉa; phần xe chạy giữ là `road` |
| `hard_panoptic` / `000000460147.jpg`, dải cây phân cách ở giữa đường | Là `road` hay `vegetation` | Dải này có bụi cây trồng liên tục, tách khỏi mặt đường bằng kết cấu phân cách | Gán là `vegetation`; phần làn xe hai bên được gán `road` |
