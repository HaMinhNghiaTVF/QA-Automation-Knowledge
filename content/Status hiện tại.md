# Phase A — Tạo Test Case Checklist ✅
[[spec-generator]] đã hoàn thành và được validate:
- Chạy thử nghiệm trên **TBP016**: output khớp với bảng QA làm tay (51 test cases)
- Đã có checklist cho: **VMI046**, **GBP013**, **TBP010**

# Phase B — Automation Pipeline 🔄
[[feature-drafter]] → [[pom-builder]] → [[steps-builder]] đã chạy thử trên màn hình **VMI046**:

| Chỉ số            | Kết quả    |
| ----------------- | ---------- |
| Tổng số scenarios | 89         |
| Pass              | 55 (≈ 62%) |
| Fail              | 34         |
| Cần QA review     | 18         |

**Nhận xét:**
- Pipeline hoạt động end-to-end — từ checklist ra được test chạy được
- Pass rate 62% là điểm khởi đầu — chưa phải final, cần tiếp tục fix
- 18 scenarios được AI tự động flag `@qa-review` — cần QA xem lại trước khi tin kết quả

# Vấn đề đang gặp
- [ ] Một số test cases trong checklist còn mơ hồ về logic → AI sinh ra output không chính xác → cần làm việc lại với QA để làm rõ
- [ ] Các skills vẫn chưa ổn định: đôi khi cần chạy lại hoặc sửa tay output → tốn token và thời gian
- [ ] Một số locators (selector) dễ vỡ khi layout màn hình thay đổi → cần `/qa-heal` để tự động sửa
