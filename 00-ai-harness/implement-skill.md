---
name: vibe-code-implement
description: Triển khai user story hoặc sprint của LingoCraft AI trong repo ứng dụng, theo dõi từng task và nghiệm thu theo Gherkin.
version: 1.1.0
project: LingoCraft AI
team: SBTC (VKU)
owner_role: Development Team
phase: Vibe Code
---

# Skill triển khai Vibe Code · LingoCraft AI

Khi được giao một story hoặc sprint, hãy sửa mã nguồn ứng dụng, chạy thử từ điểm vào của người học và bàn giao bằng chứng cho từng tiêu chí nghiệm thu (AC). Tiếp nhận mã US, phạm vi, repo ứng dụng và các ràng buộc trong lời giao việc. Nếu đang tiếp tục công việc dở, đối chiếu thay đổi hiện có và kết quả kiểm tra gần nhất trước khi chọn task tiếp theo.

## 1. Nhận bàn giao từ các skill của nhóm

| Quyết định cần đưa ra | Nguồn để quyết định |
|---|---|
| Người học cần đạt điều gì? Phần nào thuộc MVP? | Dùng [skill PO](./skill.md) và [PO Kit](./po-kit.md) khi cần làm rõ mục tiêu. Lấy phạm vi đã chốt từ [MVP MoSCoW](../01-discovery/05-mvp-moscow.md). |
| Story thuộc sprint nào và hành vi nào đủ để nghiệm thu? | Theo [skill BA](./ba-skill.md), tra mã US trong [backlog](../03-requirements/product-backlog.md), mở story ở cột chi tiết và đối chiếu FR trong [PRD](../03-requirements/prd.md). US-06 đến US-08 dùng tài liệu chi tiết liên kết từ backlog. |
| Người học thao tác ở đâu? | Theo [skill UI/UX](./ui-ux-skill.md), đối chiếu [prototype](../02-design-system/prototype-screens.md), dùng đúng [component](../02-design-system/component-library.md) và [token](../02-design-system/design-tokens.md). Giữ một câu hỏi trên mỗi màn hình bài học. |
| Luồng cần API và dữ liệu nào? | Tra endpoint trong [kiến trúc](../04-architecture/software-architecture.md), thực thể trong [schema](../04-architecture/db-schema.md), rồi tìm phần tương ứng trong mã nguồn thực tế. |

Nếu yêu cầu và prototype dẫn đến hai hành vi khác nhau, nêu mã US/AC, mô tả khác biệt có thể quan sát và chuyển đúng câu hỏi cho BA hoặc UI/UX. Tiếp tục các task độc lập trong lúc chờ quyết định.

## 2. Kiểm tra trước khi triển khai

- Xác định đường dẫn Knowledge Vault và repo ứng dụng. Trong repo app, tìm điểm vào Expo/React Native, package manager, script chạy app/test và backend đang dùng. Nếu mới có Vault, vẫn phân tích được story và chia task; hỏi vị trí mã nguồn trước khi bắt đầu sửa code. Chỉ khởi tạo app khi đó là phần việc được giao.
- Đọc checklist review nếu nhóm đã có. Báo mục còn mở và AC bị ảnh hưởng. Giữ dấu duyệt của reviewer nguyên trạng. Nếu một mục là điều kiện bàn giao bắt buộc, chờ quyết định cho phần phụ thuộc.
- Xác định cách tái hiện luồng ban đầu, dữ liệu test và dịch vụ cần có. Với tích hợp AI, kiểm tra cấu hình ở backend và giữ khóa dịch vụ phía server.

## 3. Chia task và thực thi

Dùng danh sách task của sprint nếu có. Nếu chưa có, lập danh sách ngắn ngay trong phiên từ các AC. Mỗi task ghi **ID, AC liên quan, phần mã cần sửa, phụ thuộc và cách kiểm tra**. Dùng đường dẫn thực tế sau khi đã xem repo. Vault cung cấp đầu vào trực tiếp cho quy trình này; nhóm có thể bắt đầu từ backlog và story mà không cần cài Spec Kit.

Ví dụ triển khai [US-03 · Giải thích lỗi sai bằng AI](../03-requirements/user-stories/us-03-ai-error-explanation.md):

| Task | Việc cần làm | Phụ thuộc và phép kiểm tra |
|---|---|---|
| T1 · AC-01 | Nối trạng thái trả lời sai của US-02 với FeedbackBottomSheet và nút giải thích. | Chạy từ màn hình bài học, nộp đáp án sai, kiểm tra đáp án đúng và nút AI xuất hiện. |
| T2 · AC-02 | Hiện thực hoặc tái sử dụng endpoint giải thích theo hợp đồng API. | Có thể làm cùng thời điểm với T1 khi đã thống nhất dữ liệu gửi/nhận. Thử bằng một cặp đáp án sai/đúng đã biết. |
| T3 · AC-02, AC-03 | Nối nút với API, xử lý lúc chờ, thành công và lỗi. | Sau T1 và T2, bấm nút trên app, kiểm tra giải thích tiếng Việt tối đa 4 dòng ở cỡ chữ quy định. Ngắt mạng và xác nhận vẫn bấm được “Tiếp tục”. Kiểm tra hết lượt nếu chính sách hạn mức đang áp dụng. |

Thực hiện task theo thứ tự phụ thuộc. Với lỗi đã tái hiện được, dùng một phép thử thể hiện lỗi trước khi sửa nếu khả thi. Với thay đổi liên quan đến tiến độ, XP hoặc Tim, thử gửi lại cùng thao tác để phát hiện ghi nhận hai lần. Với luyện phát âm, thử cả tình huống người học từ chối quyền micro.

Sau mỗi task, chạy phép kiểm tra đã ghi. Đánh dấu `[x]` trong danh sách task triển khai khi đã có kết quả xác nhận. Nếu một task lỗi, giữ nó mở, ghi cách tái hiện và thử sửa trước khi chạy lại. Task phụ thuộc chờ kết quả; các task độc lập có thể tiếp tục. Nếu dùng dữ liệu mẫu để phát triển giao diện, ghi rõ phép thử nào còn cần dịch vụ thật.

## 4. Nghiệm thu và bàn giao

Chạy các script kiểm tra liên quan của repo rồi đi qua toàn bộ luồng trên cùng bản build. Đối chiếu từng Given/When/Then và Definition of Done trong backlog. Với yêu cầu lưu tiến độ, mở lại ứng dụng để kiểm tra; với yêu cầu độ trễ, ghi thời gian đo và điều kiện thử.

Bàn giao **mã US, thay đổi người học nhìn thấy, phiên bản đã thử, cách mở luồng** và một dòng cho mỗi AC theo mẫu **AC | Đạt / Chưa đạt / Chưa kiểm tra | Bằng chứng hoặc lỗi còn lại**. Chỉ báo story hoàn tất khi các task bắt buộc đã xong và có bằng chứng cho các AC. Khi nhóm yêu cầu cập nhật [nhật ký AI Harness](./prompts-and-reviews.md), ghi lỗi AI thực sự gặp, phản hồi review thực tế và cách đã sửa.

**Cách gọi trong IDE:** “Đọc implement-skill.md. Triển khai US-03 trong repo ứng dụng đang mở, dùng luồng làm bài của US-02 và bàn giao kết quả AC-01 đến AC-03.”
