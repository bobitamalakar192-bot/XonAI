# XonAI AI — Production Runbook

## 1. Deploy
1. Create a Node 22 web service on the selected host.
2. Deploy this repository/package.
3. Set `NODE_ENV=production` and a strong `XONAI_ADMIN_KEY`.
4. Set the platform-provided `PORT`.
5. Add only secrets through the host secret manager.
6. Confirm `GET /api/health` returns `ok: true`.
7. Confirm `GET /api/readiness` and `GET /api/media/status`.

## 2. AI
Set `OPENAI_API_KEY` and, if needed, the model variables. Never put API keys in frontend code, HTML, Git, or screenshots.

## 3. Database
The current application keeps its operational store in `data/xonai.json`. For a real multi-instance deployment, provision managed PostgreSQL, run `npm run db:migrate`, then complete an application-level PostgreSQL persistence migration before scaling to multiple instances. The included schema/migration is a migration asset, not a claim that the running app has already switched storage engines.

## 4. Payments
Configure Razorpay live credentials and webhook secret only after account/KYC approval. Verify signatures server-side and test with a small controlled transaction before public launch. Reconcile subscription expiry through a reliable scheduled job.

## 5. Voice / Email / Video
Configure provider credentials and test each integration from the admin/test endpoints. Browser STT/TTS remains available as a local fallback where supported. The video endpoint expects a provider-specific API contract at `VIDEO_PROVIDER_URL`; adapt the payload/status flow to the chosen provider before production use.

## 6. OAuth / Domain
Set Google OAuth redirect URI to the exact HTTPS production callback. Point DNS to the host and enforce HTTPS. Update `GOOGLE_REDIRECT_URI` and `EMAIL_FROM` to the final domain.

## 7. Final checks
- Signup/login/logout
- Password reset email
- Google login
- AI chat/vision/image
- Adaptive practice/test/revision/planner
- Voice STT/TTS
- Video job
- Razorpay order/verify/webhook
- Analytics/guardian/teacher paths
- Backups and restore drill
- Rate limiting and logs

## 8. Rollback
Keep the previous deployment artifact. If a release fails health checks, roll back to the previous artifact and preserve logs. Do not delete the previous database backup during an incident.
