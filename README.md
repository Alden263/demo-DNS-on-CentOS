# Demo DNS Server on CentOS 7

Repository này chứa tài liệu hướng dẫn cài đặt và cấu hình **DNS Server trên CentOS 7**, bao gồm:
- Primary DNS Server
- Secondary (Backup) DNS Server
- Thiết lập Forwarder giữa các DNS Server

## Nội dung

### 1. Cài đặt & Cấu hình DNS Server
- Cài đặt gói BIND và bind-utils:
  ```bash
  yum install bind bind-utils -y
  ```
- Cấu hình IP tĩnh và chỉnh sửa file `named.conf`, `named.rfc1912.zones`.
- Tạo các bản ghi trong:
  - `forward.sgu.edu.vn`
  - `reverse.192.168.1.0`
- Khởi động dịch vụ:
  ```bash
  systemctl enable named
  systemctl start named
  ```

### 2. Backup DNS Server (Secondary)
- Cấu hình **allow-transfer** trên Primary để cho phép đồng bộ dữ liệu sang Secondary.
- Cài đặt bind trên Secondary, chỉnh `named.conf` và `named.rfc1912.zones`.
- Khởi động dịch vụ DNS:
  ```bash
  systemctl start named
  systemctl restart named
  ```
- Kiểm tra đồng bộ trong thư mục:
  ```bash
  ls -l /var/named/slaves
  ```

### 3. Thiết lập Forwarder giữa các DNS Server
- Khi mỗi DNS Server quản lý một zone riêng, cần cấu hình **forwarder** để truy vấn tên miền từ DNS khác.
- Chỉnh `named.conf` trên cả 2 máy, sau đó restart dịch vụ:
  ```bash
  systemctl restart named
  ```

## Kiểm tra hoạt động
- Sử dụng một trong các lệnh:
  ```bash
  nslookup
  dig
  host
  ```

## Tài liệu kèm theo
- [CentOS7 DNS Server.pdf](./CentOS7%20DNS%20Server.pdf)

## Video minh họa
- [Hướng dẫn DNS Server trên CentOS 7](https://youtu.be/-o-4PqG-tnw)

---
Contributors: [mujin0422](https://github.com/mujin0422), [Alden263](https://github.com/Alden263)
