# DESIGN.md — Chậm Rãi — Quán cà phê specialty (MSR-31)

- Task thiết kế: TEC-241 — Epic: TEC-240 "[Epic] Chậm Rãi — Quán cà phê specialty (MSR-31)"
- Repo: https://github.com/Muse-Soft/m-software-cham-rai
- Phạm vi: 1 landing page duy nhất, visual-first (ảnh lớn làm nội dung chính, nhiều khoảng trắng).
- Tài nguyên (máy đọc): site-cham-rai

## 1. Phong cách tham chiếu (chỉ MỘT)

**Quán cà phê specialty tối giản kiểu Bắc Âu ấm áp.**

Biểu hiện cụ thể, Dev phải theo đúng các thông số dưới đây, không thay bằng cảm nhận chung:

- Không gian: gỗ sáng, tường kem, bàn gỗ thấp, ghế vải lanh, ánh sáng tự nhiên qua cửa sổ lớn.
- Màu sắc: nền kem ấm làm chủ đạo, chữ nâu mực, điểm nhấn nâu đất cháy ở nút bấm, giá và tiêu đề phụ.
- Kiểu chữ: tiêu đề serif cổ điển có chân (Playfair Display), nội dung không chân rõ ràng (Be Vietnam Pro).
- Ảnh: ảnh chụp thật về hạt, cách pha và không gian quán, tông ấm, ánh sáng mềm, không dùng icon phẳng minh họa thay cho ảnh.
- Bố cục: mỗi khối tối đa 1 ảnh lớn + tối đa 2 cột chữ, khoảng trắng giữa các khối 80px trên desktop.

## 2. Bảng màu (8 mã hex, mỗi màu có vai trò rõ)

| Mã hex | Vai trò |
| --- | --- |
| `#FAF5EE` | Nền chính của toàn trang — màu chủ đạo |
| `#EFE7DA` | Nền phụ cho khối xen kẽ (Hành trình hạt cà phê, Lịch workshop) |
| `#FFFFFF` | Nền thẻ, nền form và nền thẻ thực đơn |
| `#2E2318` | Chữ chính: tiêu đề, nội dung chính — màu chủ đạo |
| `#6B5B4A` | Chữ phụ: mô tả, chú thích, giờ mở cửa mẫu |
| `#A85B2A` | Điểm nhấn: nút bấm chính, giá, tiêu đề phụ, đường gạch dưới tiêu đề — màu chủ đạo |
| `#D9CDBB` | Viền thẻ, đường kẻ phân tách khối |
| `#1F1710` | Nền tối cho một khối duy nhất: chân trang (footer) |

Ba màu gốc phải giữ đúng và là chủ đạo: nền `#FAF5EE`, chữ `#2E2318`, nhấn `#A85B2A`. Các màu phụ chỉ bổ sung, không lấn át ba màu gốc.

## 3. Font chữ và cỡ chữ

- Font tiêu đề: **Playfair Display** (Google Fonts, weight 700 cho H1/H2, 600 cho H3).
- Font nội dung: **Be Vietnam Pro** (Google Fonts, weight 400 cho nội dung, 500 cho nhãn, 700 cho nút).
- Cỡ chữ desktop:
  - H1: 56px, line-height 1.15
  - H2: 36px, line-height 1.2
  - H3: 22px, line-height 1.3
  - Nội dung: 17px, line-height 1.65
  - Chú thích / giá mẫu: 14px, line-height 1.5
  - Nút bấm: 16px, weight 700
- Cỡ chữ mobile (màn hình ≤ 768px):
  - H1: 40px
  - H2: 30px
  - H3: 20px
  - Nội dung: 16px, line-height 1.6
- Tiêu đề viết hoa đầu câu bình thường, không viết hoa toàn bộ; tiêu đề phụ dùng màu `#A85B2A`, cỡ 14px, letter-spacing 0.18em, viết hoa toàn bộ chỉ ở nhãn khối.

## 4. Quy tắc hình ảnh

