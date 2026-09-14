# AGRA License Dashboard V24 — GitHub / Cloudflare

Cloudflare Worker dashboard package. The dashboard HTML is embedded in `worker.js`, so this repository does not require a separate static-assets directory.

## Cloudflare secrets / variables
Set these in the Cloudflare Worker, NOT in GitHub:

- `AGRA_API_URL` = `https://agra-session-lease-final.vercel.app`
- `ADMIN_SECRET` = exactly the Production `ADMIN_SECRET` used by the License API
- `DASHBOARD_SESSION_SECRET` = a separate random session secret
- `DASHBOARD_OWNER_PASSWORD_HASH` = SHA-256 hash of the Owner password

Never commit secret values to GitHub.

## GitHub deployment
1. Create a GitHub repository.
2. Upload `worker.js`, `wrangler.toml`, `package.json`, and this README to the repository root.
3. In Cloudflare Workers & Pages, create/import the Worker from Git.
4. Select this repository and the production branch.
5. Build command: `npm run check` (or leave blank if Cloudflare does not require one).
6. Deploy command: `npx wrangler deploy`.
7. Add the four variables/secrets above in Cloudflare before testing.

## Important
This V24 dashboard is a Cloudflare Worker BFF. The current License API backend remains the V21 FAST API until the actual backend migration is completed and validated.

## Diagnostic
After Owner login, open:
`/api/owner/auth-test`

This verifies Worker → Production API authorization without exposing the actual `ADMIN_SECRET`.
