# 📘 Hệ thống Quản Lý Khách Sạn

## I. Đặt Vấn Đề

Trong bối cảnh ngành du lịch và dịch vụ khách sạn ngày càng phát triển, việc quản lý hoạt động khách sạn một cách hiệu quả và chính xác là nhu cầu tất yếu. Trước đây, nhiều khách sạn vẫn còn quản lý theo phương pháp thủ công như sổ sách, giấy tờ hoặc các file rời rạc. Cách làm này dễ gây ra sai sót, thất thoát thông tin, khó khăn trong việc tra cứu và chia sẻ dữ liệu giữa các bộ phận. 

Do đó, việc xây dựng **hệ thống quản lý khách sạn** dựa trên cơ sở dữ liệu tập trung không chỉ giúp tự động hóa quy trình quản lý, mà còn mang lại sự tiện lợi trong điều hành, tiết kiệm chi phí và nâng cao trải nghiệm khách hàng.

Hệ thống này cho phép:
- Quản lý thông tin khách hàng, nhân viên và các bộ phận trong khách sạn.  
- Quản lý đặt phòng, tình trạng phòng, dịch vụ sử dụng và hóa đơn thanh toán.  
- Quản lý nhà hàng, gọi món, thanh toán ăn uống.  
- Quản lý thiết bị, báo cáo sự cố và quá trình sửa chữa.  
- Cung cấp báo cáo thống kê, hỗ trợ nhà quản lý đưa ra quyết định.  

🎯 **Mục tiêu của đề tài “Hệ thống Quản lý Khách Sạn”**:
- Nâng cao hiệu quả quản lý thông tin khách sạn.  
- Cải thiện chất lượng phục vụ và trải nghiệm của khách hàng.  
- Tăng cường bảo mật, toàn vẹn dữ liệu.  
- Hỗ trợ báo cáo, thống kê để phục vụ phân tích kinh doanh.  
- Tối ưu chi phí vận hành và tăng khả năng phối hợp giữa các bộ phận.  

---
## II. Phân Tích

### 1. Mô tả “kịch bản thế giới thực”
Ứng dụng của hệ cơ sở dữ liệu này là quản lý hoạt động khách sạn bao gồm: đặt phòng, sử dụng dịch vụ, thanh toán và quản lý nhân sự.  
Hệ thống sẽ giúp:
- Lưu trữ và quản lý thông tin khách hàng, nhân viên, phòng, dịch vụ, thiết bị.  
- Hỗ trợ khách hàng đặt phòng nhanh chóng, sử dụng dịch vụ và thanh toán thuận tiện.  
- Giúp nhân viên dễ dàng theo dõi lịch làm việc, quản lý phòng và xử lý sự cố.  
- Giúp nhà quản lý theo dõi hoạt động kinh doanh, doanh thu và hiệu quả vận hành.
---
### 2. Yêu cầu về dữ liệu cần được lưu trữ
### a. Các thông tin chính cần quản lý trong cơ sở dữ liệu khách sạn:
#### 1. Người
- **Người** : NguoiID, CCCD, HoTen, NgaySinh, GioiTinh, DiaChi, Sdt, email, QuocTich
- **Khách Hàng** : KhachHangID, NguoiID, HangThanhVien, DiemTichLuy
- **NhanVien** : NhanVienID, NguoiID, ChucVu, NgayVaoLam, Luong, BoPhanID
---
#### 2. Phòng và Đặt Phòng
- **Phòng** : PhongID, SoPhong, LoaiPhong, GiaPhong, TrangThai
- **Đặt Phòng** : DatPhongID, KhachHangID, PhongID, Ngay Dat, NgayNhan, NgayTra, TienCoc, TrangThai
---
#### 3. Dịch Vụ và Sử Dụng
- **Dịch Vụ** : DichVuID, TenDichVu, MoTa, DonGia
- **SuDungDichVu** : SuDungID, KhachHangID, DichVuID, NgaySuDung, SoLuong, TongTien
---
#### 4. Nhà Hàng
- **Nhà hàng** : NhaHangID, TenNhaHang, ViTri, GioMoCua, GioDongCua
- **MonAn** : NhaHangID, MonAnID, TenMon, MoTa
- **Gọi Món** : GoiMonID, NhaHangID, MonAnID, KhachHangID, SoLuong, ThoiGianGoi, GhiChu, TrangThai, TongTien
- **ThanhToanNhaHang** : ThanhToanID, GoiMonID, PhuongThuc, NgayThanhToan, TongTien
---
#### 5. Quản lý Nhân Sự
- **BoPhan** : BoPhanID, TenBoPhan, MoTa
- **LichLamViec** : LichID, NhanVienID, NgayLam, CaLam
---
#### 6. Thanh Toán
- **HoaDon** : HoaDonID, DatPhongID, NguoiThanhToan, NgayLap, TongTien, TinhTrang, PhuongThuc
---
#### 7. Đánh Giá
- **DanhGia** : DanhGiaID, KhachHangID, NoiDung, SoSao, NgayDanhGia
---
### b. Các thao tác chính trên hệ thống
Hệ thống quản lý khách sạn sẽ hỗ trợ các thao tác:
- **Cập nhật**: thêm/sửa thông tin khách hàng, nhân viên, phòng, dịch vụ, thiết bị.  
- **Đặt phòng & thanh toán**: cho phép khách hàng đặt phòng, sử dụng dịch vụ và thanh toán.  
- **Tra cứu**: tìm kiếm thông tin khách hàng, phòng trống, dịch vụ, hóa đơn.  
- **Xem dữ liệu**: hiển thị danh sách khách hàng, phòng đang sử dụng, doanh thu theo ngày/tháng/năm.  
- **Lập báo cáo**: doanh thu khách sạn, hiệu quả nhân viên, thống kê dịch vụ sử dụng nhiều nhất, tỷ lệ phòng trống.  
---
## Ghi Chú
- **Thực thể mạnh**: Nguoi, KhachHang, NhanVien, Phong, DichVu, NhaHang, ThucDon, BoPhan, HoaDon, DanhGia
- **Thực thể yếu**: DatPhong, SuDungDichVu, ThanhToanNhaHang, LichLamViec
- **Liên kết 3 ngôi**: GoiMon (KhachHang – NhaHang – ThucDon)
- **Quan hệ cha – con**: Nguoi → KhachHang, NhanVien
## III. Lược Đồ E-R


### 1. Các ràng buộc và yêu cầu dữ liệu:
## Các ràng buộc dữ liệu:
-Mã định danh duy nhất (Khóa chính):

- **Ghi chú**: Mỗi đối tượng trong hệ thống (Người, Khách hàng, Nhân viên, Phòng, Đặt phòng, Dịch vụ, Hóa đơn, …) đều cần có một mã duy nhất để phân biệt.
- **Diễn giải**: Ràng buộc này đảm bảo không có hai đối tượng nào trùng mã. Việc này giúp hệ thống quản lý chính xác, không nhầm lẫn dữ liệu.

## 📅 Các phần đã hoàn thành

- **Phần 1:** Đặt vấn đề & đăng ký đề tài  
- **Phần 2:** Mô tả kịch bản thế giới thực  
---
