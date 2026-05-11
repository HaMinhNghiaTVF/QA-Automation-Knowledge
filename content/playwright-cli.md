---
tags:
  - technology
---
# Là gì?
Tool cho phép AI **tự mở trình duyệt, thăm dò màn hình**, và tìm ra selector chính xác cho từng element — thay vì phải tự viết tay.

# Vai trò trong pipeline
Được dùng bên trong [[pom-builder]]:
1. AI mở URL màn hình thực
2. Tương tác với các element (nút, input, dropdown...)
3. Ghi lại selector chính xác vào locator file

# Tại sao quan trọng?
Locator sai là nguyên nhân hàng đầu khiến automation test fail. playwright-cli giúp verify selector ngay lúc sinh code thay vì phát hiện sau khi chạy test.

# Liên kết
- [[pom-builder]]
- [[Playwright BDD]]
