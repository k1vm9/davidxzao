---
name: Bot state flags
description: globalLock and silentMode flags in the bot engine
---

## Rule
`global.GoatBot.globalLock` and `global.GoatBot.silentMode` are checked in `src/engine/handlerEvents.js` AFTER the admin-only check but BEFORE prefix parsing.

- `globalLock = true` → all commands blocked except role≥3 (owner/superAdmin)
- `silentMode = true` → bot receives messages but never responds to any

**API endpoints:**
- POST `/api/bot/lock` → sets globalLock=true
- POST `/api/bot/unlock` → sets globalLock=false
- POST `/api/bot/silent` with `{ enable: bool }` → sets silentMode

**Why:** Added to bring ZAO's tier security system to DAVID. Owner retains full control even when bot is locked.
