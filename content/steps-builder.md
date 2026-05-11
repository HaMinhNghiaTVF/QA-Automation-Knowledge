---
tags:
  - skill
  - phase-b
---
# Định nghĩa
Skill tạo **step definitions** và **fixtures** — phần code kết nối Gherkin scenarios với các thao tác thực tế trên trình duyệt.

# Input → Output
**Input:** Feature files (đã QA review) + Locators + POM từ [[pom-builder]]
**Output:**
- `{screen}.fixtures.ts` — mock data và record builders cho test
- `steps/{screen}/*.steps.ts` — implementation của từng bước Given/When/Then

# Vai trò trong pipeline
Bước cuối của Phase B. Sau khi steps-builder xong → có thể chạy `pnpm test` để thực thi automation test.

# Liên kết
- [[pom-builder]] — bước trước
- [[Giải pháp cho TBS Testing]]
- [[Status hiện tại]]
