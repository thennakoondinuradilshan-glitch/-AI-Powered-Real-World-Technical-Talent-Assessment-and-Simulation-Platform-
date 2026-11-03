# TalentForge AI — Technical Talent Assessment Platform (Frontend Prototype)

React + Vite implementation of the TalentForge frontend, developed **separately from the original Figma file**. The original Figma was **not modified**.

## Start locally

Install Node.js 18+ and run:

```bash
npm install
npm run dev
```

Open http://localhost:5173. Production build: `npm run build`.

## Available routes

| Route | Screen |
| --- | --- |
| `/` | Responsive marketing homepage |
| `/login`, `/signup` | Demo sign-in and registration |
| `/dashboard` | Employer dashboard |
| `/assessments` | Assessment list and filters |
| `/assessments/new` | 5-step assessment builder |
| `/assessments/:id` | Assessment details, publishing, duplication, archive |
| `/invitations` | Candidate invitation manager |
| `/candidates` | Candidate directory |
| `/candidates/:id` | Candidate details and human review |
| `/candidate/welcome/:id` | Candidate welcome/instructions |
| `/candidate/assessment/:id` | Candidate challenge response workspace |
| `/candidate/success/:id` | Submission confirmation |
| `/settings` | Local profile settings |
| `/privacy` | Demo disclaimer |

## What's interactive

- Navigation, responsive sidebar and FAQ accordion.
- Assessment creation: basic info, challenges, AI policy, rubric, review and publish; draft is saved locally while being created.
- Assessment search and filters; publish/archive/duplicate controls.
- Candidate directory search and filters, invitation records, copyable assessment links.
- Candidate answers saved in browser storage as drafts, submission, manual review score.
- Sign-in/signup **only simulate a session**; no real authentication or password verification.

## Important constraints

This is a **frontend prototype**, not a production hiring tool. It deliberately **does not** send emails, perform real AI scoring, safely enforce exam deadlines, authenticate users, protect routes, persist data across devices, or securely store candidate records. Data is held in the browser's `localStorage` so it can be demonstrated without a backend. Sample profiles are synthetic. Never collect real applicant data or passwords with this demo.

The connected Figma API rejected direct design access. Accordingly, the UI uses the available user-supplied screenshot as a **visual and screen-name reference** (dark theme, warm orange accent, and visible route inventory). Remaining layouts are original design interpretations, **not verified pixel-perfect reproductions** of unseen Figma frames. Supplying screenshots or granting read access is necessary for high-fidelity matching later.

## Future backend integration

Suggested backend endpoints:

```text
POST /api/auth/register
POST /api/auth/login
GET  /api/assessments
POST /api/assessments
GET  /api/assessments/:id
PATCH /api/assessments/:id
GET  /api/candidates
POST /api/invitations
GET  /api/invitations/:token
POST /api/submissions
GET  /api/submissions/:id
PATCH /api/submissions/:id/review
```

The backend must authorize employer and candidate actions, generate unique secure invitation tokens, store and retrieve records, verify submissions, define a clear AI-assistance policy, and handle privacy/retention. Manual rubric scoring should be distinct from any automated evaluation. Replace `src/context/Store.jsx` local state with a proper data access/API layer during integration.

## Project structure

```text
src/
  components/  UI.jsx, Layout.jsx
  context/     Store.jsx (demo data and local state)
  pages/       Home, Auth, Dashboard, Assessments, CreateAssessment,
               Candidates, CandidateFlow, Settings
  styles/      global.css
  App.jsx      Routes and toast notifications
  main.jsx     React entry
```

## Integration note

Do not mix this ZIP blindly into an existing project or overwrite teammates' work. Review routes, dependencies, shared styles, and backend contract before merging. Replace sample data with real API data only after endpoint details are agreed upon.
