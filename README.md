# BuyLink — Phase 1 + 2 + 3

Auth, store creation, product listing, search, category filters,
product/store pages, and real-time buyer-seller messaging — built with
Next.js and Supabase.

## Setup

1. **Create a Supabase project** at supabase.com (free tier is fine).
2. In the Supabase SQL editor, run `supabase/schema.sql` to create the
   `profiles`, `stores`, `products`, `conversations`, and `messages`
   tables with row-level security. This also enables Realtime on the
   `messages` table, which the chat UI needs.
3. Copy `.env.local.example` to `.env.local` and fill in your project's
   URL and anon key (Project Settings → API in Supabase).
4. Install dependencies and run:
   ```
   npm install
   npm run dev
   ```
5. Open http://localhost:3000

## What's built (Phase 1 + 2 + 3)

- `/signup` — create an account as buyer, seller, or both
- `/login` — log in
- `/dashboard` — sellers create their store here
- `/dashboard/products/new` — add a product to your store
- `/products` — buyers browse all listed products, with a search bar and
  a category filter (built client-side from existing product categories)
- `/products/[id]` — individual product page with a working "Message
  seller" button that starts or resumes a conversation
- `/stores/[id]` — public store page listing everything that store sells
- `/messages` — inbox of all your conversations
- `/messages/[id]` — a real-time chat thread (Supabase Realtime) with
  a seller or buyer
- Optional Plausible analytics — set `NEXT_PUBLIC_PLAUSIBLE_DOMAIN` in
  `.env.local` once you have a domain; leave blank to skip for now

## Not yet built (later phases)

- Photo/video upload for products (needs Supabase Storage or Cloudinary)
- Server-side/full-text search once product volume grows past what
  client-side filtering handles well
- Read receipts / unread counts / push notifications for messages
- Social feed / vertical swipe view (Phase 4)

## Notes

- Auth and RLS are wired so a seller can only edit their own store/products,
  but anyone can view stores and products (public marketplace).
- Styling uses Tailwind with a small custom palette in `tailwind.config.js` —
  change `clay`/`ink`/`sand`/`moss` there to rebrand.
