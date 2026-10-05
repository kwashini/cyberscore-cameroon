# CyberScore Cameroon — Full-stack MVP
Founder: **Kwashini Tagha**

### Backend
Node.js + Express + PostgreSQL + bcrypt + JWT HTTP-only cookie sessions + Fapshi Initiate Pay + signed Fapshi webhook.

### Fapshi
Start with sandbox. Fapshi's current docs define `POST /initiate-pay` at `https://sandbox.fapshi.com/initiate-pay`, authenticated with `apiuser` and `apikey`. It returns a hosted `link` and `transId`. Configure the service webhook as:
`https://YOUR-BACKEND-DOMAIN/api/webhooks/fapshi`
and set the same webhook secret in `FAPSHI_WEBHOOK_SECRET`.
When approved for production, switch to `https://live.fapshi.com` and live credentials. Never commit API keys.

### Run
1. Create PostgreSQL database.
2. Run `backend/schema.sql`.
3. Copy `backend/.env.example` to `backend/.env`.
4. Fill database, JWT and Fapshi sandbox credentials.
5. `cd backend && npm install && npm start`
6. Open `http://localhost:8080`.

### Production
Deploy the frontend to Netlify and the Node backend to a Node host with PostgreSQL. Set `FRONTEND_URL` to the Netlify URL. Keep Fapshi credentials only on the backend. This MVP's scanner is deliberately non-invasive and only performs URL-level checks; a production scanner should use isolated workers, allowlists, scope records and rate limits.

© 2026 CyberScore. All rights reserved.