- Ảnh lớn làm nội dung chính: mỗi khối có ít nhất 1 ảnh lớn, ảnh chiếm tối thiểu 45% chiều rộng khối trên desktop.
- Tông ảnh: đồng tông ấm — nền kem, gỗ sáng, nâu đất, ánh sáng tự nhiên mềm, không ảnh tông lạnh xanh xám.
- Ảnh mẫu: toàn bộ ảnh trên trang là ảnh mẫu, phải ghi rõ trong thuộc tính alt và chú thích dạng "(ảnh mẫu)". Trước khi đưa vào bản dựng, Dev kiểm tra từng ảnh mẫu trả về HTTP 200.
- Không dùng icon phẳng, không dùng ảnh minh họa vẽ tay thay cho ảnh chụp quán, hạt và đồ uống.
- Tỉ lệ khung hình bắt buộc theo từng khối (xem mục 5):
  - Hero: 16:9 trên desktop, phủ toàn màn hình (chiều cao 100vh), mobile chuyển sang 4:5.
  - Hành trình hạt cà phê: 3:2 cho mỗi chặng.
  - Thực đơn mẫu: 4:5 cho ảnh món.
  - Không gian quán: 4:3 cho ảnh lớn, 16:9 cho ảnh toàn cảnh.
  - Lịch workshop: 3:2 cho ảnh workshop.
  - Form đặt bàn/liên hệ: không bắt buộc ảnh; nếu có ảnh kèm thì dùng 4:3.

## 5. Bố cục từng khối (6 khối, đúng thứ tự)

Khoảng cách chung: padding khối 80px trên desktop, 64px trên mobile; chiều rộng nội dung tối đa 1120px, căn giữa.

### Khối 1 — Hero toàn màn hình

- Bố cục: ảnh hero toàn màn hình 16:9, lớp phủ tối 40% để chữ đọc được, chữ đặt ở phía trái, nút "Đặt bàn" màu `#A85B2A` và nút "Xem thực đơn" viền `#D9CDBB`.
- Nội dung: tên "Chậm Rãi", dòng giới thiệu "Quán cà phê specialty — pha chậm, uống chậm, sống chậm.", giờ mở cửa mẫu 7:30–21:30.
- Ảnh: 1 ảnh lớn toàn màn hình, tông ấm, alt "(ảnh mẫu)".

### Khối 2 — Hành trình hạt cà phê

- Bố cục: nền phụ `#EFE7DA`, 3 chặng ngang trên desktop (Trồng — Rang — Pha), mỗi chặng 1 ảnh 3:2 + tiêu đề H3 + mô tả ngắn.
- Nội dung: nguồn hạt mẫu (vùng trồng mẫu, độ rang mẫu), không bịa tên nông trại thật; mọi tên vùng chưa xác thực ghi là mẫu.
- Ảnh: 3 ảnh 3:2, đồng tông ấm, alt "(ảnh mẫu)".

### Khối 3 — Thực đơn mẫu

- Bố cục: nền `#FFFFFF`, lưới 3 cột trên desktop, mỗi món 1 thẻ: ảnh 4:5, tên món, mô tả 1 dòng, giá.
- Giá mẫu (ghi rõ "Giá mẫu" ngay dưới tiêu đề khối, và mỗi giá kèm chữ "Giá mẫu" ở lần xuất hiện đầu tiên trong khối):
  - Espresso — 45.000 đồng (Giá mẫu)
  - Pour Over — 65.000 đồng (Giá mẫu)
  - Latte — 60.000 đồng (Giá mẫu)
  - Cold Brew — 70.000 đồng (Giá mẫu)
  - Bánh mẫu kèm cà phê — 55.000 đồng (Giá mẫu)
- Ảnh: ảnh món 4:5, đồng tông ấm, alt "(ảnh mẫu)".

### Khối 4 — Không gian quán

- Bố cục: 1 ảnh lớn 16:9 toàn cảnh + 2 ảnh 4:3 (góc pha chế, góc ngồi đọc sách), chú thích ngắn dưới mỗi ảnh.
- Nội dung: mô tả không gian mẫu — bàn gỗ, ánh sáng tự nhiên, yên tĩnh để làm việc và trò chuyện; không ghi địa chỉ thật ở khối này.
- Ảnh: 3 ảnh, đồng tông ấm, alt "(ảnh mẫu)".

### Khối 5 — Lịch workshop

- Bố cục: nền phụ `#EFE7DA`, danh sách 3 workshop mẫu theo hàng ngang trên desktop, mỗi mục: ảnh 3:2, tên workshop, ngày mẫu, giờ mẫu, giá mẫu.
- Lịch mẫu:
  - Workshop "Pha Pour Over tại nhà" — Thứ 7, 9:00–11:00 — 250.000 đồng (Giá mẫu)
  - Workshop "Nếm thử hạt mới" — Chủ nhật, 9:00–10:30 — 150.000 đồng (Giá mẫu)
  - Workshop "Rang mẫu và phân biệt độ rang" — Thứ 7, 14:00–16:00 — 300.000 đồng (Giá mẫu)
