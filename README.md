# Bài giảng đổi đơn vị đo lường — Toán lớp 4 (HTML trực quan)

Mỗi bài là **một file HTML độc lập**, mở bằng cách double-click, không cần cài đặt, không cần build.
Lấy cấu trúc mẫu từ [`bai-giang-toan-4`](https://github.com/HoaTran1127/bai-giang-toan-4)
(5 mục: dạy trực quan → ví dụ từng bước → luyện tập 7 cấp độ → chấm điểm → POST về Google Form).

## Danh sách bài

| Bài | File | Nội dung |
|---|---|---|
| Đổi đơn vị đo lường | [`index.html`](index.html) | Thang độ dài → cách đổi từng bước → thang khối lượng → **bẫy diện tích ×100** → luyện tập 7 cấp độ |

## Cách dùng trên lớp

1. Mở file HTML bằng Chrome / Edge (khuyến nghị) hoặc Cốc Cốc.
2. Trang dùng Tailwind CDN + Google Fonts, cần mạng cho **lần mở đầu**; các lần sau dùng cache.
3. Giáo viên chạy lần lượt Mục 1 → 4; Mục 5 mỗi học sinh **làm một lần rồi nộp**, kết quả tự gửi về bảng điểm của thầy.

## Cấu trúc bài "Đổi đơn vị đo lường"

| Mục | Nội dung | Cơ chế |
|---|---|---|
| 1 | Thang 7 bậc độ dài (km→mm), bấm 2 bậc xem hệ số đổi | Thang tương tác + máy đổi nhanh |
| 2 | Cách đổi độ dài từng bước | 4 ví dụ đổi được: 3 km = ? m, 500 cm = ? m, 2 km 5 hm, 7 dm = ? mm |
| 3 | Thang 7 bậc khối lượng (tấn→g) + ví dụ | 4 ví dụ: 3 tạ = ? kg, 5000 g = ? kg, 2 tấn 5 tạ, 9 kg = ? g |
| 4 | **Bẫy diện tích**: 1 m² = 100 dm² (không phải ×10!) | So sánh cạnh nhau + lưới 10×10 minh hoạ + 3 ví dụ |
| 5 | Luyện tập 7 cấp độ — **chấm 16 câu cấp 4·5·6·7, mỗi bạn chỉ làm 1 lần** | Gõ tên (Mai / Gia Linh / Trà Giang) → làm → nộp → **kết quả tự gửi về bảng điểm của thầy** |

## Quy tắc sư phạm cốt lõi

- **Độ dài / khối lượng**: đi **xuống** 1 bậc ×10, đi **lên** 1 bậc ÷10. Đếm bậc rồi nhân/chia 10^mũ số bậc.
- **Diện tích**: mỗi bậc **×100** (thấy chữ "vuông" là ×100). 1 m² = 100 dm² = 10 000 cm².
- **Thời gian KHÔNG ×10**: 1 giờ = 60 phút, 1 phút = 60 giây, 1 ngày = 24 giờ, 1 tuần = 7 ngày.

## Quy tắc chấm điểm Mục 5

- Cổng vào duy nhất là **ô ghi tên**; nhận đúng ba bạn Mai / Gia Linh / Trà Giang (không dấu cũng được, "giang" → Trà Giang).
- Cấp 1·2·3 là **ôn** (thứ tự bảng, đổi độ dài 2 chiều), bấm Kiểm tra bao nhiêu lần cũng được, không lưu.
- Cấp 4·5·6·7 = **16 câu được chấm** (khối lượng, dạng hỗn hợp, bẫy diện tích, lời văn); mỗi câu chỉ **ghi nhận lần đầu**.
- Nộp bài khi đủ 16 câu → trang dựng một **form ẩn POST thẳng về Google Form**, kết quả đổ vào Google Sheet.
- Sao: 3★ từ 85% (≥14/16) · 2★ từ 60% (≥10) · 1★ từ 30% (≥5) · dưới 5 câu = 0★.

## Cài đặt nơi nhận kết quả (làm 1 lần)

`FORM_ENDPOINT` và `ENTRY.*` trong `index.html` đang để trống — trang vẫn chạy, chỉ không gửi điểm.

1. Trên Google Drive: **nhân bản** form "Bảng điểm Cộng trừ nhẩm qua 10" (giữ nguyên 8 câu hỏi).
2. Mở `/viewform` của form mới → xem mã nguồn → lấy 8 `entry.*` theo tiêu đề câu.
3. Điền vào `FORM_ENDPOINT` (đổi `/viewform` → `/formResponse`) và `ENTRY` trong file, commit.
4. Giữ nguyên 3 chế độ như form cũ: **không thu thập email · TẮT giới hạn 1 lần trả lời · không đổi kiểu câu hỏi**.

## Mở bằng link (không cần tải file)

Bật **GitHub Pages** cho repo (Settings → Pages → Deploy from branch → main → /root),
học sinh chỉ cần bấm link:

```
https://hoatran1127.github.io/bai-giang-doi-don-vi/
```

## Kiểm định đã chạy

- Toàn bộ 28 đáp số (12 ôn + 16 chấm) dò tay khớp phép tính độc lập.
- Cú pháp JS kiểm tra bằng `node --check` tư duy (vm.Script), không lỗi.
- Luồng POST dùng chung mẫu đã kiểm chứng ở `bai-giang-toan-4` (curl ẩn danh → 200, Sheet nhận đủ 8 cột).

## Hạn chế đã biết

- Phụ thuộc `cdn.tailwindcss.com`: mở khi mất mạng và chưa cache thì giao diện vỡ.
- File tĩnh không xác nhận được Google đã nhận hay chưa, và không khoá được học sinh làm lại lần hai.
- Chưa có bài riêng cho đơn vị thời gian (mới chỉ 1 câu ở cấp 7) — làm bài tiếp theo nếu cần.
