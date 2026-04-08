# Workflow: Tạo Slide Chuyên Nghiệp với Claude + NotebookLM + Canva

> Tạo slide đẹp, đúng brand identity, hoàn toàn bằng AI — không cần giỏi thiết kế.

---

## Công cụ sử dụng

| Công cụ | Vai trò |
|---|---|
| **Claude** | Phân tích ảnh mẫu → tạo design prompt chi tiết |
| **NotebookLM** | Research nội dung + generate slide (tính năng Slides) |
| **Canva Pro** | Chỉnh sửa text, hình ảnh qua tính năng Magic Layer |

---

## Quy trình 4 bước

### Bước 1 — Thu thập ý tưởng & tài sản thương hiệu

- Lên **Pinterest** tìm kiếm theo tên thương hiệu, ngành hàng, hoặc chủ đề slide
- Chụp/lưu những mẫu slide có phong cách phù hợp với brand
- Thu thập: logo, màu sắc, phông chữ, bố cục mong muốn

> 💡 Càng nhiều ảnh tham khảo → AI càng hiểu đúng phong cách bạn muốn

---

### Bước 2 — Tạo Design Prompt bằng Claude

1. Upload ảnh mẫu slide lên Claude (có thể upload nhiều ảnh)
2. Yêu cầu Claude tạo prompt thiết kế, ví dụ:

```
Giúp tôi tạo prompt AI để từ prompt này AI sẽ tạo slide 
có phong cách y hệt như này về: màu sắc, bố cục, 
cách thức trang trí, phông chữ, cỡ chữ...
để nói về [chủ đề của bạn].

Lưu ý:
- Hình minh họa phải thiên hướng nghệ thuật/abstract
- Hình phải lấy từ nguồn có sẵn, không tự tạo
- Tạo prompt bằng tiếng Anh
- Tạo 15 slides
```

3. Nhận prompt từ Claude → review và chỉnh sửa theo ý muốn:
   - Sửa tiêu đề
   - Thay đổi số lượng slide
   - Bỏ/thêm phần nội dung

> 💡 **Tại sao dùng Claude thay vì ChatGPT?**  
> Prompt Claude tạo ra sát hơn, chi tiết hơn → kết quả slide đẹp hơn đáng kể

---

### Bước 3 — Tạo Slide với NotebookLM

#### 3a. Chuẩn bị nội dung

Truy cập [NotebookLM](https://notebooklm.google.com) → Tạo notebook mới → Nạp nguồn tài liệu:

- Upload file PDF, Word, PowerPoint
- Dán link website hoặc link YouTube
- Kết nối Google Drive
- Dùng tính năng **Deep Research** để tự động cào nội dung theo chủ đề

#### 3b. Tạo slide — 2 cách

**Cách 1: Tạo ngay trong khung chat**

```
Giúp tôi tạo slide gồm 15 slides nói về việc [tên chủ đề],
trong đó nêu lên được [điểm 1], [điểm 2], [điểm 3]
theo phong cách thiết kế này: [dán design prompt từ Claude vào]
```

Sau khi AI trả về nội dung → yêu cầu tiếp: **"Tạo slide thiết kế luôn"**  
→ NotebookLM tự gọi tính năng Slides để render.

**Cách 2: Dùng nút SlideX (khuyến nghị)**

1. Nhấn nút **SlideX** ở sidebar trái
2. Chọn chế độ: **Detail Deck** (chi tiết)
3. Chọn độ dài: **Default**
4. Paste design prompt từ Claude vào ô prompt
5. Nhấn **Generate** → chờ 10–15 phút

> ✅ Cách 2 cho kết quả đẹp hơn đáng kể so với Cách 1

#### 3c. Xuất file

NotebookLM hỗ trợ xuất 2 định dạng:

| Định dạng | Ưu điểm | Nhược điểm |
|---|---|---|
| **PDF** | Giữ nguyên thiết kế | Không chỉnh sửa được |
| **PowerPoint (.pptx)** | Dùng để chiếu | Vẫn không chỉnh sửa được text/hình trực tiếp |

→ Giải pháp cho nhược điểm này: **dùng Canva ở bước 4**

---

### Bước 4 — Chỉnh sửa với Canva (Magic Layer)

#### Tại sao cần bước này?

File PDF/PPT từ NotebookLM không chỉnh sửa được trực tiếp.  
Canva Pro có tính năng **Magic Layer** giúp AI tách từng element (text, hình, khối màu) thành layer riêng để edit tự do.

#### Các bước thực hiện

1. Mở file PPT trong Canva → chọn tất cả trang → **Download as PNG**
2. Quay lại Canva → **Upload** toàn bộ ảnh PNG vừa tải
3. Mở từng ảnh → nhấn **Edit** → chọn **Magic Layer**
4. Chờ ~30 giây để AI tách layer
5. Giờ có thể:
   - Chỉnh sửa / xóa / thay text
   - Thay hình ảnh
   - Điều chỉnh màu sắc, kích thước từng element

> ⚠️ **Lưu ý:** Magic Layer có thể làm mất một số hiệu ứng bóng/3D → sửa tay thủ công (thêm viền, bo góc...) là cách khắc phục đơn giản nhất

---

## Lưu ý & Yêu cầu

- Cần **Canva Pro** để dùng tính năng Magic Layer
- NotebookLM và Claude đều có gói miễn phí dùng được
- Nội dung tiếng Việt: NotebookLM render không bị lỗi font
- Nếu AI tạo sai hình sản phẩm → thay thủ công trên Canva

---

## Tóm tắt nhanh

```
Pinterest (tìm mẫu)
    ↓
Claude (phân tích mẫu → tạo design prompt)
    ↓
NotebookLM (research nội dung + generate slide qua SlideX)
    ↓
Export PNG → Upload Canva Pro
    ↓
Magic Layer → chỉnh sửa tự do
    ↓
✅ Slide hoàn chỉnh
```
