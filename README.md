# Dawamu Library — Standalone Module

Standalone book inventory & borrow/return system, built to merge into the main
Dawamu School Management System (DMS) later. Same stack as DMS: Node.js/Express,
SQLite (via sql.js), JWT auth.

## What it does
- **Book inventory**: add/edit/delete books, with a book code, category, shelf location, and total vs. available copies
- **Delivery tracking**: each book records date received and who delivered it (supplier/person)
- **Search & filters**: search books by title/author/ISBN/code, filter by category or availability; filter loans by book, code, or borrower
- **Borrowers**: register students (name, admission no., grade) or staff (name, staff no., department)
- **Borrow / Return**: issue a book (auto-decrements available copies), mark returned (auto-increments copies) — no fines, since this is a school setup
- **Overdue tracking**: dedicated view of everything currently overdue, with contact info
- **CSV & PDF export**: download the full loan history or book inventory as CSV or a formatted PDF
- **Settings**: change your own password from the app (no need to touch the database)

## Deploying (e.g. Render.com)

1. Push this folder to its own GitHub repo (make sure it's at the repo root, not nested in a subfolder — Render looks for `package.json` at the root).
2. On Render: New → Web Service → connect the repo.
3. Build command: `npm install`
4. Start command: `npm start`
5. Add environment variables from `.env.example` (at minimum, set `JWT_SECRET` to a long random string).
6. Note: the SQLite file lives on local disk (`db/library.sqlite`), so on most free-tier hosts it resets on redeploy. For persistent data across deploys, use a paid plan with a persistent disk, or swap in a hosted database later.

## Run it

```bash
npm install
node server.js
```

Then open **http://localhost:5500** in your browser.

Default login: `admin` / `admin123` — change this after first login (or via
`POST /api/auth/register` once logged in as admin).

## Project structure
