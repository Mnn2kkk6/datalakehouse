# 📚 BÁO CÁO NGÀY THỨ TƯ

Hôm nay tiếp tục từ bài PySpark hôm trước và áp dụng vào một flow **Data Lakehouse** đơn giản theo mô hình **Bronze / Silver / Gold**, kết hợp lưu dữ liệu lên **MinIO**.

🔗 **GitHub:** https://github.com/Mnn2kkk6/pyspark-orders-repo

### Công việc đã làm

* Tạo `orders.csv` gồm **250 dòng**, trong đó có 30 dòng cố tình tạo lỗi.
* **Bronze:** đọc dữ liệu bằng PySpark và lưu nguyên dữ liệu, chỉ thêm `source_file` và `load_time`.
* **Silver:** làm sạch dữ liệu, bỏ `order_id` rỗng, loại `amount <= 0`, chuẩn hóa `status` và chuyển `order_date` sang kiểu date. Kết quả còn **220 dòng**.
* **Gold:** tổng hợp dữ liệu theo `province`, tính số đơn, tổng tiền, số đơn thành công/thất bại.
* **MinIO:** tạo bucket và upload dữ liệu của cả 3 layer lên MinIO.

### Kinh nghiệm rút ra

Qua bài này hiểu rõ hơn cách **Bronze giữ dữ liệu gốc → Silver làm sạch → Gold tổng hợp**, cũng như cách MinIO có thể đóng vai trò như một storage kiểu S3 trong hệ thống Data Lakehouse.

