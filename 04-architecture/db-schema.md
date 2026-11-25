> **Liên kết ngữ cảnh:** [Software Architecture](./software-architecture.md) | [PRD Chính thức](../03-requirements/prd.md) | [Product Backlog](../03-requirements/product-backlog.md) | [US-01](../03-requirements/user-stories/us-01-auth-and-onboarding.md) | [US-05](../03-requirements/user-stories/us-05-gamification-streak-xp-hearts.md)

# 🗄️ Lược đồ Cơ sở Dữ liệu (Database Schema — `LingoCraft AI`)

> **Mục tiêu:** Thiết kế lược đồ PostgreSQL tinh gọn phục vụ đầy đủ các yêu cầu MVP (`US-01`..`US-05` và `US-06`..`US-08`) trong **4 tuần Vibe Code**.

---

## 1. Sơ đồ Quan hệ Thực thể (Entity Relationship Diagram — Mermaid)

```mermaid
erDiagram
    USERS ||--o{ USER_PROGRESS : "hoan thanh"
    USERS ||--o{ STREAK_LOGS : "duy tri"
    USERS ||--o{ AI_EXPLANATION_LOGS : "yeu cau"
    USERS ||--o{ FRIEND_CHALLENGES : "tham gia"
    LEARNING_TRACKS ||--|{ LESSONS : "gom"
    LESSONS ||--|{ QUESTIONS : "chua 5-8 cau"
    LESSONS ||--o{ USER_PROGRESS : "duoc hoc"
    QUESTIONS ||--o{ AI_EXPLANATION_LOGS : "phat sinh"

    USERS {
        uuid id PK
        string email UK
        string password_hash
        string display_name
        string target_track "a1-daily | toeic-b1 | office"
        int xp_total
        int streak_current
        int hearts_current "Mac dinh 5"
        boolean is_pro "Goi LingoCraft Pro"
        string reminder_time "VD: 21:00"
        timestamp created_at
    }

    LEARNING_TRACKS {
        uuid id PK
        string code UK "a1-daily | toeic-b1 | office"
        string title
        string level "A1-A2 | TOEIC-B1"
    }

    LESSONS {
        uuid id PK
        uuid track_id FK
        string title
        int order_index
        int estimated_minutes "5-10 phut"
    }

    QUESTIONS {
        uuid id PK
        uuid lesson_id FK
        string question_type "mcq | fill_blank | pronunciation"
        string prompt_text
        string correct_answer
        jsonb options_json
    }

    USER_PROGRESS {
        uuid id PK
        uuid user_id FK
        uuid lesson_id FK
        int score_percent
        int xp_earned
        timestamp completed_at
    }

    STREAK_LOGS {
        uuid id PK
        uuid user_id FK
        date study_date
        int xp_day
    }

    AI_EXPLANATION_LOGS {
        uuid id PK
        uuid user_id FK
        uuid question_id FK
        string user_answer
        text ai_vietnamese_explanation
        timestamp created_at
    }

    FRIEND_CHALLENGES {
        uuid id PK
        uuid user_id FK
        uuid friend_id FK
        string status "active | completed"
        timestamp created_at
    }
```

---

## 2. Giải thích Các Bảng Cốt lõi theo Nghiệp vụ

1. **`USERS`:** Lưu thông tin đăng nhập, lộ trình mục tiêu (`FR-01`), trạng thái Gamification cốt lõi (`xp_total`, `streak_current`, `hearts_current` mặc định `5`), cờ gói thuê bao `is_pro` (**LingoCraft Pro `39.000đ–59.000đ/tháng`**) và giờ nhắc học `reminder_time` (**US-08**).
2. **`LEARNING_TRACKS` $\rightarrow$ `LESSONS` $\rightarrow$ `QUESTIONS`:** Tổ chức sẵn lộ trình từ gốc A1–A2 (5 chủ đề giao tiếp, hướng tới **200+ bài học 5–10 phút** theo **O1**). Mỗi câu hỏi có `question_type` (`mcq`, `fill_blank`, `pronunciation`) để khi người dùng bật **"Tạm ẩn Nghe/Nói 15 phút"** (`FR-06`), ứng dụng dễ dàng lọc/thay thế các câu `pronunciation`.
3. **`USER_PROGRESS` & `STREAK_LOGS`:** Ghi nhận lịch sử hoàn thành bài để tính **tỷ lệ hoàn thành bài ($\ge 70\%$)**, **Retention D1/D7/D30** và duy trì chuỗi Streak thực chất.
4. **`AI_EXPLANATION_LOGS`:** Lưu lại câu trả lời sai và giải thích tiếng Việt của AI Tutor (`FR-03`) để có thể tái sử dụng (cache) giảm biến phí LLM API và theo dõi lỗi lặp lại của người học.
5. **`FRIEND_CHALLENGES`:** Phục vụ **Bảng xếp hạng & Thách đấu bạn bè** (`FR-07`, động lực **40,7%** khảo sát).
