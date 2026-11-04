# Ecommerce API - Postman Pipeline

## Files
- `ecommerce-API-project.json` — Postman collection export
- `my-environment.json` — Postman environment template (fill in values before running)

## Local Setup

### Prerequisites
- Node.js installed
- Newman: `npm install -g newman newman-reporter-htmlextra`

### Run locally
```bash
newman run ecommerce-API-project.json \
  --environment my-environment.json \
  --reporters cli,htmlextra \
  --reporter-htmlextra-export newman-report.html
```

## CI/CD (GitHub Actions)
Add the following secrets to your GitHub repository:
- `BASE_URL` — The base URL of your ecommerce API (e.g. `https://api.example.com`)

The pipeline runs automatically on push to `main` or `develop` branches and on pull requests to `main`.

## Environment Variables
| Variable | Description | Set in CI via |
|---|---|---|
| `base_url` | API base URL | `BASE_URL` GitHub secret |
| `access_token` | JWT access token (set by login request) | Auto-populated at runtime |
| `refresh_token` | JWT refresh token (set by login request) | Auto-populated at runtime |
| `product_id` | Product ID for testing | Hardcode in environment file |
| `cart_id` | Cart ID for testing | Hardcode in environment file |
