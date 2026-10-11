# Session 09 – Bài 3: Đóng gói website HTML tĩnh với Docker

## Mục tiêu
Tạo trang HTML tĩnh, đóng gói bằng Dockerfile sử dụng `nginx:alpine`, build image `my-html-app:v1` và chạy container trên cổng 8081.

## Cấu trúc thư mục
```text
ss09-b3/
├── Dockerfile
├── index.html
└── README.md
```

## Nội dung trang web
File `index.html`:
```html
<h1>Hello Docker Session 09!</h1>
```

## Dockerfile
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```

- `FROM`: sử dụng image Nginx Alpine làm nền.
- `COPY`: sao chép trang HTML vào vị trí Nginx phục vụ mặc định.

## Thực hành
Từ thư mục chứa Dockerfile, chạy:

### 1. Build image
```bash
docker build -t my-html-app:v1 .
docker images
```

### 2. Chạy container
```bash
docker run -d -p 8081:80 --name html-app my-html-app:v1
docker ps
```

### 3. Kiểm tra phản hồi
```bash
curl http://localhost:8081
```

Kết quả **mong đợi**:
```html
<h1>Hello Docker Session 09!</h1>
```

### 4. Dọn dẹp container (tùy chọn)
```bash
docker stop html-app
docker rm html-app
```

## Kết quả thực hành
Chưa có đầu ra Terminal thực tế được cung cấp. Sau khi chạy, bổ sung ảnh hoặc đầu ra của `docker build`, `docker ps` và `curl` vào phần này để làm bằng chứng.

## Nộp bài
Nộp ba tệp `index.html`, `Dockerfile` và `README.md` tại `homework/session_09/ex3/` theo yêu cầu của đề bài.
