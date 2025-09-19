# 🏨 Hệ thống Quản lý Khách sạn

## 📌 Giới thiệu
Trong bối cảnh ngành du lịch – khách sạn ngày càng phát triển, việc quản lý khách sạn hiệu quả đóng vai trò quan trọng trong việc nâng cao chất lượng dịch vụ và tối ưu hóa nguồn lực.  

Đề tài **“Quản lý khách sạn”** được xây dựng nhằm ứng dụng **cơ sở dữ liệu quan hệ (RDBMS)** để quản lý toàn diện hoạt động của một khách sạn: từ khách hàng, phòng, dịch vụ đến hóa đơn.  

Hệ thống giúp quy trình đặt phòng – thanh toán trở nên **nhanh chóng, chính xác và hiện đại hơn**, đồng thời hỗ trợ ban quản lý trong việc lập báo cáo, phân tích doanh thu, nâng cao trải nghiệm khách hàng.  

---

## 🎯 Mục tiêu hệ thống

### Chức năng
- Quản lý thông tin khách hàng, phòng và khuyến mãi.  
- Hỗ trợ đặt phòng, hủy phòng, xử lý yêu cầu đặc biệt.  
- Quản lý nhân viên, ca trực và phân công công việc.  
- Ghi nhận, theo dõi và bảo trì thiết bị khách sạn.  
- Cung cấp dịch vụ bổ sung (ăn uống, spa, giặt ủi,…).  
- Xuất hóa đơn và quản lý thông tin thanh toán.  
- Thống kê doanh thu, tỷ lệ lấp đầy phòng, dịch vụ phổ biến.  

### Phi chức năng
- Bảo mật thông tin khách hàng và giao dịch.  
- Tránh dư thừa dữ liệu, đảm bảo ràng buộc khóa ngoại.  
- Hỗ trợ sao lưu và phục hồi khi có sự cố.  
- Thiết kế trực quan, dễ sử dụng và nâng cấp.  
---
## 🏨 Kịch bản thế giới thực 
*Hệ thống quản lý khách sạn và khách đặt phòng sẽ bao gồm các nhóm chức năng để dễ tổ chức và triển khai hệ thống :*

---
## 1. Người
- **Người** : NguoiID, CCCD, HoTen, NgaySinh, GioiTinh, DiaChi, Sdt, email
- **Khách Hàng** : KhachHangID, NguoiID, HangThanhVien, DiemTichLuy
- **NhanVien** : NhanVienID, NguoiID, ChucVu, NgayVaoLam, Luong, BoPhanID
---
## 2. Phòng và Đặt Phòng
- **Phòng** : PhongID, SoPhong, LoaiPhong, GiaPhong, TrangThai
- **Đặt Phòng** : DatPhongID, KhachHangID, PhongID, Ngay Dat, NgayNhan, NgayTra, TienCoc, TrangThai
---
## 3. Dịch Vụ và Sử Dụng
- **Dịch Vụ** : DichVuID, TenDichVu, MoTa, DonGia
- **SuDungDichVu** : SuDungID, KhachHangID, DichVuID, NgaySuDung, SoLuong, TongTien
---
## 4. Nhà Hàng
- **Nhà hàng** : NhaHangID, TenNhaHang, ViTri, GioMoCua, GioDongCua
- **Thực Đơn** : MonAnID, TenMon, MoTa
- **Gọi Món** : GoiMonID, NhaHangID, MonAnID, KhachHangID, SoLuong, ThoiGianGoi, GhiChu, TrangThai, TongTien
- **ThanhToanNhaHang** : ThanhToanID, GoiMonID, PhuongThuc, NgayThanhToan, TongTien
---
## 5. Quản lý Nhân Sự
- **BoPhan** : BoPhanID, TenBoPhan, MoTa
- **LichLamViec** : LichID, NhanVienID, NgayLam, CaLam
---
## 6. Thanh Toán
- **HoaDon** : HoaDonID, DatPhongID, NguoiThanhToan, NgayLap, TongTien, TinhTrang, PhuongThuc
---
## 7. Đánh Giá
- **DanhGia** : DanhGiaID, KhachHangID, NoiDung, SoSao, NgayDanhGia
---
## 8. Thiết Bị và Sửa Chữa
- **ThietBi** : ThietBiID, TenThietBi, ViTri
- **BaoCao** : BaoCaoID, ThietBiID, NhanVienID, PhongID (có thể trong phòng hoặc không), TinhTrang, MoTa
- **SuaChua** : SuaChuaID, ThietBiID, NgaySua, ChiPhi
---
## 📅 Các phần đã hoàn thành

- **Phần 1:** Đặt vấn đề & đăng ký đề tài  
- **Phần 2:** Mô tả kịch bản thế giới thực  
---
