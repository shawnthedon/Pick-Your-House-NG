# Code Standards - PickAHouse

## General Principles
- Maintain explicit separation of concerns: Next.js handles presentation/routing; Express/Prisma handles business logic and DB access.
- Always handle async errors gracefully using structured `try/catch` blocks and centralized Express error handling.
- Eliminate static mock data fallbacks in production views once backend API routes are active.

## TypeScript Guidelines
- Strict mode is mandatory (`"strict": true` in `tsconfig.json`). Never enable `ignoreBuildErrors`.
- Avoid using `any`—define explicit interface models in `lib/types.ts` or Prisma schema types.
- Validate all incoming request bodies (`req.body`) and query params (`req.query`) using Zod schemas at API boundaries.

## Next.js & React Conventions
- Components default to React Server Components unless browser interactivity (`useState`, `useEffect`, `onClick`) requires `'use client'`.
- All client-side data fetching must route through `lib/api.ts` (ApiClient) or custom hooks, displaying standard skeleton loaders during loading states.
- Follow the Radix UI accessibility primitive standards.

## Styling & Theme Rules
- Use utility classes via Tailwind CSS v4.
- Use explicit NGN currency formatting for prices (`₦850,000,000`).
- Ensure touch targets on mobile viewports meet minimum dimensions (`min-h-[44px]`, `min-w-[44px]`).

## API Response Standard
All API responses must conform to a predictable JSON shape:
```json
{
  "success": true,
  "data": { ... },
  "error": "Error description if success is false",
  "pagination": { "total": 100, "page": 1, "limit": 20 }
}
