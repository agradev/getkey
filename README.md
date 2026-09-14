# AGRA License Control V26

Cloudflare Worker dashboard based directly on V25. This release replaces the misleading License Growth Signal with a real 7-day activity view based on `created_at` from the license registry.

## GitHub deployment
- `npm run check`
- `npx wrangler deploy`

## Cloudflare variables/secrets
Keep the existing working values:
- `AGRA_API_URL=https://agra-session-lease-final.vercel.app`
- `ADMIN_SECRET` = exact Production API ADMIN_SECRET
- `DASHBOARD_SESSION_SECRET`
- `DASHBOARD_OWNER_PASSWORD_HASH`

Do not commit secrets to GitHub.
