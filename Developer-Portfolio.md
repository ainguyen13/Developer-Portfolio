# GitHub Pages Portfolio & App Landing Architecture

Tài liệu này hướng dẫn cách thiết lập một repository duy nhất trên GitHub Pages để làm trung tâm lưu trữ (hub) cho toàn bộ hệ sinh thái các ứng dụng cá nhân (Indie Developer Portfolio). Mục tiêu là có một nơi quản lý tập trung, có thể dễ dàng thêm các app mới về sau mà không cần tạo nhiều repository.

## 1. Cách đặt tên Repository
Tạo một Repository public trên GitHub với tên chính xác là: 
`[username-của-bạn].github.io`
*(Ví dụ: `ainguyen13.github.io`)*

GitHub sẽ tự động host repository này thành một trang web gốc với domain là `https://[username-của-bạn].github.io`.

## 2. Cấu trúc thư mục (Folder Structure)

Bên trong repository, tổ chức các file theo cấu trúc sau:

```text
[username].github.io/
│
├── index.html              <-- (1) Trang cá nhân/Portfolio giới thiệu bạn là ai
├── css/                    <-- CSS dùng chung
├── assets/                 <-- Logo, avatar của bạn
│
└── apps/                   <-- (2) Thư mục "tổng quản" chứa tất cả app của bạn
    │
    ├── offloop/            <-- App đầu tiên: OffLoop
    │   ├── index.html      <-- Landing page giới thiệu app OffLoop (có link tải app)
    │   ├── privacy.html    <-- Privacy Policy của OffLoop
    │   ├── terms.html      <-- Terms of Use của OffLoop
    │   └── assets/         <-- Screenshot, icon của app OffLoop
    │
    ├── app-thu-hai/        <-- App thứ 2 sau này
    │   ├── index.html
    │   ├── privacy.html
    │   └── terms.html
    │
    └── app-thu-ba/         <-- App thứ 3 sau này...
```

## 3. Kết quả URLs

Với cấu trúc trên, các đường link của bạn sẽ được tự động định tuyến (routing) rất đồng bộ:

- **Trang cá nhân:** `https://[username].github.io`
- **Trang giới thiệu OffLoop:** `https://[username].github.io/apps/offloop`
- **Link App Store cho Privacy:** `https://[username].github.io/apps/offloop/privacy.html`
- **Link App Store cho Terms:** `https://[username].github.io/apps/offloop/terms.html`

## 4. Tại sao cấu trúc này tối ưu?

1. **Quản lý tập trung (Single Source of Truth):** Duy nhất 1 repository. Thêm app mới chỉ việc tạo 1 folder mới ném vào thư mục `apps/`.
2. **Xây dựng thương hiệu (Branding):** Domain chính là portfolio của bạn. Người dùng vào xem 1 app có thể dễ dàng điều hướng về trang chủ để xem các app khác của bạn.
3. **Mở rộng dễ dàng:** Hoàn toàn miễn phí. Nếu sau này mua custom domain (ví dụ `ainguyen.dev`), toàn bộ link sẽ tự chuyển thành `ainguyen.dev/apps/offloop/...` mà không gãy link cũ.

## 5. Mẫu HTML cơ bản cho Policy/Terms

Dùng đoạn HTML siêu nhẹ này cho các trang Privacy Policy / Terms of Use để đảm bảo load nhanh và tương thích mọi thiết bị:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Privacy Policy - [Tên App]</title>
    <style>
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            line-height: 1.6;
            color: #333;
            max-width: 800px;
            margin: 0 auto;
            padding: 40px 20px;
        }
        h1, h2, h3 { color: #111; }
        a { color: #0066cc; text-decoration: none; }
        a:hover { text-decoration: underline; }
    </style>
</head>
<body>
    <h1>Privacy Policy for [Tên App]</h1>
    <p><em>Last updated: [Ngày tháng năm]</em></p>
    
    <!-- Dán nội dung policy được generate vào đây -->
    <p>Nội dung chính sách bảo mật...</p>

</body>
</html>
```
