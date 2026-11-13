# 🐎 Nhật ký Điều phối & Kiểm soát AI (AI Harness Log)

Tài liệu này ghi lại cách nhóm sử dụng các bộ Kit/Prompt và quá trình con người kiểm duyệt, chỉnh sửa (Human-in-the-loop) ở từng bước.

## Giai đoạn 1: Research & Discovery

| Tài liệu đầu ra | Công cụ / Kit sử dụng | Prompt / Input đầu vào của nhóm | Điểm AI làm chưa tốt (Hallucination / Chung chung) | Cách nhóm đã ghìm cương & sửa lại (Human Review) |
| :--- | :--- | :--- | :--- | :--- |
| [Problem Statement](../01-discovery/02-problem-statement.md) | Claude + PO Kit | *(Dán câu lệnh nhóm đã dùng vào đây)* | Ví dụ: AI ban đầu liệt kê vấn đề quá rộng, thiếu góc nhìn về bài toán doanh thu tại thị trường Việt Nam. | Nhóm đã yêu cầu AI thu hẹp tệp khách hàng vào nhóm tuổi 18-24 và bổ sung phân tích đối thủ cạnh tranh trực tiếp. |
| [Persona 1](../01-discovery/personas/persona-01-student.md) | Claude + Survey Data | *(Dán câu lệnh nhóm đã dùng vào đây)* | Ví dụ: AI tự bịa ra thói quen học tập không sát với kết quả khảo sát thực tế của nhóm. | Đối chiếu với dữ liệu khảo sát, cập nhật lại đúng Pain Point về giao diện và thời gian học. |