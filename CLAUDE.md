# Bản tin của Điền

Web tin tức cá nhân, tĩnh, chạy bằng Jekyll mà GitHub Pages tự build (không cần cài Node/Ruby trên máy). Chỉ cần Git.

## Cấu trúc

- `_issues/YYYY-MM-DD.md` — mỗi số bản tin một file. Tên file chính là link: `_issues/2026-10-25.md` → `/2026-10-25/`.
- `index.html` — trang chủ, tự lấy số có `date` mới nhất.
- `luu-tru.html` — trang lưu trữ (`/luu-tru/`), tự liệt kê mọi số theo tháng.
- `_layouts/`, `_includes/issue-body.html`, `assets/style.css` — giao diện (có chế độ tối).
- `_config.yml` — cấu hình. `SITE_URL` bên dưới là địa chỉ web thật.

Trang chủ và lưu trữ **tự cập nhật** khi thêm file mới vào `_issues/` — không cần sửa tay.

SITE_URL: https://thanhdien426-lab.github.io
Repo: https://github.com/thanhdien426-lab/thanhdien426-lab.github.io (nhánh `main`)

Git và GitHub CLI cài qua winget. Nếu shell chưa nhận PATH, gọi trực tiếp `& "C:\Program Files\Git\cmd\git.exe"` và `& "C:\Program Files\GitHub CLI\gh.exe"`.

## Quy trình "bản tin sáng nay"

Khi người dùng gõ **"bản tin sáng nay"** (hoặc "bản tin DD/MM"), làm lần lượt:

1. **Xác định ngày**: ngày hôm nay theo giờ Việt Nam (UTC+7), trừ khi người dùng nêu ngày khác. Nếu `_issues/<ngày>.md` đã có, hỏi người dùng muốn ghi đè hay bổ sung.
2. **Tìm tin trên web** theo cấu trúc ở dưới. Search từng chủ đề riêng (không gộp nhiều chủ đề vào một query), query tiếng Việt kèm ngày cụ thể, ví dụ `giá vàng SJC hôm nay 25/10/2026`. Mở bài gốc (WebFetch) khi cần xác nhận số liệu.
3. **Viết file** `_issues/<YYYY-MM-DD>.md` theo mẫu ở dưới.
4. **Commit và push**:
   ```
   git add _issues/<YYYY-MM-DD>.md
   git commit -m "Bản tin <DD/MM/YYYY>"
   git push
   ```
   Nếu push lỗi (chưa đăng nhập, mất mạng), báo lỗi nguyên văn cho người dùng, không thử cách vòng.
5. **Báo link** số mới: `SITE_URL/<YYYY-MM-DD>/`. GitHub Pages cần khoảng 1–2 phút để cập nhật sau khi push.

## Mẫu file

```markdown
---
title: "Bản tin sáng 25/10/2026"
date: 2026-10-25
summary: "Một câu tóm tắt 2–3 tin lớn nhất — hiện ở trang lưu trữ và khi chia sẻ link."
---

## 🔥 Tin nóng trong ngày
...
```

Không viết lại tiêu đề H1 hay dòng disclaimer trong file — layout đã tự thêm. Các mục dùng `##`, tin con dùng gạch đầu dòng hoặc `###`.

## Cấu trúc bản tin (đúng thứ tự)

1. **🔥 Tin nóng trong ngày** (luôn đứng đầu): 5–7 tin nổi bật nhất, lấy từ tin đọc nhiều trên VnExpress, Dân trí, Tuổi Trẻ, Thanh Niên, cùng sự kiện quốc tế lớn trong đêm. Không bỏ qua chủ đề nào, kể cả giải trí hay xã hội.
2. **💰 Kinh tế**: vàng SJC, vàng nhẫn và vàng thế giới; bạc; VN-Index, HNX; lãi suất huy động; Bitcoin; kết quả kinh doanh doanh nghiệp lớn.
3. **📉 Vĩ mô & Dòng tiền**: tỷ giá (trung tâm NHNN, tự do, ngân hàng); khối ngoại mua/bán ròng; lãi suất theo 3 tầng (điều hành / liên ngân hàng–OMO / huy động–cho vay); dầu Brent, WTI; DXY; Fed và số liệu Mỹ; Trung Quốc.
4. **🏛️ Chính trị**
5. **🤖 Công nghệ/AI**
6. **⚽ Thể thao**
7. **🌧️ Thiên tai & Thời tiết**
8. **🎓 Giáo dục**
9. **🏥 Sức khỏe**
10. **⚔️ Chiến sự & Sự kiện quốc tế**: các xung đột lớn và sự kiện ảnh hưởng mạnh đến thị trường.
11. **💡 Ghi chú học vĩ mô**: giải thích ngắn một mối liên hệ nhân quả trong tin hôm nay.
12. **⏳ Chưa công bố hôm nay** (gói các chỉ số chưa có số mới vào một dòng) và **📅 Lịch tuần tới**.
13. **🔗 Nguồn**: danh sách link đầy đủ các bài đã dùng.

## Quy tắc nội dung

- **Không bịa số liệu.** Số nào không tìm được thì ghi "chưa có dữ liệu".
- **Ghi rõ thời điểm** của số liệu, ví dụ "(chốt phiên 24/10)", "(sáng 25/10)".
- **Các số liệu chính in đậm** (`**...**`).
- Tiếng Việt, ngắn gọn, có cấu trúc, dễ đọc trên điện thoại. Bảng nhỏ được dùng cho giá vàng/tỷ giá.
- Chỉ đưa link khi đã có URL bài viết cụ thể; không dùng link trang chủ chuyên mục như thể là link bài.
- Không lặp một số liệu ở hai mục (ví dụ vàng thế giới chỉ nêu một lần).
- Cuối bản tin luôn có mục Nguồn. Dòng "Thông tin tham khảo, không phải khuyến nghị đầu tư" do layout tự thêm.

## Nguồn ưu tiên

- Tin tức: VnExpress, Dân trí, Tuổi Trẻ, Thanh Niên, VietnamNet, VOV.
- Thị trường/vĩ mô: CafeF, VnEconomy, Vietstock, NHNN (sbv.gov.vn), Tổng cục Thống kê, Investing.com, Reuters.
