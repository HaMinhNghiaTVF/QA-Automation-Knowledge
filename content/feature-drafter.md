---
tags:
  - skill
  - phase-b
---
# Định nghĩa
Skill chuyển **test case checklist** thành **Gherkin feature files** — ngôn ngữ mô tả test automation dạng kịch bản (Given/When/Then).

# Input → Output
**Input:** Checklist từ [[spec-generator]] (đã được QA review)
**Output:** 3 file `.feature` cho mỗi màn hình:
- `@functional.feature` — test cases từ checklist
- `@core.feature` — các rule chung áp dụng mọi màn hình
- `@extension.feature` — các rule mở rộng theo độ phức tạp

# Lưu ý
- Nội dung viết bằng tiếng Việt để QA dễ review
- Thuật ngữ Nhật (tên nút, message lỗi) giữ nguyên không dịch
- Sau khi skill chạy xong → **QA review feature files trước khi sang bước tiếp theo**

# Liên kết
- [[pom-builder]] — bước tiếp theo
- [[Giải pháp cho TBS Testing]]
