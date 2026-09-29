# XonAI AI — Backend connection

The website can run from GitHub Pages while the Express API runs on Render/another Node host.

## 1. Deploy the backend
Use this repository/package as a Node service. Start command: `npm start`.

## 2. Add server secrets
At minimum: `OPENAI_API_KEY`. Recommended production settings include:
- `OPENAI_MODEL=gpt-5.6-luna`
- `OPENAI_IMAGE_MODEL=gpt-image-2`
- `STT_PROVIDER=openai`
- `TTS_PROVIDER=openai`
- `FRONTEND_ORIGINS=https://YOUR_GITHUB_USERNAME.github.io`

Add Razorpay, Google OAuth, email, PostgreSQL and video-provider credentials only when those services are enabled.

## 3. Connect GitHub Pages frontend
Open the Pages URL once with:
`https://YOUR_GITHUB_USERNAME.github.io/xonai-ai/?api=https://YOUR-BACKEND-DOMAIN`

The frontend stores the backend origin in localStorage and all `/api/...` calls are routed there.

## 4. Verify
Open `/api/health` and `/api/version` on the backend. Then use AI Teacher and ask a normal study question.

No API key is placed in the browser.
