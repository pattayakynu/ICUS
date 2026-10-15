# ICUS – website icusspa.com

Landing page tĩnh cho ICUS (spa, vệ sinh, phục hồi giày/túi hàng hiệu, 2 chi nhánh TP.HCM). Deploy trên Netlify, tên miền thật `https://icusspa.com/`.

## Cấu trúc

- `icus-landing-page/index.html`: **trang chính** (form đặt lịch Netlify, chatbot, SEO). Mọi sửa đổi làm ở đây.
- `icus-landing-page/assets/`: ảnh (có bản `.webp`), `css/tailwind.css` (CSS đã dịch sẵn), `icons/`.
- `netlify.toml`: cố định publish = `icus-landing-page`, 301 các trang trùng, header noindex/cache.
- `tailwind.config.js` + `src/tailwind.css` + `package.json`: sửa class trong HTML xong phải chạy `npm install && npm run build:css` và commit `assets/css/tailwind.css`.
- `google-apps-script/Code.gs`: đường gửi đơn dự phòng (Google Sheets + Gmail); gắn bằng biến `ICUS_GOOGLE_SCRIPT_URL` trong `index.html` (đang để trống).
- `index.html` ở gốc: bản cũ, không còn được deploy. `index.html.html`, `index_netlify_form_fixed.html`, 2 file zip: bản cũ/trùng, chờ chủ tiệm đồng ý mới xóa.
- `GHI-CHU-SUA-LOI.md`: nhật ký từng đợt sửa (Đợt 1–4) cho khách đọc. Mỗi lần sửa thêm, ghi một mục mới vào đây.

## Quy trình làm việc

- Repo gốc của khách: `phamminh2411003-prog/ICUS`. Repo này là bản fork `pattayakynu/ICUS`.
- Sửa trên nhánh `claude/peaceful-archimedes-v81ws7`. Netlify thử nghiệm `https://fixicus.netlify.app` deploy từ nhánh này.
- Thay đổi đi vào repo khách qua PR `phamminh2411003-prog/ICUS#1`; commit mới trên nhánh tự hiện trong PR.
- Trong code, đánh dấu chỗ sửa bằng ghi chú `[Sửa lỗi]`, `[SEO]` hoặc `[Tốc độ]`.

## Chatbot (bot từ khóa, không phải AI)

Trong `icus-landing-page/index.html`: `SOP_RESPONSES` (câu trả lời viết sẵn), `INTENT_RULES` (thứ tự = ưu tiên; quy tắc là danh sách từ khóa hoặc `{ all: [...] }`), `parseUserIntent`. So khớp nguyên từ; từ khóa có dấu chỉ khớp khi khách gõ có dấu. Giá, thời gian trong câu trả lời phải lấy từ kịch bản của tiệm, không tự thêm. Đã cân nhắc nâng lên chatbot AI (Claude/DeepSeek qua Netlify Function), chờ chủ tiệm quyết.

## Đang chờ chủ tiệm trả lời

1. Ưu đãi 1 tặng 1: "món bất kỳ" hay "gửi túi tặng vệ sinh giày"?
2. Miễn phí giao nhận: "từ 2 món" hay "đơn trên 3.000.000đ"?
3. Thời gian vệ sinh (2–3 / 2–5 / 3–5 ngày) và dán đế (1–2 / 3–4 ngày).
4. Mã xác minh Zalo: `...HqIdp0e...` (số 0) hay `...HqIdpOe...` (chữ O)?
5. "Thợ trên 5 năm" vs "EST. 2026"; các số "5.000+ món", "2.000+ khách".
6. Có xóa file zip và các trang trùng không.
7. Chọn chatbot AI hay không, dùng bên nào.

## Việc chủ tiệm tự làm (đã có hướng dẫn)

Merge PR #1; đặt `icusspa.com` làm primary domain + HTTPS trên Netlify; bật Forms → Submission notifications; Google Search Console + gửi sitemap; Google Business Profile cho 2 chi nhánh.
