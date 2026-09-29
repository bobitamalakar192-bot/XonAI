# XonAI AI — Final Launch Checklist

## Accounts/configuration
- [ ] Hosting account + custom domain (optional)
- [ ] Production PostgreSQL `DATABASE_URL`
- [ ] OpenAI production key
- [ ] Razorpay live keys + webhook secret
- [ ] Google OAuth credentials (if Google Login is enabled)
- [ ] SMTP/email provider for password reset
- [ ] STT/TTS provider keys
- [ ] Video-generation provider key/endpoint

## Deployment
1. Copy `.env.production.example` to the hosting provider's environment-variable settings.
2. Fill secrets directly in the provider dashboard; never commit `.env` files.
3. Run `node scripts/validate-env.mjs`.
4. Deploy with the included Dockerfile/Render config.
5. Set Razorpay webhook URL to `/api/billing/webhook` and use the exact webhook secret.
6. Run the smoke tests below.

## Smoke tests
- [ ] Signup/login/logout
- [ ] Profile save
- [ ] AI teacher response
- [ ] Image upload/vision question
- [ ] Practice/test/revision persistence
- [ ] Planner/reminder behavior
- [ ] Google Login (if enabled)
- [ ] Razorpay test payment + verified callback + webhook
- [ ] Password-reset email
- [ ] Video/image provider request
- [ ] Mobile/PWA install
- [ ] Health/readiness endpoints

## Important
The source package contains integration code and safe configuration templates. Live credentials, paid accounts, DNS, and provider-side verification must be completed in the owner's accounts before public launch.

## Final hardening audit
- [x] Required deployment/configuration files present
- [x] Core API route coverage checked statically
- [x] Secret-pattern scan completed (no bundled live secrets)
- [x] Render build command works without requiring a package-lock.json
- [x] Docker/Render/Compose configuration present
- [x] PostgreSQL migration assets present
- [x] Voice/media/email/payment integration adapters present
- [x] Final syntax/preflight checks passed in the build environment

### Environment limitation
A full live end-to-end test still requires external credentials/services and a real deployment environment. Those credentials are intentionally not bundled.
