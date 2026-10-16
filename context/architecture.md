# Architecture Context - PickAHouse

## Stack
| Layer | Technology | Version | Purpose |
| --- | --- | --- | --- |
| **Frontend Runtime** | Next.js (App Router) | 15.x | SSR/SSG React Framework |
| **Frontend UI** | Tailwind CSS, Radix UI, Framer Motion | Latest | Utility styling, accessible primitives, animations |
| **Global State** | Zustand | Latest | Auth state, filters, favorites/wishlist persistence |
| **Backend API** | Node.js / Express.js | Latest | REST API server, business logic processing |
| **ORM / Database** | Prisma ORM / PostgreSQL | 15.x / Latest | Structured database persistence & query building |
| **Authentication** | JWT (jsonwebtoken) + bcryptjs | Latest | Session token signing, authorization, password hashing |
| **Form & Validation** | React Hook Form + Zod | Latest | Strict schema validation at client and server boundaries |

## System Boundaries
- `app/` — Next.js App Router frontend routes (`/properties`, `/profile`, `/admin/*`, `/signin`, `/register`).
- `components/` — Reusable client/server components (`ui/` Radix primitives, `property-grid`, `header`, `ai-search`).
- `lib/` — API client configuration (`lib/api.ts`), Zustand global state store (`lib/store/`), and utility functions.
- `backend/src/controllers/` — Express route controllers for Auth, Properties, Users, Inquiries, and Messages.
- `backend/src/middleware/` — Auth verification (`auth.ts`), Rate limiting, Cors, and Error handling middleware.
- `prisma/` — Schema declaration (`schema.prisma`), database migrations, and seed scripts.

## Storage Model
- **PostgreSQL Database:** Stores Users, Properties, Inquiries, Messages, Favorites, and Admin Activity Logs.
- **CDN / Cloud Storage (Cloudinary/S3):** Stores high-resolution property photos, agent avatars, and document attachments.

## Auth & Access Model
- **Token Mechanism:** JWT tokens generated on login/register, stored securely in client storage/cookies, and passed via `Authorization: Bearer <token>` headers.
- **Role Hierarchy:**
  - `MEMBER`: Can browse properties, save wishlists, and submit inquiries.
  - `AGENT`: Can create/edit their own property listings and respond to inquiries.
  - `ADMIN`: Full system access, user role modification, property approval, and analytics.

## Invariants
1. **Strict Route Protection:** Unauthenticated requests to `/admin/*` or `/profile` must be blocked by middleware before rendering page layouts.
2. **Password Security:** Passwords must never be stored or logged in plain text; bcrypt hashing (min 10 rounds) is mandatory.
3. **No Unoptimized Images:** External property images must be fetched through Next.js `<Image />` optimization or Cloudinary CDN.
4. **Type Safety:** TypeScript strict mode must remain enforced across both Next.js frontend and Express backend.
