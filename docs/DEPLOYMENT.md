# Deployment guide

## Vercel frontend
Import this repository into Vercel, keep the root directory as `/`, and deploy as a static site. Add the custom domain `short.dipenbrahma.in`. The included rewrite forwards `/api/*` to `api.short.dipenbrahma.in`; change it to your backend URL.

## Backend VPS
Use Node 20+, MongoDB Atlas or a private MongoDB instance, and Nginx/Caddy for TLS. Copy `.env.example` to `.env`, set strong random secrets, then:

```bash
cd backend && npm ci && npm start
```

Run with systemd or PM2. Allow only 80/443 through the firewall and keep port 8080 private. Configure Cloudflare DNS with proxy enabled, SSL mode Full (strict), HSTS, bot fight mode, and a rate limit rule for `/api/*`.

## Docker
`docker build -t dipen-links . && docker run --env-file .env -p 8080:80 dipen-links` serves the frontend. Run the backend separately with MongoDB; a managed database is recommended for production.

## Security checklist
HTTPS, strong admin secret, MongoDB network allowlist, Helmet, CORS allowlist, rate limiting, payload limits, CSRF token for cookie-authenticated admin mutations, strict validation, NoSQL sanitization, XSS-safe output, Argon2/bcrypt password hashes, reCAPTCHA on public abuse-sensitive routes, backups, audit logs, and monitoring.
