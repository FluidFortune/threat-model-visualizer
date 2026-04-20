# Threat Model Visualizer

A client-side web app that generates structured threat models using the **STRIDE framework** — the same methodology used by security teams at Microsoft, Google, and across the industry.

**[Live Demo →](https://YOUR_USERNAME.github.io/threat-model-visualizer)**

---

## What it does

Describe your system's architecture in plain English and the app returns a full STRIDE threat model: categorized threats, severity ratings, attack vector descriptions, and concrete mitigations — all rendered as an interactive dashboard.

**STRIDE categories covered:**
- **S**poofing — impersonating users, services, or components
- **T**ampering — unauthorized modification of data in transit or at rest
- **R**epudiation — denying actions without an audit trail
- **I**nformation disclosure — leaking sensitive data
- **D**enial of service — making the system unavailable
- **E**levation of privilege — gaining unauthorized access levels

---

## Design decisions worth noting

**User-supplied API key**
The app uses the Google Gemini API but does not bundle an API key. Instead, users paste their own key into the interface. The key is held in a JavaScript variable for the session and is gone when the tab closes — it is never written to localStorage, never sent to any server other than `generativelanguage.googleapis.com`, and never logged. This is a deliberate security design choice.

**Fully client-side**
There is no backend, no database, no server. The entire app is a single HTML file. This eliminates a large class of server-side vulnerabilities and means the app can be deployed anywhere static files are served — including GitHub Pages.

**Free API tier**
The app runs on Gemini 2.0 Flash, which has a generous free tier (1,500 requests/day). No credit card required to get an API key.

---

## Running it locally

No build step, no dependencies, no npm install.

```bash
git clone https://github.com/YOUR_USERNAME/threat-model-visualizer
cd threat-model-visualizer
open index.html   # or just double-click it
```

Get a free Gemini API key at [aistudio.google.com/apikey](https://aistudio.google.com/apikey).

---

## Deploying to GitHub Pages

1. Push `index.html` to a GitHub repo
2. Go to **Settings → Pages**
3. Set source to **Deploy from branch → main → / (root)**
4. Your app will be live at `https://YOUR_USERNAME.github.io/REPO_NAME`

---

## Tech stack

- Vanilla HTML, CSS, JavaScript — no frameworks
- Google Gemini 2.0 Flash API
- STRIDE threat modeling framework

---

## Example system descriptions to try

> A React SPA with a Node.js REST API, PostgreSQL database, and JWT auth stored in localStorage. File uploads go to S3. The API is behind AWS API Gateway. Admins have a separate dashboard at /admin.

> A locally hosted AI chatbot (llama.cpp) exposed via a public subdomain. No user authentication. Users send free-text prompts directly to the inference server.

> A mobile app (iOS/Android) with a Firebase backend. Users authenticate via Google OAuth. The app stores medical records and syncs across devices.

---

*Part of my cybersecurity portfolio. Built in an evening as a practical demonstration of STRIDE threat modeling and secure API design patterns.*
