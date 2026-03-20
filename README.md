# EMS Test Task

Event Management System (EMS) with a NestJS + Prisma API and a Next.js frontend. A PostgreSQL database is provided via `docker-compose.yml`.

**Repo Layout**
1. `api` - NestJS backend (Prisma, JWT auth, Swagger).
2. `frontend` - Next.js 16 App Router frontend (React Query, MUI, Google Maps).
3. `docker-compose.yml` - Local PostgreSQL service.

**Requirements**
1. Node.js and npm (for `api` and `frontend`).
2. Docker (optional, for PostgreSQL).

**Submodules**
This repo uses git submodules for `api` and `frontend`. If you cloned without submodules:

```bash
git submodule update --init --recursive
```

**Quick Start (Local)**
1. Start PostgreSQL via Docker:

```bash
docker compose up -d
```

2. Create API env file in `api`:

```env
PORT=3000
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/ems_db"
JWT_SECRET="your_jwt_secret"
```

3. Install and run the API:

```bash
cd api
npm install
npm run prisma:migrate
npm run prisma:seed
npm run start:dev
```

4. Create frontend env file in `frontend`:

```env
NEXT_PUBLIC_API_URL="http://localhost:3000/api"
NEXT_PUBLIC_GOOGLE_MAPS_API_KEY="your_api_key_here"
```

5. Install and run the frontend:

```bash
cd ../frontend
npm install
npm run dev
```

Frontend runs on `http://localhost:7777`.

**API Docs**
Swagger UI is available at `http://localhost:3000/api/docs` after the API starts.

**Scripts**
API (`api/package.json`)
1. `npm run start` - Start API.
2. `npm run start:dev` - Start API with watch mode.
3. `npm run prisma:migrate` - Apply Prisma migrations.
4. `npm run prisma:seed` - Seed database.

Frontend (`frontend/package.json`)
1. `npm run dev` - Start Next.js dev server on port 7777.
2. `npm run build` - Build for production.
3. `npm run start` - Start production server on port 7777.

