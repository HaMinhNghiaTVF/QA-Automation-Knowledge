# Mục đích
- Giải quyết [[Vấn đề hiện tại về Test trong dự án TBS]]

# Phương hướng
## 1. Sử dụng AI để tạo Functional Test Cases
Áp dụng [[spec-generator]] để tạo functional test cases từ BA Spec:
- Format đúng chuẩn bảng QA (9 cột)
- Chỉ dựa trên BA Spec — không tự thêm rule ngoài
- QA review và chỉnh sửa trước khi dùng

## 2. Sử dụng AI để tạo Automation Test Cases
Pipeline 3 bước, QA review sau mỗi bước:

| Bước | Skill | Output |
|------|-------|--------|
| 1 | [[feature-drafter]] | Gherkin feature files |
| 2 | [[pom-builder]] | Locators + Page Object Model |
| 3 | [[steps-builder]] | Step definitions + Fixtures |

### Nền tảng kỹ thuật

**[[Playwright BDD]]** ([github.com/vitalets/playwright-bdd](https://github.com/vitalets/playwright-bdd))
Framework kết hợp Playwright với BDD. Điểm mạnh chính:
- Tự động map Gherkin steps sang Playwright actions — không cần config thủ công
- Tổ chức test theo folder → mỗi màn hình độc lập, không ảnh hưởng nhau
- Báo cáo kết quả chi tiết theo scenario, dễ đọc cho cả QA lẫn dev

**[[playwright-cli]]** — AI tự mở trình duyệt, thăm dò màn hình, tìm đúng locator trước khi viết code

### Tag Taxonomy
Mỗi scenario trong feature file được gắn tags để truy vết và lọc. Xem [[Tag Taxonomy]] để biết đầy đủ.

Tóm tắt nhanh:

| Tag | Ý nghĩa |
|-----|---------|
| `@P-High` / `@P-normal` / `@P-low` | Priority của test case |
| `@CL-2.5` | Truy vết về checklist row 2.5 |
| `@from-CORE-6` | Rule chung số 6 áp dụng cho màn này |
| `@qa-review` | AI tự flag — cần QA xác nhận trước khi tin kết quả |

Xem [[Status hiện tại]] để biết tiến độ hiện tại.
Xem [[Plan tiếp theo cho QA Agent trong MVP 2]] để biết bước tiếp theo.
