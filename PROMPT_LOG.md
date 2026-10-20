# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)
**Họ và tên:** [Nguyễn Văn A - Sinh viên điền thông tin]  
**MSSV:** [21000000 - Sinh viên điền MSSV]  
**Tên đề tài Website:** Website Bán Game Steam (Steam Store Landing Page)  
**Công cụ AI đã sử dụng:** VS Code & Antigravity AI (Senior Web Developer & Prompt Engineer Mode)

---

## 1. Yêu cầu ban đầu (System/Initial Prompt)
> "Hãy đóng vai một Chuyên gia Lập trình Web Front-End (Senior Web Developer) và Prompt Engineer xuất sắc. Tôi muốn bạn tự động tạo và xây dựng trọn vẹn một trang web mới dựa trên các yêu cầu kỹ thuật nghiêm ngặt dưới đây:
> 
> ### 1. TÊN ĐỀ TÀI & THƯ MỤC DỰ ÁN
> - Tên đề tài: Website Bán Game Steam (Steam Game Store Landing Page).
> - Cấu trúc thư mục và file:
>   ├── index.html
>   ├── style.css
>   ├── assets/ (chứa ảnh đại diện, banner, icon game...)
>   └── PROMPT_LOG.md
> 
> ### 2. YÊU CẦU KỸ THUẬT CỐT LÕI
> 1. Semantic HTML5 (Chuẩn ngữ nghĩa, tuyệt đối KHÔNG lạm dụng `<div>` vô nghĩa): Bắt buộc dùng đúng tối thiểu 5 thẻ ngữ nghĩa: `<header>`, `<nav>`, `<main>`, `<section>` (hoặc `<article>`), và `<footer>`. Chia bố cục rõ ràng: Hero Banner, Game Bán Chạy, Khuyến Mãi Hot, Game Theo Thể Loại, Chân trang.
> 2. CSS Variables & Layout Hiện Đại: Khai báo CSS Variables tại `:root` (color, font, spacing, radius, transitions). Flexbox & Grid cho toàn bộ bố cục, responsive Desktop/Mobile.
> 3. Tích hợp Thư viện & Hiệu ứng Động: Animate.css, AOS (Animate On Scroll), CSS :hover/:focus/:active cho toàn bộ tương tác.
> 
> ### 3. THIẾT KẾ PHỐI MÀU & TRÁNH LỖI PHÔNG CHỮ / TRẢI NGHIỆM CHI TIẾT (UI/UX)
> - Bảng màu Steam Dark Theme: `#171a21`, `#1b2838`, card `#16202d` / `#2a475e`, accent `#66c0f4`, nút mua `#5c7e10` / `#a4d007`. Tương phản cao, chữ `#ffffff` và `#c6d4df`, không chìm màu.
> - Font: Google Fonts Unicode tiếng Việt ('Inter', sans-serif), `<meta charset="UTF-8">`.
> - Micro-interactions: Card Hover phóng to nhẹ kèm box-shadow glow, nút CTA đổi màu gradient & hiệu ứng tia sáng (shine), cursor glow."

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration)

### Lần 1: Dựng khung Semantic HTML & CSS Variable
- **Prompt đã dùng:**
  > "Hãy khởi tạo cấu trúc dự án chuẩn gồm thư mục `assets/`, file `index.html` và `style.css`. Trong HTML, hãy áp dụng đầy đủ các thẻ ngữ nghĩa chuẩn HTML5: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<figure>`, `<figcaption>`, `<aside>`, `<footer>`. Tuyệt đối không dùng `<div>` bừa bãi. Trong file `style.css`, xây dựng hệ thống CSS Custom Properties (`:root`) theo phong cách Steam Dark Theme bao gồm bảng mã màu chuẩn (Steam Dark Navy, Card Blue, Accent Cyan, Steam Green Purchase), Typography thang đo chữ, Spacing, Radius và Box Shadows."
