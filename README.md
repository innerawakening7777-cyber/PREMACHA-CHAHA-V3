# Premacha Chaha V3

V3 removes the customer Udhaar system entirely.

## V3 features
- Owner/staff login
- Inventory
- POS sales
- Cash / UPI / Card payment split
- Stock purchases + supplier
- Expenses
- Daily cash closing
- Cash shortage/overage calculation
- 7-day sales chart
- Payment-method chart
- Monthly revenue/profit summary
- CSV sales export
- Low-stock alerts
- Supabase PostgreSQL + RLS
- Mobile responsive

## HOSTING: SUPABASE + VERCEL

### Step 1 — Supabase database
1. Open https://supabase.com/
2. Create an account and a new project.
3. Open your project.
4. Go to SQL Editor.
5. Open `supabase_v3.sql`.
6. Copy the complete SQL.
7. Paste it into SQL Editor.
8. Click Run.

### Step 2 — Create owner login
1. Supabase -> Authentication -> Users.
2. Add a new user.
3. Enter your owner email and password.
4. Copy the email.
5. In SQL Editor run:

update public.profiles
set role='owner'
where email='YOUR_OWNER_EMAIL';

Replace YOUR_OWNER_EMAIL with the owner email.

### Step 3 — Create staff login
Supabase -> Authentication -> Users -> Add user.
The trigger creates the profile as `staff`.

### Step 4 — Get Supabase keys
Go to Project Settings -> API.
Copy:
- Project URL
- Publishable/anon key

Do NOT copy the service_role/secret key.

### Step 5 — Configure index.html
Open `index.html`.

Find:
const SUPABASE_URL="YOUR_SUPABASE_URL",SUPABASE_ANON_KEY="YOUR_SUPABASE_ANON_KEY";

Replace both values.

### Step 6 — Put the project on GitHub
1. Open https://github.com/
2. Create a new repository, e.g. `premacha-chaha-v3`.
3. Upload `index.html` and `supabase_v3.sql` (README optional).
4. Commit the files.

### Step 7 — Deploy on Vercel
1. Open https://vercel.com/
2. Sign in with GitHub.
3. Click Add New -> Project.
4. Select `premacha-chaha-v3`.
5. Framework Preset: Other.
6. Build Command: leave empty.
7. Output Directory: leave empty.
8. Click Deploy.
9. Vercel gives you a public `vercel.app` URL.

### Step 8 — Configure Supabase Auth URL
After deployment:
1. Supabase -> Authentication -> URL Configuration.
2. Set Site URL to your Vercel URL.
3. Add the Vercel URL to Redirect URLs if required.

### Step 9 — Test
Test:
- Login
- Add item
- Stock in
- Sale with Cash
- Sale with UPI
- Sale with Card
- Expense
- Daily closing
- Reports
- Staff login

## Important security
Never place a Supabase service_role/secret key in frontend code.
The browser should use the publishable/anon key plus Auth and RLS.

## Free hosting
Vercel has a free tier suitable for a small personal/shop web app. Supabase also has a free tier, subject to its current usage limits.

## Next version ideas
- Barcode scanner
- Thermal receipt printing
- Product-wise sales
- Purchase/supplier outstanding
- GST invoice
- WhatsApp daily report
- Multiple branches
- Backup/export
