# Bài 5 : Chuẩn hóa quy trình báo cáo sự cố an ninh mạng


PHẦN 1: PHÂN TÍCH
Cơ chế "Google Search của bảng tính" qua AutoFilter:

Tìm kiếm theo từ khóa: Ô search trong AutoFilter cho phép gõ chuỗi ký tự để lọc nhanh dữ liệu tương tự nhập truy vấn trên Google.

Hỗ trợ ký tự đại diện (Wildcard): Dùng * (đại diện cho chuỗi bất kỳ) hoặc ? (đại diện cho 1 ký tự) để tìm kiếm linh hoạt (ví dụ: *Trojan*).

Lọc có điều kiện: Hỗ trợ toán tử logic (Contains, Begins With, Greater Than...) tương tự bộ lọc tìm kiếm nâng cao.

Truy vấn không phá hủy: Chỉ ẩn các dòng không khớp tiêu chí chứ không xóa dữ liệu gốc, giúp trích xuất thông tin sự cố nhanh chóng.

PHẦN 2: TRIỂN KHAI
1. Excel (Tra cứu mã độc với VLOOKUP & TRIM)
Xử lý: Dữ liệu log thô hay dính dấu cách thừa ở đầu/cuối khiến hàm dò tìm bị lỗi #N/A. Dùng TRIM bọc ô tìm kiếm để chuẩn hóa.

Công thức tại bảng Nhật ký hệ thống:

Lấy Tên mã độc:

```Excel
=VLOOKUP(TRIM(A2), 'Cơ sở dữ liệu virus'!$A$2:$C$50, 2, FALSE)
```
Lấy Mức độ nguy hại:

Excel
=VLOOKUP(TRIM(A2), 'Cơ sở dữ liệu virus'!$A$2:$C$50, 3, FALSE)
2. Word (Auto TOC & Navigation Pane)
Gán Heading: Bôi đen các tiêu đề mục lớn chọn Heading 1, mục con chọn Heading 2 (trong tab Home).

Quản lý cấu trúc: Vào thẻ View > tích chọn Navigation Pane để theo dõi và nhảy nhanh giữa các trang báo cáo.

Tạo mục lục tự động: Vào thẻ References > chọn Table of Contents > chọn mẫu tự động. Khi văn bản dài thêm, click chuột phải vào mục lục > chọn Update Field (F9) > Update entire table.

3. PowerPoint (Chiến lược phòng thủ 3 tầng)
Quy chuẩn Font: Toàn bộ slide dùng font Montserrat hoặc Inter (không dùng Times New Roman).

Nội dung sơ đồ phân cấp :

Tầng 1 (Ngoại vi): Firewall thế hệ mới (NGFW), WAF, hệ thống chống DDoS.

Tầng 2 (Mạng nội bộ & Thiết bị): Phân vùng mạng (VLAN), IDS/IPS, Antivirus, giải pháp EDR.

Tầng 3 (Dữ liệu & Con người): Mã hóa dữ liệu, Backup cô lập, xác thực đa yếu tố (MFA), đào tạo nhận thức an toàn thông tin.
