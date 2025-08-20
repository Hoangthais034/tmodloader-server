# 🌐 Web Terminal cho tModLoader Server

## 📋 Mô tả
Service này cung cấp web terminal để truy cập console của tModLoader server từ trình duyệt web, với xác thực bảo mật.

## 🚀 Cách sử dụng

### 1. Khởi động services
```bash
docker-compose up -d
```

### 2. Truy cập Web Terminal
- **URL**: `http://YOUR_SERVER_IP:8080`
- **Username**: `admin`
- **Password**: `1234`

### 3. Tính năng
- ✅ Truy cập trực tiếp console của tModLoader
- ✅ Xác thực bảo mật (admin:1234)
- ✅ Giao diện web thân thiện
- ✅ Không cần SSH client
- ✅ Hoạt động trên mọi thiết bị có trình duyệt

## ⚙️ Cấu hình

### Thay đổi thông tin đăng nhập
Để thay đổi username/password, sửa trong `docker-compose.yml`:

```yaml
command: -c YOUR_USERNAME:YOUR_PASSWORD -p 7681 docker attach tmodloader
environment:
  - TTYD_CREDENTIAL=YOUR_USERNAME:YOUR_PASSWORD
```

### Thay đổi port
Để thay đổi port web terminal, sửa trong `docker-compose.yml`:

```yaml
ports:
  - "YOUR_PORT:7681"
```

## 🔒 Bảo mật
- Service chỉ có thể attach vào container `tmodloader`
- Không thể truy cập shell của VPS
- Xác thực bắt buộc trước khi sử dụng
- Docker socket được mount với quyền hạn chế

## 🛠️ Troubleshooting

### Nếu web terminal không hoạt động:
1. Kiểm tra container status: `docker-compose ps`
2. Xem logs: `docker-compose logs ttyd`
3. Đảm bảo port 8080 không bị firewall chặn
4. Kiểm tra Docker socket permissions

### Restart service:
```bash
docker-compose restart ttyd
```

## 📱 Tương thích
- ✅ Chrome/Chromium
- ✅ Firefox
- ✅ Safari
- ✅ Edge
- ✅ Mobile browsers

## 🎯 Lưu ý
- Web terminal sẽ tự động reconnect nếu mất kết nối
- Có thể sử dụng để gửi lệnh console commands
- Không ảnh hưởng đến performance của tModLoader server
- Service tự động restart nếu gặp lỗi
