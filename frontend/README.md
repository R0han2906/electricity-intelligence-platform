<div align="center">

# 💻 Electricity Intelligence Platform — Frontend

**React + TypeScript SPA delivering a SaaS-grade analytics dashboard for residential electricity forecasting and billing insight.**

[![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=black)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Vite](https://img.shields.io/badge/Vite-8-646CFF?logo=vite&logoColor=white)](https://vitejs.dev/)
[![Tailwind](https://img.shields.io/badge/Tailwind-v4-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](../LICENSE)

[Live App](#-live-demo) · [Backend Repo / API Docs](../backend) · [Report Bug](../../issues)

</div>

---

## 📖 Overview

This is the client-facing SPA for the Electricity Intelligence Platform — the layer users actually interact with to enter consumption history, view forecasts, and see slab-based billing projections translated into carbon impact.

Built as a modular React + TypeScript codebase with a clear separation between API access, reusable UI primitives, and view-level page sections — not a single monolithic `App.tsx`.

---

## 🎯 Live Demo

| Environment | Link |
|---|---|
| Production | `<ADD_YOUR_DEPLOYED_FRONTEND_URL>` |
| Backend API (consumed by this app) | `https://electricity-intelligence-platform-backend.onrender.com/docs` |

> Backend is on Render's free tier — expect a cold-start delay of 30–50s on first request after inactivity.

---

## 🛠️ Tech Stack

| Layer | Choice |
|---|---|
| Framework | React 19 + TypeScript |
| Bundler / Dev Server | Vite 8 |
| Styling | Tailwind CSS v4 (`@import` in `index.css`) |
| Charts | Chart.js 4 + `react-chartjs-2` |
| Routing | React Router 7 |
| Icons | Lucide React |
| Formatting | `oxfmt` (Rust-based formatter) |

---

## 📂 Folder Architecture

```text
src/
├── api/
│   └── client.ts                    # Unified REST client (fetch definitions)
├── components/
│   ├── Card.tsx                     # Reusable card container with hover states
│   ├── Button.tsx                   # Button with style variants (primary, ghost, etc.)
│   ├── Navbar.tsx                   # Header branding + user status
│   └── landing/
│       └── LandingOptionCard.tsx    # Hero landing page option cards
├── constants/
│   ├── landing.ts                   # Landing page option data
│   └── routes.ts                    # Standardized route path constants
├── sections/
│   ├── Landing/                     # Landing view
│   ├── CreateUser/                  # New user creation form
│   ├── SelectUser/                  # Existing user lookup/search
│   ├── AddConsumption/              # 12-month consumption entry form
│   └── Dashboard/                   # Analytics — charts, forecasts, insight cards
├── App.tsx                          # Router + top-level wiring
├── index.css                        # Global styles, Tailwind imports, fonts (Inter)
└── main.tsx                         # React DOM entry point
```

---

## ⚡ Dev Proxy & CORS Handling

Client-side requests during development are routed through a Vite proxy to avoid CORS issues against the deployed backend.

**`vite.config.ts`:**
```typescript
server: {
  proxy: {
    '/api': {
      target: process.env.VITE_BACKEND_ORIGIN ?? 'https://electricity-intelligence-platform-backend.onrender.com',
      changeOrigin: true,
      rewrite: (path) => path.replace(/^\/api/, ''),
    }
  }
}
```

> Pulling the target from an env var (rather than hardcoding it) means this file doesn't need to be edited every time the backend deployment URL changes.

**`.env.local`:**
```env
VITE_API_URL=/api
```

For direct local backend testing (bypassing the deployed Render instance), point at your local FastAPI server instead:
```env
VITE_API_URL=http://localhost:8000
```

---

## 🌐 Environment Variables

| Variable | Purpose | Example |
|---|---|---|
| `VITE_API_URL` | Base path/URL the API client sends requests to | `/api` or `http://localhost:8000` |
| `VITE_BACKEND_ORIGIN` | (Optional) Overrides the Vite dev-proxy target | `https://your-backend.onrender.com` |

---

## 🚀 Running Locally

```bash
npm install
```

Configure `.env.local`:
```env
VITE_API_URL=/api
```

```bash
npm run dev
```

Open `http://localhost:8443`

### Production Build
```bash
npm run build
```
Outputs static assets to `/dist`, ready for deployment to any static host (Vercel, Netlify, Render static site, etc.).

---

## 🧪 Quality & Tooling

| Task | Command | Status |
|---|---|---|
| Format | `<ADD_YOUR_FORMAT_COMMAND>` | via `oxfmt` |
| Lint | `<ADD_YOUR_LINT_COMMAND_OR_REMOVE_ROW>` | — |
| Test | `<ADD_YOUR_TEST_COMMAND_OR_REMOVE_ROW>` | — |

> Fill in or remove rows above based on what's actually configured in `package.json`. An unverified claim here is worse than no row at all.

---

## 📱 Browser & Responsiveness Notes

`<ADD_ACTUAL_BREAKPOINTS_AND_BROWSER_SUPPORT_HERE — e.g. "Tested on Chrome/Firefox/Safari, responsive from 375px mobile viewport up to 1920px desktop.">`

---

## 🖼️ Screenshots

`<ADD_SCREENSHOTS_OR_A_SHORT_GIF_OF_THE_DASHBOARD_HERE>`

> This is the single highest-impact addition you can make to this README — a dashboard product with no visual is a hard sell to anyone skimming the repo.

---

## 🤝 Contributing

```bash
git checkout -b feature/your-feature
git commit -m "feat: description"
git push origin feature/your-feature
```

---

## 📄 License

MIT — see [`LICENSE`](../LICENSE).

---

<div align="center">

Part of the [Electricity Intelligence Platform](../) monorepo — built by **Rohan Acharya** ([@R0han2906](https://github.com/R0han2906))

</div>
