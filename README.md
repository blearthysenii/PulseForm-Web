# PulseForm Web

Frontend for **PulseForm** — a survey & feedback platform. Build a survey, share a link, collect answers, and watch the results fill in as clean, visual charts.

This repository contains the web client built with **React**. The backend lives in a separate repo: [PulseForm-API](https://github.com/blearthysenii/PulseForm-API).

---

## ✨ The core loop

1. **Build** — a creator makes a survey: title, description, and a list of questions. Each question has a type (multiple choice, rating scale, free text) and the builder shows the matching options.
2. **Share** — publish the survey and get a shareable link anyone can open.
3. **Collect** — respondents see a clean page with one survey, fill it in, and submit.
4. **Analyze** — the creator opens the results view: bar charts for multiple-choice, distributions for rating scales, response counts, and free-text answers gathered for reading.

## 🧩 Main screens

| Screen | Description |
|---|---|
| **Auth** | Register & login for creators and admins. Respondents need no account. |
| **My surveys** | List of the creator's surveys with status (draft / open / closed). |
| **Survey builder** | Add, edit, reorder, and remove questions; pick a type per question; mark questions as required; import questions from a CSV file. |
| **Public survey page** | Clean page that renders the right input for each question type, validates required questions, and confirms submission. |
| **Results dashboard** | A visual summary per question — bar charts for choices, a distribution for scales, totals, and free-text answers. |
| **Admin view** | Overview of all surveys and accounts, for moderation and support. |

## 👤 Roles in the UI

- **Creator** — full builder + results for their own surveys only.
- **Respondent** — sees only the survey itself, never any results.
- **Admin** — platform-wide overview.

---

## 🛠 Tech stack

- **React 18** + **Vite**
- **React Router** — routing
- **Axios** — API client
- **Recharts** — charts for the results dashboard
- **Context API / hooks** — auth & app state

## 📁 Project structure

```
PulseForm-Web/
├── src/
│   ├── main.jsx
│   ├── App.jsx                # routes
│   ├── api/                   # axios instance & API calls
│   ├── context/               # AuthContext (JWT, role)
│   ├── components/
│   │   ├── builder/           # question editor, type picker, CSV upload
│   │   ├── survey/            # public survey renderer (one input per type)
│   │   └── results/           # charts & summaries
│   ├── pages/
│   │   ├── Login.jsx / Register.jsx
│   │   ├── Dashboard.jsx      # my surveys
│   │   ├── SurveyBuilder.jsx
│   │   ├── PublicSurvey.jsx   # /s/:shareToken
│   │   └── Results.jsx
│   └── utils/
├── public/
├── .env.example
├── package.json
└── README.md
```

## 🚀 Getting started

> Requires the backend ([PulseForm-API](https://github.com/blearthysenii/PulseForm-API)) running locally at `http://localhost:8000`.

### 1. Clone & install

```bash
git clone https://github.com/blearthysenii/PulseForm-Web.git
cd PulseForm-Web
npm install
```

### 2. Configure environment

```bash
cp .env.example .env
```

```env
VITE_API_URL=http://localhost:8000
```

### 3. Run the dev server

```bash
npm run dev
```

The app runs at `http://localhost:5173`.

### Build for production

```bash
npm run build
npm run preview
```

## 🔌 Talking to the API

All requests go through a single Axios instance (`src/api/`) that:

- prefixes requests with `VITE_API_URL`,
- attaches the JWT token from `AuthContext` for protected routes,
- leaves public routes (`/s/:shareToken`) token-free so anonymous respondents can answer.


## 👥 Team

- [Abit Hyseni](https://github.com/biti222)
- [Flamur Avdylaj](https://github.com/avdylaj-flamur)
- [Bleart Hyseni](https://github.com/blearthysenii)
- [Elijon Rexhepi](https://github.com/ElionR)

## 🎓 Mentor

- Labinot Jaha

Project developed as part of the Intern Capstone Project.



## 🎨 Design note

A central UI challenge of this project: **rendering the correct input for each question type** — radio buttons / checkboxes for multiple choice, a 1–5 scale control for ratings, and a textarea for free text — all driven by the same question data structure coming from the API.

## 🔗 Related

- Backend: [PulseForm-API](https://github.com/blearthysenii/PulseForm-API)
