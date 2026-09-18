# Dipen URL Shortener

A production-oriented URL shortener starter for `short.dipenbrahma.in`. The static app is deployable to Vercel immediately and includes responsive UI, dark mode, local preview persistence, QR generation, analytics dashboard, legal pages, PWA support, and an API-ready architecture.

## Run

```bash
npx serve .
```

The frontend uses localStorage in preview mode. For production, deploy `backend/` and set `API_BASE_URL` in your frontend build integration (or replace the persistence functions in `app.js` with the documented API calls).

## Included

- Responsive Tailwind UI, SEO metadata, PWA manifest/service worker
- Custom slugs, password-protected-link UI, QR codes, link table, analytics overview
- Backend-ready API contract and MongoDB schema in `backend/`
- Docker and Vercel configuration
- Security checklist and deployment guide in `docs/DEPLOYMENT.md`

## API contract

`POST /api/urls` `{ url, slug?, password?, expiresAt? }` · `POST /api/urls/bulk` `{ urls: [] }` · `GET /api/urls/:slug` · `GET /api/urls/:slug/analytics` · `GET /api/admin/overview`.

> Never expose admin credentials in frontend code. Put the API behind HTTPS, a firewall, and a secret manager.
