# 🧰 PO Kit: Skills & Templates cho Giai đoạn Research & Discovery

## 1. Quy tắc bắt buộc cho AI (PO Skills & Guardrails)
- **Không nhảy cóc:** Tuyệt đối không viết tính năng kỹ thuật (Requirements) khi chưa làm rõ Nhu cầu (Needs) và Khoảng trống thị trường (Market Gap).
- **Bài toán kinh doanh:** Mọi phân tích thị trường phải đi kèm mô hình kiếm tiền (Monetization).
- **Liên kết Vault (Second Brain):** Đầu mỗi file `.md` bắt buộc phải có khối `> **Liên kết ngữ cảnh:**` dẫn link tương đối (`./...` hoặc `../...`) tới các file liên quan trong Vault.
- **Trực quan hóa:** Bắt buộc sử dụng sơ đồ `Mermaid` (`quadrantChart`, `flowchart`, `journey`) trong các file để mô tả luồng.
- **Ánh xạ Persona sang UI:** Trong file Persona, bắt buộc phải có mục giải thích: Từ Độ tuổi, Giới tính, Tính cách và Pain Points này thì giao diện (Design System) cần thiết kế màu sắc, bố cục, cỡ chữ như thế nào.

## 2. Cấu trúc Biểu mẫu chuẩn (Templates)
- **File `01-market-and-needs.md`:** 1. User Needs -> 2. Market Gap (kèm Mermaid quadrantChart) -> 3. Monetization Model.
- **File `02-problem-statement.md`:** 1. Core Problem Statement -> 2. Impact (Hệ quả) -> 3. Sơ đồ nguyên nhân-hệ quả (Mermaid flowchart).
- **File `03-product-vision.md`:** Tuyên ngôn tầm nhìn theo khung Geoffrey Moore (For / Who / The Product / Unlike / Our Product) + 3 Product Goals.
- **File `04-product-canvas.md`:** Bảng Markdown gồm (Tên SP, Goals/KPIs, Target Personas, Key Pain Points, Core Solutions) + Sơ đồ `Mermaid journey`.
- **File `personas/*.md`:** 1. Demographics (Tuổi, giới tính, thiết bị) -> 2. Goals & Motivations -> 3. Habits -> 4. Pain Points -> 5. UI/UX Implications (Ánh xạ sang giao diện).