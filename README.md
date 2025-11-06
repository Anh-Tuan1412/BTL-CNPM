# BTL Công nghệ phần mềm (PERT Stack)

Đây là dự án nội bộ nhằm xây dựng một website hỗ trợ đăng ký tutor cơ bản. Project được xây dựng trên nền tảng **PERN Stack** (PostgreSQL, Express, React, TypeScript) và được tổ chức theo mô hình **MVC**.

Hệ thống được thiết kế để phân chia chức năng cho 3 vai trò (role) chính: **Student** (Sinh viên), **Tutor**, và **Admin** (Quản trị viên).

## 🚀 Công nghệ sử dụng

* **Backend:** PostgreSQL, TypeScript, CSS, React, HTLM
* **Frontend:** TypeScript
* **ORM:** Prisma (Kết nối và quản lý CSDL)
* **Xác thực:** JWT (JSON Web Tokens)
* **UI (Gợi ý):** MUI hoặc Ant Design
* **Gọi API:** Axios
* **Quản lý State (Data):** React Context (cho Auth) & TanStack/React Query (cho server data)

---

## 📂 Cấu trúc Thư mục

Dự án được chia thành hai phần riêng biệt: `/backend` và `/frontend`.

### 1. `/backend` (Server)

Phần backend được tổ chức theo mô hình MVC:

/backend
├── /prisma         <-- MODEL (M)
│   └── schema.prisma (Định nghĩa CSDL: User, Student, Tutor...)
├── /src
│   ├── /config     (Chứa client Prisma, kết nối CSDL)
│   ├── /controllers<-- CONTROLLER (C) (Logic xử lý: auth.controller, product.controller)
│   ├── /middlewares(Code chạy giữa: isAuth, isRole (phân quyền))
│   ├── /routes     (Định nghĩa API endpoints: /api/auth, /api/products)
│   └── /utils      (Các hàm hỗ trợ: tạo JWT, hash password...)
├── app.js          (File Express server chính)
├── .env            (Biến môi trường, chuỗi kết nối CSDL)
└── package.json


### 2. `/frontend` (Client/View)
Phần frontend (React) đóng vai trò là View (V) trong MVC.

/frontend
├── /src
│   ├── /api        (Các file service để gọi API: authService.ts...)
│   ├── /components (Các component UI nhỏ, tái sử dụng: StudentCard, Header...)
│   ├── /context    (AuthContext - Nơi quản lý state đăng nhập toàn cục)
│   ├── /hooks      (Các custom hook)
│   ├── /pages      (Các trang hoàn chỉnh: LoginPage, HomePage, AdminDashboard...)
│   ├── /routes     (Logic điều hướng: ProtectedRoute, RoleRedirect...)
├── App.jsx         (Component App chính, chứa logic router)
├── main.jsx        (File khởi chạy React)
└── package.json

## 🛠️ Cách chạy dự án (Development)

Mỗi thành viên cần chạy cả 2 server (backend và frontend) song song.

### 1. Chạy Backend

```bash
# 1. Đi vào thư mục backend
cd backend

# 2. Cài đặt các gói
npm install

# 3. (Làm 1 lần) Thiết lập file .env (copy từ .env.example)
#    và điền chuỗi kết nối PostgreSQL của bạn

# 4. (Làm 1 lần) Chạy migration để tạo CSDL
npx prisma migrate dev

# 5. Khởi động server (với nodemon)
npm run dev
```

### 2. Chạy Frontend

```bash
# 1. Mở 1 terminal MỚI, đi vào thư mục frontend
cd frontend

# 2. Cài đặt các gói
npm install

# 3. Khởi động server React (Vite)
npm run dev

# 4. Mở trình duyệt và truy cập http://localhost:5173 (hoặc cổng tương tự)
```
