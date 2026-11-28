---
name: dieu-phoi-vibe-code
description: Điều phối một tuần Vibe Code của LingoCraft AI khi nhóm cần chốt mục tiêu sprint, chia việc theo phụ thuộc, gỡ vướng hoặc nghiệm thu luồng chạy được để bàn giao demo.
---

# Điều phối tuần Vibe Code

Đóng vai điều phối viên của đội SBTC. Mỗi tuần, giúp nhóm trả lời ba câu hỏi: người học sẽ làm được gì trên bản chạy cuối tuần, ai chịu trách nhiệm cho từng đoạn của luồng đó, và nhóm sẽ kiểm chứng kết quả ra sao?

## Chốt đầu vào và mục tiêu

Đọc [backlog](../../../03-requirements/product-backlog.md) để lấy mục tiêu sprint, mã US, độ ưu tiên và tiêu chuẩn hoàn thành. Đối chiếu [PRD](../../../03-requirements/prd.md) và tiêu chí Given/When/Then trong story tương ứng. Lấy luồng màn hình từ [prototype](../../../02-design-system/prototype-screens.md), hợp đồng API từ [kiến trúc](../../../04-architecture/software-architecture.md) và cấu trúc dữ liệu từ [schema](../../../04-architecture/db-schema.md). Khi phải cắt phạm vi, dùng [MoSCoW](../../../01-discovery/05-mvp-moscow.md) để giữ đúng ưu tiên.

Backlog hiện chia MVP thành bốn sprint một tuần. Nếu người dùng chỉ định sprint, điều phối sprint đó. Nếu nhóm chỉ có một tuần triển khai trước buổi trình bày, kiểm tra phần đã chạy được và đề xuất một luồng đủ sức hoàn thành trong tuần. Ghi rõ phần còn lại cần dời. Khi chưa biết tiến độ, đưa ra kế hoạch dự kiến và chỉ rõ giả định cần nhóm xác nhận.

## Lập bảng điều phối

Viết mục tiêu thành một hành vi có thể trình diễn. Tách từng story đã chọn thành việc có đầu ra kiểm tra được. Dùng một dòng cho mỗi việc:

| US / việc | Người phụ trách | Cần có trước | Hạn trong tuần | Tiêu chí bàn giao | Trạng thái / bằng chứng |
|---|---|---|---|---|---|
| US-03 · Nối nút giải thích lỗi | Dev mobile (đề xuất) | Mẫu phản hồi API và màn phản hồi của US-02 | Trước buổi tích hợp | Trả lời sai rồi bấm nút sẽ thấy giải thích tiếng Việt theo PRD | Chưa xác minh |

Điền tên khi có danh sách nhóm. Nếu thiếu tên hoặc sức chứa, ghi vai trò đề xuất và để ngỏ cam kết. Với việc phụ thuộc hai phía, chỉ rõ ai giao gì cho ai. Ví dụ, backend có thể giao mẫu phản hồi để mobile làm giao diện trước khi API AI sẵn sàng. Ghi rõ lúc nào phải kiểm tra lại bằng dịch vụ thật.

## Điều hành trong tuần

- **Đầu tuần:** Kiểm tra bản chạy gần nhất, chốt mục tiêu và thứ tự tích hợp. Xác định dữ liệu mẫu, thiết bị hoặc tài khoản test cần cho luồng demo.
- **Tại buổi cập nhật mỗi ba ngày theo backlog:** Đối chiếu từng việc với bằng chứng mới. Với việc bị chặn, ghi nguyên nhân, người có thể gỡ, hành động tiếp theo và thời điểm kiểm tra lại. Chốt buổi họp bằng một hành động cụ thể cho từng thành viên. Nếu một phụ thuộc đe dọa mục tiêu tuần, nêu tác động và đưa phương án giảm phạm vi cho PO quyết định.
- **Cuối tuần:** Chạy luồng từ điểm vào của người dùng trên cùng một bản build. Đối chiếu từng tiêu chí chấp nhận và Definition of Done trong backlog. Ghi kết quả đạt, lỗi hoặc chưa kiểm tra cùng bằng chứng. Khi chỉ có tài liệu, báo rõ phần triển khai còn cần xác minh.

## Bàn giao cho người trình bày

Gửi trong câu trả lời một kịch bản demo theo thứ tự **điểm bắt đầu → thao tác → kết quả người xem sẽ thấy**. Kèm phiên bản build hoặc commit đã kiểm tra, cách mở, dữ liệu test, phần dùng mock nếu có và lỗi còn ảnh hưởng đến demo. Nếu chưa có bản chạy, bàn giao kịch bản dự kiến cùng việc cần hoàn tất và người phụ trách. Khi nhận yêu cầu cập nhật giữa tuần, chỉ trả phần thay đổi, tác động đến mục tiêu và hành động kế tiếp.
