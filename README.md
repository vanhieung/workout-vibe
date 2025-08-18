# Workout Player — 30‑Minute (Dumbbells + Mat)

Train at home with **coaching videos**, a **countdown timer**, **auto‑advance**, and a **day‑based auto schedule**. Ships with a full React app and ready‑to‑use single‑file HTML demos.

---

## Features
- ⏱️ Per‑exercise countdown with **Work → Rest → Next** flow.
- ▶️ Embed YouTube/MP4 for each exercise (auto‑converts watch/short links to `embed`).
- 🔔 (React app) Optional 3‑2‑1 beeps near the end of each set.
- 💾 (React app) Import/Export workout JSON and persist to `localStorage`.
- 🗓️ (HTML demo) **Auto Schedule** by weekday (Mon→A, Tue→B, Wed→REST, Thu→A, Fri→B, Sat→C, Sun→REST).
- ⌨️ Shortcuts: `Space` (Pause/Resume), `←/→` (Prev/Next), `R` (Reset).
- ♿ Accessible labels, numeric **tabular** font for timers.

---

## Quick Demo (Single‑file HTML)
The `standalone/` folder contains open‑and‑run HTML files, ideal for GitHub Pages/Netlify/S3 uploads:

- `workout_player_standalone_v2.html` — single default session (curated videos).
- `workout_player_30min_multiplan_v2.html` — choose **A/B/C** sessions.
- `workout_player_auto_schedule_v2.html` — auto‑selects session by weekday and shows a **REST** screen (breathing animation + tips).

> Note: the HTML demos use **Tailwind CDN** and **in‑browser Babel** for convenience. For production, prefer the built React build (or bundle these files yourself).

---

## Getting Started (React + Vite)
```bash
npm install
npm run dev            # http://localhost:5173
npm run build && npm run preview
npm run test
```
Main dependencies: React, Vite, Tailwind CSS, framer‑motion, lucide‑react, Vitest, Testing Library.

---

## Project Structure
```
.
├─ standalone/
│  ├─ workout_player_standalone_v2.html
│  ├─ workout_player_30min_multiplan_v2.html
│  └─ workout_player_auto_schedule_v2.html
├─ src/
│  ├─ App.tsx
│  ├─ main.tsx
│  ├─ index.css
│  ├─ types.ts
│  ├─ utils/
│  │  ├─ time.ts
│  │  └─ storage.ts
│  ├─ data/
│  │  └─ defaultWorkout.ts
│  ├─ hooks/
│  │  └─ useBeeps.ts
│  ├─ reducer/
│  │  ├─ playerReducer.ts
│  │  └─ playerReducer.test.ts
│  └─ components/
│     ├─ ProgressCircle.tsx
│     └─ WorkoutPlayer.tsx
├─ index.html
├─ tailwind.config.ts
├─ vite.config.ts
└─ package.json
```

---

## Customization

### 1) Default workout (React)
Edit `src/data/defaultWorkout.ts` (schema below) or Import a JSON from the UI:
```ts
export type Workout = {
  name: string
  exercises: {
    id: string
    title: string
    durationSec: number
    restSec?: number
    videoUrl?: string
    tips?: string
  }[]
}
```
- Use YouTube `watch?v=` or `youtu.be/...` — the app converts to `embed` automatically.

### 2) Auto schedule mapping (HTML demo)
In `standalone/workout_player_auto_schedule_v2.html`:
```js
// 0=Sun ... 6=Sat
const DAY_PLAN = { 0:'REST', 1:'A', 2:'B', 3:'REST', 4:'A', 5:'B', 6:'C' }
```
Change this mapping to fit your training rhythm (e.g., mobility on Wed, full rest Sun).

### 3) Video links (refreshed)
- Goblet Squat — `https://www.youtube.com/watch?v=MeIiIdhvXT4`
- DB Floor Press — `https://www.youtube.com/watch?v=uUGDRwge4F8`
- DB Romanian Deadlift — `https://www.youtube.com/watch?v=FQKfr1YDhEk`
- Dead Bug — `https://www.youtube.com/watch?v=bxn9FBrt4-A`
- Cooldown/Mobility — `https://www.youtube.com/watch?v=lxuTCHJSers`

---

## Deploy

### A) React app (recommended for production)
- Vercel/Netlify:
  - Build: `npm run build`
  - Output: `dist/`
- GitHub Pages:
  - If deploying under a subpath, set `base` in `vite.config.ts`:
    ```ts
    export default defineConfig({
      base: '/<repo-name>/',
      plugins: [react()],
    })
    ```

### B) Single‑file HTML
Upload the files from `standalone/` to any static host (GitHub Pages/Netlify/S3).  
Run locally:
```bash
python -m http.server 8080
# or
npx serve -p 8080 .
```

---

## Accessibility & Shortcuts
- Timers use tabular numbers; key UI elements include ARIA labels.
- Shortcuts: `Space` (Pause/Resume), `←` Prev, `→` Next, `R` Reset.

---

## License
**MIT** — use, remix, and share freely. Please credit original video creators where appropriate.
