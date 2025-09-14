https://youtu.be/-o-4PqG-tnw
# Demo DNS Server on CentOS 7

Repository này chứa tài liệu hướng dẫn cài đặt và cấu hình **DNS Server trên CentOS 7**, bao gồm:
- Primary DNS Server
- Secondary (Backup) DNS Server
- Thiết lập Forwarder giữa các DNS Server

## 📘 Nội dung

### 1. Cài đặt & Cấu hình DNS Server
- Cài đặt gói BIND và bind-utils:
  ```bash
  yum install bind bind-utils -y
