# XonAI AI — Deployment Checklist

## What is ready in this package
- Node/Express production configuration
- API rate limiting and security headers
- Health/readiness endpoints
- Docker + Docker Compose
- Render deployment blueprint
- PostgreSQL migration blueprint (`db/schema.sql`)
- Razorpay webhook signature handling + captured-payment reconciliation
- Preflight syntax check
- Graceful shutdown and error handling

## What must still be supplied by the owner
1. Hosting account/domain
2. Production OpenAI key
3. Production Razorpay account + webhook secret
4. Google OAuth credentials (optional)
5. Real video/STT/TTS provider credentials (optional)
6. Production email provider
7. Managed PostgreSQL and migration of the current JSON data

Never commit `.env` or secret keys.

## Local check
```bash
npm install
npm run preflight
npm start
```
Then open `/api/health` and `/api/readiness`.

## Important
This package does not claim that third-party services are live. They become active only after their credentials/accounts are configured and end-to-end tests pass.

## Added integration adapters
- OpenAI cloud STT/TTS endpoints: `/api/speech/transcribe` and `/api/speech/synthesize` when `STT_PROVIDER=openai` / `TTS_PROVIDER=openai`.
- Resend email adapter for password-reset mail and admin test mail when `EMAIL_PROVIDER=resend`.
- Generic video-provider adapter at `/api/media/video` using `VIDEO_PROVIDER_URL` + `VIDEO_PROVIDER_API_KEY`.
- PostgreSQL migration script: `npm run db:migrate` after setting `DATABASE_URL`. The current JSON app remains the safe default; switching the live store to PostgreSQL still requires the DB adapter to be enabled and tested.
- Google OAuth, Razorpay, OpenAI image generation, Render/Docker deployment configuration and production environment examples are included.

## Owner-only activation
These adapters are code-complete but intentionally remain inactive until the owner supplies real credentials and verifies the external accounts. Never commit secrets.
