# ⚽ Sport Kicks - Website Quản Lý Bán Giày Bóng Đá Online

<p align="center">
  <i>Đồ án môn học: Lập trình trên môi trường Web - Trường Đại học Công nghệ GTVT</i>
</p>

## 📖 Giới thiệu (Lý do chọn đề tài)
Sự bùng nổ của mua sắm trực tuyến đòi hỏi các website bán hàng không chỉ dừng lại ở việc "trưng bày sản phẩm", mà phải mang lại trải nghiệm tiện lợi và thông minh. Đối với mặt hàng đặc thù như giày bóng đá, khách hàng cần biết chính xác size giày mình muốn còn hàng hay không, và người bán cần một công cụ quản lý kho chặt chẽ để tránh thất thoát.

**Sport Kicks** được xây dựng nhằm cung cấp một nền tảng mua sắm chuyên nghiệp, minh bạch về tồn kho thực tế, tích hợp thanh toán tiện lợi và được thiết kế bài bản dựa trên kiến trúc phần mềm chuẩn mực.

## 🛠 Công nghệ sử dụng & Kiến trúc hệ thống
- **Ngôn ngữ Back-end:** PHP thuần (Vanilla PHP).
- **Kiến trúc phần mềm:** Mô hình **MVC** (Model - View - Controller). Tách biệt rõ ràng giữa xử lý logic, tương tác CSDL và giao diện người dùng.
- **Cơ sở dữ liệu:** MySQL.
- **Front-end:** HTML, CSS, JavaScript (AJAX).
- **Tích hợp API:** API VietQR (Tạo mã QR thanh toán tự động).

## ✨ Chức năng chính

### 🛒 Dành cho Khách hàng (Client)
- **Cơ chế Điều hướng (Routing):** Sử dụng Front Controller (`index.php?controller=...&action=...`) thân thiện, dễ quản lý.
- **Xem & Lọc sản phẩm:** Lọc theo danh mục (Cỏ nhân tạo, Cỏ tự nhiên...), sắp xếp theo giá, tên, độ mới.
- **Kiểm tra tồn kho Real-time:** Hiển thị chính xác số lượng tồn kho theo từng **Size giày** cụ thể, ngăn chặn việc đặt hàng khi hết size.
- **Giỏ hàng thông minh (AJAX):** Thêm sản phẩm và tính tổng tiền ngay lập tức mà không cần tải lại trang.
- **Thanh toán VietQR:** Tự động sinh mã QR chuyển khoản chứa sẵn thông tin: STK đích, số tiền chính xác và nội dung chuyển khoản.
- **Flash Sale:** Tính năng giảm giá theo khung giờ thực (Server Time) với nhãn đếm ngược bắt mắt.

### ⚙️ Dành cho Quản trị viên (Admin)
- **Dashboard Tổng quan:** Thống kê đơn hàng, doanh thu (ngày/tháng/năm) và cảnh báo sản phẩm sắp hết hàng.
- **Quản lý Sản phẩm & Biến thể:** Thêm/Sửa/Xóa sản phẩm, định nghĩa cấu hình Size (39, 40, 41...) và thiết lập khung giờ Flash Sale.
- **Quản lý Nhập kho (Stock Import):** Hỗ trợ nhập hàng loạt số lượng và giá vốn cho nhiều Size cùng lúc. Tự động cộng dồn vào tồn kho.
- **Quản lý Đơn hàng:** Quy trình xử lý khép kín (Chờ xử lý -> Đang giao -> Hoàn thành / Hủy). Tự động hoàn trả số lượng về kho nếu đơn hàng bị hủy.
- **Quản lý Hệ thống:** Quản lý thương hiệu, quản lý thành viên và phân quyền (Admin/Customer/Staff).
- **Bảo mật:** Mã hóa mật khẩu người dùng, chống SQL Injection.

## 🗄 Cấu trúc Cơ sở dữ liệu (Database)
Hệ thống sử dụng các thực thể chính liên kết chặt chẽ với nhau:
- `products`: Thông tin cơ bản của giày (tên, giá, mô tả...).
- `product_variants`: Quản lý tồn kho chi tiết theo từng Size.
- `orders` & `order_details`: Lưu trữ giao dịch và chi tiết sản phẩm khách mua.
- `stock_imports`: Ghi nhận lịch sử nhập hàng.
- `users`: Quản lý tài khoản và phân quyền.

*(Thêm hình ảnh ERD của CSDL vào đây)*
<!-- ![Database Schema](đường_dẫn_tới_ảnh_CSDL_của_bạn) -->

## 💻 Hướng dẫn cài đặt (Setup)
1. Tải và cài đặt phần mềm tạo Web Server cục bộ như **XAMPP** hoặc **WAMP**.
2. Clone repository này về thư mục `htdocs` (nếu dùng XAMPP) hoặc `www` (nếu dùng WAMP):
   
```bash
   git clone [https://github.com/your-username/sport-kicks.git](https://github.com/your-username/sport-kicks.git)