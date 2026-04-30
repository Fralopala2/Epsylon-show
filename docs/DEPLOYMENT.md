# Deployment (Free Tier First)

## Target stack
- API host: Render Free Web Service
- PostgreSQL: Neon Free
- Redis: Upstash Free
- Billing: Stripe
- Storage: Cloudflare R2
- Desktop release: GitHub Releases (Tauri artifacts)

## 1) Provision cloud dependencies
1. Create Neon project and copy `DATABASE_URL`.
2. Create Upstash Redis database and copy `REDIS_URL`.
3. Create Stripe products/prices for `pro`, `premium`, `lifetime`.
4. Create R2 bucket and access keys.

## 2) Configure Render
1. Connect this repo in Render.
2. Use `render.yaml` from repository root.
3. Set required environment variables:
   - `DATABASE_URL`
   - `REDIS_URL`
   - `JWT_ACCESS_SECRET`
   - `STRIPE_SECRET_KEY`
   - `STRIPE_WEBHOOK_SECRET`
   - `STRIPE_PRICE_PRO`
   - `STRIPE_PRICE_PREMIUM`
   - `STRIPE_PRICE_LIFETIME`
   - `API_ALLOWED_ORIGINS`

## 3) Stripe webhook
1. Create webhook endpoint in Stripe dashboard:
   - URL: `https://<your-api-domain>/webhooks/stripe`
2. Subscribe to events:
   - `checkout.session.completed`
   - `invoice.paid`
   - `invoice.payment_failed`
   - `customer.subscription.updated`
   - `customer.subscription.deleted`
3. Save signing secret to `STRIPE_WEBHOOK_SECRET`.

## 4) Desktop production API
1. Create desktop env file (`apps/desktop/.env.production`):
   - `VITE_API_URL=https://<your-api-domain>`
2. Build and publish desktop:
   - `npm run build:phase3`
3. Publish generated artifacts to GitHub Releases.

## 5) Production sanity checks
- `GET /health` returns 200.
- Register/login/refresh/logout works.
- `GET /billing/plans` returns plans.
- Stripe checkout returns URL.
- Stripe webhook updates subscription state.
