# MyTax Receipt Logger — UI Prototype

A web application that helps Malaysian individual taxpayers digitise, categorise, and track tax relief receipts in compliance with LHDN's 7-year retention requirement under the Income Tax Act 1967.

**Live demo:** https://joshjw89.github.io/MyTax-Receipt-Logger/

> This is a UI-only prototype built for assignment (Software Process and Management). It runs entirely in the browser with no backend server.

---

## Features

- **User authentication** — registration and login
- **Receipt upload** — JPEG, PNG and PDF support
- **OCR auto-fill** — [Tesseract.js](https://github.com/naptha/tesseract.js) scans receipt images client-side and auto-fills merchant, date and amount, with manual override
- **LHDN relief categorisation** — receipts are mapped to official MyTax tax relief categories with their RM limits
- **Dashboard** — real-time tracking of claimable amounts per category
- **Search & filter** — by merchant, category, and date range
- **Storage lifecycle simulation** — demonstrates a Hot → Cold tiering policy (modelled on Azure Blob Storage lifecycle management)
- **Annual summary report** — exportable to PDF via the browser's print function

## Tech stack

| Layer | Technology |
|---|---|
| UI framework | React 18 (via CDN, no build step) |
| Styling | Tailwind CSS (CDN) |
| JSX transform | Babel Standalone (in-browser, classic runtime) |
| OCR | Tesseract.js v5 |
| Data storage | Browser `localStorage` (UI prototype only — see below) |
| Hosting / CI-CD | GitHub Pages + GitHub Actions |

## Architecture

This repository contains the UI build for MyTax Receipt Logger. A full-stack version of this project also exists, using:

- Node.js + Express backend
- SQLite (local prototype) — designed for Azure Database for PostgreSQL in production
- Local filesystem Hot/Cold folders — designed for Azure Blob Storage lifecycle tiers in production
- JWT + bcrypt authentication

For this UI build, the backend is replaced with the browser's `localStorage` so the app can run as a static site with no server. Functionally, the login to the UI and the OCR works. All other feature as still in development.

## Running locally

No installation required - just open `index.html` directly in a browser.

For local testing:

1. Download the MyTax-Receipt-Logger-main.zip
2. Extract the files to directory
3. Install Node.js https://nodejs.org/en/download 
4. Launch cmd or powershell and navigate to the folder containing the extracted file for MyTax-Receipt-Logger-main.zip
5. Run: npx serve
6. Then open the printed `http://localhost:3000` address on your browser.
