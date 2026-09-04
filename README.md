# Golpogram

A writing platform where one account gives you everything — feed, story
library, events, and messages — instead of juggling separate logins for
each feature.

This repo is the **foundation prototype**: unified authentication and a
single user profile, built on a data model where every future feature
(stories, events, posts, messages) hangs off the same `User` table.

## Why this exists

The original version of Golpogram (PHP + separate databases per feature)
required users to create up to 3 different accounts to use the whole
platform. This rebuild fixes that at the root: one database, one identity,
one login.

## Tech stack

- **Next.js 14** (App Router) — React frontend + API routes in one project
- **Prisma + SQLite** (swappable to Postgres) — unified data model
- **jose** — signed session cookies (JWT)
- **bcryptjs** — password hashing
- **Tailwind CSS** — styling
- **Zod** — request validation

## Getting started

```bash
npm install
cp .env.example .env   # then set JWT_SECRET (e.g. `openssl rand -base64 32`)
npm run db:push
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

| Route | What it does |
|---|---|
| `/signup` | Create an account |
| `/login` | Sign in |
| `/profile` | Protected — view/edit your unified profile |

## Data model

One `User` table. Everything else references it:
