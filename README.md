# CourseHub

Full-stack **MERN** app for uploading and managing courses. React (Vite) UI talks to an Express/MongoDB API; media is handled via Cloudinary (and Vercel Blob helpers).

**UI deploy (from CORS config):** [courseui.vercel.app](https://courseui.vercel.app)

## Overview

CourseHub lets authenticated users register/login, create and update courses, and upload related media. The repo is split into `Api/` (backend) and `Ui/Course/` (frontend).

## Features

- User auth (JWT + bcrypt) and session-aware UI
- Course create / update / list flows
- Media upload via Cloudinary / multer; image compression on the client
- Storage routes for blobs/files
- Excel (`xlsx`) support for bulk-oriented workflows in the UI
- CORS allowlist for local and production frontends

## Stack

| Area | Tech |
|------|------|
| Frontend | React 18, Vite, MUI, Axios, react-hook-form, react-toastify |
| Backend | Node.js, Express, Mongoose |
| Auth | JWT, bcrypt |
| Media | Cloudinary, multer, sharp, `@vercel/blob` |
| Deploy | Vercel (`Api/vercel.json`) |

## Structure

```
Api/
  index.js          # Express entry, CORS, routes
  Models/           # Course, User
  Routes/           # course, user, storage
  authMiddleware.js
Ui/
  Course/           # Vite React app (Pages: Login, Home, Upload, Create, Update, …)
```

## Setup

### API

```bash
cd Api
npm install
# Set MONGOURL, PORT, JWT secret, Cloudinary (and related) env vars — do not commit .env
npm start
```

### UI

```bash
cd Ui/Course
npm install
npm run dev
```

Point the client API base URL at your running backend. Production builds: `npm run build` in `Ui/Course`.

## Notes

Env files may exist locally for development; keep secrets out of commits and prefer `.env.example` patterns for documentation.
