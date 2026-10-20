---
name: pre-register-visitor
description: Pre-register an expected visitor in MRI OnLocation and review the resulting visitor sign-in events.
api: mri-software:mri-onlocation-api
operations: [createVisitorRegister, getVisitorRegister, updateVisitorRegister, deleteVisitorRegister, getVisitorEventList]
generated: '2026-10-20'
method: generated
---
1. Authenticate with a Bearer token (scopes `visitor:read` / `visitor:write`) or a legacy `APIKEY` header.
2. `createVisitorRegister` to pre-register the visitor; read it back with `getVisitorRegister`.
3. Change details with `updateVisitorRegister` (full replacement) or cancel with `deleteVisitorRegister` — the only documented reversal.
4. After arrival, `getVisitorEventList` with `order=id&limit=...` and `q=` filters to list sign-in/out events; use `time_zone=` for local timestamps.
