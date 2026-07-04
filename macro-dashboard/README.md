# Macro Dashboard

Trang tổng hợp chỉ số kinh tế vĩ mô Việt Nam (CPI, tỷ giá, giá vàng) từ dữ liệu
đã crawl, kèm góc nhìn hoạch định tài chính và đề xuất phân bổ tài sản tham khảo.

**Live:** https://macro-dashboard-black.vercel.app

## Chạy local server

Từ thư mục gốc của repo (không phải trong `macro-dashboard/`):

```
node server.js
```

Mặc định chạy tại http://localhost:5500 (đổi cổng bằng biến môi trường `PORT`).

## Deploy lên Vercel

Thư mục này là site tĩnh thuần (không có server-side logic, `index.html` tự
`fetch()` `data.json`). Deploy trực tiếp từ thư mục `macro-dashboard/`:

```
cd macro-dashboard
npx vercel deploy --prod
```

## Cấu trúc

- `data.json` — dữ liệu thô đã crawl (tỷ giá Vietcombank, CPI/lạm phát cơ bản/giá vàng từ Tổng cục Thống kê), cùng đề xuất phân bổ tài sản theo 3 khẩu vị rủi ro.
- `index.html` — dashboard tĩnh, đọc `data.json` và tự render (không cần build step).
- `server.js` — static file server bằng Node.js thuần (không cần cài thêm package).

## Cập nhật dữ liệu

Sửa trực tiếp `data.json` với số liệu mới, hoặc mở rộng crawler để tự động ghi
đè file này định kỳ. Các mục còn thiếu, cần bổ sung nguồn: VN-Index, lãi suất
điều hành SBV, giá dầu thô thế giới, giá vàng SJC thời gian thực (xem mục
`data_gaps` trong `data.json`).
