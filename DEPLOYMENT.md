# CyberScore deployment

## Architecture
- Frontend: Netlify (static HTML/CSS/JS)
- API: Node.js/Express (deploy separately to Render, Railway, Fly.io, VPS, etc.)
- Database: PostgreSQL
- Payments: Fapshi

Netlify is the frontend host; the Express API needs a server runtime unless you migrate its routes to Netlify Functions.

## 1. Database
Create PostgreSQL and run `backend/schema.sql`.

## 2. API
Deploy `backend/` as a Node service. Set:
`DATABASE_URL`, `JWT_SECRET`, `FRONTEND_URL`, `FAPSHI_BASE_URL`, `FAPSHI_APIUSER`, `FAPSHI_APIKEY`, `FAPSHI_WEBHOOK_SECRET`.

For the competition use Fapshi sandbox first. Never commit API credentials.

## 3. Frontend
Set `config.js` to your API URL:
`window.CYBERSCORE_API = 'https://YOUR-API-DOMAIN/api';`
Then deploy the project root to Netlify.

## 4. Fapshi webhook
Set the Fapshi webhook/callback target to:
`https://YOUR-API-DOMAIN/api/webhooks/fapshi`
Configure the same webhook secret in the API environment.

## 5. Demo
1. Register a business.
2. Enter a domain you own or have explicit authorization to assess.
3. Select industry/size and run the CyberScore Intelligence Engine.
4. Show the score, priority and recommendations.
5. Open Services and demonstrate Fapshi checkout in sandbox.
6. Show Cyber News and Partnerships.
