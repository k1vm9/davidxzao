---
name: Dashboard auth
description: How the DAVID V1 dashboard authentication works
---

## Rule
Dashboard password is stored in `config.json` at `dashboard.password`. Current value: `Sain12`.

**How to apply:**
- POST `/api/login` with `{ password }` → returns `{ ok, token }`
- All subsequent API calls use `x-david-token: <token>` header
- Token expires in 8 hours
- Socket.io authenticates via query param `?token=<token>`

**Why:** Token-based auth avoids session cookies and works cleanly across the proxied Replit iframe preview.
