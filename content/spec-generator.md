---
tags:
  - skill
  - phase-a
---
# Định nghĩa
Skill tự động tạo **functional test case checklist** từ BA Spec.

# Input → Output

```
BA Spec (.md)  →  [spec-generator]  →  specs/{SCREEN_ID}/checklist.md
```

**Input:** File BA Spec dạng Markdown (ví dụ: `SC-BP-TBP010-SENIOR-ANALYZED.md`)
**Output:** Bảng test cases 9 cột lưu tại `specs/{SCREEN_ID}/checklist.md`

---

# Cơ chế hoạt động

## Nguyên tắc cốt lõi
> **Sections trong checklist phản ánh đúng cấu trúc màn hình trong BA Spec — không dùng template cố định.**

Mỗi BA Spec có phần `B.2 Screen Component Detail` mô tả các khối thành phần của màn hình đó. AI đọc từng khối `B.2.1`, `B.2.2`... và ánh xạ thành section tương ứng trong checklist.

## Pipeline 7 bước

```
Bước 1  →  Đọc metadata: Screen ID, tên JP, chế độ màn hình
Bước 2  →  Trích xuất component blocks từ B.2 của BA Spec
Bước 3  →  Đọc thêm: Validation List (C), Events (D), Screen Transitions (A.2)
Bước 4  →  Sinh test cases cho từng section (9 cột)
Bước 5  →  Áp dụng constraints: không tự thêm rule, gắn flag khi không chắc
Bước 6  →  Ghi file output
Bước 7  →  Báo cáo tóm tắt: tổng số cases, số sections, số flags cần QA review
```

## Ví dụ ánh xạ thực tế (VMI046)

| BA Spec block | Section trong checklist |
|---|---|
| B.2.1 ボタンブロック | Menu thao tác |
| B.2.2 検索条件ブロック | Khu vực điều kiện tìm kiếm |
| B.2.3 詳細条件ブロック | Khu vực chi tiết điều kiện |
| B.2.4 一覧ブロック | Khu vực danh sách kết quả |

→ Màn hình đơn giản 4 block → 4 sections. Không thêm section không có trong spec.

## Constraints AI tự tuân thủ
- **Frontend UI/UX only** — không sinh test cho backend, API, DB
- **Không tự thêm rule** — nếu BA Spec không nhắc đến thì không test
- **Gắn flag khi mơ hồ** — `QA-REVIEW:` khi không chắc, để QA quyết định
- **Giữ nguyên thuật ngữ Nhật** — `検索`, `担当者`, message lỗi JP không dịch
- **Format sạch** — ID tuần tự, không trùng, không nhảy số

---

# Format output (9 cột)

| ID | Precondition | Description | Expect result | Priority | BugID | Chrome | Tester | Date |
|---|---|---|---|---|---|---|---|---|
| 1.1 | Đang ở màn VMI046 | Kiểm tra hiển thị ban đầu | Danh sách hiển thị đầy đủ | High | | | | |

Priority: `High` / `normal` / `low`
ID: `{section}.{item}` — ví dụ `2.5`, không có prefix màn hình

---

# Kết quả thực tế
Validate trên **TBP016**: 51 test cases, khớp với bảng QA làm tay.
Đã tạo checklist cho: VMI046 (64 cases), GBP013 (80 cases), TBP010 (206 cases).

# Liên kết
- [[Giải pháp cho TBS Testing]]
- [[feature-drafter]] — bước tiếp theo sau khi QA review checklist
