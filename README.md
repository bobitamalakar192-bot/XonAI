# XonAI AI — Final Launch Build

This package contains the current XonAI AI prototype plus the final production-readiness hardening layer.

## Run locally
1. `npm install`
2. Copy `.env.example` to `.env` and add only the credentials you actually have.
3. `npm start`
4. Open `/` and check `/api/health` and `/api/readiness`.

## Production requirements
- Use HTTPS and a managed host.
- Configure `OPENAI_API_KEY` for real AI.
- Configure Razorpay production credentials for live billing.
- Configure Google OAuth credentials if Google login is enabled.
- Configure a real video/STT/TTS provider for cloud media/voice.
- Migrate JSON storage to PostgreSQL/managed DB before multi-instance production.
- Configure an email provider for real password-reset emails.
- Set a strong `XONAI_ADMIN_KEY`.

The app deliberately does not ship secrets or pretend that external services are live without credentials.


## Final hardening
See `FINAL_HARDENING_REPORT.md` for the verified static launch audit. Run `node scripts/launch-audit.mjs` before deployment.
