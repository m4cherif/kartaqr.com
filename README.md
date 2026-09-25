KARTAQR.COM

A QR-based digital catalog SaaS platform for small and medium businesses — designed, built, and shipped end-to-end, solo.

🔗 Live product: kartaqr.com

This repository is a public overview of the project for portfolio purposes. The production codebase is private (it powers a live product with real merchants and real payments).

What It Is

KARTA QR lets any small business create a digital storefront — products, prices, offers, contact info — accessible instantly to customers by scanning a single QR code. No app download, no account creation for the customer, no technical skill required from the merchant.

Built mobile-first and fully bilingual (English / Arabic, with proper right-to-left layout), for merchants and customers who move naturally between both.

Core Features
Digital storefront — bilingual, mobile-optimized product catalog with grid/list display options
Offers & discounts — time-limited promotions with auto-generated shareable promo images
Printable QR sign — instantly generated, print-ready QR code for the merchant's counter/window
Partner/referral program — a full commission system: partners refer merchants and earn a recurring percentage of every subscription payment, for as long as the merchant stays subscribed
Automated marketing video generation (in active development) — short promotional videos composed from a store's real product data, on a subscription-tier-based schedule. Currently functional but not yet production-quality — an honest, ongoing engineering effort, not a finished feature
Payment processing — full PayPal integration handling real subscription billing
Admin operations panel — subscription/payment management, partner performance tracking, platform-wide analytics
Tech Stack

Frontend: Next.js (App Router), TypeScript, Tailwind CSS, shadcn/ui Backend: Supabase (PostgreSQL, Auth, Storage), Row-Level Security as the primary authorization model Infrastructure: Netlify (hosting, serverless functions, scheduled jobs, background functions) Integrations: PayPal (payments), Shotstack (video rendering), Resend (transactional email) i18n: next-intl, full Arabic/English support with logical (direction-aware) layout throughout

Engineering Highlights

A few things I'm genuinely proud of from an engineering standpoint:

RLS-first security model — nearly every access-control decision lives in Postgres Row-Level Security policies, not application code, verified through deliberate live "attack" testing (attempting writes as unauthorized roles, confirming they're rejected) rather than just trusting the policy definitions on paper
Atomic financial ledger design — subscription payments, partner commissions, and store activation all flow through a single, append-only, idempotent ledger table with atomic database functions — no split-write windows where a payment could be recorded without a corresponding activation, or vice versa
Webhook-driven payment reconciliation — PayPal payment confirmation is handled via signature-verified webhooks with a fallback reconciliation sweep, so the system can self-heal if a webhook delivery ever fails
Systematic debugging discipline — treating "it looks fixed" as a hypothesis to verify, not a conclusion: reproducing issues against real infrastructure, isolating variables one at a time, and confirming fixes with direct evidence (database state, real API responses, live device testing) rather than assuming a change worked because the code looks right
Solo, End-to-End

Every part of this — architecture, database design, security model, payment integration, UI/UX, deployment, and ongoing operations — was designed and built by me, from an empty repository to a live product serving real customers.

📍 Based in Qatar. Built for the Gulf SME market, expanding toward global reach.
