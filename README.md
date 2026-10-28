# Hannah Montemayor - Personal Blog & Novel Platform

A modern, high-performance web platform for author **Hannah Montemayor**, featuring serialized novel publishing, chapter-by-chapter reading, editorial blog articles, candid thoughts, and a comprehensive admin management dashboard.

Migrated from legacy **ASP.NET Core 6 MVC + MySQL** to a modern, type-safe full-stack architecture.

---

## 🚀 Tech Stack

- **Framework**: [Next.js 15](https://nextjs.org/) (App Router, Server Actions, React 19, TypeScript)
- **Database**: [PostgreSQL](https://www.postgresql.org/)
- **ORM**: [Prisma ORM 6.x](https://www.prisma.io/)
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/) with editorial serif typography
- **Icons**: [Lucide Icons](https://lucide.dev/)
- **Authentication**: Encrypted JWT HTTP-only session cookies with `jose` & `bcryptjs` password hashing

---

## ✨ Features

### Public Portal
- **Hero & Author Bio**: Dynamic author profile, introduction banner, and featured links.
- **Serialized Stories**: Catalog of novels, fiction, and ongoing series with cover art, genre tags, and chapter counts.
- **Chapter Reader**: Clean, distraction-free reading layout with Prev / Next chapter navigation and table of contents.
- **Editorial Blog**: Curated articles and reflections with category filtering (`Blog`, `Random`, `Both`).
- **Random Thoughts**: Stream of short musings and late-night reflections.
- **Unique Visitor Analytics**: Automatic IP-based unique visitor counting per post, chapter, and aggregate story views.

### Admin Dashboard (`/admin`)
- **Protected Access**: Route guards redirecting unauthenticated visitors to `/login`.
- **Overview Dashboard**: High-level metrics for published stories, blog posts, random thoughts, drafts, and total reads.
- **Post Manager**: Full CRUD for articles with category assignment and Draft vs. Published states.
- **Stories & Chapters Manager**: Create novels, upload covers, add new chapters, and manage parts.
- **Author Profile**: Edit name, bio, login username, password, and public avatar photo.

---

## 📦 Project Structure

```
hannahm-blog/
├── prisma/
│   ├── schema.prisma       # Database schema (PostgreSQL)
│   └── seed.ts             # Admin account & sample content seeder
├── public/
│   └── covers/             # Book covers & assets
├── src/
│   ├── actions/            # Next.js Server Actions (Posts, Stories, Account)
│   ├── app/                # App Router pages & API routes
│   │   ├── (public)/       # Home, Stories, Blog, Random, Login
│   │   ├── admin/          # Protected Admin Dashboard
│   │   ├── api/            # Dynamic Blob Image Routes (covers & avatars)
│   │   └── globals.css     # Tailwind CSS styles
│   ├── components/         # Shared UI components (Navbar, Footer, etc.)
│   └── lib/                # Database singleton, auth, visitor tracker
├── .env.example            # Environment variables template
├── package.json
└── tsconfig.json
```

---

## 🛠️ Getting Started

### 1. Prerequisites
- **Node.js**: v18.18+ or v20+ (tested on Node.js 24)
- **PostgreSQL**: v14+ running locally or in cloud (Supabase, Neon, AWS RDS, etc.)

### 2. Clone & Install Dependencies
```bash
git clone https://github.com/paulrndp/HannahM-Blog.git
cd HannahM-Blog
npm install
```

### 3. Configure Environment Variables
Create a `.env` file in the root directory:
```bash
cp .env.example .env
```
Update `.env` with your PostgreSQL database URL:
```env
DATABASE_URL="postgresql://postgres:password@localhost:5432/hannahm_db?schema=public"
AUTH_SECRET="your-super-secret-random-32-character-key"
PORT=3000
```

### 4. Setup Database & Seed Initial Content
Push the Prisma schema to PostgreSQL and seed initial data:
```bash
# Push database schema
npm run db:push

# Seed admin user and sample stories/posts
npm run db:seed
```

### 5. Run the Application

#### Development Mode:
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your browser.

#### Production Build & Start:
```bash
npm run build
npm run start
```

---

## 🔐 Default Admin Credentials

- **Login URL**: [http://localhost:3000/login](http://localhost:3000/login)
- **Username**: `admin`
- **Password**: `password`

*(Note: Change your password immediately via the Admin Dashboard under **My Profile**).*

---

## 📝 Available Scripts

| Command | Description |
| :--- | :--- |
| `npm run dev` | Starts local Next.js development server with hot-reloading |
| `npm run build` | Compiles and optimizes production build |
| `npm run start` | Runs the production server |
| `npm run db:push` | Syncs Prisma schema with PostgreSQL database |
| `npm run db:seed` | Populates database with sample data & admin account |
| `npm run db:studio` | Opens Prisma Studio web UI for database inspection |

---

## 📄 License
This project is open-source and available under the [MIT License](LICENSE).
