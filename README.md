# Bản tin của Điền — hướng dẫn đưa lên mạng

Web: https://thanhdien426-lab.github.io

Web tĩnh dùng Jekyll; GitHub Pages tự build, miễn phí. Máy chỉ cần cài Git.

## 1. Tạo tài khoản GitHub (nếu chưa có)

1. Vào https://github.com/signup, nhập email, mật khẩu, chọn **username** (ví dụ `dien-news`). Username sẽ nằm trong địa chỉ web.
2. Xác nhận email.

## 2. Tạo repo

1. Vào https://github.com/new
2. **Repository name**: gõ đúng `<username>.github.io` (ví dụ `dien-news.github.io`) → web sẽ ở `https://dien-news.github.io`, link ngắn, gọn.
3. Chọn **Public**. Không tick "Add a README". Bấm **Create repository**.

## 3. Cài Git trên Windows

Tải tại https://git-scm.com/download/win, cài với các lựa chọn mặc định. Mở lại Claude Code sau khi cài.

## 4. Đẩy code lên (Claude Code sẽ chạy giúp)

```
git init -b main
git add .
git commit -m "Khởi tạo Bản tin của Điền"
git remote add origin https://github.com/<username>/<username>.github.io.git
git push -u origin main
```

Lần push đầu, Windows sẽ mở cửa sổ đăng nhập GitHub — bạn tự đăng nhập trong cửa sổ đó (chọn "Sign in with your browser").

## 5. Bật GitHub Pages

Repo → **Settings** → **Pages** → *Build and deployment* → Source: **Deploy from a branch**, Branch: **main**, thư mục **/ (root)** → **Save**. Đợi 1–2 phút, web sẽ có ở `https://<username>.github.io`.

## Hằng ngày

Mở Claude Code trong thư mục này và gõ: **bản tin sáng nay**. Quy trình chi tiết nằm trong `CLAUDE.md`.
