# Thiệp 20/10 Diên Hồng – mã nguồn

Trang tĩnh, một tệp HTML tự chứa (Three.js tải từ CDN). Không cần build.

## Cấu trúc
```
index.html            trang thiệp (CSS + JS + nội dung)
og-image.png          ảnh xem trước 1200×630 cho Zalo/Facebook
video/thiep-2010.mp4  video kỷ niệm (720×720, H.264/AAC, faststart)
video/poster.jpg      ảnh chờ của video
```

## Chạy thử trên máy
```
cd thiep-2010
python3 -m http.server 8080      # rồi mở http://localhost:8080
```
(Cần mở qua máy chủ HTTP, không mở trực tiếp file:// vì video sẽ không phát.)

## Tự lưu trữ trên tên miền riêng (Netlify / Vercel / Cloudflare Pages / GitHub Pages)
1. Tải toàn bộ thư mục này lên dịch vụ (kéo thả cả thư mục).
2. Mở `index.html`, điền địa chỉ đầy đủ vào `og:url` và đổi `og:image` thành đường dẫn tuyệt đối, ví dụ `https://ten-mien.vn/og-image.png`.
3. Gửi đường link HTTPS vào Zalo.

## Thay video / nội dung
- Đổi video: thay tệp `video/thiep-2010.mp4` (hoặc đặt địa chỉ HTTPS khác vào `CONFIG.VIDEO_URL` ở đầu phần `<script>` trong `index.html`). Thay `video/poster.jpg` nếu muốn ảnh chờ khác.
- Ngày, nhãn các trang: `CONFIG.EVENT_DATE`, `CONFIG.STEP_LABELS`.
- Lời chúc: các đoạn trong các `<section class="screen">` (màn 2, 4, 5, 6).

## Hành vi
- 6 màn: Mở thiệp → Lời chào → Video → Thông điệp → Chạm cho hoa nở → Lời kết.
- Điều hướng: nút mũi tên, chấm tiến trình, vuốt dọc, phím mũi tên, cuộn chuột. Có thể nhảy thẳng tới một màn bằng `#man3`, `#man4`… ở cuối đường link.
- Âm thanh hiệu ứng tắt mặc định, bật bằng nút loa góc trên. Video chỉ phát khi nhấn.
- Tự giảm hiệu ứng 3D trên máy yếu; không có WebGL thì dùng cánh hoa CSS; tôn trọng `prefers-reduced-motion`.
