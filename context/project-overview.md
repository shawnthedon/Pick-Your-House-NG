# PickAHouse (Abuja Premier Estates) - Project Overview

## Overview
PickAHouse is a luxury real estate marketplace platform built for the Nigerian market, specifically targeting the Abuja Premier Estates segment. Designed to replace static prototypes with a full-stack, production-ready solution, the platform facilitates property discovery, automated agent inquiries, custom admin governance, and AI-powered natural language search capabilities across mobile, tablet, and desktop viewports.

## Goals
1. **Full-Stack Persistence:** Transition from a frontend-only mock prototype to a fully integrated Express/Node.js backend with PostgreSQL/Prisma ORM data persistence.
2. **Secure Authentication & RBAC:** Implement JWT authentication, password hashing (bcrypt), and Role-Based Access Control (MEMBER, AGENT, ADMIN) with protected route middleware.
3. **Property & Inquiry Pipeline:** Enable real-time property searching, category/location filtering, bookmarking/wishlists, and direct agent inquiry messaging via email/WhatsApp integrations.
4. **AI Property Search:** Connect a functional NLP/LLM search engine (OpenAI/Claude API) to allow buyers to discover luxury properties using conversational search queries.

## Core User Flow
1. **Discovery & Search:** User arrives on the homepage, uses conversational AI search or location filters (Maitama, Asokoro, Jabi) to browse listings.
2. **Property Inspection:** User views detailed property cards, photo galleries, amenities, and agent verification badges.
3. **Authentication:** User registers or logs in via JWT token auth; session state persists via global state management (Zustand).
4. **Agent Contact / Inquiry:** User submits a property inquiry or initiates a direct messaging workflow routed to the listing agent.
5. **Admin Governance:** Admins log into the protected `/admin` dashboard to manage users, approve property listings, view system analytics, and audit messages.

## Features
### User & Buyer Portal
- Conversational AI Search & Filter Bar (Type, Price in NGN ₦, Location, Bedrooms).
- Saved Properties / Wishlist state and saved search history.
- Property Detail view with interactive image galleries, maps, and agent contact modal.

### Agent & Admin Management
- Agent verification badge system and commission tracking placeholders.
- Protected Admin Dashboard (`/admin`) for Property CRUD, User Role management, and Analytics.
- Inquiry and message routing center.

## Scope
### In Scope
- Next.js 15 App Router frontend with Tailwind CSS 4, Radix UI, and Framer Motion.
- Node.js / Express REST API backend with Prisma ORM and PostgreSQL.
- JWT Authentication, bcrypt password hashing, and cookie/header token management.
- Dynamic property filtering, pagination, and search endpoints.
- Deployment readiness via Vercel (Frontend) and AWS RDS / DigitalOcean / Railway (Backend & DB).

### Out of Scope
- Native iOS/Android apps (core target is responsive Web/PWA).
- Unrestricted public access to `/admin` routes without valid JWT Admin tokens.
- Hardcoded mock data in production builds.

## Success Criteria
1. **Security & Protection:** All `/admin` and `/profile` routes are strictly protected by middleware, redirecting unauthenticated requests to `/signin`.
2. **API Data Flow:** Frontend components successfully fetch, filter, and paginate real property records from PostgreSQL via the Express REST API in <200ms.
3. **Production Build Integrity:** TypeScript strict mode passes with 0 type errors, Next.js image optimization is active, and `pnpm build` succeeds without `ignoreBuildErrors`.
