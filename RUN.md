# EMS – Run Backend + Frontend Together

## Prerequisites

- **Node.js** (v18+)
- **MongoDB** running locally (default: `mongodb://localhost:27017/ems-db`)
- Backend and frontend dependencies installed

## One-time setup

From the project root (`R:\wamp64\www\ems`):

```bash
npm run install:all
```

Or install manually:

```bash
npm install
cd EMS-BE && npm install
cd ../EMS-FE && npm install
```

## Run both (backend + frontend)

From the project root:

```bash
npm run dev
```

- **Backend**: http://localhost:5000 (API base: http://localhost:5000/api)
- **Frontend**: http://localhost:3000

## Run separately

- Backend only: `npm run dev:be` (or `npm run start:be`)
- Frontend only: `npm run dev:fe` (or `npm run start:fe`)

## Integration summary

- Frontend `.env` uses `REACT_APP_API_URL=http://localhost:5000`; API requests use `http://localhost:5000/api`.
- Backend CORS allows `http://localhost:3000` (see `EMS-BE/.env` → `CORS_ORIGIN`).
- Auth is still using the frontend **fake backend** (`REACT_APP_DEFAULTAUTH=fake`). To use real backend auth later, switch to JWT and point login/register to `/api/auth/login` and `/api/auth/register`.

## If the backend fails to start

- Ensure MongoDB is running (e.g. WAMP or a separate MongoDB service).
- Check `EMS-BE/.env` for `MONGODB_URI` and `PORT=5000`.
