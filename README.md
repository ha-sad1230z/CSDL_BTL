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
### Khách hàng & Phòng
- **KhachHang**: quản lý khách hàng  
  `KhachHang (KhachHangID, CCCD, HoTen, GioiTinh, SDT, Email, DiaChi)`

- **Phong**: thông tin phòng  
  `Phong (PhongID, SoPhong, LoaiPhong, GiaPhong, TrangThai)`

- **KhuyenMai**: chương trình khuyến mãi / mã giảm giá  
  `KhuyenMai (KhuyenMaiID, TenCT, TyLeGiam, NgayBatDau, NgayKetThuc)`

- **DatPhong** *(liên kết 3 ngôi giữa KhachHang – Phong – KhuyenMai)*  
  `DatPhong (KhachHangID, PhongID, KhuyenMaiID, NgayDat, NgayNhan, NgayTra, YeuCau, TrangThaiDat)`

---

### Thanh toán
- **NguoiThanhToan**: thông tin người/đơn vị thanh toán  
  `NguoiThanhToan (NguoiTTID, HoTen, SDT, Email, DiaChi, Loai)`

- **HoaDon**: hóa đơn thanh toán  
  `HoaDon (HoaDonID, DatPhongID, NguoiTTID, TongTien, PTThanhToan, TinhTrangThanhToan, NgayThanhToan, GhiChu)`

---

### Nhân sự
- **NhanVien**: thông tin nhân viên  
  `NhanVien (NhanVienID, HoTen, GioiTinh, NgaySinh, SDT, Email, DiaChi, ChucVu)`

- **CaTruc**: ca làm việc  
  `CaTruc (CaTrucID, NhanVienID, TenCa, NhiemVu, GioBatDau, GioKetThuc)`

---

### Thiết bị & Bảo trì
- **ThietBi**: danh mục thiết bị  
  `ThietBi (ThietBiID, TenThietBi)`

- **BaoCao**: báo cáo sự cố hoặc tình trạng thiết bị  
  `BaoCao (BaoCaoID, ThietBiID, ViTri, MoTa, NgayBaoCao, NguoiBaoCao)`

- **BaoTri** *(thực thể yếu, phụ thuộc ThietBi)*: lịch sử bảo trì  
  `BaoTri (BaoTriID, BaoCaoID NULL, ThietBiID, LoaiBaoTri, NgayBaoTri, ChiPhi, NoiDung)`

---

### Dịch vụ khách sạn
- **DichVuKhachSan**: dịch vụ cung cấp  
  `DichVuKhachSan (DichVuID, TenDichVu, GiaDichVu)`

- **DichVuSuDung** *(thực thể yếu, phụ thuộc KhachHang & DichVuKhachSan)*  
  `DichVuSuDung (SuDungID, KhachHangID, DichVuID, NgaySuDung, SoLuong, ThanhTien)`

---

### Nhà cung cấp & Hợp đồng
- **NhaCungCap**: thông tin nhà cung cấp  
  `NhaCungCap (NCCID, TenNCC, LoaiHangHoa, SDT, DiaChi)`

- **HopDong**: hợp đồng với nhà cung cấp  
  `HopDong (HopDongID, NCCID, NgayKy, GiaTri, NoiDung)`

---

### Đánh giá
- **DanhGia** *(thực thể yếu, phụ thuộc KhachHang)*  
  `DanhGia (DanhGiaID, KhachHangID, PhongID, DichVuID, DiemSo, NhanXet)`

---

## ⚙️ Quy trình nghiệp vụ minh họa
1. Khách hàng đặt phòng → tạo bản ghi trong **DatPhong**.  
2. Nếu có khuyến mãi, hệ thống liên kết với **KhuyenMai**.  
3. Sau khi khách sử dụng dịch vụ và trả phòng → phát sinh **HoaDon**.  
4. Người thanh toán có thể là chính khách, bạn bè hoặc công ty → lưu tại **NguoiThanhToan**.  
5. Nhân viên tiếp nhận sự cố thiết bị → lập **BaoCao**, sau đó ghi nhận **BaoTri**.  
6. Ban quản lý có thể xem báo cáo doanh thu, tình trạng phòng, lịch sử dịch vụ và bảo trì.  

---

## 📊 Phân loại thực thể
- **Thực thể Mạnh**: KhachHang, Phong, KhuyenMai, NguoiThanhToan, HoaDon, NhanVien, CaTruc, ThietBi, BaoCao, DichVuKhachSan, NhaCungCap, HopDong.
- **Thực thể Yếu**: BaoTri, DichVuSuDung, DanhGia.
- **Liên kết 3 ngôi**: DatPhong (KhachHang – Phong – KhuyenMai).

---


## 📅 Các phần đã hoàn thành

- **Phần 1:** Đặt vấn đề & đăng ký đề tài  
- **Phần 2:** Mô tả kịch bản thế giới thực  
---
