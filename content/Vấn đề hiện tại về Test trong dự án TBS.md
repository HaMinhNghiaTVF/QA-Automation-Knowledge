# 1. Tốn thời gian để tạo test cases từ BA Specs
Trung bình tốn khoảng **nửa ngày (4h)** để đọc, phân tích và format test cases từ một BA Spec — chưa kể thời gian làm rõ yêu cầu với BA.

Nguyên nhân: QA phải tự suy ra các trường hợp cần test, format theo chuẩn bảng, rồi review lại từng dòng — lặp đi lặp lại với mỗi màn hình mới.

# 2. Tốn thời gian để test màn hình
Việc test 1 màn hình mất nhiều thời gian. Thời gian từ **3 - 7h** và không ổn định tùy 2 biến số là **độ khó của màn** và **con người (dev + QA)**.

Với automation test, chi phí setup ban đầu còn cao hơn: viết locator, POM, step definitions. Thường bị bỏ qua vì deadline gấp — dẫn đến không có safety net khi regression xảy ra.