# FS05 Spa Management System - Backend 🚀

---
---

Dự án Backend cho Hệ thống Quản lý Spa, được xây dựng trên nền tảng **Irwin Framework** - một framework Node.js mạnh mẽ tập trung vào năng suất (Convention over Configuration), lấy cảm hứng từ Ruby on Rails.

## 🛠 Công nghệ sử dụng

- **Runtime**: Node.js với TypeScript.
- **Framework**: Irwin Framework (Express-based).
- **Database ORM**: Prisma.
- **Validation**: Class-validator.
- **Background Jobs**: BullMQ / AWS Lambda.
- **Infrastructure**: Hỗ trợ Serverless (AWS Lambda).

---

## 🌟 Tính năng chính (Features)

Hệ thống bao gồm các module quản trị quan trọng:
- **Quản lý người dùng (User Management)**: Phân quyền (RBAC), quản lý tài khoản.
- **Quản lý lịch hẹn (Appointment)**: Đặt lịch và theo dõi trạng thái.
- **Quản lý dịch vụ (Service)**: Danh mục gói dịch vụ Spa.
- **Quản lý bài viết (News & Comments)**: Hệ thống tin tức, xu hướng làm đẹp và tương tác người dùng.
- **Quản lý nhân viên (Staff Schedule)**: Sắp xếp lịch làm việc cho nhân viên.
- **Hệ thống Chat**: Giao tiếp thời gian thực.

---

## 🚀 Bắt đầu nhanh (Quick Start)

### 1. Thiết lập môi trường
Cài đặt các thư viện cần thiết và cấu hình biến môi trường:
```bash
yarn install
cp .env.example .env
```

### 2. Cơ sở dữ liệu & Seed dữ liệu
Khởi tạo database và nạp dữ liệu mẫu (bao gồm quyền, tính năng và bài viết mẫu):
```bash
yarn db:migrate
yarn db:seed
```

### 3. Chạy môi trường phát triển
```bash
yarn dev
```

- **App URL**: `http://localhost:8000`
- **Swagger API Documentation**: `http://localhost:8000/api-docs`

---

## 🏗 Công cụ Scaffolding (Generators)

Sử dụng CLI để tạo nhanh các thành phần code nhằm đảm bảo tính đồng nhất:

| Lệnh | Chức năng |
| :--- | :--- |
| `yarn g:scaffold [Name]` | Tạo trọn bộ: Model, Controller, Service, Route, View |
| `yarn g:controller [Name]` | Tạo một Controller mới |
| `yarn g:service [Name]` | Tạo Service Object cho business logic |
| `yarn g:job [Name]` | Tạo Background Job (BullMQ/Lambda) |
| `yarn g:resource [Name]` | Tạo Resourceful Route (API + UI) |

---

## 📖 Cấu trúc code tiêu biểu

### 🛣 Resourceful Routing
Khai báo Route, Phân quyền và Swagger tại cùng một nơi:

```typescript
this.resource("/news", NewsController, {
  setPermissionFor: "NEWS",
  document: { body: CreateNewsValidator }, 
});
```

---

<a name="japanese"></a>

## 🇯🇵 日本語 (Japanese)

### 🌟 設計思想

- **設定より規約 (CoC)**: 標準化されたディレクトリ構造により、ボイラープレートを最小限に抑えます。
- **信頼できる唯一の情報源 (SSoT)**: ルーティング、権限、Swaggerドキュメントを1か所で定義します。
- **モダンなフロントエンド統合**: SSR (Pug) とリアクティブコンポーネント (Vue 3) の強力な組み合わせ。

### 🏗 ジェネレーター

ボイラープレートの作成を自動化します：
| コマンド | 機能 |
| :--- | :--- |
| `yarn g:scaffold [Name]` | モデル、コントローラー、サービス、ルート、ビューをフルセットで生成 |
| `yarn g:resource [Name]` | Swaggerドキュメント付きのAPIリソースを生成 |

### 🛣 リソースルーティング

```typescript
// 1行でRESTfulなルート、権限チェック、Swagger定義を完結
this.resource("/users", UsersController, {
  setPermissionFor: "UM",
  document: { body: CreateUserValidator },
});
```

---

<a name="vietnamese"></a>

## 🇻🇳 Tiếng Việt (Vietnamese)

### 🌟 Triết lý thiết kế

- **Convention over Configuration**: Giảm thiểu thời gian thiết lập bằng cấu trúc thư mục chuẩn Rails.
- **Single Source of Truth**: Khai báo Route, Phân quyền và Swagger Documentation tại cùng một nơi.
- **Modern Frontend Integration**: Kết hợp hoàn hảo giữa SSR (Pug) và Vue 3 Components.

### 🏗 Generators (Vũ khí Scaffolding)

Đừng viết code thủ công, hãy để framework làm việc đó cho bạn:
| Lệnh | Chức năng |
| :--- | :--- |
| `yarn g:scaffold [Name]` | Tạo trọn bộ: Model, Controller, Service, Route, View |
| `yarn g:job [Name]` | Tạo Background Job (BullMQ/Lambda) |
| `yarn g:resource [Name]` | Tạo Resourceful Route (API + UI) |

---

## 🛠 Getting Started (Quick Start)

### 1. Environment Setup

```bash
yarn install
cp .env.example .env
```

### 2. Database & Seeds

```bash
yarn db:migrate
yarn db:seed
```

### 3. Development

```bash
yarn dev
```

- App URL: `http://localhost:8000`
- Swagger UI: `http://localhost:8000/api-docs`

---

## 🎮 Controllers & Strong Parameters

Irwin uses `class-validator` to provide powerful, type-safe parameter filtering:

```typescript
export class UsersController extends RailsController {
  async create() {
    // Whitelist, Validate, and Type-cast in one line
    const userParams = await this.params(CreateUserValidator).permit(
      "email",
      "password",
      "roleIds",
    );

    const user = await UserService.create(userParams);

    if (this.req.xhr) {
      return this.renderJson(user, 201);
    }
    this.redirect("/users");
  }
}
```

---

## 📮 Background Jobs

Unified interface for **BullMQ** (Classic Server) and **AWS Lambda** (Serverless):

```typescript
// Push to queue for later processing
await WelcomeEmailJob.performLater(user.id);
```

---

## 🌍 I18n & View Helpers

- Use `t('key')` in Controllers or Pug views.
- Automatic locale detection via Query, Cookie, or Headers.
- Vite-integrated asset helpers: `h.assetPath('main.ts')`.

---

## 🚀 Deployment

Built-in support for **Serverless Framework**:

```bash
yarn serverless
```
