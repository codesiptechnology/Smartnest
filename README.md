# SmartNest — Premium Smart Home Solutions

> A full-stack, production-ready web application for showcasing, managing, and selling smart home devices — built with **React + Vite** on the frontend and **Node.js + Express + MongoDB** on the backend.

---

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#️-project-structure)
- [Getting Started](#-getting-started)
- [Environment Variables](#-environment-variables)
- [API Reference](#-api-reference)
- [Database Schemas](#️-database-schemas)
- [Pages & Routes](#-pages--routes)
- [Deployment](#-deployment)
- [Contributing](#-contributing)

---

## ✨ Features

### 🏠 Storefront (Public)
- **Animated Hero Section** — GSAP ScrollTrigger-powered scroll animation with floating product cards, split-image reveal, and auto-advancing hero slideshow
- **Product Catalog** — Live search, multi-filter (category, brand, price range, tags), sorting, and pagination
- **Product Detail Page** — High-res image gallery, specification table, related products carousel, and enquiry booking
- **Category & Brand Pages** — Dedicated landing pages for each category and partner brand
- **Cart & Wishlist** — Add-to-cart and wishlist functionality with persistent state
- **Contact & Enquiry Forms** — Customer lead capture with email notification
- **WhatsApp Floating Button** — Instant callback integration
- **FAQ, Privacy & Terms Pages** — Complete legal and support pages
- **Fully Responsive** — Mobile-first layouts with smooth adaptive behaviour

### 🔐 Admin Dashboard (Private)
- **Secure Admin Login** — JWT-based authentication with protected routes
- **Dashboard Stats** — Live counts for products, categories, brands, and enquiries
- **Tab-Specific Live Search**:
  - Products — by name, brand, or category
  - Categories — by name, slug, or tagline
  - Brands — by name or slug
  - Enquiries — by customer name, message, category, or status
- **Product Management** — Full CRUD with Cloudinary image upload, custom tags (`Trending`, `Top Seller`, `Featured`, `New`), custom specification attributes, gallery images
- **Category & Brand Management** — Create, update, delete with auto-slug generation
- **Enquiry Management** — Status lifecycle (`Pending → Contacted → Completed`), deletion
- **Appointment / Schedule Management** — View and manage customer booking appointments

### 🛠️ Developer-Friendly
- Custom `useFetch` hook for clean, reusable data fetching
- `useScrollAnimation` hook for Intersection Observer-based reveal animations
- Global `StoreContext` for shared product/category/brand state
- Centralized API client in `src/lib/`
- GSAP + Framer Motion for premium animations

---

## 🧰 Tech Stack

| Layer | Technology |
|:---|:---|
| **Frontend** | React 18, Vite, React Router v6 |
| **Styling** | Tailwind CSS v4, custom CSS tokens |
| **Animations** | GSAP (ScrollTrigger), Framer Motion |
| **Icons** | Lucide React |
| **Backend** | Node.js, Express.js |
| **Database** | MongoDB Atlas via Mongoose |
| **Authentication** | Firebase Auth (users) + JWT (admin) |
| **Image Storage** | Cloudinary |
| **Email** | Nodemailer (Gmail SMTP) |

---

## 🏗️ Project Structure

```text
SmartNest/
├── client/                        # React + Vite Frontend
│   ├── public/
│   └── src/
│       ├── assets/                # Hero images, category thumbnails
│       ├── components/
│       │   ├── common/            # Shared UI (buttons, loaders, etc.)
│       │   ├── home/              # Hero, featured sections
│       │   ├── layout/            # Navbar, Footer
│       │   └── product/           # ProductCard, BookingModal, etc.
│       ├── context/               # StoreContext (global state)
│       ├── hooks/
│       │   ├── useFetch.js        # Generic async data-fetch hook
│       │   └── useScrollAnimation.js
│       ├── lib/                   # API client & static fallbacks
│       ├── pages/
│       │   ├── Home.jsx
│       │   ├── Products.jsx
│       │   ├── ProductDetail.jsx
│       │   ├── Category.jsx
│       │   ├── Brand.jsx
│       │   ├── Cart.jsx
│       │   ├── Wishlist.jsx
│       │   ├── Contact.jsx
│       │   ├── About.jsx
│       │   ├── FAQ.jsx
│       │   ├── Privacy.jsx
│       │   ├── Terms.jsx
│       │   └── admin/
│       │       ├── Login.jsx
│       │       └── Dashboard.jsx
│       ├── styles.css             # Design tokens & global styles
│       ├── App.jsx                # Router setup
│       └── main.jsx
│
├── server/                        # Node.js + Express Backend
│   ├── config/                    # MongoDB, Cloudinary, Mailer, Firebase
│   ├── controllers/               # Business logic per resource
│   ├── middleware/                # JWT auth, Multer image upload
│   ├── models/
│   │   ├── Product.js
│   │   ├── Category.js
│   │   ├── Brand.js
│   │   ├── Enquiry.js
│   │   ├── Admin.js
│   │   ├── User.js
│   │   ├── Appointment.js
│   │   └── Schedule.js
│   ├── routes/
│   │   ├── products.js
│   │   ├── categories.js
│   │   ├── brands.js
│   │   ├── enquiries.js
│   │   ├── auth.js
│   │   ├── userAuth.js
│   │   ├── appointments.js
│   │   └── schedules.js
│   ├── seed.js                    # Database seeder script
│   ├── server.js                  # Express app entry point
│   └── package.json
│
└── README.md
```

---

## ⚡ Getting Started

### Prerequisites

- **Node.js** >= 18
- **npm** >= 9
- **MongoDB Atlas** account (or local MongoDB instance)
- **Cloudinary** account (for image uploads)
- **Gmail** account with an App Password (for email notifications)

### 1. Clone the repository

```bash
git clone https://github.com/codesiptechnology/Smartnest.git
cd Smartnest
```

### 2. Install dependencies

```bash
# Frontend
cd client
npm install

# Backend
cd ../server
npm install
```

### 3. Configure environment variables

See the [Environment Variables](#-environment-variables) section below.

### 4. Run development servers

```bash
# Terminal 1 — Backend (http://localhost:5000)
cd server
npm run dev

# Terminal 2 — Frontend (http://localhost:5173)
cd client
npm run dev
```

### 5. (Optional) Seed the database

```bash
cd server
node seed.js
```

---

## 🔑 Environment Variables

### Client — `client/.env`

```env
VITE_API_URL=http://localhost:5000
```

### Server — `server/.env`

```env
PORT=5000
NODE_ENV=development

# MongoDB
MONGO_URI=mongodb+srv://<username>:<password>@<cluster>.mongodb.net/SmartNest?appName=SmartNest

# Cloudinary
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Email (Nodemailer)
EMAIL_USER=your_gmail@gmail.com
EMAIL_PASS=your_gmail_app_password

# JWT
JWT_SECRET=your_super_secret_key

# Firebase Admin SDK (if using Firebase Auth for users)
FIREBASE_PROJECT_ID=your_project_id
FIREBASE_CLIENT_EMAIL=your_client_email
FIREBASE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\n...\n-----END PRIVATE KEY-----\n"
```

---

## 🔗 API Reference

### Health

| Method | Endpoint | Access | Description |
|:---|:---|:---|:---|
| GET | `/api/health` | Public | Server & DB connection status |

### Products

| Method | Endpoint | Access | Description |
|:---|:---|:---|:---|
| GET | `/api/products` | Public | List products — supports `?search`, `?category`, `?brand`, `?tag`, `?page`, `?limit` |
| GET | `/api/products/:id` | Public | Get single product by ID or slug |
| POST | `/api/products` | Admin | Create product (multipart/form-data with image) |
| PUT | `/api/products/:id` | Admin | Update product |
| DELETE | `/api/products/:id` | Admin | Delete product |

### Categories

| Method | Endpoint | Access | Description |
|:---|:---|:---|:---|
| GET | `/api/categories` | Public | List all categories |
| GET | `/api/categories/:id` | Public | Get single category |
| POST | `/api/categories` | Admin | Create category |
| PUT | `/api/categories/:id` | Admin | Update category |
| DELETE | `/api/categories/:id` | Admin | Delete category |

### Brands

| Method | Endpoint | Access | Description |
|:---|:---|:---|:---|
| GET | `/api/brands` | Public | List all brands |
| POST | `/api/brands` | Admin | Create brand |
| PUT | `/api/brands/:id` | Admin | Update brand |
| DELETE | `/api/brands/:id` | Admin | Delete brand |

### Enquiries

| Method | Endpoint | Access | Description |
|:---|:---|:---|:---|
| POST | `/api/enquiries` | Public | Submit enquiry (triggers email notification) |
| GET | `/api/enquiries` | Admin | List all enquiries |
| PUT | `/api/enquiries/:id` | Admin | Update status (`Pending → Contacted → Completed`) |
| DELETE | `/api/enquiries/:id` | Admin | Delete enquiry |

### Auth (Admin)

| Method | Endpoint | Access | Description |
|:---|:---|:---|:---|
| POST | `/api/auth/login` | Public | Admin login — returns JWT |

### User Auth

| Method | Endpoint | Access | Description |
|:---|:---|:---|:---|
| POST | `/api/user-auth/register` | Public | User registration |
| POST | `/api/user-auth/login` | Public | User login |

### Appointments

| Method | Endpoint | Access | Description |
|:---|:---|:---|:---|
| GET | `/api/appointments` | Admin | List all appointments |
| POST | `/api/appointments` | Public | Book a consultation appointment |

### Schedules

| Method | Endpoint | Access | Description |
|:---|:---|:---|:---|
| GET | `/api/schedules` | Admin | List all schedule slots |
| POST | `/api/schedules` | Admin | Create a schedule slot |

---

## 🗄️ Database Schemas

### Product

```json
{
  "_id": "ObjectId",
  "name": "String",
  "slug": "String (unique, auto-generated)",
  "shortDescription": "String",
  "description": "String (rich/detailed)",
  "price": "Number",
  "category": "ObjectId → Category",
  "brand": "ObjectId → Brand",
  "specifications": [{ "key": "String", "value": "String" }],
  "image": "String (primary Cloudinary URL)",
  "images": ["String (gallery Cloudinary URLs)"],
  "tag": "String — Trending | Top Seller | Featured | New",
  "featured": "Boolean",
  "inStock": "Boolean",
  "createdAt": "Date"
}
```

### Category

```json
{
  "_id": "ObjectId",
  "name": "String",
  "slug": "String (unique)",
  "tagline": "String",
  "image": "String (Cloudinary URL)"
}
```

### Brand

```json
{
  "_id": "ObjectId",
  "name": "String",
  "slug": "String (unique)",
  "logo": "String (Cloudinary URL)"
}
```

### Enquiry

```json
{
  "_id": "ObjectId",
  "name": "String",
  "email": "String (optional)",
  "phone": "String",
  "message": "String (optional)",
  "category": "String (interested category)",
  "product": "ObjectId → Product (optional)",
  "status": "String — Pending | Contacted | Completed",
  "createdAt": "Date"
}
```

### User

```json
{
  "_id": "ObjectId",
  "name": "String",
  "email": "String (unique)",
  "firebaseUid": "String",
  "createdAt": "Date"
}
```

### Appointment

```json
{
  "_id": "ObjectId",
  "name": "String",
  "phone": "String",
  "email": "String",
  "date": "Date",
  "message": "String",
  "status": "String — Pending | Confirmed | Cancelled"
}
```

---

## 📄 Pages & Routes

| Path | Page | Access |
|:---|:---|:---|
| `/` | Home (Hero + Featured Products) | Public |
| `/products` | Full Product Catalog | Public |
| `/products/:slug` | Product Detail | Public |
| `/category/:slug` | Category Landing | Public |
| `/brand/:slug` | Brand Landing | Public |
| `/cart` | Shopping Cart | Public |
| `/wishlist` | Wishlist | Public |
| `/contact` | Contact & Enquiry | Public |
| `/about` | About SmartNest | Public |
| `/faq` | FAQ | Public |
| `/privacy` | Privacy Policy | Public |
| `/terms` | Terms & Conditions | Public |
| `/admin/login` | Admin Login | Public |
| `/admin/dashboard` | Admin Dashboard | Admin only |

---

## 🚀 Deployment

### Frontend (Netlify / Vercel / Hostinger)

1. Build the frontend:
   ```bash
   cd client
   npm run build
   ```
2. Deploy the `client/dist/` folder.
3. Set the environment variable:
   ```
   VITE_API_URL=https://your-backend-url.com
   ```
4. Add a redirect rule for client-side routing:
   - **Netlify** — create `public/_redirects`: `/* /index.html 200`
   - **Vercel** — add to `vercel.json`: `{ "rewrites": [{ "source": "/(.*)", "destination": "/" }] }`

### Backend (Render / Railway / VPS)

1. Deploy the `server/` directory.
2. Set all [server environment variables](#server----serverenv) in your hosting provider's dashboard.
3. Set the start command:
   ```bash
   node server.js
   ```

### Database (MongoDB Atlas)

- Go to **Network Access** → add `0.0.0.0/0` (or your server's static IP) to the IP whitelist.
- Ensure `MONGO_URI` includes the correct database name (e.g., `/SmartNest`).

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "feat: add your feature"`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request targeting the `main` branch

---

## 📜 License

This project is proprietary software developed for **CodeSIP Technology**. All rights reserved.


---

## 🌟 Features

### 🏠 Storefront (Public Portal)
- **Premium Hero Section**: Modern, animated header with glassmorphism design and smooth page transitions.
- **Searchable & Filterable Catalog**: Live filtering by text search, price range, product category, partner brand, and sorting preferences.
- **Product Details Page**: Beautifully designed page displaying high-res image galleries, specification tables, related products, and a **Detailed Description** section.
- **Consultancy Booking & Enquiries**: Interactive customer lead forms and floating WhatsApp callback integration.
- **Responsive Architecture**: Pixel-perfect viewports on all screen sizes, from mobile drawers to widescreen monitors.

### 🔐 Admin Dashboard (Private Portal)
- **Advanced Navigation & Styling**: Highly polished color scheme matching the premium user storefront.
- **Quick Data Summary**: Dynamic stat boxes displaying **Total Categories** and **Total Brands** at a glance.
- **Tab-Specific Live Search**:
  - 🔍 **Products tab**: Search by name, brand, or category.
  - 🔍 **Categories tab**: Search by category name, slug, or tagline.
  - 🔍 **Brands tab**: Search by name or slug.
  - 🔍 **Enquiries tab**: Search by customer details, message content, category interest, or status.
- **Product & Inventory Management**: Product CRUD, custom tags (Trending, Top Seller, Featured, New), and custom specification attributes.
- **Category & Brand Management**: Create, update, or remove records with auto-slug generation.
- **Enquiry & Booking Resolution**: Real-time status updates (Pending, Contacted, Completed) and deletion tools.

---

## 🏗️ Project Structure

```text
smartnest/
├── client/                  # React + Vite Frontend
│   ├── public/
│   ├── src/
│   │   ├── components/      # Reusable UI components & layouts
│   │   ├── pages/           # Storefront & Admin pages
│   │   ├── context/         # Auth providers (Admin & User)
│   │   ├── lib/             # API clients & static fallbacks
│   │   └── index.css        # Core styling & design tokens
│   ├── .env                 # Frontend local variables
│   └── package.json
│
├── server/                  # Node.js + Express Backend
│   ├── config/              # MongoDB connection, Cloudinary, Mailer, & Firebase
│   ├── models/              # Mongoose schemas (Product, Enquiry, Category, etc.)
│   ├── controllers/         # API business logic
│   ├── routes/              # Express API routes
│   ├── middleware/          # JWT auth validation & image uploading
│   ├── .env                 # Backend environment variables
│   └── server.js            # Main server entry point
│
└── README.md
```

---

## ⚡ Getting Started

### Prerequisites
- Node.js >= 18
- npm >= 9
- MongoDB Atlas account (or a local MongoDB instance)

### 1. Installation

```bash
# Install frontend dependencies
cd client
npm install

# Install backend dependencies
cd ../server
npm install
```

### 2. Configure Environment Variables

Create `.env` files in both directories.

**Client** (`client/.env`):
```env
VITE_API_URL=http://localhost:5000

# Add Firebase config below if using custom Firebase auth
```

**Server** (`server/.env`):
```env
PORT=5000
NODE_ENV=development

# MongoDB Atlas Connection
# Add your target database name (e.g. /SmartNest) to store collections in a custom DB:
MONGO_URI=mongodb+srv://<username>:<password>@<cluster>.mongodb.net/SmartNest?appName=SmartNest

# Cloudinary Config
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Email Config
EMAIL_USER=your_gmail@gmail.com
EMAIL_PASS=your_app_password
```

### 3. Run Development Servers

```bash
# Start backend (running on port 5000)
cd server
npm run dev

# Start frontend (running on port 5173)
cd client
npm run dev
```

---

## 🔗 Key API Endpoints

| Method | Endpoint | Access | Description |
|:---|:---|:---|:---|
| **GET** | `/api/health` | Public | Reports server status & Mongoose DB connection state |
| **GET** | `/api/products` | Public | List products (with text search, category/brand filters, pagination) |
| **POST** | `/api/products` | Admin | Create new product |
| **PUT** | `/api/products/:id` | Admin | Update product details or images |
| **DELETE** | `/api/products/:id` | Admin | Delete product |
| **GET** | `/api/categories` | Public | List all categories |
| **POST** | `/api/categories` | Admin | Add new category |
| **POST** | `/api/enquiries` | Public | Submit contact enquiry (sends email & saves to DB) |
| **GET** | `/api/enquiries` | Admin | Fetch all customer enquiries |
| **PUT** | `/api/enquiries/:id` | Admin | Update enquiry status (`Pending` ➔ `Contacted` ➔ `Completed`) |

---

## 🛠️ Database Schema

### Product Collection
```json
{
  "_id": "ObjectId",
  "name": "String",
  "slug": "String (unique)",
  "shortDescription": "String",
  "description": "String (detailed description)",
  "price": "Number",
  "category": "ObjectId (ref: Category)",
  "brand": "ObjectId (ref: Brand)",
  "specifications": [{"key": "String", "value": "String"}],
  "image": "String (Primary Cloudinary URL)",
  "images": ["String (Gallery Cloudinary URLs)"],
  "tag": "String (Trending / Top Seller / Featured / New)",
  "featured": "Boolean",
  "inStock": "Boolean"
}
```

### Enquiry Collection
```json
{
  "_id": "ObjectId",
  "name": "String",
  "email": "String (optional)",
  "phone": "String",
  "message": "String (optional)",
  "category": "String (interested product category)",
  "product": "ObjectId (optional, ref: Product)",
  "status": "String (Pending / Contacted / Completed)"
}
```

---

## 🚀 Production Deployment

1. **Frontend**: Deploy `client/` to Netlify, Vercel, or Hostinger. Configure the `VITE_API_URL` environment variable.
2. **Backend**: Deploy `server/` to Render, Railway, or VPS. Configure `MONGO_URI`, Cloudinary, and Nodemailer settings in the hosting provider's environment settings.
3. **Database Security**: If using MongoDB Atlas, make sure to add `0.0.0.0/0` (or your host's static IP range) to the Network Access whitelist to allow backend server connection.