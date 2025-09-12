# Đề tài : Quản lý khách sạn

## 📌 Giới thiệu

Trong bối cảnh ngành du lịch – khách sạn ngày càng phát triển, việc quản lý khách sạn hiệu quả đóng vai trò quan trọng trong việc nâng cao chất lượng dịch vụ và tối ưu hóa nguồn lực. Trước kia, nhiều khách sạn còn quản lý thông tin bằng sổ sách hoặc file Excel thủ công, dễ xảy ra sai sót, thất lạc dữ liệu, khó khăn trong truy xuất và thiếu bảo mật.  

Đề tài **"Quản lý khách sạn và khách đặt phòng"** được xây dựng nhằm ứng dụng cơ sở dữ liệu quan hệ để quản lý toàn diện hoạt động của một khách sạn: từ khách hàng, phòng, dịch vụ đến hóa đơn, giúp quy trình đặt phòng – thanh toán trở nên nhanh chóng, chính xác và hiện đại hơn.

---

## 🎯 Mục tiêu hệ thống

- Nâng cao hiệu quả quản lý thông tin khách hàng và đặt phòng.
- Giảm thiểu sai sót khi đặt/hủy phòng.
- Quản lý dịch vụ đi kèm (ăn uống, giặt ủi, spa,…) minh bạch, rõ ràng.
- Tăng cường bảo mật dữ liệu khách hàng.
- Hỗ trợ lập báo cáo doanh thu, tỷ lệ lấp đầy phòng, xu hướng đặt phòng.
- Nâng cao trải nghiệm của khách hàng và khả năng cạnh tranh của khách sạn.

---

## 🏨 Kịch bản thế giới thực

- Hệ thống quản lý khách sạn và khách đặt phòng sẽ bao gồm các nghiệp vụ sau:
- KhachHang: lưu thông tin khách.
  - KhachID int identity(1,1) primary key,
  - CCCD nvarchar(12) unique not null,
  - Hoten nvarchar(100) not null,
  - gioitinh nvarchar(12) not null,
  - SDT nvarchar(10) not null,
  - email nvarchar(100),
  - diachi nvarchar(100)
  
- Phong: quản lý loại phòng, tình trạng, giá.
  - PhongID int identity(1,1) primary key,
  - sophong nvarchar(100) unique not null,
  - LoaiPhong NVARCHAR(20) CHECK (LoaiPhong IN (N'Đơn', N'Đôi', N'VIP')),
  - TinhTrang NVARCHAR(20) CHECK (TinhTrang IN (N'Còn trống', N'Đã đặt', N'Đang dọn dẹp')),
  - GiaPhong DECIMAL(9,2) NOT NULL
  
- DatPhong: gắn khách hàng với phòng, có ngày nhận/trả.
  - DatPhongID INT IDENTITY(1,1) PRIMARY KEY,
  - KhachHangID INT FOREIGN KEY REFERENCES KhachHang(KhachHangID),
  - PhongID INT FOREIGN KEY REFERENCES Phong(PhongID),
  - NgayNhan DATE NOT NULL,
  - NgayTra DATE NOT NULL,
  - SoNguoi INT,
  - YeuCauDacBiet NVARCHAR(200)
  
- DichVu: các dịch vụ khách sạn cung cấp.
  - DichVuID INT IDENTITY(1,1) PRIMARY KEY,
  - TenDichVu NVARCHAR(100) NOT NULL,
  - Gia DECIMAL(9,2) NOT NULL
  
- SuDungDichVu: bảng trung gian để ghi khách đã dùng dịch vụ nào, số lượng.
  - SuDungID INT IDENTITY(1,1) PRIMARY KEY,
  - DatPhongID INT FOREIGN KEY REFERENCES DatPhong(DatPhongID),
  - DichVuID INT FOREIGN KEY REFERENCES DichVu(DichVuID),
  - SoLuong INT DEFAULT 1
  
- HoaDon: mỗi đặt phòng có 1 hóa đơn, tổng tiền có thể tính dựa trên phòng + dịch vụ.
  - HoaDonID INT IDENTITY(1,1) PRIMARY KEY,
  - DatPhongID INT FOREIGN KEY REFERENCES DatPhong(DatPhongID),
  - NgayLap DATE DEFAULT GETDATE(),
  - TongTien DECIMAL(9,2)
  
- NhanVien: lưu thông tin nhân viên và chức vụ.
  - NhanVienID INT IDENTITY(1,1) PRIMARY KEY,
  - CCCD nvarchar(12) unique not null,
  - HoTen NVARCHAR(100) NOT NULL,
  - SoDienThoai VARCHAR(20),
  - ChucVu NVARCHAR(50)
---

## 🛠️ Các chức năng chính

- **Cập nhật dữ liệu:** thêm, sửa, xóa khách hàng, phòng, dịch vụ, nhân viên, đặt phòng, hóa đơn.
- **Tra cứu dữ liệu:** tìm kiếm phòng trống theo ngày, tra cứu lịch sử đặt phòng của khách hàng, tìm kiếm dịch vụ phổ biến.
- **Thống kê & báo cáo:**
  - Báo cáo doanh thu theo tháng/quý/năm.
  - Báo cáo tỷ lệ lấp đầy phòng.
  - Thống kê dịch vụ sử dụng nhiều nhất.
  - Thống kê khách hàng theo quốc tịch/độ tuổi/giới tính.

---

## 👥 Thành viên thực hiện phần 1, 2

- Đỗ mạnh Hà
- Lê Văn Nghệ
- Nguyễn Hải Nam
- Nguyễn Hoàng Tùng
- Nguyễn Văn Trường

---

## 📅 Tiến độ thực hiện

- **Phần 1:** Đặt vấn đề & đăng ký đề tài  
- **Phần 2:** Mô tả kịch bản thế giới thực  
---
