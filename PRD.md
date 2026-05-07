# PRD: Nexora E-Commerce Store

## 1. Overview
Nexora is a full‑stack, production‑style e‑commerce store with a clean, responsive UI. Users can browse products by category, sign up/login, and place COD (Cash on Delivery) orders. Admins manage products and orders through a secured dashboard. Product images are stored on Cloudinary and their URLs are saved in PostgreSQL.

## 2. Goals & Success Criteria
- Deliver a responsive, modern UI (white background, black text) with smooth animations.
- Provide a full COD order flow for authenticated users.
- Enable admin to manage products and order statuses.
- Store product images in Cloudinary and persist URLs in Postgres.

## 3. Target Users
- Customers who browse and purchase products via COD.
- Admin who manages products, prices, stock, and order status.

## 4. Tech Stack
- **Frontend:** HTML, CSS, JavaScript, Bootstrap
- **Backend:** FastAPI
- **ORM:** SQLAlchemy
- **Migrations:** Alembic
- **Database:** PostgreSQL
- **Image Storage:** Cloudinary
- **Auth:** JWT or session-based auth (FastAPI)

## 5. Core Features
### 5.1 User Features
- Home page (hero, categories, featured products)
- Product listing with categories: Shirts, Pants, Electronics, Cosmetics
- Product detail page
- Search and filter by category
- User signup & login (required to place orders)
- Order form on “Buy Now” with fields:
  - Name, Address, Phone, Email
  - Payment method: Cash on Delivery (radio button)
- Order confirmation page
- Pages: About, Contact, FAQ
- Footer with contact info and **Admin** button/link to admin login
- WhatsApp floating icon (bottom‑right) with bounce animation

### 5.2 Admin Features
- Admin login using credentials stored in .env
- Product CRUD:
  - Add / update / delete product
  - Upload images to Cloudinary
  - Manage price and stock
- Orders list view
- Update order status: Pending → Confirmed → Delivered

## 6. Animations & UI
- Hero section animation
- Product cards fade‑in on scroll
- Button hover animations
- WhatsApp icon bounce animation
- Smooth transitions for UI elements

## 7. Data Model (PostgreSQL)
### users
- id (PK)
- name
- email (unique)
- password_hash
- role ("user" | "admin")
- created_at

### categories
- id (PK)
- name

### products
- id (PK)
- name
- price
- description
- stock
- category_id (FK)
- image_url (Cloudinary)
- created_at

### orders
- id (PK)
- user_id (FK)
- name
- email
- phone
- address
- payment_method (COD)
- status (Pending | Confirmed | Delivered)
- created_at

### order_items
- id (PK)
- order_id (FK)
- product_id (FK)
- quantity
- price_at_time

## 8. API Endpoints (FastAPI)
### Auth
- POST /auth/signup
- POST /auth/login
- GET /auth/me

### Products & Categories
- GET /products
- GET /products/{id}
- GET /categories
- GET /products?category=shirts

### Admin Products
- POST /admin/products
- PUT /admin/products/{id}
- DELETE /admin/products/{id}

### Orders
- POST /orders
- GET /admin/orders
- PUT /admin/orders/{id}/status

## 9. Pages & Routes (Frontend)
- /index.html (Home)
- /products.html (Product listing)
- /product.html (Product detail)
- /signup.html
- /login.html
- /about.html
- /contact.html
- /faq.html
- /admin-login.html
- /admin-dashboard.html

## 10. Milestones
1. Frontend UI (all pages + animations)
2. Backend API (auth, products, orders)
3. Admin dashboard (product CRUD + order status)
4. Integrations (Cloudinary + PostgreSQL)
5. Testing & polish

## 11. Assets
- **Logo:** Provided by client (NEXORA) for navbar (left side)
