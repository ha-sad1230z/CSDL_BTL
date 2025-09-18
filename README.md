# 🏨 Hệ thống Quản lý Khách sạn

## 📌 Giới thiệu
Trong bối cảnh ngành du lịch – khách sạn ngày càng phát triển, việc quản lý khách sạn hiệu quả đóng vai trò quan trọng trong việc nâng cao chất lượng dịch vụ và tối ưu hóa nguồn lực.  

Đề tài **“Quản lý khách sạn”** được xây dựng nhằm ứng dụng **cơ sở dữ liệu quan hệ (RDBMS)** để quản lý toàn diện hoạt động của một khách sạn: từ khách hàng, phòng, dịch vụ đến hóa đơn.  

Hệ thống giúp quy trình đặt phòng – thanh toán trở nên **nhanh chóng, chính xác và hiện đại hơn**, đồng thời hỗ trợ ban quản lý trong việc lập báo cáo, phân tích doanh thu, nâng cao trải nghiệm khách hàng.  

---

## 🎯 Mục tiêu hệ thống

### Mục tiêu chức năng
- Quản lý thông tin khách hàng, phòng, dịch vụ.
- Quản lý đặt phòng, hủy phòng, yêu cầu đặc biệt.
- Quản lý dịch vụ đi kèm (ăn uống, giặt ủi, spa,…).
- Lập hóa đơn và tính tổng chi phí.
- Thống kê & báo cáo doanh thu, tỷ lệ lấp đầy phòng, dịch vụ phổ biến.

### Mục tiêu phi chức năng
- Tăng cường **bảo mật dữ liệu khách hàng**.
- Đảm bảo **toàn vẹn dữ liệu** (tránh trùng lặp, mất mát).
- Hỗ trợ **sao lưu & phục hồi dữ liệu**.
- Cấu trúc **dễ mở rộng** và thân thiện với người dùng.

---

## 🏨 Kịch bản thế giới thực

- Hệ thống quản lý khách sạn và khách đặt phòng sẽ bao gồm các nghiệp vụ sau:
- **KhachHang**: thông tin khách hàng : KhachHang (KhachHangID, CCCD, HoTen, GioiTinh, SDT, Email, DiaChi)
- **NhanVien**: thông tin nhân viên khách sạn : NhanVien (NhanVienID, CCCD, HoTen, GioiTinh, SDT, ChucVu, Luong)
- **Phong**: quản lý loại phòng, tình trạng, giá : Phong (PhongID, SoPhong, LoaiPhong, TinhTrang, GiaPhongNgay, GiaPhongDem)
- **DatPhong**: lưu thông tin đặt phòng của khách hàng : DatPhong (DatPhongID, KhachHangID, PhongID, NgayNhan, NgayTra)
- **PhanCong**: phân công nhân viên phụ trách phòng cho khách trong thời gian đặt phòng : PhanCong (PhanCongID, NhanVienID, DatPhongID, NgayPhanCong, VaiTro)
- **DichVu**: danh sách dịch vụ khách sạn cung cấp : DichVu (DichVuID, TenDichVu, DonGia)
- **SuDungDichVu**: lưu dịch vụ khách đã sử dụng theo đặt phòng : SuDungDichVu (DatPhongID, DichVuID, SoLuong)
- **HoaDon**: thông tin hóa đơn thanh toán : HoaDon (HoaDonID, NgayLap, TongTien)
- **ChiTietHoaDon**: lưu chi tiết hóa đơn theo từng đặt phòng : ChiTietHoaDon (HoaDonID, DatPhongID, TongGiaPhong, TongGiaDichVu, ThanhTien)
---
  
## ⚙️ Các chức năng chính

### 1. Quản lý dữ liệu
- Thêm, sửa, xóa khách hàng, phòng, dịch vụ.
- Quản lý đặt phòng, hủy phòng, yêu cầu đặc biệt.
- Tạo và quản lý hóa đơn.

### 2. Tra cứu dữ liệu
- Tìm phòng trống theo ngày.
- Xem lịch sử đặt phòng của khách.
- Tìm dịch vụ phổ biến.

### 3. Thống kê & báo cáo
- Doanh thu theo tháng/quý/năm.
- Tỷ lệ lấp đầy phòng.
- Dịch vụ được sử dụng nhiều nhất.
- Thống kê khách hàng theo độ tuổi/giới tính/quốc tịch.

---

## 📅 Các phần đã hoàn thành

- **Phần 1:** Đặt vấn đề & đăng ký đề tài  
- **Phần 2:** Mô tả kịch bản thế giới thực  
---