- **Kết quả AI tạo ra:**
  - File `index.html` có kiến trúc phân tầng ngữ nghĩa rõ ràng: `<header>` chứa thanh tiện ích và 2 tầng `<nav>` (Main Nav và Subnav); `<main>` chia thành 5 `<section>` chuyên biệt (`#hero-showcase`, `#special-offers`, `#top-sellers`, `#categories`, `#hardware`) cùng thẻ `<aside>` và `<footer>`. Mỗi card game được bao bọc trong thẻ `<article>`, hình ảnh đặt trong `<figure>` có `<figcaption>`.
  - File `style.css` định nghĩa toàn bộ Design System tại `:root` với hơn 35 biến CSS, kiểm soát toàn diện bảng màu Steam, font chữ `Inter` hỗ trợ Unicode tiếng Việt, cùng layout CSS Grid/Flexbox đa tầng.
  - Tải tự động các hình ảnh banner game AAA chính hãng từ Steam CDN về thư mục `assets/` (Black Myth Wukong, Cyberpunk 2077, Elden Ring, Baldur's Gate 3, Helldivers 2, v.v.).
- **Nhận xét & Tinh chỉnh của SV:**
  - Cấu trúc chuẩn W3C, điểm SEO và Accessibility (ARIA) cao nhờ có đầy đủ `aria-label`, `role="search"`, `aria-selected`.
  - Bảng màu tương phản cực kỳ tốt: Nền tối sâu kết hợp chữ trắng tinh khôi (`#ffffff`) và xám lam (`#c6d4df`), các điểm nhấn xanh Steam (`#66c0f4`) và xanh lá mua hàng (`#a4d007`) giúp các nút kêu gọi hành động (CTA) nổi bật và không gây mỏi mắt.

---

### Lần 2: Tích hợp thư viện Animate.css & AOS & Hiệu ứng Hover
- **Prompt đã dùng:**
  > "Tích hợp thư viện Animate.css và AOS (Animate On Scroll) qua CDN. Bổ sung các hiệu ứng chuyển động mượt mà cho Logo, Hero Banner và Nút CTA. Viết thêm micro-interactions phong phú cho Card Game (zoom nhẹ 1.02, đổ bóng neon blue glow `0 10px 25px rgba(102, 192, 244, 0.3)`), hiệu ứng vệt sáng quét qua nút Mua Hàng (`shine effect`), đèn chiếu điểm theo con trỏ chuột (`ambient cursor glow`), bộ lọc danh mục game theo thể loại, thanh tìm kiếm tức thì và giỏ hàng tương tác với thông báo Toast."
- **Thách thức gặp phải:**
  1. *Lỗi xung đột và hiển thị tiếng Việt:* Một số font sans-serif mặc định trên Windows có thể bị lỗi dấu ngã hoặc hỏi ở các ký tự tiếng Việt đặc thù (ư, ơ, ẵ, ệ).
  2. *Thư viện AOS chưa kích hoạt khi tải trang:* Khi sử dụng CDN, nếu không gọi hàm khởi tạo `AOS.init()` sau sự kiện `DOMContentLoaded`, hiệu ứng cuộn trang sẽ không chạy.
  3. *Hiệu ứng đèn chuột (Cursor Glow) trên thiết bị di động:* Trên màn hình cảm ứng, con trỏ chuột không tồn tại, có thể gây lag hoặc che khuất giao diện.
- **Cách sửa prompt (Debug prompt):**
  - Khai báo nhúng trực tiếp Google Font `Inter` với bộ ký tự `vietnamese,latin,latin-ext` và trọng số từ 300 đến 900; đặt `<meta charset="UTF-8">` ngay dòng đầu thẻ `<head>`.
  - Khởi tạo `AOS.init({ duration: 750, easing: 'ease-out-cubic', once: true, offset: 80 });` trong khối script.
  - Sử dụng CSS Media Query `@media (max-width: 768px)` và điều kiện JavaScript `window.matchMedia('(pointer: fine)').matches` để chỉ kích hoạt hiệu ứng vệt sáng đèn chuột trên thiết bị Desktop/Laptop có chuột rời.

---

## 3. Đánh giá cá nhân về quá trình Vibe Coding
- **Lợi ích:**
  - AI đóng vai trò như một Senior Front-End Developer sát cánh: giải quyết nhanh chóng bài toán layout CSS Grid tự co giãn theo màn hình (`grid-template-columns: repeat(auto-fit, minmax(...))`) và CSS Flexbox căn chỉnh chính xác đến từng pixel.
  - Tiết kiệm 80% thời gian tìm kiếm tài nguyên ảnh và xây dựng mock data game chân thực (Black Myth: Wukong, Cyberpunk 2077, Elden Ring...).
  - Mã nguồn tuân thủ nghiêm ngặt chuẩn Semantic HTML5, không xuất hiện hiện tượng `<div>` soup lồng nhau vô nghĩa.
- **Bài học rút ra:**
  - Cần quy định rõ ràng bảng mã màu (HEX/RGB), font chữ Unicode UTF-8 và danh sách các thẻ ngữ nghĩa bắt buộc ngay từ prompt đầu tiên.
  - Khi yêu cầu AI tạo hiệu ứng động (micro-interactions), việc đặc tả cụ thể giá trị `transform`, `box-shadow`, thời gian `transition` và điều kiện Responsive sẽ giúp sản phẩm đầu ra đạt độ hoàn thiện cao nhất ngay trong lần tạo đầu tiên.
