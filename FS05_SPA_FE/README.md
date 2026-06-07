# FS05 Spa Management System - Frontend 💅 ✨

---

Giao diện người dùng cho Hệ thống Quản lý Spa, được xây dựng với mục tiêu mang lại trải nghiệm mượt mà, sang trọng và hiện đại. Dự án sử dụng **Next.js** kết hợp với **Tailwind CSS** để tối ưu hóa hiệu năng và tốc độ phát triển.

## 🛠 Công nghệ sử dụng

- **Framework**: [Next.js 14+](https://nextjs.org/) (App Router).
- **Styling**: [Tailwind CSS](https://tailwindcss.com/).
- **UI Components**: 
    - **Swiper.js**: Xử lý các slider/carousel mượt mà.
    - **Lucide Icons / Custom SVG**: Hệ thống icon đồng bộ.
- **State Management**: React Hooks & Context API.
- **Animation**: CSS Animations & Swiper transitions.

---

## 🌟 Tính năng nổi bật

- **Giao diện Responsive**: Hiển thị hoàn hảo trên mọi thiết bị (Desktop, Tablet, Mobile).
- **Trang chủ chuyên nghiệp**:
    - Banner Carousel ấn tượng.
    - Khu vực giới thiệu dịch vụ (Facial Care, Body Treatment).
    - Khối trải nghiệm khách hàng với hiệu ứng chữ xoay SVG độc đáo.
- **Module Chuyên gia**: Giới thiệu đội ngũ chuyên viên có trình độ cao.
- **Tối ưu SEO**: Cấu hình metadata chuẩn cho các trang dịch vụ và tin tức.
- **Tương tác thời gian thực**: Kết nối với Backend thông qua Socket.io (cho tính năng Chat).

---

## 🚀 Bắt đầu nhanh (Quick Start)

### 1. Cài đặt thư viện
```bash
yarn install
# hoặc
npm install
```

### 2. Cấu hình biến môi trường
Tạo file `.env.local` ở thư mục gốc và cấu hình URL của Backend API:
```env
NEXT_PUBLIC_API_URL=http://localhost:8000
```

### 3. Chạy môi trường phát triển
```bash
yarn dev
```
Mở http://localhost:3000 trên trình duyệt để xem kết quả.

---

## 📂 Cấu trúc thư mục chính

- `/src/app`: Định nghĩa các route và page (Home, Chuyên gia, Tin tức...).
- `/src/components`: Các component dùng chung (Header, Footer, Section layouts).
- `/public`: Chứa hình ảnh, icons và tài nguyên tĩnh.

---

**Copyright © Spa System Frontend Team**
