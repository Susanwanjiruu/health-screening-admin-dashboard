# Compassion Health Screening Platform — Admin Dashboard

The Admin Dashboard is the web-based administration interface for the Compassion Health Screening Platform. It enables authorized Center Administrators to oversee healthcare facilities, providers, beneficiaries, clinical screenings, referrals, and annual reports.

The platform is maintained as three separate applications:

| Component | Repository | Technology | Responsibility |
| --- | --- | --- | --- |
| Admin Dashboard | [health-screening-admin-dashboard](https://github.com/Susanwanjiruu/health-screening-admin-dashboard) | Next.js 16, React 19, TypeScript, Tailwind CSS | Center Admin workflows |
| Backend API | [Health_screening_platform_backend](https://github.com/Susanwanjiruu/Health_screening_platform_backend) | FastAPI, Python, SQLAlchemy | Authentication, authorization, business logic, clinical records, reporting, and AI-assisted report queries |
| Doctor Mobile App | [Health_screening_platform_mobile](https://github.com/Susanwanjiruu/Health_screening_platform_mobile) | Flutter | Provider workflows and digital screening forms |

The backend exposes its API under `/api/v1` and is shared by the web dashboard and mobile application.

## Features

The dashboard includes the following documented workflows:

- Administrator authentication, including OTP verification and first-login password setup.
- Facility and provider administration.
- Beneficiary management.
- Clinical screening oversight.
- Referral management.
- Fiscal-year reporting and report exploration with an AI chat assistant.
- Application settings.

Access to protected data and operations is enforced by the backend. Frontend route guards and hidden UI controls are not substitutes for server-side authorization.

## Technology stack

- Next.js 16
- React 19
- TypeScript
- Tailwind CSS 4
- Lucide React icons

## Project structure

The web application lives in `apps/admin-web/`.

```text
apps/admin-web/
├── app/          # Next.js App Router pages and layouts
├── components/   # Shared dashboard and authentication components
├── lib/
│   ├── api/      # Backend API client and feature-specific API functions
│   ├── auth/     # Authentication and session helpers
│   └── utils/    # Shared utilities
├── public/       # Static assets
├── package.json
└── .env.example  # Local environment variable template
```

## Prerequisites

- Node.js 20.9 or later (required by the installed Next.js 16 release).
- npm.
- Access to a running instance of the [FastAPI backend](https://github.com/Susanwanjiruu/Health_screening_platform_backend).

Use a Node.js version supported by the installed Next.js release.

## Getting started

Clone the repository and move into the web application directory:

```bash
git clone https://github.com/Susanwanjiruu/health-screening-admin-dashboard.git
cd Health_screening_platform_admin_dashboard/apps/admin-web
```

Install dependencies:

```bash
npm install
```

Create your local environment file from the example:

```bash
cp .env.example .env.local
```

Update `.env.local` with the base URL of your running backend. Then start the development server:

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Environment configuration

The API client reads the backend base URL from `NEXT_PUBLIC_API_BASE_URL`.

| Variable | Purpose | Example |
| --- | --- | --- |
| `NEXT_PUBLIC_API_BASE_URL` | Base URL for the backend API, including the `/api/v1` prefix | `http://localhost:8000/api/v1` |

Example:

```env
NEXT_PUBLIC_API_BASE_URL=http://localhost:8000/api/v1
```

This variable is prefixed with `NEXT_PUBLIC_`, so its value is exposed to browser-side code. It must contain only the API endpoint URL, never passwords, API keys, signing secrets, or other credentials.

Keep `.env.local` out of version control. The committed `.env.example` should contain placeholder or local-development values only.

## Available scripts

Run these commands from `apps/admin-web/`:

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Next.js development server |
| `npm run build` | Build the application for production |
| `npm run start` | Start the production build |
| `npm run lint` | Run ESLint |

## Documented routes

| Path | Purpose |
| --- | --- |
| `/` | Admin dashboard |
| `/login` | Administrator sign-in |
| `/login/verify` | OTP verification |
| `/login/first-login` | First-login password setup |
| `/providers` | Provider management |
| `/reports` | Reports and AI chat assistant |
| `/settings` | Application settings |

The backend API is the source of truth for permissions and data access. Refer to its interactive OpenAPI documentation when the backend is running:

- Swagger UI: `http://localhost:8000/docs`
- ReDoc: `http://localhost:8000/redoc`

These are FastAPI's default documentation paths and may be changed by backend configuration.

## Related project documentation

For backend installation, environment configuration, API contracts, authentication, roles, and business rules, see the [Backend API README](https://github.com/Susanwanjiruu/Health_screening_platform_backend).

The Flutter application is maintained separately in the [Doctor Mobile repository](https://github.com/Susanwanjiruu/Health_screening_platform_mobile).

## Security and sensitive data

This platform processes sensitive health and identity information.

- Never commit `.env.local`, credentials, tokens, or private keys.
- Do not store real patient or beneficiary data in test fixtures, screenshots, logs, or public documentation.
- Keep AI provider credentials on the backend; do not expose them through Next.js public environment variables.
- Use HTTPS and appropriately restricted origins in deployed environments.
- Ensure backend authorization checks protect every sensitive operation.

## License

No license has been specified in this repository. Unless a license is added, the source code should not be assumed to be available for reuse under an open-source license.
