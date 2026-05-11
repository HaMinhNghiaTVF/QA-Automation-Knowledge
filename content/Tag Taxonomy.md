---
tags:
  - reference
---
# Tag Taxonomy — QA Agent

Tags gắn lên mỗi Gherkin scenario phục vụ 3 mục đích: **lọc test**, **truy vết nguồn gốc**, và **đánh dấu cần review**.

## Nhóm 1 — Loại test (Feature-level)
Gắn ở dòng `Feature:`, xác định file thuộc loại nào.

| Tag | File | Mô tả |
|-----|------|-------|
| `@functional` | `@functional.feature` | Test cases từ checklist màn hình cụ thể |
| `@core` | `@core.feature` | Rule chung áp dụng mọi màn hình |
| `@extension` | `@extension.feature` | Rule mở rộng theo độ phức tạp màn hình |

## Nhóm 2 — Priority (Scenario-level)
Gắn ở mỗi `Scenario`, ánh xạ trực tiếp từ cột Priority trong checklist.

| Tag | Priority |
|-----|----------|
| `@P-High` | Phải pass — ảnh hưởng nghiệp vụ chính |
| `@P-normal` | Nên pass |
| `@P-low` | Nice to have |

## Nhóm 3 — Truy vết (Traceability)
Cho phép link ngược từ kết quả test → nguồn gốc yêu cầu.

| Tag | Dùng ở | Ý nghĩa |
|-----|--------|---------|
| `@CL-2.5` | `@functional` | Truy về checklist row 2.5 |
| `@from-CORE-6` | `@core` | Truy về Core rule số 6 |
| `@from-EXT-2-19` | `@extension` | Truy về Extension group 2, rule 19 |
| `@VMI046` | Tất cả | Scope test cho màn hình VMI046 |

## Nhóm 4 — Review flag
| Tag | Ai gắn | Ý nghĩa |
|-----|--------|---------|
| `@qa-review` | AI tự động | Selector chưa verify, hoặc logic mơ hồ — **cần QA xem lại trước khi tin kết quả** |

## Ví dụ thực tế
```gherkin
@functional @VMI046
Feature: VMI046 — Đăng ký vật tư

  @P-High @CL-1.3 @qa-review
  Scenario: Nhập mã vật tư trùng lặp hiển thị lỗi
    ...
```
Scenario này: priority cao, truy về checklist 1.3, AI đã flag cần QA review.

## Liên kết
- [[Giải pháp cho TBS Testing]]
- [[feature-drafter]]
