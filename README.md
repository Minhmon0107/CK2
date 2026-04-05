# 📚 Ngân Hàng Câu Hỏi Ôn Tập Cuối Kỳ 2

> **THPT Phan Châu Trinh** · Năm học 2025 – 2026  
> 🌐 **Live site:** [https://minhmon0107.github.io/CK2/](https://minhmon0107.github.io/CK2/)

Trang ôn tập tổng hợp dành cho học sinh lớp 12, bao gồm ngân hàng câu hỏi trắc nghiệm và tự luận cho 5 môn học cuối kỳ 2. Toàn bộ trang web chạy tĩnh (static HTML/CSS/JS) – không cần backend, không cần cài đặt.

---

## 🗂 Cấu trúc dự án

```
CK2/
├── index.html          # Trang chủ – chọn môn học
├── shared.css          # CSS dùng chung (tokens, reset, utilities)
├── dia-ly.html         # Ôn tập Địa lý 12
├── lich-su.html        # Ôn tập Lịch sử 12
├── gdkt-pl.html        # Ôn tập GDKT & Pháp luật 12
├── tin.html            # Ôn tập Tin học 12
└── phap.html           # Ôn tập Tiếng Pháp 12
```

---

## 📖 Các môn học

| Môn | File | Màu chủ đạo | Nội dung |
|-----|------|-------------|----------|
| 🌏 **Địa lý** | `dia-ly.html` | Teal `#38d9a9` | Bài 22–25: Duyên hải NTB, Tây Nguyên, Đông Nam Bộ, ĐBSCL |
| 📜 **Lịch sử** | `lich-su.html` | Pink `#f472b6` | Bài 12–15: Đối ngoại VN & Hồ Chí Minh (Bộ Cánh Diều) |
| ⚖️ **GDKT – Pháp luật** | `gdkt-pl.html` | Amber `#facc15` | Nội dung GDKT & PL học kỳ 2 |
| 💻 **Tin học** | `tin.html` | Blue `#4f9cf9` | Chủ đề F (HTML/CSS), Chủ đề EICT (Mobirise) |
| 🇫🇷 **Tiếng Pháp** | `phap.html` | Purple `#c084fc` | Ngữ pháp, từ vựng, luyện tập kỳ 2 |

---

## 🎯 Dạng bài & tính năng

### Dạng 1 – Trắc nghiệm nhiều lựa chọn
- Chọn đáp án → phản hồi ngay (đúng/sai + đáp án đúng nếu sai)
- Theo dõi điểm số theo thời gian thực
- Nút **↺ Làm lại** để reset toàn bộ section

### Dạng 2 – Trắc nghiệm Đúng – Sai
- Mỗi câu có đoạn văn/bảng số liệu làm ngữ cảnh
- 4 mệnh đề (a, b, c, d) – chọn Đúng hoặc Sai từng mệnh đề
- Phản hồi màu ngay sau khi chọn

### Dạng 3 – Tự luận
- Câu hỏi mở – click vào để mở/đóng gợi ý lời giải chi tiết
- Không tự động chấm điểm; dành cho luyện viết và tự đánh giá

### Tính năng chung
| Tính năng | Mô tả |
|-----------|-------|
| 🧭 Điều hướng sidebar | Sticky sidebar với scroll-spy – highlight section đang xem |
| ↺ Reset từng section | Nút reset riêng cho mỗi dạng bài |
| 🏠 Nút về trang chủ | Fixed button ở góc trên trái trên mọi trang |
| 📱 Responsive | Sidebar ẩn trên màn hình nhỏ; layout stack trên mobile |
| 🔤 Font chất lượng | Be Vietnam Pro (body) + JetBrains Mono (code/số liệu) |
| 🌑 Dark mode | Giao diện nền tối toàn bộ, dễ đọc nhiều giờ |

---

## 🛠 Công nghệ sử dụng

| Layer | Chi tiết |
|-------|----------|
| **Markup** | HTML5 thuần – không framework |
| **Styling** | CSS3 + CSS Variables – không Tailwind, không preprocessor |
| **Logic** | Vanilla JavaScript (ES2020+) – không jQuery |
| **Font** | Google Fonts CDN (Be Vietnam Pro + JetBrains Mono) |
| **Hosting** | GitHub Pages (static, free) |
| **Build** | Không cần – mở thẳng file HTML trong trình duyệt |

---

## 🚀 Cách chạy trên máy cục bộ

```bash
# Clone về máy
git clone https://github.com/minhmon0107/CK2.git
cd CK2

# Cách 1 – Dùng VS Code Live Server (khuyên dùng)
code .
# Nhấn "Go Live" ở thanh trạng thái

# Cách 2 – Dùng Python HTTP server
python -m http.server 8080
# Mở http://localhost:8080 trong trình duyệt

# Cách 3 – Mở thẳng file
# Kéo index.html vào trình duyệt (một số tính năng có thể bị giới hạn do CORS)
```

---

## 📐 Hướng dẫn sử dụng `shared.css`

Để tránh lặp code giữa các file, thêm dòng này vào `<head>` của mỗi trang **trước** `<style>` nội bộ:

```html
<link rel="stylesheet" href="shared.css">
```

`shared.css` cung cấp:
- CSS variables (màu sắc, font, breakpoint)
- Global reset (`*`, `html`, `body`)
- Nút back/home (`.back-btn`, `.back-link`)
- Page header/hero wrapper
- Footer (`.page-footer`)
- Reset button (`.reset-btn`)
- Scrollbar styling
- Responsive helpers

Các style đặc thù của từng trang (layout sidebar, câu hỏi, animation...) vẫn nằm trong `<style>` nội bộ của mỗi file.

---

## 📝 Thêm câu hỏi mới

### Địa lý (`dia-ly.html`)
Dữ liệu lưu trong object `GEO`. Mỗi bài có 3 key: `mcq`, `ds`, `tln`.

```js
// Thêm câu MCQ vào bài 22, mức thông hiểu
GEO.bai22.mcq.thong_hieu.push({
  id: 23,  // số tiếp theo trong mảng
  text: "Nội dung câu hỏi?",
  options: { A: "Đáp án A", B: "Đáp án B", C: "Đáp án C", D: "Đáp án D" },
  correct: "A"
});
```

### Lịch sử (`lich-su.html`)
Dữ liệu lưu trong các mảng riêng theo bài và dạng:

```js
// Thêm câu MCQ vào bài 14
bai14_mc.push({
  q: "Nội dung câu hỏi?",
  opts: ["Đáp án A", "Đáp án B", "Đáp án C", "Đáp án D"],
  ans: 0  // chỉ số của đáp án đúng (0 = A, 1 = B, ...)
});
```

---

## 🎨 Bảng màu

```
Background  #0a0e1a   ██  Nền chính
Panel       #141c2e   ██  Card / sidebar
Border      #1e2d4a   ██  Đường viền

Địa lý      #38d9a9   ██  Teal
Lịch sử     #f472b6   ██  Pink
GDKT-PL     #facc15   ██  Amber
Tin học     #4f9cf9   ██  Blue
Tiếng Pháp  #c084fc   ██  Purple

OK / Đúng   #34d399   ██  Green
Sai / Lỗi   #f87171   ██  Red
Cảnh báo    #fbbf24   ██  Yellow
```

---

## 📋 Checklist nội dung

- [x] Địa lý – MCQ, Đúng/Sai, Tự luận số (TLN)
- [x] Lịch sử – MCQ, Đúng/Sai (Bài 14–15), Tự luận
- [ ] GDKT-PL – đang hoàn thiện
- [x] Tin học – MCQ, Đúng/Sai, Tự luận thực hành
- [ ] Tiếng Pháp – đang hoàn thiện

---

## 🤝 Đóng góp

1. Fork repo
2. Tạo branch mới: `git checkout -b them-cau-hoi-lich-su`
3. Commit thay đổi: `git commit -m "feat: thêm 5 câu MCQ bài 15"`
4. Push và mở Pull Request

---

## 📄 License

Tài liệu học tập nội bộ – **THPT Phan Châu Trinh**, Đà Nẵng.  
Không sử dụng cho mục đích thương mại.
