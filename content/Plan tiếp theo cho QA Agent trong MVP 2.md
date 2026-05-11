# Plan tiếp theo — MVP 2

## 1. Review & cải thiện chất lượng trên VMI046
Review lại toàn bộ test cases của VMI046 để xác định những phần đang xử lý chưa ổn:
- Phân loại nguyên nhân fail: selector sai, logic test sai, hay skill sinh output kém?
- Từ đó cải thiện trực tiếp vào các skills hoặc commands liên quan

## 2. Thử nghiệm với QA team
### 2a. QA tự dùng spec-generator
QA chạy thử [[spec-generator]] trực tiếp từ BA Spec của một màn hình mới:
- So sánh output AI với cách làm trước đây
- Thu thập feedback: thiếu gì, sai ở đâu, cần bổ sung rule gì

### 2b. QA chạy thử pipeline automation
Chọn **1 màn hình mới** (chưa có automation), QA tự chạy [[feature-drafter]] → [[pom-builder]] → [[steps-builder]]:
- So sánh output AI với kinh nghiệm QA làm tay
- Feedback này là input trực tiếp để cải thiện skills

## 3. Xây dựng Memory Loop cho Agent
Vấn đề hiện tại: mỗi lần chạy, agent không "nhớ" những lỗi đã gặp ở lần trước — dẫn đến lặp lại cùng sai lầm.

Hướng giải quyết: xây dựng cơ chế **học liên tục**:
- Sau mỗi run, ghi lại những pattern lỗi thường gặp (selector dễ vỡ, logic không khớp BA spec...)
- Agent đọc lại memory này ở đầu mỗi lần chạy → tránh lặp lỗi cũ
- Dần dần tích lũy thành knowledge base cho dự án TBS

Đây là nền tảng để scale sang nhiều màn hình mà không tốn công sức review lại từ đầu.
