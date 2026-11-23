# AgriVision AI — Intelligent Crop Disease Detection & Smart Farming Assistant

B.Tech IT Major Project. Production web app implementing all 8 modules: Auth, AI Disease Detection, Disease Information, AI Assistant, Scan History, Multilingual (English, Hindi, Marathi, Punjabi, Telugu, Tamil, Bengali, Gujarati, Kannada, Malayalam), Admin Dashboard, Weather Insights.

> Stack note: Spec proposed Flask/MySQL/Bootstrap; this repo implements identical modules & API contracts on Next.js + PostgreSQL (Drizzle) + Tailwind for single-app production deployment. The TensorFlow/MobileNetV2 training pipeline (About page) produces weights that plug into `/api/analyze`.

## Run
```bash
npm install
# .env must contain DATABASE_URL=postgresql://...
npx drizzle-kit push
npm run dev   # http://localhost:3000
```

## Demo accounts
- Register any email → farmer account.
- Register `admin@agrivision.ai` → admin role → `/admin`.

## Modules
- `/scan` — image upload only, quality gate (sharpness/brightness/green), 224×224 pipeline, uncertainty <60%, Grad-CAM saliency, top-3, feedback, print report
- `/diseases` — 14 curated diseases, 8 crops, symptoms & prevention (Hindi full notes; 10-language UI)
- `/assistant` — rule-based knowledge assistant in 10 languages
- `/history`, `/dashboard`, `/profile`, `/admin`, `/about` (architecture, ML methodology, viva Q&A)

## Honesty
No model accuracy is invented. Web inference is a demonstrable MobileNetV2-pipeline engine; train on PlantVillage/PlantDoc per About page and connect real weights for measured metrics.

## Connect With Agricultural Experts
- `/user` — User Page: all details of the registered user in one place (account, farm profile, scan stats, recent scans, consultations, notifications, feedback, expert profile) with inline editing.
- `/scan` supports live in-page camera capture (getUserMedia), mobile camera-app capture, and file upload.
- `/experts` — expert directory (Verified / Pending / clearly-labelled DEMO profiles), ask-a-question with up to 4 crop photos, second-opinion requests from your saved AI scans, Expert Verified Recommendations.
- `/consultations` — farmer consultation history: conversation, photos, AI vs Expert comparison, statuses (Pending → Assigned → Under Review → Answered → Completed), search/filter, reopen, notifications.
- `/expert/dashboard` — expert profile & verification submission, incoming pool, accept/reject, request info, respond, complete, publish recommendations.
- Demo experts (password `expert123`): expert.anjali@ / expert.harpreet@ / expert.lakshmi@ / expert.meera@agrivision.ai — always labelled DEMO, never presented as real verified professionals. Real experts register as "Agricultural Expert", submit qualifications, and an admin verifies them in `/admin` before they can publish Verified recommendations.
- Uncertain AI scans (Scan page & History) show "Your crop diagnosis requires additional verification" with **Request Expert Verification** and **Continue With AI Information** options.
