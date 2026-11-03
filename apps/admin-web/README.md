# Compassion Health Screening Platform — Admin Dashboard

The Admin Dashboard is the web application for authorized Center Administrators to manage facilities, providers, beneficiaries, clinical screenings, referrals, and fiscal-year reports. It is built with Next.js and communicates with the platform's separate FastAPI backend.

## Features

- Administrator sign-in with email, password, and OTP verification.
- First-login password setup and password reset flows.
- Facility and provider administration.
- Beneficiary and screening oversight.
- Referral management.
- Fiscal-year reports and report exports.
- Report question-and-answer interface.

The backend is responsible for authentication, authorization, and access to protected data. Frontend route guards are an additional user-interface check, not a replacement for backend authorization.

## Technology

- Next.js 16
- React 19
- TypeScript
- Tailwind CSS 4
- Lucide React

## Prerequisites

- Node.js 20.9 or later.
- npm.
- A running instance of the [FastAPI backend](https://github.com/Susanwanjiruu/Health_screening_platform_backend).

## Getting started

Run these commands from the `apps/admin-web/` directory:

```bash
npm install
cp .env.example .env.local
```

Edit `.env.local` and set the backend API URL:

```env
NEXT_PUBLIC_API_BASE_URL=http://localhost:8000/api/v1
```

Start the development server:

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

Ensure the backend is running and reachable at the configured URL.

## Environment configuration

| Variable | Purpose | Example |
| --- | --- | --- |
| `NEXT_PUBLIC_API_BASE_URL` | Backend API base URL, including the `/api/v1` prefix | `http://localhost:8000/api/v1` |

**Important:** Next.js exposes variables prefixed with `NEXT_PUBLIC_` to browser-side code. This variable must contain only the API endpoint URL. Never place passwords, API keys, tokens, or signing secrets in it.

Keep `.env.local` out of version control. The committed `.env.example` contains a local-development example only.

## Available scripts

Run from `apps/admin-web/`:

| Command | Description |
| --- | --- |
| `npm run dev` | Start the development server |
| `npm run build` | Build the production application |
| `npm run start` | Start the production server |
| `npm run lint` | Run ESLint |

## Main routes

| Route | Purpose |
| --- | --- |
| `/` | Admin dashboard |
| `/login` | Administrator sign-in |
| `/login/verify` | OTP verification |
| `/login/first-login` | First-login password setup |
| `/login/forgot-password` | Request a password reset |
| `/login/reset-password` | Reset password |
| `/providers` | Provider management |
| `/reports` | Reporting and report assistant |
| `/settings` | Application settings |

The backend API is the source of truth for permissions and data access. When the backend is running, its API documentation may be available at `http://localhost:8000/docs` and `http://localhost:8000/redoc`, depending on backend configuration.

## Security notes

This platform handles sensitive health and identity information.

- Never commit local environment files, credentials, access tokens, or private keys.
- Do not use real patient or beneficiary information in test fixtures, screenshots, logs, or public documentation.
- Keep AI provider credentials on the backend; do not expose them through public Next.js environment variables.
- Use HTTPS and appropriately restricted origins in deployed environments.
- Enforce authorization on every protected backend endpoint. A frontend route guard alone is not sufficient.

## Related repositories

- [FastAPI Backend](https://github.com/Susanwanjiruu/Health_screening_platform_backend)
- [Doctor Mobile App](https://github.com/Susanwanjiruu/Health_screening_platform_mobile)
