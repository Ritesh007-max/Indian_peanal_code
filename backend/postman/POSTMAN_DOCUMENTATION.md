# Indian Law Penal Code API — Postman Documentation

This document summarizes the Postman collection and how to import and use it.

## Importing
- Open Postman → Import → Choose File → select [backend/postman/indian-law-penal-code.postman_collection.json](backend/postman/indian-law-penal-code.postman_collection.json).
- Or in Postman, use "Import" → "Link" with a hosted URL for the above file.

## Environment / Variables
- `baseUrl` (default): `http://localhost:5000`
- `authToken`: set to a valid JWT for protected endpoints.
- `lawId`, `userId`, `reportId`: example IDs used in requests.

After importing, set the `baseUrl` and `authToken` in the collection or an environment.

## Authentication
Protected endpoints use `Authorization: Bearer {{authToken}}`. Use the `User Login` request to obtain a token and paste it into the `authToken` variable.

## Sections & Key Endpoints
The collection is organized into these folders. For full examples, see the imported collection.

- **0. Health & Diagnostics**
  - GET `/` — API Root Check
  - GET `/api/v1/health` — API v1 health

- **1. Authentication Suite**
  - POST `/api/v1/auth/register` — User Registration
  - POST `/api/v1/auth/login` — User Login
  - GET/PATCH `/api/v1/auth/profile` — Get / Update profile (requires auth)
  - POST `/api/v1/auth/forgot-password` — Request OTP
  - POST `/api/v1/auth/reset-password` — Reset password with OTP

- **2. Laws Core CRUD**
  - GET `/api/v1/laws` — List laws (supports `page`, `limit`, `sort`)
  - POST `/api/v1/laws` — Create law (admin)
  - GET `/api/v1/laws/{{lawId}}` — Get law by ID
  - PATCH `/api/v1/laws/{{lawId}}` — Update law (admin)
  - DELETE `/api/v1/laws/{{lawId}}` — Delete law (admin)

- **3. Search & Filters**
  - GET `/api/v1/search/laws?q=...` — Search laws
  - GET `/api/v1/laws/filter/act/:actName` — Filter by act
  - GET `/api/v1/laws/filter/category/:category` — Filter by category

- **4. Aggregation Analytics**
  - GET `/api/v1/analytics/laws/most-viewed`
  - GET `/api/v1/analytics/laws/most-bookmarked`
  - GET `/api/v1/analytics/laws/by-category`

- **5. Counts Statistics**
  - GET `/api/v1/stats/laws/count`
  - GET `/api/v1/stats/laws/active`

- **6. Administration Suite**
  - GET `/api/v1/admin/users` — List users (admin)
  - PATCH `/api/v1/admin/users/{{userId}}/ban` — Ban user
  - PATCH `/api/v1/admin/reports/{{reportId}}/resolve` — Resolve report

- **7. JWT Utility Utilities**
  - POST `/api/v1/jwt/generate-token` — Generate token (debug)
  - POST `/api/v1/jwt/verify-token` — Verify and decode token

- **8. Middleware Practice**
  - GET `/api/v1/middleware/logger`
  - GET `/api/v1/middleware/auth` — Demo protected middleware

## Notes & Next Steps
- The collection already contains request bodies and example payloads. Review and update descriptions or examples in the imported collection as needed.
- To publish official Postman docs, import this collection into Postman and use the Postman workspace's Publish → Documentation feature.

## Collection file
The source collection file is at [backend/postman/indian-law-penal-code.postman_collection.json](backend/postman/indian-law-penal-code.postman_collection.json).
