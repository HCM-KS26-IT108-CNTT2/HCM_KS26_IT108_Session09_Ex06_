Phần 1. Phân tích

Input / Output dữ liệu của trang trại:

Thành phần	Nội dung
Input	Dữ liệu cảm biến (nhiệt độ, độ ẩm không khí, độ ẩm đất, ánh sáng) và ngưỡng cài đặt từ người dùng
Output	Điều khiển bơm, quạt, đèn; gửi cảnh báo và biểu đồ lên dashboard

Sơ đồ phối hợp CPU / RAM (dạng Markdown):

[Cảm biến] --> [Cổng I/O] --> [RAM] <--> [CPU] --> [Cổng I/O] --> [Bơm / Quạt]

RAM lưu chương trình và dữ liệu tạm. CPU lấy lệnh từ RAM (Fetch), giải mã (Decode), thực thi (Execute), rồi ghi kết quả ngược lại RAM.