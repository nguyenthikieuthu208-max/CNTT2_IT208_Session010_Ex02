  
**Bài 2 : Chuẩn hóa tài liệu cài đặt hệ thống**
PHẦN 1: BÁO CÁO PHÂN TÍCH (INPUT / OUTPUT)

-   **Input (Dữ liệu đầu vào thô):**
    -   Các câu lệnh cài đặt hệ thống, tên biến cấu hình bị trộn lẫn với văn bản giải thích.
    -   Đoạn code Python điều khiển máy bơm hiển thị dưới dạng văn bản thường, không có màu sắc lập trình.
    -   Thông số so sánh các loại cảm biến được viết rời rạc, khó đối chiếu.
-   **Output (Giao diện render chuyên nghiệp mong muốn):**
    -   Tách biệt rõ ràng các lệnh Terminal ngắn bằng định dạng `Inline Code`.
    -   Đoạn mã Python được đặt trong `Code Block` có bật tính năng **Syntax Highlighting** giúp hiển thị màu sắc cú pháp chuẩn phần mềm.
    -   Dữ liệu được tổ chức thành cấu trúc **Table** (Bảng) trực quan và **Task List** (Danh sách công việc) để kỹ sư tích chọn tiến độ lắp đặt.
    -   Sử dụng ký tự **Escape (`\`)** tại các vị trí ký tự đặc biệt để hệ thống hiển thị chính xác văn bản thô, tránh lỗi vỡ định dạng.

----------

PHẦN 2: MÃ NGUỒN MARKDOWN HOÀN THIỆN (`.md`)

Bạn hãy sao chép toàn bộ đoạn mã nguồn sạch dưới đây vào ô soạn thảo bên trái của StackEdit:

markdown

```
# Hướng dẫn Cài đặt Cảm biến Độ ẩm - Trang trại Lan

Tài liệu này hướng dẫn chi tiết cách cấu hình phần cứng và phần mềm cho hệ thống tưới tưới tự động.

## 1. Cấu hình Môi trường & Lệnh Hệ thống
Để khởi chạy thiết bị, kỹ sư cần mở Terminal và thực thi câu lệnh sau để cài đặt thư viện điều khiển:
`pip install telemetry-sensor`

Sau khi cài đặt xong, thiết lập biến môi trường cấu hình cổng kết nối:
* Tên biến: `SENSOR_PORT`
* Giá trị mặc định: `COM3`

*Lưu ý kỹ thuật:* Để hiển thị ký tự mã nguồn trên tài liệu, chúng ta sử dụng ký tự đặc biệt như \#1 và \*đầu ra\* mà không bị lỗi định dạng bằng cách thêm dấu gạch chéo ngược `\` ở phía trước.

## 2. Mã nguồn Python Điều khiển Máy bơm
Dưới đây là đoạn mã Python chạy trên vi xử lý để tự động kích hoạt máy bơm khi độ ẩm xuống thấp:

```python
import time
from telemetry_sensor import HumiditySensor

# Khởi tạo cảm biến tại cổng COM3
sensor = HumiditySensor(port="COM3")
PUMP_STATUS = False

while True:
    current_humidity = sensor.read_retry()
    print(f"Độ ẩm hiện tại: {current_humidity}%")
    
    # Kích hoạt máy bơm nếu độ ẩm dưới 60%
    if current_humidity < 60:
        PUMP_STATUS = True
        print("-> Cảnh báo: Độ ẩm thấp! Đang bật máy bơm tự động.")
    else:
        PUMP_STATUS = False
        
    time.sleep(5)
```

## 3. Bảng so sánh các loại Cảm biến (Table)

| Tính năng kỹ thuật | Cảm biến Thế hệ cũ | Cảm biến GreenTech V2 (Mới) |
| :--- | :---: | :---: |
| Tần suất quét dữ liệu | 10 giây / lần | 1 giây / lần |
| Sai số biên độ | \pm 5\% | \pm 1\% (Cực kỳ chính xác) |
| Chuẩn chống nước | IP65 | IP68 (Chống ngập hoàn toàn) |
| Trạng thái cung ứng | Đã ngừng sản xuất | Sẵn hàng trên kho |

## 4. Danh sách kiểm tra nghiệm thu Thiết bị (Task List)

Kỹ sư vận hành tiến hành tích chọn cấu hình phần cứng trước khi bàn giao hệ thống:

- [x] Đã đấu nối thành công dây tín hiệu của cảm biến vào mạch điều khiển trung tâm.
- [x] Đã kiểm tra nguồn điện cấp cho máy bơm tự động (Đảm bảo điện áp 220V ổn định).
- [ ] Đã nạp code Python điều khiển vào vi xử lý thành công.
- [ ] Chạy thử nghiệm hệ thống liên tục trong 30 phút để kiểm tra độ ổn định.
```

