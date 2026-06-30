# CPCL Holiday Facility — Frontend

The employee-facing web portal for CPCL's Holiday Home booking system. A single-page
application built in plain HTML, CSS, and JavaScript — no frameworks, no build step.

**Live demo:** https://cpcl-holiday-facility-frontend.vercel.app

## Overview

This frontend talks to the [CPCL Holiday Facility backend](https://github.com/Hasi0402/cpcl-holiday-facility)
over a REST API. It provides role-based dashboards for four user types:

- **Supervisor / Non-Supervisor (Employee):** browse eligible hotels, submit booking
  requests, track booking status, cancel bookings, view email notifications
- **IT Admin:** review pending requests, approve or reject bookings
- **Finance:** view cancellation fee notices and booking statistics

## Tech Stack

- HTML5, CSS3, vanilla JavaScript (ES6+)
- No frameworks, no bundler — a single `index.html` file
- Authenticates via JWT, stored in `localStorage` and sent as a Bearer token on every
  protected API request
- All data is fetched live from the backend; no mock data or local storage of app state

## Running Locally

This is a static file — no install step required.

```bash
git clone https://github.com/Hasi0402/cpcl-holiday-facility-frontend.git
cd cpcl-holiday-facility-frontend
```

Open `index.html` directly in a browser, or serve it with any static server:

```bash
npx serve .
```

### Connect to a backend

Open `index.html` and find this line near the top of the `<script>` block:

```javascript
const API_BASE = "http://localhost:3000/api";
```

Point it at your running backend:

- **Local backend:** leave as `http://localhost:3000/api`
- **Deployed backend:** change to your backend's public URL, e.g.
  `https://cpcl-holiday-facility-api.onrender.com/api`

The backend must have CORS configured to allow this frontend's origin — see the
backend's `FRONTEND_URL` environment variable.

## Demo Accounts

These exist after the backend's seed script has been run:

| Employee ID | Password | Role |
|---|---|---|
| EMP001 | pass | Supervisor |
| EMP002 | pass | Non-Supervisor |
| ADMIN01 | admin | IT Admin |
| FIN01 | fin | Finance |

## Deployment

Currently deployed on [Vercel](https://vercel.com) as a static site. To deploy your
own copy:

1. Fork or clone this repo
2. Import it into Vercel (or Netlify, GitHub Pages, etc.) — no build settings needed,
   it's a static HTML file
3. Update `API_BASE` to point at your deployed backend before pushing
4. Update the backend's `FRONTEND_URL` to this deployed frontend's URL so CORS allows it

## Related Repository

Backend API, database schema, and email service: 
[github.com/Hasi0402/cpcl-holiday-facility](https://github.com/Hasi0402/cpcl-holiday-facility)
