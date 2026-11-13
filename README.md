# 🧠 Product Knowledge Vault (AI-Native Second Brain)

> Kho lưu trữ tri thức tập trung (Single Source of Truth) cho dự án. Toàn bộ tài liệu được viết bằng Markdown & Mermaid và liên kết chéo với nhau để cung cấp ngữ cảnh chuẩn xác cho AI (chống Hallucination).

## 🗺️ Sơ đồ liên kết tri thức (Knowledge Graph)

```mermaid
graph TD
    A[01. Market & Needs] --> B[02. Problem Statement]
    B --> C[03. Product Vision]
    B --> D[Personas & Pain Points]
    C --> E[04. Product Canvas]
    D --> E
    D --> F[02. Design System & Prototype]
    E --> G[03. PRDs & User Stories]
    F --> G
    G --> H[04. Architecture & DB Schema]