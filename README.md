# GOODFELLAS Booking — Cirebon

Responsive barber booking website built with Vite, vanilla JavaScript and Supabase.

## Features
- Public service menu and appointment request form
- Availability slots based on shop opening hours and existing bookings
- Email/password admin login through Supabase Auth
- Admin booking queue, status updates, delete and print-friendly receipts
- Gallery upload to Supabase Storage
- Shop settings and booking slot interval controls

## Local development
1. Install Node.js 20+.
2. Run `npm install`.
3. Run `npm run dev`; production build is `npm run build`.
4. Optionally set `VITE_SUPABASE_URL` and `VITE_SUPABASE_PUBLISHABLE_KEY`.

## First admin
1. In Supabase Dashboard → Authentication → Users, create an admin user with email/password.
2. Copy the user's UUID.
3. In SQL Editor run: `insert into public.admin_users (user_id) values ('YOUR-AUTH-USER-UUID');`
4. Sign in at `/#admin`. No default password is shipped.

The Supabase schema has been applied to the GOODFELLAS project. Public users can create pending bookings only; RLS restricts booking management and photo upload to users listed in `public.admin_users`.

## Vercel
Build command `npm run build`, output directory `dist`, framework Vite. Set the two VITE environment variables if overriding the safe public fallback config.

## Printer limitations
The receipt opens a print-friendly page via the browser print dialog. Browsers generally do not expose Bluetooth Classic SPP/RAW ESC-POS directly. For direct RAW printing, use a trusted local bridge/desktop helper or native Android print app. Direct Bluetooth Classic pairing has not been tested.