- Ảnh: ảnh workshop 3:2, đồng tông ấm, alt "(ảnh mẫu)".

### Khối 6 — Form đặt bàn/liên hệ (chỉ giao diện)

- Bố cục: nền `#FFFFFF`, 2 cột trên desktop (trái: thông tin liên hệ, phải: form), 1 cột trên mobile.
- Thông tin liên hệ: địa chỉ [CẦN BỔ SUNG], điện thoại [CẦN BỔ SUNG], giờ mở cửa mẫu 7:30–21:30. Không bịa địa chỉ, số điện thoại thật; không gắn link tel: hay mailto: giả.
- Form chỉ giao diện, gồm 5 trường: họ tên, số điện thoại, ngày muốn đến, giờ muốn đến, số người + ghi chú. Nút "Gửi yêu cầu đặt bàn" chỉ chạy ở phía trình duyệt (preventDefault) và hiện dòng "Bản demo — form chưa gửi dữ liệu thật." Không có backend, không hiện thông báo thành công giả.
- Chân trang (footer): nền tối `#1F1710`, chữ `#FAF5EE`, nhắc lại tên quán, giờ mẫu, và địa chỉ/điện thoại [CẦN BỔ SUNG].

## 6. Quy tắc responsive / mobile (breakpoint 768px)

- Breakpoint duy nhất: 768px. Dưới hoặc bằng 768px: mọi lưới chuyển thành 1 cột.
- Header dính: `position: sticky; top: 0; height: 64px; background: #FAF5EE; z-index: 10`.
- Hero mobile: tỉ lệ 4:5, chữ H1 40px, nút xếp dọc, đủ rộng bấm bằng ngón tay.
- Ảnh mobile: giữ đúng tỉ lệ khung của mục 4, không cắt mất chủ thể chính.
- Khoảng cách khối mobile: 64px; khoảng cách giữa các thẻ trong lưới: 24px.
- Form mobile: các trường xếp dọc 1 cột, nút bấm rộng toàn bộ.

## 7. Quy tắc dữ liệu mẫu và [CẦN BỔ SUNG]

- Tất cả giá trên trang là giá mẫu, phải có dòng "Tất cả giá trên trang là giá mẫu." ở khối Thực đơn và khối Lịch workshop.
- Tất cả ảnh là ảnh mẫu, alt và chú thích ghi "(ảnh mẫu)".
- Địa chỉ thật, số điện thoại thật, tên nông trại thật, lịch workshop thật đều để placeholder [CẦN BỔ SUNG] cho đến khi PO/khách cung cấp — tuyệt đối không bịa dữ liệu thật.
- Form chỉ giao diện, không hứa hẹn "quán sẽ liên hệ xác nhận" khi chưa có backend.

## 8. Checklist nghiệm thu cho Dev và QA (đối chiếu khi dựng và kiểm thử)

- [ ] Đủ 6 khối đúng thứ tự: hero toàn màn hình, Hành trình hạt cà phê, thực đơn mẫu, không gian quán, lịch workshop, form đặt bàn/liên hệ.
- [ ] Đủ 8 mã hex ở mục 2, 3 màu gốc `#FAF5EE` / `#2E2318` / `#A85B2A` là chủ đạo.
- [ ] Font Playfair Display cho tiêu đề, Be Vietnam Pro cho nội dung, đúng cỡ chữ mục 3.
- [ ] Đúng phong cách tham chiếu: quán cà phê specialty tối giản kiểu Bắc Âu ấm áp.
- [ ] Đúng tỉ lệ khung mục 4, ảnh đồng tông ấm, alt "(ảnh mẫu)", ảnh mẫu kiểm tra HTTP 200.
- [ ] Mobile 768px: 1 cột, header dính 64px, hero 4:5.
- [ ] Form 5 trường, preventDefault, dòng "Bản demo — form chưa gửi dữ liệu thật.", không tel:/mailto: giả.
- [ ] Giá ghi "Giá mẫu"; địa chỉ/điện thoại ghi [CẦN BỔ SUNG].
