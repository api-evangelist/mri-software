---
name: sync-employees
description: Page through MRI OnLocation employees with keyset pagination and create or update staff records.
api: mri-software:mri-onlocation-api
operations: [getStaffList, getStaff, createStaff, updateStaff]
generated: '2026-10-20'
method: generated
---
1. Authenticate: exchange client credentials at https://login.whosonlocation.com/oauth2/token (scope `staff:read staff:write` as configured on the client), send `Authorization: Bearer <token>` and `Accept: application/json` (XML is the default otherwise).
2. `getStaffList` with `order=id&limit=<= 5000`; continue with `q=id>{last id}` until a page returns fewer rows than the limit.
3. `getStaff` for detail; `createStaff` for new people; `updateStaff` to change one. PUT replaces the entity: send every field, omitted fields are emptied.
4. No idempotency key exists: check for an existing record before `createStaff` retries. On 429 wait for `Retry-After` (100 requests/minute per credential).
