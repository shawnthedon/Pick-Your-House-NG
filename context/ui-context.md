# UI Context & Design System - PickAHouse

## Visual Direction
Luxury real estate marketplace visual identity tailored for high-end estate listings in Abuja. Clean white/slate backgrounds in light mode, deep slate/navy surfaces in dark mode, rich gold/emerald status accents, and crisp typography hierarchy.

## Typography
| Role | Font Family | Variable / CSS Class |
| --- | --- | --- |
| Main Headings | Playfair Display / Serif | `font-serif` |
| Primary UI Text | Inter / Sans-Serif | `font-sans` |
| Code & Badges | JetBrains Mono / Mono | `font-mono` |

## Color Tokens & Tailwind Mapping
- **Primary Accent:** Deep Luxury Green / Emerald (`bg-emerald-700`, `text-emerald-600`)
- **Secondary Accent:** Gold / Amber (`text-amber-500`, `border-amber-400`)
- **Background Base:** `#FFFFFF` (Light Mode) / `#0F172A` Slate-900 (Dark Mode)
- **Card Surfaces:** Slate-50 / Slate-800
- **Borders:** Slate-200 / Slate-700

## Layout System
- **Desktop Grid:** 3-column property grid, fixed top navigation bar, sticky search/filter toolbar.
- **Mobile PWA Layout:** Fixed top header with logo and burger menu, 1-column responsive card stack, floating action buttons (AI Chat, WhatsApp Contact), and minimum 44px touch targets.
- **Admin Layout:** Left collapsible sidebar navigation, top breadcrumb bar, full-width data tables with sorting/pagination controls.
